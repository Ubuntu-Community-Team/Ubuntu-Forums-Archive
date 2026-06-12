---
title: "Should I switch to Ubuntu GNOME from Windows 10?"
date: 2017-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by justint15 on 2017-08-16
Hello,
I am considering switching to Ubuntu GNOME 17.04 from my Windows 10 Machine. I don't request much from my OS; just normal browsing, speed, videos, and the like. Windows 10 has had its bad days with me. BSODs, Slow performance, needed to wipe drive and reinstall Windows, other annoyances, ect. have occurred on this Windows 10 "expedition." I have looked at Ubuntu GNOME and it really caught my eye. I hear that Linux has all the features (and drivers) that Windows has and more without the frustration and angst that comes with Windows. Should I go full-time Ubuntu GNOME, or should I stay with Windows? What are the pros and cons?

---

### Post by Autodave on 2017-08-16
Pro: MUCH safer than Windows. Faster, too.

Before we go any further though, please reply with specs of your machine. Desk or laptop? Video card or on board video?  Wired or wireless ethernet?

---

### Post by Autodave on 2017-08-16
If you eventually got with Ubuntu, I would stick with the long term releases.

Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release. Unless you need the bleeding-edge release, stay with the LTSs.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by justint15 on 2017-08-16
It's a Toshiba Satellite C55-B laptop with a dual core Intel Celeron processor at 2.16 GHz. It has Intel HD Graphics and has wired Ethernet support, even though I use Wi-Fi.

---

### Post by vocx on 2017-08-16
> **justint15 said:**
> It's a Toshiba Satellite C55-B laptop with a dual core Intel Celeron processor at 2.16 GHz. It has Intel HD Graphics and has wired Ethernet support, even though I use Wi-Fi.
The Celeron processor is meant for the low-end consumer market, so it won't be the fastest in Windows or Linux. You should be aware of this.

The Intel HD Graphics is well supported in Linux. It is not a dedicated graphics card for playing video games, but it should be sufficient just for displaying your desktop and running a few videos here and there.

You should check the specific model of the Wi-Fi card. There are two things that cause problems for Linux systems, the video drivers for Nvidia and AMD/ATI dedicated cards, and the Wi-Fi drivers. Some Wi-Fi cards work very nicely with Linux, and some others are troublesome. So inform yourself before jumping in. Have those bookmarks ready to install the appropriate Wi-Fi drivers if needed.

Also, please be very honest with yourself as to why you want Linux. Linux is not, and never will be Windows. Don't just assume that everything will be the same, because it will not. You still have to learn a lot about the Linux operating system. Do not be like those people that want a different system (Linux), but at the same time they want it to be the same as what they know (Windows). That's a paradox. [https://ubuntuforums.org/showthread.php?t=2368692&p=13676034#post13676034](https://ubuntuforums.org/showthread.php?t=2368692&p=13676034#post13676034)

---

### Post by Impavidus on 2017-08-16
Pro: Every problem can be fixed. Contra: Fixing it may require a brain.

Feel free to try Ubuntu or Ubuntu Gnome, but keep in mind it's not a drop-in replacement for Windows. On weaker hardware, you may prefer one of the light flavours. Some people love Linux from the first day, others can never adapt.

---

### Post by Mark Phelps on 2017-08-16
I've been using Windows and Linux distros for well over 10 years and I know from experience that each has its pros and cons compared with the other.

In terms of very new hardware, there is no question that Windows has the drivers advantage -- as the new hardware comes with Windows drivers.  Most manufacturers don't bother with Linux drivers, so it takes the community a while to catch up.

As to frustrations,  IMHO, Win10 has many more than any previous Windows version -- due primarily to decisions that MS has made.  Most common problems are related to forced updates and new OS versions coming out every few months -- which combine to make an unstable environment.  

But ... I've been using Win10 since the earliest days of the Insider program -- and I've never run into a single BDOS or encountered a performance problem.  

So, if you are encountering these with a PC that came with Win10 preinstalled, that implied underlying hardware problems that installing Linux is NOT going to fix.

As others have indicated, Linux is not a free version of Windows, but instead, a free alternative to Windows -- and one that will take some time to learn in order to use it effectively.

As to Interface, I personally prefer Gnome.  I have used Smartphones since they first came out, and the LAST thing I want is that kind of UI on my desktop.  So, Gnome has a look and feel that I like a lot better than BIG BUTTONS.

My suggestion is to create install media and run from that in LIVE mode -- to see how well your hardware is detected and the right drivers are loaded.  Anything then that does not work can range from trivial to impossible to fix -- as some OEM PCs come with hardware for which Linux drivers simply do not exist.  And those same OEMs generally do NOT supply Linux drivers.  Better to find out about hardware problems BEFORE you wipe the PC and then end up with an unusable computer.

---

### Post by vocx on 2017-08-16
> **Mark Phelps said:**
> 
But ... I've been using Win10 since the earliest days of the Insider program -- and I've never run into a single BDOS or encountered a performance problem.  

So, if you are encountering these with a PC that came with Win10 preinstalled, that implied underlying hardware problems that installing Linux is NOT going to fix.

What is BDOS? Blue death of screen?

Not necessarily a problem with the hardware, it could also be a problem with the software. If a driver is badly programmed in Windows, but correctly programmed in Linux, the one in Linux will work better and without crashing. So, a crash is no confirmation that the hardware is bad. I get what you mean here, but I think it is not really like that.

By the way, this is one of the advantages of free software development. If there is a specification or standard, you can almost guarantee the Linux implementation will be better because it will be developed in the open and anybody can contribute by pointing out errors, or shortcomings, whereas in a closed environment you basically have to trust that the developers of that software have correctly implemented the functionality, and if they didn't then there is not much you can say about it.

---

### Post by vasa1 on 2017-08-16
> **Mark Phelps said:**
> ...
My suggestion is to create install media and run from that in LIVE mode -- to see how well your hardware is detected and the right drivers are loaded ...
+1

And this is essential, though a bit dated, reading: [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by handydandyhim on 2017-08-17
After having made the switch myself earlier this month I have to echo the response of others that you should only make the switch if you are looking for an alternative and are fine with missing out on exclusive software. I have played around with multiple distros in the past and almost used Mint as my dedicated OS 2 years ago. One thing you must realize is that there may be some frustrating nights trying to get things to work but there is a huge community willing to help. I'm using Ubuntu GNOME and find that I enjoy it more than the Unity desktop, but that's really just preference.

---

### Post by leunam12 on 2017-08-17
I have encountered multiple problems with Windows 10 such as missing fonts ( I have to run a script that deletes the font cache file an restart every time fonts are reported as missing), messed up printer drivers, and resetting of settings on my Wacom tablet after every update. Also there are forced updates and restarts. Additionally, after every upgrade windows 10 will store the upgrade file and other information that takes up a lot of disk space. I just recovered 17 GB of space after a windows 10 upgrade on my tablet. On a 32GB ssd that is a lot of disk space taken up by an upgrade, so I decided to downgrade to windows 8.1 on two computers and I am thinking that I am going to downgrade a third one.

So, consider downgrading to Windows 8.1 as an alternative to Windows 10. Ubuntu is great and that is what I use on my main computer but Windows may be necessary depending on what you are doing. For internet surfing and watching videos and stuff like that I would go with Ubuntu.

---

### Post by wildmanne39 on 2017-08-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Perfect Storm on 2017-08-17
Perhaps dual-booting as a start to get familiar with it.

---

### Post by kansasnoob on 2017-08-17
> **Artificial Intelligence said:**
> Perhaps dual-booting as a start to get familiar with it.

+1!

I recently went back to dual-booting with Windows after being 100% Ubuntu for nearly a decide. I did so mostly because there are ongoing (albeit intermittent) problems streaming videos in Linux. They can always be "worked around" but the ultimate "workaround" is simply dual-booting (or installing Windows in a VM if hardware specs are up to it). I still use Ubuntu nearly all the time, but if I encounter a streaming problem with a specific website I just reboot and try it in Windows - easy and no brain power involved.

My biggest frustration with Windows 10 is updates - especially BROKEN updates :mad: Of course I still prefer Ubuntu just because I've grown so accustomed to using Linux apps. Whenever I need to use (or fix) Windows (beyond Chrome or Firefox) I feel like a lost, blind kitten! Thankfully a quick Google search finds a multitude of people with the identical problem so finding solutions is somewhat easy.

---

### Post by QIII on 2017-08-17
Hello!

I am often frustrated by the use of the word "switch".  There is absolutely no reason to switch when you can use both without violating some natural law of the universe.

The Linux community does itself no favors by trying to convince people to "switch" as if one were obliged to be monogamous.

+1 to dual booting.

---

### Post by Geoffrey_Arndt on 2017-08-17
Dual-Booting is really a sub-optimal way to run two OS's.   

A much safer and long-term effective way is to run Windows on a fast internal SSD type device, and optionally to store data on another internal disk such as 500 to multi-GiB HDD.

The second OS (Ubuntu, Solus, Manjaro etc.) is installed on a fast external usbv3 SSD such as the portable SanDisk 500 SSD (see link below)).

A bootable USB Flash-Stick (aka Thumb Drive) with the Live OS/Installer is used to do a full install on the SanDisk SSD - - important to install Grub on the SanDisk.   Will not affect normal UEFI boot if device is not plugged in - - meaning before running any Windows OS updates, the Linux OS can be safely sandboxed by just unmounting the SSD.

[https://www.youtube.com/watch?v=4qtr9QaYJ7U](https://www.youtube.com/watch?v=4qtr9QaYJ7U)

---

### Post by justint15 on 2017-08-17
I do understand that Linux will never be Windows, but that is one of the reasons why I am switching. I WANT more freedom. I WANT a better desktop environment. I know that Linux is good for me because of that. I also like the idea of trying GNOME before I wipe, and I will do that before I commit myself.

---

### Post by justint15 on 2017-08-17
Would I be able to get rid of Windows after, if I don't feel the need for it anymore? (Without causing any catastrophic problems, that is?)

---

### Post by metalbiker on 2017-08-17
hello to you! first of all, thank you for considering making the switch to Ubuntu Gnome! It's a wonderful OS and Ubuntu itself has a lot of hardware support and your laptop should be good to go. Linux, specifically Ubuntu, offers a lot of pros: safe (nearly 100% from viruses, malware, hacking due to its very own, built-in anti-virus/malware software/code and firewall), speed: doesn't take a huge amount of hardware resources to function, free: you can download it and put it on as many computers as you want and there's no fee unless you choose to pay for customer support through Canonical and perhaps the Ubuntu Advantage and Ubuntu Live Path, all of which can be read on ubuntu.com. 

Other pros: recently Windows 10 was shown to have a major exploit in its code and causes it to be very vulnerable and that exploit may not be corrected with an update for some time, if it hasn't already, and that's one of the biggest issues with Windows is that the code tends to have way more problems, possibly due to be closed source with a dedicated development team instead of the way Ubuntu does it with many, many volunteers and open calls for testing, which is what I'm doing with ubuntu 17.10. But, Ubuntu and other distros of Linux are not without issues either, but, generally, if an issue arises, it's corrected fairly quickly due to our excellent infrastructure (i.e. launchpad.net for bug reporting through the terminal using a specific command which you can learn as well).

Now, the cons: the biggest con with Ubuntu, and most of us users of it know this, lack of support for major games. Now, we do have our own games that are clones of major titles and even a growing independent game development community, but games like Call of Duty don't have support for Linux out of the box. it takes special software to get a lot of those games to run on Ubuntu or anything Linux. that's about the only con with it and that's changing as of now anyway. 

but, the pros, IMHO, easily outweigh the cons. i'm not a major gamer so it doesn't really bother me that much but there's days where i do wish i could load Call of Duty or something like that but we do have Steam support and there's some good titles there as well. 

You should definitely give Ubuntu a try before making a final decision and this involves creating a live USB/disk which is fairly easy to do and I know it's been stated before in this thread.

But, if you do decide to make the switch, after a very thorough review/viewing of it, then you'll be greatly pleased with a lot of people here to help with any questions you may have going forward. 

And so you know, Ubuntu Gnome will no longer be a separate flavor or Ubuntu. The Gnome desktop is going to be used in Ubuntu 17.10 and going forward with it just called Ubuntu. The unity DE is no longer being used but if you get Ubuntu Gnome 17.04 now, when 17.10 comes out, you'll be prompted to upgrade to it if you so choose to do at that time. The DE will stay Gnome with Ubuntu stylings, of course. 

Welcome aboard!

---

### Post by metalbiker on 2017-08-17
yes, most certainly! you can go through the install of Ubuntu Gnome again and choose to have it be the only OS on your laptop. You'll just choose erase windows and install ubuntu in the installation options window.

also, on another note, if you're just going to try ubuntu gnome without installing it first, there should be an icon on the desktop for you to install it then. just double click that and it'll take you through the process of it.

---

### Post by Geoffrey_Arndt on 2017-08-17
JustInt15 . . . 

Regarding your post about just getting rid of windows - - be careful as removing windows and the boot partition can cause problems for booting to any installed OS including Ubuntu.    Read up on how to do first.

---

### Post by justint15 on 2017-08-17
I thought that it would cause problems with Ubuntu, after hearing it from somewhere. (I think it was the Ubuntu Wiki.)

---

### Post by bluemagoo on 2017-08-31
Very good advice.

> **vocx said:**
> The Celeron processor is meant for the low-end consumer market, so it won't be the fastest in Windows or Linux. You should be aware of this.

The Intel HD Graphics is well supported in Linux. It is not a dedicated graphics card for playing video games, but it should be sufficient just for displaying your desktop and running a few videos here and there.

You should check the specific model of the Wi-Fi card. There are two things that cause problems for Linux systems, the video drivers for Nvidia and AMD/ATI dedicated cards, and the Wi-Fi drivers. Some Wi-Fi cards work very nicely with Linux, and some others are troublesome. So inform yourself before jumping in. Have those bookmarks ready to install the appropriate Wi-Fi drivers if needed.

Also, please be very honest with yourself as to why you want Linux. Linux is not, and never will be Windows. Don't just assume that everything will be the same, because it will not. You still have to learn a lot about the Linux operating system. Do not be like those people that want a different system (Linux), but at the same time they want it to be the same as what they know (Windows). That's a paradox. [https://ubuntuforums.org/showthread.php?t=2368692&p=13676034#post13676034](https://ubuntuforums.org/showthread.php?t=2368692&p=13676034#post13676034)

---

### Post by bluemagoo on 2017-08-31
Very good advice; I bought a discounted Inspiron tower last year specifically for running Ubuntu, AMD A8, 1 TB hard drive, integrated graphics, 16 GB of main memory.  It came with Windows 10 Home, and I made the necessary Dell re-install thumb drive.  I have tried it as native Linux, & native Win. 10;  Windows 10 is "ok", but just, "ok".  less stable, with regular forced reboots of updates.  Doesn't seem to handle VMware well as a Win. 10 host, and Linux guests have occasional sound issues.  But the system really shines as a Ubuntu computer, with a VMware Win. 7 guest.  So, I agree, having both is good, no reason to be one way or the other, and the technology today easily allows both to co-exist.

> **QIII said:**
> Hello!

I am often frustrated by the use of the word "switch".  There is absolutely no reason to switch when you can use both without violating some natural law of the universe.

The Linux community does itself no favors by trying to convince people to "switch" as if one were obliged to be monogamous.

+1 to dual booting.

---

