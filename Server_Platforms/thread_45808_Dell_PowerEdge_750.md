---
title: "Dell PowerEdge 750"
date: 2005-07-01
forum: Server Platforms
---

### Post by subterrific on 2005-07-01
I recently purchased one of these servers from Dell for email, web, subversion, etc. I tried to install Hoary, but ran into problems because the aacraid driver didn't work with the Dell CERC SATA RAID Controller. The driver was correctly loaded, but failed to find any drives.

Here is the bug in Ubuntu bugzilla for anyone interest:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12243](https://bugzilla.ubuntu.com/show_bug.cgi?id=12243)

I ended up installing Breezy, which worked fine. I'm not sure how I feel about having Breezy on a server that is about to be put in a colo, but since it is just for personal use I think it will work out ok.

---

### Post by sesstreets on 2005-07-01
[QUOTE=subterrific]I recently purchased one of these servers from Dell for email, web, subversion, etc. I tried to install Hoary, but ran into problems because the aacraid driver didn't work with the Dell CERC SATA RAID Controller. The driver was correctly loaded, but failed to find any drives.

Here is the bug in Ubuntu bugzilla for anyone interest:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12243](https://bugzilla.ubuntu.com/show_bug.cgi?id=12243)

I ended up installing Breezy, which worked fine. I'm not sure how I feel about having Breezy on a server that is about to be put in a colo, but since it is just for personal use I think it will work out ok.[/QUOTE]
 I guess you should be alright. BTW whats a colo?

---

### Post by alastair on 2005-07-02
I had the same problem - the install would not find "partitonable media" when disks were connected to the CERC controller (aacraid).

So ... I plugged 2 SATA disks in the motherboard SATA ports, and installed on RAID1 (s/w). This is fine by me.

If you have more disks, you can access them on the aacraid CERC after install.

---

### Post by xcape on 2007-10-26
> **sesstreets said:**
> I guess you should be alright. BTW whats a colo?

I think colo is short for colon.  Some people put their servers in the strangest places. :-({|=

---

