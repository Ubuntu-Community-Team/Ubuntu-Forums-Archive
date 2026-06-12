---
title: "External Hard Drive for Media Streaming and Life Span."
date: 2011-06-14
forum: The Cafe
---

### Post by donniezazen on 2011-06-14
Hi,

I just set up a server which i am going to use for serving media and files and keeping backup of other system i have. The computer has 100 GB hard drive. I have hooked up a 1.5 TB external hard drive which i plan use 24X7. 

I was wondering if it will drastically reduce the life span of my external hard drive. I want it to work flawlessly for near future. 

What is the best way to mount it for media serving purposes? Like a usb or make a home folder off it. I kind of keep it isolated from affairs of OS and just use it as data storage.

Thanks.

---

### Post by jerenept on 2011-06-14
> **soham_1207 said:**
> Hi,

I just set up a server which i am going to use for serving media and files and keeping backup of other system i have. The computer has 100 GB hard drive. I have hooked up a 1.5 TB external hard drive which i plan use 24X7. 

I was wondering if it will drastically reduce the life span of my external hard drive. I want it to work flawlessly for near future. 

What is the best way to mount it for media serving purposes? Like a usb or make a home folder off it. I kind of keep it isolated from affairs of OS and just use it as data storage.

Thanks.

I'm sure you've heard this before, but you really should not use a USB disk for high-performance purposes like media serving.

To answer  your question,  i think, unless your drive is old, the lifespan will not really be shortened...   you will easily fill a 1.5TB  drive.

---

### Post by ghostborg on 2011-06-14
I just use Ubuntu desktop sharing files with media drives just mounted to the /media folder. They show up on the desktop like a USB stick would as I think you where describing.
I have a small drive as my OS and additional internal drives for media that way if you need to do something drastically with the OS your media is still intact. 
I use the WD Green drives and in the Screen Saver -> Power management I have spin down hard drives when ever possible checked.

The only minor drawback is if you are accessing the drive from another computer there is a slight spin-up delay the first time it is accessed. Small price to pay for lower power and longevity.

I would recommend that you also use a battery backup for those pesky brown outs.
My system has been running 24/7 I think three years now and I just routinely update the OS and occasionally add drives for expansion. Now I have to knock on wood.

I think also it can be a PIA to setup shares on a USB disc.

---

### Post by donniezazen on 2011-06-14
> **jerenept said:**
> I'm sure you've heard this before, but you really should not use a USB disk for high-performance purposes like media serving.

To answer  your question,  i think, unless your drive is old, the lifespan will not really be shortened...   you will easily fill a 1.5TB  drive.

Thanks,

Is it because of low read write speed. I just wanted to know if it would blow up if i use it a lot. At the end of day their will be hardly 2-3 hours of usage but it will have to remain connected to server. I am pretty sure ubuntu will spin it down when not needed.

---

### Post by cariboo on 2011-06-14
I've had far more problems with inexpensive enclosures, than I have hard drives, except for a Seagate 750GiB that has been replaced under warranty twice. Data transfer speeds are noticeably slower using a usb drive.

---

### Post by donniezazen on 2011-06-14
> **ghostborg said:**
> I just use Ubuntu desktop sharing files with media drives just mounted to the /media folder. They show up on the desktop like a USB stick would as I think you where describing.
I have a small drive as my OS and additional drives for media that way if you need to do something drastically with the OS your media is still intact. 
I use the WD Green drives and in the Screen Saver -> Power management I have spin down hard drives when ever possible checked.

The only minor drawback is if you are accessing the drive from another computer there is a slight spin-up delay the first time it is accessed. Small price to pay for lower power and longevity.

I would recommend that you also use a battery backup for those pesky brown outs.
My system has been running 24/7 I think three years now and I just routinely update the OS and occasionally add drives for expansion. Now I have to knock on wood.

I am using Ubuntu Server so their is no GUI. I created a folder in system root and mount external drive there. This is exactly how i want to do it. Keep OS separate from data. I am sure ubuntu server takes care of power management and spinning it down on its own.

---

### Post by donniezazen on 2011-06-14
I don't know why i need a server. :lolflag: i guess to kill time setting it up. The good thing using an external drive is that it is portable and data remains safe.

I guess Subsonic's cache takes care of lag. My upload speed is capped to 4 MBPS. But that's alright.

---

### Post by Spr0k3t on 2011-06-14
I wouldn't use a USB drive for the long term to serve up files for media.  If you are only using it for short term, then you are set, just be sure to have backups handy.  As for connecting other computer systems to the drive over the network, I would use NFS.  If you really need connectivity through to a windows computer, you could get away with using CIFS without problems... use SAMBA if you really need it.

---

### Post by donniezazen on 2011-06-14
> **Spr0k3t said:**
> I wouldn't use a USB drive for the long term to serve up files for media.  If you are only using it for short term, then you are set, just be sure to have backups handy.  As for connecting other computer systems to the drive over the network, I would use NFS.  If you really need connectivity through to a windows computer, you could get away with using CIFS without problems... use SAMBA if you really need it.


What do you consider long or short term? I use the external hard drive to make backups. Do you mean i need another drive to make its back. Are their chances that it could get corrupted. I will be connecting it to local network to back up of windows and ubuntu system. Mostly i need to use something like Ajaxplorer to upload/download files over internet.

Since this is mostly for fun. I don't think i will buy a dedicated hard drive for media serving for atleast a year.

---

