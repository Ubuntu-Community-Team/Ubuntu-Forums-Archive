---
title: "WPA_Supplicant auto start &amp; change to rc.local stuck at boot"
date: 2011-08-01
forum: Server Platforms
---

### Post by donniezazen on 2011-08-01
I have tried different methods to auto start wpa_supplicant at boot on Ubuntu Lucid server on a laptop which can't be connected to Ethernet.

The only thing that worked is adding the wpa_supplicant command before exit0 in rc.local. It solve my problem of wpa_supplicant auto start and annoyance on not be able to ssh before local login. But the screen stuck at Ubuntu Logo. How can i get pass Ubuntu logo screen to regular tty or xbmc in future?

Thanks.

Sources:-
[http://ubuntuforums.org/showthread.php?t=352568](http://ubuntuforums.org/showthread.php?t=352568)
[http://ubuntuforums.org/showthread.php?t=208472](http://ubuntuforums.org/showthread.php?t=208472)
[http://ubuntuforums.org/showthread.php?t=1259003](http://ubuntuforums.org/showthread.php?t=1259003)

---

### Post by donniezazen on 2011-08-01
Resolved for now. Thanks.

---

### Post by chankyakutil on 2012-05-31
> **donniezazen said:**
> Resolved for now. Thanks.

What did you do to resolve your issue, I am having the same issue, your help would be great.

Thank you.

---

