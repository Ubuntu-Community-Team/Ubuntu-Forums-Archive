---
title: "TASCAM us-144 and jaunty jackalope"
date: 2009-06-03
forum: Ubuntu Studio
---

### Post by tascamuser on 2009-06-03
Hi
I'm new to ubunto but have some unix experience - very rusty though.  I understand that the tascam us144 is now supported but have not been able to get it to work.
I have just installed a fresh release of ubunto and need some hand holding.  At this point aplay -l does not reveal the tascam.  It is on the usb though.
$ lsusb
Bus 002 Device 002: ID 0644:800f TEAC Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63fa Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I don't know where to start.  HELP!

Thanks

---

### Post by tascamuser on 2009-06-04
:ks

---

### Post by PurpleSkyz on 2009-06-16
Same problem.

---

### Post by fergrorke on 2009-06-16
I'm also looking for the solution to this. Although the 2.6.28 kernel support the US-122L, which is supposed to be a work-alike of the US-144, Alsa doesn't want to know about the 144. So, how to spoof Alsa into thinking the 144 is a 122L?

---

### Post by keithacole on 2009-06-17
i've had the us-144 for about 8 months now. and i still dont have it working, i even have a modified fedora that is supposed to work, but not having any luck.

---

### Post by keithacole on 2009-06-24
i am going to try install the newest version of alsa from source.

my current version is

```
sudo apt-cache showpkg alsa
Package: alsa
Versions: 

Reverse Depends: 
Dependencies: 
Provides: 
Reverse Provides: 
alsa-base 1.0.18.dfsg-1ubuntu8

```

on [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) they are showing 1.0.2

ive have followed every step on this [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux) in the past with no luck. thats why i tried with fedora because thats what the developer used. there is also a .deb there to try, i didnt have luck with it. but i tried all this stuff "Hardy Heron" with no luck. i updated my studio to 9.04 last week, which made some things much more stable, like my dm2 in mixxx but still no luck with my main audio interface the US-144


btw the US-144 is not like the 122 they are different enough for US-122 drivers not to work.

---

### Post by EliasKesh on 2009-07-18
I have been working on this now and downloaded the daily alsa-drivers (alsa-driver-20090718.tar.gz) . The 122l is support so I added the US144 to the ./alsa-kernel/usb/usx2y/us122l.c . Now I am getting kernel various memory failures when I plug the device in . 

Has anyone managed to get this working ?

Karamic
2.6.31-rc3 

Thanks,
Elias

---

### Post by Jonatello on 2011-06-13
has anyone had any luck getting this working?

---

### Post by wbm on 2011-06-14
Option 1:
Shutdown computer
Unplug Tascam USB device
Reboot and log in
Plug Tascam USB device back in and see if it is now detected
If not, unplug and replug in one more time for good measure while logged in.

Option 2:
Maybe you don't have all needed software yet.
In Synaptic search for Tascam.
It should list 3 Alsa items related to Tascam hardware.
Install those.
Unplug Tascam USB device
Reboot
When logged in plug Tascam USB device back in.

The key in all this is that you must plug the device in while logged in after you have all drivers installed.
On KDE you get to do that after each reboot :)

I have the Tascam US122 and what I just described may not help you at all, but it is worth a try. Good luck!

---

### Post by Jonatello on 2011-06-18
> **wbm said:**
> Option 1:
Shutdown computer
Unplug Tascam USB device
Reboot and log in
Plug Tascam USB device back in and see if it is now detected
If not, unplug and replug in one more time for good measure while logged in.

Option 2:
Maybe you don't have all needed software yet.
In Synaptic search for Tascam.
It should list 3 Alsa items related to Tascam hardware.
Install those.
Unplug Tascam USB device
Reboot
When logged in plug Tascam USB device back in.

The key in all this is that you must plug the device in while logged in after you have all drivers installed.
On KDE you get to do that after each reboot :)

I have the Tascam US122 and what I just described may not help you at all, but it is worth a try. Good luck!

still didn't work for my 144. you said this is all you had to do for the 122?

---

### Post by wbm on 2011-06-18
> **Jonatello said:**
> still didn't work for my 144. you said this is all you had to do for the 122?
Yes, that was all to get it to be recognised (the 3 lights came on, one stayed on), and it showed up in the various sound preferences, control panels and software.
You still need to tell the OS to use the interface of course. What I described was to get it powered and recognised.
Usually then you would go into the sound control preferences and select it as your output device and input device (gnome), or into System Settings Multimedia (KDE)

---

### Post by Jonatello on 2011-06-18
> **wbm said:**
> Yes, that was all to get it to be recognised (the 3 lights came on, one stayed on), and it showed up in the various sound preferences, control panels and software.
You still need to tell the OS to use the interface of course. What I described was to get it powered and recognised.
Usually then you would go into the sound control preferences and select it as your output device and input device (gnome), or into System Settings Multimedia (KDE)

wow that's pretty good. mine is a us-144 mkii, and unfortunately, the above process doesn't seem to work. the lights come on, but nothing seems to be recognized by the computer. it does not show up as an option when choosing input device, etc. 

:(

---

### Post by wbm on 2011-06-21
> **Jonatello said:**
> wow that's pretty good. mine is a us-144 mkii, and unfortunately, the above process doesn't seem to work. the lights come on, but nothing seems to be recognized by the computer. it does not show up as an option when choosing input device, etc. 

:(

I read on the Ardour forums that "pretty much all USB 1 devices work", and that "pretty much no USB 2 devices work"; with some lengthy explanation about all that. Maybe it's not the device but the fact that it is USB 2?
Mine is a USB 1 device.

---

### Post by wergelt on 2011-06-23
the fine print on the alsa web site 

[http://www.alsa-project.org/main/index.php/Matrix:Module-usb-us122l](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-us122l)

says

**Limitations for the US-144**

 The US-144 works with kernel 2.6.33 and above, but only when uhci-hcd  (USB 1.1) is forced. This can be done by using an USB 1.1 only USB hub  or by disabling ehci-hcd (USB 2.0). The US-144 will run as an US-122L,  so the digital channels won't work. 





so maybe plugged into a cheap 1.1 hub

---

### Post by crispyrich on 2011-09-12
> **Jonatello said:**
> still didn't work for my 144. you said this is all you had to do for the 122?

fed up with ubuntu  audio is rubbish  scanners wont work midi is hopeless  how long have people been trying to get certain usb audio cards working, if canonical gave a s**t it would have been sorted ages ago, seems to me they are just like any other corporation  will stay with xp as i am not a computer hacker and am happy with tascam us144 see ya

---

### Post by jejeman on 2011-09-12
> if canonical gave a s**t it would have been sorted ages ago,If companies that make hardware give s**t about Linux, it would have been sorted ages ago. ;)
Canonical has nothing to do with it. Ubuntu is not the only linux distribution on the world. Hardware have to work on every linux distribution, and only companies that make hardware can make that happen. Just like they make it happen for windows. 
But, that's old news.

---

### Post by wbm on 2011-09-12
The Tascam 122 is USB 1, the Tascam 144 is USB 2

USB 1 is supported out of the box

USB 2 is NOT supported

I suggest you either get on eBay a Tascam US 122. They sell for anywhere $15 - $50, or get a Firewire device.
My Tascam US122 eventually died. I got from eBay both a "new" used US 122 and an Edirol FA-66 firewire device. Both work by just plugging them in. I paid $12 for the Tascam and $105 for the FA-66.

If you want to do mainly audio recording and not computer tinkering get a Mac.
Audio on Linux is half making music and half messing with Linux all the time.
But hey, it's free, as in around $2000 cheaper than a Mac with Logic etc.

---

