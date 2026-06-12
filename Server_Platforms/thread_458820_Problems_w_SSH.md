---
title: "Problems w/ SSH"
date: 2007-05-30
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-05-30
Installed open-ssh on ubuntu server edition

```
sudo apt-get install openssh-server openssh-client
```

When I try to log in I get the prompt to enter the username.  No matter which account I use it always gives me the wrong password prompt.  Accounts that I can log into on the machine I cannot use to log in remotely.  I didn't not have this problem with my fedora box - I was wondering if anyone had an ideas.

Thanks in advance

---

### Post by hartz on 2007-05-30
Please give some more info on your problem.  Detail your network, how are you doing the remote login, etc.

Have you tried
```
ssh -l *username *localhost
```

---

### Post by MJN on 2007-05-30
Check for an **AllowUsers** directive in **/etc/ssh/sshd_config**
 
If specified then only those users listed will be allowed to log in.
 
The **/var/log/auth.log** logfile ought to shed some light also.
 
Mathew

---

### Post by turinglabs on 2007-05-30
> **Dudsmacka2 said:**
> Installed open-ssh on ubuntu server edition
When I try to log in I get the prompt to enter the username.  No matter which account I use it always gives me the wrong password prompt.  Accounts that I can log into on the machine I cannot use to log in remotely.  I didn't not have this problem with my fedora box - I was wondering if anyone had an ideas.


By default, the ssh client will try to login with your current user. You can specify a different one with the '-l' switch, as hartz indicated, or as 'ssh username@hostname'.  There are lots of things that can cause SSH login failures, from disabling password authentication, to improper permissions. Are you trying to use key-based authentication, or just simple password auth? 

Try 'ssh -v username@hostname' and post the output (or use '-vv' for even more output, just beware if you are posting a public IP address, you might want to edit the output first).

---

