---
title: "Home Server Booting from USB Flash Drive"
date: 2008-12-16
forum: Server Platforms
---

### Post by sameat on 2008-12-16
I am helping my brother out with his home media server.  My goal is to create the following:

Server OS running on a flash drive.  All system changes (which will be infrequent after it is built) should be stored on the flash drive, just like it is a regular hard drive (with whatever technology is needed to limit write cycles on the flash drive)   Samba shares served from sata drives (considering LVM because I want to add drives over time).  The server will be headless.  I'd like to use SSH for administration, plus (possibly) some web administration tools for my brother, who does not know linux.  I'm going to suggest backing the server up to a separate external drive.


I have all of the hardware I need.

I was assuming the ubuntu would be a good candidate, but I am really struggling with installing the server on flash memory.  I've been poking at it for a couple of days, and I thought I'd ask for some tips.

1.  What is the best approach to running ubuntu server from a usb flash drive?  I have booted syslinux, dsl, and xubuntu from the drive I plan to use, but I can't get it to work consistently.
I tried installing directly to the flash drive, but it seemed like there was no mbr...it wouldn't boot at all.  Plus, I don't want to kill the flash drive with frequent writes.  I can muddle through problems when they come up, but I would really like to hear methods of doing this successfully so I'm not wasting time.

2.  Has anybody ever tried to replicate the client side features of Windows home server?  I've never seen it, but I want to give my brother a good user experience and I am assuming that WHS has a little bit of that built in.

I'm not married to the idea of running ubuntu.  My OS requirements are: stability, efficiency, and freeness (as in beer).  Freeness (as in speech) is always nice.

Thanks to anybody who can lend me a hand.

---

### Post by sameat on 2008-12-17
I believe I am getting what I need by using remastersys and unetbootin.  Still working out the details, but I've gotten it to work pretty consistently.

---

