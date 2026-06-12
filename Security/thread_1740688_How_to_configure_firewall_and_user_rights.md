---
title: "How to configure firewall and user rights"
date: 2011-04-27
forum: Security
---

### Post by geekcalledsick on 2011-04-27
Hello,

I am novice user of linux. I need to know how to configure firewall so my system cant be compromised...

In windows my system was greatly compromised. keyloggers were installed without my approval and my desktop was taken on remote. 

What should I do so without my knowledge no software can be installed and i can close all ports and only open which ever port is required to open. What should i do so my desktop cant be taken on remote?

How do I configure user rights ? So except me no one can install any software. I will have another general user id for internet surfing.

Please advise...

---

### Post by cipherboy_loc on 2011-04-27
By default, no ports are open on the basic Ubuntu install. To check install nmap (**sudo apt-get install nmap**), and then run it:

```

nmap {computer-IP-address}

```If you create another user, you can revoke admin privlages. But "installing software" on Ubuntu the regular way won't do much good, as all the software is tested. Also, as for the firewall, forget it. It is configured by default. Linux is more secure than windows by default.

Cipherboy

---

### Post by spynappels on 2011-04-27
Linux is not Windows, it does not have ports opened/services listening by default, so you should be safe. 

Nothing can be installed without your permission, you will notice that to install packages you need to enter your sudo password. Just be careful to only install software from trusted sources and you should be fine.
 
You could also enable the built in firewall by running the following:

```
sudo ufw enable
```

Regarding your desktop being taken over, make sure that you do not have VNC enabled without a very strong password.

But generally, with a standard Desktop install, you are safe from most nasty stuff.

---

### Post by bodhi.zazen on 2011-04-27
Linux is not windows and is much more secure out of the box. In addition the threats to a linux desktop are not the same as to a window desktop.

Neither viruses or key loggers are significant threats to Linux, I suggest you read the security sticky.

---

