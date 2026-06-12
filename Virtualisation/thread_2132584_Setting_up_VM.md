---
title: "Setting up VM"
date: 2013-04-05
forum: Virtualisation
---

### Post by ChochiWpg on 2013-04-05
[COLOR=#222225][FONT=Arial]Hi Everyone,

This is my first post on the forum and I am happy to be a new member of the Ubuntu forum community.  I have been doing a lot of reading over the past few months in regards to Ubuntu and Linux in general.  I am a long time Windows user and want to setup Ubuntu on a Virtual Machine to give it a try.  The reasons for trying out Ubuntu and for a possible switch to Linux if everything goes well is because I want something that looks beautiful, works fast, doesn't get viruses and is free and open.  I just love the open concept and the fact that you don't have to be concerned with installing antivirus software.  Also, I am an Android enthusiast and ready to make (or start to make) the leap into building my own ROMs from source.
 
Before I start, I think I might have some issues. My system is kind of old and I don't know how much space is required to boot Ubuntu via VM and also how much space I should allocate especially if I am wanting to build Android ROMs from source.  This is what I am currently working with, what do you think?[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]Windows Vista 64 bit[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]4GB System Memory[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]640GB Hard Drive[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]2.20 GHz[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]The problem is I only have 194GB of free hard drive space remaining on my system. It doesn't sound like that will be enough.[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]Also should I be downloading the 32 bit or 64 bit version of Ubuntu?  How should I configure the VM to get Ubuntu installed and running without issue.  

Really excited to get started and give it a try, it's the whole installation process that is kind of frustrating, especially for someone new and used to using Windows.  Thanks.[/FONT][/COLOR]

---

### Post by slickymaster on 2013-04-05
Here is a pretty good tutorial on how to do it: [Installing Ubuntu inside Windows using VirtualBox]("http://www.psychocats.net/ubuntu/virtualbox")

_Edit_: Be very welcome to the forum.
If you find you'll need assistance don't hesitate to post asking for help, you'll find that everyone will be more than glad to help you.

---

### Post by ChochiWpg on 2013-04-05
Thank you for your prompt reply slickymaster it is much appreciated.

I will take a look at the guide in your post and give it a try when I get home from work.  If I run into any problems or have concerns I will post them here.  

Wow, quick response and very polite as well.  My first experience with the Ubuntu forums is already a pleasant one and has started off on a good note.  Thank you again.  I will keep you posted of my progress.

---

### Post by ibjsb4 on 2013-04-05
I would suggest 1 gig of memory.

---

### Post by MoebusNet on 2013-04-05
If you are going to be compiling programs, you will want all the RAM you can get. If hard drive space is an issue, either buy a bigger HDD or run Ubuntu from an external HDD installation.

---

### Post by slickymaster on 2013-04-05
> **ChochiWpg said:**
> [COLOR=#222225][FONT=Arial]Hi Everyone,

This is my first post on the forum and I am happy to be a new member of the Ubuntu forum community.  I have been doing a lot of reading over the past few months in regards to Ubuntu and Linux in general.  I am a long time Windows user and want to setup Ubuntu on a Virtual Machine to give it a try.  The reasons for trying out Ubuntu and for a possible switch to Linux if everything goes well is because I want something that looks beautiful, works fast, doesn't get viruses and is free and open.  I just love the open concept and the fact that you don't have to be concerned with installing antivirus software.  Also, I am an Android enthusiast and ready to make (or start to make) the leap into building my own ROMs from source.
 
Before I start, I think I might have some issues. My system is kind of old and I don't know how much space is required to boot Ubuntu via VM and also how much space I should allocate especially if I am wanting to build Android ROMs from source.  This is what I am currently working with, what do you think?[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]Windows Vista 64 bit[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]4GB System Memory[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]640GB Hard Drive[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]2.20 GHz[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]The problem is I only have 194GB of free hard drive space remaining on my system. It doesn't sound like that will be enough.[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]Also should I be downloading the 32 bit or 64 bit version of Ubuntu?  How should I configure the VM to get Ubuntu installed and running without issue.  

Really excited to get started and give it a try, it's the whole installation process that is kind of frustrating, especially for someone new and used to using Windows.  Thanks.[/FONT][/COLOR]

By the way, and just as a reference to you, in this machine in particular I have Xubuntu 13.04 running on a VM Virtual Box with 1 GB of RAM and using 100 GB of my hard drive, divided in three partitions, as follows:
One ext4 partition of 50 GB for my root, one ext4 partition of 50 GB for my home, and a last partition of 2 GB for my swap.

---

### Post by ChochiWpg on 2013-04-05
> **slickymaster said:**
> By the way, and just as a reference to you, in this machine in particular I have Xubuntu 13.04 running on a VM Virtual Box with 1 GB of RAM and using 100 GB of my hard drive, divided in three partitions, as follows:
One ext4 partition of 50 GB for my root, one ext4 partition of 50 GB for my home, and a last partition of 2 GB for my swap.

When I setup the VM I will set with 1GB of RAM since I have a machine with 4GB total RAM.  Just wasn't sure how much harddrive I should allocate for the VM.  I don't think I will divide my VM into separate partitions.  This is my first time setting up a VM so I am a complete noob, that's pretty advanced for me to be honest.

If I am wanting to build Android from source, how much space should be allocated or how much would suffice?

---

### Post by slickymaster on 2013-04-05
> **ChochiWpg said:**
> If I am wanting to build Android from source, how much space should be allocated or how much would suffice?

Sorry, but I'm unqualified to help you with that. Personally I just develop in Java and SQL.

My advise to you is to start a new thread on the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") sub-forum asking it, there.

---

### Post by ChochiWpg on 2013-04-05
> **slickymaster said:**
> Sorry, but I'm unqualified to help you with that. Personally I just develop in Java and SQL.

My advise to you is to start a new thread on the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") sub-forum asking it, there.

No problem, you have been a big help, thank you very much for all your assistance.

---

### Post by ChochiWpg on 2013-04-06
Alright, I setup my VM today and installed the 64bit version of 12.04LTS.  It was relatively simple to install.  I allocated 1GB RAM and provided 20GB of HDD for the time being just to play around and get familiar with everything.

I notice that it seems to run extremely slow.  I don't know if it's because it's running as a VM on top of Windows so my computer is working hard to keep 2 OS's going at the same time?  Windows, my main OS, is working the way it normally does with no lag whatsoever.  But even to go to Ubuntu Software Centre to install VLC Player it's been installing for the past 5 mins.  Also I checked for updates first thing after initial install and reboot.  The system found 132 items that needed updating, I click update and it asked for a password, which I provided and then click next and it just sits there as if attempting to download but doesn't do anything.

I am on a desktop PC with a wired internet connection, so I know connection isn't a problem.  I don't know why it's taking forever to do the first basic steps after install and seems very very laggy.  Did I do something wrong?

---

### Post by slickymaster on 2013-04-06
The first thing that cross my mind is that Virtualbox Guest Additions could be the culprit of that slowness, not providing 3D acceleration.
Please see this: [https://www.virtualbox.org/ticket/11107](https://www.virtualbox.org/ticket/11107)

---

### Post by ChochiWpg on 2013-04-06
> **slickymaster said:**
> The first thing that cross my mind is that Virtualbox Guest Additions could be the culprit of that slowness, not providing 3D acceleration.
Please see this: [https://www.virtualbox.org/ticket/11107](https://www.virtualbox.org/ticket/11107)

That seems very complicated for me TBH.  I ended up uninstalling the VM software and deleting the files it created as well.

I was speaking with someone on Google+ who suggested to run Ubuntu natively via dual boot as it runs much better.  So I am currently attempting to give that try.  But I am already running into issues.

First off I will not repartition my HDD without having a full image of my Windows OS.  Problem with that is my current system holds 380GB of information.  I do not have enough additional HDD space to repartition and save a backup on a separate partition.  Nor do I have enough DVD's to backup 380GB of data.

So ATM I am at an impasse.  I want to use Ubuntu and think I will enjoy running and using the distro.  At the same time I want to make sure I have everything backed up first before installing.

Seems to me that using Ubuntu is the fun/easy part.  The extremely frustrating and complicated part (for me at least) is having to backup everything, create partitions and then make sure to install it correctly.  It's the whole install process that I find very un-user friendly.  Where Ubuntu itself is extremely user friendly and seems to be a joy to use.  I just want to use it already and I have been backing up and trying to figure out how to partition for the past 7 hours.

---

### Post by slickymaster on 2013-04-07
> **ChochiWpg said:**
> That seems very complicated for me TBH.  I ended up uninstalling the VM software and deleting the files it created as well.

I was speaking with someone on Google+ who suggested to run Ubuntu natively via dual boot as it runs much better.  So I am currently attempting to give that try.  But I am already running into issues.

Running it natively will give you better performance because you aren't running two OS's at the same time. Yours native install will have all the RAM and CPU cycles to itself. 

> **ChochiWpg said:**
> First off I will not repartition my HDD without having a full image of my Windows OS.  Problem with that is my current system holds 380GB of information.  I do not have enough additional HDD space to repartition and save a backup on a separate partition.  Nor do I have enough DVD's to backup 380GB of data.

So ATM I am at an impasse.  I want to use Ubuntu and think I will enjoy running and using the distro.  At the same time I want to make sure I have everything backed up first before installing.

Seems to me that using Ubuntu is the fun/easy part.  The extremely frustrating and complicated part (for me at least) is having to backup everything, create partitions and then make sure to install it correctly.  It's the whole install process that I find very un-user friendly.  Where Ubuntu itself is extremely user friendly and seems to be a joy to use.  I just want to use it already and I have been backing up and trying to figure out how to partition for the past 7 hours.

Installing Ubuntu dual-booting with your existing Windows install is not that complicated and you shouldn't be afraid of attempting to do it. It's a very straightforward process and there are a lot of tutorials that you can see before you'll do it.

One thing I do advice and encourage you to do is to defragment your hard drive before starting with the Ubuntu installation, even though Windows partition and Linux partition have no real impact on each other, beyond accessing each others' data if you'd like to do that.
The Ubuntu installer will offer to resize your Windows partition to create space on your hard disk for Ubuntu. All you need to do is tell it how much space to give to each OS. Fragmentation of the Windows partition affects how well the installer can resize it, so you should defragment the disk from Windows before installing Ubuntu.

---

### Post by ChochiWpg on 2013-04-07
> **slickymaster said:**
> Running it natively will give you better performance because you aren't running two OS's at the same time. Yours native install will have all the RAM and CPU cycles to itself. 



Installing Ubuntu dual-booting with your existing Windows install is not that complicated and you shouldn't be afraid of attempting to do it. It's a very straightforward process and there are a lot of tutorials that you can see before you'll do it.

One thing I do advice and encourage you to do is to defragment your hard drive before starting with the Ubuntu installation, even though Windows partition and Linux partition have no real impact on each other, beyond accessing each others' data if you'd like to do that.
The Ubuntu installer will offer to resize your Windows partition to create space on your hard disk for Ubuntu. All you need to do is tell it how much space to give to each OS. Fragmentation of the Windows partition affects how well the installer can resize it, so you should defragment the disk from Windows before installing Ubuntu.

Thanks again for your help. I run defrag on my system weekly and just to be safe before partitioning and installing Ubuntu I will run it manually as well.

I have watched tutorials and did notice that the Ubuntu install does offer to resize the partition. However, I noticed in other tutorials to repartition the HDD first in Windows via disk management before installing Ubuntu. Which option is ideal? Also, you mentioned it is possible to share files/data between Windows and Linux? Because I would like to access my media files I already have on my Windows partition in Linux as well. Lastly, you also mentioned it's a good idea to setup a Home, Root and Swap partition. Is this something that can be done during the Ubuntu install when it says it will partition the HD for you? Or is this something you have to do before or after install? 

Sorry guys, so many questions and I am probably making this harder than it really is, but it's all very new and overwhelming at the moment.

---

### Post by slickymaster on 2013-04-08
> **ChochiWpg said:**
> I have watched tutorials and did notice that the Ubuntu install does offer to resize the partition. However, I noticed in other tutorials to repartition the HDD first in Windows via disk management before installing Ubuntu. Which option is ideal?
Personally I prefer to use Linux programs because they are faster as you don't need to defragment first. If you go with Windows Disk Management I do advise you to defragment your hard drive before installing Ubuntu.
Please see this link, it's quite explanatory on this subject: [Resize the Windows partition]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions#Resize_the_Windows_partition")

> **ChochiWpg said:**
> Also, you mentioned it is possible to share files/data between Windows and Linux? Because I would like to access my media files I already have on my Windows partition in Linux as well.
Yes, it's possible, though it might strike you as a bit difficult at the beginning, it's not so. You can do it is through the possibility that  even though Windows can't read from EXT2/4 partitions, Ubuntu can read from NTFS partitions.
See these: [A Comprehensive Guide to Sharing Your Data Across Multi-Booting Windows, Mac, and Linux PCs]("http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems") and [How To Harmonize Your Dual-Boot Setup for Windows and Ubuntu]("http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/")

> **ChochiWpg said:**
> Lastly, you also mentioned it's a good idea to setup a Home, Root and Swap partition. Is this something that can be done during the Ubuntu install when it says it will partition the HD for you? Or is this something you have to do before or after install?
Yes, you do it when you're installing Ubuntu, not after. See this very easy tutorial on how to do it: [Ubuntu 12.10 installation and disk partitioning guide]("http://www.linuxbsdos.com/2012/11/03/ubuntu-12-10-installation-and-disk-partitioning-guide/2/")

---

### Post by ChochiWpg on 2013-04-08
> **slickymaster said:**
> Personally I prefer to use Linux programs because they are faster as you don't need to defragment first. If you go with Windows Disk Management I do advise you to defragment your hard drive before installing Ubuntu.
Please see this link, it's quite explanatory on this subject: [Resize the Windows partition]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions#Resize_the_Windows_partition")


Yes, it's possible, though it might strike you as a bit difficult at the beginning, it's not so. You can do it is through the possibility that  even though Windows can't read from EXT2/4 partitions, Ubuntu can read from NTFS partitions.
See these: [A Comprehensive Guide to Sharing Your Data Across Multi-Booting Windows, Mac, and Linux PCs]("http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems") and [How To Harmonize Your Dual-Boot Setup for Windows and Ubuntu]("http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/")


Yes, you do it when you're installing Ubuntu, not after. See this very easy tutorial on how to do it: [Ubuntu 12.10 installation and disk partitioning guide]("http://www.linuxbsdos.com/2012/11/03/ubuntu-12-10-installation-and-disk-partitioning-guide/2/")

Thank you again for all your help SlickyMaster.  Looks like I have a lot of reading to do.  Partitioning using the built in Ubuntu installer sounds much simpler than defraging and using the Disk Management utility.  The disk partitioning guide was very helpful.  As for sharing between OS's I will have to re-read that section a few times over as it seems advanced for me right now.  

Thanks for all your help. This thread has somewhat veered from my initial question and before I attempt to go further I want to do some more reading and understanding beforehand. Much appreciated, if I run into any problems I will let you know.  Thank you.

---

### Post by slickymaster on 2013-04-08
Maybe it would be better to close this thread then, and mark it as solved, and if latter on you run with any problems you can open a new one, specifically to the issues you eventually stuck on.

If you have doubts on how to mark a thread as SOLVED please see my signature on how to do it.

---

### Post by Bucky Ball on 2013-04-08
*Thread moved to **Virtualisation**.*

> **slickymaster said:**
> Maybe it would be better to close this thread then, and mark it as solved, and if latter on you run with any problems you can open a new one, specifically to the issues you eventually stuck on.

Agreed, good plan. After you have researched some more you may have very different questions. Post them in new threads with descriptive titles and in the appropriate sub-forums to maximise your chances of help. Good luck with it. ;)

---

