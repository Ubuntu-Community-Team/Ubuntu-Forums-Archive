---
title: "encrypt persistent loopback file live cd"
date: 2009-05-06
forum: Security
---

### Post by dstempfley on 2009-05-06
I'm trying to implement an encryption solution for a project.  Using a live cd image that I am customizing, I need to find encrypted files that will be used for the persistent home and possibly root directories.  I then need to decrypt the file and set it up to be mounted on boot.  

I see how to do this on the command line, but I am struggling to get it right during the boot-up process.  

I've seen the encryption howto, and the cryptroot, but I'm not encrypting the whole disk, and I can't repartition the drive that the data is on. The data must be in file based file systems.

Is there an existing project to support this or that gets me part the way there?

Thanks,

/dion

---

