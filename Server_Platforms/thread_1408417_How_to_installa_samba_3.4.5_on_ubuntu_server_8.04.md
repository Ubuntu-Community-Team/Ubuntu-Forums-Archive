---
title: "How to installa samba 3.4.5 on ubuntu server 8.04?"
date: 2010-02-16
forum: Server Platforms
---

### Post by eufran on 2010-02-16
Hello i have ubuntu server 8.04 witch preinstalled samba 3.0.28.
I like to install from repositories samba 3.4.5.

How???

Thanks

---

### Post by cdenley on 2010-02-16
If you want samba 3.4.5, upgrade to ubuntu 10.04, which is due to be released in a couple months. Of course I don't recommend this since it would be very unstable. Samba 3.4.5 will not be backported to hardy.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Is there a reason you want to upgrade?

---

### Post by eufran on 2010-02-16
Only i need to upgrade samba to 3.4.5 for integration with windows 7 and fixes bug.

I no like to upgrade to ubuntu server 10 cause the ubuntu 8.04 is Long Time Suport.

thanks

---

### Post by cdenley on 2010-02-16
> **eufran said:**
> Only i need to upgrade samba to 3.4.5 for integration with windows 7 and fixes bug.

I no like to upgrade to ubuntu server 10 cause the ubuntu 8.04 is Long Time Suport.

thanks

Yes, and it is stable and supported long-term because the packages were tested before 8.04 was released 2 years ago. Bug fixes should be backported, but not new features. You can remove all the samba packages and compile 3.4.5 yourself, but don't expect any support or automatic updates for it.

---

