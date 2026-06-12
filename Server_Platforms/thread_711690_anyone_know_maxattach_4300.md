---
title: "anyone know maxattach 4300"
date: 2008-02-29
forum: Server Platforms
---

### Post by camkay on 2008-02-29
I am working on our network. We have 2 Dell servers running ubuntu server with one of them our mail server. We have a Maxtor Maxattach NAS 4300 rack mounted server that once ran NT 2000. It has 380 megs ram and 680 gig storage. Does anyone have any experience with this server, or know how to get it up and running with Ubuntu or something simular?

---

### Post by faulkes on 2008-02-29
> **camkay said:**
> I am working on our network. We have 2 Dell servers running ubuntu server with one of them our mail server. We have a Maxtor Maxattach NAS 4300 rack mounted server that once ran NT 2000. It has 380 megs ram and 680 gig storage. Does anyone have any experience with this server, or know how to get it up and running with Ubuntu or something simular?

Offhand, no, I couldn't answer.  I would suggest comparing the hardware
it has in it (models, vendors, chipsets) if at all possible with the various
compatibility lists that exist for linux.

Faulkes

---

### Post by Diressive on 2008-05-28
Hi, I realise I'm a bit late here but just incase anybody else comes looking for an answer. I have a MaxAttach 4300 and it run Ubuntu 8.04 absolutly fine. You just need to open it up and install a CD-ROM drive to get 'buntu installed and then you can add all the hard disks you want later and use mdadm to set up the RAID. I also set up ssh so I could make it headless and smb shares. I connect to it from Windows and Mac OS X.

Hope this helps. :)

---

