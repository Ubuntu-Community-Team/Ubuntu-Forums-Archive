---
title: "Installing Ubuntu Touch Vivid on a 7&quot; tablet"
date: 2014-11-29
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-11-29
I bought this [RCA]("http://www.rcatablets.com/tablets/7-voyager") 7" tablet at Walmart's Black Friday sale, the price was right, and the specs were pretty good, It has 8Gib of storage, and an ArmV7 quad core processor. It already has Ubuntu installed, see the screenshot, so it shouldn't be too tough to install Touch on it. I got the image from [here]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/"). I'll update this thread as I progress.

---

### Post by sammiev on 2014-11-29
> **cariboo907 said:**
> I bought this [RCA]("http://www.rcatablets.com/tablets/7-voyager") 7" tablet at Walmart's Black Friday sale, the price was right, and the specs were pretty good, It has 8Gib of storage, and an ArmV7 quad core processor. It already has Ubuntu installed, see the screenshot, so it shouldn't be too tough to install Touch on it. I got the image from [here]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/"). I'll update this thread as I progress.

You have my interest! Looking forward to the out come. :)

---

### Post by jerrylamos on 2014-11-30
> **cariboo907 said:**
> I bought this [RCA]("http://www.rcatablets.com/tablets/7-voyager") 7" tablet at Walmart's Black Friday sale, the price was right, and the specs were pretty good, It has 8Gib of storage, and an ArmV7 quad core processor. It already has Ubuntu installed, see the screenshot, so it shouldn't be too tough to install Touch on it. I got the image from [here]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/"). I'll update this thread as I progress.

?  The screenshot says Android 4.4.2.  How do I tell when looking at the RCA in Wallmart whether it's Ubuntu or not?

Thanks

---

### Post by mc4man on 2014-11-30
> **jerrylamos said:**
> ?  The screenshot says Android 4.4.2.  How do I tell when looking at the RCA in Wallmart whether it's Ubuntu or not?

Thanks
pretty easily - it's not on the units (or any unit) at Wallmart - "It already has Ubuntu installed" didn't mean 'It already had Ubuntu installed'

---

### Post by ventrical on 2014-12-01
> **cariboo907 said:**
> I bought this [RCA]("http://www.rcatablets.com/tablets/7-voyager") 7" tablet at Walmart's Black Friday sale, the price was right, and the specs were pretty good, It has 8Gib of storage, and an ArmV7 quad core processor. It already has Ubuntu installed, see the screenshot, so it shouldn't be too tough to install Touch on it. I got the image from [here]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/"). I'll update this thread as I progress.

+1 Got the ditto same thing.

? Can it be booted from SD card?

Thanks..

---

### Post by DogMatix on 2014-12-01
> **ventrical said:**
> +1 Got the ditto same thing.

? Can it be booted from SD card?

Thanks..

I think it may be a little more involved than that. The adb and phablet route.
[URL="http://www.pcadvisor.co.uk/how-to/linux/3531970/how-install-ubuntu-touch/"]

How to install Ubuntu Touch on your Android phone or tablet - Tech Advisor[/URL]
[URL="http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/"]
Install Ubuntu for devices on a supported phone or tablet - Ubuntu.com[/URL]

This thread caught my attention so I did a little reading. Careful not to brick your new tablets though.

EDIT: I also stumbled across this although a bit dated seemed specific to connecting via adb to similar RCA tablets that are mentioned:

[How to get working ADB drivers for unrecognized Android devices - a blogspot]("http://ryancuda.blogspot.co.uk/2013/12/how-to-get-working-adb-drivers-for.html") - which may or may not be relevant!

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
[color=red]**NOTE:** ventrical discovered information in the above links to be outdated or not relevant to the RCA tablet discussed in this thread.[/color]

---

### Post by ventrical on 2014-12-02
> **DogMatix said:**
> I think it may be a little more involved than that. The adb and phablet route.
[URL="http://www.pcadvisor.co.uk/how-to/linux/3531970/how-install-ubuntu-touch/"]

How to install Ubuntu Touch on your Android phone or tablet - Tech Advisor[/URL]
[URL="http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/"]
Install Ubuntu for devices on a supported phone or tablet - Ubuntu.com[/URL]

This thread caught my attention so I did a little reading. Careful not to brick your new tablets though.

EDIT: I also stumbled across this although a bit dated seemed specific to connecting via adb to similar RCA tablets that are mentioned:

[How to get working ADB drivers for unrecognized Android devices - a blogspot]("http://ryancuda.blogspot.co.uk/2013/12/how-to-get-working-adb-drivers-for.html") - which may or may not be relevant!

Thanks for these finds. I updated it to ubuntu 3.6.x.x (at first start)and it is working great.  They are so inexpensive (still on Black Friday list) that I will probably get another one. :) Hopefully will not brick :)

---

### Post by cariboo on 2014-12-02
> **ventrical said:**
> Thanks for these finds. I updated it to ubuntu 3.6.x.x (at first start)and it is working great.  They are so inexpensive (still on Black Friday list) that I will probably get another one. :) Hopefully will not brick :)

I haven't managed to brick mine yet, with all that I've tried so far. The thing I've had more problems with than anything else is rooting the device, I found a solution that worked for me on the [XDA  Developers forum]("http://forum.xda-developers.com/")

---

### Post by ventrical on 2014-12-02
> **cariboo907 said:**
> I haven't managed to brick mine yet, with all that I've tried so far. The thing I've had more problems with than anything else is rooting the device, I found a solution that worked for me on the [XDA  Developers forum]("http://forum.xda-developers.com/")

But I can't find anything related to Voyager7 and so I have some trepedations going into this. Basically I am a complete noob at this and I am not sure which link to follow or which images to download (as provided in your link). I looked at the other links  provided by dogMatix but I don't see where those files line up with the link you provided.

---

### Post by DogMatix on 2014-12-02
> **ventrical said:**
> But I can't find anything related to Voyager7 and so I have some trepedations going into this. Basically I am a complete noob at this and I am not sure which link to follow or which images to download (as provided in your link). I looked at the other links  provided by dogMatix but I don't see where those files line up with the link you provided.


[How to root RCT6773W22 (rca voyager) -  XDA Developers]("http://forum.xda-developers.com/android/development/how-to-root-rct6773w22-rca-voyager-t2955600")

Sounds like someone else having fun with Black Friday mechandise.

---

### Post by ventrical on 2014-12-02
When you allow 'developers options' it will warn of breakage. Then , allow and when you try to enable 'Show CPU Usage' it will display  tiny verbose text at top right, but no status bar indicator. Easy enough to turn off .etc.. 

Toe in. Feet wet ... :) 

#note to Cariboo... hope it does not seem like I am hi-jacking your thread:) I am sometimes asking off topic question so I can get a better handle on install process.

thnxs

---

### Post by PDA1 on 2014-12-04
Yes, you sound right about that. The OP on that forum didn't write a sequential step-by-step process.

That certainly doesn't inspire any confidence in his procedure (if you want to call it that).

---

### Post by ventrical on 2014-12-06
> **PDA1 said:**
> Yes, you sound right about that. The OP on that forum didn't write a sequential step-by-step process.

That certainly doesn't inspire any confidence in his procedure (if you want to call it that).

At this stage of the game  I am not too concerned if I brick my  Voyager 7 because it  is really rather useless in it's current state of spewing out adware the way that it does.

---

### Post by sammiev on 2014-12-06
Just got my new toy. I have the v10. Following this thread closely. ):P

---

### Post by ventrical on 2014-12-06
> **cariboo907 said:**
> I haven't managed to brick mine yet, with all that I've tried so far. The thing I've had more problems with than anything else is rooting the device, I found a solution that worked for me on the [XDA  Developers forum]("http://forum.xda-developers.com/")

So I have to run this program on a Wndows machine?

---

### Post by ventrical on 2014-12-06
Finally got device but you have to authorize from tablet and choose 'Always use this device?' OK

```

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
error: device not found
ventrical@ventrical-MS-7798:~$ adb reboot-bootloader
error: device not found
ventrical@ventrical-MS-7798:~$ adb devices
List of devices attached 
W8KBIZVGPFNFRGON    device

ventrical@ventrical-MS-7798:~$ 

```

Edit:

Sometimes you have to pull out the USB cable from tablet (then replace it) to provoke continuance of connection.

---

### Post by ventrical on 2014-12-06
Bricked! :) bwhahahaha

```

bug tags are printed.
ventrical@ventrical-MS-7798:~$ adb kill-server
ventrical@ventrical-MS-7798:~$ adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
error: device not found
ventrical@ventrical-MS-7798:~$ adb reboot-bootloader
error: device not found
ventrical@ventrical-MS-7798:~$ adb devices
List of devices attached 
W8KBIZVGPFNFRGON    device

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
ventrical@ventrical-MS-7798:~$ sudo fastboot oem unlock
[sudo] password for ventrical: 
ventrical@ventrical-MS-7798:~$ sudo fastboot oem unlock
[sudo] password for ventrical: 
...
^C
^X
ventrical@ventrical-MS-7798:~$ 
ventrical@ventrical-MS-7798:~$ adb devices
List of devices attached 

ventrical@ventrical-MS-7798:~$ 

```

 .. and now I just have this 

=> FASTBOOT mode ...

at bottom of tablet screen .. no response .. :)

It was the 

```


adb reboot bootloader


```
 that killed it .

so don't do what I did :)

but I am going to try for recovery  by rebooting desktop.




Regards..

Edit..
 No .. not bricked yet ! :)

---

### Post by ventrical on 2014-12-06
Edit  : No brick yet.

  I had to do 

```

fastboot reboot

```

from terminal..

---

### Post by ventrical on 2014-12-06
Update..

 My problem is I can't get to the screen (below) but everything else is working.



```

ventrical@ventrical-MS-7798:~$ adb devices
List of devices attached 
W8KBIZVGPFNFRGON    device

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
ventrical@ventrical-MS-7798:~$ fastboot reboot
rebooting...

finished. total time: 0.002s
ventrical@ventrical-MS-7798:~$ 

```

Edit:

 Tomorrow I will try and just keep going and skip this screen.

 Anybody else..?

---

### Post by sammiev on 2014-12-07
> **ventrical said:**
> Update..

 My problem is I can't get to the screen (below) but everything else is working.



```

ventrical@ventrical-MS-7798:~$ adb devices
List of devices attached 
W8KBIZVGPFNFRGON    device

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
ventrical@ventrical-MS-7798:~$ fastboot reboot
rebooting...

finished. total time: 0.002s
ventrical@ventrical-MS-7798:~$ 

```

Edit:

 Tomorrow I will try and just keep going and skip this screen.

 Anybody else..?

I do not want to brick mine yet but really looking to play. I should have got the smaller one but I got the last one in stock at Walmart.

---

### Post by ventrical on 2014-12-07
> **sammiev said:**
> I do not want to brick mine yet but really looking to play. I should have got the smaller one but I got the last one in stock at Walmart.

I'm back .  Sometimes following all instructions are not always necessary.  I've had a good rest and ready to get back at it :) I'll let you all know what I have found out or if I succeed in bricking or not bricking. 

Regards..

---

### Post by ventrical on 2014-12-07
Ok... THis RCA Voyager 7 series is a little different animal than others. When following instructions here: [http://www.pcadvisor.co.uk/how-to/linux/3531970/how-install-ubuntu-touch/](http://www.pcadvisor.co.uk/how-to/linux/3531970/how-install-ubuntu-touch/)  one does not get the standard android setup as show in the pic and the order is slightly different. 

  If you shut your V7 tablet down and then reboot it by holding down both up+down volume rocker and then hold power on button until you get the screen below. This is where the setting has to be set to be able to flash your slate.

  I'm just not sure if it's  update from ADB , cache or do a wipe/reset first.  I am assuming cache because it says the image is automatically downloaded from /dev/ which is vivid. So that would mean that it was not necessary to download the image cariboo recommended if the current web page documentation is still current.

 Anybody else get any further??

---

### Post by cariboo on 2014-12-07
> **ventrical said:**
> Update..

 My problem is I can't get to the screen (below) but everything else is working.



```

ventrical@ventrical-MS-7798:~$ adb devices
List of devices attached 
W8KBIZVGPFNFRGON    device

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
ventrical@ventrical-MS-7798:~$ fastboot reboot
rebooting...

finished. total time: 0.002s
ventrical@ventrical-MS-7798:~$ 

```

Edit:

 Tomorrow I will try and just keep going and skip this screen.

 Anybody else..?

I'm having the same problem, I can get to a similar screen by holding the power button and volume up.

---

### Post by ventrical on 2014-12-07
> **cariboo907 said:**
> I'm having the same problem, I can get to a similar screen by holding the power button and volume up.

I actually think this is the CMOS 'type" to work from. I am going to do a backup, see what happens and then try to do an ADB update using the tools and process described in the RCA how to. I am now of the thinking that it may have to be wiped/reset.  I'll go ahead and try that after back up  and get back ..see what happens..  I am also of the thinking now that it really cannot get bricked.. just some extra work in reinstalling backup/restore.

Here goes.. :)

Edit:

Ok .. chose backup. have to have SD card installed before it will backup. 
User data allocated :448MB
name_of_backupfile_here

Also it reports 'Installing system Update...' under the adroid robot  thingy (and it is actually updating!!) but I have no idea what :)  ..... I have it connected to PC. I think it is auto updating from a cache that was perhaps downloaded lastnight . have no idea.. brb

more notes ... it is over halfway done installing system update from my trusty tower. I downloaded the vivid-preinstalled-touch-armhf.tar.gz a couple of days ago but didn't unpack it.

Ok.. system update done. Time to reboot.

Ok .. all the system update did was restore it back to kernel version 3.4.67root@ubuntu-018#1?? I updated it when I firsr got it to kernel 3.6.x.x so this is weird.

Ok .. so now back to the ADB update process.

---

### Post by ventrical on 2014-12-07
```


adb sideload <filename>


```

fails as reported by the tablet.  But I think I did something wrong.

Here 

```

ventrical@ventrical-MS-7798:~$ cd Downloads
ventrical@ventrical-MS-7798:~/Downloads$ cd vividtouch
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ adb sideload /vivid-preinstalled-touch-armhf/
* cannot read 'sideload' *
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ adb sideload /vivid-preinstalled-touch-armhf
* cannot read 'sideload' *
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ adb sideload vivid-preinstalled-touch-armhf.tar.gz
sending: 'sideload'  100%    
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ 

```

 Also .. I extracted those files to a directory but extracting those files give me all the directories of the OS and it will not install if you use a directory as a sideload.

Edit..

A small time out here. Got a do some more research on this. It's right there in front of me..:)

---

### Post by sammiev on 2014-12-07
Reading on and getting more excited. :)

---

### Post by ventrical on 2014-12-07
Trying to brute force it I get:

```

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
ventrical@ventrical-MS-7798:~$ fastboot reboot
rebooting...

finished. total time: 0.002s
ventrical@ventrical-MS-7798:~$ ubuntu-device-flash --channel=devel --bootstrap
DEPRECATED: Implicit 'touch' subcommand assumed
2014/12/07 19:38:56 Expecting the device to be in the bootloader... waiting


```

and then it hangs so I will have to use one of the other options in the device boot menu and also there is no such :-   ~/.cache/ubuntuimages  folder in /home so there is a process skipped with the deprecated method refered to in the techrepublic article.

---

### Post by ventrical on 2014-12-07
It appears the next method will be to try to use the  'wipe data/factory reset' option  and/or read a bit more on phablet-tools man pages.

---

### Post by ventrical on 2014-12-07
Switching over here : [http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)  and then trying this command:

```

ventrical@ventrical-MS-7798:~$ adb shell grep ro.product.device /system/build.prop
ro.product.device=RCT6773W22
# ro.build.product is obsolete; use ro.product.device
ventrical@ventrical-MS-7798:~$ 

```

shows that the page has not been updated ... so I'll try the correction referenced. Also it is a bug because it does use 'ro.product.device'

---

### Post by ventrical on 2014-12-07
It just will not unlock .... tried everything at 2 recomended sites. So I am assuming it may be an encrypt which means it has to be factory reset before ubuntu can be put on there.

Edit:

  I wiped it/factory reset and it just keeps coming back:) Cannot get the oem unlock. So I guess it has to be done through adb.

---

### Post by sammiev on 2014-12-07
> **ventrical said:**
> It just will not unlock .... tried everything at 2 recomended sites. So I am assuming it may be an encrypt which means it has to be factory reset before ubuntu can be put on there.

Edit:

  I wiped it/factory reset and it just keeps coming back:) Cannot get the oem unlock. So I guess it has to be done through adb.

I know you can do it. :popcorn:

---

### Post by ventrical on 2014-12-07
> **sammiev said:**
> I know you can do it. :popcorn:

I have been studying some stuff from xda-developers (framroot) and Kingo from CNet which is windows app. There is nothing in the documentation provided so far that says the 'tablet' has to be *rooted*.

No offence to Dogmatix but his references here : [http://ubuntuforums.org/showthread.php?t=2254725&p=13178630#post13178630](http://ubuntuforums.org/showthread.php?t=2254725&p=13178630#post13178630)  are deprecated atm .. at least for this particular device.

 So I'll have to go back to the drawing board.  I thought I would have had it working by now :) but I am not going to blame myself for being provided with obsoleted instructions.. alright .. I'll stop me whining :)


Regards..

---

### Post by ventrical on 2014-12-07
> **ventrical said:**
> ```


adb sideload <filename>


```

fails as reported by the tablet.  But I think I did something wrong.

Here 

```

ventrical@ventrical-MS-7798:~$ cd Downloads
ventrical@ventrical-MS-7798:~/Downloads$ cd vividtouch
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ adb sideload /vivid-preinstalled-touch-armhf/
* cannot read 'sideload' *
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ adb sideload /vivid-preinstalled-touch-armhf
* cannot read 'sideload' *
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ adb sideload vivid-preinstalled-touch-armhf.tar.gz
sending: 'sideload'  100%    
ventrical@ventrical-MS-7798:~/Downloads/vividtouch$ 

```

 Also .. I extracted those files to a directory but extracting those files give me all the directories of the OS and it will not install if you use a directory as a sideload.

Edit..

A small time out here. Got a do some more research on this. It's right there in front of me..:)



  I am going to try using adb sideload with the image files.

First I will have to boot to Android System Recovery.
The choose apply update from ADB

and install

[vivid-preinstalled-boot-armhf+flo.img]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/vivid-preinstalled-boot-armhf+flo.img")  
[vivid-preinstalled-recovery-armel+flo.img]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/vivid-preinstalled-recovery-armel+flo.img")
[vivid-preinstalled-system-armel+flo.img]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/vivid-preinstalled-system-armel+flo.img")

 in that order.

Here goes :) lol

Edit:

It appeared that system was 'updating' but they all ended in fails.

---

### Post by ventrical on 2014-12-07
Oh well.. zzzzz time :)

```

ventrical@ventrical-MS-7798:~$ adb root
adbd cannot run as root in production builds
ventrical@ventrical-MS-7798:~$

```

one blog said that model was factory defected.

---

### Post by ventrical on 2014-12-08
Some progress.

 You have to get to the =>FASTBOOT mode... screen first, then

```

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
ventrical@ventrical-MS-7798:~$ ubuntu-device-flash --bootstrap
DEPRECATED: Implicit 'touch' subcommand assumed
2014/12/08 09:31:03 Expecting the device to be in the bootloader... waiting
2014/12/08 09:31:03 Device is |RCT6773W22|
Device RCT6773W22 not found on server https://system-image.ubuntu.com channel ubuntu-touch/stable
ventrical@ventrical-MS-7798:~$ 

```

so to overwrite you have to be able to name a source device that will overwrite(replace) |RCT6773W22|. So looks like some work renaming .. fanagling  around...because we want /vivid/ and not stable  :)

---

### Post by ventrical on 2014-12-08
Another assumption is that the 'ubuntu-device-flash tool is deprecated because it keeps reporting a set server:

```

Channel ubuntu-touch/ubuntu/devel not found on server https://system-image.ubuntu.com

```

so one has to manually set the server.

From mapage:

```

       -server="https://system-image.ubuntu.com": Select image server


```

so using:

```

ubuntu-device-flash -server="name_of_correct_server_here"

```

should override the deprecated server.

  The question is .. which is the correct server name.

#note#  This activity only happening on RCA tablet Voyager 7. The information may work just fine with other listed tablets.

@cariboo907... anything new on your slate ?

---

### Post by ventrical on 2014-12-08
Well they locked this baby up really good :) But I'm not giving up yet. I have a few theories on this. Mark Shuttleworth talked a bit about this last year about 'firmware'.

Regards..

---

### Post by cariboo on 2014-12-08
> **ventrical said:**
> Another assumption is that the 'ubuntu-device-flash tool is deprecated because it keeps reporting a set server:

```

Channel ubuntu-touch/ubuntu/devel not found on server https://system-image.ubuntu.com

```

so one has to manually set the server.

From mapage:

```

       -server="https://system-image.ubuntu.com": Select image server


```

so using:

```

ubuntu-device-flash -server="name_of_correct_server_here"

```

should override the deprecated server.

  The question is .. which is the correct server name.

#note#  This activity only happening on RCA tablet Voyager 7. The information may work just fine with other listed tablets.

@cariboo907... anything new on your slate ?

I've be working 60 hour weeks lately, so I haven't really had a lot of time to do anything, I'll keep following your progress, and in the new year when things slow down a bit, I'll get to it again.

---

### Post by ventrical on 2014-12-08
I'm think I'm this close    ''  ... this close ! :)

I'll try this  later .. busy atm.

---

### Post by sammiev on 2014-12-08
> **ventrical said:**
> Some progress.

 You have to get to the =>FASTBOOT mode... screen first, then

```

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
ventrical@ventrical-MS-7798:~$ ubuntu-device-flash --bootstrap
DEPRECATED: Implicit 'touch' subcommand assumed
2014/12/08 09:31:03 Expecting the device to be in the bootloader... waiting
2014/12/08 09:31:03 Device is |RCT6773W22|
Device RCT6773W22 not found on server https://system-image.ubuntu.com channel ubuntu-touch/stable
ventrical@ventrical-MS-7798:~$ 

```

so to overwrite you have to be able to name a source device that will overwrite(replace) |RCT6773W22|. So looks like some work renaming .. fanagling  around...because we want /vivid/ and not stable  :)

Happy to hear you made it that far, I started looking into rooting the V10 and found little so far. I hope what works for you works on this puppy. GL ):P

---

### Post by DogMatix on 2014-12-08
> **ventrical said:**
> .... No offence to Dogmatix but his references here : [http://ubuntuforums.org/showthread.php?t=2254725&p=13178630#post13178630](http://ubuntuforums.org/showthread.php?t=2254725&p=13178630#post13178630)  are deprecated atm .. at least for this particular device. :)


Regards..

Duly noted. I've appended that post to such effect. ;)

---

### Post by ventrical on 2014-12-08
> **sammiev said:**
> Happy to hear you made it that far, I started looking into rooting the V10 and found 
                                                                                                                                 ^^^^^
little so far. I hope what works for you works on this puppy. GL ):P


  I am trying to avoid this method by all means but, it appears ,(contrary to the current and present documentation provided), that it may be needed.  I have been reading volumes of posts and there are several people attempting to get a successful root on the "Black Friday" misfits.

 So far most of the instructions work as they should until one gets to the command:

```

adb reboot-bootloader

```

There is suppossed to be a green Android bot laying on it's back but what happenes with this Kitkat 4.4.2 version is that the screen blanks for a second and then:

=>Fastboot....  verbose appears at the lower left hand side of the screen. some of the adb commands will work like extracting the log.file .. etc.. but once you try to  unlock the bootloader:

```

sudo fastboot oem unlock

```

 it just hangs. I tried just waiting for a long while but nothing. You have to :

```

fastboot reboot

```

 to get your machine back, otherwise it will stay locked up in => Fastboot...

 One good thing I had noted is that I was able to backup and then  subsequently restore from a backup file but the backup file is written to the SD card. You can also use the :

```

adb sideload <filename>

```

but it is knowing what file name to send and I have tried various but eventually get errors from terminal or I have to close the terminal.

  One way I was hypothsesizing of doing this is to use an image file in the guise of a backup file and try to trick it into installing the new vivid/devel/ daily build... but I am not sure where to get such an image.

  Since adb  is installed from a :ppa I don't see what good it would do to file a bug.

And then there is Kingo Android Root which is a Windows app and it looks like this app has the market cornered because none of the root apps in the Play Store will work unless phone/tablet is rooted first.

Regards...

edit:

To root or not to root : ? :)

Time to crack open the ole Windows 7 Box :)

---

### Post by ventrical on 2014-12-08
Tried Kingo Android Root.

Went through all the bells and whistles.

Goes to =>Fastboot mode ...

Then reports after a while on the tablet screen some info about 'not a boot image' and reboots the Tablet and starts over again. Endless loop - not supported by Kingo.

This slate is like the unsinkable Molly Brown :)

Geeesh :)

---

### Post by cariboo on 2014-12-08
I couldn't get Kingo to work either, I used [iRoot]("http://www.mgyun.com/m/en"), it's a bit of a pain to use, as it installs a couple of Chinese apps, that you need to go into Settings->Apps to remove. They will also get re-installed every time time you connect the tablet via usb, so I'd recommend removing iRoot after you have rooted your device.

---

### Post by grahammechanical on 2014-12-08
I see you people have noticed that the Ubuntu Touch porting guide is hopelessly inadequate. The devs know about it. They were discussing this on last week's Ubuntu On Air Community Q & A. I think it was last week. The difficulty for the devs is that they do not have these devices. They are not very experienced in porting. <hint>There is an open invitation to write porting guides.</hint> :)

Have fun. Regards.

---

### Post by cariboo on 2014-12-09
@ventrical, I had some time to do a bit more research, I think the solution to the problem may be device spoofing. I have Tuesday and Wednesday off, so I'll have some time to try a couple of things.

---

### Post by ventrical on 2014-12-09
> **grahammechanical said:**
> I see you people have noticed that the Ubuntu Touch porting guide is hopelessly inadequate. The devs know about it. They were discussing this on last week's Ubuntu On Air Community Q & A. I think it was last week. The difficulty for the devs is that they do not have these devices. They are not very experienced in porting. <hint>There is an open invitation to write porting guides.</hint> :)

Have fun. Regards.

  If I  discover a way to use an existing tool to get the job done I will certainly help out.

Regards..

---

### Post by ventrical on 2014-12-09
> **cariboo907 said:**
> @ventrical, I had some time to do a bit more research, I think the solution to the problem may be device spoofing. I have Tuesday and Wednesday off, so I'll have some time to try a couple of things.

 Any tidbit you have is fine with me :)

btw .. yes I heard about the Chinese iroot.... thanks for taking one for the group :)


Regards..

---

### Post by ventrical on 2014-12-09
> **cariboo907 said:**
> I couldn't get Kingo to work either, I used [iRoot]("http://www.mgyun.com/m/en"), 

Thanks! :)

That worked pretty quick.

Regards..

---

### Post by cariboo on 2014-12-10
In my quest to install Ubuntu Touch on my RCA tablet, I've tried the following things, first, is to 
see what the device looks like to another system. I used the following command found[ here]("[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/") to gather some information:

```
adb shell grep ro.product.name /system/build.prop > mydevicedata \
&& adb shell grep build.id /system/build.prop >> mydevicedata \
&& adb shell grep ro.product.device /system/build.prop >> mydevicedata
``` 

Creates a file called mydevicedata, to view the file in a terminal type:

```
cat mydevicedata
```

which results in:

```
cat mydevicedata
ro.product.name=RCT6773W22
ro.build.id=KOT49H
ro.product.device=RCT6773W22
# ro.build.product is obsolete; use ro.product.device
```

There's not a lot of help here, as we already know this.

Next running:

```
adb reboot bootloader
```

and then:

```
fastboot devices
```

results in somethig else:

```
cariboo@skynet:~$ fastboot devices
mt8127_phone	fastboot
```

This starts to give me a bit of hope, if I can find a similar device that uses the same chipset,
I may be able to change /system/build.prop to spoof a different device.

In order to actually access the build.prop file, you have to make sure your device is rooted, then use
an app like [ES File Explorer]("https://play.google.com/store/apps/details?id=com.estrongs.android.pop&hl=en") to navigate to it's location.

[[img]http://i.imgur.com/y2XPjuFl.png[/img]](http://imgur.com/y2XPjuF)

[[img]http://i.imgur.com/MLm3Kngl.png[/img]](http://imgur.com/MLm3Kng)

[[img]http://i.imgur.com/2yNToNel.png[/img]](http://imgur.com/2yNToNe)

[[img]http://i.imgur.com/jWpnsX6l.png[/img]](http://imgur.com/jWpnsX6)

I've also attached build.prop and build.prop.original, for anyone that is curious.

---

### Post by ventrical on 2014-12-10
+1   exact same results here.

Thanks for the other app reference also.

The wheels are turning :)

Regards..

---

### Post by ventrical on 2014-12-10
> **cariboo907 said:**
> In my quest to install Ubuntu Touch on my RCA tablet, I've tried the following things, first, is to 
see what the device looks like to another system. I used the following command found[ here]("http://[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/") to gather some information:

```
adb shell grep ro.product.name /system/build.prop > mydevicedata \
&& adb shell grep build.id /system/build.prop >> mydevicedata \
&& adb shell grep ro.product.device /system/build.prop >> mydevicedata
``` 

Creates a file called mydevicedata, to view the file in a terminal type:

```
cat mydevicedata
```

which results in:

```
cat mydevicedata
ro.product.name=RCT6773W22
ro.build.id=KOT49H
ro.product.device=RCT6773W22
# ro.build.product is obsolete; use ro.product.device
```

There's not a lot of help here, as we already know this.

Next running:

```
adb reboot bootloader
```

and then:

```
fastboot devices
```

results in somethig else:

```
cariboo@skynet:~$ fastboot devices
mt8127_phone    fastboot
```

This starts to give me a bit of hope, if I can find a similar device that uses the same chipset,
I may be able to change /system/build.prop to spoof a different device.

In order to actually access the build.prop file, you have to make sure your device is rooted, then use
an app like [ES File Explorer]("https://play.google.com/store/apps/details?id=com.estrongs.android.pop&hl=en") to navigate to it's location.
[snip]
I've also attached build.prop and build.prop.original, for anyone that is curious.

It only allows you a one shot read of the .prop files .. other wise it keeps numbering them (1) (2) etc... so I guess I'll have to download them..

Edit:
Downloading those files are readable.

---

### Post by kccv42 on 2014-12-10
I have the RCA Pro Edtion 10in tablet. I am interested in putting ubuntu touch on it but worried how to go back to the kikat version later.

---

### Post by sammiev on 2014-12-10
> **kccv42 said:**
> I have the RCA Pro Edtion 10in tablet. I am interested in putting ubuntu touch on it but worried how to go back to the kikat version later.

+1 I have the same unit and reading on as to have hope to do the same.

---

### Post by ventrical on 2014-12-10
> **cariboo907 said:**
> In my quest to install Ubuntu Touch on my RCA tablet, I've tried the following things, first, is to 
see what the device looks like to another system. I used the following command found[ here]("http://[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/") to gather some information:

```
adb shell grep ro.product.name /system/build.prop > mydevicedata \
&& adb shell grep build.id /system/build.prop >> mydevicedata \
&& adb shell grep ro.product.device /system/build.prop >> mydevicedata
``` 

Creates a file called mydevicedata, to view the file in a terminal type:

```
cat mydevicedata
```

which results in:

```
cat mydevicedata
ro.product.name=RCT6773W22
ro.build.id=KOT49H
ro.product.device=RCT6773W22
# ro.build.product is obsolete; use ro.product.device
```

There's not a lot of help here, as we already know this.


When it reports #ro.build.product is obsolete; use ro.product.device   I think  (my assumption)it is meant that the file has to be literally edited , ie; the line  in the build prop file,

```

ro.build.product=rct6773w22

```

needs to be changed to

```

ro.product.device

```
 or
```

ro.product.device=rct6773w22

```

I'll try an edit with the latter.

I'll get back later.

Edit:

Will not let me save ro.prop.Reports Error. I have rooted device . Must need permissions then  in ES File Exploer?

---

### Post by cariboo on 2014-12-10
You shouldn't be able to access / if you aren't rooted. I copied build.prop to my desktop system and planned on editing in gedit, then copying it back to the tablet. 

I recall seeing mention of some HTC devices last week, when I was running some of the adb commands but I don't remember how I made it happen. I usually document what I'm doing but last week, I failed to do it, so now I have to start all over again. :(

---

### Post by ventrical on 2014-12-10
> **cariboo907 said:**
> You shouldn't be able to access / if you aren't rooted. I copied build.prop to my desktop system and planned on editing in gedit, then copying it back to the tablet. 

That way might work. Maybe it is prob with ES editor.
> 
I recall seeing mention of some HTC devices last week, when I was running some of the adb commands but I don't remember how I made it happen. I usually document what I'm doing but last week, I failed to do it, so now I have to start all over again. :(

Gee... pretty well same thing here. I've come close.  I'm still on it.  I am actually beginning to like the tablet as it is... but I would like to see Ubuntu on it also.... I read some where about dual boot and I of all people should have documented that, but I didn't.

---

### Post by ventrical on 2014-12-10
ES had caused some problem on my tablet. When I try to run the root tool in (tools which is off by default) it knocks out the /root/ access I have from iRoot. So I have to run iRoot  to get #root#,then , run ES, tools and knocks out root again. This is why I cannot edit or copy  file build.prop to SD..

---

### Post by ventrical on 2014-12-11
Just making mention of the unreliability of rooting applications for android. I have one app that says I am "rooted" and another app says "not rooted: Also iroot app is on again /off again.  So it is difficult to discern rooted/not rooted and the quality and trustworthiness of the apps available out there.

Regards..

---

### Post by cariboo on 2014-12-11
@ventrical have you got something like [SuperSU]("https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=en") installed it allows you to give root access to any apps that need it.

[[img]http://i.imgur.com/xWbIzPKl.png[/img]](http://imgur.com/xWbIzPK)

---

### Post by ventrical on 2014-12-11
> **cariboo907 said:**
> @ventrical have you got something like [SuperSU]("https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=en") installed it allows you to give root access to any apps that need it.

[[IMG]http://i.imgur.com/xWbIzPKl.png[/IMG]]("http://imgur.com/xWbIzPK")


It's asking me Normal or TWRP/CWM    I'll try normal.

---

### Post by ventrical on 2014-12-11
Normal doesn't work. 

TWRP/CWM says it will attempt to reboot (but does not work on all systems) now I just have screen that says "No apps configured' .. so I'll wait a bit and try again.

---

### Post by ventrical on 2014-12-11
Several apps tell me I am rooted but I can't write to internal storage etc..

---

### Post by ventrical on 2014-12-11
Just will not let me write to file even though it says I have read/write access. Wow .. this is frustrating .

---

### Post by WinEunuchs2Unix on 2014-12-14
> **cariboo907 said:**
> @ventrical have you got something like [SuperSU]("https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=en") installed it allows you to give root access to any apps that need it.

[[IMG]http://i.imgur.com/xWbIzPKl.png[/IMG]]("http://imgur.com/xWbIzPK")

There is a multi-boot manager called "Boot Manager Pro" that sells for 3 bucks on Google Store.  It says not to use Super User with it's product because there is a bug in it.  [https://play.google.com/store/apps/details?id=com.drx2.bootmanager&hl=en](https://play.google.com/store/apps/details?id=com.drx2.bootmanager&hl=en)

It looks interesting and I wonder if anyone reading this has tried it yet? (1,072 downloads to date).

Keenly hoping for a tablet soon that can multi-boot OS's, WiFi and Cell Phone...

---

### Post by ventrical on 2014-12-14
Yes.. I have read up on multi-boot tab. I am trying to keep it all "free" software. Some of those apps will apply charges to your provider. 'Slating (using phones and tablets) can cost hidden fees. 

I may have to restore my slate and start over again.

Regards..

---

### Post by ventrical on 2014-12-15
@cariboo

 Try Debian Kit from the app store. It will give you terminal. From there you can install ubunt repos .. etc.. or so it says. Mine will not work as it still says I am not rooted from some apps and not others.

[s]Also 'Complete Linux Installer' will set up Ubuntu 13.10 on the SD card ( a good read) and from there you can perhaps update/upgrade to vivid. My SD card is too small atm .. so I have to get  a larger microsd card.  I am going to go ahead and try to install the smaller 500MB image and try to update.[/s]

Not a complete loss as I was actually able   to transfer files back and forth between internal storage and SD card. The SD card is very sensitive and if you do not have enough space it will tell you that you do not have permissions .. etc... anyways .. the whole concept being that one may be able to boot from SD card. 

The basic errors I have been getting is that 'not supported'  comes up alot. It appears also that if you try to update the current ubuntu kernel that is on the slate that it will break it. (RCA black Friday brand).

---

### Post by sammiev on 2014-12-15
Hi ventrical, I can not believe you threw that may apps at it and it's still running.

I have been looking at kingo or VROOT for root. Thread getting long, have you looked at either?

Info I got [here]("http://forums.androidcentral.com/other-tablets/355355-custom-rom-rca-tablet.html").

Edit: I see you tried kingo as listed back a thread or two but I see another app is required.

---

### Post by cariboo on 2014-12-15
> **sammiev said:**
> Hi ventrical, I can not believe you threw that may apps at it and it's still running.

I have been looking at kingo or VROOT for root. Thread getting long, have you looked at either?

Info I got [here]("http://forums.androidcentral.com/other-tablets/355355-custom-rom-rca-tablet.html").

Searching for vRoot, actually takes you to the iRoot home page, it worked OK for me, but take note of the warning I posted [here]("http://ubuntuforums.org/showthread.php?t=2254725&p=13183586&viewfull=1#post13183586")

---

### Post by sammiev on 2014-12-15
> **cariboo907 said:**
> Searching for vRoot, actually takes you to the iRoot home page, it worked OK for me, but take note of the warning I posted [here]("http://ubuntuforums.org/showthread.php?t=2254725&p=13183586&viewfull=1#post13183586")

Thanks

---

### Post by ventrical on 2014-12-15
> **sammiev said:**
> Hi ventrical, I can not believe you threw that may apps at it and it's still running.

I have been looking at kingo or VROOT for root. Thread getting long, have you looked at either?

Info I got [here]("http://forums.androidcentral.com/other-tablets/355355-custom-rom-rca-tablet.html").

Edit: I see you tried kingo as listed back a thread or two but I see another app is required.

Thanks for reply and encouragement.  :)  I am getting very close. I think this 'long thread' may turn up success eventually.

I used the iRoot method and I am certain now that my slate is rooted. The problem is that  one has to follow  a very carefully well laid order of (app)erations.

Order of (App)erations. Much like Order of Operations.  (Not related to apparitions such as ghosts and personages.  Remember .. you heard it here first :)

 As for cariboos warning , I am trying to remove this one app that is hidden that has the icon of a horse. I may have to start from square one and I am still searching for other free apps to  see what is quality out there.

  I'll keep you all aprised..

Regards..

---

### Post by ventrical on 2014-12-16
Just to eliminate the possibility that there is something wrong with my Trusty install that I am using to  download all the PPAs, I am going to try all this on Precise and see if that works as far as the <oem unlock> because that is where everything seems to be failing atm.

---

### Post by cariboo on 2014-12-16
Well it seems I have bricked mine :( I was running:

```
fastboot oem unlock
```

and accidentally unplugged the usb cable.

I've tried a couple of restore images for other devices, but so far everything has failed. The only one that I tried that looked like it might be successful, Samsung Galaxy 3, failed at 94%.

---

### Post by ventrical on 2014-12-16
> **cariboo907 said:**
> Well it seems I have bricked mine (: I was running:

```
fastboot oem unlock
```

and accidentally unplugged the usb cable.

I've tried a couple of restore images for other devices, but so far everything has failed. The only one that I tried that looked like it might be successful, Samsung Galaxy 3, failed at 94%.


I did the same thing here but was able to recover by reinserting USB after closing terminal/reopen terminal and run 
```

fastboot reboot

```

Looks like  you got the closest so far. Hope you can restore bricked slate.

---

### Post by cariboo on 2014-12-16
> **ventrical said:**
> I did the same thing here but was able to recover by reinserting USB after closing terminal/reopen terminal and run 
```

fastboot reboot

```

Looks like  you got the closest so far. Hope you can restore bricked slate.

I contacted RCA technical support to see if they can provide a link to a recovery image.Hopefully they are still as good as they were back in the day when I used to repair their VCRs and Stereo systems.

---

### Post by kccv42 on 2014-12-16
If you can get a an image be sure to share it with me.

---

### Post by ventrical on 2014-12-17
I have a 420MB backup image. It restores from SD card. I have already used it once. I wiped the tablet completely  and it worked just fine when running from the recovery option from boot menu.

Whoops :) Had my gmail account on there. :) I was sending it up.. :)  I don't think it would have worked.

 Had a good sleep here.

  I can wipe and make another generic backup and we can try that. In fact I was thinking that the recovery option from Fastboot would be the way to install an image but it will only recognize file ext with .backup

Regards..

---

### Post by cariboo on 2014-12-17
This is one of those cases where I had made several backups, but the one I needed, I never checked. the others are only backups of user data. I'm assuming that when the O/S is updated, everything gets over-written with new versions of the files, so I'm using:

```
sudo adb sideload <img file>
```

When my Nexus 5 updated to Android 5, it downloaded about 450MiB of data, then took about 10 minutes to install the new/updated files, I'm hoping that using abd sideload works the same way.

---

### Post by ventrical on 2014-12-17
> **cariboo907 said:**
> This is one of those cases where I had made several backups, but the one I needed, I never checked. the others are only backups of user data. I'm assuming that when the O/S is updated, everything gets over-written with new versions of the files, so I'm using:

```
sudo adb sideload <img file>
```

When my Nexus 5 updated to Android 5, it downloaded about 450MiB of data, then took about 10 minutes to install the new/updated files, I'm hoping that using abd sideload works the same way.

What was the actual name of the <img file> ???  Just that there ?

  I tried using the; for example
```

adb sideload  vivid-preinstalled-recovery-armel+flo.img

```
 etc.. along with the other images but they keep terminating.

---

### Post by ventrical on 2014-12-17
Here is what I got when I unpacked that file I downloaded originally and I think the trick is to make it into an .img file .. but not sure what program to use.  A needle in a haystack is one thing but this is beginning to become like the rage over looking for a lost penny! (Beethoven)

:)

Regards..

---

### Post by ventrical on 2014-12-17
!

```

adb backup -system

```

will NOT work for current RCA model discussed.

*note*

  I tried to  to a backup from the bootloader.  Then is hung on 'installing updates' and after w hile , finished. So I'll reboot now and see what happened.

edit:

nothing happened.

---

### Post by ventrical on 2014-12-17
> **cariboo907 said:**
> I bought this [RCA]("http://www.rcatablets.com/tablets/7-voyager") 7" tablet at Walmart's Black Friday sale, the price was right, and the specs were pretty good, It has 8Gib of storage, and an ArmV7 quad core processor. It already has Ubuntu installed, see the screenshot, so it shouldn't be too tough to install Touch on it. I got the image from [here]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/"). I'll update this thread as I progress.

The link within the link which you provided  [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)  is totally obsoleted and has absolutely nothing to do with installing the image file you referenced.

Regards..

---

### Post by ventrical on 2014-12-17
The adb sideloader does not recognize the  .tar.gz  format.

 How do I convert the files inside of  vivid-preinstalled-touch-armhf.tar.gz to vividtouch.zip ??

 I try unpacking to directory but then those files will not zip . I get a read  error or unknown files.

@cariboo

Read here - > [http://www.droid-life.com/2013/02/12/download-nexus-7-android-4-2-2-jdq39-update/](http://www.droid-life.com/2013/02/12/download-nexus-7-android-4-2-2-jdq39-update/)

  I think if I can convert the files in the tar.gz format to zip that it will actually install the image from adb recovery mode on the tablet. I think this is where the problem (and the solution) is  for original post of install vivid test on RCATab

Regards..

---

### Post by ventrical on 2014-12-17
Back to the drawing board :)

---

### Post by ventrical on 2014-12-19
I tried the  <fastboot flashall -p RCT6773W22 in fastboot mode by entering into the directory where I had extracted the image from the vivid archive (and also was able to create various *.zip files and use the <adb sideload> option but to no avail.  All the instructions on the myraid of websites I have researched all point to pretty well the same proceedures using adb, fastboot and the tablet recovery mode  but it seems one of the core issues is getting to a true '#root' as many applications will report "rooted" and others "not rooted". 

The RCA tablet is proving enigmatic as it seems impervious to be being unlocked, however one article (can't recall off hand) says that after the <adb reboot bootloader> command in invoked that  the <fastboot oem unlock> is not necessary when the tablet is displaying  white background screen and the verbose <Fastboot mode=> at the lower lefthand of the screen.

Another difficulty where the provided documentation is lacking, is backing up an image of the whole RCA tablet system.  There *are* apps that claim to do so. The free ones will tell you you are not #rooted# (when other 'am I rooted' apps will tell you you are #rooted#) and there are apps that claim to do this , but for a fee, all the more reason to have  opensource OS on this gadget.

  I have been trying to make an image that can be read  from the 'restore' option in the bootloader.  This tool seems to work well and I had just thought that if a backup os system could be made and put up for backup option that others may not feel too inhibited to try  and work on this RCA device and others similar. It may also be a way to spoof ubuntu image  through is port.

I am sure the answer is simple but for now the code to do so  is elusive.

edit:  I also assumed perhaps that there may be some sort of conflict with trusty and usb ver3.0 so I tried a different machine with xubuntu and the same proceedures but no success.



I've taken a time out here and am back a it. :)

Regards..

---

### Post by cariboo on 2014-12-19
I rooted my Nexus 5, then used Nandroid to do a complete back up of everything on the phone, in order to see ifI could force the backup on to the tablet. All the adb commands including:

```
fastboot oem unlock
```

worked like a charm. I'm still convinced that the tablet needs to be unlocked in order to install Ubuntu Touch on it. I guess another emaill to 1800customersupport.com is in order, to see if they have any instructions in their playbook on how to unlock the device.

---

### Post by ventrical on 2014-12-19
I'll have to try this. I didn't know about the sdk.exe and drivers.

[https://www.youtube.com/watch?v=qaRvUeSdrL4](https://www.youtube.com/watch?v=qaRvUeSdrL4)

---

### Post by ventrical on 2014-12-19
> **cariboo907 said:**
> I rooted my Nexus 5, then used Nandroid to do a complete back up of everything on the phone, in order to see ifI could force the backup on to the tablet. All the adb commands including:

```
fastboot oem unlock
```

worked like a charm. I'm still convinced that the tablet needs to be unlocked in order to install Ubuntu Touch on it. I guess another emaill to 1800customersupport.com is in order, to see if they have any instructions in their playbook on how to unlock the device.

 I mee tooed it. :) I must be getting old. Back 25 years ago I've of hacked this one in less than 24 hours. :)lol

---

### Post by ventrical on 2014-12-19
I factory reset my slate, then did a backup through adb.

```

 adb backup -apk -shared -all -f test.backup

```

It is only 16MBs though.  

If anybody has a bricked device and wants to try this.

edit.. Ok .. forum will not allow for uploading larger than 976.6KBs for .zip

---

### Post by ventrical on 2014-12-19
I sent an e--mail to RCA helpdesk and received a prompt reply. My email stated that I could not get the bootloader to oem unlock and I asked .. how to ?

They sent me a link to a proceedure that I have must of done about  at least 60 times now...

[http://www.rcatablets.com/how-completely-reset-your-rca-android-7-voyager-tablet-android-44](http://www.rcatablets.com/how-completely-reset-your-rca-android-7-voyager-tablet-android-44)

<sigh>

edit:

 I sent a reply with more detail and asked if they have any developer tools or other methods to unlock the fastboot bootloader oem.

---

### Post by ventrical on 2014-12-20
I think it has to do with this here:

```

root@ventrical-MS-7798:~# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 0bb4:0c01 HTC (High Tech Computer Corp.) Dream / ADP1 / G1 / Magic / Tattoo
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ventrical-MS-7798:~# 

```


I'll be back with edit.  Something about the HTC version.

Ok.. using 

```

lsusb -v

```

should produce -

```

Bus 003 Device 012: ID 0bb4:0c01 HTC (High Tech Computer Corp.) Dream / ADP1 / G1 / Magic / Tattoo
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bb4 HTC (High Tech Computer Corp.)
  idProduct          0x0c01 Dream / ADP1 / G1 / Magic / Tattoo
  bcdDevice            1.00
  iManufacturer           1 MediaTek
  iProduct                2 Android
  iSerial                 3 mt8127_phone
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              256mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     66 
      bInterfaceProtocol      3 
      iInterface              4 fastboot
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered

```

xda says that the version has to be updated.

[http://android.stackexchange.com/questions/40450/unlock-bootloader-using-fastboot-using-ubuntu-linux](http://android.stackexchange.com/questions/40450/unlock-bootloader-using-fastboot-using-ubuntu-linux)

[http://forum.xda-developers.com/showthread.php?t=1205605&page=15](http://forum.xda-developers.com/showthread.php?t=1205605&page=15)

Edit:

As usual this process failed , even updating from the SD card using the tablet bootloader options.

---

### Post by allerkogo on 2014-12-20
thx

---

### Post by ventrical on 2014-12-20
Part of the problem is that the ubuntu server does not support this RCA version. Unless there is a way to spoof it out.

```

ubuntu-device-flash --channel=devel --bootstrap


```
```

2014/12/20 03:31:52 Expecting the device to be in the bootloader... waiting
2014/12/20 03:31:52 Device is |RCT6773W22|
Device RCT6773W22 not found on server https://system-image.ubuntu.com channel devel
ventrical@ventrical-MS-7798:~/Downloads$ 

```

---

### Post by ventrical on 2015-08-05
Bump!

I have been working on another idea. Haven't tried it yet, not exactly sure what it is and I am a little rusty .. but I just wanted to bump this  up in light of recent developments with snappy.

Regards..

---

### Post by sammiev on 2015-08-05
> **ventrical said:**
> Bump!

I have been working on another idea. Haven't tried it yet, not exactly sure what it is and I am a little rusty .. but I just wanted to bump this  up in light of recent developments with snappy.

Regards..

+1 I have followed this thread from the start.

---

### Post by ventrical on 2015-08-05
I thought I could use 'disks' or mkusb to hack it ... but honestly .. it's  like a barnacle on a ships hull. :)


Regards..

---

### Post by ventrical on 2015-08-05
I tried a new extra that I hadn't opened and didn't put any info on it and I still cannot get the:

```

=>FASTBOOT mode...

```

Everything else works but when it gets to this point is just hangs...waiting for something else I guess.

---

### Post by ventrical on 2015-09-16
Bump!

@Cariboo

Anyway to bump this up or edit  the title so it includes wily/snappy so that it would be current in development version? I just need it as a current reference side kick.

thanks
Regards..

---

### Post by ventrical on 2015-09-16
I'll be using the wily images as oppossed to vivid images.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/)

---

### Post by cariboo on 2015-09-16
> **ventrical said:**
> Bump!

@Cariboo

Anyway to bump this up or edit  the title so it includes wily/snappy so that it would be current in development version? I just need it as a current reference side kick.

thanks
Regards..

It may be better to start a new thread, as this was created during the Vivid development cycle.

---

### Post by ventrical on 2015-09-29
> **DogMatix said:**
> [How to root RCT6773W22 (rca voyager) -  XDA Developers]("http://forum.xda-developers.com/android/development/how-to-root-rct6773w22-rca-voyager-t2955600")

Sounds like someone else having fun with Black Friday mechandise.

Just as an update ... Kingo root can now be downloaded from Google Store which is provided by default on the RCA tablet.  It has rooted successfully everytime on both my RCA Voyager 7" tablets .. so there is no need to use a Windows OS to do this any longer. 

Regards..

---

### Post by QDR06VV9 on 2015-09-29
Will Kingo install one of  the .img from ubuntu?
Just curious.
Thanks

---

### Post by ventrical on 2015-09-29
> **runrickus said:**
> Will Kingo install one of  the .img from ubuntu?
Just curious.
Thanks


Yes and no.  Linux Deploy along with VNC will load a 'linux.img' file 4GBs in size. Once you learn how to use Linux Deploy app (free) and VNC app (free) you can pretty well run LXDE or Xubuntu desktop. However, the problem is that this image created and downloaded will only run on the VNC which is like a virtual machine on top of Android. What we really want is to be able to load a recovery image so that we can boot directly into the image. I have been hacking and searching around, trying to develop a hack that will work around the Nexus limitation that adb and tools and other scripts limit us to.

 I have been able to run LDXE 15.10 and Xubuntu 15.10 on top of android but  this is not what we want.  We want either raw ubuntu recovery image to boot n' brick our slates or the dual boot option to be able to boot from a linux image at android startup. I came very , very close but some of the scripts are so outdated and there is not much new info on the RCA brand anyways. There are other methods where one can use Windows 7/8 or whatever  but I DO not want to go that route and it is not trustworthy and if it comes to choices then I'll just leave my slates be as there are because they already have ubuntu.kernels on them.

 With the RCA Voyager set I am assuming there is a code bug in the fastboot/adb routines/tools. I read all about the {TWRP} flashing methods .. yada .. etc.. perhaps that is working for some. Windows may provide more documentation but documentation is lite with ubuntu.

  What I plan to do  is a review of this current thread even though it is expired from development, but, because it has sensitive links and pertinent data I think it should stay for a bit because it might eventually help us with install snappy-personal . .in the long run. These particular tablets are tough nuts to crack :)

regards..
[http://ubuntuforums.org/showthread.php?t=2295245&p=13358419#post13358419](http://ubuntuforums.org/showthread.php?t=2295245&p=13358419#post13358419)

---

### Post by QDR06VV9 on 2015-09-29
> **ventrical said:**
> Yes and no.  Linux Deploy along with VNC will load a 'linux.img' file 4GBs in size. Once you learn how to use Linux Deploy app (free) and VNC app (free) you can pretty well run LXDE or Xubuntu desktop. However, the problem is that this image created and downloaded will only run on the VNC which is like a virtual machine on top of Android. What we really want is to be able to load a recovery image so that we can boot directly into the image. I have been hacking and searching around, trying to develop a hack that will work around the Nexus limitation that adb and tools and other scripts limit us to.

 I have been able to run LDXE 15.10 and Xubuntu 15.10 on top of android but  this is not what we want.  We want either raw ubuntu recovery image to boot n' brick our slates or the dual boot option to be able to boot from a linux image at android startup. I came very , very close but some of the scripts are so outdated and there is not much new info on the RCA brand anyways. There are other methods where one can use Windows 7/8 or whatever  but I DO not want to go that route and it is not trustworthy and if it comes to choices then I'll just leave my slates be as there are because they already have ubuntu.kernels on them.

 With the RCA Voyager set I am assuming there is a code bug in the fastboot/adb routines/tools. I read all about the {TWRP} flashing methods .. yada .. etc.. perhaps that is working for some. Windows may provide more documentation but documentation is lite with ubuntu.

  What I plan to do  is a review of this current thread even though it is expired from development, but, because it has sensitive links and pertinent data I think it should stay for a bit because it might eventually help us with install snappy-personal . .in the long run. These particular tablets are tough nuts to crack :)

regards..
[http://ubuntuforums.org/showthread.php?t=2295245&p=13358419#post13358419](http://ubuntuforums.org/showthread.php?t=2295245&p=13358419#post13358419)
Yup Linux Deploy along with VNC is about the only method I have been able to mustard up.
On my Sero 7 pro I just about hard bricked it. Sheesseesh, but I got got it back to lolipop.
But there is another thread i am looking at maybe a hack to get it working
[http://ubuntuforums.org/showthread.php?t=2263389&page=2](http://ubuntuforums.org/showthread.php?t=2263389&page=2) post #18
Thanks Ventrical

---

### Post by ventrical on 2015-09-29
> **ventrical said:**
> Some progress.

 You have to get to the =>FASTBOOT mode... screen first, then

```

ventrical@ventrical-MS-7798:~$ adb reboot bootloader
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
ventrical@ventrical-MS-7798:~$ ubuntu-device-flash --bootstrap
DEPRECATED: Implicit 'touch' subcommand assumed
2014/12/08 09:31:03 Expecting the device to be in the bootloader... waiting
2014/12/08 09:31:03 Device is |RCT6773W22|
Device RCT6773W22 not found on server https://system-image.ubuntu.com channel ubuntu-touch/stable
ventrical@ventrical-MS-7798:~$ 

```

so to overwrite you have to be able to name a source device that will overwrite(replace) |RCT6773W22|. So looks like some work renaming .. fanagling  around...because we want /vivid/ and not stable  :)


Some progress . The device is now recognized.

```

ventrical@ventrical-MS-7798:~$ ubuntu-device-flash --bootstrap
DEPRECATED: Implicit 'touch' subcommand assumed
2015/09/29 12:39:30 Expecting the device to be in the bootloader... waiting
2015/09/29 12:39:30 Device is |RCT6773W22|
Channel  not found on server https://system-image.ubuntu.com
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2015-09-29
Just out of curiostiy I ran the command:

```

adb bugreport

```

and the slate blacked out while a plethora of verbose code raced across the terminal. After it was finished I tried to find the 'log' file and the whole system (desktop 14.04) locked up. When I pulled the adb cable out it let me back in. So this is another report tool that is buggy with these programs.

regards..

---

### Post by ventrical on 2015-09-29
Everything you need to know about your RCA tablet.
:note: This is a monster bug report. It's a real sleeper.. but if you like reading code .. then it's for you :)

---

### Post by QDR06VV9 on 2015-09-29
Can you disable SELINUX?
I have not got as far as you yet.
I am trying to find a RCA Tab to mess with.
Both of mine Sero 7 && Samsung tab2 are no go's.
I have tried everything under the sun to no avail. :confused:

---

### Post by ventrical on 2015-09-29
> **runrickus said:**
> Can you disable SELINUX?
I have not got as far as you yet.
I am trying to find a RCA Tab to mess with.
Both of mine Sero 7 && Samsung tab2 are no go's.
I have tried everything under the sun to no avail. :confused:

Everything I get I'll put up here. I have a Proscan tablet also and it has been  useless trying to get than thing going with an ubuntu spin. I thought the Samsungs were being hotly developed.

I am on second shift of the day here :)hehehehe
 I am hoping I get  a 'ta da!' moment soon... but it does not look good.
Regards..

edit:

@ runrickus

I read up a lot about why different proprietors are employing unlockable bootloaders. First reason is money of course. There is a Mortorola brand that if you try to unlock the bootloader it will  purposely brick into a permanent off state, never to be enabled to an on state again. There are also bounties offered for those who can crack locked bootloaders. In the RCA 7" Voyager case they are using an open source ubuntu kernel and this defies the spirit of open source in that they  have their bootloader vaulted. It's not that it cannot be done. It is just  the hours of added scripting, testing and hacking that can be somewhat arduous and disappointing. I guess from the proprietors' point of view that would be 'mission accomplished'.

Regards..

---

### Post by QDR06VV9 on 2015-09-30
> [COLOR=#000000][INDENT]@ runrickus

I read up a lot about why different proprietors are employing unlockable bootloaders. First reason is money of course. There is a Mortorola brand that if you try to unlock the bootloader it will purposely brick into a permanent off state, never to be enabled to an on state again. There are also bounties offered for those who can crack locked bootloaders. In the RCA 7" Voyager case they are using an open source ubuntu kernel and this defies the spirit of open source in that they have their bootloader vaulted. It's not that it cannot be done. It is just the hours of added scripting, testing and hacking that can be somewhat arduous and disappointing. I guess from the proprietors' point of view that would be 'mission accomplished'.

Regards..[/INDENT]


[/COLOR]

I found one in the local ad section of a newspaper I had talked to guy for about 2 hrs he also Tells of the same information you have here.
Decided I would wait for things to become more mature and more devices being supported.
Guess they decided that my samsung Tab GT-3110 is to old. There is an old Quantral .img out there, But what for?
Found a couple of links that might be useful, and then again maybe not

[http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page22](http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page22)

[http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page18](http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page18) post #175

On that same forum there was a guy who claimed he had installed wily on a Sero 7 Pro but I call BS, There was about 6 other's calling him out on that also. 
So that is where I am for now.
Oh just to be clear I have already Rooted both of my devices so i guess i will continue testing for [COLOR=#6A6A6A][FONT=arial]**CyanogenMod only for those two devices.**[/FONT][/COLOR]
Regards

---

### Post by ventrical on 2015-09-30
> **runrickus said:**
> I found one in the local ad section of a newspaper I had talked to guy for about 2 hrs he also Tells of the same information you have here.
Decided I would wait for things to become more mature and more devices being supported.
Guess they decided that my samsung Tab GT-3110 is to old. There is an old Quantral .img out there, But what for?
Found a couple of links that might be useful, and then again maybe not

[http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page22](http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page22)

[http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page18](http://forum.xda-developers.com/general/help/root-rca-7-voyager-rct6773w22-tablet-t2954669/page18) post #175

On that same forum there was a guy who claimed he had installed wily on a Sero 7 Pro but I call BS, There was about 6 other's calling him out on that also. 
So that is where I am for now.
Oh just to be clear I have already Rooted both of my devices so i guess i will continue testing for [COLOR=#6A6A6A][FONT=arial]**CyanogenMod only for those two devices.**[/FONT][/COLOR]
Regards

 I tried the 'scatterfile" method as mentioned by Cariboo in another thread. Trying to do that work-a-round on Windows 7 gave me night terrors. Thats why I think I may have hit a brick wall and have to conceed on these RCA bricks. It's an awful game. As per your link .. it talks of superSu and Kingo.. it roots , it unroots .. it is  just a lot of malarkey and it says volumes about the quality  of android apps that are out there a that are completely useless. I worked it all over again  - getting ready to install the modified build.prop and then ES Explorer all of a sudden says it cannot write to protected file system when I tired to move the new build.prop over to root. Then SuperSu asks for TWRP/CVM or normal and no matter what I do it fails. Boy oh boy did that ever get my shorts in a knot !

  I am going to try one more method . To directly restore an image to the root directory because even if I brick it completely I'll have some sense  that I have accomplished something :) 

Regards..

---

### Post by ventrical on 2015-09-30
SuperSu keeps asking to update binary then fails. Then I cannot use ES Explorer to move or copy build files to other directories on internal storage. So this is the fly in the ointment atm.

---

### Post by QDR06VV9 on 2015-09-30
> **ventrical said:**
> I tried the 'scatterfile" method as mentioned by Cariboo in another thread. Trying to do that work-a-round on Windows 7 gave me night terrors. Thats why I think I may have hit a brick wall and have to conceed on these RCA bricks. It's an awful game. As per your link .. it talks of superSu and Kingo.. it roots , it unroots .. it is  just a lot of malarkey and it says volumes about the quality  of android apps that are out there a that are completely useless. I worked it all over again  - getting ready to install the modified build.prop and then ES Explorer all of a sudden says it cannot write to protected file system when I tired to move the new build.prop over to root. Then SuperSu asks for TWRP/CVM or normal and no matter what I do it fails. Boy oh boy did that ever get my shorts in a knot !

  I am going to try one more method . To directly restore an image to the root directory because even if I brick it completely I'll have some sense  that I have accomplished something :) 

Regards..
You now know where I was coming from in the other messages we discussed.(PM) I still owe you an ear:D

> **ventrical said:**
> SuperSu keeps asking to update binary then fails. Then I cannot use ES Explorer to move or copy build files to other directories on internal storage. So this is the fly in the ointment atm.
That's pretty normal I have seen that message 100 times if I seen it once.
I learned if I did see that it was going to be a journey of 1000 steps.:D

---

### Post by ventrical on 2016-06-23
Ok.. Bump !

:)

ahhh.. I am going to  try something soon. Not sure what .. but something. Snappy or yappity I think:)


Regards..

---

