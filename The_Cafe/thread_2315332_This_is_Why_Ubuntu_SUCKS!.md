---
title: "This is Why Ubuntu SUCKS!"
date: 2016-02-27
forum: The Cafe
---

### Post by hgibson1 on 2016-02-27
Two days ago my Zareason Strata 7440 Laptop began going to sleep at random times and not waking up even in response to keyboard input: it would only wake up after a restart. The hardware diagnostics in bios recovery mode said no hardware issues, so thinking something was wrong with the screen or keyboard drivers I backed up my files, wiped the HD and re installed Ubuntu 14.04 from a CD. It installed without issue but when I rebooted and tried to log on to my user I kept getting "system error" messages on a light blue screen and no desktop is loaded. I can't re install from CD because the HD is higher than CD in the boot order and there is no way to reset the boot order from the bios. I can't wipe the HD again or re install Ubuntu from a USB stick because the computer doesn't detect boot-able usbs and I can't boot from the usb manually from the grub terminal: the screen freezes or says not boot file found.   OSX is better!

---

### Post by MibunoOokami on 2016-02-27
It sounds more like user error than a problem with Ubuntu. Obviously something went wrong with your re-install and in my limited experience with Ubuntu, an error message on a blue screen doesn't sound right, perhaps it's the BSOD which belongs to Window$?

Can you not change boot options in BIOS to make it boot from USB? Or use the recovery software that came with your machine to set things straight for another attempt at installing Ubuntu.

---

### Post by CharlesA on 2016-02-27
If it is what I think it is, this should fix the problem..
[http://askubuntu.com/questions/468798/how-to-solve-system-errors-at-startup-not-just-report-them](http://askubuntu.com/questions/468798/how-to-solve-system-errors-at-startup-not-just-report-them)

Else you will need to find out what is causing the crashes in the first place.

Does a livecd/liveusb give you the same errors?

Please watch your language - it would also be a good idea to read the [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules") that you agreed to when you signed up.

---

### Post by yancek on 2016-02-27
You're posting conflicting information.  First you say you re-installed Ubuntu from a CD you booted.  I assume you meant a DVD as Ubuntu 14.04 won't fit on a CD.  If you booted the DVD and installed Ubuntu, repeat the process and set the DVD drive to first boot priority.  If you can't do that, it is unrelated to what you are trying to install but is a hardware problem with your system board.

---

### Post by CharlesA on 2016-02-27
> **yancek said:**
> You're posting conflicting information.  First you say you re-installed Ubuntu from a CD you booted.  I assume you meant a DVD as Ubuntu 14.04 won't fit on a CD.  If you booted the DVD and installed Ubuntu, repeat the process and set the DVD drive to first boot priority.  If you can't do that, it is unrelated to what you are trying to install but is a hardware problem with your system board.

In addition to what yancek said, since this laptop came with [Linux preloaded]("http://zareason.com/shop/Strata-7440.html"), it would be a good idea to contact Zareason and ask for support from them.

---

### Post by stalkingwolf on 2016-02-28
what about using the boot menu?   f8 f10 f12?

---

### Post by Geoffrey_Arndt on 2016-02-28
YAOPW . . . Yet Another One Post Wonder . . . .

---

### Post by stalkingwolf on 2016-02-29
maybe he totally borked it?

---

### Post by Geoffrey_Arndt on 2016-02-29
It helps to "save" the bios/firmware changes before exiting the setup screen(s).

---

### Post by yoshii on 2016-02-29
On my AMD computer, to get to the boot order section of the BIOS I had to enable "Legacy Mode" or something like that (BIOS mode).  I also had to disable secure boot and pretty much go around UEFI.  After that, I was able to boot into the my LiveDVD's and erase Windows with gParted, make my new partitions including SWAP and do a nice clean install.  

Maybe your system is similar and you have to do some BIOS stuff.  On the HP, you have to press ESC several times during boot to get a setup menu and then you can configure the other parts.  Google your computer's manufacturer and model to get info on the BIOS / setup keys to press during boot so you can get to the boot order.

---

### Post by user1397 on 2016-03-01
I don't really get how you can't go into your BIOS settings and change the boot order...is it greyed out or something?

---

### Post by poorguy on 2016-03-02
I have seen bios locked so tight and it wasn't from the oem builder.

Some companies lock down their laptops to where no one can enter.
Companies don't want people to be able to alter their computers.

I have an intel desktop build from a company and the only way to open the bios. 
The only is to replace the bios rom.
There is no way to crack / find the password.

Bought at an auction for a $5.00 bill. The processor is an i3 core and also has 8gb ddr3 ram sticks so it is worth a $5.00 bill.
No hard drive though.

---

### Post by QIII on 2016-03-02
I believe the drive-by shooter has sped off to parts unknown.  Let's not give this more attention.

Closed.

---

