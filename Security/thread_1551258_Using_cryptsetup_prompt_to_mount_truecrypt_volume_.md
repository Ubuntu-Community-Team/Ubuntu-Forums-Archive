---
title: "Using cryptsetup prompt to mount truecrypt volume as well"
date: 2010-08-12
forum: Security
---

### Post by nyda on 2010-08-12
Hello,

I have a dualboot setup with WinXP/TrueCrypt and Ubuntu/LUKS. Since most of the software I use is cross platform, I'd like to share the configuration files for a few of my applications between XP and Linux. That works nicely using symlinks - as long as XP's TrueCrypt volume is mounted, since that's where those links point to. Mounting it can be annoying though, especially since it's a rather long password...

Now since in my case, both the TC and LUKS volume use the same password, I'd like to use the prompt that appears when booting Linux to mount the XP/TC partition as well. I would imagine the script to display the prompt is located on the inital ramdisk and I probably can't use truecrypt at that time, but there must be a way to pass along the password until the LUKS root is mounted and normal bootscripts are run, at which point writing a little script to run truecrypt and mount the volume using the cached password shouldn't be a problem. But how would I get the password there? Where would I start? Any help would be appreciated. I don't suppose there's a howto out there, but if there is, I really like to see that link :)

---

