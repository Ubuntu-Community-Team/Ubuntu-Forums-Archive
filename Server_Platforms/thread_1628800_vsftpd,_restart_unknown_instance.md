---
title: "vsftpd, restart: unknown instance"
date: 2010-11-23
forum: Server Platforms
---

### Post by francesco.daguanno on 2010-11-23
I have installed **vsftpd**.
When I run the command [FONT="Courier New"]**[COLOR="DarkRed"]sudo service vsftpd restart[/COLOR]**[/FONT], I get the following response: [FONT="Courier New"]**[COLOR="DarkRed"]restart: Unknown instance[/COLOR]**[/FONT].
But if I run the command [FONT="Courier New"]**[COLOR="DarkRed"]sudo service vsftpd start[/COLOR]**[/FONT], I get the following response: [FONT="Courier New"]**[COLOR="DarkRed"]vsftpd start/running, process _3804_[/COLOR]**[/FONT].
To understand what is happening, I run the command [FONT="Courier New"]**[COLOR="DarkRed"]ps aux | grep vsftpd[/COLOR]**[/FONT], I get [FONT="Courier New"]**[COLOR="DarkRed"]root _3805_ 0.0  0.0 27120 620 ? Ss 14:00 0:00 usr/sbin/vsftpd[/COLOR]**[/FONT].

Why are different pids?
This is why the restart (and stop) do not work?

Thanks in advance.

---

### Post by builtbylane on 2011-01-15
Identical Problem here on Ubuntu 10.04.1 LTS.  is this an ubuntu issue or vsftpd?  


```
root     12024  0.0  0.0   6152   672 pts/0    S+   13:02   0:00 grep --color=auto vsftpd

```

---

### Post by rezsbc on 2011-02-16
I had the same problem here but doing:

```
sudo apt-get remove --purge vsftpd
```

and then reinstalling sorted it out.  Must have been something in my vsftpd conf.

p.s. builtbylane the process shown in your comment is the "grep" command itself not the vsftpd daemon.

---

### Post by eaonflux on 2011-07-25
Ah thanks dude,

Works like a charm, saved my alot of reinstalling time.
Gladly i looked first on this fora.

grts,

eaonflux

---

### Post by bludilnik on 2011-12-15
For me it was option "background=YES"  in /etc/vsftpd.conf file, that caused this problem.
Ensure that no vsftpd processes is running, comment "#background=YES" in /etc/vsftpd.conf and  start vsftpd service with " service vsftpd start" or "start vsftpd"

---

### Post by tomdagreek on 2012-03-07
same problem here.. using the --purge tag and redownloaded..
thanks

---

