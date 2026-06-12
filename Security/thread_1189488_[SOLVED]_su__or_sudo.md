---
title: "[SOLVED] su  or sudo"
date: 2009-06-16
forum: Security
---

### Post by neoforest on 2009-06-16
I've become comfortable starting terminal sessions with su command when root user permissions are required. This method is more convenient than having to run each command with sudo prefix.

It seems I have to give the root user a password in order to do this. Is giving the root user a password a bad idea? Is using su for the entire terminal session a security risk?

Any thoughts are appreciated.

---

### Post by lisati on 2009-06-16
You don't need to enable root or give it a password: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2009-06-16
There is no root account login in Ubuntu. It's disabled.

If you want a persistent root prompt, use ```
sudo -i
``` (Do not use *sudo -s*)

---

### Post by neoforest on 2009-06-17
Great specific answers.
The support here in ubuntuforums is fantastic.

Many thanks.

---

### Post by reddog4063 on 2009-06-18
Question:  why should we not use sudo -s? That is currently what I am using and I want to make sure I am doing things right. What makes sudo -i better/safer/more secure?


thanks,
Joe

---

### Post by aysiu on 2009-06-18
> **reddog4063 said:**
> Question:  why should we not use sudo -s? That is currently what I am using and I want to make sure I am doing things right. What makes sudo -i better/safer/more secure?


thanks,
Joe
With *sudo -s*, you might accidentally change ownership of your user files and settings to root.

With ```
sudo -i
``` you won't.

**More details** ```
username@mini-otter:~$ *sudo -s*
root@mini-otter:~# *$HOME*
[color=red]bash: /home/username: is a directory[/color]
root@mini-otter:~# *exit*
exit
username@mini-otter:~$ *sudo -i*
root@mini-otter:~# [I]$HOME
[/I][color=red]-bash: /root: is a directory[/color]
root@mini-otter:~# 
```

---

