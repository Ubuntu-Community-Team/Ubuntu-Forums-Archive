---
title: "Why doesnt the ubuntu site host usb images that can be installed via dd?"
date: 2010-04-30
forum: The Cafe
---

### Post by markp1989 on 2010-04-30
title says it all really, arch have been doing it for a long time so why cant ubuntu?

---

### Post by snowpine on 2010-04-30
Because Ubuntu includes a handy little application called 'usb-creator' that will do it for you. 'dd' can be a dangerous command for noobs and even not-so-noobs like me. :)

---

### Post by markp1989 on 2010-04-30
> **snowpine said:**
> Because Ubuntu includes a handy little application called 'usb-creator' that will do it for you. 'dd' can be a dangerous command for noobs and even not-so-noobs like me. :)

i am aware of the usb creator, i only have 1 pc i use ubuntu on, and that doesn't have a cd drive on it, so i have to burn the cd , boot it from a computer with a cd drive then make the usb disk there, which seems alot of un necessary steps

---

### Post by oldsoundguy on 2010-04-30
personally, I can think of many reasons.  First being actual demand.  Of all of the users of Ubuntu, how many run it from a USB?

Then there is the issue of USB itself.  How reliable is your pen drive .. is it a quality drive or a cheap piece of junk that can and will fail at any moment?  

USB itself on some computers is a total crap shoot as to ITS reliability.

Why offer something that is going to get a bunch of complaints about "my download doesn't work" because there is no control over USB itself during the download?

Just my thoughts.

---

### Post by Lightstar on 2010-04-30
I used unetbootin

My PC does have a cd-rom drive, but I rather use my usb flash drive than add another used cd-rom to my big pile of cup coaster thingies

---

### Post by cariboo on 2010-04-30
> **markp1989 said:**
> i am aware of the usb creator, i only have 1 pc i use ubuntu on, and that doesn't have a cd drive on it, so i have to burn the cd , boot it from a computer with a cd drive then make the usb disk there, which seems alot of un necessary steps

You can create a usb image directly from the iso, using the USB Startup Creator applet.

You can also mount the iso and use dd to create a usb device.

---

### Post by K.Mandla on 2010-04-30
> **markp1989 said:**
> title says it all really, arch have been doing it for a long time so why cant ubuntu?
I've been wondering about this for a while too. It's very handy to dd a USB image and boot straightaway from that.
> **snowpine said:**
> Because Ubuntu includes a handy little application called 'usb-creator' that will do it for you. 'dd' can be a dangerous command for noobs and even not-so-noobs like me. :)
The only problem is, before you can get to the USB creator, you still have to get into the Ubuntu system, so you still end up writing a CD to get to the desktop to open the USB creator. ... :confused:
> **Lightstar said:**
> I used unetbootin ... My PC does have a cd-rom drive, but I rather use my usb flash drive than add another used cd-rom to my big pile of cup coaster thingies
I tried that this time too, and it worked quite well. Not every ISO seems to work, but the majority do.

---

### Post by chris200x9 on 2010-04-30
> **oldsoundguy said:**
> 

Then there is the issue of USB itself.  How reliable is your pen drive .. is it a quality drive or a cheap piece of junk that can and will fail at any moment?  

This is pure bupkus IMHO, it's not like he's installing to USB and using it for data, this is no different than CD. You could have bad burns, or scratch the disk.

---

### Post by juancarlospaco on 2010-04-30
*Very friendly method...*

---

### Post by Dr Belka on 2010-04-30
> **oldsoundguy said:**
> personally, I can think of many reasons.  First being actual demand.  Of all of the users of Ubuntu, how many run it from a USB?

Then there is the issue of USB itself.  How reliable is your pen drive .. is it a quality drive or a cheap piece of junk that can and will fail at any moment?  

USB itself on some computers is a total crap shoot as to ITS reliability.

Why offer something that is going to get a bunch of complaints about "my download doesn't work" because there is no control over USB itself during the download?

Just my thoughts.

I think that you are missing the point.  I do all of my installs since 8.10 with a usb drive.  Its not like I use a live-usb to do any work, I just find it to be a much faster and more convenient way to do an install.  Besides, I would rather do it with the live-usb then have to use yet another CD any day.  But this is just my preference.

---

### Post by K.Mandla on 2010-05-02
I decided to take the initiative on this one, and used dd to write a disk image of an Ubuntu 10.04 desktop i386 ISO written to a 1Gb disk with Startup Disk Creator. A torrent is [here]("http://linuxtracker.org/index.php?page=torrent-details&id=c54b4dd3f1ab9d50a25ebdccc7157fc843292784"), if anyone is interested. It would still be preferable for the Ubuntu overlords to do this automagically instead. ;)

---

### Post by init1 on 2010-05-02
Someone should make an image and torrent it.

---

### Post by me98278 on 2010-05-02
Another option to create a bootable USB drive is outlined here ..

[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

That is if you have access to a windows system...

---

### Post by sunk8 on 2010-05-02
> **markp1989 said:**
> title says it all really, arch have been doing it for a long time so why cant ubuntu?

I use [Unetbootin]("http://unetbootin.sourceforge.net/") . It writes an iso directly onto a usb flash drive. And it availaable for Windows as well as Linux.

---

### Post by ugm6hr on 2010-05-02
The 8.04 Netbook Remix was available as a USB image.  Unfortunately, the powers that be decided to axe it for later versions.

Given the absence of CD / DVD drives on netbooks, and no USB Creator / Unetbootin that works on the lpia version pre-installed on those devices, there was a bit of a problem for a few upgraders.

For most existing Ubuntu users, USB Creator does the trick without having to burn a CD, as does Unetbootin for Windows users (the Linux version of Unetbootin has always been a bit less reliable).

---

### Post by Paqman on 2010-05-02
> **snowpine said:**
> 'dd' can be a dangerous command for noobs and even not-so-noobs like me. :)

They don't call it "destroy disk" for nothing.

---

### Post by markp1989 on 2010-05-02
> **K.Mandla said:**
> I decided to take the initiative on this one, and used dd to write a disk image of an Ubuntu 10.04 desktop i386 ISO written to a 1Gb disk with Startup Disk Creator. A torrent is [here]("http://linuxtracker.org/index.php?page=torrent-details&id=c54b4dd3f1ab9d50a25ebdccc7157fc843292784"), if anyone is interested. It would still be preferable for the Ubuntu overlords to do this automagically instead. ;)

thanks for the upload :) i will seed it, it would be nice if they made it available, esp for netbook remix, there is obviously some demand for it, because there are alot of how tos over the web from before the usb creator was available

---

