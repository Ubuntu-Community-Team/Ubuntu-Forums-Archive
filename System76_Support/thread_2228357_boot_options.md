---
title: "boot options"
date: 2014-06-06
forum: System76 Support
---

### Post by JohnDillinger43 on 2014-06-06
I'm trying to set up my Gazelle Pro to dual boot Ubuntu and openSUSE, so I have a USB drive that I'm trying to boot from.  The problem is that the boot options don't have the usual names like CD-ROM, USB, etc.  Instead it looks like they're labeled with the manufacturer.  I have one that contains "HD" that's obviously the hard drive, but the other read "Staples 1.14", "REALTEK" followed by what look like a model number, and one other that I can't remember at the moment.  Anyone know which is USB?  I was thinking it would be the RealTek, but that one just boots up normally.

---

### Post by sudodus on 2014-06-07
Try them one after another, they are not too many for simple trial and error :-)

If that does not help you, try according to this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

Some pendrives are better booters, some are worse (the hardware). It is also important to create the pendrive with a good tool. You find many tips about those things if you browse the whole web page of the link above.

---

### Post by varunendra on 2014-06-07
Monitoring 'lsusb' output in Ubuntu can also tell you the name of the USB drive. Usually these devices appear with the same name in the boot options as in lsusb (well.. only part of its output).

---

### Post by JohnDillinger43 on 2014-07-24
I tried each of the options in turn, but none of them booted from USB.  I'm trying to figure out which one is supposed to be the correct one to do some troubleshooting.  I've done a lot of booting from USB on other computer and never had an issue, but for some reason I have yet to get it to work with my System76 laptop.

lsusb doesn't give me anything with a name resembling any of the boot options -- am I missing something?

I used UNetbootin, which I've used successfully many times in the past, but maybe I'll try wiping the drive again and reinstall.  I've already done it twice, but maybe third time's the charm.

---

### Post by sudodus on 2014-07-25
If your USB drive as it is now (made with Unetbootin) is booting other computers, it *should* boot the Gazelle too. If it doesn't, I don't think it is Unetbootin's fault.

If your USB drive as it is now (made with Unetbootin) does not boot other computers, try [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") to flash the iso file to the USB drive.

Some USB drives do not boot some motherboards, while other USB drives will be happy booting that motherboard. So it is worthwhile trying another one or try chainloading. Maybe you can borrow a pendrive or get one that is known as a good booter. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL][URL="http://ubuntuforums.org/showthread.php?t=2196858"]
[/URL]
Edit: In order to identify the manufacturer and model identification string of all mass storage devices including those connected via USB, you can run this command, which is used by [mkusb8-rc2]("http://ubuntuforums.org/showthread.php?t=1958073")

```
ls -l /dev/disk/by-id| grep [a-z]$|cut -d ' ' -f 10,12|sort -k2|grep -e \^a -e \^u|sed 's#../..#/dev#'
```

---

### Post by monocell on 2014-07-25
I had problems booting from a USB drive by setting boot priorities. It worked better for me to use the one time boot menu. Worth a try if you are currently changing priorities.

---

