---
title: "Booting Windows in VMware server"
date: 2008-04-04
forum: Virtualisation
---

### Post by Perk on 2008-04-04
Hello, I'm having problems with VMware Server. I have installed VMware Server on my Ubuntu machine, and I want to boot into my Windows XP partition on my physical disk. 

I've successfully installed VMware server, and I set the settings to boot from my physical disk. I run the virtual machine, I select my Window's partition, and I see the Window's logo come up. But then, after the logo disappears, it is replaced by a BSOD. What happened?

Here is what it says:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

---

### Post by andydread on 2008-04-04
sound like windows is having problems accessing the disk once it boots.  Possibly a problem with windows not having the proper driver installed to access the disk through the vmware disk controller.  Try booting to your windows and installing vmware tools in your windows partition, run chkdsk /f then boot back into ubuntu and try it.

---

### Post by fjgaude on 2008-04-04
I could be dead wrong but I've never heard of anyone doing what you wish to do.

Normally once the vmware server is installed, you install Windows in it, from the original Windows install disk.

There is a converter that converts an installing Win install that is on the vmware.com site, but few have found it a good option.

Please, anyone, let us know what you think of what is trying to be done.

---

### Post by andydread on 2008-04-04
It looks like he got it to boot.  The windows logo came up and windows started to load.  But if it cant load the disk controller driver for vmware then it will not be able to access the partition and will blue screen with the error message he is getting.    This is the same thing that happens when u switch motheboards and windows doesn't have the new driver for the new motherboard pre-installed.   I suspect installing the vmware tools into windows will install the driver for the virtual disk controller then windows. should be able to access the disk.

---

### Post by Perk on 2008-04-04
How do I install the tools for windows? According to here:
[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_windows.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_windows.html)

It says I have to use VMware to boot my OS and install the tools there
(there's an option in the menu bar). But I can't do that because BSOD always appears. Is there a separate set of tools that I can download so that I can just boot into my windows through the physical drive and install from there?

---

### Post by timestryder on 2008-04-07
I am having the same exact issue, though this guide was supposed to fix it: [http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

It says to change your IDE controller to the standard, and make sure the virtual controller stays on Buslogic. It made sense to me, but I still get the BSOD on startup, right after the windows logo.

Thanks.

---

