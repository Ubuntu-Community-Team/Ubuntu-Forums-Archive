---
title: "Re: lxle error errno30 on laptop"
date: 2015-09-16
forum: Ubuntu/Debian BASED
---

### Post by lenny8 on 2015-09-16
Hello,

I am trying to install lxle 12.04.5 on asus eee pc laptop

I am trying to install it on a mini pci-e ssd i bought for it but i always get a ''bad dvd'' or disk error.

Before the obvious is asked i will state the following:
I tried installing this via usb, sd card, cd and dvd SAME error on all of them.

I did 5 passes of memtest and my memory comes up with NO errors, i checked the hard drive and it shows up healthy and passes.
Not only that initially i was led to believe it was actually the hard drive but i got another brand new one that the factory tested and showed me screenshots of it in perfect working condition.

I don't know why it won't let me install is frustrating to say the least because of the amount of time i spent trying to figure this mess out. I don't have a lot of options in terms of what i can pick because my laptop has a 900mhz celeron processor so i can't use newer distros and most don't even work at all. however lxle 12.04.5 works just fine when i tested it on a live usb in fact it works perfect but it just wont install in the mini pci-e hard drive.

So  obviously there is some issue going on that won't let me complete the installation i downloaded the file from sourceforge and from 3 other places , as stated i tried more than 1 dvd/cd, did the install via usb, sd card and so forth everything has the same issue.

I installed the operating system with linuxpendrive software, power iso and rufus made no difference with any of them 

help much appreciated!

Also i tried the new version of lxle for 32 bit which is 14.04.3 and it won't even boot in the laptop so my guess is i can't even use that version for my asus 701

Unless the iso is ''broken'' from all 4 places i got it then there is just something else i can't figure out , i searched online and some others had this exact issue some had faulty memory sticks and others they could never resolve.

If anyone could tell me where to get lxle besides sourceforge or has a link to an iso that they know for certain works please refer me and ill try it out but i really doubt that's the issue here.

---

### Post by howefield on 2015-09-16
Thread moved to the "*Ubuntu/Debian BASED*" forum.

You are welcome to post here but bear in mind supporting and being supported by the[ lxle]("http://www.lxle.net/forums/") forums might be a better bet.

---

### Post by lenny8 on 2015-09-16
the lxle forums do not have as much traffic as here so i was hoping someone here would be able to assist

---

### Post by Sweet_Baby_Jamie on 2015-09-16
The first few times I tried it I had burned a data disk instead of an *image* disk.  I fixed it by downloading a program called UNetbootin which burned it correctly to a thumb drive.  

I know that's probably not what you did but I may not be the only silly person to have made that mistake...

Anyway after I had it on a USB stick in a bootable form (.iso), then I had to figure out how to boot from it.  It's different from some computers to others.  On mine you have to have the USB drive plugged in before power-up, then hit the F12 key a bunch of times right after power-up to get a menu that offers "boot options" or "boot order."  I selected USB and it booted up LXLE.  

This may not answer your question but it's all I know really, and maybe it'll help someone else.

---

### Post by lenny8 on 2015-09-16
unetbootin is the same as rufus, and the other software i tried i still gave it a try it made no difference.

If i had burned the cd/dvd as a data disk i don't even think it would have booted into the live cd

---

### Post by mörgæs on 2015-09-18
Have you tried booting a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by Sweet_Baby_Jamie on 2015-09-18
I had alot of trouble getting it right for my parents' installation.  I ended up ordering a Live DVD in the mail!  You can get them from [https://www.osdisc.com/products/lxle-12045-install-live-dvd-32bit.html](https://www.osdisc.com/products/lxle-12045-install-live-dvd-32bit.html)
That's for the 12.04 edition but you can get 14.04 there too, 32 and 64-bit

---

### Post by lenny8 on 2015-09-20
Its not the dvd , or file i got as i installed it in other computer and even an sd card. 

Its an issue with the pci-e slot and the laptop  and linux in combination. 

Any here use any eee pc older models from 2009 and under? If so how is the bios updated because i can't seem to get it right

---

