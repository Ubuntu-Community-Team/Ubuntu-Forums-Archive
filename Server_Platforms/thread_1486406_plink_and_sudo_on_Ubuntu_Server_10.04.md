---
title: "plink and sudo on Ubuntu Server 10.04"
date: 2010-05-17
forum: Server Platforms
---

### Post by shadowwyvernx on 2010-05-17
Hello,

I wish to be able to remotely wake up/suspend my system running Ubuntu server, ostensibly from my Windows desktop.  I have Wake on Lan working very nicely for waking up, but am having difficulty with sleeping. I am loosely following [this]("http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html") guide.

I am using plink on Windows to issue the command "sudo pm-suspend" to the system as my user (shadowwyvern), like this:

```
plink shadowwyvern@server "sudo pm-suspend"
```

It connects fine, and prompts for password, then again for the password for sudo.  Seeking a way around this little problem, I added this line to /etc/sudoers (on the advice given [here]("http://ubuntuforums.org/showthread.php?t=680312")):

```
shadowwyvern ALL= NOPASSWD: /usr/sbin/pm-suspend
```

This does not work however.  I understand that line to mean that user shadowwyvern can run for any host the command "/usr/sbin/pm-suspend" without a password.

Why does that line not work, and what is the correct one?  Do I need to do anything since this is run over plink (which apparently does not open a tty - needed the line "Defaults visiblepw" in sudoers to ever get this far...)?

Thanks for the help :)

---

