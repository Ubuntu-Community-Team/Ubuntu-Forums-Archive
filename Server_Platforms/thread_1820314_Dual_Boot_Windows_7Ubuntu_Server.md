---
title: "Dual Boot Windows 7/Ubuntu Server"
date: 2011-08-07
forum: Server Platforms
---

### Post by tjmedsker on 2011-08-07
I would like to start off apologizing for my ignorance to ubuntu.  I am in the long process of making a switch over to linux, away from windows.  In the meantime I am using Windows 7.  I would like to know how to do the following:

Dual Boot Windows 7/Ubuntu Server 11.04
Install an interface in Ubuntu Server (so it looks like regular Ubuntu OS)
Continue to keep my Ubuntu Server up and running will working in Windows 7

I know this is possible to do, I just want to do it right the first time as I just got done setting up Windows 7 programs, etc., and do not want to have to reformat and do it over.  I plan on serving a couple of websites from my new computer.  As a bonus :D, I know there is free websites that will allow you to host from ubuntu server, using a non-static ip...any good suggestions?

I greatly appreciate any help I can get.

Thanks,

Tim

---

### Post by drdos2006 on 2011-08-07
When you dual boot, only one operating system is running at a time. Either Windows or Linux, not both.
To run run Windows and Linux at the same time I run linux, virtualbox from Oracle, then run the Windows OS on top of linux through virtualbox. Both operating systems can then run at the same time.

regards

---

### Post by haqking on 2011-08-07
> **tjmedsker said:**
> I would like to start off apologizing for my ignorance to ubuntu.  I am in the long process of making a switch over to linux, away from windows.  In the meantime I am using Windows 7.  I would like to know how to do the following:

Dual Boot Windows 7/Ubuntu Server 11.04
Install an interface in Ubuntu Server (so it looks like regular Ubuntu OS)
Continue to keep my Ubuntu Server up and running will working in Windows 7

I know this is possible to do, I just want to do it right the first time as I just got done setting up Windows 7 programs, etc., and do not want to have to reformat and do it over.  I plan on serving a couple of websites from my new computer.  As a bonus :D, I know there is free websites that will allow you to host from ubuntu server, using a non-static ip...any good suggestions?

I greatly appreciate any help I can get.

Thanks,

Tim

first thing i notice is that you have 2 different types of OS, a server and a Desktop OS ?

So they are designed for different functionality, you say moving over to linux from windows 7 then you would move to ubuntu desktop edition not a server edition.

However if you really want a dekstop interface (i presume you mean gui) then in server you can:

sudo apt-get install ubuntu-desktop

however a GUI is not recommended for a server as is why it comes without one.

If you want them both running at the same time you cannot dual boot.

I would recommend looking a virtual box or wmware to virtualise the OS of choice within your preferred working environment.

example:

windows 7 host running virtual box or vmware with ubuntu server running as a virtual machine

---

### Post by tjmedsker on 2011-08-07
Thanks for the replies...couple questions?

1.) Why is a GUI interface not recommended?

2.) Pardon my ignorance, if I run Ubuntu Server in vmware, then I can host a website while using Windows 7?  I had heard there was some program that allowed you to run Windows 7 with an add/remove program...keeping the same files as are in the Ubuntu server, so that when you are working in W7, you still have your website up and running.  

I really want a interface because I will be using this computer for more than just serving a website...so perhaps a virtual OS is the way to go?

Still a little confused.

Thanks,

Tim

---

### Post by arrrghhh on 2011-08-07
> **tjmedsker said:**
> Thanks for the replies...couple questions?

1.) Why is a GUI interface not recommended?

2.) Pardon my ignorance, if I run Ubuntu Server in vmware, then I can host a website while using Windows 7?  I had heard there was some program that allowed you to run Windows 7 with an add/remove program...keeping the same files as are in the Ubuntu server, so that when you are working in W7, you still have your website up and running.  

I really want a interface because I will be using this computer for more than just serving a website...so perhaps a virtual OS is the way to go?

Still a little confused.

Thanks,

Tim

Everything you can run on an Ubuntu Server install can also be run on an Ubuntu Desktop install.  It sounds like you really want a GUI, so why use Ubuntu Server at all...?

As far as your other question, yes you can run Ubuntu as a VM under Windows, and have Ubuntu serving your webpage while Windows still works just as it did.  The only caveat/warning I'll give you is resources - your host machine will have to be pretty beefy to run two (or more) operating systems at the same time.  If your website gets a lot of traffic, you'll also want to make sure the VM is scaled with enough resources to handle the load...

---

### Post by YesWeCan on 2011-08-07
> **tjmedsker said:**
> 1.) Why is a GUI interface not recommended?
Probably because it consumes a lot of resources to run a GUI and a server is normally run "headless" - connecting machines use their own GUIs. You could install a less hungry GUI than Gnome.

> 2.) Pardon my ignorance, if I run Ubuntu Server in vmware, then I can host a website while using Windows 7?  I had heard there was some program that allowed you to run Windows 7 with an add/remove program...keeping the same files as are in the Ubuntu server, so that when you are working in W7, you still have your website up and running.
For being able to run both OSs concurrently, for best performance I imagine VMWare is best. VMWare is the host OS and Windows and Ubuntu would both be hosted by it.

VirtualBox is very good but it is not an OS and needs to be hosted itself. Whether you host W7 on Ubuntu or Ubuntu on W7 may not matter too much although I consider Ubuntu faster and more reliable than W7 and so may make a better host. BTW VirtualBox will run headless and you can access its guest's GUI by remote desktop.

---

### Post by tjmedsker on 2011-08-08
Okay I found the software that allows you to run a Ubuntu server while in windows:

[http://www.wampserver.com/en/](http://www.wampserver.com/en/)

Still I am scratching my head at how to setup the Ubuntu server.  Using this software would I download regular Ubuntu OS or Ubuntu Server?  As I said earlier, I do not want to have to reformat.  My computer can handle the load, I am running a Sandy Bridge processor with 16 GB of ram.

Tim

---

### Post by arrrghhh on 2011-08-08
> **tjmedsker said:**
> Okay I found the software that allows you to run a Ubuntu server while in windows:

[http://www.wampserver.com/en/](http://www.wampserver.com/en/)

Still I am scratching my head at how to setup the Ubuntu server.  Using this software would I download regular Ubuntu OS or Ubuntu Server?  As I said earlier, I do not want to have to reformat.  My computer can handle the load, I am running a Sandy Bridge processor with 16 GB of ram.

Tim

Why not just use VirtualBox?  Seems simpler... I've never heard of this WAMP server... if you think that's better, then have at it!

---

### Post by ingeva on 2011-08-08
> **arrrghhh said:**
> Why not just use VirtualBox?  Seems simpler... I've never heard of this WAMP server... if you think that's better, then have at it!
All in all I would recommend to run a dual-boot system. To achieve this, I would use Windows to reduce the size of its partitions to make room for at least 3 new partitions: Boot/root, SWAP and user. You COULD do that from the Ubuntu installation CD, but in this case (and ONLY in this case!) I actually trust Windows to do a better job!
The advantage of separating Windows from Unbuntu is that they can share common files, that is, with Ubuntu you can read/write the Windows file system, but of course Windows doesn't know squat about Linux. With VirtualBox you would need some external medium to share files.
If you install VirtualBox (I guess VMware will be the same) in Linux and then install Windows inside that, you'll get a significantly faster Windows, but as it is inside a virtual box and uses a special file for its file system, they are isolated from each other even if they can run concurrently. You must look at your needs and see what's the best solution for you, but I can't see any reason why you should want Windows in the long run.

For a new Linux user I recommend to install a full desktop version so you'll be able to start working right away. Personally I always install the server version and load the desktop afterwards, but that requires some learning.

2 wishes for the future:
A Windows-based Linux installation program, allowing you to skip the CD, and to keep on working during the installation. When ready: Reboot.
A Linux-based Linux installation program, allowing you to skip the CD, and to keep on working during the installation. When ready: Reboot.
For the people who build the distro CD this should be a fairly easy task, so why hasn't it been done already?

---

### Post by YesWeCan on 2011-08-08
> **ingeva said:**
> 2 wishes for the future:
A Windows-based Linux installation program, allowing you to skip the CD, and to keep on working during the installation. When ready: Reboot.
A Linux-based Linux installation program, allowing you to skip the CD, and to keep on working during the installation. When ready: Reboot.
For the people who build the distro CD this should be a fairly easy task, so why hasn't it been done already?
Those are very good ideas. I would also want the Windows-based installer to set Grub up so it is not in the MBR at all and add Ubuntu to the Windows boot menu.

---

### Post by ingeva on 2011-08-08
> **YesWeCan said:**
> Those are very good ideas. I would also want the Windows-based installer to set Grub up so it is not in the MBR at all and add Ubuntu to the Windows boot menu.
I think that may be possible.
A simple thing like this would make it so much easier for Windows users to try out Linux!

---

### Post by arrrghhh on 2011-08-08
> **YesWeCan said:**
> Those are very good ideas. I would also want the Windows-based installer to set Grub up so it is not in the MBR at all and add Ubuntu to the Windows boot menu.

I didn't think the Windows boot menu would work - how can it start Linux...?  Windows has no idea of Linux partitions...  Cannot read or write to them natively.

> **ingeva said:**
> I think that may be possible.
A simple thing like this would make it so much easier for Windows users to try out Linux!

It would be nice, but what about WUBI?  I think that's a pretty good way for users to safely try out Ubuntu before taking the plunge.  VM's are also great, assuming your machine has the chops to handle it.

I'm not trying to say your idea is bad, I would like to see it as well... but there are options for people who want to try before they buy if you will... ;)

---

### Post by ingeva on 2011-08-08
> **arrrghhh said:**
> I didn't think the Windows boot menu would work - how can it start Linux...?  Windows has no idea of Linux partitions...  Cannot read or write to them natively.
It would be nice, but what about WUBI?  I think that's a pretty good way for users to safely try out Ubuntu before taking the plunge.  VM's are also great, assuming your machine has the chops to handle it.
I'm not trying to say your idea is bad, I would like to see it as well... but there are options for people who want to try before they buy if you will... ;)
About putting it in boot.ini:
I don't know exactly how to do it, but the Windows boot programs ntldr and $ldr$ are not windows programs either.
All the little boot helper would need to do is find the correct linux partition and the boot files, sufficient to load the rest of the OS.

I'm sure that WUBI or any kind of VM would do the trick also (if, as you say, the computer is powerful enough), but only as a first start. To run Windows under Linux I think would be inferior to running Windows under Linux. I've tried the latter, and the performance is better than running Windows native. The other way around I think would be opposite.

---

### Post by YesWeCan on 2011-08-08
It "just" needs Ubuntu/Grub to be installed in an MBR system compliant manner. For what I can only assume are historical reasons they currently are not and this is what causes all the MBR conflict issues.

Booting Ubuntu from a partition using Windows boot manager without Grub corrupting the MBR area of the disk is perfectly achievable. I know because I have done it. But it needs automating and I doubt Canonical would put any priority on this. It would surely make life so much easier and less worrisome for many same-disk dual booters.

---

### Post by arrrghhh on 2011-08-08
> **YesWeCan said:**
> It "just" needs Ubuntu/Grub to be installed in an MBR system compliant manner. For what I can only assume are historical reasons they currently are not and this is what causes all the MBR conflict issues.

Booting Ubuntu from a partition using Windows boot manager without Grub corrupting the MBR area of the disk is perfectly achievable. I know because I have done it. But it needs automating and I doubt Canonical would put any priority on this. It would surely make life so much easier and less worrisome for many same-disk dual booters.

You really think having Windows boot Linux/GRUB would be more compatible/less painful than the reverse?

I'm sure Windows makes no attempts whatsoever to be compliant with other OSes booting - it doesn't have to be compliant here.  That's always their attitude (and most closed-source projects that are driven monetarily...), unless they are forced to be compliant.  Again, they have no incentive (usually) to be compliant/compatible with other systems.

---

### Post by ingeva on 2011-08-09
> **arrrghhh said:**
> You really think having Windows boot Linux/GRUB would be more compatible/less painful than the reverse?
I don't think so, but the fact is that if you install (or even repair?) a Windows installation, GRUB will no longer be accessible. So if you were able to use the Windows MBR to boot another OS, that would be quite helpful - especially to novice Linux users.
The more experienced, of course, would have a Super-Grub CD lying around .... :)

> **arrrghhh said:**
> I'm sure Windows makes no attempts whatsoever to be compliant with other OSes booting - it doesn't have to be compliant here.  That's always their attitude (and most closed-source projects that are driven monetarily...), unless they are forced to be compliant.  Again, they have no incentive (usually) to be compliant/compatible with other systems.
Right. So if Muhammed doesn't want to go to the mountain .... :)

---

### Post by YesWeCan on 2011-08-09
> **arrrghhh said:**
> You really think having Windows boot Linux/GRUB would be more compatible/less painful than the reverse?
Yes. Why should Windows comply with Grub - Windows has already gone to the effort of complying with IBM's MBR system.

> I'm sure Windows makes no attempts whatsoever to be compliant with other OSes booting - it doesn't have to be compliant here.  That's always their attitude (and most closed-source projects that are driven monetarily...), unless they are forced to be compliant.  Again, they have no incentive (usually) to be compliant/compatible with other systems.
So why does Windows comply with the multi-OS MBR system? Why does the Windows bootloader accommodate chain-loading other OSs?

I used to think like this too. When I first started using Linux I came to this forum and read in a post that it was all Microsoft's fault and the "Grand Unified Bootloader" was our salvation against our oppressive corporate enemy. I was happy to just believe this because I was annoyed with MS at the time for various reasons.

Later I actually learned about how PCs boot and now I realise reality is quite different. IBM invented the PC and its bios boot system and MBR. It is a multi-OS boot system. Yes it is. Windows complies with it: its bootloader is properly contained within its own partition. Ubuntu does not comply with it - instead, Ubuntu wipes out the MBR code and puts its bootloader in a "non mans land" between the MBR and the 1st partition which is a hack and causes conflicts from time to time with other apps. This non-compliance by Ubuntu is the root of the problems people have when same disk dual booting with Windows.

Consider this question: why doesn't Ubuntu contain its bootloader inside its own partition like Windows manages to do?

---

### Post by ingeva on 2011-08-09
> **YesWeCan said:**
> Yes. Why should Windows comply with Grub - Windows has already gone to the effort of complying with IBM's MBR system.No reason to.

In this case it should be in Ubuntu's (Linux's) interest to be compatible with the Windows boot loader. We have established that it's possible. This would help many Windows user to make a migration to Ubuntu/Linux without being worried that they would lose the ability to boot the system they want.

Boot.ini opens the possibility to boot from another file than Windows' own, by making the boot file available from boot.ini.

I hate Windows intensely after having troubled with it for 20 years. The Linux community is responsible for opening our gates for Windows users who want to migrate to a better environment.

---

### Post by arrrghhh on 2011-08-09
I don't exactly want to start a flamewar here "YesWeCan".  We're really getting off-topic here.  If you want to continue this topic, I'm sure there's a section of this forum to do it in.  Sorry for starting the argument, I'd like to try and end it now :p.

---

### Post by ingeva on 2011-08-09
> **arrrghhh said:**
> I don't exactly want to start a flamewar here "YesWeCan".  We're really getting off-topic here.  If you want to continue this topic, I'm sure there's a section of this forum to do it in.  Sorry for starting the argument, I'd like to try and end it now :p.
The digression is not far from the current theme, but point taken.

---

