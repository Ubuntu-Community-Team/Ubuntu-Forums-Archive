---
title: "Virtualisation onto my 54-bit platform"
date: 2008-10-12
forum: Virtualisation
---

### Post by freakalad on 2008-10-12
I've come across numerous write-ups on the subject, but having trouble finding anything conclusive or comprehensive.

I run Hardy 8.04.1 64-bit LTS (fully patched) as my primary OS.
Pretty kick-*** hardware spec: 
Intel Quad Q6600 @ 2.40GHz
4GB RAM
etc, etc

Pretty stable thus far; now I have to start doing some serious virtualisation.
I know that most doc's "recommend" not doing VM's on a 64-bit machine, yet, but this does not resolve my issues, and hoping to put that behind me.

I'm running with 2 candidates: (took me a log time to get to this point)
* VMWare (currently v2), as this is the market-leader
* Xen (Source Community v3.3.0), as this will probably be the next big contender, since it's acquisition by Citrix, another market-leader, and as close as I'm willing to "chummy-up" with M$. It's GPL (*whoo-hoo*) & Citrix is pretty big in terminalisation

I've got a fair bit of experience with VMWare (even went as far as purchasing a Fusion licence way-back-when). Xen's pretty new to me, so my understanding's sketchy.

OK! That's all said & done.

Now....has anyone had success in setting up & configuring these systems, stability, on Hardy? If so, could you please assist me?

Any help would be appreciated

---

### Post by patrickballeux on 2008-10-12
Yes, I currently use Hardy 64 bits.

I use VMWare Server and VirtualBox.  Both are very stable and quite fast.  Nothing special was done to make them work (beside the installation of VMWare from the command line...)

I am setup on a Dell Inspiron 1521 and need those virtualized PC to run "Windows Server 2003 + SQL Server 2005" for testing installation procedure, and overall performance of our web application.

I use Ubuntu 64bits because of the cpu power available that I could not have with Vista 32 bits that came with my laptop.

So I use Ubuntu to run Windows... Yes, I know, it's strange... :)

My experience is great and flawless with VMWare and VirtualBox

---

### Post by freakalad on 2008-10-13
Yip. I get those results too

Managed to install VMWare Server v2 (the new "web-based" version) from source without much trouble, and was able to load my old VMWare VM's without much hassle.

But the performance-drain on my system is pretty hectic. This was an issue on the previous versions on various platforms as well, hence my need to look into other solutions.

Installed Qemu & VirtualBox OK on the system too. Seems to have gone down without a hitch, but more testing is needed in this area

Xen is the only one that is still outstanding & problematic. Still unable to find a resource to address this issue. (may just be missing something here?). Will dig around & post again if I find something

u have any luck?

---

### Post by freakalad on 2008-10-14
I'm trying to follow the instructions as put forward here:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

Problem is that this is starting to lag behind the current releases (Ubuntu standing @ Hardy 8.04.1 LTS, Ibex 8.10 will be here soon. Xen now @ v5)

The only portion I can comfortably execute on my 64-bit OS is:
[sudo aptitude install ubuntu-xen-server]
(hesitant about the desktop as of yet)

Also, started looking into the nitty-gritty in more detail, and it would seem that Citrix's acquisition of Xen is not honouring the GPL. Nowhere on Citrix.com is there mention of "GPL"; only "open"-buzzbord to move more "Enterprise Product". It would seem that the "XenServer Express" is the "free" (beer) counterpart to VMWare's server (am I correct here?).
I can live with that, but I'd like to know what I'm getting myself into

Am I missing something? Can someone please illuminate me?

---

### Post by freakalad on 2008-10-14
Found some more info here that seems to be a bit less bewildering:
[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

---

