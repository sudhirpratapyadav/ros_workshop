  # Free Online ROS Courses/Resources

## MOST IMPORTANT
- **MUST READ BOOK: Robot Operating System (ROS) for Absolute Beginners**
	- https://www.amazon.in/Robot-Operating-System-Absolute-Beginners-ebook/dp/B07D9CGKQ7
	- It covers basics of linux/ubuntu, C++, python then start with ROS
	- It covers history and why to use ROS and when not to
	- It covers very basic concept of ROS to get you started
	- Read other books/course only after you cover this
- **Official Documentation (THESE ARE YOUR GO TO SITE FOR ANY THING ABOUT ROS)**
	- https://wiki.ros.org/ (DOCUMENTATION, TUTORIALS, INSTALLATION)
	- https://answers.ros.org/ (DOUBTS/QUESTIONS)

## EXTRAS
- Pre-requisites
	- Linux (how to work in linux OS)
		- https://www.youtube.com/watch?v=_YHvSl_yQDk
	- Python
		- https://www.youtube.com/watch?v=HqKpHj0_jtg
-  ETH Zurich
	- https://www.youtube.com/watch?v=0BxVPCInS3M&list=PLE-BQwvVGf8HOvwXPgtDfWoxd4Cc6ghiP
	- https://www.youtube.com/watch?v=aL7zLnaEdAg&list=PLBuuYcZ1GRMQ-zmoS5WM4RJr6_wbqY4dH
		- https://www.youtube.com/watch?v=aL7zLnaEdAg (if above link doesn't works)
- The Construct
	- All Courses List: https://www.theconstructsim.com/robotigniteacademy_learnros/ros-courses-library/
	- https://www.theconstructsim.com/robotigniteacademy_learnros/ros-courses-library/ros-python-course/
	- https://www.theconstructsim.com/robotigniteacademy_learnros/ros-courses-library/linux-for-robotics/
-  EDX
	- https://www.edx.org/course/hello-real-world-with-ros-robot-operating-system
-  List of other courses
	- http://wiki.ros.org/Courses

# Table of content
- Intro to ROS
	- Why ROS
	- What is ROS
	- Why not ROS
- Installation
- Basics of ROS
	- File System Level
	- Computational Graph Level
- Official Tutorials
- Other
	- Simulation - Gazebo
	- Visualisation - Rviz
	- Robot Modelling - URDF
- Hands On
	- P3DX
	- UR5

# Content
- Sources
	- Book mentioned above
	- Official documentation mentioned above

## Intro
- Sources
	- Link: http://wiki.ros.org/ROS/Introduction
		- http://wiki.ros.org/ROS/StartGuide
	- Ch4: Kick-Starting Robot Programming Using ROS

### Inspiration
- From Shakey (1972) to Say-Can (2022) - What we want **GENERALISATION / ROBUSTNESS**
	- Shakey: https://www.youtube.com/watch?v=GmU7SimFkpU
	- Say-Can: https://www.youtube.com/watch?v=ysFav0b472w&feature=youtu.be
-  and off-course **Boston Dynamics** (Hopefully you already know it, otherwise search on you tube)
- Other Videos if you are interested
	- MIT robotics seminar: https://www.youtube.com/c/MITRoboticsSeminar/videos
		- my favourite: https://www.youtube.com/watch?v=k8Zh7ColEbw
	- Robotics Today: https://www.youtube.com/c/RoboticsTodaySeminar/videos
	- 
### Robot Programming
- **Robot Definition:** Robot is a machine with sensors, actuators (motors), and a computing unit that behaves based on user controls, or it can make its own decisions based on sensor inputs
- ![[Pasted image 20220721232453.png]]
	- Source: http://www.incbtech.com/index.php/articles/80-mechatronic/3269-using-basic-blocks-en-robotic-projects-mec114e
- **Robot Programming** is programming the  microcontroller (Brain) inside robot for performing a specific application using actuators and feedback from various sensors.
	- Robotic programming creates intelligence in the robot for self-decision making, implementing controllers like PID to move joints, automating repeated tasks, and creating robotic vision applications.

#### Robot Programming vs Normal Programming
- Robot programming is a subset of computer programming. Most robots have a "brain" that can make decisions. It can be a microcontroller or a PC.
- The differences between robot programming and conventional programming are the input and output devices. The input devices include robot sensors, teach pendants, and touch screens, and the output devices include LCD displays and **actuators**.

### What does ROS offer?
- Most important thing that ROS offers in my view is **Hardware Abstraction** in a conceptual-framework appropriate for robot operation, thus aptly called Robot "Operating System".
	- As the name says, ROS is not a real operating system. It is a meta-operating system that provides some operating system functionalities.
	- These functionalities include multithreading, low-level device control, package management, and hardware abstraction.
	- The hardware abstraction layer enables programmers to program a device. The advantage is that we can write code for a sensor that works the same way with different vendors. So, we don’t need to rewrite the code when we use a new sensor.
	- Package management helps users organize software in units called packages. Each package has source code, configuration files, or data files for a specific task. These packages can be distributed and installed on other computers.
- Other things
	- Message passing interface between processes:
	- High-level programming language support and tools:
	- Availability of third-party libraries:
	- Off-the-shelf algorithms:
	- Ease in prototyping:
	- Ecosystem/community support:
	- Extensive tools and simulators:
- The ROS runtime "graph" is a peer-to-peer network of processes (potentially distributed across machines) that are loosely coupled using the ROS communication infrastructure. ROS implements several different styles of communication, including synchronous RPC-style communication over [services](http://wiki.ros.org/Services), asynchronous streaming of data over [topics](http://wiki.ros.org/Topics), and storage of data on a [Parameter Server](http://wiki.ros.org/Parameter%20Server). These are explained in greater detail in our [Conceptual Overview](http://wiki.ros.org/ROS/Concepts).
- ROS is not a realtime framework, though it is possible to integrate ROS with realtime code. The Willow Garage PR2 robot uses a system called [pr2_etherCAT](http://wiki.ros.org/pr2_etherCAT), which transports ROS messages in and out of a realtime process. ROS also has [seamless integration with the Orocos Real-time Toolkit](http://www.willowgarage.com/blog/2009/06/10/orocos-rtt-and-ros-integrated).

#### Goals of ROS
- the primary goal of ROS is to support code _reuse_ in robotics research and development. ROS is a distributed framework of processes (aka _Nodes_) that enables executables to be individually designed and loosely coupled at runtime. These processes can be grouped into _Packages_ and _Stacks_, which can be easily shared and distributed. ROS also supports a federated system of code _Repositories_ that enable collaboration to be distributed as well. This design, from the filesystem level to the community level, enables independent decisions about development and implementation, but all can be brought together with ROS infrastructure tools.
- In support of this primary goal of sharing and collaboration, there are several other goals of the ROS framework:
	- Thin: ROS is designed to be as thin as possible -- we won't wrap your main() -- so that code written for ROS can be used with other robot software frameworks. A corollary to this is that ROS is easy to integrate with other robot software frameworks: ROS has already been integrated with OpenRAVE, Orocos, and Player.
	- ROS-agnostic libraries: the preferred development model is to write ROS-agnostic libraries with clean functional interfaces.
	- Language independence: the ROS framework is easy to implement in any modern programming language. We have already implemented it in [Python](http://wiki.ros.org/rospy), [C++](http://wiki.ros.org/roscpp), and [Lisp](http://wiki.ros.org/roslisp), and we have experimental libraries in Java and Lua.
	- Easy testing: ROS has a builtin unit/integration test framework called [rostest](http://wiki.ros.org/rostest) that makes it easy to bring up and tear down test fixtures.
	- Scaling: ROS is appropriate for large runtime systems and for large development processes.

#### Before and after ROS
- Before ROS
	- There was active development in robotics before the ROS project, but there was no common platform and community for developing robotics applications.
	- Each developer created software for their own robot, which, in most cases, couldn’t be reused for any other robot. Developers had to rewrite code from scratch for each robot, which takes a lot of time.
	- Also, most of the code was not actively maintained, so there was no support for the software. Also, developers needed to implement standard algorithms on their own, which took more time to prototype the robot.
- After ROS
	- Now there is a common platform for developing robotics applications.
	- It is free and open source for commercial and research purposes.
	- Off-the-shelf algorithms are readily available, so there is no longer a need to code.
	- There is big community support, which makes development easier.
- In short, the ROS project changed the face of robotics programming.

### When not to use ROS (yet)
- Where real-time performance is critical is required
- Although ROS has many options like Micro-ROS for embedded systems, but it still not good enough if you want tighter integration with hardware and optimised perfomance.

## Installation
- In this workshop we will use following softwares
	- Operating System: Ubuntu 20.04
	- ROS version: ROS Noetic
- Installation Link (ROS Noetic)
	- http://wiki.ros.org/noetic/Installation/Ubuntu
		- Note: install full package using  `sudo apt install ros-noetic-desktop-full`
- Other ROS versions and related OS requirements can be found here http://wiki.ros.org/Distributions

## ROS Basic Concepts
- Links: https://clearpathrobotics.com/blog/2014/01/how-to-guide-ros-101/

### ROS Architecture
- Basically, ROS is a framework to communicate between two programs or processes. For example, if program A wants to send data to program B, and B wants to send data to program A, we can easily implement it using ROS. So the question is whether we implement it using socket programming directly. Yes, we can, but if we build more and more programs, it gets complex, so ROS is a good choice for interprocess communication.
- Do we really need interprocess communication in a robot? Can weprogram a robot without it? The answer to the first question is explained in Figure
	- ![[Pasted image 20220726211111.png]]
	 
- A robot may have many sensors and actuators, as well as a computing unit. How can we control many actuators and process so much sensor data? Can we do it in a single program? Yes, but that is not a good way of doing it. The better way is we can write independent programs to handle sensor data and controlling actuators, and often, we may need to exchange data between these programs. This is the situation where we use ROS.
- So can we program a robot without ROS? Yes, but the complexity of software increases according to the number of actuators and sensors. Let’s see how the communication is happening between two programs in ROS.
	- Figure: ROS Communication block diagram
	- ![[Pasted image 20220726211156.png]]
	- Figure shows two programs marked as node 1 and node 2. When any of the programs start, a node communicates to a ROS program called the ROS master. The node sends all its information to the ROS master, including the type of data it sends or receives. The nodes that are sending a data are called publisher nodes, and the nodes that are receiving data are called subscriber nodes. The ROS master has all the publisher and subscriber information running on computers. If node 1 sends particular data called “A” and the same data is required by node 2, then the ROS master sends the information to the nodes so that they can communicate with each other. The ROS nodes can send different types of data to each other, which includes primitive data types such as integer, float, string, and so forth.
	- The different data types being sent are called ROS messages. With ROS messages, we can send data with a single data type or multiple data with different data types. These messages are sent through a message bus or path called ROS topics. Each topic has a name; for example, a topic named “chatter” sends a string message. When a ROS node publishes a topic, it sends a ROS topic with a ROS message, and it has data with the message type. In Figure 4-12, the ROS topic is publishing and subscribing node 1 and node 2. This process starts when the ROS master exchanges the node details to each other.
- Next, let’s go through some important concepts and terms that are used when working with ROS. They can be classified as three categories:
	- the ROS file system
	- ROS computation concepts
	- and the ROS community.
- In addition to the three levels of concepts, ROS also defines two types of [names](http://wiki.ros.org/Names) -- Package Resource Names and Graph Resource Names -- which are discussed below.

#### ROS File System
- The filesystem level concepts mainly cover ROS resources that you encounter on disk, such as:
	- **[Packages](http://wiki.ros.org/Packages)**: Packages are the main unit for organizing software in ROS. A package may contain ROS runtime processes (_nodes_), a ROS-dependent library, datasets, configuration files, or anything else that is usefully organized together. Packages are the most atomic build item and release item in ROS. Meaning that the most granular thing you can build and release is a package.
	- **[Metapackages](http://wiki.ros.org/Metapackages)**: Metapackages are specialized Packages which only serve to represent a group of related other packages. Most commonly metapackages are used as a backwards compatible place holder for converted [rosbuild](http://wiki.ros.org/rosbuild) [Stacks](http://wiki.ros.org/rosbuild/ROS/Concepts#Stacks).
	- **[Package Manifests](http://wiki.ros.org/catkin/package.xml)**: Manifests (package.xml) provide metadata about a package, including its name, version, description, license information, dependencies, and other meta information like exported packages. The package.xml package manifest is defined in [REP-0127](http://www.ros.org/reps/rep-0127.html).    
	- **Repositories**: A collection of packages which share a common VCS system. Packages which share a VCS share the same version and can be released together using the catkin release automation tool [bloom](http://wiki.ros.org/bloom). Often these repositories will map to converted [rosbuild](http://wiki.ros.org/rosbuild) [Stacks](http://wiki.ros.org/rosbuild/ROS/Concepts#Stacks). Repositories can also contain only one package.
	- **[Message (msg) types](http://wiki.ros.org/msg)**: Message descriptions, stored in my_package/msg/MyMessageType.msg, define the data structures for [messages](http://wiki.ros.org/Messages) sent in ROS.
	- **[Service (srv) types](http://wiki.ros.org/srv)**: Service descriptions, stored in my_package/srv/MyServiceType.srv, define the request and response data structures for [services](http://wiki.ros.org/Services) in ROS.

#### ROS Computational Graph
- The _Computation Graph_ is the peer-to-peer network of ROS processes that are processing data together. The basic Computation Graph concepts of ROS are _nodes_, _Master_, _Parameter Server_, _messages_, _services_, _topics_, and _bags_, all of which provide data to the Graph in different ways.
- These concepts are implemented in the [ros_comm](http://wiki.ros.org/ros_comm) repository.
	- **[Nodes](http://wiki.ros.org/Nodes)**: Nodes are processes that perform computation. ROS is designed to be modular at a fine-grained scale; a robot control system usually comprises many nodes. For example, one node controls a laser range-finder, one node controls the wheel motors, one node performs localization, one node performs path planning, one Node provides a graphical view of the system, and so on. A ROS node is written with the use of a ROS [client library](http://wiki.ros.org/Client%20Libraries), such as [roscpp](http://wiki.ros.org/roscpp) or [rospy](http://wiki.ros.org/rospy).
	- **[Master](http://wiki.ros.org/Master)**: The ROS Master provides name registration and lookup to the rest of the Computation Graph. Without the Master, nodes would not be able to find each other, exchange messages, or invoke services.
	- **[Parameter Server](http://wiki.ros.org/Parameter%20Server)**: The Parameter Server allows data to be stored by key in a central location. It is currently part of the Master.
	- **[Messages](http://wiki.ros.org/Messages)**: Nodes communicate with each other by passing [messages](http://wiki.ros.org/Messages). A message is simply a data structure, comprising typed fields. Standard primitive types (integer, floating point, boolean, etc.) are supported, as are arrays of primitive types. Messages can include arbitrarily nested structures and arrays (much like C structs).
	- **[Topics](http://wiki.ros.org/Topics)**: Messages are routed via a transport system with publish / subscribe semantics. A node sends out a message by _publishing_ it to a given [topic](http://wiki.ros.org/Topics). The topic is a [name](http://wiki.ros.org/Names) that is used to identify the content of the message. A node that is interested in a certain kind of data will _subscribe_ to the appropriate topic. There may be multiple concurrent publishers and subscribers for a single topic, and a single node may publish and/or subscribe to multiple topics. In general, publishers and subscribers are not aware of each others' existence. The idea is to decouple the production of information from its consumption. Logically, one can think of a topic as a strongly typed message bus. Each bus has a name, and anyone can connect to the bus to send or receive messages as long as they are the right type.
	- **[Services](http://wiki.ros.org/Services)**: The publish / subscribe model is a very flexible communication paradigm, but its many-to-many, one-way transport is not appropriate for request / reply interactions, which are often required in a distributed system. Request / reply is done via [services](http://wiki.ros.org/Services), which are defined by a pair of message structures: one for the request and one for the reply. A providing node offers a service under a [name](http://wiki.ros.org/Names) and a client uses the service by sending the request message and awaiting the reply. ROS client libraries generally present this interaction to the programmer as if it were a remote procedure call.	    
	- **[Bags](http://wiki.ros.org/Bags)**: Bags are a format for saving and playing back ROS message data. Bags are an important mechanism for storing data, such as sensor data, that can be difficult to collect but is necessary for developing and testing algorithms.

- The ROS [Master](http://wiki.ros.org/Master) acts as a nameservice in the ROS Computation Graph. It stores [topics](http://wiki.ros.org/Topics) and [services](http://wiki.ros.org/Services) registration information for ROS [nodes](http://wiki.ros.org/Nodes). Nodes communicate with the Master to report their registration information. As these nodes communicate with the Master, they can receive information about other registered nodes and make connections as appropriate. The Master will also make callbacks to these nodes when this registration information changes, which allows nodes to dynamically create connections as new nodes are run.
- Nodes connect to other nodes directly; the Master only provides lookup information, much like a DNS server. Nodes that subscribe to a topic will request connections from nodes that publish that topic, and will establish that connection over an agreed upon connection protocol. The most common protocol used in a ROS is called [TCPROS](http://wiki.ros.org/ROS/TCPROS), which uses standard TCP/IP sockets.
- This architecture allows for decoupled operation, where the [names](http://wiki.ros.org/Names) are the primary means by which larger and more complex systems can be built. Names have a very important role in ROS: nodes, topics, services, and parameters all have names. Every ROS [client library](http://wiki.ros.org/Client%20Libraries) supports [command-line remapping of names](http://wiki.ros.org/Remapping%20Arguments), which means a compiled program can be reconfigured at runtime to operate in a different Computation Graph topology.
- For example, to control a Hokuyo laser range-finder, we can start the [hokuyo_node](http://wiki.ros.org/hokuyo_node) driver, which talks to the laser and publishes [sensor_msgs/LaserScan](http://docs.ros.org/en/api/sensor_msgs/html/msg/LaserScan.html) messages on the scan topic. To process that data, we might write a node using [laser_filters](http://wiki.ros.org/laser_filters) that subscribes to messages on the scan topic. After subscription, our filter would automatically start receiving messages from the laser.
- Note how the two sides are decoupled. All the hokuyo_node node does is publish scans, without knowledge of whether anyone is subscribed. All the filter does is subscribe to scans, without knowledge of whether anyone is publishing them. The two nodes can be started, killed, and restarted, in any order, without inducing any error conditions.
- Later we might add another laser to our robot, so we need to reconfigure our system. All we need to do is _remap_ the names that are used. When we start our first hokuyo_node, we could tell it instead to remap scan to base_scan, and do the same with our filter node. Now, both of these nodes will communicate using the base_scan topic instead and not hear messages on the scan topic. Then we can just start another hokuyo_node for the new laser range finder.

	- ![[Pasted image 20220726212602.png]]
	- ![[Pasted image 20220726221928.png]]

#### ROS Community
- The ROS Community Level concepts are ROS resources that enable separate communities to exchange software and knowledge. These resources include:
	- **[Distributions](http://wiki.ros.org/Distributions)**: ROS Distributions are collections of versioned [stacks](http://wiki.ros.org/Stacks) that you can install. Distributions play a similar role to Linux distributions: they make it easier to install a collection of software, and they also maintain consistent versions across a set of software.
	- **[Repositories](http://wiki.ros.org/Repositories)**: ROS relies on a federated network of code repositories, where different institutions can develop and release their own robot software components.
	- **[The ROS Wiki](http://wiki.ros.org/Documentation)**: The ROS community Wiki is the main forum for documenting information about ROS. Anyone can sign up for an account and contribute their own documentation, provide corrections or updates, write tutorials, and more.
	- **Bug Ticket System**: Please see [Tickets](http://wiki.ros.org/Tickets) for information about file tickets.
	- **[Mailing Lists](http://wiki.ros.org/Mailing%20Lists)**: The [ros-users mailing list](http://wiki.ros.org/Mailing%20Lists) is the primary communication channel about new updates to ROS, as well as a forum to ask questions about ROS software.
	- **[ROS Answers](http://answers.ros.org)**: A Q&A site for answering your ROS-related questions.
	- **[Blog](http://www.ros.org/news)**: The [ros.org Blog](http://www.ros.org/news) provides regular updates, including photos and videos.

#### ROS Names
##### Graph Resource Names
- Graph Resource Names provide a hierarchical naming structure that is used for all resources in a ROS Computation Graph, such as [Nodes](http://wiki.ros.org/Nodes), [Parameters](http://wiki.ros.org/Parameter%20Server), [Topics](http://wiki.ros.org/Topics), and [Services](http://wiki.ros.org/Services). These names are very powerful in ROS and central to how larger and more complicated systems are composed in ROS, so it is critical to understand how these names work and how you can manipulate them.
- Before we describe names further, here are some example names:
	- / (the global namespace)
	- /foo
	- /stanford/robot/name
	- /wg/node1

- Graph Resource Names are an important mechanism in ROS for providing encapsulation. Each resource is defined within a namespace, which it may share with many other resources. In general, resources can _create_ resources within their namespace and they can _access_ resources within or above their own namespace. Connections can be made between resources in distinct namespaces, but this is generally done by integration code above both namespaces. This encapsulation isolates different portions of the system from accidentally grabbing the wrong named resource or globally hijacking names.
- Names are resolved relatively, so resources do not need to be aware of which namespace they are in. This simplifies programming as nodes that work together can be written as if they are all in the top-level namespace. When these Nodes are integrated into a larger system, they can be _pushed down_ into a namespace that defines their collection of code. For example, one could take a Stanford demo and a Willow Garage demo and merge them into a new demo with stanford and wg subgraphs. If both demos had a Node named 'camera', they would not conflict. Tools (e.g. graph visualization) as well as parameters (e.g. demo_name) that need to be visible to the entire graph can be created by top-level Nodes.
- **Valid Names**
	- A valid name has the following characteristics
		1. First character is an alpha character ([a-z|A-Z]), tilde (~) or forward slash (/)
		2. Subsequent characters can be alphanumeric ([0-9|a-z|A-Z]), underscores (_), or forward slashes (/)
	- Exception: base names (described below) cannot have forward slashes (/) or tildes (~) in them
- **Resolving**
	- There are four types of Graph Resource Names in ROS: _base_, _relative_, _global_, and _private_, which have the following syntax:
		- base
		- relative/name
		- /global/name
		- ~private/name
	- By default, resolution is done _relative_ to the node's namespace. For example, the node /wg/node1 has the namespace /wg, so the name node2 will resolve to /wg/node2.
	- Names with no namespace qualifiers whatsoever are _base_ names. Base names are actually a subclass of relative names and have the same resolution rules. Base names are most frequently used to initialize the node name.
	- Names that start with a "/" are _global_ -- they are considered fully resolved. Global names should be avoided as much as possible as they limit code portability.
	- Names that start with a "~" are _private_. They convert the node's name into a namespace. For example, node1 in namespace /wg/ has the private namespace /wg/node1. Private names are useful for passing parameters to a specific node via the parameter server.
	- Here are some name resolution examples:
		- ![[Pasted image 20220726213039.png]]

##### Remapping
- Any name within a ROS Node can be remapped when the Node is launched at the command-line. For more information on this feature, see [Remapping Arguments](http://wiki.ros.org/Remapping%20Arguments).

##### Package Resource Names
- Package Resource Names are used in ROS with Filesystem-Level concepts to simplify the process of referring to files and data types on disk. Package Resource Names are very simple: they are just the name of the [Package](http://wiki.ros.org/Packages) that the resource is in plus the name of the resource. For example, the name "std_msgs/String" refers to the "String" message type in the "std_msgs" Package.
- Some of the ROS-related files that may be referred to using Package Resource Names include:
	-   [Message (msg) types](http://wiki.ros.org/msg)
	-   [Service (srv) types](http://wiki.ros.org/srv)
	-   [Node types](http://wiki.ros.org/Nodes)
- Package Resource Names are very similar to file paths, except they are much shorter. This is due to the ability of ROS to locate Packages on disk and make additional assumptions about their contents. For example, Message descriptions are always stored in the msg subdirectory and have the .msg extension, so std_msgs/String is shorthand for path/to/std_msgs/msg/String.msg. Similarly, the Node type foo/bar is equivalent to searching for a file named bar in Package foo with executable permissions.
- **Valid Names**
	- Package Resource Names have strict naming rules as they are often used in auto-generated code. For this reason, a ROS [package](http://wiki.ros.org/Packages) cannot have special characters other than an underscore, and they must start with an alphabetical character. A valid name has the following characteristics:
		1.  First character is an alpha character ([a-z|A-Z])
		2.  Subsequent characters can be alphanumeric ([0-9|a-z|A-Z]), underscores (_) or a forward slash (/)
		3.  There is at most one forward slash ('/').

### ROS Tools
- Link: http://wiki.ros.org/Tools
#### ROS CLI Tools
- Link: http://wiki.ros.org/ROS/CommandLineTools
#### ROS GUI Tools: Rviz and Rqt
- RQT: http://wiki.ros.org/rqt_graph
- Rviz: http://wiki.ros.org/rviz
#### ROS Higher Level Concepts
- http://wiki.ros.org/ROS/Higher-Level%20Concepts
- Coordinate Frames/Transforms
- Actions/Tasks
- Message Ontology
	- The [common_msgs](http://wiki.ros.org/common_msgs) stack provide a base message ontology for robotic systems. It defines several classes of messages,
- Plugins
	- [pluginlib](http://wiki.ros.org/pluginlib) provides a library for dynamically loading libraries in C++ code.
- Filters
	- The [filters](http://wiki.ros.org/filters) package provides a C++ library for processing data using a sequence of filters.
- Robot Model
	- The [urdf](http://wiki.ros.org/urdf) package defines an XML format for representing a robot model and provides a C++ parser.
#### ROS Client Libraries
- A ROS client library is a collection of code that eases the job of the ROS programmer. It takes many of the [ROS concepts](http://wiki.ros.org/ROS/Overview) and makes them accessible via code. In general, these libraries let you write ROS [nodes](http://wiki.ros.org/Nodes), publish and subscribe to [topics](http://wiki.ros.org/Topics), write and call [services](http://wiki.ros.org/Services), and use the [Parameter Server](http://wiki.ros.org/Parameter%20Server). Such a library can be implemented in any programming language, though the current focus is on providing robust C++ and Python support.
- Main client libraries
	- [roscpp](http://wiki.ros.org/roscpp) : roscpp is a C++ client library for ROS. It is the most widely used ROS client library and is designed to be the high performance library for ROS.
	- [rospy](http://wiki.ros.org/rospy): rospy is the pure Python client library for ROS and is designed to provide the advantages of an object-oriented scripting language to ROS. The design of rospy favors implementation speed (i.e. developer time) over runtime performance so that algorithms can be quickly prototyped and tested within ROS. It is also ideal for non-critical-path code, such as configuration and initialization code. Many of the ROS tools are written in rospy to take advantage of the type introspection capabilities. The ROS Master, roslaunch, and other ros tools are developed in rospy, so Python is a core dependency of ROS.
	- [roslisp](http://wiki.ros.org/roslisp): roslisp is a client library for LISP and is currently being used for the development of planning libraries. It supports both standalone node creation and interactive use in a running ROS system.

### Cheatsheet
- Check out the [ROS cheatsheet](https://github.com/ros/cheatsheet/releases/).

# Hands-On
## Official Tutorials
- Link: http://wiki.ros.org/ROS/Tutorials
- Beginner Level
	- Set 1: Installation and Setup (Tutorial 1-4)
	- Set 2: Basic ROS concepts (Tutorial 5-10)
		- Node, Topic, Message, Service
	- Set 3: Programming yourself (Tutorial 12-18)
- Intermediate Level
	- Intermediate Level: Tutorial (1-5)
	- URDF: http://wiki.ros.org/urdf/Tutorials
	- TF: http://wiki.ros.org/tf/Tutorials
- Advanced:
	- Tutorial for Other ROS Libraries
		- Rviz: http://wiki.ros.org/visualization/Tutorials
		- Action (server-client): http://wiki.ros.org/actionlib_tutorials/Tutorials
		- Plugin: http://wiki.ros.org/pluginlib/Tutorials/Writing%20and%20Using%20a%20Simple%20Plugin
		- Navigation Stack: http://wiki.ros.org/navigation/Tutorials
		- ROS Industrial (for working with UR5 and other arms): http://wiki.ros.org/Industrial/Tutorials
		- Dynamixel Motor: http://wiki.ros.org/dynamixel_controllers/Tutorials
	- External
		- Point Cloud Library: http://wiki.ros.org/pcl/Tutorials
			- Also check Open3D: http://www.open3d.org/
- Other
	- Ros controllers
		- http://wiki.ros.org/ros_control
	- Gazebo
		- https://classic.gazebosim.org/tutorials

## Other
- Controlling UR5
- Controlling P3DX (remotely)
