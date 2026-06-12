---
title: "Calling SSH PAM file - multiple servers"
date: 2014-03-09
forum: Server Platforms
---

### Post by izziere on 2014-03-09
I have two SSH servers set up along the lines in this thread: [http://ubuntuforums.org/showthread.php?t=1497376]("http://ubuntuforums.org/showthread.php?t=1497376")

I want different PAM files for each server (ie ssh referring to /etc/pam.d/sshd and sshd2 referring to /etc/pam.d/sshd2), but my sshd2 instance still follows /etc/pam.d/sshd

How do I get sshd2 to call the PAM file in /etc/pam.d/sshd2?

Thanks!

---

### Post by izziere on 2014-03-10
User error.  My /etc/init.d/ssh2 script was calling sshd rather than sshd2.

---

