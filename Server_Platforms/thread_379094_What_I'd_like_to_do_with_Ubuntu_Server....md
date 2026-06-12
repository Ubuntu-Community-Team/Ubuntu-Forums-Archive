---
title: "What I'd like to do with Ubuntu Server..."
date: 2007-03-08
forum: Server Platforms
---

### Post by s1mple_M4N on 2007-03-08
Hi all, thanks for the help so far with my Ubuntu questions.

Right now what I'd like to do is set up Ubuntu Server 6.06 on my home network to centralise music/video/other data.

I have installed Server on an older spare PC to test and have followed a few guides to install webmin and configure it.

I'm still a relative Ubuntu newbie, although through how-to's I have set up a 3-machine LAN, but there are a couple of things I'd like to know about -

1. Server will be only used as a file server and I want to add a PCI SATA card with a 160G disc already containing data. Is it easy enough to share the data and connect the current network machines to Server and use samba to 'map' network drives?

2. Will/can this be done through webmin and how would I go about it?

I appreciate all the help forum members have given so far and look forward to any replies.

Thanks,

RoyJ

---

### Post by pppetter on 2007-03-08
1. I don't know anything about SATA. But I do know that NTFS and Linux isn't a great idea, so if that's what you have on the drive..... 
I think it's easy to set up, how you will feel, I can't tell.

2. Log into webmin and click Servers--->Filesharing with samba--->Choose to install it.
The thingy is that I don't know if webmin itself can configure samba the way You want it to work, you'll probably have to edit the config file.

But hey, if all your computers in the network is linux, then use NFS!!

---

### Post by Aberrix on 2007-03-08
Have you thought of giving [FreeNAS]("http://www.freenas.org") a shot? its a stripped down version of FreeBSD that meant to be a really easy to configure NAS. It sounds like it'd be perfect for what you're trying to do.

---

### Post by Mr. C. on 2007-03-08
> **Aberrix said:**
> Have you thought of giving [FreeNAS]("http://www.freenas.org") a shot? its a stripped down version of FreeBSD that meant to be a really easy to configure NAS. It sounds like it'd be perfect for what you're trying to do.

This is a much better solution for a file-server only type of setup.

MrC

---

