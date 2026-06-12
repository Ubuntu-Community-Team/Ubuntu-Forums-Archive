---
title: "file system error on boot"
date: 2014-08-09
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2014-08-09
So, I have been happily using xubuntu 14.10 live for some weeks now and since alpha2 got released I decided it was time to dd the usb pen again....

 Xubuntu 14.10 a2 doesn't boot, it gives some kind of file system error... no errors on my part, did everything right.

 I figured I would just have to wait a couple of days till they would fix it so I changed to ubuntu mate, 2 days ago I decided to try xubuntu again... same exact error

 are people aware of this?

---

### Post by kc1di on 2014-08-09
you should file a bug report if you feel it's a bug, most of the developers don't have time to look here in the forums. But they do pay attention to the bug reports on launchpad. 

Good Luck.

---

### Post by grahammechanical on 2014-08-09
Here is a similar thread. Might be related. Might not be.

[http://ubuntuforums.org/showthread.php?t=2237818](http://ubuntuforums.org/showthread.php?t=2237818)

[http://ubuntuforums.org/showthread.php?t=2237535](http://ubuntuforums.org/showthread.php?t=2237535)

There have been times in past development cycles when I have not been able to install from a daily image either due to the live session not loading or something wrong with the installer. Once, the only time I could get a live session to run was to select all of the F6 options. Another time I had to add irqpoll as a boot parameter. This is a fine opportunity to learn about alternative boot options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by ventrical on 2014-08-09
I just downloaded the 14.10 xubuntu.iso about two hours ago and it works just great on an old Dual core non exotic system.

Regards..


[https://www.youtube.com/watch?v=hojB2c4CSmU&feature=youtu.be](https://www.youtube.com/watch?v=hojB2c4CSmU&feature=youtu.be)

---

### Post by syntaxerror74 on 2014-08-11
> **nomenkultur said:**
> 
 Xubuntu 14.10 a2 doesn't boot, it gives some kind of file system error...

Lubuntu here, but maybe we two got the same problem?

I finally had to go back to 3.13 kernel, since all I saw was a black screen, in 100% of times. Everything running smooth as silk since then. Literally. - So just downgrade the kernel you're booting from (or adapt grub config accordingly, or press and hold SHIFT during bootup to enter grub menu) and report back whether it worked or not.
And please be so kind to post your log file, since "file system error" can mean a lot of things, e. g. even something that can be cured by *fsck*.

---

### Post by ventrical on 2014-08-23
xubuntu-amd64 Aug 22 daily live working fine .

---

### Post by nomenkultur on 2014-08-29
am I the only one unable to boot xubuntu?


I have tried with beta1 released yesterday, created the live usb using both dd command line and with pendrivelinux windows program 

 it refuses to boot with either method, complains about c32 something with pendrivelinux and with dd it blinks the underscore and goes nowhere...

---

### Post by Elfy on 2014-08-29
no - that's a known issue

I've seen people manage to get a ubuntu usb creator usb to work by typing live, I use unetbootin - had the same issue yesterday - I needed unetbootindefault

Boot it - then when you get the error - hit tab and see what options it gives you 

had the same problem with dd as you yesterday too

---

### Post by VMC on 2014-08-29
> **nomenkultur said:**
> So, I have been happily using xubuntu 14.10 live for some weeks now and since alpha2 got released I decided it was time to dd the usb pen again....

 Xubuntu 14.10 a2 doesn't boot, it gives some kind of file system error... no errors on my part, did everything right.

 I figured I would just have to wait a couple of days till they would fix it so I changed to ubuntu mate, 2 days ago I decided to try xubuntu again... same exact error

 are people aware of this?

If you open that usb flash, doesn the structure appear correct?

---

### Post by nomenkultur on 2014-08-31
Neither method works, tab key or 'live' .... it's simply a blinking underscore on the top left of the screen and hitting any key results in an audible error beep.


 The structure appears correct, both DD and pendrivelinux get completed without reporting any errors, the usb pen is working fine .... I fail to see how the xubuntu people can be at this sad state of affairs in beta1, it's unusable this is no minor bug.

---

### Post by Elfy on 2014-09-01
> **nomenkultur said:**
> Neither method works, tab key or 'live' .... it's simply a blinking underscore on the top left of the screen and hitting any key results in an audible error beep.


 The structure appears correct, both DD and pendrivelinux get completed without reporting any errors, the usb pen is working fine .... I fail to see how the xubuntu people can be at this sad state of affairs in beta1, it's unusable this is no minor bug.

Well - it's not everyone is it - I can boot fine - but I don't use pendrivelinux;)

Where's your bug report number?

---

### Post by nomenkultur on 2014-09-01
if you could share your method to 'burn' the usb it would be helpful... the 3 that I've tried all fail to produce a bootable system, even dd that never failed to do so before

---

### Post by Elfy on 2014-09-01
As I said, I've got the same issue with dd as you. 

I have successfully(ish) used unetbootin - if I let the boot run then I get a menu, if I do F12 for a boot menu and choose the usb I have to tab at the boot: and use unetbooindefault - that boots straight to desktop.

---

### Post by nomenkultur on 2014-09-03
that's strange since I was udner the impression both pendrive and unetbootin used the same method (dd.exe) to create the usb...

 I'll try burning with unetbootin in windows and see how it goes

---

