---
title: "Compaq Proliant 1600R Boot Error (8.04)"
date: 2008-10-17
forum: Server Platforms
---

### Post by Joseph Rawlings on 2008-10-17
I am currently trying to install Ubuntu Server 8.04 on a Compaq Proliant 1600R server configured with a single HD Raid0 array (its in an array format, because its hot swap with a 5 HD slot aray). When trying to boot to the install CD after the Smart Start Bios Configuration wipe and then a manual configuration with the Linux OS selected. Upon boot it says this:

```
ISOLINUX 3.53 Debian-2007-12-11 isolinux:
Cannot boot from this CD. Please try a BIOS Update.
```

I am sorry to say, but the BIOS are at current P8, the latest version released by Compaq. Any help would be appreciated and thank you in advanced.

I am also willing to try any ideas anyone has. Its been a brick for about a week since trying to install Ubuntu Server.

---

### Post by submain on 2008-10-17
I have no experience with RAID but maybe the boot CD could be corrupted. I would suggest checking its checksum against an md5

---

### Post by Joseph Rawlings on 2008-10-17
Doesn't seem to be the problem. I have tried some two times before with different CD's, and I did try to reburn at a slower speed and md5 does check, so its not the CD. I am trying to see is dapper will install, but no promises. I dont think it will help any.

---

### Post by Joseph Rawlings on 2008-10-17
Sorry to say, but sarge yields no responce as such expiraments as Debian Etch. It just sits at an underscore blinking page. 

By the way, the Install Ubuntu Server page comes up, just after that I recieve errors.

---

