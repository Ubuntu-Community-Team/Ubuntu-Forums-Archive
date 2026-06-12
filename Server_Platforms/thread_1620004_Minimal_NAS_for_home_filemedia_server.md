---
title: "Minimal NAS for home file/media server"
date: 2010-11-12
forum: Server Platforms
---

### Post by alanbrowne on 2010-11-12
I have a notion to create a home file/media server around Ubuntu server.  I'm not a Linux expert (though I have Ubuntu desktop installed for the hell of it under VMWare Fusion on my Mac).

See network diagram - attached (SVG [Inkscape]).

Spec:
   .x86 - is a dual core needed?    - would be cool to build a fanless box.
   .SATA (two drives - eventually RAID 1) 2 x 2 TB.
   .1 GB RAM
   .1 Gb ethernet
            (connects to a 1 Gb switch which connects to a 1 Gb router/Gateway and 802.11n/300)

It's essential that it play nice with 2 Win XP boxes and 2 Mac (OS X 10.6) systems on the network.

I've been reading the Ubuntu Server Guide ( [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html) )     which is certainly helpful - and covers more than I need, but I'm still hazy over a few things.

1. Is there a means to have a remote GUI (HTML) "control panel" for the server?  I'll be burying the server in a remote part of the house, out of the way (once I get it up and running).  Would be nice to monitor it, etc. from the home office.

2. Is there a checklist of the _minimum_ I need to do for such a file server.  In effect I want to emulate the D-Link DNS-323 without its screwed up permissions.

3.  I don't need : print, web, etc. servers.

All guidance, esp. existing checklists for the strict minimum, appreciated.  (No RAID to begin with).

Thanks,
Alan

---

### Post by CharlesA on 2010-11-12
> **alanbrowne said:**
> 
   .x86 - is a dual core needed?    - would be cool to build a fanless box.
   .SATA (two drives - eventually RAID 1) 2 x 2 TB.
   .1 GB RAM
   .1 Gb ethernet
            (connects to a 1 Gb switch which connects to a 1 Gb router/Gateway and 802.11n/300)

That should work fine. I would suggest having one dedicated drive for the OS and the other drive (or RAID array) for the data, since that's what I do and it's worked great.

You don't really need a dual-core machine, but if you can get one, it would be great. My NAS box is a dual core with 6GB of RAM, since I use it for virtulization.

> It's essential that it play nice with 2 Win XP boxes and 2 Mac (OS X 10.6) systems on the network.

Look into Samba if you are going to be running with Windows machines. I think Macs can use NFS, but I'm not 100% sure as I've not messed with it.

> I've been reading the Ubuntu Server Guide ( [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html) )     which is certainly helpful - and covers more than I need, but I'm still hazy over a few things.

It's a good guide. There is also good info over at [http://help.ubuntu.com](http://help.ubuntu.com) and [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

> 1. Is there a means to have a remote GUI (HTML) "control panel" for the server?  I'll be burying the server in a remote part of the house, out of the way (once I get it up and running).  Would be nice to monitor it, etc. from the home office.

You can look into Webmin, or ISPstatus, or just use SSH. I used to use Webmin, but now I admin the server directly using SSH.

> 2. Is there a checklist of the _minimum_ I need to do for such a file server.  In effect I want to emulate the D-Link DNS-323 without its screwed up permissions.

There isn't a minimum that I know of, outside of using Samba if you are connecting with Wndows boxes.

> 3.  I don't need : print, web, etc. servers.

The default install of Ubuntu doesn't have any of that stuff installed.

> All guidance, esp. existing checklists for the strict minimum, appreciated.  (No RAID to begin with).

Thanks,
Alan

Like I said earlier, use two drives, one for the OS and one for the data drive, but other then that. It's not really that hard to set up. :)

My server started out as a NAS with just Samba and SSH installed, but now it's running Apache (web server), VirtualBox (VM software) as well as Samba and SSH.

---

