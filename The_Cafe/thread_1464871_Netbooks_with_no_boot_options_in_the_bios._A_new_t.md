---
title: "Netbooks with no boot options in the bios. A new threat for us?"
date: 2010-04-28
forum: The Cafe
---

### Post by JC Cheloven on 2010-04-28
Hi, I'm really worried:

I had at hand a Samsung N-150 notebook, and of course tried to test ubuntu on it. 
To my surprise, the boot section of the bios only had a few stupid options (about what you'd like to see at startup and such), bun no options as to where to boot from. 
So I was unable to boot ubuntu from pendrive. In fact I don't figure out how I could boot/install anything else than the branded OS (w7 starter).

If this is made on purpose by the manufacturer, it would be a real problem for FOSS.
Anyone else has found a similar problem? 

JC
_______________________

---

### Post by madjr on 2010-04-28
try

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by alket on 2010-04-28
1.Install Ubuntu via WUBI
2.Go to Ubuntu and install GRUB
3.Erase the Windows partition

---

### Post by madjr on 2010-04-28
> **babaroga said:**
> 1.Install Ubuntu via WUBI
2.Go to Ubuntu and install GRUB
3.Erase the Windows partition

what lol

---

### Post by CharlesA on 2010-04-28
If it's the kind of BIOS I am thinking of, does it let you stick the USB in and select it under "hard drive" ?

Also, what size of thumb drive are you using?

---

### Post by ttshivers on 2010-04-28
> **JC Cheloven said:**
> Hi, I'm really worried:
 
I had at hand a Samsung N-150 notebook, and of course tried to test ubuntu on it. 
To my surprise, the boot section of the bios only had a few stupid options (about what you'd like to see at startup and such), bun no options as to where to boot from. 
So I was unable to boot ubuntu from pendrive. In fact I don't figure out how I could boot/install anything else than the branded OS (w7 starter).
 
If this is made on purpose by the manufacturer, it would be a real problem for FOSS.
Anyone else has found a similar problem? 
 
JC
_______________________
 
Yikes.  I hope the stop doing that.

---

### Post by Lightstar on 2010-04-28
Yeah, like someone above said, check your hard drives in the bios, some usb flash drives will appear there.

While you can't choose "boot from usb".. if it appears as a hard drive, you can put the USB flash drive as primary hard drive boot.

---

### Post by Crunchy the Headcrab on 2010-04-28
I'm gonna go ahead and third the check under hard drives option.  There has to be a way to install from a physical medium or else your pc would be bricked if you messed Windows up.

---

### Post by Chronon on 2010-04-28
I have seen other people mention success with booting from an SD card in the card reader.

Do you get a boot menu if you press F2 while booting?
I got this idea from a comment here:
[http://www.groupsrv.com/linux/about159692.html](http://www.groupsrv.com/linux/about159692.html)

---

### Post by CharlesA on 2010-04-28
I'd probably just connect a USB dvd drive and install from there, if it wouldn't take a usb key.

---

### Post by JC Cheloven on 2010-04-28
> **babaroga said:**
> 1.Install Ubuntu via WUBI
2.Go to Ubuntu and install GRUB
3.Erase the Windows partition
Is that for serious? I din't use wubi, but afaiu it installs ubuntu as a program in the win2 partition. Erasing that, will not erase ubuntu as well? 

Thank you for all answers, I'll check out wheter the usb appears as a hard drive or not (and try to set it as boot device if applicable).
@CharlesA: It's a 2Gb pendrive. I used it to install in a number of machines.

Despite possible workarounds, I dislike the way they are making harder to install a different OS. I wonder if the change is because "they" are worried about Chrome...

---

### Post by chris4585 on 2010-04-28
> **babaroga said:**
> 1.Install Ubuntu via WUBI
2.Go to Ubuntu and install GRUB
3.Erase the Windows partition

That would erase Ubuntu since wubi installs Ubuntu on the windows partition.  Unless wubi has had some radical changes.

---

### Post by marshmallow1304 on 2010-04-28
> **babaroga said:**
> 1.Install Ubuntu via WUBI
2.Go to Ubuntu and install GRUB
3.Erase the Windows partition

Wubi doesn't create a separate partition, so that won't work.

---

### Post by CharlesA on 2010-04-28
> **JC Cheloven said:**
> 
@CharlesA: It's a 2Gb pendrive. I used it to install in a number of machines.

Yah, that should be fine then. It wasn't listed under hard drives right?

---

### Post by JC Cheloven on 2010-04-28
> **CharlesA said:**
> I'd probably just connector a USB dvd drive and install from there, if it wouldn't take a usb key.
Thanks for your new post. Just to make it clearer:
In the boot menu, I find no options to boot from anything, to my surprise. I downloaded the manual of the netbook (a .exe, pfft... wine deals with it)
[http://printer1.blogspot.com/2010/03/samsung-n150-user-manual.html](http://printer1.blogspot.com/2010/03/samsung-n150-user-manual.html)
and it's supposed to appear "boot from usb", even if no usb is found (a "NA" for "not applicable" should be shown in that case). But again, in my bios this not even appear.

EDIT: ha ha, posted while you did :-)  I haven't the netbook at hand right now (it's not mine). Will try asap if the usb is listed under hard drives. I didn't figure out that bit when I tested it.

---

### Post by CharlesA on 2010-04-28
Ah ok. Please post back when you are able to find out.

Who the hell puts a manual in an exe? (Samsung apparently) Sheesh!

---

### Post by magmon on 2010-04-28
Where it me, I'd set up wubi, partition the HD in windows, move wubi to the new partition, kill the windows section and expand the new linux partition, and laugh at the manufacturer.

Edit- Read some other posts. I'll try and dig up the tutorial that showed me how to move wubi to a partition and post it here. Keep in mind that this process is a major pain in the anus.

---

### Post by lykwydchykyn on 2010-04-28
I wonder if this would work:
[http://www.goodbye-windows.com/](http://www.goodbye-windows.com/)

---

### Post by magmon on 2010-04-28
[Found it.]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by wilee-nilee on 2010-04-28
Personally I never change the boot order I just make sure the f12 option to choose the boot is enabled. Here is a link that describes install arch to this very computer, look closer at the f12 option.
[http://wiki.archlinux.org/index.php/Samsung_N150](http://wiki.archlinux.org/index.php/Samsung_N150)
I suspect that this is a user error in understanding. Not pointing any fingers here but a modern computer not being able to choose a boot option is well, ridiculous and I suspect not the case with this model.

So stick that formatted USB in the slot make sure you have f12 or what ever key that computer needs to see the boot choice menu choose the listed USb and install.

---

### Post by JimTaverna on 2010-04-28
Slap the flash drive in a port, reset, enter BIOS, check Boot Sequence options. Not there. Rinse and repeat until you run out, of ports or patience.

Some BIOSs have a static Boot Sequence setup whereas others are dynamic. Yours isn't the former, unless it's modded for lock out, your port(s) dead or both. Either way, in that case, you're SOOL. 

If it's dynamic, the drive needs to be detected before it will ascend to the setup throne, meaning it has to be inserted into a port before the boot sequence begins. The first paragraph would have determined that.

Then again, you could have just hit all the obvious keys (esc, F1, F2, F8, F9, F10, F12) or my preferred way of any and all as fast as I can and hope for the best, that being the Boot Selection menu sans BIOS runaround.

My guess is it's not modded, since no one seems to be b*tching about it online and sooner or later you'll strike gold or better yet the correct key.

Oh, oh. Forgot one thing. All bets are off if you got it via a 2 (years) for 1 (laptop) scam that seems to be popular with the telcoms and Comcast. Uses a branded BIOS and only God and Sen. Orin Hatch knows what's in it.

---

### Post by NormanFLinux on 2010-04-29
Stupid manufacturers. You can install PLOP Linux and have a USB flash drive set to boot as another hard drive.  It ain't rocket science!

---

### Post by clanky on 2010-04-30
> **magmon said:**
> Where it me, I'd set up wubi, partition the HD in windows, move wubi to the new partition, kill the windows section and expand the new linux partition, and laugh at the manufacturer.

Edit- Read some other posts. I'll try and dig up the tutorial that showed me how to move wubi to a partition and post it here. Keep in mind that this process is a major pain in the anus.

> **JC Cheloven said:**
>  I haven't the netbook at hand right now (it's not mine).

I don't think whoever the netbook belongs to would be too impressed with that solution.

---

