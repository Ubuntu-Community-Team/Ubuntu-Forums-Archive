---
title: "Lost X server  when logging into ubuntu 12.04"
date: 2012-06-11
forum: Ubuntu Studio
---

### Post by Flaggmann on 2012-06-11
On restart setup process OK and initial ubuntu logo "for creative humans" displayed and then systems just hangs there will not progress any further. 

I had added a 2nd monitor (hdmi o/p) Acer Aspire and used nvidia config to set up as dual separate X monitors. Worked OK for about 5 hours restarted numerous times, then left system on and came back 3 hours later with it simply idling. Firefox froze, had to Ctrl-Alt-Fx and use level 3 login to kill firefox process; return to X monitor and worked OK. No crash messages, logged out and restart only to find above described symptoms. 

Can run all OK from a UNETBOOT thumb drive as well as access Ubuntu 12.04 hard drive via level 3 login. all X config files look normal.
Unable to run Xorg from thumb drive has to be Xvesa

Can anyone point me in direction to correct this pls?  Thanx

---

### Post by Flaggmann on 2012-06-12
ntfs non-boot partition constant busy no mount or unmount hung system

---

### Post by Sylos on 2012-06-12
Hello there.

Excuse me if Im being dim and not understanding your post but could you confirm whether you can get to a command prompt or not?

Also, have you tried booting into the recovery mode?

If this is purely an xorg problem then you should be able to get to a prompt and issue a command to reconfigure x and get back to a usable system. 

```
sudo dpkg-reconfigure xserver-xorg
```

You will loose your current X configuration but you can start again and see what the issue is.

---

