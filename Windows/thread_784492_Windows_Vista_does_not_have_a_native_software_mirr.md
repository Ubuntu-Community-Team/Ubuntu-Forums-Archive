---
title: "Windows Vista does not have a native software mirroring capability?"
date: 2008-05-06
forum: Windows
---

### Post by -random on 2008-05-06
Windows Vista does not have a native software mirroring capability.

--
Carey Frisch
Microsoft MVP
Windows Client

--------------------------------------------------------------------------------------------------

"Sanze" wrote:

| Hi,
| Windows Vista supports Software HD Mirroring like Windows 2003 Server? Copy
| 1 to 1 of a physical Hd.
|
| If this is supported, which version will support this feautures?
| Thx
|
| Regards

[http://www.vistax64.com/vista-installation-setup/56217-vista-software-mirror.html](http://www.vistax64.com/vista-installation-setup/56217-vista-software-mirror.html)

is this true??

i'd like 2 have a raid-1 on both ubuntu and vista.. (for vista games better  reading speed for loooading gamez...)

or didn't i google enough?

---

### Post by igknighted on 2008-05-06
Software mirroring wouldn't speed load times at all... a software driven raid1 (mirrored) array would likely slow disk I/O a lot.  If your mobo doesn't have a raid component (most gaming ones do), you should buy a plug in card.  Also, raid0 is what will speed up disk I/O.  Mirroring will only make a duplicate of the data... ie, write it twice.  What you want is striping, where it writes to both disks alternately to speed up I/O.

---

### Post by Dr. C on 2008-05-07
Would not a native software mirroring capability interfere with the DRM in Vista? 

Vista was designed first and foremost to accommodate DRM so I would be very surprised if it included anything like a native software mirroring capability.

---

### Post by K.Mandla on 2008-05-07
Moved to Windows discussions.

---

### Post by rickyjones on 2008-05-08
> **FineE said:**
> Would not a native software mirroring capability interfere with the DRM in Vista? 

Vista was designed first and foremost to accommodate DRM so I would be very surprised if it included anything like a native software mirroring capability.

No.

Where do you gather that Vista was designed first and foremost to accommodate DRM? If that was true then my syncing all my music to an external hard drive would not be allowed...

As to the actual topic I'm not sure if Vista has native software RAID capabilities, I've never checked. I know that it recognizes my motherboard RAID on my gaming rig (an Nvidia Nforce RAID) without issues and with great performance!

Sincerely,
Richard

---

