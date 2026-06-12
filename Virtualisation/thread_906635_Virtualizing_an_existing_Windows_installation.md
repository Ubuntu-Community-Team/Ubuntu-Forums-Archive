---
title: "Virtualizing an existing Windows installation"
date: 2008-08-31
forum: Virtualisation
---

### Post by jvincent08 on 2008-08-31
I have Windows and Ubuntu on separate hard drives. I use Windows for gaming and Ubuntu for everything else. I'm aware that you can run Windows inside of Linux using virtualization software, but all of the guides talk about installing a fresh copy of Windows, rather than booting into an existing one from within Linux. I need to do this because I want to be able to directly boot into Windows when I want to play a game (or any app that doesn't run well in a virtual environment), but I also want to be able to access it from within Linux so I don't have to reboot to run a quick application. Is there a way to do this?

Thanks in advance.

---

### Post by Sand Lee on 2008-11-22
You can find a way to do this in the stickies, but it's not prefered as you'll have to reactivate windows every time you switch back and forth between virtual/native booting.

---

### Post by waydownsouth on 2008-11-24
Sand Lee,

to get around the reactivation I used the how to found here:

[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/]("http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/")

it works perfectly for me...

---

### Post by Sand Lee on 2008-11-24
> **waydownsouth said:**
> Sand Lee,

to get around the reactivation I used the how to found here:

[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

it works perfectly for me...

Are you using SP3? I actually used that howto to make mine initially, but since it stopped working after SP3, I decided to remove it. If you look at the bottom of the wordpress page, you'll see people using SP3 who didn't get the tutorial to work. Thanks.

---

### Post by waydownsouth on 2008-11-24
yep, XP Pro SP3,

running on Vmware server 2 with the Vmware tools installed in XP...

---

### Post by Sand Lee on 2008-11-24
Hmm, that's odd. It probably doesn't matter the VM, but unless this method is reconfirmed to work with VirtualBox, more than once, I don't think I'll go through the trouble of re-including it into the tutorial.. I might make the link to that tutorial more obvious however (it's there already).

---

### Post by waydownsouth on 2008-11-24
Ahh, 
thats probably where I got the link from to begin with... 

Sorry, my bad.

I initially used Virtualbox using your how to, but switched to VMware server 1.07 which doesn't seem to max out one of the cpu cores as I experienced with Virtualbox.
I also heeded your warnings about not installing the vbox tools, but, the VMware ones installed and have given no issues when booting natively.

After the upgrade to Intrepid, VMware stopped working so I installed VMware server 2.0 which recognized the previous vm and all is working perfectly after I did the workaround on that link.

---

### Post by wirporte on 2008-12-03
I have used VMWare Server and VMWare Converter in the past with success.  There is a lot of documentation concerning the install and usage.  Basically, install VMWare converter on your physical Windows computer and convert (I saved the resulting files to an external hard drive).  Then open the converted Virtual Machine in VMware Server, and there is your previous physical computer running virtually.  I formatted my previous physical computers, so I am not sure how the two versions will interact with upgrades and concerns of that nature.  Good luck.

---

