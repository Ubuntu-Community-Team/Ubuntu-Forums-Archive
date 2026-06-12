---
title: "Ubuntu for daily usage and learning."
date: 2014-07-28
forum: Ubuntu, Linux and OS Chat
---

### Post by puto2 on 2014-07-28
Hi,

I am on a lookout for a linux flavour that can be used for general computer usage and some learning (Bash Scripting, Perl, may be try some devops stuff later on). How's Ubuntu suited for it?

I have a thinkpad that came preloaded with Windows 7. Every few weeks, it gets slow, and sometimes I get the BSOD. Windows Updates fail to install and whatnot. Looking for a Linux Flavor that I start using and eventually replace Windows. I am familiar with Linux. Been using RHEL 6.4 through command line ssh at work, so I am aware of the basics.

Any tips, suggestions and guidance would be great. Existing thinkpad users who have migrated to/dual booting Ubuntu, kindly share your experience.

I am in the process of downloading Trusty Tahr 14.04.1. Cant wait to try it out. 

Regards,
Puto

---

### Post by TheFu on 2014-07-28
Ubuntu is a fine distro for general purpose use - desktops or servers.  Would you expect any different answer on these, the Ubuntu Forums?

I don't expect most people to completely remove Windows from their lives. There are a few things that Windows does better than Linux still - just a few for my personal requirements.  Besides that tiny list of things - about 2 hrs a week in Windows, I use Linux for everything else.  Desktops, servers, remote access, DevOps, Perl development, documentation, email, calendaring, everything ...

---

### Post by puto2 on 2014-07-28
Hi Fu,

No, I dont expect different answer. Just wanted to get some opinions. Nothing wrong with that I guess.

Also wanted to see what existing thinkpad users on Ubuntu feel.

---

### Post by tgalati4 on 2014-07-28
I've been running Linux Mint MATE on my Thinkpad T43p for years.  It dual-boots to WinXP for some proprietary programs that I need in the field, but otherwise works fine with linux.  Check out [http://thinkwiki.org](http://thinkwiki.org) for tips on installation.

---

### Post by oldfred on 2014-07-28
Most Windows 7 systems use all 4 primary partitions allowed with MBR partitions and BIOS boot. Only a few new Windows 7 systems released just before Windows 8 used UEFI with gpt partitions.
If you have the 4 partitions used, you will have to backup & delete one, typically the vendor tools but it may vary.

Best to have full backup of Windows.

Use Windows own tools to shrink the NTFS partition and reboot immediately to let it run chkdsk and make repairs for its new size. Do not create partitions with Windows.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

If reinstalling Ubuntu or for any reason it does not specifically mention Windows is already installed do not use any auto install options. Only use Something Else.

 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Bucky Ball on 2014-07-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by puto2 on 2014-07-29
Hi tgalati4 and oldfred,

Thank you for taking time to answer my queries.

Ran ubuntu off usb drive. Looks awesome.

Will install it over the weekend.

---

### Post by lz1dsb on 2014-07-29
I've been using Linux and Ubuntu in general on my home machines on and off since 2009. Since 2012 it's my main desktop OS. 
I use it for general computing, preparing documents for my part time job, managing a medium sized IP network, e-banking, learning, testing... anything you can think of. 
So i would say that throughout the years my experience is quite a positive one. I've also expanded my horizon and knowledge about networking, computers and operating systems in general, and I'm still learning :) 

The only thing I wasn't able to solve was an issue with the video and Wifi drivers on my old laptop. But again - it's not Ubuntu to be blamed. 
If you choose you hardware carefully, I think that your experience with Linux in general would be quite a good one. If your hardware is supported - the first 5 major Linux distribution would work just fine. 

I think the great thing about Linux these days is that we have such a broad range of nice and free applications to choose from. Which is great. In my case so far I have always been able to find an application to do my job. Well maybe the folks who use very specific applications which are Windows only will have other opinion, but I think the situation is improving...

---

### Post by d-cosner on 2014-07-29
Ubuntu, Mint and PCLInuxOS all have very satisfied users. LTS releases are the best for a machine you want to get work done on. PCLinuxOS is a rolling release but it is very stable and relyable. Mint is Ubuntu based but gives you other desktop environment choices, there are LTS releases also. All of these choices have excellant support and are very friendly to new users.

I have Ubuntu running on a laptop with a gtp partition and secure boot but it is the only OS on the machine. The laptop came with Windows 8 and I quickly wiped it out. Ubuntu had no problems with the gtp partition and secure boot though, the signed kernel installed fine and the laptop runs perfectly.

I mentioned PCLInuxOS because it is well known for good hardware support and the community will go above and beyond to help you should you run into problems. I also mention this in case you are interested in a rolling release, these guys and gals do very nice work. Also, PCLinuxOS comes stock with the "mylivecd" tool that allows you to create a Live / Install CD of your system.

Try out the distros that interest you from a usb stick or Live CD to get an idea how they will run on your hardware and to try out the different desktop environments to see what best suits your needs.

---

### Post by Linux_Son on 2014-07-29
Your BSOD can be a hardware cause which Linux will not fix btw. I recommend Ubuntu or Mint only for absolute newcomers.

---

