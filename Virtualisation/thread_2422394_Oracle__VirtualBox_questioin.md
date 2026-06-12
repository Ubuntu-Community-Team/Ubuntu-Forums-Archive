---
title: "Oracle  VirtualBox questioin"
date: 2019-07-06
forum: Virtualisation
---

### Post by oilyfish on 2019-07-06
I have  18.04 on a machine.
I have a separate hard disk with Windows 7 64Bit on it
I have software on that drive that  runs on windows.
I have installed Oracle on my Ubuntu machine
I have one of those  Out board Drive handlers to USB that I can plug a Hard drive into  for back ups and such.
(1) Can I access that  as my Guest in Oracle VBox And  run The windows OS and the software 
or 
(2) must the Win OS be installed VIA the Oracle interface and then all the software  also installed in that  win OS?

---

### Post by TheFu on 2019-07-06
The normal way this works is there is a hostOS and a guestOS.
In your situation, the hostOS appears to be Ubuntu 18.04.

You would install virtualbox which is used to provide simulated hardware for different guestOSes to be installed onto.  If the simulated hardware isn't identical to the real hardware, then Windows will complain.  The guest OSes only see that simulated hardware, not the real hardware.  Windows doesn't like it when you change the motherboard, GPU, disk controllers and network adaptor(s) underneath it. That is what it looks like if you try to trick virtualbox into using a previously installed copy of Windows.

After you have installed Windows into the virtual machine GuestOS, then you would install software into that VM.  You can install Oracle DBMS, if you like or Oracle Discoverer or any other Oracle software - well, of the stuff that works on Windows and inside a virtual machine.
You do not have to use the fancy GUI to install Windows inside a virtual machine. There are multiple ways that don't use the hypervisor GUI.

When you say "Oracle", we can't which of the 500 different software products that Oracle makes you are writing about. Accurate, specific, details matter here. But most Windows software needs to be installed into the OS, so if anything about the OS is different, then it won't work.

I won't say you absolutely cannot do what you are dreaming. All sort of funky things are possible with Linux and virtual machines, but I will say that it will be an extremely steep effort for someone new to Unix/Linux and virtualization. You definitely will NOT be point-n-clicking this solution. I'd be surprised if it is possible in less than 60-100 separate, non-trivial, steps.

If this is your first time using a hypervisor, it is best to go the well-travelled path for a few months as you learn what does and doesn't work as you expect.

---

### Post by oilyfish on 2019-07-08
Thanks  for the reply.  Looks like I installing  inside the Oracle  Vbox
In this instance  "When you say "Oracle","  is  to be taken in the context of the post;  VirtualBox is the only oracle software  I'm referencing here.

---

