---
title: "Low resolition in xp in virtualbox"
date: 2009-05-22
forum: Virtualisation
---

### Post by kentpend on 2009-05-22
I used to be able to get 1280x800 resolution in virtualbox, and then one day my higher resolutions disappeared.  After reinstalling virtualbox and guest additions, the problem is persisting.  I can get no higher than 1024x768.  Any ideas?

(Host is 8.10)

---

### Post by roman_platonov on 2009-05-24
video ram setting?

---

### Post by kentpend on 2009-05-24
I've tried both 8Mb and 128Mb.  No difference at all.

---

### Post by roman_platonov on 2009-05-25
ok. in that case you need to reset you monitor and video driver in XP.
try 1
deinstall virtual box guest additions.
reboot
install vbox adds 

if not solved
try 2
deinstall virtual box guest additions.
reboot
second reboot  xp in SAFE mode (it's important)
go to the hw manager
remove all devices looks like videocards & monitor.
reboot in normal mode
install vbox additionals.

i hope this help.

if even that don't help, than try to install monitor driver - standart digital panel (1280*1024) this will help to change the limit.

---

### Post by kentpend on 2009-05-26
Thanks for the help... but when I booted it up today it had magically fixed itself.

Now on to solving the problem of my machine freezing on shut down...

---

### Post by gakon77 on 2011-06-07
Hi.

Here there is the same problem that originated this thread. My resolution after installing "guest additions" has decreased to 800X600 and it doesn't allow to make it better.

I've tried the second option suggested without any improvement. The first I haven't because I don't understand how to install vbox adds.

Do you think can explain how to install vbox adds?

Anyway it may solve itself or eventually I will find the solution.

Thanks.

> **roman_platonov said:**
> ok. in that case you need to reset you monitor and video driver in XP.
try 1
deinstall virtual box guest additions.
reboot
install vbox adds 

if not solved
try 2
deinstall virtual box guest additions.
reboot
second reboot  xp in SAFE mode (it's important)
go to the hw manager
remove all devices looks like videocards & monitor.
reboot in normal mode
install vbox additionals.

i hope this help.

if even that don't help, than try to install monitor driver - standart digital panel (1280*1024) this will help to change the limit.

---

### Post by CharlesA on 2011-06-07
I have never had to boot into safe mode to install the guest additions. You should be able to install them from the devices menu after the VM is running.

---

### Post by gakon77 on 2011-06-08
The problem seems sorted.
 
After removing all video drivers in safe mode and reinstalling Guest Additions in safe mode as well (to enable 3D graphics, as it says in the manual).

I checked the video drivers and it turned up that there was to drivers, one the virtual box and other for the standard monitor.

After disabling the virtual box driver the screen resolution improved and now allows me to change it.

To be honest I really don't know what solve the problem, but I suspect that the virtual box driver in the Guest Additions was the cause.

Cheers!!!

---

### Post by linuxmaniack on 2011-06-08
tried vbox guest editions? that did the trick for me! (evan though im using 1920x1080, it does has your res on there!) 

to do it, go to (when vbox open) go to Devices, then install guest editions. or host+d (host on my pc is right ctrl... mabey on your too)?ellio

---

### Post by asoares on 2011-06-08
I'm having low graphic issues!

Host: Ubuntu Natty
Virtualbox 4: Windows 7 with VB Extension Package installed

Up until a couple hours ago everything in VB worked great! Now, Natty is working great but VB is loading low resolution or garbled graphics. I don't know what happened but I seriously need this solved. 

I've tried enabling 3D and 2D in the Display area of the Vb Settings and that doesn't work. I never had it enabled before neither.

Any suggestions??

Thanks
Aaron

---

### Post by asoares on 2011-06-08
I booted VB (Win 7) in Safe Mode and the graphics are perfect!
So now how do I fix it to work in Normal Mode?

---

### Post by asoares on 2011-06-08
Hey I got it fixed!

I loaded VB (Win 7) normally and adjusted the screen resolution to 800x600 true color 32 bit and applied it as the display I want to use. Then I closed those screens and hit CTRL+F and the screen went to full size and now everything is working great! I suspect the guest extension got corrupted somehow.

Cheers!

---

### Post by gakon77 on 2011-06-09
> **asoares said:**
>  I suspect the guest extension got corrupted somehow.



Yes, I think the same. May be it is worth to report it as a bug. Do you know how to do that?

---

