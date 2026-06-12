---
title: "VMware Workstation 8/VMware player 3.15 problems"
date: 2011-11-08
forum: Virtualisation
---

### Post by BobDull on 2011-11-08
Hello All,

First post here officially, I've been using Linux for about a year now, and I always find myself at the Ubuntu forums troubleshooting. Well, I've come across a problem that I can't find any good solutions to along the internet. So, here I am.

I am running Ubuntu 11.10

Kernel version 3.0.0-12.


First, I had been trying the free version of VMWare Workstation 8. Two things happen:

a) (vmware-installer.py:1757): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(repeats itself 3 times)

b) A dialog window pops up from VMWare Installer that says, "One or more of your processors does not have the necessary 64-bit extensions to run VMware virtual machines."

I am trying to run the i386 (32bit) version of this as well, so I don't know why its giving me an error about 64 bit.

[EDIT]: **Installation Requirements**

64-bit x86 CPU

[http://www.vmware.com/support/player40/doc/releasenotes_player40.html#Installation_Requirements](http://www.vmware.com/support/player40/doc/releasenotes_player40.html#Installation_Requirements)

*oops* Ok. anyone got any solution on the VMWare Player then?

------------------

Then I tried VMWare Player 3.15 because I heard maybe there was some compatibility with 4.0 and the new release of Ubuntu 11.10. Well, no avail there. I had a similar issue and went through a bunch of troubleshooting and tried the patch over at [http://reformedmusings.wordpress.com/2011/10/15/fixing-vmware-workstation-7-14-and-7-15-in-ubuntu-11-10-with-kernel-3-0-0-12/](http://reformedmusings.wordpress.com/2011/10/15/fixing-vmware-workstation-7-14-and-7-15-in-ubuntu-11-10-with-kernel-3-0-0-12/). 

-------------------

So now, I'm stuck with no VMware. And I can't figure out why I'm getting a bunch of GtK errors. Did I compile my GtK library wrong? What do I need to know? 

Thanks for educating me,
-Bob Dull

---

### Post by BillyBoa on 2011-11-08
I used to use VMware but in every Ubuntu update I was losing contact. Try Vbox which is simpler to follow the updates.

---

### Post by fjgaude on 2011-11-09
With Ubuntu 11.10 you have to use **Player 4.0**. VMware usually comes out with a new version just as Ubuntu makes a major change.

---

### Post by BobDull on 2011-11-15
Just a little side note: I was able to solve this problem. I had tried using VMWare Workstation 8, VMWare Player 3.15, VMWare Player 4.0, and was having the same problem across the board.

Finally I just uninstalled every instance I had of VMWare Player and re-installed, then followed the patching instructions I found online.

---

