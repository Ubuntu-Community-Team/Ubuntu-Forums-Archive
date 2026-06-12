---
title: "Duplicate a harddrive (different size)"
date: 2008-12-26
forum: Server Platforms
---

### Post by Thirtysixway on 2008-12-26
I have an Ubuntu server at home with a 39GB harddrive.  While this works out okay, I want to replace it with a larger drive (either 160, 250, or 320 depending on my budget) but still keep all my settings, files, etc.

I'd rather have some way to copy everything over instead of installing a new system and going from there.  Somebody told me about using "dd" but wouldn't there be an issue with the differing harddrive sizes?

If anyone has any help or experience with this, I'd appreciate it. :popcorn:

---

### Post by windependence on 2008-12-26
Use dd with the notrunc option like this:

dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror


/dev/sda is the source. /dev/sdb is the target. [COLOR=red]Do not reverse the intended source and target.[/COLOR] It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

-Tim

---

### Post by CrucifiedEgo on 2008-12-26
Wouldn't this leave him with a ext3 partition that's only formatted for 39GB?  I could be wrong as i've only tried this on windows disks in the past.

---

### Post by windependence on 2008-12-27
Nope, the notrunc option takes care of this. I know many people think you can only clone hard drives of the same size with dd but that's not true. I don't use any of the "other" tools like ghost anymore. You can clone almost any OS like this (except Mac OS X).

You can use a bigger block size than 4096 of you like to speed up the process a bit.

-Tim

---

### Post by Bucky Ball on 2008-12-27
You could try partimage and copy your small drive contents onto the larger one. It can be found in the repositories.

---

