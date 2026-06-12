---
title: "running ubuntu OS on usb vs ssd"
date: 2014-07-12
forum: Ubuntu, Linux and OS Chat
---

### Post by giermo on 2014-07-12
Hey guys

I'm planning on revamping my home media server. Just wanted to know people's thoughts on Running ubuntu on a ssd vs a usb key.  

The OS will be only serving smb share, plex media server and a torrent client withe the data stores being on a dedicated data hdd. So not that intensive. I would prefer to use usb as I would then also have an additional SATA port to use for another data drive. 

What are your thoughts? They are both flash lol

Thanks

Thanks

---

### Post by Bucky Ball on 2014-07-12
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Speed-wise you are talking night and day and a no-brainer, but you probably know that. If it was me, I would do a minimal install to the USB and add a lightweight desktop like xfce4 or lxde, samba, plex media server and a torrent client.

I was using a Raspberry Pi to do what you're thinking and worked beautifully. That runs off just an SD card or SD and USB (faster). USB is my vote. I wouldn't waste an SSD on such a trifling task. ;)

PS: Silly question, but we are talking SSD hard drive, not SD card?

---

### Post by 3rdalbum on 2014-07-13
I tried running an Ubuntu home server off a USB key (the files to be served were on an HDD).

The USB key died in a matter of months. I don't know whether it was just a bad key (it was a decent brand which had very good reviews) or whether Ubuntu is rough on USB keys that it has been installed to, but the experience put me off trying that again!

(the same server has been running nearly non-stop since 2009 with a little laptop HDD as the boot drive).

---

### Post by giermo on 2014-07-13
Thanks for the replies!

@Bucky ball -- Yeah i meant ssd. I have not heard of xfce4 or lxde, i presume they just have a lighter weight GUI front to make them more efficient?

@3rdalbum -- I have indeed heard of this issue with the usb being destroyed from read writes etc. This is what i don't want lol, and why i polled to see if others had success. Thanks for your input. Maybe a few others will report their experience. Did you install the OS to the USB directly as a normal install, or did you use a tool to make the OS bootable on the usb key? IE: (pendrivelinux.com)

Thanks again

---

### Post by Bucky Ball on 2014-07-13
You have to use something to create a bootable install on a USB. You can't just drop the ISO.

---

### Post by sudodus on 2014-07-13
If you want to use a USB drive, and want longer life than with a pendrive, you can ***boot from a USB hard disk drive***. USB 2 will be slower than with an internal drive, but I think it will be OK for you. If USB 3 is available, it will be quite a lot faster than USB 2 and definitely fast enough.

---

### Post by 3rdalbum on 2014-07-14
I did a normal install to the pen drive as though it was a hard disk. I'll also mention that I disabled swap space, set ext3 to "noatime" and set up some other things to prevent premature wearing down of the flash.

Within a couple of months it was becoming read only. Run an fsck manually and it would be fine for days before going ro again. Eventually the fscks failed completely. I tried erasing the flash drive on another computer but it was dead.

---

### Post by monkeybrain20122 on 2014-07-14
> **sudodus said:**
> If you want to use a USB drive, and want longer life than with a pendrive, you can ***boot from a USB hard disk drive***. USB 2 will be slower than with an internal drive, but I think it will be OK for you. If USB 3 is available, it will be quite a lot faster than USB 2 and definitely fast enough.

It is the same speed as internal hd unless you are transferring file from another usb. I have done it many times.

---

### Post by Bucky Ball on 2014-07-14
? An external USB will never be the same speed as an internal SATAII drive, unless you are using USB3, but that won't equate to SATAIII.

---

### Post by monkeybrain20122 on 2014-07-14
> **Bucky Ball said:**
> ? An external USB will never be the same speed as an internal SATAII drive, unless you are using USB3, but that won't equate to SATAIII.

For an external hd is the same, at least I can't tell the difference (except for booting up and transferring files from another external device) You can test it out yourself if you don't believe me. :)

---

### Post by kurt18947 on 2014-07-14
> **3rdalbum said:**
> I did a normal install to the pen drive as though it was a hard disk. I'll also mention that I disabled swap space, set ext3 to "noatime" and set up some other things to prevent premature wearing down of the flash.

Within a couple of months it was becoming read only. Run an fsck manually and it would be fine for days before going ro again. Eventually the fscks failed completely. I tried erasing the flash drive on another computer but it was dead.

A few months seems about right to me. From [http://searchsolidstatestorage.techtarget.com/definition/TLC-flash-triple-level-cell-flash:](http://searchsolidstatestorage.techtarget.com/definition/TLC-flash-triple-level-cell-flash:)[INDENT]
TLC flash will also have lower write endurance than both SLC and MLC flash. Generally, the more bits of data the cell has, the fewer write cycles it will support. SLC memory cells can withstand up to 100,000 write cycles before failing. A 2-bit MLC memory cell can typically withstand up to 10,000 write cycles before failing. A TLC memory cell can sustain about 1,000 write cycles before failing, which is why thus far it has been limited to consumer-grade applications.
[/INDENT]

As I understand it, new relatively inexpensive SSDs use TLC flash but over-provision the amount of memory.  For instance a 128 GB. drive might contain 150GB (or some such number) of storage . The controller mechanism is clever enough to recognize when a cell is close to failing and will lock that one out and tap one of the unused cells as a replacement. I guess TLC flash is enough cheaper than more durable forms that it's cost effective to over-provision TLC rather than using a SLC or MLC flash. The li'l flash drives are not so clever.

---

### Post by giermo on 2014-07-14
hmmmm, perhaps i could use a usb header on the motherboard, but i think that would still leave me bottle necked for speed.
Perhaps best bet would be to keep the boot on a sata disk and have the torrents go to a usb drive, keeping my other sata drives free for formatted / clean data.

---

### Post by thinkingbeyondthesquare on 2014-07-21
> **giermo said:**
> Hey guys

I'm planning on revamping my home media server. Just wanted to know people's thoughts on Running ubuntu on a ssd vs a usb key.  

The OS will be only serving smb share, plex media server and a torrent client withe the data stores being on a dedicated data hdd. So not that intensive. I would prefer to use usb as I would then also have an additional SATA port to use for another data drive. 

What are your thoughts? They are both flash lol

Thanks

Thanks


SSD is a type of hard drive, a usb stick/key is a storage technology not made for high number of data access. An SSD should last 10+ years under normal use, a usb thumb drive will likely die within 1 to 4 months.

Why not install Ubuntu + swap partition on the media server hard disk? Afterall a media server is on 24/7 and so you dont need a quick start for it (that an SSD would bring). 

Thumbdrives are fun to show how flixible linux is when doing a demo etc, but I wouldnt even think of using such a beast for regular/mission critical funtions. A usb connected SSD is a different matter - but then you are limited to the USB speed which, unless its USB3, is no faster than a SATA III hard disk.

So if it was me just back up your media server disk, shrink a partition (if you can) create a 60gb Linux parition, 8gb for swap drive (Or whatever size you memory is - reflect that in you swap pration size.) and install. That way if you ever need to upgrade the OS by doing a 'start from scratch' install you just need to nuke the 60gb OS - linux partition.

Saves money on getting a new drive too. ;)

---

### Post by mastablasta on 2014-07-21
I was just checking the HP microserver. It has a internal USB plug where you can attach a usb stick and run the server off it. 

I don't think the USB would be under too much stress in such case. I mean once you boot the system is loaded into ram, right? well mostly at least. then mostly logs and such would be written in / and you could write those onto hard disk along with other data. every now and then USB stick would get some additional data. but that is not too much reads and rewrites.

unless you are constantly doing something on it.

similar goes for media server. usually it is not in constant use and if you put the server stuff on USB and the data on hard drive it shouldn't overload it too much I think. I have OpenElec on rapsberiPi on noobs microSD card. it's been mostly on for the last 8 months. so far the PSU failed. but the card seems fine. the only data that is on card is system and media fan art data (which I am sorry I didn't set to be written on USB hard disk and I might change it later on). the media data itself is on USB hard disk and it is mostly that which get's reads and writes. and mostly an hour or two a day. maybe more during weekend and less during week.

---

### Post by giermo on 2014-07-21
Thanks guys for all the input.

I was thinking the ssd not to increase boot speed, as a more useful method of speeding up the computer in general, vs upgrading the systems ram etc. 
Ram is not as useful after a system gets old(so many form factors), vs a ssd which could be re-used a lot easier :)

---

