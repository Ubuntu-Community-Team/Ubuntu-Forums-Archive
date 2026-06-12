---
title: "Initialize session to Repository before apt-get"
date: 2006-09-03
forum: Repositories &amp; Backports
---

### Post by Gooldux on 2006-09-03
Hi, 

I'm encountering problems when browsing the Repositories. 
It starts here : 
```

sudo apt-get update
0% [Connecting to be.archive.ubuntu.com (1.0.0.0)]
...

```

I have the same timeouts when connecting to archive.ubuntu.com, security.ubuntu.com or be.security.ubuntu.com.

BUT, I found out that when I first open FireFox on ex. [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) before I run apt-get update, everything is ok for apt-get (or any other package manager).

So, it seems that I firts need to init a connection to repository with FireFox before I am able to work with any of the package managers.

My problem is that I don't know enough yet to start investigating on this
problem. 

The fact that I was forced to setfirefox param network.dns.disableIPv6 on true could be the cause or related.


Thank for helping me out of darkness.

---

### Post by mssever on 2006-09-03
It appears that the system DNS resolver isn't doing appropriate lookups, but Firefox is. Firefox's results are cached, so other programs don't have to do a lookup. This is indicated by the apt-get output. 1.0.0.0 isn't a valid IP address.

What happens if you ping the servers? Do you get a real IP address then? Also try nslookup servername.

---

### Post by intux on 2006-09-06
Hi, 

I've encountered the same problem.
Disableing IPv6 solved my internet speed conneciton issue but updates are still unreachable.
Moreover, ping on all IP address is possible.

I tried this :
[http://www.ubuntuforums.org/showthread.php?t=251419](http://www.ubuntuforums.org/showthread.php?t=251419)
disable DHCP and set up a static IP address manually for my Linux computer.
But the problem is still there.

Please, help !

---

### Post by mssever on 2006-09-06
Please post the results of doing ```
sudo apt-get update
```

---

### Post by intux on 2006-09-06
intux@intuxbox:~$ sudo apt-get update
Password:
0% [Connexion à archive.ubuntu.com (1.0.0.0)] [Connexion à security.ubuntu.com (1.0.0.0)...

and then no possible update.:(

---

### Post by mssever on 2006-09-07
Hmmm... What do you get from ```
nslookup archive.ubuntu.com
``` Apt-get is trying to use an incorrect IP address (1.0.0.0). It should be using one of 195.248.90.23 or 195.248.90.54. But the question is, is it just apt, or is it more widespread?

Anybody else have any ideas?

---

### Post by RoelCCU on 2009-04-01
same prob here

roel@CORE1:~$ sudo nslookup be.archive.ubuntu.com
Server:         192.168.2.1
Address:        192.168.2.1#53

Non-authoritative answer:
be.archive.ubuntu.com   canonical name = ubuntu.mirrors.skynet.be.
Name:   ubuntu.mirrors.skynet.be
Address: 195.238.1.5


roel@CORE1:~$ sudo ping 195.238.1.5
PING 195.238.1.5 (195.238.1.5) 56(84) bytes of data.

no reply .......

---

### Post by mssever on 2009-04-01
> **RoelCCU said:**
> same prob here
This thread is nearly three years old. You'll probably get better help if you start a new thread.

---

