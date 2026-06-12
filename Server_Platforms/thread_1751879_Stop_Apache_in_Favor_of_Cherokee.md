---
title: "Stop Apache in Favor of Cherokee"
date: 2011-05-07
forum: Server Platforms
---

### Post by jnorthr on 2011-05-07
Can anyone please advise if i can use Cherokee for my http service rather than Apache2 ? How do i stop apache2 from auto starting at reboot time ?

---

### Post by Lars Noodén on 2011-05-07
One way to stop the apache server would be to uninstall it.  The uninstallation process won't touch your data.

If you want to leave it in and just turn it off then one way is to use  [update-rc.d](http://manpages.ubuntu.com/manpages/natty/en/man8/update-rc.d.8.html) to turn it off for all run levels.

---

