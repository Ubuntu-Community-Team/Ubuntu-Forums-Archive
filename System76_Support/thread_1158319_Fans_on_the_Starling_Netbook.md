---
title: "Fans on the Starling Netbook"
date: 2009-05-13
forum: System76 Support
---

### Post by kingnerd on 2009-05-13
Hey guys, I just got a Starling netbook yesterday, and I love it.  I am planning to do a review on it on Friday, however, before I can do this review I want to clear something up.  The fans seem really loud, especially in a quiet environment, specifically, about 2/3 of the way through the linear boot-loading screen, the noise starts.  Before that, I can hear some soft fans, but it is not until then a static-like fan noise begins.  Having never owned a notebook besides the EEE PC, I am wondering if this static-like noise is normal.  If it is, I can definetely live with it, I just want to make sure that the computer is not damaged in any ways.

Besides that, I love it so far, and look forward to using it in the future.

Thanks,
KingNerd

PS - Fan volume is in comparison to a virtualy silent EEE PC, and a virtually silent iMac, so this could be perfectly normal and I would have no idea.  If it is, sorry for wasting your time.

EDIT - The device seems fairly easy to open, so if I was to go ahead and do that to see which fan or component exactly was making the noise, I could probably figure the rest out, however, does anybody know if opening the computer voids the warranty in any way?

---

### Post by thomasaaron on 2009-05-13
Just started up our Starling, and I certainly wouldn't classify it as noisy. How close do you have your ear to it?

I think the sound you are hearing, that static sound, might be the hard drive. I can hear that, but it shouldn't be constant.

---

### Post by kingnerd on 2009-05-13
I can easily hear it when it's about 2 feet from my ear and there is decent background noise.  What I can do is take include it in my video review on Friday, and post the link here so you can judge if it is normal.

So will opening the machine void the warranty?

EDIT - By the way, it's clearly the fans not the HD from the position of bootup where the noise begins as well as the fact that it's a constant noise.

---

### Post by thomasaaron on 2009-05-13
There is only one removable panel on the bottom, which does not expose the fan. Removing the whole bottom panel *would* void the warranty. It is not to meant to be accessed at the end-user level.

I just re-checked our shop Starling, and it is VERY quiet. We can't hear it from two feet away in a quiet room.

A few questions:
1. Have you downloaded any software? If so, what?
2. Can you open a terminal and run...

```
top
```

...and see what the first few processes are. That might give an indication as to what is going on.

There are some fan settings in the BIOS. I played with them, but I was unable to make the machine loud.

---

### Post by kingnerd on 2009-05-13
That is very odd....

I have downloaded and installed a few programs that I have run across many pieces of hardware / distros without an issue.  Teamspeak, WINE, and gkrellm seem to be the main ones.  In gkrellm, I cannot see the fan speed listed, nor is there a module for it.

This may lead me to believe that Ubuntu might be cranking the fans to maximum, as it does not have a driver.... I'm not sure how I would go about confirming this though,


top returns : 
```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 3137 kingnerd  20   0  326m 148m  34m R   27 15.0  38:42.71 firefox                                                         
 2514 root      20   0  304m  32m  11m R   18  3.3  14:04.72 Xorg                                                            
 9077 kingnerd  20   0 33484  13m 9288 S    4  1.4   0:00.98 gnome-terminal                                                  
 9096 kingnerd  20   0  2448 1184  912 R    1  0.1   0:00.13 top                                                             
 5947 kingnerd  20   0  101m  43m  18m S    1  4.4   1:57.64 pidgin                                                          
 3038 kingnerd  20   0 52680  29m  16m S    1  3.0   0:12.21 gnome-do                                                        
 2969 kingnerd  20   0  7580 4444 2168 S    0  0.4   0:02.40 gconfd-2                                                        
 3036 kingnerd  20   0 28648  16m  10m S    0  1.7   0:20.24 nm-applet                                                       
 3159 kingnerd  20   0 17076 5560 3988 S    0  0.5   0:30.38 gnome-screensav                                                 
    1 root      20   0  1908  780  564 S    0  0.1   0:01.71 init                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.82 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.54 ksoftirqd/1                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.58 events/0                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0                                                         
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1                                                         
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                   

```Also : lspci returns :
```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

EDIT - I see the SMBus drivers are working fine, however, I am not sure if that is how the netbook controls the fans.

---

### Post by thomasaaron on 2009-05-13
Top seems to indicate that firefox and xorg are cranking the CPU the most. However,  the only one of those that would kick in early in the boot process would be xorg.

I don't think Ubuntu cranks the fans to maximum unless it needs to, as it does not do it on a fresh install here in our shop.

Try --purge removing that software and seeing if you still have the maxed out fans.

Also, did the machine do this out of the box, before you installed the software?

---

### Post by kingnerd on 2009-05-13
> **thomasaaron said:**
> Top seems to indicate that firefox and xorg are cranking the CPU the most. However,  the only one of those that would kick in early in the boot process would be xorg.

I don't think Ubuntu cranks the fans to maximum unless it needs to, as it does not do it on a fresh install here in our shop.

Try --purge removing that software and seeing if you still have the maxed out fans.

Also, did the machine do this out of the box, before you installed the software?

I will try to purge, but I doubt it will make any difference.  I am not sure if the machine did this in the beginning, because in my initial video it was mostly off or on a carpet, and after that I used it with music or a movie playing.  The first time I noticed it was in the first quiet environment at school, after the software had been installed.  Is there any way to monitor fan usage to see if they are truly maxed out?  And does gkrellm or another monitor on the shop netbook have the fans on it?  That is what strikes me as odd, because a valid fan module should show up on gkrellm, providing the sensors are recognized, and I am inferring that they are not.  I will purge the software now, but I doubt it'll do much.

A purge and a reboot did nothing.  I am beginning to think it's X, as when the screen flashes / changes, the noise begins.  It also starts around in the boot sequence where X would start.  I am going to try to boot in runlevel 3 to test this out.

Apparently, Jaunty team did all they could to stop me from booting into 3 (init, telinit, editing grub, all work on Arch and Fedora but not Ubuntu).  I'm going to try to enable the ctrl-alt-backspace in xorg.conf and see if for the time X is off the noise persists.

---

### Post by kingnerd on 2009-05-13
Okay, X appears to be the issue, but an X reinstall did not help.

---

### Post by thomasaaron on 2009-05-14
We don't test with gkrellm, lmsensors or any other monitor software, so I'm not sure if will detect the Starling's fan. And our Starling is gone for a week, so I can't install and test them.

However, I (and one of our other techs) listened carefully to a Starling in a quiet environment yesterday, and could barely hear it at all. These types of issues (sound output and heat output in particular) are very subjective. Some people are more sensitive to them than others, and they are always a bit difficult to quantify on forum posts.

So, here is what I would suggest...

1. To eliminate the possibility of a hosed configuration causing the fan to stay maxed out, you could re-image the machine per these instructions...

[http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook) 

With a clean image, it will be as quiet as it is going to be.

2. If you still feel there is something wrong with it after re-imaging, we can bring it in and analyze it alongside of our shop machine.

You may also try disabling desktop effects to see if that quiets it down. Compiz, sweet as it is, is notorious for being buggy from time to time.

---

