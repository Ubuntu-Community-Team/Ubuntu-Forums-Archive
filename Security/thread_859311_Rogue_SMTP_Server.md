---
title: "Rogue SMTP Server?"
date: 2008-07-14
forum: Security
---

### Post by oxsyn on 2008-07-14
I'm running Ubuntu 8.04 Server.  I have not installed an SMTP server on it.  From another computer, if I nmap the server, i see: 

> f4rr4r@poisontongue:~$ nmap runcible

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-07-14 11:05 MDT
Interesting ports on runcible.anarchia (192.168.1.3):
Not shown: 1708 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.180 seconds
f4rr4r@poisontongue:~$ 

Those are all expected.

However, if I nmap the machine locally, I see:

> f4rr4r@runcible:~$ nmap localhost

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-07-14 11:06 MDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1707 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.089 seconds
f4rr4r@runcible:~$ 

Note the SMTP server.  If I try to connect to port 25 remotely, the connection is refused.  If I try locally, I see:

> f4rr4r@runcible:~$ nc localhost 25
220 runcible ESMTP Exim 4.69 Mon, 14 Jul 2008 11:07:28 -0600

f4rr4r@runcible:~$ 

So, apparently my server is running Exim, only I didn't install it.  If I check the /etc/init.d/ directory, I see the exim4 daemon.  However, apt-show-versions says that exim4 is not installed.

> f4rr4r@runcible:~$ sudo apt-show-versions exim
exim not installed
f4rr4r@runcible:~$ sudo apt-show-versions exim4
exim4 not installed
f4rr4r@runcible:~$ 

I am experiencing something funky here?  Is exim4 built into Ubuntu and impossible to remove?  Hmm.  Help!? :p

---

### Post by Titan8990 on 2008-07-14
Exim can be installed during installation of the OS. Just try apt-get remove --purge exim4 or exim4-daemon-heavy.

---

### Post by oxsyn on 2008-07-14
> **Titan8990 said:**
> Exim can be installed during installation of the OS. Just try apt-get remove --purge exim4 or exim4-daemon-heavy.

Tried, didn't work.

> f4rr4r@runcible:~$ sudo apt-get remove --purge exim4
[sudo] password for f4rr4r: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package exim4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
f4rr4r@runcible:~$ sudo apt-get remove --purge exim4-daemon-heavy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package exim4-daemon-heavy is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
f4rr4r@runcible:~$ 


> f4rr4r@runcible:~$ nmap localhost

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-07-14 12:45 MDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1707 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.093 seconds
f4rr4r@runcible:~$ 


---

### Post by brian_p on 2008-07-14
> **F4RR4R said:**
> I'm running Ubuntu 8.04 Server.  I have not installed an SMTP server on it.

I bet you did.

---

### Post by brian_p on 2008-07-14
> **F4RR4R said:**
> Tried, didn't work.

```
sudo apt-get remove --purge exim4-base
```

---

