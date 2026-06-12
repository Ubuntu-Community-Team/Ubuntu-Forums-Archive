---
title: "[SOLVED] lfd.log file changed permissions &amp; broke logcheck reporting"
date: 2014-08-18
forum: Server Platforms
---

### Post by gyzer on 2014-08-18
After getting spammed errors from logcheck (99.99% of them going to my junk folder) for over a month, I dug around to find out what was causing the issue with logcheck not able to send me reports. I found it was the lfd.log file. It had been working for quite sometime without issues. I found that the lfd.log file did have the secondary group of adm which I added the logcheck user into, but the adm user had no permissions to the file. After I have it read permissions to the lfd.log file everything started working again.

Any ideas on what might have changed the permissions on the lfd.log file? This system isn't running much on there outside of csf firewall, a ftp directory and a different sftp directory. I'm assuming this was some sort of automated processes but I'm not sure.

Any help with this would be greatly appreciated. I'd love to be able to prevent this in the future.

---

### Post by gyzer on 2014-09-05
I found that the issue was with logrotate. When it rotated the lfd.log file it lost read permissions from the adm group. I entered in a custom section into logrotate.conf and that did the trick.

---

