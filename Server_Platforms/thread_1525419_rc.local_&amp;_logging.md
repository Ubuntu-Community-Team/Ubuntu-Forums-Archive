---
title: "rc.local &amp; logging?"
date: 2010-07-06
forum: Server Platforms
---

### Post by mc2718 on 2010-07-06
What is the standard (=default) error logging location for commands executed from rc.local on ubuntu (9.04)? I thought ubuntu would automatically log all errors during boot to /var/log/boot but that file is in fact empty (except for a one-line message that states it is empty). I searched through everything in /var/log/* but none of the files there had indicated any errors with rc.local, even though commands in my /etc/rc.local did fail to execute. 

I did find out eventually why the commands failed (they did execute but quickly exited with some error) but it would have been loads easier to troubleshoot if error messages had been collected at some standard location. Or... am I just looking for them at the wrong place?

---

