---
title: "Linux hacked"
date: 2009-06-08
forum: Security
---

### Post by mack_guy911 on 2009-06-08
i just installed mint linux 7 which is based on ubuntu 9.4 distro 


my quest is what is difference in mint and ubuntu as security point of view 

and also wants ubuntu users review on this 

LINUX HACKED ](*,)

[http://forums.linuxmint.com/viewtopic.php?f=6&t=25416](http://forums.linuxmint.com/viewtopic.php?f=6&t=25416)


thanks to all :) for your kindness to take free time from your precious time and review..

---

### Post by kerry_s on 2009-06-08
i think security is the same.

like it says you should never run a server that is not properly secured, 1234 for a password, tops the list of things you should not do. ;)

---

### Post by lukjad on 2009-06-08
Well, the password is pretty important on the security level. :) 1234 doesn't cut the mustard anymore. ;)

---

### Post by bobince on 2009-06-08
> **mack_guy911 said:**
> and also wants ubuntu users review on this LINUX HACKED

Dude, that's a JavaScript alert() box. Any web page can open one. It is completely harmless.

If a third-party managed to inject JavaScript into the Mint forum without their permission, then that compromises the user accounts on that forum, but no more. If that's what's happened, then it's just another case of poorly-written PHP forum software that they haven't bothered keep up to date. Which is (sadly) not unusual, but is nothing to do with Linux.

---

### Post by bodhi.zazen on 2009-06-08
> **mack_guy911 said:**
> i just installed mint linux 7 which is based on ubuntu 9.4 distro 


my quest is what is difference in mint and ubuntu as security point of view 

and also wants ubuntu users review on this 

LINUX HACKED ](*,)

[http://forums.linuxmint.com/viewtopic.php?f=6&t=25416](http://forums.linuxmint.com/viewtopic.php?f=6&t=25416)


thanks to all :) for your kindness to take free time from your precious time and review..

If you read the thread you will see:

> I'm the son he is talking about, and i think this is because my dad has an openssh server on the pc and his pass was 1234.

It seems most of the "hacks" on these forums involve one of two "mistakes":

1. weak passwords.
2. unsecured servers (ftp, ssh, and vnc).

See the comments re: java script.

Otherwise read the security sticky :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by mack_guy911 on 2009-06-09
thanks guys for your replays 

:)

one more question by default i see samba server is enable i dont use windows to share files so i no need these services i disable them 

but one thing i wonder when i use zenmap on mintlinux 7 default before stoping samba it shows 

138 open Samba/NetBIOS port 

139 open Samba/NetBIOS port 

by default is that port open when i didnt disable samba service or block port by firewall i think it make very vulnerable to attacks in mintlinux by default for newbies 

is that same ubuntu 9.04 as well as well in default mode ?

i have used 8.10 and 8.04 they look pretty secure by default by closing all ports dont know about 9.04

---

### Post by cariboo on 2009-06-09
This is what I get when I run nmap on a default Jaunty install. 

```
nmap localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-09 11:14 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.13 seconds
```

As you can see 631 is open, but only to localhost. If I try to access it from any other system on the network, it won't open the cups web interface.

---

