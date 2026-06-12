---
title: "bind mounts from fstab in dapper"
date: 2006-10-16
forum: Server Platforms
---

### Post by AhYup on 2006-10-16
Hello

So running postfix in Ubuntu server we need to use saslauthd with postfix. As postfix runs chrooted we need a way for it to communicate properly. 

A bind mount seems to be the best way to do this. 

So we stuck this line in fstab. 

Under Breezy it worked fine. But for some reason when using Dapper to build a mail server it breaks. Or at least it no longer mounts on boot. If the power goes down I need to log in and mount it manually. 

Would anybody know why this won't mount from fstab under Dapper? has something changed?

---

