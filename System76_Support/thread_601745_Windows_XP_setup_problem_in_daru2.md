---
title: "Windows XP setup problem in daru2"
date: 2007-11-03
forum: System76 Support
---

### Post by muzcuk on 2007-11-03
I know this is not the best place to ask this but well.. zindows doesn't have any forums, does it...?

Ok, I have a windows xp professional cd which I know to be working, I put it in,boot up,  it says "press any key to boot from cd", I do so, and it says "Windows setup is going to check out your hardware now" or something an then the screen goes black and nothing happens..

I also have a deeper problem which is the main reason I am struggling with this right now, when I try to intstall VMware, it says 

VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

why is that? 

I need some windows xp only (not even vista) applications for school and I am  totally hopeless at this point.

did anyone try to install xp on a darter and encounter something like this before..?

Damn thing doesn't even tell me what is wrong, just a black screen! That's why I switched to linux in the first place..

---

### Post by palintheus on 2007-11-04
I had to install VMWare from the download on the official site, it wouldn't work out of the repos for me either.

Not sure on the windows problem, could be the SATA drive ::shrug::

---

### Post by theologian aaron on 2007-11-04
Mine does the same exact thing with XP.  I think it may be something to do with the santa rosa hardware.  It doesn't recognize it properly, and kills the install.  there may be a patched version somewhere out there, but I don't know.  Vista (boo) does work fine though, if you want to deal with that nonsense.

VMware server works fine, but as the other fellow said, it's not in the repos.  

Maybe try using wine.  You never know, the applications may work!

Cheers, and good luck!

---

### Post by saxamo on 2007-11-06
I  can confirm what all of you are saying. Every time I try to install windows, it gives me a message saying no hard drives were found. I haven't found a way around this :(:(

---

### Post by thomasaaron on 2007-11-06
This is a common problem with XP (particularly the older disks, I think). There is a way to install, but I've not fully researched it.

The problem is that XP didn't come with a SATA driver. In order to load XP, you will need to make the SATA driver available. This thread mentions using a floppy disk to do so, but I understand that it can be done now with a USB flash drive.

Hope this helps:
[http://www.pcreview.co.uk/forums/thread-460057.php](http://www.pcreview.co.uk/forums/thread-460057.php)

Best,
Tom

---

### Post by Aug Leopold on 2007-11-06
If that isn't the problem, you might also want to make sure AHCI is disabled in the BIOS. It is enabled by default, but windows xp doesn't support it, only vista.

---

### Post by saxamo on 2007-11-07
I have been researching this issue. I tried disabling ACHI in the BIOS but the install still did not recognize my hard drive.

It is very possible to load the drives during the windows XP install, however according to the explicit FAQ [Here]("http://www.hitachigst.com/hdd/support/hddfaqs.htm") the installer specifically looks at the A: drive.

If I were to get a USB floppy drive, what exact files should I put on it? I have poked around in the driver CD provided with the laptop and am not sure which files are the SATA drivers. 

The [other ]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml") option I found involves using nLite to create a new windows XP cd with the drivers preinstalled. Running nLite under wine is not breeze. 

The only other thing I could think of is getting a USB stick to mount as A:/ But I've searched and the only things I get are how to make it bootable. And those instructions are for windows, too!!

---

### Post by tedrampart on 2007-11-08
you could also modify the windows disc image, and have it include the drivers right from the install.. 

a friend of mine did that for me, and it worked for a newer toshiba with sata drives in it.  I'm not sure how he did it, but you could try looking that up and see how to do it.

we're going to try the modified disc that I have on my friends new darter, as the normal disc doesn't work.. if it does work, I'll let you know.

EDIT - I founded a program (mind you it was a windows one ugghh, so you'll probably have to borrow a friends windows box for this) called nLite, which allows you to put drivers, service packs etc onto a new bootable image.. might be how my friend did it (sadly I can't ask him since he suffered a stroke 2 weeks ago and is in the hospital with brain damage) .. here's the blog I found for an acer with the same problem [http://komku.blogspot.com/2007/08/install-windows-xp-on-acer-aspire-4710.html](http://komku.blogspot.com/2007/08/install-windows-xp-on-acer-aspire-4710.html)

EDIT 2 - woops.. haha I guess I shoulda read the last comment before commenting myself.. oh well..

---

### Post by saxamo on 2007-11-08
Yes I have found that nLite tutorial but thanks anyway. 

I am most likley going to borrow a friend's XP box with nLite. However, I still don't know which driver files for the SATA hard drive I need off the driver CD, so if someone could help me with that, it would be greatly appreciated. I can't get them off the Hitachi website, either.

---

