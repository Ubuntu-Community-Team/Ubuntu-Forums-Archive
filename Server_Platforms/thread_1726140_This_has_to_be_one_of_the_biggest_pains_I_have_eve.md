---
title: "This has to be one of the biggest pains I have ever experienced!!!"
date: 2011-04-10
forum: Server Platforms
---

### Post by pepsifx357 on 2011-04-10
Ok, I still haven't calmed down yet, so please be understanding of my frustration.

I'm trying to get my work's infrastructure built at home before I go up there and show the boss.  It is as follows:

VMware esxi installed on the server with:

Windows server 2008
Ubuntu 10.04 server

I've got VMware installed.  And I have spent the past 7 hours trying to figure out how to manage it.

I found out that vsphere has not nor will ever be supported for Linux; which was my first problem.  

Second Problem

So I had to dig around for a spare Windows 7 dvd.  To my UN-surprise it blue screened before it even got to the Windows installer.

Third Problem

So I dug around for my Windows XP disc.  Wouldn't find my sata hard drive and I wasn't about to dig around for a floppy drive and disk, in order to install it.

Fourth Problem

I remembered that I had a dual boot of Windows 7 downstairs and proceeded to download and install vsphere.  It wouldn't install because of some updates that needed to be installed.  I installed them and got vsphere installed as well.  However upon connecting to my vmware esxi, there was yet another error that had to do with some update.  I found out that the error had been existent since 2009 and for some reason NO ONE at VMware has fixed it.

Fifth Problem

So as frustrated as I was six hours later, I went back to my Ubuntu machine and proceeded to install the vsphere CLI.  Guess what?  Didn't work.  Some kind of perl error, that again, has been existent for a while now and no one has fixed it.

So what have I accomplished today?  I installed Vmware esxi.  Thats it.  No guest OSs nothing else, just that.

So what are my options?  Do I:

A. Try another VM host such as Xen?  I don't have a server with         VT tech so I can't use KVM.

B. Quit my job and sit at home.

C. Take a picture of Bill Gates and Paul Maritz, tie them to a tree and use them for target practice?


Seriously, I have no Idea what to do at this point.  I've run out of computers, OSs, and patience.

---

### Post by rubylaser on 2011-04-10
I use Proxmox.  It works great, is open source, and supports both full and paravirtualization.
[http://www.proxmox.com/products/proxmox-ve]("http://www.proxmox.com/products/proxmox-ve")

Even without VT hardware, OpenVZ will work great as long as your processor is a 64 bit version.

---

### Post by conradin on 2011-04-10
vmware for your second issue converts actual OS installations (bootable hard drives) to disk images, it can be freely downloaded.
Or you could use virtual box to make a similar virtual machine. Im guessing here, but you're not just installing w7, but a bunch of other software on the Virtual Machine, to make a rough clone of your workplace architecture. 

It might be helpful to us unpaid - ueber Patience techs to get actual error logs  than vague reports of errors. 

My guessing aside, Im not clear on what is going down for you. It sounds like you want a whole bunch of virtual machines, and a computer to run them, but the installs aren't going so well is this correct?

what might be helpfull for us to know is what version of ubuntu are you running? And What are your hardware specs? And, do you intend on running any crazy peripherial / proprietary hardware from your geust OSes once they are installed?

I have a ISA slot spectrometer for example which my XP guest OS has no idea how to handle.

Also, are you doing any graphics intensive work via your guest OSes?
Give us detail on what you're trying to do and perhaps we can help.

---

### Post by pepsifx357 on 2011-04-10
> **conradin said:**
> vmware for your second issue converts actual OS installations (bootable hard drives) to disk images, it can be freely downloaded.
Or you could use virtual box to make a similar virtual machine. Im guessing here, but you're not just installing w7, but a bunch of other software on the Virtual Machine, to make a rough clone of your workplace architecture. 

It might be helpful to us unpaid - ueber Patience techs to get actual error logs  than vague reports of errors. 

My guessing aside, Im not clear on what is going down for you. It sounds like you want a whole bunch of virtual machines, and a computer to run them, but the installs aren't going so well is this correct?

what might be helpfull for us to know is what version of ubuntu are you running? And What are your hardware specs? And, do you intend on running any crazy peripherial / proprietary hardware from your geust OSes once they are installed?

I have a ISA slot spectrometer for example which my XP guest OS has no idea how to handle.

Also, are you doing any graphics intensive work via your guest OSes?
Give us detail on what you're trying to do and perhaps we can help.

The actual server for work, that I am creating here at home first, is just Windows Server 2008 and Ubuntu 10.04 Server running together in VMware ESXi.  That's pretty much it.  However, to manage ESX or ESXi you have to have vsphere, which is only available for windows.  So, I have to have a separate computer with Windows on it to manage the server, basically until the OSs are installed and running.  Then I can just Remote into them using what ever I want.

I've decided to try something and install Ubuntu server 64bit and install Windows server 2008 inside it using somehing like qemu.I've 

I'm going to check out ProxMox.  Downloading now.

---

### Post by BkkBonanza on 2011-04-11
I'd highly recommend VirtualBox. I've used it painlessly for years and it supports remote control and is a breeze to install. It has a control panel included. I've run several versions of Windows and different Linux installs and never had any frustrations getting them to work. Since it's worked so well I never explored VMWare at all.

I've generally always worked by mounting a system ISO image in the new machine and booting that way, rather than using physical media.

---

