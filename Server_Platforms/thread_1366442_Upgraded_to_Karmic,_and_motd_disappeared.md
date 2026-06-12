---
title: "Upgraded to Karmic, and motd disappeared"
date: 2009-12-28
forum: Server Platforms
---

### Post by BKonkle on 2009-12-28
Quick question - I upgraded from Jaunty server to Karmic server over the weekend, and now my motd is not displaying upon SSH connect.  The last login displays, but /etc/motd is not displayed.  In /etc/pam.d/login the motd line reads "session    optional   pam_motd.so ", which should be correct.  I'm not sure where else to go to troubleshoot.  Any ideas?

---

### Post by slakkie on 2009-12-28
Check your sshd_config:

Banner /etc/issue.net

---

### Post by BKonkle on 2009-12-28
Thanks!  That's what the problem was, apparently.  The 'Banner' line was commented out.  When I uncommented it, it printed the contents of /etc/issue.net.  I changed the line to 'Banner /etc/motd', and it gave me exactly what I wanted.

Thanks!

---

