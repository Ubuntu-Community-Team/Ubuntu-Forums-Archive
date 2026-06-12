---
title: "Kernel 2.6.13 / Breezy"
date: 2005-10-19
forum: Ubuntu Backports
---

### Post by sfabel on 2005-10-19
Hi ppl,

will this kernel be in the repositories for Breezy or will I have to look for it somehwere else?

I have hardware that needs that version of the kernel, and I am not sure how to proceed. If I must, I'd recompile the kernel as well, but I would like to play it safe: is there any way to how to find out regarding the original / official config file? I could also patch the existing kernel (2.6.11), and my plan would be to use the "oldconfig" option, after applying the patch, and then going through the file looking for the one additional driver that I need. From what I understand, I then only would need to compile the modules (provided that I set it to "M"), and do a manual install? That should re-create the /lib/modules directory structure with that one additional driver? What else do you guys suggest?

Just throwing ideas out, let me know if any of them are woth a try. ;)

Thanks,
Stephan

---

### Post by Technoviking on 2005-10-19
The Backport Project does not backport updated version of the kernel or other major libraries. 

Mike

---

### Post by sfabel on 2005-10-19
> The Backport Project does not backport updated version of the kernel or other major libraries. 

So, the place to look for is the main repository?

Thanks,
Stephan

---

### Post by ember on 2005-10-19
I guess, you won't find a new major version of the kernel unless you update to Dapper.

---

### Post by jarturoar on 2005-10-20
the official kernel config is under /boot with a name corresponding with the kernel version config-2.6.12xxxxx you can use that to suit your needs

---

### Post by faustobp on 2005-11-03
>  The Backport Project does not backport updated version of the kernel or other major libraries.
If the Backport Project does not backport the kernel could it backport individual modules?

For example: I need the via drm module (for my VIA Unichrome graphics), the Backport Project could pack this module (compiled to the breezy kernel).

Ps: If some one points me the way (some good tutorial in deb packaging, package naming/versioning convetions, etc) I could do it and send for someone in the Backports Project for upload.

---

### Post by Xian on 2005-11-03
[QUOTE=faustobp]Ps: If some one points me the way (some good tutorial in deb packaging, package naming/versioning convetions, etc) I could do it and send for someone in the Backports Project for upload.[/QUOTE]
Sure, here you go: [Making Debian Packages](http://www.debian.org/doc/manuals/maint-guide/index.en.html)

---

