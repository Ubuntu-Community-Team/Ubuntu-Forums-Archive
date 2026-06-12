---
title: "gnome screenshot tool communicates over network interface"
date: 2006-05-02
forum: The Cafe
---

### Post by PatrickMay16 on 2006-05-02
I have a small network activity monitor on the gnome panel and it lights up with activity when running gnome screenshot. This kind of worries me, is it possible that I've been rooted? Or what else could be happening here?

---

### Post by aysiu on 2006-05-02
Maybe it's related to [this bug that I filed a while ago](https://launchpad.net/distros/ubuntu/+source/gnome-keyring-manager/+bug/39239).

---

### Post by towsonu2003 on 2006-05-02
[QUOTE=PatrickMay16]I have a small network activity monitor on the gnome panel and it lights up with activity when running gnome screenshot. This kind of worries me, is it possible that I've been rooted? Or what else could be happening here?[/QUOTE]
try to catch what's connecting with ```
sudo lsof -i -n
``` while taking a screenshot and seeing your lights on. 

lsof -i -n will spit out all the processes that (sort of) connect to the net. output will include ip addresses. if you wanna see domain names instead, remove the -n from the command.

---

### Post by GeneralZod on 2006-05-02
Is it definitely the network interface, or could it be the loopback one?

Make sure no proper network activity is happening, then type

```

cat /proc/net/dev

```

start up gnome-screenshot/ whichever activity you are suspicious of and wait a while; close it, and do

```

cat /proc/net/dev

```

and see which numbers have changed.

---

### Post by PatrickMay16 on 2006-05-02
Here's some results:
```

patrick@ubuntu:~$ sudo lsof -i -n 
COMMAND    PID    USER   FD   TYPE DEVICE SIZE NODE NAME
cupsd     7592  cupsys    0u  IPv4  11038       TCP 127.0.0.1:ipp (LISTEN)
cupsd     7592  cupsys    4u  IPv4  39919       TCP 127.0.0.1:ipp->127.0.0.1:517
61 (ESTABLISHED)
hpiod     7621   hplip    0u  IPv4  10952       TCP 127.0.0.1:32770 (LISTEN)
hpiod     7621   hplip    2u  IPv4  10955       TCP 127.0.0.1:32770->127.0.0.1:4
4578 (ESTABLISHED)
python    7668   hplip    4u  IPv4  11045       TCP 127.0.0.1:32771 (LISTEN)
python    7668   hplip    5u  IPv4  11050       TCP 127.0.0.1:44578->127.0.0.1:3
2770 (ESTABLISHED)
master    7852    root   11u  IPv4  11302       TCP 127.0.0.1:smtp (LISTEN)
nmbd      7961    root    6u  IPv4  11556       UDP *:netbios-ns 
nmbd      7961    root    7u  IPv4  11557       UDP *:netbios-dgm 
nmbd      7961    root    8u  IPv4  11559       UDP 192.168.0.88:netbios-ns 
nmbd      7961    root    9u  IPv4  11560       UDP 192.168.0.88:netbios-dgm 
smbd      7965    root   20u  IPv4  11642       TCP *:microsoft-ds (LISTEN)
smbd      7965    root   21u  IPv4  11643       TCP *:netbios-ssn (LISTEN)
gnome-cup 9433 patrick   16u  IPv4  39918       TCP 127.0.0.1:51761->127.0.0.1:i
pp (ESTABLISHED)
gnome-vfs 9449 patrick   50u  IPv4  63033       TCP 192.168.0.88:45618->192.168.
0.222:netbios-ssn (ESTABLISHED)
gnome-vfs 9449 patrick   54u  IPv4  63035       UDP *:32807

```
I notice some connection with 192.168.0.222, my brother's computer.
I shall try your recommendation now, GeneralZod, to determine if it is the loopback interface or not.

---

### Post by towsonu2003 on 2006-05-02
I filtered out ones that do not deal with loopback, for your viewing pleasure:
[QUOTE=PatrickMay16]
COMMAND    PID    USER   FD   TYPE DEVICE SIZE NODE NAME
**nmbd**      7961    root    6u  IPv4  11556       UDP *:netbios-ns 
nmbd      7961    root    7u  IPv4  11557       UDP *:netbios-dgm 
nmbd      7961    root    8u  IPv4  11559       UDP 192.168.0.88:netbios-ns 
nmbd      7961    root    9u  IPv4  11560       UDP 192.168.0.88:netbios-dgm 
**smbd**      7965    root   20u  IPv4  11642       TCP *:microsoft-ds (LISTEN)
smbd      7965    root   21u  IPv4  11643       TCP *:netbios-ssn (LISTEN)
**gnome-vfs** 9449 patrick   50u  IPv4  63033       TCP  92.168.0.88:45618->192.168.0.222:netbios-ssn (ESTABLISHED)
gnome-vfs 9449 patrick   54u  IPv4  63035       UDP *:32807
[/QUOTE]
unfortunately, I'm not sure what these services are (none of them is gnome-screenshot, that's for sure), so you'll need to wait for a more experienced user :)

in the meantime, with this many services, I'd recommend you to have a firewall (firestarter).

---

### Post by endersshadow on 2006-05-02
This probably has to do with gnome-screenshot trying to find a place to save it and scanning your network for any remote harddrives that you're connected to.  It's a guess, but I figure that's the only thing it could be...

---

