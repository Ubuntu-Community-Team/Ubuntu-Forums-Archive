---
title: "turning the desktop on and off"
date: 2009-05-19
forum: Server Platforms
---

### Post by fenixbtc on 2009-05-19
i'm pretty new to linux in general, i had installed 9.04 server on an older x86 machine and added in the desktop package and have found it to be buggy at times.

is there a way that i can have the desktop installed, but by default boot to the CLI and from there start up the desktop if i would like to, and shut down the GUI and return straight back to the CLI.....all without any rebooting?

at some point i want to be able to have virtual machines on there and access them remotely over the internet such as a RDP. in order to run the GUI stuff remotely, does the desktop have to be running and active on the server or can i still be in a strictly CLI mode?

would i be correct to assume that vmware and vbox work equally well in gnome, kde and xfce? i thought i would give xfce a try since i haven't yet, and being a 'server' on an older machine i figure the lighter weight would be more beneficial.

---

### Post by windependence on 2009-05-19
You certainly could boot into what we in the RedHat world call run level 3 and then do the startkde command or startx.

My suggestion: Do the desktop version and become familiar with the distribution and the CLI, then when you are comfortable, switch to the server version. You need to ween yourself off of that GUI crutch if you wanna run full blown servers at maximum efficiency.

You may be unaware that you don't need to run your virtualization software on top of an operating system. VMware makes ESXi, which is free and runs right directly on the hardware. This is the fastest way to run your VMs and takes the least resources. 

Personally, I think if you are gonna insist on using VMware server or Virtual Box to run on top of Ubuntu, you are going to find that configuring networking on VMware will be much easier than VBox. They are both about as fast, but again, a bare metal hypervisor is much better.

-Tim

---

### Post by fenixbtc on 2009-05-19
thank you Tim, i have seen your replies on various other threads and you have always appeared very knowledgeable.

i have my laptop set up to a dual boot with one being jaunty 64bit. so i am learning my way around the gui there.

one of those threads was on virtualization and i believe you covered some of how amazing ESXI was. i can't recall, but would that allow me to essentially have desktop control over them such as an RDP or vnc? (don't yet entirely know the details of vnc but at least from a short description of it i've seen it looks like something i want to try out.) also, the machine that will currently serve as the server has a chip that was before HW virtualization, isn't that a requirement for ESXI or am i thinking of another hypervisor or KVM or something?

---

