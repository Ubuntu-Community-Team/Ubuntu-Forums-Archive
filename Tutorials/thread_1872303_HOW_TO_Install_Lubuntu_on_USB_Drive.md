---
title: "HOW TO Install Lubuntu on USB Drive"
date: 2011-10-30
forum: Tutorials
---

### Post by amjjawad on 2011-10-30
[CENTER][SIZE=4]
**[COLOR=Navy] HOW TO Install Lubuntu on USB Drive[/COLOR]**[/SIZE]
[LEFT][CENTER]


[LEFT][B]Can I install Lubuntu on USB Drives?
[/B]Yes, you can.


[B]What is the minimum size?
[/B]4GB USB Drive.


[B]What do I need to know or learn in the process?
[/B]Please have a look at:

In General: [Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755")
Specifically: [URL="https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu"]Lubuntu Installation
[/URL]
Just have a look at the above two links and you should be good to go.


[B]Any Preparations I need to start before installation to the USB Drive?
[/B]Yes, you need to prepare your USB Drive for the installation Process. It's highly recommended to do that before the installation.

Please have a look at: [How to Use GParted]("http://forum.lxde.org/viewtopic.php?f=8&t=31411")

GParted will help you to prepare your USB Drive so that you can easily install Lubuntu on.


[B]What release/version of Lubuntu do I have to use?
[/B]This guide will explain that using Lubuntu 11.10 32-bit. However, the release doesn't really matter. You can follow the same steps with any other release, even other variant such us Ubuntu or Xubuntu. Same concept.


**Okay, how do I do that?**

1- Download Lubuntu

2- Check MD5SUM

3- Burn the image (iso) to a CD

4- Plug your USB to your machine

5- Turn your machine on and then Enter BIOS

6- Make sure your CD-Drive is the FIRST DEVICE to boot from

7- Make sure your USB Drive is the SECOND DEVICE to boot. Some 
     BIOS detect/read USB Drive as HDD. In that case, please see this:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]


[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


In the above Screenshot, USB Drive got detected as **[COLOR=Red]USB-HDD0[/COLOR]**.
In that case, just set your **Hard Disk** *(as showed in the first Screenshot) *as the SECOND DEVICE to boot from.

8- In case your BIOS will detect your USB as something else rather than **[COLOR=Red]USB-HDD0[/COLOR]** then you need to select the correct option and set that as the SECOND DEVICE to boot from and set your Hard Disk as the THIRD DEVICE to boot from.

9- After you are done with BIOS, please Save and Exit.

10- Your machine will start booting from your Live-CD. Please follow the same steps in [Lubuntu Installation Guide]("https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu"). To summarize that:
a- Choose your Language
b- Choose Try Lubuntu without installation
c- You should see the Live Desktop after a while
d- If Try Lubuntu without installation didn't work then please [check this]("http://ubuntuforums.org/showpost.php?p=11398602&postcount=35").

11- From the Live Desktop, please run GParted and Prepare your USB for the Installation. [This guide]("http://forum.lxde.org/viewtopic.php?f=8&t=31411") will help you to do that step by step. I wrote it specially for this.

12- Once you are done with GParted, please start the Installation.

13- Please have a look at these Screenshots:

a- In this example, there is /dev/sda and there is /dev/sdb which are Internal HDD and also there is /dev/sdc which is the 4GB USB Drive. Please make sure to select the correct drive - this is very important.

[IMG]http://i44.tinypic.com/alok04.jpg[/IMG]


b- Because you have previously prepared your USB for the installation, the next steps will be very easy. Now, you just need to select the mounting points and choose to format as EXT4.

/dev/sdc1 will be your ROOT Partition. Note that, you don't really need /home partition here. Total Size is just 4GB so no need for that. After all, this is not meant for day-to-day use or long-run use.

[IMG]http://i44.tinypic.com/2r22l1c.jpg[/IMG]


c- Device for Boot Loader Installation MUST be:

[IMG]http://i41.tinypic.com/1zccp50.jpg[/IMG]


/dev/sdc ImationFlashDrive (4.1 GB) is the MBR of your USB Drive.

If you are going to install Lubuntu Boot Loader (GRUB2) to the MBR (sdc) of your USB Drive, then you are NOT going to mess with your Internal HDD and its Boot Loader no matter what OS you have there. 

This is the safest way to do it. Later, will explain in details how safe and good that is. 



d- Please, make sure this is the final screen that you'll see before you go on with the installation:

[IMG]http://i42.tinypic.com/2e1ufq1.jpg[/IMG]


e- Click on Install Now. The installation will start and once it's done, restart your machine.



**Now, what will happen?**
As long as your USB is plugged in AND as long as your BIOS has the same settings/configuration that you set at the beginning of this guide THEN ... your machine will BOOT FIRST from your USB Drive.


[B]What if I'll ignore what you explained and install Lubuntu GRUB2 to the MBR of my Internal HDD (sda in this example)?
[/B]It's okay to install Lubuntu GRUB2 to the MBR of your internal HDD but that will replace and overwrite whatever is installed on the MBR of your internal HDD. Above all, your USB MUST BE Plugged in ALL THE TIME because GRUB2 files will be stored in your USB Drive since you have installed Lubuntu over there.

[IMG]http://i41.tinypic.com/2vmdm9y.jpg[/IMG]

This is NOT recommended AT ALL. Please avoid that.

USB Devices are mobile devices that you can carry with you wherever you go. If you make sure to install GRUB2 during the above installation on the MBR of your USB Drive then you are basically creating a mobile OS that can work on any machine and you are not messing around with your internal boot loader.



[COLOR=Red]**Note:**[/COLOR] As always, this guide will be updated on daily basis if needed :)

Enjoy!

  [/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by Sef on 2011-10-30
Moved to Tips and Tutorials.

---

### Post by viperdvman on 2011-10-30
This should really apply to ANY of the *buntu distros. I've used steps very similar to these to install Oneric to one of my larger USB drives, which I use for test-driving on my desktop. Thanks for the post :)

---

### Post by amjjawad on 2011-11-04
> **viperdvman said:**
> This should really apply to ANY of the *buntu distros. I've used steps very similar to these to install Oneric to one of my larger USB drives, which I use for test-driving on my desktop. Thanks for the post :)

Yes, it should be similar :)
I do have actually a guide but it's old and it was talking about something else so this is more Lubuntu Specific :)

Thank you!

---

### Post by Chame_Wizard on 2011-11-04
At least it's easy to do.[IMG]http://i236.photobucket.com/albums/ff286/nfforums/NF%20smilies/_brofist__by_kaiser321.gif[/IMG]

---

### Post by sudodus on 2011-11-25
Than you for a nice how-to, amjjawad :KS

If we compare a
1. 'regular' live USB drive made from a lubuntu iso file with Ubuntu's tool or Unetbootin
2. persistent live USB drive made from a lubuntu iso file (with a casper-rw file)
3. live USB drive made by installation with your method

Is there any difference
A. how the computer hardware is recognized - portability to other computers?
B. how fast it boots and works?
C. how much drive space is occupied by the system (and how much is free to use)?
D. how it can be configured (installed programs and drivers) - stability and portability?

I guess you suggest your method (3.) for a computer with a small internal drive. But what would you suggest to make a USB drive with high portability but also some tweaking? So that you can carry your computer environment in your pocket on a USB flash stick.

---

### Post by amjjawad on 2011-11-25
> **sudodus said:**
> Than you for a nice how-to, amjjawad :KS
Glad you like it :)

> **sudodus said:**
> If we compare a
1. 'regular' live USB drive made from a lubuntu iso file with Ubuntu's tool or Unetbootin
2. persistent live USB drive made from a lubuntu iso file (with a casper-rw file)
3. live USB drive made by installation with your method

I haven't tried the 2nd method/approach so I can't answer anything related to that.

> A. how the computer hardware is recognized - portability to other computers?

I have installed Lubuntu 11.10 on USB Drive (Imation 4GB) on P4 PC, tried it on two different machines. It worked perfectly on Lenovo G570 Core i5 2nd generation with 4GB RAM + Intel Graphics Card (built-in) and it did not work perfectly on HP Pavilion DV6 Core i5 with 4GB RAM + 1GB ATI Graphics Card.

If I'll get more free time, I might try that on more different machines and see what will happen.


> B. how fast it boots and works?

Faster than LiveUSB and slower than Internal HDD installation. It's a very good choice (install to USB - this guide) because it's a middle choice with nice speed.

> C. how much drive space is occupied by the system (and how much is free to use)?

LiveUSB if I'm not wrong must take LESS space than USB Installation. As for FREE SPACE, that totally depends on the size of the USB Drive that you will use :)


> D. how it can be configured (installed programs and drivers) - stability and portability?

I haven't tried to update/upgrade the Kernel (USB Installation) but everything else, it should be the same (installing programs and updates).


> I guess you suggest your method (3.) for a computer with a small internal drive. But what would you suggest to make a USB drive with high portability but also some tweaking? So that you can carry your computer environment in your pocket on a USB flash stick.
Sorry, not sure what do you mean?

---

### Post by sudodus on 2011-11-25
> Quote:
 	 	 		 			 				[SIZE=1]I guess you suggest your method (3.) for a computer with a small  internal drive. But what would you suggest to make a USB drive with high  portability but also some tweaking? So that you can carry your computer  environment in your pocket on a USB flash stick. 			 		[/SIZE] 	 	 
Sorry, not sure what do you mean?

Well, I meant to compare persistent USB boot with your installation method, but since you have not tried persistent USB boot, I can't expect you to answer. I might test that myself, and come back to share the result (but it will take some days until I'm there).

Anyway, thank you again, amjjawad :-)

---

### Post by amjjawad on 2011-11-25
> **sudodus said:**
> Well, I meant to compare persistent USB boot with your installation method, but since you have not tried persistent USB boot, I can't expect you to answer. I might test that myself, and come back to share the result (but it will take some days until I'm there).

Anyway, thank you again, amjjawad :-)

You welcome and please feel free to share anything related to the topic with us ;)

---

### Post by ThickPizza on 2011-11-26
[quote=amjjawad]11- From the Live Desktop, please run GParted and Prepare your USB for the Installation. [This guide]("http://forum.lxde.org/viewtopic.php?f=8&t=31411") will help you to do that step by step. I wrote it specially for this.[/quote]

Is it just me, or is forum.lxde.org down? 

I'm loving Lubuntu, though. Personally, I'm running Ubuntu 11.10 on my laptop, but Lubuntu + remote desktop has allowed me to not only resurrect my parents old and outdated laptops, but allowed me to easily keep them maintained while I'm at school.

---

### Post by amjjawad on 2011-11-26
> **ThickPizza said:**
> Is it just me, or is forum.lxde.org down?
Yet again, it's down and I confirm that. I must move all my guides from there to Lubuntu One Stop Thread or a new thread. Better to keep everything here.


> I'm loving Lubuntu, though. Personally, I'm running Ubuntu 11.10 on my laptop, but Lubuntu + remote desktop has allowed me to not only resurrect my parents old and outdated laptops, but allowed me to easily keep them maintained while I'm at school.
Thank you for using and choosing Lubuntu :)

---

### Post by Borunco on 2012-02-22
Hi all, I had some time yesterday and decided to make a usb of Lubuntu. I followed amjjawad tutorial on this thread, and once again it was a flawless install. Thank you amjjawad for making such thorough tutorials.
I have a question, I have made copies with the cd/usb creater in Ubuntu, and can do it with a 2 gig usb drive. why can it be done with this tutorial? Don't get me wrong I like the end results here, I just want to know the difference for learning purposes.
Thank you
borunco

---

### Post by amjjawad on 2012-04-30
> **Borunco said:**
> Hi all, I had some time yesterday and decided to make a usb of Lubuntu. I followed amjjawad tutorial on this thread, and once again it was a flawless install. Thank you amjjawad for making such thorough tutorials.
At your service, my friend and I'm glad I still can help (not yet rusty) :)

> I have a question, I have made copies with the cd/usb creater in Ubuntu, and can do it with a 2 gig usb drive. why can it be done with this tutorial? Don't get me wrong I like the end results here, I just want to know the difference for learning purposes.
Thank you
borunco

My bad, I was out of town when you posted your Q and I didn't get back to you, sorry :(

I'm afraid that wasn't clear enough for me, my friend :(
Are you trying to "install" or creating "LiveUSB"? because the approach is different and this guide is for "installing" to an USB Drive :)

Let me know, I'm here now :)

---

### Post by km3952 on 2012-05-01
From your tutorial:-

/dev/sdc1 will be your ROOT Partition. Note that, you don't really need /home partition here. Total Size is just 4GB so no need for that. After all, this is not meant for day-to-day use or long-run use.

....but could be; I use a 4Gb pendrive (system / no personal info) + 16Gb or 32Gb pendrive (data / music) on a netbook.

This way it will be easy to upgrade every 6 months.
(To access the Internet = 4Gb pendrive only needed.)

---

### Post by amjjawad on 2012-05-01
> **km3952 said:**
> From your tutorial:-

[QUOTE=amjjawad;11409451]/dev/sdc1 will be your ROOT Partition. Note that, you don't really need /home partition here. Total Size is just 4GB so no need for that. After all, this is not meant for day-to-day use or long-run use.

....but could be; I use a 4Gb pendrive (system / no personal info) + 16Gb or 32Gb pendrive (data / music) on a netbook.

This way it will be easy to upgrade every 6 months.
(To access the Internet = 4Gb pendrive only needed.)[/QUOTE]

It is totally up to the user to decide whether he will use this approach for learning, testing or daily tasks :)

My job is to highlight the important issues and notes and the user is free to choose his/her own path ;)

---

### Post by fencer on 2012-07-14
Just installed it to a 32G usb stick lets now see how it works, I chose 1G swap, 15G / , and 16G for home. I'll be back with results

BTW great tutorial, thanks for sharing it, I just think that the gparted step is not needed since the live installer can do the partitions things as well (if you know how to use it)

---

### Post by mandza on 2012-11-12
i want to install ubuntu on my 16GB flash drive and make portable OS.
i know that i can install it i run ubuntu on same PC,  but can i install it on flash drive and use it on multiple PC and install all updates?
is anyone try something like this?

---

### Post by Borunco on 2012-11-12
> **mandza said:**
> i want to install ubuntu on my 16GB flash drive and make portable OS.
i know that i can install it i run ubuntu on same PC,  but can i install it on flash drive and use it on multiple PC and install all updates?
is anyone try something like this?
Hi mandza, if you fallow this tutorial you can totally use a flash drive and make a portable OS. I do it all the time, just make sure you do what amjjawad tells you at the beginning of the thread and you will be just fine. :P

enjoy Lubuntu

borunco :popcorn:

---

### Post by cforput on 2012-11-20
What type of speed is everyone seeing? I've tried installing Ubuntu & Lubuntu on flash drivers and they are so slow they aren't usalbe. They are 2.0 USB drives. 

Anyone had any luck getting one of the light linux systems to run on a USB? I've been trying to get SliTaz to work but I just can't get it to even boot.

---

### Post by Borunco on 2012-11-20
> **cforput said:**
> What type of speed is everyone seeing? I've tried installing Ubuntu & Lubuntu on flash drivers and they are so slow they aren't usalbe. They are 2.0 USB drives. 

Anyone had any luck getting one of the light linux systems to run on a USB? I've been trying to get SliTaz to work but I just can't get it to even boot.

Hi cforput, make sure you partition your usb before installing and follow this tutorial it should work with any OS. I have installed Ubuntu with all the Wiesel, like the cube and I can run it just a little slower than a regular Hdd install. If you have a real old system you might have a little slowness, but still it will be faster than using it for the live cd. If you partition and format as instructed in this tutorial, and you set your system bios to boot from usb , your system will see your usb as a Hdd. You need to set up your bios to boot #1 cd/dvd #2 usb Hdd #3 your internal Hdd. It should totally work ths is not the fault the OS. Make sure you don't have a Live cd in the computer when you try to boot from a usb, because the system will boot from the cd first or in some systems it will get confused? and run super slow if it dose get to boot.
Regards
borunco :popcorn:

---

### Post by raskalnickoff on 2012-12-17
[FONT=Calibri]First off, thanks this was quite helpfull and just what I was chasing.[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]I used an old Lubuntu 10.10 install CD and attempted to partition my USB to 8GB ext4 “\”, 4GB ext4 “\home” and 4GB swap. But every partition had ~4 bytes added or taken from it so they none of them were nice round numbers.[/FONT]


[FONT=Calibri]After installing the OS I restarted the PC and ran the performance test, then restarted a few more times. Seems best to consistently keep the USB in the same slot otherwise it resets the boot order and occasionally boots Windows. Also I can only use the GRUB to start XP on the computer I used to install Lubuntu, all the others say serial number not found.[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]I've sucessfully updated this to Lubuntu 12.10, but I havent been able to reformat my /home drive so that it is visable to windows. Any ideas on how I should try this?[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]removingthe lable and reformatting to fat32 hasn't helped, maybe it needs to be the first partition?[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]Other than that; Is there a way to stop windows from asking to format my USB all the time?[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT]

---

### Post by oldfred on 2012-12-17
If you are going to have a separate /home, it has to be Linux format. But for a small USB flash drive of 32GB or less I would not have a separate /home.

Windows only sees the first partition. So that is why you cannot use it with Windows and probably why Windows wants to reformat it. Windows does not see Linux formatted partitions.

If you have a fair amount of RAM I would also not create swap or keep it small and set swapiness so it is not used much.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
            [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it)?
I prefer sleep and shutdown to hibernate.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

---

### Post by C.S.Cameron on 2012-12-18
You can have the first partition FAT32 or NTFS, so both Windows and Linux can see it, then put / on the second partition and /home on the third.

Then you can move stuff you wish to be available to both operating systems from /home to the first partition.

---

### Post by raskalnickoff on 2012-12-20
[FONT=Calibri][FONT=Times New Roman][SIZE=2]Thanks, I’d forgotten how helpful and quick Linux forums were.[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2] [/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]Well since the main reason for a windows accessible partition is to avoid accidentally formatting the drive and I can’t use it as a home directory I may as well make is small, 512MB should be fine.[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]It’s not likely I will use hibernation on a flash drive, and although I may be using some 7GB database files on a PC with only 2GB of RAM. Plus it sounds fairly simple to create a swap file which should work as well as a partition anyway (if I decide I need it after all). This should give me plenty of room to trial Steam if the open Beta is indeed available next week.[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2] [/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]I changed my mind again and made a 930MiB Fat32 partition at the end of the drive. This worked because it is logically the first partition (/dev/sdb1), even though physically it isn’t. This leaves exactly 14336MiB (14GB neat) at the front of the drive and I made that all ext4 for my OS install. (sometimes this is recorded as 15GB, sometimes13.8GiB I probably should have reformatted the entire drive at some point)[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2] [/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]Also incidentally the boot times on my 5 year old PC were roughly[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]Lubuntu 10.04 3min 30sec[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]XP pro (HDD)  1min 25 sec[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]Lubuntu 12.10 0min 50sec[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]And on a 6 month old laptop with Win7 everything went from the GRUB loader to login screen in ~20seconds.[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2] [/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]So all is now working well on 3 fundamentally different hardware systems. [/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2](After changing the theme, resetting boot orders again & resetting the screen resolution on my 2 screen PC)[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Times New Roman][SIZE=2]I’m quite impressed.[/SIZE][/FONT][/FONT]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE]

---

### Post by purplegreen on 2013-06-22
Hello [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=941822")amjjawad,

Thank you for this brilliant guide. I'm trying to install Lubuntu 13.04, including boot loader, onto a USB stick.

I was wondering it's also possible to "Encrypt the [L]Ubuntu installation for security", i.e full USB drive encryption rather than just the home folder encryption option?

Thanks.

---

### Post by amjjawad on 2013-06-25
> **purplegreen said:**
> Hello amjjawad,

Thank you for this brilliant guide. I'm trying to install Lubuntu 13.04, including boot loader, onto a USB stick.

I was wondering it's also possible to "Encrypt the [L]Ubuntu installation for security", i.e full USB drive encryption rather than just the home folder encryption option?

Thanks.

Thank you for your nice comment and welcome to Ubuntu Forums :)

I'm still alive, I'm sorry for the late reply but I don't login here like I used to do. Real Life and other Lubuntu Activities outside the wall of Ubuntu Forums :)

You can encrypt the Home Folder but I assume you have read my notes? 
This approach is not for day-to-day use unless you have a High Speed USB Drive and not 4GB or 8GB Flash Drive.

As for FULL installation encryption? I'm not sure what do you mean by that?
Maybe if you could please explain what exactly are you trying to achieve, I may be able to help :)

Thank you and I'm glad this one was helpful.

I guess I need to create new one with new screenshots but I just don't have the time. Too much tasks, no time.

---

### Post by purplegreen on 2013-06-25
Hi amjjawad,

Thank you for the warm welcome!

I'm relatively new to the world of Ubuntu/Lubuntu etc., so apologies if my question wasn't as clear as it should of been. I have a high speed 32GB USB 3.0 flash drive that I'd like to install Lubuntu on using the method detailed in your guide, but with one customization: full drive encryption (rather than just home folder encryption).

You can see an example of this option in the [L]Ubuntu installation options menu here: [https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption](https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption) (I'm not sure if that link will show up as I'm a new forum user, if it doesn't just Google "Privacy in Ubuntu 12.10: Full Disk Encryption" for an EFF blog article detailing what I'd like to achieve, if possible).

I thought that maybe the answer was to use a different format when formatting the drive (step 13b of your guide), but I'm not sure...

Any help is appreciated, thanks!

---

### Post by Svante65 on 2013-10-22
I would like to know something about full encryption as well.
Having a Lubuntu installation on a USB key is not very save unless it's encrypted.

---

### Post by sudodus on 2013-10-22
> **Svante65 said:**
> I would like to know something about full encryption as well.
Having a Lubuntu installation on a USB key is not very save unless it's encrypted.

You can follow these instructions for the ***alternate iso*** file (yes, they are instructions for testing, but work well also for someone who 'only' wants to install it)

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

---

### Post by Svante65 on 2013-10-23
It looks like running the command **sudo swapoff -a** before installation solves the problem.
It did for me :-)

---

### Post by amjjawad on 2013-12-16
Hi,

Have anyone tried to install Lubuntu 13.10 (the latest stable release) on an USB Drive? 

If you have done that already, was it a successful installation? any problem? did zram-config caused any issue?

---

### Post by sudodus on 2013-12-17
Yes, and it works well. No particular problem because of USB. I have tried USB 2 as well as USB 3.

---

### Post by amjjawad on 2013-12-17
> **sudodus said:**
> Yes, and it works well. No particular problem because of USB. I have tried USB 2 as well as USB 3.

Hi my friend,

That is great to know :)

Haven't yet used USB 3.0 and I don't think I have that among my USB Drives.

Is there anything on this guide that you recommend to update? change?

---

### Post by sudodus on 2013-12-17
Well, if you have the time and energy ... I suggest that you update the first post. Do not describe Lubuntu 11.10, but a current version, and have current pictures (screendumps). I would add a reference to the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), which works very well for this purpose ;-)

---

### Post by amjjawad on 2013-12-17
> **sudodus said:**
> Well, if you have the time and energy ... I suggest that you update the first post. Do not describe Lubuntu 11.10, but a current version, and have current pictures (screendumps). 
While there is some energy, I am afraid there is less time available but I will do my best to update it - that was in mind few weeks ago when I took a look at the first post. I feel a bit rusty, it has been a long time since I have written a HOWTO ;) 

Let's see if I can make this any time soon :)


> I would add a reference to the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), which works very well for this purpose ;-)
Will keep that on mind :)

Thank you!

---

### Post by mildmcgee on 2013-12-20
> **amjjawad said:**
> Hi,

Have anyone tried to install Lubuntu 13.10 (the latest stable release) on an USB Drive? 

If you have done that already, was it a successful installation? any problem? did zram-config caused any issue?

Yes, I'm having trouble installing 13.10 on a USB drive.

I followed your preparation instructions, chose my location and got as far as creating a Lubuntu username and password etc.. After clicking the final continue button the install just hangs with the rotating loading cursor, here:

[IMG]http://i.imgur.com/GunV0GS.jpg[/IMG]

Nothing seems to happen after that, I had to shutdown the computer after an hour of waiting. Any advice?

Thank you.

---

### Post by monkeybrain20122 on 2013-12-20
Were you browsing the internet when you were installing? If yes, then close the browser next time when you are installing, may be using too much ram.

---

### Post by monkeybrain20122 on 2013-12-20
> **amjjawad said:**
> Hi,

Have anyone tried to install Lubuntu 13.10 (the latest stable release) on an USB Drive? 

If you have done that already, was it a successful installation? any problem? did zram-config caused any issue?

I haven't tried installing Lubuntu 13.10 in a flash drive, but I have done it on  an old hard drive removed from a dead laptop. I see no reason why it wouldn't work. As  long as the installer works and detects the device it shouldn't matter  where you install it into.

---

### Post by sudodus on 2013-12-20
> **mildmcgee said:**
> Yes, I'm having trouble installing 13.10 on a USB drive.

I followed your preparation instructions, chose my location and got as far as creating a Lubuntu username and password etc.. After clicking the final continue button the install just hangs with the rotating loading cursor, here:

Nothing seems to happen after that, I had to shutdown the computer after an hour of waiting. Any advice?

Thank you.

Please specify the computer

- Brand name and model
- CPU
- RAM (size)
- Graphics chip/card
- Wifi chip/card

It makes it much easier to give relevant tips and advice :-)

---

### Post by amjjawad on 2013-12-20
Hello and Welcome to Ubuntu Forums :)

> **mildmcgee said:**
> Yes, I'm having trouble installing 13.10 on a USB drive.
I am sorry to know that. I will do my very best to help!

> I followed your preparation instructions, chose my location and got as far as creating a Lubuntu username and password etc.. After clicking the final continue button the install just hangs with the rotating loading cursor, here:

[IMG]http://i.imgur.com/GunV0GS.jpg[/IMG]

Nothing seems to happen after that, I had to shutdown the computer after an hour of waiting. Any advice?

Thank you.

Yes indeed there is an advice:

1- Make sure to check MD5SUM for the ISO you have downloaded before creating a LiveCD or LiveUSB

2- Make sure - if creating a LiveCD - to choose the minimum burning speed, say 8x

3- If you are using the LiveUSB to install Lubuntu, please use the latest version of UNetbootin (there is Windows version and there is Linux version) - it is very handy and great tool/application to create LiveUSB

4- Try to use GParted to create New Partition Table for your USB Drive, then create the needed partitions for the installation OR let the installer handle that - your choice

Please, feel free to ask if you have anything in mind :)

You can use Google as always but still, do ask please if you feel there is something not clear.

All the best and I do hope you will be able to install Lubuntu :)

By the way, what is the size of your USB that you are trying to install on?
What are the hardware specifications of that machine?
What media are you using to install? LiveCD? LiveUSB?

---

### Post by amjjawad on 2013-12-20
> **monkeybrain20122 said:**
> I haven't tried installing Lubuntu 13.10 in a flash drive, but I have done it on  an old hard drive removed from a dead laptop. I see no reason why it wouldn't work. As  long as the installer works and detects the device it shouldn't matter  where you install it into.

Lubuntu 13.10 had a super nasty bug regarding zram-config and I was worried that, for whatever reason, it might cause some troubles and was curious to know, that is all :)

I am very much aware of the note you have posted, thank you anyway!

---

### Post by mildmcgee on 2013-12-21
> **monkeybrain20122 said:**
> Were you browsing the internet when you were installing? If yes, then close the browser next time when you are installing, may be using too much ram.

I didn't have any applications running during install.

> **sudodus said:**
> Please specify the computer

- Brand name and model
- CPU
- RAM (size)
- Graphics chip/card
- Wifi chip/card

It makes it much easier to give relevant tips and advice :-)

I installed and ran Lubuntu 13.04 on a USB drive via this laptop not too long ago with no issues. It's a Dell laptop I'm borrowing from a friend, purchased in 2012. I believe it has an i3 processor and 4GB of RAM. I can't provide any more specs until I see my friend next, sorry!

> **amjjawad said:**
> Hello and Welcome to Ubuntu Forums :)


I am sorry to know that. I will do my very best to help!



Yes indeed there is an advice:

1- Make sure to check MD5SUM for the ISO you have downloaded before creating a LiveCD or LiveUSB

2- Make sure - if creating a LiveCD - to choose the minimum burning speed, say 8x

3- If you are using the LiveUSB to install Lubuntu, please use the latest version of UNetbootin (there is Windows version and there is Linux version) - it is very handy and great tool/application to create LiveUSB

4- Try to use GParted to create New Partition Table for your USB Drive, then create the needed partitions for the installation OR let the installer handle that - your choice

Please, feel free to ask if you have anything in mind :)

You can use Google as always but still, do ask please if you feel there is something not clear.

All the best and I do hope you will be able to install Lubuntu :)

By the way, what is the size of your USB that you are trying to install on?
What are the hardware specifications of that machine?
What media are you using to install? LiveCD? LiveUSB?

1 - I did check the ISO MD5 before installation, everything verified OK.

2 - N/A; I used, and will continue using, a LiveUSB for installation.

3 - I used Pen Drive Linux's USB Installer mentioned in this guide: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) - I'll try UnetBootin for the next install attempt.

4 - I did use GParted to create a new partition table and also the installation partitions. I didn't know I could leave the installer to create the partitions automatically (I thought it had to be done manually before install), so I'll also try that during the next install attempt.

It's a 4GB USB drive - I installed and ran Lubuntu 13.04 on this USB drive not too long ago with no issues.
A few machine specs are listed in response to sudodus' question above (again, sorry for the lack of info!)
I'm using a LiveUSB to install.

I'm also interested in full USB drive encryption mentioned here: [http://ubuntuforums.org/showthread.php?t=1872303&p=12706069#post12706069](http://ubuntuforums.org/showthread.php?t=1872303&p=12706069#post12706069), is this possible?

Thanks (everyone!) for your help so far.

---

### Post by sudodus on 2013-12-21
> **mildmcgee said:**
> 
I installed and ran Lubuntu 13.04 on a USB drive via this laptop not too long ago with no issues. It's a Dell laptop I'm borrowing from a friend, purchased in 2012. I believe it has an i3 processor and 4GB of RAM. I can't provide any more specs until I see my friend next, sorry!

It should be possible to run every version and flavour of Ubuntu in that computer. There might be problems with the graphics or wifi, that the drivers do not work with the hardware. In that case you can try with the boot option ***nomodeset*** and some other boot options and maybe install a proprietary driver. See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It could also be some problem with the the pendrive or putting the system into it. See this link for an overview of different methods

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
> 
I'm also interested in full USB drive encryption mentioned here: [http://ubuntuforums.org/showthread.php?t=1872303&p=12706069#post12706069](http://ubuntuforums.org/showthread.php?t=1872303&p=12706069#post12706069), is this possible?

Thanks (everyone!) for your help so far.
Edit: I have tested the following method and I know that it works (for internal as well as external drives). But it will be slow unless you use a USB 3 pendrive, slower than a live drive. 

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

---

### Post by mildmcgee on 2013-12-23
I finally managed to install Lubuntu 13.10 onto my 4GB drive. It seems that leaving the "Encrypt my home folder" option unticked solved the problem (I had ticked this option during previous install attempts).

> **sudodus said:**
> I have tested the following method and I know that it works (for internal as well as external drives). But it will be slow unless you use a USB 3 pendrive, slower than a live drive. 

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

Sudodus, I read the guide you linked to regarding full drive encryption but couldn't get past step 12. I don't know if the option is missing or maybe removed in Lubuntu 13.10, but I just couldn't find it anywhere!

---

