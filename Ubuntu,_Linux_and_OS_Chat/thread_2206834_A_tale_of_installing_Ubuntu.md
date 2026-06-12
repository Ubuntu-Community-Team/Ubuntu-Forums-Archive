---
title: "A tale of installing Ubuntu"
date: 2014-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by jwn-2 on 2014-02-21
About a month ago I decided to change over to Linux Ubuntu, and without a doubt, this was the most difficult task I have ever attempted.
 
I started by downloading Ubuntu 13.10. No problem so far. Then I learned I need a CD drive or live USB to install. What the hell is a live USB? My notebook doesn’t have a CD drive, so I will have to learn what a live USB is. Googled it. Okay, it is one that you can boot from. So how do you create that? Googled it. Found Linux Live Creator. It is Linux, it must be good. Download and install. O shucks, my USB flash drive is to small. Go buy a 16 gig one. Make my live USB drive. Try booting from it. Errors everywhere. No Ubuntu. Try creating and running again. And again, and again and again. No luck. Visited this forum. Read something about unetbootin. Googled it. Okay, it is another live USB creator. Download. Create live USB. Boot. And what do you know, ubuntu started correctly. Go celebrate my success with a beer. After all it took me more than a week just to get here!
 
Now I just have to install Ubuntu to my hard disk and I am a for a way. I wish!!! All went smoothly up to a point where everything halted with a message that I have several options to try and remedy the problem. I can’t remember all the options any more, but amongst them was redownload the install file, reburn the CD at a lower speed (which CD, I am using a live USB), and moving my computer to a cooler environment. I tried them all. Again and again and again. I even bought another flash drive. But the install process halted time and again at exactly the same spot.
 
Yesterday I decided to buy a USB CD drive, burned an install CD and installed ubuntu successfully, all in one day. I am not going to celebrate my success yet with another beer though. I do however really hope that Ubuntu will be worth all this trouble.
 
Now I am pretty sure that you clever guys who created Ubuntu (which is claimed to be the best OS in the world) can come up with an easier way to install it without a CD drive. For instance just a normal executable program that can run on any OS (including Windows). I am sure it can’t be that difficult!!!

---

### Post by QIII on 2014-02-21
Not a support request.   Moved to ***Ubuntu, Linux and OS Chat.***

---

### Post by mastablasta on 2014-02-21
things that could have gone wrong : 
- downloaded image is not good - MD5sum check solves this issue
- usb drive is of poor quality

solution - well you found one another one is to get official CD/DVD or USB from ubuntu shop... :-) or to follow the file check procedures. remember downloaded and created image must match exactly to the one on server. to check download use md5 hash. to check the "burned" image there is a utility available on boot.

> **jwn-2 said:**
> Now I am pretty sure that you clever guys who created Ubuntu (which is claimed to be the best OS in the world) can come up with an easier way to install it without a CD drive. For instance just a normal executable program that can run on any OS (including Windows). I am sure it can’t be that difficult!!!

1. people here are for the most part not those who created this system. this is just support forum. developers rarely visit it. you will get enthusiast and dedicated people offering technical support for free.
2. there is an easier way that doesn't include the CD drive. use a USB stick and boot from it, select install.
3. normal executable program is not possible when installing a CD. have you ever installed windows? "normal" executable from windows won't run on MacOS, Andorid, iOS, Solaris, Linux.... system architectures are completely different. you can't have one executable to rule them all. so not only it would be difficult but nearly impossible to create such a thing to install operating systems.

even windows when you install it on empty hard disk will actually load parts of it's system into ram so you can at least use some basic components of the computer in order to instal the operating system to it's hard disk. can you use USB to install windows? i believe you can (at least i know you can use it to restore windows) but not without 3rd party tools. i knwo this because i have a windows netbook where i cretaed windows restore/backup on USB and then i installed Kubuntu on it from USB key. there are no CD/dvd drives on netbooks and ultrabooks.

one more thing - next time when you have trouble visit the ubuntu IRC channel, things will get resolved a lot quicker. or if you can wait a bit create a post here. i am sure people will help you resolve th eissues without contant trips to the shop and buying things you do not need to buy.

---

### Post by buzzingrobot on 2014-02-21
> **jwn-2 said:**
> About a month ago I decided to change over to Linux Ubuntu, and without a doubt, this was the most difficult task I have ever attempted.
 
I started by downloading Ubuntu 13.10. No problem so far. Then I learned I need a CD drive or live USB to install. What the hell is a live USB?

You need some medium -- USB, CD, DVD, etc. -- to hold the OS you wish to install. Same applies if you want to install Windows or OS X.  

It's unfortunate you had such difficulty. Your main difficulty seems to have been correctly creating the live boot USB.  I've found USB sticks to vary in quality, and, in general, to be less reliable than using a CD/DVD.  The web, too, is strewn with bad advice about creating a bootable USB.

 >   So how do you create that? Googled it. 

Ubuntu provides excellent instructions for creating installation USB's and CD/DVD's:  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop). 

>  O shucks, my USB flash drive is to small.

The install image for the current release is less than one gig. I'm not sure you can buy a USB stick that small.

Are you sure you weren't following advice on how to *install* Ubuntu to a USB drive, rather than how to create a bootable USB?

  > After all it took me more than a week just to get here!

Should have taken about 30 minutes, following the appropriate advice.
 
> Now I just have to install Ubuntu to my hard disk and I am a for a way. I wish!!! All went smoothly up to a point where everything halted with a message that I have several options to try and remedy the problem. I can&#8217;t remember all the options any more, but amongst them was redownload the install file, reburn the CD at a lower speed (which CD, I am using a live USB), and moving my computer to a cooler environment.

Well, I've installed Ubuntu many times and I've never seen the installer spit out those kind of options.

Where did you acquire the iso image you used for the install?  What version of Ubuntu?  What's your hardware?

> ..an easier way to install it without a CD drive. For instance just a normal executable program that can run on any OS (including Windows). I am sure it can&#8217;t be that difficult!!!

It's the same install image and the same installer script on a CD a DVD or a USB. They are just different kinds of media to hold the thing.

You can't really have a "normal executable program" running as a normal application install a new OS to that machine in a manner that would be safely handled by the vast majority of consumers. Again, installation of Windows or OS X is handled the same way as Ubuntu:  You boot off the install medium and that process has full control of the hardware.

---

### Post by lykwydchykyn on 2014-02-21
> **jwn-2 said:**
> About a month ago I decided to change over to Linux Ubuntu, and without a doubt, this was the most difficult task I have ever attempted.


You must live a charmed life.  
>  
Now I am pretty sure that you clever guys who created Ubuntu (which is claimed to be the best OS in the world) can come up with an easier way to install it without a CD drive. For instance just a normal executable program that can run on any OS (including Windows). I am sure it can’t be that difficult!!!

I just thought I'd point out that you can purchase ready-made install media (CD, DVD, USB) for many linux distros from websites like [http://www.osdisc.com](http://www.osdisc.com).  You can also purchase preinstalled Linux computers from retailers like System76, Dell, and HP.

As for the window executable idea, there used to be something like that, but it was rather buggy and subject to some major limitations, so it was dropped.  I've seen other projects to do similar things (e.g. [http://www.goodbye-windows.com](http://www.goodbye-windows.com)) and they've been rather unstable and inconsistently supported.

Installing an operating system is really just one of those things that requires a bit of patience, research, and knowledge.  There's probably no way around that at this point.

---

### Post by Tar_Ni on 2014-02-21
I understand you perfectly! First time I attempted installing Ubuntu I didn't know what I was doing and ended up screwing up Windows XP and got Ubuntu with no sound!

I learned form my mistakes, which costed me 100$ to pay for a computer technician. I know it sounds silly but out of windows I was really a newbie.

Second attemp, I read carefully the explanation on how to boot a USB flash with the Universal USB installer and got Ubuntu on my 2 GB flash drive. Got to the Bios -> hard drive > change the order of booting  and here you go. The Ubuntu installer is very user friendly (compared to other distro) so after that it was very easy.

But hey, if this is too much a pain for you, I know it is for some people, you can get a USB flash drive already booted up ready to install and CDs/DVDS for reasonable prices and shipping here: [https://www.osdisc.com/](https://www.osdisc.com/)  Also there: on-disk.com

You've got just about every linux distros both 32bit and 64bit with the shipping to you mailbox.

Good luck and hopefully it was a leanring that will serve you again in the future.

---

### Post by buzzingrobot on 2014-02-21
> **Tar_Ni said:**
> I understand you perfectly! First time I attempted installing Ubuntu I didn't know what I was doing and ended up screwing up Windows XP and got Ubuntu with no sound!


Installing Ubuntu, or any other OS, alongside Windows, aka dual booting, makes a lot of sense for new folks. It's a pity, though, that it's gotta be the most problematic thing they will do in Linux.

Windows and OS X are preinstalled for a good reason (besides the cornering-the-market reason).  Installing an OS can expose you to boot sectors, boot loaders, primary partitions, extended partitions, swap partitions,  fdisk, parted, boot flags, mbr, gpt, BIOS, UEFI, safe boot, Secure Boot, etc., etc. that can be a mine field for mistakes.  Add in the fact that Windows assumes it is the only OS on the machine and works hard to keep it that way, and it's a miracle any dual booting setup goes right.

Ubuntu running off a USB stick is not terribly slow. If I was asked, I'd recommend newbies try to make up their mind about Ubuntu using a live USB image.  If and when they are ready to make the move away from Windows, they shouldn't dual boot.  They should just make the commitment and install Ubuntu as the only OS on the machine.

---

### Post by monkeybrain20122 on 2014-02-21
> **buzzingrobot said:**
> 
If I was asked, I'd recommend newbies try to make up their mind about Ubuntu using a live USB image.  If and when they are ready to make the move away from Windows, they shouldn't dual boot.  They should just make the commitment and install Ubuntu as the only OS on the machine.

+100! It is MicroSoft which makes dual booting so problematic and to add insult to injury some uninformed people would blame Linux for their bad experience in setting up a dual boot while Windows is the only source of their woes (like some guy who started a thread saying the difficulty in installing Ubuntu proves Windows 8 is still the best after mucking up his dual boot the nth time)

Ubuntu doesn't have to be the only OS, multibooting with other Linux distros is usually easy, just Windows is causing all the problems.

---

### Post by craig10x on 2014-02-21
@moneybrain20122: and it was until the windows 8 computers came out...now it's become a real pain...
yes, i would say the advice to try it on a usb stick for a while is not a bad idea...and if he likes it, unless there are critical programs he just has to have windows for, i'd say go 100% ubuntu...but of course, make back up discs for your windows install, just in case you ever change your mind or need to put things back to the way the computer originally came...

---

### Post by kevdog on 2014-02-22
I wish I could have experienced what you did.  I love troubleshooting. I've installed Ubuntu along with a lot of other distros.  Usually they are very straight forward -- almost to the point of boring

---

### Post by coldraven on 2014-02-22
I do all my installs from an old 1GB SD card, it works like a charm. Most machines have a SD card slot these days.
I make the card bootable with Unetbootin which can be found here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

