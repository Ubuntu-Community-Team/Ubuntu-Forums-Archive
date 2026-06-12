---
title: "3 linux distributions for old slow PCs"
date: 2010-01-11
forum: The Cafe
---

### Post by replikanxxl on 2010-01-11
I wanted to post my so little experience with 3 Linux distributions that are intended to ask for lowest system requirements possible as i searched forum and couldn't find much info more than some suggestions 

The system i used is an 11 years old PC with 256MB S-DRAM , Pentium III 933mhz CPU and a 32MB geforce2 video card , an Ethernet card and a CD-ROM drive.

The first distro i tried was "Damn Small Linux" . You can find the details on [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")
First i used the USB flash stick method. I used a 1GB flash stick and v4.4.9-embedded with the USB loader application that DSL provides. But i couldn't get it to run as it has no support for booting from USB device(But i tested the USB method still. i got this USB stick to boot from another PC that was like 5-6 years old. It was not easy either cause the BIOS on it was not directly giving you an option to set the USB stick as a boot device , but as it was showing the stick as a kind of HDD , i bypassed booting priority problem with disabling the actual HDD so the system used the USB stick as second HDD to boot from).So i burnt v4.4.10 on a CD (just 50 MB) and got it working live on CD. &#304;t was really so quick on boot. The visuals are just a step further than command line, as expected. But I'm sure all the software and utilities on it are chosen wisely and can satisfy your needs, if your point is getting the job done. I would like to see how it performs on web browsing and instant messaging but i couldn't get the connection working at all. it was able to detect eth0 interface but couldn't get an IP from DHCP server. In some forums people say it was working when they used "pump -i eth0" command but when i did it all i get was a wait of 20 seconds and a message: " Operation failed".

The second distro i used was Puppy Linux. You can find details on [http://puppylinux.org/]("http://puppylinux.org/").
I burnt v4.3.1 on Cd (Just 105 MB) and got it running Live. It was really satisfactory on visual terms. But once again i was not able to test its performance on web browsing and instant messaging cause i could not set up the connection. Though, from what I've experienced so far i can tell you that it would be working fine cause the CPU load was around %30 most times and all the software i launched inside was launching and running really smooth. The only problem was about the screen display; it was not fitting on right position no matter what resolution i choose.

The third and last distro i tried was Vector Linux. You can find detailed info at [http://vectorlinux.com/]("http://vectorlinux.com/")
First of all, Low system requirements is not the highest priority motivation of this distro. Thus, even the version i used (6.0 Light Live Edition) is not small; 645 MB. I got this version running Live on CD and it was not so quick on boot but it was performing really good, considering its "not bad at all" visuals. Its look was just like a mix of Ubuntu and vista at basic elements. And it was able to manage the connection automatically and i was able to surf the web with Firefox. It was working fine as long as i do not dance on tabs or scroll so fast.Also, resizing the pages was a heavy load for my Pentium III as well.

***Persistent Feature*** : This feature allows you to save your settings even if you boot from a Live CD!(that exclamation mark is for me being impressed). We know we can save our works and files on net or any removable storage device or native ones but this feature lets us boot from a Live CD or a USB-stick like we are using a HDD.Now this, is really carrying your OS with you.When you shutdown Puppy Linux , its asking you if you want to save your settings; which means all the customization you did for your comfort and needs. You can save them on a USB-stick or a Zip drive or a Floppy Disk or a HDD or even on the **[COLOR="Red"]Live CD itself[/COLOR]** if its not closed.A pupsave.2fs file is saved which contains a ext2 structure inside. DSL distro is opting for a backup at log out too but i couldn't get detailed information on it.   

For conclusion , i can say that it feels like Puppy Linux was the one that hit the right balance between the visuals and performance versus system requirements. But i cant be sure as i couldn't manage the Internet connection and spend time on more various applications. Vector Linux was not so 'light' IMHO. And DSL is sacrificing too much on comfort and that feels like its more for experiments and geeks rather than users-in-need.

nice day everyone :popcorn:

edit1: after suggestions i have tried slitaz. it was the best experience ever among all.its absolutely the best performing one (and its 30 MB !). There was no freeze on videos or scrolling or resizing at firefox

---

### Post by egalvan on 2010-01-11
SliTaz has a nice write-up on DistroWatch.

Reviewer mentions that one of the iso's is only 30MB.

[http://distrowatch.com/](http://distrowatch.com/)


Then of course there is TinyCore Linux, which weighs in at around 10MB download.

---

### Post by Darce on 2010-01-11
Your on the money with Puppy for older systems.
I managed to put in on a friends old laptop that couldnt boot from USB or the pcmcia attached CDROM.
If your puppy system is on a network, try Menu->Setup->Network to get internet acccess. That will sort both wired & wireless, else Modems for USB wireless Modems was hassle free as well.

Cheers,

Tim

---

### Post by replikanxxl on 2010-01-11
> **egalvan said:**
> SliTaz has a nice write-up on DistroWatch.

Reviewer mentions that one of the iso's is only 30MB.

[http://distrowatch.com/](http://distrowatch.com/)


Then of course there is TinyCore Linux, which weighs in at around 10MB download.

10MB ?? i cant wait to see how it looks :D though i already feel ashamed for calling DSL 'experimental' :p

---

### Post by mkvnmtr on 2010-01-11
I like Puppy but I believe nobody is working on Damn Small Linux anymore so it may have lived its lifespan. I have PClinux with a LXDE desktop in a virtual box with only 256Mb and it runs very well and I find it easier to use than Puppy because it uses Synaptic. I am now trying AntiX Mepis Bbut 4 times it has not installed. The live ISO boots and looks like something I will like but the installer gets to about 20% and says it can not complete with no reason. I think it will be a good light system if i can install it.

---

### Post by replikanxxl on 2010-01-11
> **Darce said:**
> Your on the money with Puppy for older systems.
I managed to put in on a friends old laptop that couldnt boot from USB or the pcmcia attached CDROM.
If your puppy system is on a network, try Menu->Setup->Network to get internet acccess. That will sort both wired & wireless, else Modems for USB wireless Modems was hassle free as well.

Cheers,

Tim

ah. i dont know what the saying"on the money" means but i guess you are thumbs up for puppy linux as well ? 
i just plugged in an Ethernet cable as I'm using a 4-port router ADSL modem if that helps about explaining.
thanks for advice.ill try soon

edit1 : i just did it right now and its working ?!?! i swear i did not do anything different. i clicked DHCP as i did before and now its working. And its really working flawless on Seamonkey web browser with no freeze or flicker. The monitor positioning problem is still on though. my monitor is a 22" samsung and i choose 1024x768 as the video card is crappy. the screen is like 10-20 pixels right of the center it should be.

---

### Post by replikanxxl on 2010-01-11
> **mkvnmtr said:**
> I like Puppy but I believe nobody is working on Damn Small Linux anymore so it may have lived its lifespan. I have PClinux with a LXDE desktop in a virtual box with only 256Mb and it runs very well and I find it easier to use than Puppy because it uses Synaptic. I am now trying AntiX Mepis Bbut 4 times it has not installed. The live ISO boots and looks like something I will like but the installer gets to about 20% and says it can not complete with no reason. I think it will be a good light system if i can install it.

Just 5 minutes ago i made my conclusion sure about Puppy as well. cause i got the net working and i see it is really working good. I just came up with the idea to run this old PC so that my dad can read newspapers and i can buy even a monster PC with that money wasted on stupid newspapers :D nice day

---

### Post by smo0th on 2010-01-11
everyone likes puppy(me too), although you may want to try [vector linux]("http://vectorlinux.com")

---

### Post by Sef on 2010-01-11
Moved to Community Cafe.

>  i dont know what the saying"on the money" means

It means that you are correct.

---

### Post by replikanxxl on 2010-01-11
> **Sef said:**
> Moved to Community Cafe.



It means that you are correct.

thanks for the move and the illumination :popcorn:

---

### Post by Warpnow on 2010-01-11
Definitely, definitely give Slitaz a try.

---

### Post by Project PWNED on 2010-01-11
Debian minimal install will work for you, install IceWM or IceWM-lite after your post install to get a less resource intensive Windows Manager up. Or you can install Ubuntu 9.10, through an alternate installer, and when you post install - do IceWM-lite. No need to bother with "specialized" distributions that are just repackaged larger distributions meant for niche markets. 

A "slow" PIII 933Mhz is a decent Linux box. I was running Ubuntu 9.10 on an Intel Celeron 400Mhz, 256mb RAM with IceWM-lite. Compiles were slow, but the machine worked.

---

### Post by kyuubi777 on 2010-01-11
i got Gos 3.0 running gnome to install and run perfectly on a 10-14 year old dell tower
566Mhz cpu
64megs ram initial.. recently bumped it to 256 otherwise live cd would have failed
7Gb hdd

terrible specs, but it's running only a second slower than my laptop @ 1.66Ghz + 1G sdram
pretty impressive stuff considering it had windows 98 on it before which allowed for no wireless capabilities and terrible graphics

---

### Post by replikanxxl on 2010-01-11
thanks for the detailed advice. for doing what u say , i need a HDD perhaps ? or will i build my own Live CD and a mechanism for saving settings at log out ?

---

### Post by replikanxxl on 2010-01-11
> **smo0th said:**
> everyone likes puppy(me too), although you may want to try [vector linux]("http://vectorlinux.com")

actually vector linux was the only one i could experience Internet. but as i said before , it was not running easy and smooth like puppy

---

### Post by replikanxxl on 2010-01-11
> **Warpnow said:**
> Definitely, definitely give Slitaz a try.

right now i tried slitaz and its really good for web as well. Automatic connection management and a smooth running firefox. Visuals are fine as well

---

### Post by starcannon on 2010-01-11
> **replikanxxl said:**
> 

For conclusion , i can say that it feels like Puppy Linux was the one that hit the right balance between the visuals and performance versus system requirements. 

I agree, puppy ftw on my old jurassic-ware.

---

### Post by phrostbyte on 2010-01-11
Puppy Linux is pretty good.

---

### Post by johnboy1313 on 2010-01-11
Puppy Linux is good for slower systems, I ran damn small linux on my G1 when i had it, that was fun too

---

### Post by chris4585 on 2010-01-11
DSL really is amazing, I got it to install on a computer with 24mbs with a cpu of 166mhz.  This is an older version of DSL though.

---

### Post by sliketymo on 2010-01-11
You may at some point want to give Absolute Linux a spin.It is based on Slackware.Doesn't seem to be terribly bloated,and seems to run pretty snappy for me on an old Dell laptop with a 40 Gig HD.

---

### Post by replikanxxl on 2010-01-12
> **sliketymo said:**
> You may at some point want to give Absolute Linux a spin.It is based on Slackware.Doesn't seem to be terribly bloated,and seems to run pretty snappy for me on an old Dell laptop with a 40 Gig HD.

Whats the CPU and RAM ?

---

