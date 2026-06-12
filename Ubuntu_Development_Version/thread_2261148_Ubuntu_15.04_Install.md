---
title: "Ubuntu 15.04 Install"
date: 2015-01-16
forum: Ubuntu Development Version
---

### Post by Redalien0304 on 2015-01-16
I have tried to Install Ubuntu 15.04 Alpha but it is 14.04 i can tell by the kernel 3.24 if i remember right. Did the Alpha with 14.04 when it came out, was not that much of Problem. Have download form [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Any help would be Appreciated. Thanks

---

### Post by buzzingrobot on 2015-01-16
What does 'cat /etc/issue' show?

I did an install earlier today of today's daily and the kernel is  3.18.0-9-generic.

---

### Post by grahammechanical on 2015-01-16
Vivid Vervet is being built on the 14.10 code base. It started with the 14.10 kernel, 3.13 and has moved on to 3.15, then 3.16 and the latest daily ISO images do indeed have 3.18.

At the beginning of the development period we still have the 14.10 labels but that has been corrected for some time. The login screen says Ubuntu 15.04 and so does the Details page. The ISO image is vivid-desktop-amd64.iso. The installation slideshow will still be 14.10. There should be nothing 14.04 about Vivid Vervet.

Regards.

---

### Post by Redalien0304 on 2015-01-16
Here are cat /etc/issue 
Ubuntu 14.04.1 LTS \n \l
uname -a
Linux craig-ThinkPad-T60p 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Generic linux-headers-generic versions & linux-image-generic version 3.13.0.43.50 are in the Update list. did not update yet.

---

### Post by grahammechanical on 2015-01-16
This is what I get

> cat /etc/issue
Ubuntu Vivid Vervet (development branch) \n \l




> uname -a
Linux sdb8-Roll-Dev 3.18.0-9-generic #10-Ubuntu SMP Mon Jan 12 21:41:54 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Ubuntu 14.04.1 got the 14.10 kernel - 3.13. 
Ubuntu 14.04.2 will come out in February and it will have kernel 3.16. 
Ubuntu 14.04.3 will come out in April and it most likely have the kernel that Vivid Vervet (15.04) now has - 3.18

What name did this ISO image have? The only explanation that fits is that you downloaded Ubuntu 14.04.1.

> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Vivid Vervet (development branch)
Release:	15.04
Codename:	vivid




The lsb_release file has said that since the first or second week of the development period. 
Regards.

---

### Post by Redalien0304 on 2015-01-17
was downloaded from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)  
[vivid-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/vivid-desktop-amd64.iso") was the name,i did rename it though.

---

### Post by ventrical on 2015-01-17
> **Redalien0304 said:**
> was downloaded from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)  
[vivid-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/vivid-desktop-amd64.iso") was the name,i did rename it though.

What did you rename it to?

Regards..

---

### Post by Redalien0304 on 2015-01-17
Renamed to Ubuntu 15.04 vivid-desktop-amd64 1-13-15.iso & used Startup Disk Creator on a Usb Stick.

---

### Post by ventrical on 2015-01-17
> **Redalien0304 said:**
> Renamed to Ubuntu 15.04 vivid-desktop-amd64 1-13-15.iso & used Startup Disk Creator on a Usb Stick.

Often what happens when renaming and Using SDC we do not always <select>  the right .iso to burn to USB, especially if we have mutiple .isos in the same directory. I would open SDC and check that out. I think this is what happened.

Regards..

---

### Post by grahammechanical on 2015-01-17
The last Vivid ISO image that I downloaded was the one from 15 Jan. I use DVDs. So, Nautilus Write to Disc option works for me. I am writing this from the Try Ubuntu session of the 15 Jan vivid daily image and it is not 14.04.

> unubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.18.0-9-generic #10-Ubuntu SMP Mon Jan 12 21:41:54 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid

ubuntu@ubuntu:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Vivid Vervet (development branch)"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


If it walks like a duck, talks like a duck and looks like a duck - what is it?

Regards.

---

### Post by forcecore on 2015-01-18
Anyone has lastest netboot iso?, jan 13 do not work [http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/)

---

### Post by grahammechanical on 2015-01-18
> **forcecore said:**
> Anyone has lastest netboot iso?, jan 13 do not work [http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/)

As a matter of simple curiosity, in what way does it not work?

Regards

---

### Post by forcecore on 2015-01-18
downloading file failed, retry, change mirror

---

### Post by funakyfunaky on 2015-01-18
I "burned" 17 January daily iso to a usb using the Startup disk creator tool. It didn't load on my machine. It hanged in the 15.04 logo (where some dots change colors). Tried installing the ISO using virtualbox. Got to the setup but it crashed after choosing the Timezone...
Anyone else had problems with recent isos?

---

### Post by Redalien0304 on 2015-01-18
Solved the way SDC has the ISO Selected. Now a update for SDC has gave me this [COLOR=#333333][FONT=monospace]"gfxboot.c32: not a COM32R image [/FONT][/COLOR][COLOR=#333333][FONT=monospace]boot:"
Did Workaround to bypass message "Press Tab & Select option".  Before the SDC Update was not getting this Message. The SDC version i have is 0.2.56.3. I have the Bug report on it at [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1342626](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1342626)[/FONT][/COLOR]

---

### Post by syntaxerror74 on 2015-01-18
NOTE:

Folks, we're closely approaching Alpha 2. Just saying. So you guys had better not bother with Alpha 1 quirks and (possibly) non-working stuff, but just wait some more hours (roughly 100 hours telling from current schedule) until **Alpha 2** is ready.
Maybe the issues reported by the OP some days ago will even resolve by itself that way.

---

### Post by ventrical on 2015-01-19
> **Redalien0304 said:**
> Solved the way SDC has the ISO Selected. Now a update for SDC has gave me this [COLOR=#333333][FONT=monospace]"gfxboot.c32: not a COM32R image [/FONT][/COLOR][COLOR=#333333][FONT=monospace]boot:"
Did Workaround to bypass message "Press Tab & Select option".  Before the SDC Update was not getting this Message. The SDC version i have is 0.2.56.3. I have the Bug report on it at [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1342626](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1342626)[/FONT][/COLOR]

The workaround for that is here:

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

---

### Post by ventrical on 2015-01-19
> **syntaxerror74 said:**
> NOTE:

Folks, we're closely approaching Alpha 2. Just saying. So you guys had better not bother with Alpha 1 quirks and (possibly) non-working stuff, but just wait some more hours (roughly 100 hours telling from current schedule) until **Alpha 2** is ready.
Maybe the issues reported by the OP some days ago will even resolve by itself that way.

There is nothing wrong with the .isos

Regards..

---

### Post by ventrical on 2015-01-19
> **grahammechanical said:**
> The last Vivid ISO image that I downloaded was the one from 15 Jan. I use DVDs. So, Nautilus Write to Disc option works for me. I am writing this from the Try Ubuntu session of the 15 Jan vivid daily image and it is not 14.04.



If it walks like a duck, talks like a duck and looks like a duck - what is it?

Regards.

All the .isos work for me. I use : 
[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

this option or SDC from an old Maveric install or mkusb. btw .. a big SDC update rolled in for 14.04.1 just the other day.

Regards..

---

### Post by kansasnoob on 2015-01-19
> **ventrical said:**
> The workaround for that is here:

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

Is persistence enabled by default using that method?

I kind of like just using dd for the speed (it takes only a couple of minutes as opposed to the 15 or 20 minutes either usb-creator or unetbootin require) but it doesn't create a persistent USB where changes are saved.

---

### Post by ventrical on 2015-01-19
> **kansasnoob said:**
> Is persistence enabled by default using that method?



No.

I kind of like just using dd for the speed (it takes only a couple of minutes as opposed to the 15 or 20 minutes either usb-creator or unetbootin require) but it doesn't create a persistent USB where changes are saved.[/QUOTE]

I use SDC from 10.10 and can still make persistent drives with dev isos.  I'll try with new SDC in Ubuntu.

  It never takes long here... 2 minutes max on ver 2.0 .. less with ver 3.0

---

### Post by ventrical on 2015-01-19
I am writing this message from live/persistent drive created with SDC in ubuntu-unity 15.04.

The actually process appears very buggy with reports going back and forth from 5 minute to 240 minutes .. all in all taking 4 minutes.

Btw this is cheap ver 3.0 usb stick .. I'm broke :)  Ok .. will save .. shut down , reboot and see how persistent it is.

Regards..

---

### Post by ventrical on 2015-01-19
Ok.. rebooted .. cliked on firefox and it brought me right back to this page. Success..... for now .. but it is not as fast as usual .. so I will try this in 14.04.1

Oh .. yeah ... buit got to get sleep first .. pooped ...

---

### Post by bcschmerker on 2015-01-19
**Good luck, everybody,** on getting Ubuntu® 15.01a2 up and running! 8-) I've already bumped my entire upgrade-Winbox schedule back, as Microsoft Corporation is looking for enterprise clients for the Windows® 10 Technical Beta (MultiProcessor Kernel 6.5.9840) as of this post.  I reckon on Win10 being ready for market about the time the first Ubuntu® 15.12a1 ISO becomes available - hopefully closer to the 16.01a2 ISO ready date, as I'd like a more stable LinUX Kernel for my Asus® 1630-06 as upgraded (Advanced Micro Devices® Athlon II® X2 220, 760G/SB700 chipset) along with better X.org radeon, ALSA snd-virtuoso, LinUXUVC, and so forth.
):P

---

### Post by ventrical on 2015-01-20
@kansasnoob,

  SDC is working in 14.04.1 persisitent also.

Regards..

---

### Post by kansasnoob on 2015-01-20
> **ventrical said:**
> @kansasnoob,

  SDC is working in 14.04.1 persisitent also.

Regards..

Cool, I'll be trying it soon.

---

### Post by /ADM on 2015-01-23
> **grahammechanical said:**
> Vivid Vervet is being built on the 14.10 code base. It started with the 14.10 kernel, 3.13 and has moved on to 3.15, then 3.16 and the latest daily ISO images do indeed have 3.18.

At the beginning of the development period we still have the 14.10 labels but that has been corrected for some time. The login screen says Ubuntu 15.04 and so does the Details page. The ISO image is vivid-desktop-amd64.iso. The installation slideshow will still be 14.10. There should be nothing 14.04 about Vivid Vervet.

Regards.

I've raised a bug and let the devs know that Welcome.html needs updating to 15.04.  I was truly amazed however that it took under 5 minutes to complete installation.  Like..  O__O

---

### Post by sudodus on 2015-01-23
Concerning the mini.iso:

> **grahammechanical said:**
> As a matter of simple curiosity, in what way does it not work?

Regards

> **forcecore said:**
> downloading file failed, retry, change mirror

I reported it at [https://bugs.launchpad.net/ubuntu/+source/gnupg/+bug/1403982](https://bugs.launchpad.net/ubuntu/+source/gnupg/+bug/1403982)

It was reported to be fixed 2015-01-14, but I have not seen the fix trickle down to us yet.

-o-

I was iso-testing Lubuntu alpha 2, and it worked well for me.

---

### Post by sudodus on 2015-01-23
> **kansasnoob said:**
> Is persistence enabled by default using that method?

I kind of like just using dd for the speed (it takes only a couple of minutes as opposed to the 15 or 20 minutes either usb-creator or unetbootin require) but it doesn't create a persistent USB where changes are saved.

... and I make the dd method safe using [mkusb]("https://help.ubuntu.com/community/mkusb"). This method is independent of mismatches between versions, so good when testing versions before they are released.

I think there are bugfixes for the[COLOR=#333333][FONT=monospace] "gfxboot.c32: not a COM32R image [/FONT][/COLOR][COLOR=#333333][FONT=monospace]boot:"[/FONT][/COLOR] bug, but I'm not sure they have trickled down everywhere yet. At least Unetbootin works for me now (from older Ubuntu versions to Utopic and Vivid).

*Edit*: and SDC works for *ventrical*, so things get better :-)

---

### Post by kansasnoob on 2015-01-23
> **sudodus said:**
> ... and I make the dd method safe using [mkusb]("https://help.ubuntu.com/community/mkusb"). This method is independent of mismatches between versions, so good when testing versions before they are released.

I think there are bugfixes for the[COLOR=#333333][FONT=monospace] "gfxboot.c32: not a COM32R image [/FONT][/COLOR][COLOR=#333333][FONT=monospace]boot:"[/FONT][/COLOR] bug, but I'm not sure they have trickled down everywhere yet. At least Unetbootin works for me now (from older Ubuntu versions to Utopic and Vivid).

*Edit*: and SDC works for *ventrical*, so things get better :-)

I notice they removed persistence testing from the basic Live iso-test on the QA Tracker, at least in Ubuntu GNOME, so I think I'll just not worry about persistence anymore. I have a somewhat oldish Puppy drive setup for some rescue operations, but otherwise I just don't care that much about persistence. I'll give mkusb a try soon.

---

### Post by sudodus on 2015-01-23
Persistence is still working with Unetbootin and the Startup Disk Creator (when you select it). I ***test it*** now and then, but I ***don't use*** it. Instead I use installed systems in USB 3 pendrives when I want 'more than standard live drives'. C.S.Cameron and a few other people were exploring persistence in dual- or multi-boot pendrives recently. See this link

[Multiboot flash drive with second partition]("http://ubuntuforums.org/showthread.php?t=2260697")

---

### Post by sudodus on 2015-01-25
> **forcecore said:**
> downloading file failed, retry, change mirror

The Ubuntu Vivid mini.iso works now. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2262339"]
testing vivid mini.iso[/URL]

---

### Post by repeztech on 2015-03-27
Always try in Virtual machine [https://youtu.be/XZKktVYfXqY](https://youtu.be/XZKktVYfXqY)

---

### Post by ubunt72 on 2015-03-28
If anyone cares, I used Startup Disk Creator in an installed 14.10 OS (14.04 was upgraded to 14.10 successfully, previously) and created a usb stick with 15.04-beta2 with Ubuntu MATE.   It booted up fine.   I deleted what was previously on the usb stick and formatted it w/ FAT32.    Then I used the Ubuntu program.   I don't have a good experience whenever I try to use Unetbootin.  I find it unreliable.

---

### Post by ubunt72 on 2015-03-28
> **ventrical said:**
> No.

I kind of like just using dd for the speed (it takes only a couple of minutes as opposed to the 15 or 20 minutes either usb-creator or unetbootin require) but it doesn't create a persistent USB where changes are saved.

I use SDC from 10.10 and can still make persistent drives with dev isos.  I'll try with new SDC in Ubuntu.

  It never takes long here... 2 minutes max on ver 2.0 .. less with ver 3.0dd is awesome.    If you have the correct syntax, it always works.    I wish Ubuntu would add 'mintstick' or whatever it's called.   I know you can add it with the ppa (I think?) as it seems even more reliable than Startup Disk Creator.   I have a LMDE install and was using their usb iso creator (Usb Image Writer?) program (it is supposedly called 'Mintstick' but doesn't list it as so, anywhere) and it has always worked.   They are just using dd and providing a gui front end.    Works perfectly.

---

### Post by ventrical on 2015-03-28
> **sudodus said:**
> ... and I make the dd method safe using [mkusb]("https://help.ubuntu.com/community/mkusb"). This method is independent of mismatches between versions, so good when testing versions before they are released.

I think there are bugfixes for the[COLOR=#333333][FONT=monospace] "gfxboot.c32: not a COM32R image [/FONT][/COLOR][COLOR=#333333][FONT=monospace]boot:"[/FONT][/COLOR] bug, but I'm not sure they have trickled down everywhere yet. At least Unetbootin works for me now (from older Ubuntu versions to Utopic and Vivid).

*Edit*: and SDC works for *ventrical*, so things get better :-)

Just an add on. No matter what method you use (and if the COM32R error comes up when booting USB) it always goes to Grub when using UEFI mode/then boots right into ubiquity. 

So non UEFI boot can equal COM32R error when using SDC but not with UEFI. Why ?

Regards..

---

### Post by sudodus on 2015-03-29
> **ubunt72 said:**
> dd is awesome.    If you have the correct syntax, it always works.    I wish Ubuntu would add 'mintstick' or whatever it's called.   I know you can add it with the ppa (I think?) as it seems even more reliable than Startup Disk Creator.   I have a LMDE install and was using their usb iso creator (Usb Image Writer?) program (it is supposedly called 'Mintstick' but doesn't list it as so, anywhere) and it has always worked.   They are just using dd and providing a gui front end.    Works perfectly.

I agree that dd is awesome (and dangerous).

mkusb is available from a PPA, so it is easy to install (in order to wrap security around dd)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2015-03-29
> **ventrical said:**
> Just an add on. No matter what method you use (and if the COM32R error comes up when booting USB) it always goes to Grub when using UEFI mode/then boots right into ubiquity. 

So non UEFI boot can equal COM32R error when using SDC but not with UEFI. Why ?

Regards..

I think you just showed us why. COM32R is used with syslinux but not with grub.

---

