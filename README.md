# Clean-Architecture-Book
Clean Architecture



Clean Architecture


第16章标题为《独立性》，探讨了系统架构中如何实现各部分的独立性，以支持系统的不同使用场景和开发模式。这个章节详细阐述了如何通过分离系统的不同层次和用例，最大化灵活性、开发效率以及系统的易部署性。

1. 用例（Use Cases）
系统架构首先必须支持系统的用例，也就是支持系统的预期行为。无论是购物车系统还是订单处理系统，系统的架构都需要清晰地展现其主要用例，使其在架构层次上显而易见。在这一点上，良好的架构并不仅仅依赖于功能，而是需要通过清晰的系统设计将功能呈现出来，使得开发者能够轻松找到系统的行为和对应的功能模块。

为了确保这一点，架构师应当关注如何将这些行为抽象化，确保架构清晰可见。理想的架构会将系统的主要功能模块，例如订单添加、订单删除等，划分为各自独立的部分，这些功能应该是系统的顶级元素，具有清晰的名称和明显的功能描述。

2. 操作（Operation）
除了支持系统行为，架构在系统运行中也起着重要作用。架构应当支持系统的性能需求，例如高吞吐量、低延迟等。具体实现方式可能包括将系统的处理元素拆分为多个小服务，这些服务可以在多个服务器上并行运行，从而提高系统的扩展性和运行效率。

良好的架构应当尽可能地开放操作选项。系统架构设计得越松散，越能适应未来的操作需求变化。比如，一个良好的架构能够从单一的进程扩展到多线程甚至微服务架构，而不需要对系统的基本结构进行大幅度调整。

3. 开发（Development）
在系统的开发过程中，架构的设计同样起着至关重要的作用。良好的架构应该能够支持团队的并行开发。为了避免团队之间的干扰，系统需要被合理地划分为多个独立的组件。这些组件可以分别分配给不同的团队进行开发，从而提高开发效率。

这里引用了康威定律（Conway’s Law）：任何组织设计的系统，其结构必然反映该组织的沟通结构。因此，一个多团队开发的系统架构必须适应这种团队的结构。通过对系统进行适当的分区，能够确保各个团队可以独立工作，减少沟通成本和协调的负担。

4. 部署（Deployment）
架构在系统的部署中也起着决定性的作用。理想的架构设计应当能够使系统在构建之后即可部署，不依赖于复杂的配置脚本或手动操作。这就需要架构设计能够将系统分割成多个可独立部署的部分，确保每个组件都能够单独启动和集成。

通过这种方法，系统的各个部分可以分别进行部署，甚至在运行时也能够替换或更新单个组件，而不影响系统的其他部分。这种设计大大提高了系统的灵活性和可维护性，能够适应持续交付和频繁更新的需求。

5. 保持选择的开放性（Leaving Options Open）
在应对系统复杂性的过程中，架构师需要平衡各方需求，并尽可能地保持架构的灵活性。问题在于，通常在项目初期，架构师并不完全清楚系统所有的用例、操作约束或团队结构。甚至这些因素在系统生命周期中也会不断变化。因此，架构设计必须尽可能为未来的变化留出空间。

解决这一问题的关键在于，架构师可以采用一些相对廉价的架构原则，帮助将系统划分为独立的组件，从而在尽量长的时间内保持尽可能多的选项开放。

6. 分离层（Decoupling Layers）
在设计系统架构时，架构师通常知道系统的基本目标是什么，但不一定知道所有的用例。因此，使用单一职责原则（SRP）和共同闭包原则（CCP），可以将那些由于不同原因而变化的部分分离出来，收集那些由于相同原因而变化的部分。具体来说，UI通常由于与业务规则无关的原因发生变化，因此应当将UI部分与业务规则部分分离开。

此外，架构师还可以使用垂直的切片方法，将系统按用例划分为多个竖向的薄片（thin slices），每个用例横跨不同的系统层次。通过这种方式，系统的UI、业务规则和数据库等部分可以分别演化，避免相互影响。

7. 独立开发性（Independent Develop-ability）
系统的各个组件应当能够独立开发，减少团队间的干扰。例如，UI团队和业务规则团队应当能够并行工作，而不互相影响。为了实现这一点，系统的用例也应当被解耦。添加订单和删除订单的用例应当独立存在，确保一个用例的修改不会影响另一个用例。

通过解耦层和用例，系统架构可以支持团队的组织结构，无论团队是按照功能、组件还是层级来划分，架构都能够提供足够的灵活性，支持不同的开发模式。

8. 独立可部署性（Independent Deployability）
通过解耦用例和层，系统在部署时也能具备高度的灵活性。如果解耦做得好，理论上可以实现对系统各个层次和用例的热插拔。也就是说，开发者可以通过添加一些新的JAR文件或服务，来增加一个新功能，而不需要重新部署整个系统。

这种独立可部署性极大地提高了系统的运维效率和可靠性，能够确保系统在运行时可以平稳地进行更新和维护。

9. 重复问题（Duplication）
许多架构师往往会因为对代码重复的恐惧而陷入困境。尽管代码重复通常是不好的，但书中指出，必须区分不同类型的重复：真实的重复和偶然的重复。如果两个表面上相似的代码片段在不同时间、由于不同原因发生变化，那么它们实际上并不是重复的。

对于看似重复的部分，架构师需要谨慎处理，确保不要过早地将它们统一起来。否则，随着系统的演进，可能会发现这些部分逐渐分化，最终很难再次将它们分离出来。

10. 解耦模式（Decoupling Modes）
系统的解耦可以发生在多个层次上：源代码层、二进制部署层和服务层。尽管服务层的解耦具有高度的灵活性，但其开发和维护成本也较高。因此，作者建议在可能的情况下，先将组件在源代码层上解耦，只有在需要时才将其提升为独立的服务。

这种分阶段的解耦方式，可以使系统在初期保持单体架构的简单性，但在需要时也可以逐渐扩展为服务架构或微服务架构。随着系统的演变，解耦模式也可能随之改变。良好的架构应当允许系统从单体架构逐步扩展为一组独立部署的单元，甚至进一步发展为完全解耦的微服务架构。



第17章《边界：划定界限》探讨了软件架构中的边界问题，即如何在系统中划分和管理不同组件之间的边界。良好的边界划分是构建可维护、灵活且可扩展的软件系统的基础。通过合理划定边界，开发者可以将系统的核心业务逻辑与外部细节（如数据库、UI等）隔离开来，延迟技术决策，并减轻系统演进过程中耦合和复杂性的增加。以下是对第17章的详细总结：

1. 软件架构的核心：划定边界
软件架构的艺术在于划定边界，这些边界将系统的不同部分隔离开来，并限制这些部分之间的相互了解。划定边界有助于使系统的不同组件在不同的开发周期中相互独立运行，减少相互之间的依赖，确保系统的核心业务逻辑不受外部细节的干扰。这一章指出，边界的划定应尽早进行，有时甚至在代码编写之前就已经开始，以便推迟那些不必要的技术决策，并使这些决策不会污染核心业务逻辑。

2. 避免早期决策
架构师的目标是通过合理设计最小化构建和维护系统所需的人力资源。导致系统复杂度增加的主要因素之一是耦合，特别是与早期决策的耦合。过早决定使用某种技术、框架或库，可能会导致后期维护和扩展上的困难。

早期的架构设计应尽可能推迟与具体实现有关的决策，例如关于数据库、Web服务器、依赖注入框架等。这些决策与系统的业务需求无关，因此应尽量推迟。在理想的系统架构中，这些决定应该是可选的、可推迟的，而且推迟这些决定不应对系统的核心业务逻辑产生重大影响。

3. 现实中的案例
本章通过几个失败的架构案例，强调了不合理边界划定的危险性。举例来说，一家公司为了跟上互联网的浪潮，决定将其原本成功的桌面应用程序转换为Web应用程序。该公司为此采用了三层架构，并过早决定在各层之间采用大量的对象序列化和通信机制。然而，最终这个系统只在单一服务器上运行，而不需要分布式的服务器场，导致他们为那些永远不会出现的需求付出了大量开发成本。

这类案例显示出，过早做出关于技术实现的决策会对项目造成严重影响。公司不仅没有实现其预期的架构目标，反而增加了开发和维护的复杂性与成本。

4. FitNesse案例：一个成功的边界划分
与失败的架构相比，书中还介绍了FitNesse项目的成功案例。FitNesse是一个用于编写验收测试的Wiki工具，最初开发时并未选择任何现成的Web服务器或框架，而是自己构建了一个简易的Web服务器。这个决策帮助开发者推迟了与Web服务器和框架相关的技术选择，直到他们确定了确实需要这类功能为止。这一决策显著减少了开发中的复杂性，使得团队能够专注于核心业务功能的开发。

通过划定边界，FitNesse的业务逻辑与底层技术实现之间建立了一道防火墙，这使得后期技术选择变得更加灵活和高效。

5. 划定边界的时机与方法
开发者应在不同模块之间划定边界，尤其是业务逻辑与用户界面、数据库之间的边界。用户界面通常会频繁变化，且与业务规则的变化无关，因此应与业务逻辑分离。同样，数据库的实现细节不应渗透到业务规则中。数据库只是用于存储和获取数据的工具，业务规则不需要了解数据库的结构或查询语言，而只需要知道可以通过某些方法存储或检索数据。这意味着数据库应当通过接口与业务逻辑进行交互。

这种边界划分使得业务逻辑能够独立于具体的数据库实现。例如，系统可以在不修改业务逻辑的情况下切换不同的数据库（如MySQL、CouchDB或文件系统），因为数据库的实现已经被封装在接口后面。

6. 插件式架构
书中提倡插件式架构，即将那些并非系统核心的功能模块设计为插件。这种设计使得系统的核心业务逻辑独立于外部模块，如用户界面、数据库等。在这种架构下，用户界面或数据库都可以作为插件接入系统，从而实现高灵活性和可扩展性。例如，系统可以在需要时切换不同的用户界面技术或数据库，而无需对核心业务逻辑进行重大修改。

插件式架构的好处还在于，系统不同部分的开发者可以独立工作，减少了耦合对开发进度的影响。系统中的变化不会轻易传播到其他无关部分，从而避免了系统脆弱性。

7. SRP和边界划分
本章进一步强调了**单一职责原则（SRP）**在划定边界时的重要性。SRP告诉我们应该在哪些地方划定边界，即系统中那些因不同原因或在不同时间变化的部分，应当通过边界分隔开来。具体而言，GUI层和业务规则层变化的原因和频率不同，因此应当划定边界。同样，依赖注入框架和业务规则层的变化原因也不同，因此也应当划定边界。

8. 插件架构的实际应用
为了更好地说明插件架构的优越性，书中以ReSharper与Visual Studio的关系为例。ReSharper是一款插件，它依赖于Visual Studio，但Visual Studio并不依赖ReSharper。这种单向依赖关系确保了Visual Studio的开发团队不会因为ReSharper的变化而受到干扰，但ReSharper的开发团队必须跟随Visual Studio的变化进行调整。这种依赖关系的非对称性是插件架构的核心理念，即通过控制依赖方向，减少系统中的耦合和变化的传播。

9. 边界的意义
本章最后总结道，软件架构中的边界划分至关重要。通过合理划定边界，系统可以实现模块化，减少耦合，提高灵活性和可维护性。架构师的任务是在系统中识别变化的轴，并根据这些变化的原因和频率划定边界。插件式架构是一种有效的边界划分方式，通过将可变的部分封装为插件，核心业务逻辑可以保持稳定，系统可以随着需求的变化轻松进行扩展和调整。



第18章《边界解剖》深入探讨了软件架构中的边界划分，以及在不同场景下如何跨越边界来确保系统的模块化和解耦性。主要内容涵盖了边界的多种形式及其应用，重点介绍了边界跨越、单体结构、部署组件、线程、本地进程和服务，以及这些边界形式在不同系统设计中的重要性和使用场景。以下是对该章内容的详细总结：

1. 边界的定义与跨越
边界的作用是将系统划分为多个部分，减少它们之间的耦合。在运行时，边界的跨越体现为一个函数调用另一个函数，并传递相应的数据。核心挑战在于如何管理源代码的依赖关系，确保系统的修改不会影响其他不相关的模块。

跨越边界时，通常会涉及到源代码依赖。如果一个源代码模块发生了变化，其他依赖于它的模块也可能需要重新编译、重新部署。通过边界管理，可以有效地建立“防火墙”，隔离变化，减少连锁反应对系统的影响。

2. 单体架构的挑战
单体架构是最常见的系统架构之一，通常表现为一个大规模的单一部署单元，比如一个包含所有功能的可执行文件。单体系统的部署尽管在物理上是单一的，但其内部可以通过严格的功能分离实现逻辑上的模块化。边界跨越在这种系统中通常只是简单的函数调用，虽然速度快，但系统各部分的开发、测试和部署会相对复杂，多个团队的工作容易相互影响。

尽管单体结构内部的通信效率很高，通常只是函数调用，但这种架构容易产生耦合，导致系统的扩展性较差。

3. 部署组件
一个更物理化的边界表现是部署组件。部署组件如Java中的JAR文件或.NET中的DLL文件，这些组件通常以二进制形式进行部署，不需要重新编译代码。这类组件的通信通常也只涉及函数调用，通信成本较低，边界跨越很快，除非涉及动态链接或运行时加载。

这种结构下的开发模式与单体结构类似，但组件间的依赖管理更为严格。每个组件可以被独立开发、测试和部署，从而实现更高的灵活性。

4. 线程
线程不是架构边界，而是用于组织系统执行顺序的机制。在单体架构或部署组件中，线程可以完全包含在组件内部，或者跨越多个组件进行执行。线程的作用是提高系统的并发性和性能，而不是分离组件。因此，线程在某种程度上不会影响系统的解耦性，但可以影响系统的执行顺序和效率。

5. 本地进程
本地进程提供了更强的物理边界。本地进程运行在独立的地址空间内，通常通过操作系统调用、套接字、消息队列等方式进行通信。这种隔离程度比单体架构和部署组件更强，进程之间的内存不共享，通信成本也更高，因为涉及数据的编组、解组和上下文切换。

尽管通信成本较高，本地进程之间的强隔离使得系统更具稳健性和安全性。进程间的相互影响更少，每个进程可以独立开发、部署和运行。

6. 服务
服务代表了最强的边界形式。服务是独立的进程，它们可能运行在同一个物理处理器上，也可能运行在不同的网络节点上。服务间的通信通常通过网络进行，因此通信延迟高且成本大，需要避免频繁的交互（即“话唠”式通信）。服务间的解耦性非常高，能够有效支持大规模的分布式系统。

通过服务划分的系统具有高度的独立性和灵活性，但需要面对高通信成本和网络延迟的挑战。

7. 边界的选择与设计
在设计边界时，架构师需要根据系统的复杂性、团队结构、部署要求等因素来决定如何划分边界。过多的边界会增加系统的复杂性和管理成本，而过少的边界则可能导致系统的耦合度过高。理想的设计是在合适的地方设置合理的边界，以达到系统性能、可扩展性和可维护性的平衡。

本章通过对比单体结构、部署组件、线程、本地进程和服务的边界形式，展示了如何根据系统需求和约束条件选择合适的边界类型。通过合理划分边界，系统可以在保持高性能的同时，实现模块化、解耦和独立部署。





