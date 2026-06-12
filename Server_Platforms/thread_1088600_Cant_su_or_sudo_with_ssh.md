---
title: "Cant su or sudo with ssh"
date: 2009-03-06
forum: Server Platforms
---

### Post by twooton on 2009-03-06
I just set up a new linux server with the latest server release. When I go to ssh into the computer remotely, I log in with the administrative user your first set up. They I try to switch to root with su, which asks me for the password. When I enter the password it says auth failed. Then i try sudo su root, or sudo su, and nothing happens at at, its acts as if I just hit the enter button with no command present. Everything works fine when try to su on the server itself (without ssh). Any ideas?

---

### Post by threetimes on 2009-03-06
You shouldn't use [FONT=Courier New]su[/FONT] with ubuntu, just use [FONT=Courier New]sudo *command*[/FONT]

---

### Post by genset on 2009-03-06
try using sudo -i
it gives u a root shell

---

### Post by matey3 on 2009-03-06
I think you should first passwd root then do su or sudo.
usually if you take the default install, linux does not allow you to create root login, if you take the advanced setup (F6) when booting with the CD then it will allow you.
seems like the root has not been setup yet?

---

### Post by cdenley on 2009-03-06
> **twooton said:**
> Then i try sudo su root, or sudo su, and nothing happens at at, its acts as if I just hit the enter button with no command present.
Are you sure you don't have a root shell now. After you enter your password once, by default you won't be prompted for it again until after 15 minutes.
```

sudo su
whoami

```
The su command, when not run as root, prompts for the root password. There is no root password in ubuntu for security reasons.
> 
I think you should first passwd root then do su or sudo.

No, he shouldn't.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

