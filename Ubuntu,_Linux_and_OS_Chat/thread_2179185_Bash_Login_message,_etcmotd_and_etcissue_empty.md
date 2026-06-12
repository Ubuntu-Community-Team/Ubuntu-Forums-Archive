---
title: "Bash Login message, /etc/motd and /etc/issue empty"
date: 2013-10-07
forum: Ubuntu, Linux and OS Chat
---

### Post by amarshat on 2013-10-07
All the terminals I open in my workstation, either by ssh or a gnome-terminal, show me a message saying,

```
Your computer is hacked, please contact some@email.com to resolve it...
```.

I checked my motd and issue files in /etc/, and they look plain and simple, 

/etc/motd

```
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-32-generic i686)

 * Documentation:  https://help.ubuntu.com/


New release '12.04 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

```

/etc/issue
```
Ubuntu 11.10 \n \l
```


The reason I am using 11.10 is, our product currently supports development on that version.

Can anyone direct me to fix this message, as I think someone might have just messed up with my system, while I left it logged-on unattended.

---

### Post by amarshat on 2013-10-07
It was .bashrc, I found it.

---

### Post by cariboo on 2013-10-07
You may want to have a look at your development model, support for 11.10 ended in May 2013, that means that there aren't any security updates any more. We don't recommend any one use unsupported versions. 12.04 plus point releases are supported until 2017.

---

