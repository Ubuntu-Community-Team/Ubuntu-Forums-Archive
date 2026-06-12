---
title: "Starling TRIM support for SSD's"
date: 2010-11-09
forum: System76 Support
---

### Post by Paul Stone on 2010-11-09
Near as I can tell, like the Mac, the Starling uses a kernel which doesn't automatically support [TRIM]("http://en.wikipedia.org/wiki/TRIM").  But, it's possible to TRIM the SSD using the wiper.sh script which comes with [hdparm]("http://sourceforge.net/projects/hdparm/files/").

However, in order for this to work:

1) Starling needs to utilize an ext4 file system.
2) The SSD shipped with Starling must support TRIM.

Are both of the above true?

Cheers.

---

### Post by isantop on 2010-11-09
Automatic TRIM support will be coming in Natty in april. For now, the Starling does use an Ext4 filesystem, and the Intel Solid State Drives do support TRIM.

---

### Post by Paul Stone on 2010-11-15
Cool!  Thanks!

---

