---
title: "Lubuntu 12.04 wont load"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by theducksfan2010 on 2012-04-03
I installed Lubuntu 12.04 on a USB HDD using my Compaq laptop for use on my Acer Travelmate 230. Since it was installed on a different computer the grub options do not line up on the Acer as it is the only OS, but it would still load. I tried to suspend the computer instead of shutting it all the way down and now it will not load again. 

It is stuck at:
ata_id[200]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument.

If I choose the (recovery mode) it is getting stuck at:
[  19.467621] ---[ end trace 1519a5a6208e5bfd ]---

what can i do to get this to boot up again??

---

### Post by amjjawad on 2012-04-04
Hello there,

Thanks for taking the time to start a new thread :)
Now, we can continue our discussion in the best place!

Kindly go through this guide: [http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

and tell me whether you have followed the same steps or not?

If yes, then we need to try something else.
If no, please follow the steps in here: [http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Another suggestion that just came to my mind. Have you tried to install Lubuntu 11.10 or any other stable version?
I'm trying to figure out whether it is a bug with 12.04, something wrong in the steps somewhere or perhaps it is a hardware issue. We will find out, no worries :)

You know what? I will try to install Lubuntu 12.04 on an USB Drive today and will get back to you. I will use 4GB USB Drive.

Thanks!

---

### Post by amjjawad on 2012-04-04
On ASUS F3F Laptop, I'm trying now to install Lubuntu 12.04 Beta 2 32-bit version from a LiveUSB to a 4GB USB Drive :)

This is my first time to install from USB to another USB :)

Will keep you updated ;)

---

### Post by amjjawad on 2012-04-04
Hi again,

Done with installing Lubuntu 12.04 Beta 2 - 32bit version from LiveUSB to a 4GB USB Drive.

Installation done on ASUS F3F Laptop with Intel Core Due CPU and 512MB RAM with 120GB internal HDD.

I rebooted and the ASUS machine booted normally from the USB Drive.

In order to be 100% sure, I booted from my main machine (Lenovo Core i5 2nd generation with 4GB RAM) and the USB drive worked without a problem. I'm actually typing this from there :)

So, I don't think there is a problem with Lubuntu 12.04 Beta 2 but rather something wrong either with the steps or the hardware but we are not so sure yet so the discussion still open :)

Kindly check the attached picture.
This is the MOST important step that will save lots of time and effort. As long as GRUB2 for Lubuntu 12.04 Beta 2 is installed in the MBR of your USB Drive, everything should be OK.
Now, I can take this USB Drive and boot from it on any machine without a problem. In case I want GRUB2 on my USB Drive to show the systems where I'm using it, I just need to run "update-grub" from LXTerminal and that is all :)
I don't need to do it now because I'm doing this test for you and "update-grub" is not needed (because it is a test).

Let me know if you need more information. I will keep this USB and won't use it in case we need to do more tests :)

Edit:
I have a 3rd machine so I will try to boot from this USB drive on there and will let you know.

---

### Post by theducksfan2010 on 2012-04-05
So you installed it onto a thumb drive, close to what I am doing, but I am using a USB Hard Drive. You installed grub to sdb? Did you have other Operating Systems on the computer you used to do the install?? Mine had 2, but like the computer I used for the install everything was on sda. This laptop I am trying to use does not have any hard drive in it so the external USB HD registers as sda.

---

### Post by theducksfan2010 on 2012-04-06
I found this in one of the other threads, could it be part of the problem????

 

 
Join Date: May 2007
Beans: 8,725
Re: Is a USB install PC specific?
Quote:
Originally Posted by Cheesemill  
For Windows yes, but I was under the impression that Linux probes the hardware and loads the correct modules every time you boot.

Generally, yes. But if you load restricted drivers as part of the initial USB setup, it will not replace them with other drivers.

---

### Post by amjjawad on 2012-04-07
> **theducksfan2010 said:**
> So you installed it onto a thumb drive, close to what I am doing, but I am using a USB Hard Drive.
Same concept, same approach, same everything except the size is different ;)
Size here is not the case, if you check my guide that I posted earlier, if you follow it as it is, you should be good to go unless something is wrong that we need to investigate. 

> You installed grub to sdb? 
Yes indeed but to make it easier to understand, let's forget about the "sdb" or "sda" or "sdc", the general rule here is:

>> Install GRUB2 in the MBR of the USB Drive.

So, whether that is /dev/sda, /dev/sdb, /dev/sdc, etc ... that does not matter :)

> Did you have other Operating Systems on the computer you used to do the install?? 

Yes indeed but again, that doesn't really matter. 

> Mine had 2, but like the computer I used for the install everything was on sda. 
If /dev/sda is your USB Drive then GRUB2 must be installed there. Yet again, the whole idea is to install GRUB2 in the MBR of your USB Drive and it doesn't matter whether it's USB Drive with 4GB or USB HDD with 1TB :D

> This laptop I am trying to use does not have any hard drive in it so the external USB HD registers as sda.

Which means there will be ONLY ONE drive listed and there is no other choice but to install GRUB2 to the MBR of that drive which will make your mission easier and less confusing :D

---

### Post by theducksfan2010 on 2012-04-07
> **amjjawad said:**
> Same concept, same approach, same everything except the size is different ;)
Size here is not the case, if you check my guide that I posted earlier, if you follow it as it is, you should be good to go unless something is wrong that we need to investigate. 


Yes indeed but to make it easier to understand, let's forget about the "sdb" or "sda" or "sdc", the general rule here is:

>> Install GRUB2 in the MBR of the USB Drive.

So, whether that is /dev/sda, /dev/sdb, /dev/sdc, etc ... that does not matter :)


Yes indeed but again, that doesn't really matter. 


If /dev/sda is your USB Drive then GRUB2 must be installed there. Yet again, the whole idea is to install GRUB2 in the MBR of your USB Drive and it doesn't matter whether it's USB Drive with 4GB or USB HDD with 1TB :D


Which means there will be ONLY ONE drive listed and there is no other choice but to install GRUB2 to the MBR of that drive which will make your mission easier and less confusing :D

Yes but I cant install it on the machine I want to use it on, meaning I had to install grub to sdb because the USB HDD showed as sdb when it was on this comp. But when I palce it on the comp I want to run it off it becomes sda. Only thing is it shows all of the OS form the installing computer in it still when they do not exist on the drive.

Right now it is stuck on the lubuntu screen with the 5 blue dots on it, if I hit escape it shows;

fsck from util-linux 2.20.1
/dev/sda1: clean, 123495/2411921 files, 76017/9649152 blocks

and it just sits there

---

### Post by amjjawad on 2012-04-07
> **theducksfan2010 said:**
> Yes but I cant install it on the machine I want to use it on, meaning I had to install grub to sdb because the USB HDD showed as sdb when it was on this comp. But when I palce it on the comp I want to run it off it becomes sda. Only thing is it shows all of the OS form the installing computer in it still when they do not exist on the drive.

Right now it is stuck on the lubuntu screen with the 5 blue dots on it, if I hit escape it shows;

fsck from util-linux 2.20.1
/dev/sda1: clean, 123495/2411921 files, 76017/9649152 blocks

and it just sits there


[http://ubuntuforums.org/showpost.php?p=9938663&postcount=1](http://ubuntuforums.org/showpost.php?p=9938663&postcount=1)

I know that thread has 16 pages and it's very old so can't remember where exactly I put that but I'm sure if you check the last two links at the bottom of that post, you may find what I'm trying to explain over here :)

When I did it with that ancient machine, it was listed as /dev/sdb on the computer I used to install and of course it will be listed as /dev/sda when I plugged the HDD back inside the laptop. There was only one drive (talking about the old OmniBook on that thread I just posted above) and that was the internal HDD but since I've used the mobile HDD enclosure with USB Connection then it's the same case as yours.

Hmmm, you know what? I can't remember what exactly I did? it's been two years now? not sure. Anyway, I connected the internal HDD of that old laptop to my PC and I honestly can't remember whether I disconnected the internal HDD of my PC or not? if I disconnected it, it means the HDD of the old laptop will be treated and listed as /dev/sda. If I did not disconnect the internal HDD of my PC while the other HDD is connected to the PC via USB connection, then it should be listed as /dev/sdb.

I don't think it does matter. I don't think that will effect anything. You are telling the BIOS to boot from Drive X and Drive X is the drive that you installed Linux (Lubuntu) onto, right? then as long as the BIOS is detecting that drive, we are ok but as long as we can't login to the desktop, that is a problem. 

Now, I think and I could be wrong, I think we are after GRUB2 not before. I mean, GRUB2 in your case has done the job but there is something ELSE that is preventing you to login to your desktop and use your machine. 

Again, if you go back to that thread of mine, you will find out that Lubuntu never worked on that machine and BIG YES, I was indeed stuck on the very same point as you are right now, the 5 dots. 

I'll not give up on you and will keep digging until we figure it out. However, I can't do it right now, it is too late here. I will come back later.

Thanks!

> fsck from util-linux 2.20.1
 /dev/sda1: clean, 123495/2411921 files, 76017/9649152 blocks

Have you tried to Google this? perhaps we can find something useful?

---

### Post by theducksfan2010 on 2012-04-07
I have got it to load 3 time, but that was last week, so I know it can work

---

### Post by theducksfan2010 on 2012-04-07
I actually read that thread about 3 weeks ago, when I was trying different versions of Puppy and looking for something that would boot on the Acer.

---

### Post by amjjawad on 2012-04-07
I found this while searching on other forum where I posted (I was trying antiX first on that ancient laptop of mine before my interest of LXDE began):

> **I disconnected all my internal HDDs on my PC**, took the HDD of that laptop out, put it on the USB Enclosure, connected to my PC and turned the PC on.

Obviously, GRUB was installed in the MBR of the USB Drive because there is no other drive anyway.

I think I did that just to be in the safe side. I still think sdb or sda doesn't matter.

Anyway, must go now and will be back later!

---

### Post by amjjawad on 2012-04-08
Hi,

Just now, two points came to my mind and I want to ask you about:

1- Have you tried Lubuntu 11.10 instead of Lubuntu 12.04?

2- Have you tried to boot from that External USB HDD from your other machine which already has an internal HDD?
If you manage to boot normally from that external drive  without any problem and was able to login, etc ... then the drive itself should be good. Don't just login, do some test on Disk Utility to make sure the drive is healthy.

Please try the above two suggestions before we carry on with our experiment :)

Thanks!


Edit:
When I did a search on:
> fsck from util-linux 2.20.1
/dev/sda1: clean, 123495/2411921 files, 76017/9649152 blocksI found ONE result only and that was this thread :)


P.S.

**A 3rd suggestion:**
Have you tried another USB Drive or HDD? it's also good idea to try another hardware and check if that will work without being stuck on the 5 dots. If you have a 4GB USB Drive, I strongly recommend to give it a go. After all, the installation will last about 15-30mins MAX and IMHO, there is no harm to try some other alternatives.

Also, you can check this out:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It will help you to make sure everything is installed in the right place. In fact, I'd like to see if GRUB2 is indeed installed in the MBR of that External HDD.

[IMG]http://pix.toile-libre.org/upload/img/1326204755.png[/IMG]

Create a bootinfo << is what I need to check. It will give you a link, don't close that pop-up and copy the link then paste it here. This will save your time and it's really very easy. Before, we used to do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Now, we don't really have to :)

Let me know if you need more information :)

---

### Post by theducksfan2010 on 2012-04-08
Yes I have used the HDD on the other laptop and it functioned great, I surfed the net ran programs, watched videos, all worked fine. I was able to get the computer to boot up on the live cd yesterday and it ran 12.04 extremely well. Fast, responsive, etc. 

I did replace the grub on the USB HDD yesterday while the live cd was running. I still have the ata_id errors and that is as far as I can get now. It will no longer make it the maintenance shell. 
Just now, two points came to my mind and I want to ask you about:
I had puppy running on it off a 4 GB thumb drive, but Puppy is fragile on this comp and would corrupt easy on shutdown startup and be trashed. I wanted a full feature OS (Ububtu based) on here and have run Xubuntu and Fedora on this machine off of this drive back in the Hardy Heron days.

Create a bootinfo << is what I need to check. It will give you a link, don't close that pop-up and copy the link then paste it here. Cant do because it wont boot, and I cant get the live CD to load again, I think the CD drive is old.



So I took the USB HDD and plugged it into the Compaq laptop (the one I am posting from now), and it still came up with the ata_id error but then quickly moved past it and the OS was up and running in about 45 seconds. But on the Acer it just sits at the ata_id error until it turns off or an hour has passed. So I know it can work, just doesn't yet....

---

### Post by amjjawad on 2012-04-08
I repeat my previous suggestions :)

1- Try to install Lubuntu on 4GB USB Drive and see if that will work or not?

2- Try Lubuntu 11.10 instead of 12.04.

I did a search on that error message:

> ata_id[200]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argumentI found a bug:[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/931135](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/931135)

I'm NOT sure how close that will be to your case?

I'm still trying to find something on google ...


Edit:
Try to do some search please using this: > [COLOR=Red]ata_id[200]: HDIO_GET_IDENTITY failed for '/dev/sda'[/COLOR]

---

### Post by theducksfan2010 on 2012-04-08
1- Try to install Lubuntu on 4GB USB Drive and see if that will work or not? I ran about 25 plus different OS's off of USB on the Acer and because of its age it doesn't work with most. I think it is something to do with the new build of Xorg. Even Puppy is getting to the point where it is losing support for the older machines that can't handle the new build of Xorg, I had better luck running it with Xvesa, but with the graphics card in the Acer, it is Very picky.

2- Try Lubuntu 11.10 instead of 12.04. Same issue with 11.10, I tried it before 12.04

I found a bug:[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/931135](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/931135)

Close but not the same - Anymore, we have goten passed that part of the problem a while back. I am actually using the USB HDD on my compaq right now to type this again. It still has the same errors but muscles on past them and boots up fully in less than a min from powering on.

I am going to look on Amazon for some memory for the Acer, I was really wanting to make it work with the 256MB, but am going to have to break down and invest some more money in the Frankenstein machine.

---

### Post by theducksfan2010 on 2012-04-09
I ordered another 256MB of RAM for it off of Ebay tonight.

---

### Post by amjjawad on 2012-04-10
You might be interested to have a look at this: [http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

;)

Oh, I did that while the internal HDD of that OLD machine was connected to my other Laptop via USB and it was /dev/sdb and ... that did NOT affect anything at all, it worked from the first time on OmniBook 4150 P2 with 64MB RAM, 4GB HDD, NO CD-Drive, broken machine and it is a must to take the HDD out and plug it to another machine and install from there :)

---

### Post by theducksfan2010 on 2012-04-11
> **amjjawad said:**
> You might be interested to have a look at this: [http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

;)

Oh, I did that while the internal HDD of that OLD machine was connected to my other Laptop via USB and it was /dev/sdb and ... that did NOT affect anything at all, it worked from the first time on OmniBook 4150 P2 with 64MB RAM, 4GB HDD, NO CD-Drive, broken machine and it is a must to take the HDD out and plug it to another machine and install from there :)

Nice!! NICE!! Nice!! I am getting this one to boot now, with a 5-15 minute boot time. I am posting this from it right now. I also ordered another 256MB of RAM for it off of ebay for $3.58 to double it to 512MB.

---

### Post by amjjawad on 2012-04-11
> **theducksfan2010 said:**
> Nice!! NICE!! Nice!! I am getting this one to boot now, with a 5-15 minute boot time. I am posting this from it right now. I also ordered another 256MB of RAM for it off of ebay for $3.58 to double it to 512MB.

So, can I say "Congratulation" or not yet? :D

---

### Post by theducksfan2010 on 2012-04-14
> **amjjawad said:**
> So, can I say "Congratulation" or not yet? :D

Not yet, it still has issues and glitches. When I get more memory  and the final version of 12.04 comes out I will start over again.....

---

### Post by amjjawad on 2012-04-15
> **theducksfan2010 said:**
> Not yet, it still has issues and glitches. When I get more memory  and the final version of 12.04 comes out I will start over again.....

If I were you, I would go for Lubuntu 11.10 and then, when Lubuntu 12.04 comes out, I will give it a go :)
For me, I can't wait all that long :P but yes, if I'm busy, I will not be able to do anything.

Let me know how things will go with you ;)

---

