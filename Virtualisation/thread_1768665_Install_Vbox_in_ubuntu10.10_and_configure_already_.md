---
title: "Install Vbox in ubuntu10.10 and configure already installed XP"
date: 2011-05-27
forum: Virtualisation
---

### Post by DMuindi on 2011-05-27
Hi Experts,

Am a new user to ubuntu 10.10. I have a compaq Laptop with three XP partitions and 1 Ubuntu partition. (only 1 HDD)

Is there a way i can install vbox and then access my already installed XP applications ?

The only docs/posts i see is installing a new XP installation...:(

Regards

---

### Post by TheFr00n on 2011-05-28
The short answer is no. In general, you will not be able to run software that is already installed on your XP partitions directly - for the same obvious reasons that Mac software won't run on XP.

But all is not lost - there are many possible ways forward, although nearly all will involve installing some form of VM. Also note that you can already access the data on the XP partitions - you just can't run the software. So if it's a case of just needing to read data, you're already there. 

You don't mention what software you want to run, either. There are many excellent open source equivalents for Windows software available in Ubuntu - for example, OpenOffice is a good equivalent for Microsoft Office. GIMP is a good equivalent for Photoshop - and so on.

Now, a lot of XP software will run quite well under Ubuntu using WINE - install it via the Ubuntu Software Center. It is basically a re-implementation of XP under Ubuntu, and is quite advanced. 

Depending on the complexity of the software you want to run, it may even be possible just to right click on the EXE files in your XP partition and run them with WINE - but you also shouldn't hold your breath. If the software uses copy protection or reg keys, it will most likely not run this way. The next thing to try is to install the software properly, using WINE and the desired app's installer. Depending on the app, there is a good chance that this will work - the WINE website keeps a list of all apps that are known to run this way, it's worth doing a little homework before you start.

If that's not going to work, you will need some form of virtualisation software like VirtualBox. Basically, it's a sandbox that you install a copy of XP into. Think of it like Pimp My Ride - Yo dog we herd u like XP and Ubuntu so we installed XP in ur Ubuntu so you can XP while you Ubuntu.

If you go this route, you will have a full version of XP running in box inside Ubuntu. Configured properly, it will be able to see all your old XP partitions, although you may still have to reinstall your XP apps inside it because of the keys issue. It will be slower than running XP natively, but the upside is that you don't have to dual boot.

And then there's always the possibility of just dual-booting. I use FL Studio a lot, for example, and I maintain an XP partition just for it. I can get it to run under WINE, but it has weird bugs running like that, so when I want to use FL, I just reboot the machine into Windows. No big deal.

Hope that helps you.

---

