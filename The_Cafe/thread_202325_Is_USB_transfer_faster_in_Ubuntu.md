---
title: "Is USB transfer faster in Ubuntu"
date: 2006-06-23
forum: The Cafe
---

### Post by slimdog360 on 2006-06-23
Is it just me or does usb transfer in ubuntu go alot faster than in windows. In windows transfering about 100MB would take forever, but using Ubuntu it takes just seconds. 
Does anyone else find this happens with them?

---

### Post by Virogenesis on 2006-06-23
Yes, copying does seem faster for me when using linux, not only does it seem faster but it seems more stable like I copy GBs of data while watching a movie and dragging it around with compiz on.

---

### Post by FountainDew on 2008-12-14
Does anyone know a windows patch that'll make usb as fast as Ubuntu? I'm quite surprised this is not tooted more as one of the advantages of Ubuntu. I transferred 4.7GB from Vista at a rate of 3.38MB/sec, and in Ubuntu it was up to 12.5MB/sec. This should seriously be looked into!

---

### Post by Therion on 2008-12-14
> **FountainDew said:**
> Does anyone know a windows patch that'll make usb as fast as Ubuntu? I'm quite surprised this is not tooted more as one of the advantages of Ubuntu. I transferred 4.7GB from Vista at a rate of 3.38MB/sec, and in Ubuntu it was up to 12.5MB/sec. This should seriously be looked into!
I'm certainly no expert but I do know there are a lot of factors that can influence transfer speed over a wired connection.  That being said, I'm wondering if this might have something to do with *nix using Ext3 and Windows using NTFS because, like the rest of you, I do notice large data transfers (6 to 10 GB at a time is pretty routine) are far faster in Ubuntu than in XP.

There's also this [YouTube vid](http://www.youtube.com/watch?v=FEvD9RHlccc) that does a time test between Vista, XP and Ubuntu.  The test: Decompress a 17MB *.zip file using the native archiving utility.  Some people say it's not a fair test or that it's meaningless, but Vista taking 12 minutes to do what Ubuntu does in...  Well, you'll just have to watch the video and draw your own conclusion's.

---

### Post by Tomosaur on 2008-12-14
Be careful! 

Linux does not work in the same way as Windows here - you should always explicitly unmount / eject the removable storage to make sure that the files have been written to the disk. 

I'm pretty sure that by default, Windows writes everything to the removable storage when you tell it to (optimised for quick removal), whereas Linux delays writes until you unmount the file-system (optimised for performance). Windows' default behaviour is perhaps more intuitive (particularly since Linux seems to just assume you understand it's default behaviour), but can lead to a direct performance hit both on the OS itself, and by causing extra wear and tear (depending on what exactly the device is, of course). Linux' behaviour means that the actual act of copying something to a USB **looks** blazingly fast, but that's only because it doesn't **actually** do it until some time in the future. If you copy a large file to a USB in Ubuntu, then remove it without unmounting it, you will get a warning telling you your files may not have been written.

I imagine you can change this behaviour so that it is more intuitive and Windows-like, but both options have their advantages and disadvantages.

Of course, since Ubuntu is focused on usability - the Ubuntu devs may have changed the default behaviour to write when you tell it to. If they have, then yes, Ubuntu and Linux in general is just faster (of course, you don't need ME to tell you that :P ).

---

### Post by MikeTheC on 2008-12-14
Being a long-time Mac user, I'm familiar with properly ejecting media before disconnecting it from the system. (This goes back to the days of floppy disks, where Macs had really nice powered-eject floppy drives made by Sony (later sourced from Matshita).

And actually, even Windows has a proper process for unmounting storage media.

Vis a vis a "patch for Windows" to make USB work faster, how about, um, "patching" your machine with Ubuntu instead? ;)

---

### Post by pp. on 2008-12-14
Virus protection in Windows takes a sizeable amount of time. In the worst case scenario the virus scanner will scan your files twice while copying between media.

Well, in the other worst case scenario, you don't have any virus protection at all in Windows.

---

### Post by Tom Mann on 2008-12-14
I find it isn't USB as much as NTFS transfer - it screams compared to Windows... Maybe a NTFS fuse driver and framework for Windows would sort this?

---

### Post by Npl on 2008-12-14
By default, Windows has no write-cache for removable devices. You can easily enable it in the device-manager if you feel like you need it.

---

### Post by pp. on 2008-12-14
> **Tom Mann said:**
> I find it isn't USB as much as NTFS transfer - it screams compared to Windows... Maybe a NTFS fuse driver and framework for Windows would sort this?

Sure, but ... NTFS ***is*** the Windows filesystem.

---

### Post by Tom Mann on 2008-12-15
> **pp. said:**
> Sure, but ... NTFS ***is*** the Windows filesystem.

I know, it's a kick up the backside to Microsoft's implementation really... :KS

---

### Post by mr.propre on 2008-12-15
> **FountainDew said:**
> Does anyone know a windows patch that'll make usb as fast as Ubuntu? I'm quite surprised this is not tooted more as one of the advantages of Ubuntu. I transferred 4.7GB from Vista at a rate of 3.38MB/sec, and in Ubuntu it was up to 12.5MB/sec. This should seriously be looked into!

I use Teracopy. It speed up fast but the disadvantage is that you lose all forms of extra system control. A simple example: When your USB drive is full, it won't let you know and just stop copying.

---

