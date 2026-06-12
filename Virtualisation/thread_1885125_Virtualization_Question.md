---
title: "Virtualization Question"
date: 2011-11-22
forum: Virtualisation
---

### Post by lionel.raphael on 2011-11-22
I am new to virtualization and working on   putting an Internal Virtualization plan in place. I will greatly appreciate   if you could help me understand under what circumstances is VMWare   Virtualization and/or RHEV and/or Xen and/or Microsoft Hyper V better over   the rest. Also, is it reasonable to assume, all that needs to be virtualized   on VMware has already occurred. Thanks for your help

---

### Post by jerrrys on 2011-11-24
A good way to search the Ubuntu-Forum is googlubuntu.  I use VirtualBox myself.  It does not require a template and can take multiple snapshots (as compared to VMware).

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Virtualization&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Virtualization&sa=Search&cof=FORID:9)

---

### Post by Old_Grey_Wolf on 2011-11-24
Is your intent to use virtualization for your home or is it for a business? Do you have budget constraints?

Also, what operating system(s) are you currently using?

Do you intend to virtualize infrastructure; such as, DNS, Active Directory, LDAP, and so forth?

Just some things that need to be considered.

Please explain what you mean by "all that needs to be virtualized on VMware has already occurred".

---

### Post by Iosonos on 2011-11-29
I have only some superficial experience with VMWare, Hyper-V I use on a daily basis, and Xen I've yet to play with.
 
As others mentioned it entirely depends upon what you currently have in place, and whether this is for personal or business.  If it's for business, let us know more about the specs and we can go from there.
 
As for home, a couple suggestions.  If you want to play around with Hyper-V, Win8 beta I believe does have it integrated; this means that you can play around with the system without having to resort to getting a full OS.  VMWare also provides licenses for their VMWare Desktop for free, although I do not know if this has support for VT-x or AMD-V technologies.
 
Limitations on Hyper-V: It's Windows Server only: it can only be installed on Server 2008 or higher (Win8 is the only desktop OS to support it), the PC has to be x64 with hardware virtualization support.  You will also have to recreate the Virtual Machine (the VHD will be fine) every time you want to switch it between dissimilar hardware, so having a copy of all settings on hand is a good idea.  Also, although Virtual PC and Virtual Server 2005 use the same extensions as Hyper-V, there's only limited compatibility.  I believe you can transfer the vhd to Hyper-V, but as soon as you install guest additions it will not work in the older virtual software anymore.  Just something to keep in mind, it's better to keep all Hyper-V in Hyper-V.
 
What I know on VMWare:  Multi-platform, if you use desktop, I don't think it supports hardware virtualization.  It also has some compatibility with Hyper-V via a VHD converter tool.  I believe the images made on desktop can be interchanged with the server software without issue.  Other than that, Hyper-V does come with free remote administration tools, VMWare I'm not so sure on.
 
Hope this helps you some.

---

