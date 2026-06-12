---
title: "[SOLVED] Ubuntu or Kali Linux ?"
date: 2014-12-23
forum: Ubuntu, Linux and OS Chat
---

### Post by panjgoori on 2014-12-23
Hello. Im confused between these two. Which one should i install alongside my Windows 8.1 OS? I want to use linux but im not new to it and want to slowly migrate from windows completely. and one more thing i also want to learn network pentesting and also want to try it on my home network. Based on my requirements which one you will suggest me to install ?

---

### Post by grahammechanical on 2014-12-23
Here is one difference between Ubuntu and Kali Linux, as I understand things: Ubuntu is supported on this forum. Kali Linux is not supported on this forum. You have answered your own question. The answer is there in your stated desires.

---

### Post by panjgoori on 2014-12-23
> **grahammechanical said:**
> Here is one difference between Ubuntu and Kali Linux, as I understand things: Ubuntu is supported on this forum. Kali Linux is not supported on this forum. You have answered your own question. The answer is there in your stated desires.

i asked this question here because Kali forums sucks. i asked a simple question about 3 months ago and an admin sent me a PM and didn't even published my thread. it was on topic and even i mentioned all the detail in it. I have used Ubuntu before and also installed it on my Windows 7 laptop using wubi and it worked extremely well.

---

### Post by sudodus on 2014-12-23
You are welcome to install standard Ubuntu or the Ubuntu flavours and get help at the Ubuntu Forums :-)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL] 				

But if you want to learn pentesting, Kali might be a better choice. Maybe you have better luck next time at the Kali forum. Read the existing threads and whatever instructions you can find (Code of Conduct etc). Then try again to make an own thread, that is not too different in style and content.

-o-

By the way, I'm sorry but wubi is no longer developed and supported because it does not work with Windows 8.

See this link [Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")

---

### Post by d-cosner on 2014-12-23
Go with Ubuntu, the support is excellant and the people on this forum are great.

---

### Post by ibjsb4 on 2014-12-23
I think grahammechanical refers to this
[https://wiki.ubuntu.com/UbuntuPentest/Coc](https://wiki.ubuntu.com/UbuntuPentest/Coc)

Is it necessary to choose one over the other? Triple boot.
[https://www.google.com/search?client=ubuntu&channel=fs&q=Triple+boot+linux&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Triple+boot+linux&ie=utf-8&oe=utf-8)

Want to be able to access and run all three at the same time?
[https://www.virtualbox.org/](https://www.virtualbox.org/)
(your machine has to be able to handle the extra load)

---

### Post by panjgoori on 2014-12-26
i installed Kali Linux but to be honest i didn't liked it. i prefer UI over Kali linux. is there any guide to dual boot windows 8.1 with Ubuntu ? I have already downloaded ubuntu 14.1 which i think is the latest available version. and one more thing from where i can install AMD Drivers ? thanks everyone

---

### Post by sudodus on 2014-12-27
I guess you have UEFI with Windows 8.1. See the following links (and links from them)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295"). 

I think you can find a lot of threads about graphics chips/cards and drivers at the [Hardware]("http://ubuntuforums.org/forumdisplay.php?f=332") Forum. There are tested drivers in the Ubuntu repositories. Other drivers can be downloaded directly from the manufacturer's website. But to get more precise help, please specify your card (model).

---

### Post by panjgoori on 2014-12-27
> **sudodus said:**
> I guess you have UEFI with Windows 8.1. See the following links (and links from them)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295"). 

I think you can find a lot of threads about graphics chips/cards and drivers at the [Hardware]("http://ubuntuforums.org/forumdisplay.php?f=332") Forum. There are tested drivers in the Ubuntu repositories. Other drivers can be downloaded directly from the manufacturer's website. But to get more precise help, please specify your card (model).

My laptop specs are AMD A10-4600M APU Radeon 7660G+HD7670M Dual Graphics. Currently I'm installing windows 7 in my laptop. Tutorials on installation is not a problem as i will find many on net. I only need a guide about drivers installation.

---

### Post by flaymond on 2014-12-27
If your working platform is pentesting, I highly recommend you to choose Kali Linux...but for a beginner..I definetely prefer Ubuntu. The difference between these distros, Kali Linux is come preinstalled and suited with a lot of forensics and pentesting stuff. While Ubuntu is good for work and home use. You can install the pentesting software from Kali Linux into Ubuntu if you want.

---

### Post by Bucky Ball on 2014-12-27
Slightly off-topic, but be aware that 14.10 has nine months support (so about seven months left) whereas 14.04 LTS has five years. The latest is not always the greatest. If you don't mind upgrading your OS every six months or so, all good. If not, stick to the LTS releases.

---

### Post by sudodus on 2014-12-27
> **panjgoori said:**
> My laptop specs are AMD A10-4600M APU Radeon 7660G+HD7670M Dual Graphics. Currently I'm installing windows 7 in my laptop. Tutorials on installation is not a problem as i will find many on net. I only need a guide about drivers installation.

If *you* are running AMD A10-4600M APU Radeon 7660G+HD7670M Dual Graphics, please chip in and help :-)

---

### Post by panjgoori on 2014-12-27
> **InterProg said:**
> If your working platform is pentesting, I highly recommend you to choose Kali Linux...but for a beginner..I definetely prefer Ubuntu. The difference between these distros, Kali Linux is come preinstalled and suited with a lot of forensics and pentesting stuff. While Ubuntu is good for work and home use. You can install the pentesting software from Kali Linux into Ubuntu if you want.

i tried Kali Linux but i didn't like its interface. and i have already used ubuntu for about a month alongside my Windows and i loved it.

> **Bucky Ball said:**
> Slightly off-topic, but be aware that 14.10 has nine months support (so about seven months left) whereas 14.04 LTS has five years. The latest is not always the greatest. If you don't mind upgrading your OS every six months or so, all good. If not, stick to the LTS releases.

yes i know about this. i will definitely re-install my windows within 6 months as Windows slowly slows down as time passes.

> **sudodus said:**
> If *you* are running AMD A10-4600M APU Radeon 7660G+HD7670M Dual Graphics, please chip in and help :-)

i will help gladly. but what help you need ? one think im sure. you know much more than me on Linux side ;) :P[CENTER][COLOR=#000000] [/COLOR][/CENTER]

---

### Post by sudodus on 2014-12-27
> **panjgoori said:**
> i will help gladly. but what help you need ? one think im sure. you know much more than me on Linux side ;) :P

I meant that ***other people reading this thread*** and have the same or similar graphics hardware ***should chip in and help*** :-)

[COLOR=#696969]Unfortunately I know very little about AMD/ATI/Radeon graphics, I run Intel and nvidia graphics).[/COLOR]

---

### Post by panjgoori on 2014-12-27
> **sudodus said:**
> I meant that ***other people reading this thread*** and have the same or similar graphics hardware ***should chip in and help*** :-)

[COLOR=#696969]Unfortunately I know very little about AMD/ATI/Radeon graphics, I run Intel and nvidia graphics).[/COLOR]

oopps. Its my first time that I bought a AMD based system (processor, chipset etc) but so far im very happy with its performance. On the topic AMD actually does provides drivers for Ubuntu on their official website. Should i download them ?

---

### Post by sudodus on 2014-12-27
Unless you get more detailed advice, you can starting checking what proprietary driver that are available via the Software Center. If you find nothing, maybe you can get help with some terminal commands.

If still no success, you can download drivers from the manufacturer and try to install them.

---

### Post by panjgoori on 2014-12-28
> **sudodus said:**
> Unless you get more detailed advice, you can starting checking what proprietary driver that are available via the Software Center. If you find nothing, maybe you can get help with some terminal commands.

If still no success, you can download drivers from the manufacturer and try to install them.

Using terminal in Linux is fun and its the best part of a Linux OS. I have used Nokia N900 for more than 3 years and still have one. Using terminal was the best thing on my N900. Best phone ever. I will today install Ubuntu and will check software center for drivers. And if i re-install my Windows while Ubuntu is installed will i also have to remove and re-install Ubuntu or there is a way to bring back dual boot option at start up ?

---

### Post by sudodus on 2014-12-28
Windows will overwrite the bootloader, so you need to reinstall it. See this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

The easiest way is to install Windows before Ubuntu.

---

### Post by panjgoori on 2014-12-28
> **sudodus said:**
> Windows will overwrite the bootloader, so you need to reinstall it. See this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

The easiest way is to install Windows before Ubuntu.

thanks for all the help. one question. can you provide a working guide to dual boot my system with Windows 7 and Ubuntu 14.04.1. I have 26gb of unallocated space on my HDD. will this be enough which i think will be enough.

---

### Post by sudodus on 2014-12-28
26 GB will be enough for Ubuntu (24 GB for the root partition and 1 or 2 GB for the swap partition).

If you want to hibernate, you need a swap partition of at least the same size as the RAM (in Gibibytes - base 2), otherwise 1 or 2 GB will be enough. You have the best control of the partitioning, if you shrink Windows with a Windows tool (but it seems you need not do it), and if you run ***gparted*** from the Ubuntu live drive before starting the installer.

There are several guides covering different parts of the task: What have you found, and where do you need help?

- select a suitable iso file (I recommend the long term support version ***14.04 LTS***)
- download and check the iso file
- create an install pendrive (or DVD disk)
- run the installer
- fix problems (if you have bad luck, most of the time it just works)

-o-

You can start with these links and links from them:
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

---

### Post by panjgoori on 2014-12-28
is home partition is necessary ? So basically you mean before installing Ubuntu i should start gparted and repartition un-allocated space. i need a tutorial what to do after partitioning ? there are basically 3 options to choose from. 
1. Install Ubuntu Alongside windows 
2. Replace windows with Ubuntu (this will completely wipe HDD) 
3. Something else. 

I found a tutorial on techspot and it explains everything very well. 
[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

---

### Post by sudodus on 2014-12-28
A home partition is not necessary. Some people prefer a home partition, but the standard installation of Ubuntu is made with only one root partition and one swap partition.

You are talking about the options at the partitioning screen. 'Install alongside' is risky, many people have lost their data using it. I strongly recommend that you use '***Something else***'. That way you know better what you are doing. If you have used gparted and its graphical user interface to create the partitions, it is easy to select them using 'Something else' alias manual selection of partitions.

But there are always risks, when you edit partitions and install operating system. So please, ***start with a backup***, at least of your personal data. Back it up to a separate drive, that you disconnect during the installation, or to the 'cloud'.

---

### Post by Bucky Ball on 2014-12-29
Don't need a /home partition. Let the install create a /home directory inside / and then delete the directories in there (/Documents, /Videos, etc.) and create symlinks to the existing data you have in other existing partitions. I'm guessing, but figure you already have data on a data drive/partition somewhere. That way, 26Gb is plenty for / and /swap. 

For instance, I have one data partition with /Documents, /Videos, etc. and three installs, all with symlinks in the /home directories pointing to the data on the data partition. That way, any changes I make from any install are reflected if I boot another install. All the installs are using and looking at the same data partition/directories. ;)

[THIS]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979") link shows you about symlinks.

---

### Post by monkeybrain20122 on 2014-12-29
Dualboot Ubuntu and Kali and forget about Windows8. :)

---

### Post by panjgoori on 2014-12-29
thanks everyone for all the help. i have created a boot able Ubuntu USB disk. will now install it. I have already created a backup of all my data as once i tried to install Ubuntu once it formatted all my HDD. 

@monkeybrain2012: Can't completely ditch windows right one but will do slowly as i will completely get familiar with Linux.

---

### Post by sudodus on 2014-12-29
Good luck :-)

---

### Post by panjgoori on 2014-12-29
> **sudodus said:**
> Good luck :-)

thanks ;)

---

### Post by monkeybrain20122 on 2014-12-29
> **panjgoori said:**
> 
@monkeybrain2012: Can't completely ditch windows right one but will do slowly as i will completely get familiar with Linux.

I wasn't completely facetious, dualbooting with Windows 8 is kind of problematic and it imposes all kinds of restrictions on boot settings, since MS goes out of its way to discourage/prevent dualboot with other OSes. On the other hand it is a rather easy to multiboot as many linux distros as your hard drive can handle. So I would use virtualbox if I only need Windows occasionally.

---

### Post by panjgoori on 2014-12-30
installed Ubuntu successfully. Now i need some basic apps to cover my needs. Which is best C++ IDE for Ubuntu for Beginners like me ?

---

### Post by sudodus on 2014-12-30
Congratulations :KS

1. Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

2. You get better help for this new task, if you create a new thread in the Ubuntu [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") Forum. Use a good descriptive title!

Good luck :-)

---

### Post by panjgoori on 2014-12-30
> **sudodus said:**
> Congratulations :KS

1. Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

2. You get better help for this new task, if you create a new thread in the Ubuntu [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") Forum. Use a good descriptive title!

Good luck :-)

thanks for all the help. I will mark this thread as solved. A great community.

---

