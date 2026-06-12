---
title: "Automatically allow external USB drives full permissions to all users"
date: 2007-11-03
forum: Ubuntu Brainstorm
---

### Post by suchawato on 2007-11-03
So yes, we External usb drives should automatically be given full permissions to ALL users, just like they do on a Mac or Windows system. Users should not have to figure out how do edit permissions as Root, just to use their everyday USB drive from work or school.
If somebody ***wants*** to change their drives permissions to be more restrictive, they could find out how to do that, but is should not be a default.
This makes it difficult, especially for new users. And especially since they can easily access their files on a Windows or Mac computer.
USB drives should be viewed as a disc, like a floppy or CD, not a restricted hard drive like an internal one might be. If somebody wants to change it that's fine, but not as default.

---

### Post by coolen on 2007-11-03
When I mount a drive, I'm automatically made the user.
Perhaps this doesn't apply to ext formatted drives, but for fat32, that's how it goes.
I think, in the absence of other information, Linux perhaps assumes the user that mounted the drive is the owner of the files?

---

### Post by suchawato on 2007-11-03
This is not the case for certain drives, for instance HFS+ formatted LaCie external Hard Drives.

---

### Post by coolen on 2007-11-03
Given that, this sounds like a great idea. I'd love to see it in Hardy.

---

### Post by smartboyathome on 2007-11-03
> **suchawato said:**
> So yes, we External usb drives should automatically be given full permissions to ALL users, just like they do on a Mac or Windows system. Users should not have to figure out how do edit permissions as Root, just to use their everyday USB drive from work or school.
If somebody ***wants*** to change their drives permissions to be more restrictive, they could find out how to do that, but is should not be a default.
This makes it difficult, especially for new users. And especially since they can easily access their files on a Windows or Mac computer.
USB drives should be viewed as a disc, like a floppy or CD, not a restricted hard drive like an internal one might be. If somebody wants to change it that's fine, but not as default.

It does this for me with all my drives already (formatted EXT3). But if it MUST be implimented, at least have a permission in the users group to make it so that a certain user cannot have access to these drives (as I like to have a guest account on my system).

---

