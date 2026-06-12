---
title: "Ubuntu should have an upstart job for saving/restoring backlight level on laptops"
date: 2014-12-28
forum: Ubuntu, Linux and OS Chat
---

### Post by tamir2 on 2014-12-28
Small script - it saves last used value of brightness (stored in file  BRIGHTNESS_CONTROL) to file (SAVEDFILE) on shutdown and restore it from  file on next startup. Works on systems Ubutnu 12.04-Ubuntu 14.04. 
Ready for use archive is in attachment, you can extract it with the following command:   sudo tar -zxvf upstart_backlight.tar.gz -C / 
 Read more - [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1270579/comments/18](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1270579/comments/18)

---

### Post by Elfy on 2014-12-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Jack_Mathews_Jr. on 2014-12-28
Thank you very much for this. Works perfectly on my HP G7.

---

### Post by ian-weisser on 2014-12-28
Comment #11 of that thread properly explains how this will be solved in future releases of Ubuntu by the already-imminent change from Upstart to Systemd.

The Upstart script may be a candidate for an SRU update to 12.04 and 14.04...if it's important enough to bother. Minor bugs don't get fixed in those, as the risk/benefit balance is too high toward causing other unexpected (and more serious) issues, and thereby undermining the purpose of 'stability' in the release.

---

### Post by tamir2 on 2014-12-29
> **Jack_Mathews_Jr. said:**
> Thank you very much for this. Works perfectly on my HP G7.

Thank you for your work [Norbert]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1270579/").

---

