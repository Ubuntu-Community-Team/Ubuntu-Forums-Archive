---
title: "Paranoia: Do you write-protect files and directories?"
date: 2010-12-01
forum: The Cafe
---

### Post by drumsticks on 2010-12-01
Files are usually created writeable.  But some files, for example: media files (*.mp3, *.ogg), disk images (*.iso) or simply old archived documents, are unlikely to be modified anymore.

Do you remove write permissions on these files to prevent accidental modification, deletion** or otherwise (god forbid) virus infection?

**Yes, I'm aware that file deletion is a directory property, not a file property; at least on *NIX systems, I don't know about Windows.

I've started doing this on some aspects of my files, for instance, my backup partitions (on different physical disks) are always mounted read-only.  The backup script remounts it read-write, does its thing, then remounts it read-only again.  My archived documents also have their write and delete permissions revoked.

Care to share your experiences?

---

### Post by NightwishFan on 2010-12-01
I see nothing wrong with doing that, just in case. Accidents do happen. :)

---

### Post by czr114 on 2010-12-01
Yes, but only on stored backups and large media.

Everything else stays write-accessible, as it's backed up.

Write protection is an important and underused failsafe.

---

### Post by drumsticks on 2010-12-01
> **czr114 said:**
> Yes, but only on stored backups and large media.

Everything else stays write-accessible, as it's backed up.

Write protection is an important and underused failsafe.

This strategy still allows the master to be modified or deleted, and the backup mirror(s) at some stage will follow suit.  I think write-protection of the master copy is still a good idea.  Don't you think?

---

### Post by czr114 on 2010-12-01
> **drumsticks said:**
> This strategy still allows the master to be modified or deleted, and the backup mirror(s) at some stage will follow suit.  I think write-protection of the master copy is still a good idea.  Don't you think?
It depends on the master copy. I can't write protect masters of source, documents, images in use, mail, etc., because I'm actively working on them. The backups are protected because they're archival in nature, but what's being archived is active work product.

I don't back up large media and ISOs because it's simply cost-prohibitive. RAID5 is the best I can do.

---

