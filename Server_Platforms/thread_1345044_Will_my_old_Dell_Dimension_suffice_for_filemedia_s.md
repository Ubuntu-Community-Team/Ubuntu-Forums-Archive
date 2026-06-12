---
title: "Will my old Dell Dimension suffice for file/media server?"
date: 2009-12-03
forum: Server Platforms
---

### Post by Lloyds on 2009-12-03
I have a 2006 Dell Dimension 3100 in storage that I'd like to use as a file and media server. It has a Pentium 4 with 1 GB of RAM and currently 1 80 GB hard drive. My basic understanding of this type of server requirement is that you don't need much in terms of processing or RAM, just lots of hard drive space.

I'm not sure if the bios will support a large hard drive. So I was thinking of installing Ubuntu on the existing 80 GB drive. And then throw in a PCI Sata controller, attaching 2 2TB hard drives configured for RAID 1 for some data protection.

I'm new to both linux/Ubuntu as well as any servers other than purchased Dell boxes for my office and would appreciate confirmation that what I'm thinking will work out and is a decent solution. And of course, anything else I should be thinking about at this point.

Thanks.

---

### Post by julianb on 2009-12-03
That machine is far above the minimum to work as a file server. There is nothing to stop you from running a machine with a 200mHz processor and 128MB of RAM as a file server, but if you wanna store more than 80GB of files, you'd better have a larger-than-80GB hard drive. 

(for myself I've never had a desire to hold on to more than 80GB of files for anything.) 

Less than 1% of the 80GB drive should be needed by OS and applications software.

---

### Post by Cheesemill on 2009-12-03
> **Lloyds said:**
> ...attaching 2 2TB hard drives configured for RAID 1 for some data protection.

Please remember that any sort of RAID **is not a backup strategy**, it's only a method to reduce downtime if a disk fails.

Whenever you use RAID you must also have a backup scheme in place as well (if you value your data that is).

---

### Post by volkswagner on 2009-12-03
As already stated that hardware is overkill for a simple file server.  Think about running that hog 24/7 and how much electric will be consumed.  Probably hovering around the 100watt range.

You may be interested in just adding a NAS device to your network at under 15 watts.

---

### Post by Lloyds on 2009-12-03
Thanks very much for the replies.

In addition to just storing data and acting as a file server, I do intend to stream music and video to my PS3. And I will allow friends and family to download music/video as well. And whenever I need to do some video conversion I'll probably look at using this server to do so overnight versus using my laptop. I'm not sure if that changes anything.

And I presume since nobody said otherwise that if I did go down this route, using the original HD for the OS and applications and then buying 2 new 2TB hard drives along with a PCI SATA controller would work and make sense? I don't think the bios can handle TB drives thus the need for the separate controller.

Backup, yeah I'll have to figure out something. It would suck to lose all that media.

---

### Post by Vegan on 2009-12-03
Some SATA cards have a boot ROM, those can use up to 2TB.

---

