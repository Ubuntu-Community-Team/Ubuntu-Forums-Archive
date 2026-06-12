---
title: "what does it mean when something comes 'from' the kernel"
date: 2021-07-30
forum: Ubuntu, Linux and OS Chat
---

### Post by jcdenton1995 on 2021-07-30
Hello all,

I'm wondering if someone can explain something for me in terms which are a little bit less abstract.

The info page for the udev daemon states:

***"The udev daemon, systemd-udevd.service(8), receives device uevents directly from the kernel whenever a device is added or removed from the system, or it changes its state"***

What does "from the kernel" mean in this context? My understanding is that the kernel is simply a collection of privelliged code which can interact directly with the system hardware, and acts as a middleman when userspace applications wish to access the system hardware.

That being said, does the phrase 'from the kernel' simply mean that a process who's code is compiled into the kernel, and operates in 'kernel space', notifies the udev daemon whenever a devices state changes, or is added / removed?

anyone with anything to add, please feel free to elaborate.

---

### Post by grahammechanical on 2021-07-31
The kernel interacts with the hardware. Any code that needs to know the state of the hardware must in turn interact with the kernel. Such code must get its data "from the kernel."

We put a USB stick into a USB port. We get a desktop notification; an icon appears in the dock and we can access the USB stick from the file manager. For these things to happen various bits of code have to interact with each other right down to code in the kernel reading the state of a USB port. 

Alternatively, it is all done by magic! :)  Sometimes, accepting that kind of "magic" is enough to allow me to do useful stuff with a computer.

Regards

---

### Post by garvinrick4 on 2021-08-04
At one time the linux kernel did not have all the drivers to run some hardware
as each new kernel came out more and more drivers where in the kernel.
We had to install linux drivers from the  manufacturer if they even had a linux driver.
With the kernels nowadays most all drivers are in kernel except a few holdouts.
Ubuntu is now so user friendly and a fantastic GUI. Easy to install and run with
many on Ubuntu forums to inform you on problems you run into. It all starts with the kernel and its drivers.

---

### Post by garvinrick4 on 2021-08-05
Read about Linus Torvalds he wrote the original code for Linux. It was suppose to be named Linus but
got confused and name Linux. It is open-source which means you can download the source code basically. At one
time 10,000 lines of code where added daily and 5000 removed he also was involved in Android. Companies such
as say the lottery use Microsoft with linux virtual machines running to servers.

---

