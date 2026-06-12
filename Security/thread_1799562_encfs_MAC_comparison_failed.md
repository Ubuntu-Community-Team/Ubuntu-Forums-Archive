---
title: "encfs: MAC comparison failed"
date: 2011-07-07
forum: Security
---

### Post by lister171254 on 2011-07-07
I'm running 11.04 (64 bit) get the following in my syslog
--------------------------------------------------------------------------------------------------------------------------
Jul  7 17:15:04 LeosLinux encfs: MAC comparison failure in block 0
Jul  7 17:15:04 LeosLinux encfs: error caught in read
Jul  7 17:15:04 LeosLinux encfs: MAC comparison failure in block 127
Jul  7 17:15:04 LeosLinux encfs: error caught in read
Jul  7 17:15:04 LeosLinux encfs: MAC comparison failure in block 0
Jul  7 17:15:04 LeosLinux encfs: error caught in read
Jul  7 17:15:09 LeosLinux encfs: MAC comparison failure in block 0
Jul  7 17:15:09 LeosLinux encfs: error caught in read
Jul  7 17:15:09 LeosLinux encfs: MAC comparison failure in block 0
Jul  7 17:15:09 LeosLinux encfs: error caught in read
-----------------------------------------------------------------------------------------------------------------------

I'd appreciate if somebody could indicate:

1) Why is this happening
2) How can it be fixed
3) How can it be avoided

Thanks

---

### Post by cprofitt on 2011-07-09
I found this discussion which may help -- [http://comments.gmane.org/gmane.comp.file-systems.fuse.encfs.user/93](http://comments.gmane.org/gmane.comp.file-systems.fuse.encfs.user/93)

---

### Post by lister171254 on 2011-07-09
Thanks, I found that too, but it does not address the fundamental issue of why this happens. 

To state the obvious, it's no good having an encrypted system that potentially is corrupt.

---

### Post by lister171254 on 2011-07-11
I've just done a 'grep -R rushish23string /personal' as suggested in the link and it found no errors!!

---

