---
title: "Genode Live CD Runs Linux Kernel as Browser Plugin"
date: 2010-11-20
forum: The Cafe
---

### Post by mmix on 2010-11-20
Genode os

[quote="[nfeske](http://www.osnews.com/story/24039/Genode_Live_CD_Runs_Linux_Kernel_as_Browser_Plugin)"]
The Genode project has released a bootable live CD showcasing the capabilities of their OS-construction framework. It boots in less than 10 seconds (on VirtualBox) to a fully functional graphical user interface featuring a selection of five subsystems (screenshot). Each subsystem demonstrates different aspects of the framework. One of the highlights is a web browser that is executed natively on the microkernel and is able to run a sandboxed Linux kernel as browser plugin. Among the other demos are the famous Gears OpenGL demo showing Gallium3D in action, and a user-level Linux seamlessly integrated into the system.

The previous live CD released in autumn 2009 was published to highlight Genode's capability to support not only a single but a range of kernels as base platform. (currently, the framework is available for 6 different kernel platforms) Apart from a general introduction, however, no real-world workload was presented. Since then, the project has come a long way, vastly improving the functionality of the framework. To name a few examples, during the last year, the project introduced support for real-time priorities, a virtualized Linux kernel, sound support, Mesa/Gallium3D, block drivers, a networking stack, and Qt4/Webkit. The great challenge for the new live CD was the integration of all these features into a single coherent setup, allowing the user to dynamically start and stop different subsystems.

Device-driver-wise, the live CD comprises a range of drivers such as USB HID, PS/2, VESA, Intel-GEM, E1000, audio output, and ATAPI - each of them operating as separate user-level process, communicating with the rest of the system via inter-process communication. Some of them are Genode-specific, some are ported from Linux, others are ported from the gPXE project. For the kernel, the live CD relies the OKL4 v2 microkernel.

Regarding the technical demos, special attention was paid to the tight integration of existing software with native Genode features. For example, the presented virtualized Linux runs seamlessly integrated with Genode's native Nitpicker GUI, it can play sound using Genode's audio mixer, and access the network via a bridging component. The most sophisticated showcase is certainly the port of the Webkit-based Arora web browser - but with a special twist. Using a custom plugin implementation, it has become possible to run fully-featured Genode subsystems as browser plugin in a secure way. This is even possible for a complete Linux system, which can actually make use of Genode's user-level device-driver capabilities by employing a custom block-device driver that fetches a disk image via HTTP from a web server.

For the project, the current live CD is an especially important milestone as it demonstrates the scalability of Genode's architecture beyond static special-purpose setups. It gives a glimpse of what will become possible when Genode develops towards a general-purpose operating system.

To give the live CD a quick spin, the project recommends VirtualBox. Further instructions are provided at the live-CD website.
[/quote]

---

