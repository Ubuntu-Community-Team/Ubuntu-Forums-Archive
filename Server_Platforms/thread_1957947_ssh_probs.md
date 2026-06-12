---
title: "ssh probs ?"
date: 2012-04-13
forum: Server Platforms
---

### Post by naragam on 2012-04-13
Is there some way to figure out why my ssh/sftp sessions are being terminated even before I start, right after login? I know I have used my remote Linux cluster server earlier from my ubuntu PC and I can get there any time from my Windows PC using Windows ssh and ftp clients....TiA for any advise...

Nash

---

### Post by nothingspecial on 2012-04-14
*Thread moved to **Server Platforms**.*

---

### Post by newbie-user on 2012-04-14
Are you getting any error messages?

---

### Post by hawkmage on 2012-04-14
Also you can do is run the ssh command with the option -vv or even -vvv for verbose output from the ssh communication process.

---

### Post by enkay009 on 2012-04-14
Let's first identify if this is an SSH problem.

Can you login to machine without SSH (i.e. walk up to the machine and login to a TTY)?

To add to what newbie-user wrote, have a look at syslog (/var/log/syslog) on the sshd server give you any hints why the sessions are being cut short.

If you don't find any hints, then trying running sshd with the debug flag (-d) and check the log again.

---

