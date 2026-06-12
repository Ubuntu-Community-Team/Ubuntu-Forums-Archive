---
title: "cpu virtualisation function"
date: 2013-08-29
forum: Virtualisation
---

### Post by mastablasta on 2013-08-29
so i was testing turnkey linux (preconfigured debian). and preinstalled options (for example WordpressTurnkey) come with 64bit images that require CPU virtualisaiton funciton to be enabled. I wonder why is it disabled by default? and my netbook even specificly says in BIOS that HP advises to leave this option disabled unless using specialised software. why would it matter if it is enabled (and for exmaple you are not using virtualisation software)? is there a security risk? is there an extra power drain? does is damage the CPU more over time? does it overheat it in normal use or what? 

ok this is maybe more of a hardware question but i am hoping someone here perhaps already knows the answer to this.

otherwise a very good idea this tunr key. easy to use and setup for some development in virtual environment.

---

### Post by TheFu on 2013-08-29
Don't know anything about your hardware, but enabling unused features is **against security best practices.** Added complexity almost always means less security. On laptops, more features often translates into lower battery life, so it should be avoided. On a netbook, these things are even more important.

When you use someone elses installation, as you do with any app-appliance like Turnkey, you are completely trusting that provider to do no harm, not leak any data, not install any back doors, tracking, or other software you don't want.  For many people, that trust is no a concern.  For others, it is so much a concern that it isn't worth any consideration.

Each person and organization will need to decide for themselves where they draw the line.  For example, it is against IT policy were I work to use 3rd party services to host any of our proprietary or customer data. To do that, the Board of Directors must meet, vote and agree for each specific 3rd party service. **They rejected Dropbox** and I had to put in blocking on our network to prevent end-user devices from accessing it.  We already block github, other source control, and many, many other websites. Sometimes it has been a hassle, but we are small, nimble, flexible.  I like to think our users don't bypass these controls.

BTW, I looked at the Turnkey wordpress webpage - looks like there is a non-VM version available (the ISO link). Is that the version you have?

---

### Post by tgalati4 on 2013-08-29
Efficient virtualization requires that your CPU support it by design (several Intel and AMD processors have it built in) and the motherboard chipset (memory and data bus) support it.  So, yes, turning it on will use more power, and as TheFu suggests might open up vulnerabilities.  To enable the motherboard portion requires turning on the BIOS switches.  To activate the CPU part requires kernel boot switches to be set.  

It's hard to imagine a use case of virtualization on a netbook, but if you have the capability, no harm in playing with it.  The manufacturer wants it turned off to reduce support calls.  That costs them money.

As far as your wordpress stack, I would use the non-VM version on a netbook.

---

### Post by mastablasta on 2013-08-30
i went to their page again and dug a bit more and i've found the i386 iso. the only reaosn i would need virtualisation on is to be able to run 64 bit OS. if it's 32 bit then this funciton is not necessary, so i think i might install the iso on disk.

if it's a power drain (even when you do not use virtualbox) and if this CPU feature is also a security risk then perhaps it is better to disable this feature in BIOS.

the netbook is not a typical one. since at the time most had Atoms with poor linux GPU support. So i took this one wiht AMD e-450 (1.6Ghz dual core). AMD unlike Atom uses a bit more power but can also handle more RAM. it is also a 64 bit CPU. at the moment i have 2 GB with one slot free and i plan to add at least 4 GB to it (if not exchange it for 2 x 4GB). 2GB in linux is a lot and for setting up a virtual LAMP server with single user you really don't need that much.

anyway as for turnkey - i don't think they have any sinister intentions. besides this server is locked in the vbox and can't reach outside my computer. well at least it shouldn't be able to as per network settings.

why is the WM version bad idea for a netbook?


edit: just in case someone else is following this i've now found some interesting info:
i found some more info on this. wiki says the following are the cons:
> 
Hardware-assisted virtualization requires explicit support in the host CPU, which is not available on all x86/x86_64 processors.

not an issue as CPU can support it.
> 
A "pure" hardware-assisted virtualization approach, using entirely unmodified guest operating systems, involves many VM traps, and thus high CPU overheads, limiting scalability and the efficiency of server consolidation.[4] This performance hit can be mitigated by the use of paravirtualized drivers; the combination has been called "hybrid virtualization".[5]

Not an issue since paravirtualized driversthey were included in kernel since Ubuntu 7.04. though pehraps it could be an issue on the other side of dualboot (=win7 starter). it seems Oracle provides them for windows. 
> 
In 2006 first-generation 32- and 64-bit x86 hardware support was found rarely to offer performance advantages over software virtualization

this could be an issue for my old Athlon64

---

### Post by tgalati4 on 2013-08-30
A netbook doesn't have the throughput on the databus to handle heavy VM loads compared to dedicated server hardware.  So, although you can play with VM's on a netbook, they might not scale up in a production environment.  *One test is worth a thousand expert opinions.*

---

