---
title: "Need to change display for console on Ubuntu 12.04 server"
date: 2012-10-27
forum: Server Platforms
---

### Post by le_jawa on 2012-10-27
I don't know if anyone here has encountered this or not, but here goes...

I just replaced a couple of Windows servers running SQL Server with Ubuntu 12.04 and PostgreSQL.  The install is fine, but the console won't work with our Raritan Dominion KXII KVM (KMM, whichever you prefer).  The KVM can't handle the resolution of the Ubuntu console.  Apparently, the console runs at 1280x1024.  I need it to run at a display just like RedHat/Fedora/CentOS use, 720x400, and may even need to change the font to get it to work.  Basically, the RedHat-based systems use the old 80x25  (80x24?) character display and it works with the KVM.  The higher resolution on the Ubuntu server creates a display that has a wider and higher character count (not sure what it is though).  

Does anyone know how to change this?  I can't do jack with the servers until this is fixed.

Thank you all,

Jason

---

### Post by tomh0665 on 2012-11-01
You probably need to play with your grub settings. Try:

1. unset GRUB_GFXMODE and set GRUB_TERMINAL and GRUB_GFXPAYLOAD_LINUX in "/etc/default/grub" to "console" and "text" respectively and then run update-grub to regenerate "/boot/grub/grub.cfg".

2. set GRUB_TERMINAL, GRUB_GFXMODE, and GRUB_GFXPAYLOAD_LINUX in "/etc/default/grub" to "gfxterm", "<resolution>", and "keep" respectively and then run update-grub to regenerate "/boot/grub/grub.cfg".

---

### Post by le_jawa on 2012-11-13
tomh,

Thanks for the tip!  That got me headed in the right direction.  With some additional digging, I found that I can blacklist the video driver, which allows me to run in pure text-only mode.  Doing that worked great, but now I'm curious, do you (or anyone else out there) know how I can more correctly disable the load of the video driver rather than blacklisting it?  I'm sure there's a more elegant solution out there, but I don't know what it is.

Thanks again all!

---

