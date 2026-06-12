---
title: "UNMOUNTABLE_BOOT_VOLUME error on migrated Win XP vdi"
date: 2007-11-05
forum: Virtualisation
---

### Post by jsbach1812 on 2007-11-05
I have a WinXP vdi image that is running fine under one machine running 1.5.0 OSE and 7.10. I migrated that vdi file to another machine (also 7.10) and created a new VM under a new install of 1.5.2. I get the Windows splash screen and then the BSOD UNMOUNTABLE_BOOT_VOLUME.  RTM and posted on the Virtualbox board but I'm coming up empty.

Has anyone had any experience with something like this?

Thanks

---

### Post by kast on 2007-11-05
I have with XP Pc's but not in a Virtual PC, the fix i used at work would be to boot to the XP cd select recovery console select the C: drive and run a** fixboot**, and then a **fixmbr**

---

### Post by jsbach1812 on 2007-11-06
That was a good idea.  The cd did boot and I got past the first screen but after I picked R for repair my system slowed down to a crawl and didn't recover.  Another thing I noticed was the permissions for the file I transfered over had the owner set to "nobody".  Once I changed that VB would boot past the splash screen and into the Welcome screen but then everything would slow down again.  I'm going to try to create a fresh image and see if I get the same problems.  Could be a unique bug.

---

### Post by kast on 2007-11-06
You want to pick the recovery console, not the repair, not sure if you did, but it sounds like your starting from scratch let me know how that goes :)

---

### Post by jsbach1812 on 2007-11-11
Figured out the machine lag issue.  I had a memory stick go bad so the VM was attempting to access more memory than available.  Everything runs fine now. 

Lessons learned:  
Check permissions to correct the Unmountable volume error 
Insure that the VM is not attempting to use more than the available memory

---

### Post by dubcat on 2008-02-16
Thanks for this - i had the same problem as you.  I checked permissions and sure enough the virtual disk was read only.  I did a chmod u+w <disk image name> and things started to work just great :)

Cheers,
Dub

---

