---
title: "average joe observations"
date: 2011-10-29
forum: Testimonials &amp; Experiences
---

### Post by landsw on 2011-10-29
I'm new to Linux (3 days). Bought an Asus netbook and started messing around with distros because, well, I'm new to Linux. And Windows was dog slow on this thing so it had to go.

Ubuntu
Peppermint OS
Joli OS
Lubuntu
EasyPeasy 
Mint

A few quick observations. 

Lubuntu and Peppermint say they're easy and quick and for average joe. They're both easy and quick but when average joe goes to date and time settings cause he wants to change from 24 hour to 12 hour he's faced with %R. What does that even mean? So I look it up and I have to change it to %X to get a 12 hour clock. Ubuntu and EasyPeasy have radio buttons that you click to choose. This is not average joe friendly.
Mint? Another series of %...

Ubuntu has trackpad options that allow two finger scrolling and vertical scrolling that just work. Lubuntu has acceleration, sensitivity and left handed options and that's it. No two finger scrolling, no horizontal. If Lubuntu is in the official Ubuntu family why is something so basic missing?

None of the ones I tried will apparently format a USB drive. Device is busy. So I look that up too and a bunch of command line stuff that may or may not work. I take them to my Mac and format them as fat32 and try again. Device is busy. I take them to my very old Windows laptop and format them and try again. Device is busy. This is not average joe friendly.

So 3 things that I think should have worked out of the box.

---

### Post by TeoBigusGeekus on 2011-10-29
You can't format a device if it's mounted. You have to go to your windows manager (nautilus, thunar, etc) and unmount it first.
Lubuntu isn't supposed to be user friendly; it's supposed to be lighter compared to the other versions of the ubuntu family.
In the name of this lightness, it lacks some features.

---

### Post by cogier on 2011-10-29
Try Ubuntu 10.04 LTS. This is available [here]("http://www.ubuntu.com/download/ubuntu/download") Just use the dropdown box to change 11.10 to 10.04.

---

### Post by roger_1960 on 2011-10-29
Hi

Sounds like you are trying to format a mounted USB drive.  In the file manager, right click it, unmount it, then try and format it.

---

### Post by HermanAB on 2011-10-29
Regarding the USB thingummajigs:
The Ubuntu desktop system automatically 'mounts' them when you plug them in.  This happens if the device has a valid file system and therefore doesn't need to be formatted.

If you wish to format a perfectly well formatted device again, then you first need to to unmount it.

Yes, it is not obvious to the uninitiated, but it isn't bad behaviour either.  If the devices were not auto-mounted when you plugged them in, then you would have complained much more!

---

### Post by nothingspecial on 2011-10-29
Moved to Testimonials.

---

### Post by landsw on 2011-10-29
Just to clarify, the device is busy popped up because I was trying to use unetbootin to make USB bootable distro's. To use unetbootin do I have to unmount it first?

---

### Post by landsw on 2011-10-29
"Lubuntu isn't supposed to be user friendly;"

from the Lubuntu page: "Lubuntu is targeted at "normal" PC and laptop users running on low-spec hardware. Such users may not know how to use command line tools, and in most cases they just don't have enough resources for all the bells and whistles of the "full-featured" mainstream distributions"

sounds like supposed to be user friendly to me!

:)

---

### Post by gandaran on 2011-10-29
> **landsw said:**
> Just to clarify, the device is busy popped up because I was trying to use unetbootin to make USB bootable distro's. To use unetbootin do I have to unmount it first?
no, and you don't have to format the usb device if it's already in fat32 format, just delete any files it contains then use unetbootin
for formatting the device install gparted, using gparted you can unmount the device to begin the format process

---

### Post by TLARbb on 2011-10-29
Notice the words "they just don't have enough resources for all the bells and whistles of the "full-featured" mainstream distributions". That's the stuff that makes for enhanced "user friendliness". So, Lubuntu won't have some things as automated as you are used to seeing in Windows environment. 
 
I am using "kubuntu" and "Linux Mint".  Of the two, I am liking Mint by just a wee bit.  Both of those distributions have run on my machines without any difficulties.  I am new again to Linux and have a lot of "education" to complete before I am even a good user.  
 
Not sure how old your ASUS netbook is, or its specs, but it should run fine on several distributions.  Drop over to the Mint website and you should be able to get some more experienced advice.  
 
Ed J

---

### Post by Autodave on 2011-10-29
> Not sure how old your ASUS netbook is, or its specs, but it should run fine on several distributions.  Drop over to the Mint website and you should be able to get some more experienced advice.  
 
Ed J

I have a 3 year old Asus eeepc900.  One gig RAM and 20 gig SSD.  I have Ubuntu 11.10 running on it with no problems at all.  Just amazes me that such a machine will run the newest Ubuntu.  And, I am running the Unity interface as well!

---

### Post by tartalo on 2011-10-29
> **landsw said:**
> Device is busy. This is not average joe friendly

No, it's not. 

There is an interesting project called one hundred paper cuts, they try to identify and correct annoyances in Ubuntu:
[https://launchpad.net/hundredpapercuts](https://launchpad.net/hundredpapercuts)

The problem I see is that no average Joe would fill a bug, I wonder if they monitor these forums.

---

### Post by landsw on 2011-10-29
I hauled my array of USB distro's over to a neighbors who has an older Ausus eePC. 

They all seemed to work better, at least the sound icon showed up in Peppermint and Lubuntu which it doesn't on mine. Peppermint allowed for side scrolling as well. 

So I'm guessing maybe this has something to do with mine is an AMD processor and his is Intel Atom? 

As is I'm going to go with Ubuntu because everything works. I'm not fond of the UI, prefer the simplicity of Peppermint and Lubuntu, didn't like Joli OS or Easy Peasy at all.  But at least it's all there.

---

### Post by Sef on 2011-10-30
> The problem I see is that no average Joe would fill a bug, I wonder if they monitor these forums.


No, they rarely do. File a [bug report]("https://launchpad.net/ubuntu") if you have a problem.

---

