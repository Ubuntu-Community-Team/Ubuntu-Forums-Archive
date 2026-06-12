---
title: "Maverick has the SSH port opened. Is it normal?"
date: 2011-04-21
forum: Security
---

### Post by nodnolse1 on 2011-04-21
[FONT="Lucida Sans Unicode"]Hi, I launched 'netstat -l -t' and I discovered that SSH was listening ... To be sure I made a 'nmap -sS -O' from a lan client and I discovered that my Maverick has the 22 port totally opened, I was shocked. At first because I have a firewall enabled ('Gufw 10.10.1'), set to close all incoming connections and ports. So how it is possible that Ubuntu leaves opened the SSH port, in more, who told to Ubuntu to start a SSH sever without ask me first seen that I don't use this service at all and opening the port making me attackable? Just for information,nmap with only the 22 port opened has discovered that was a Linux O.S. with the real kernel version ...  I believed that Ubuntu had security and privacy first of all, but I had only a false sense of security that is worst. I would like to inform that Debian by default closes all ports without installing firewall or others protection. I want specify that my system has all default settings, it is freshly installed, it is an Ubuntu 10.10 Maverick x64. Please, let me know the reason why Ubuntu put customers at security and privacy risk? [/FONT]

---

### Post by CharlesA on 2011-04-21
ssh server isn't installed by default on Ubuntu desktop. You'd have to install it, and add an exception in the firewall rules.

There are no listening services on a clean install of Ubuntu desktop (or server for that matter).

If you want it removed run this:

```
sudo apt-get purge openssh-server
```

---

### Post by nodnolse1 on 2011-04-21
I have not reason to assert a lie. I installed the OS from scratch two weeks ago, I have not installed applications that need a SSH server, in more I have installed the firewall set to close all ports. What exactly does the option 'purge'? It makes the SSH server to default setting? 

Thanks for answering, Paolo

---

### Post by CharlesA on 2011-04-21
It purges the package "openssh-server"

Is this a desktop or server install?

---

### Post by nodnolse1 on 2011-04-21
**Desktop**

Linux a 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux


Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

---

### Post by bodhi.zazen on 2011-04-21
> **nodnolse1 said:**
> I have not reason to assert a lie. I installed the OS from scratch two weeks ago, I have not installed applications that need a SSH server, in more I have installed the firewall set to close all ports. What exactly does the option 'purge'? It makes the SSH server to default setting? 

Thanks for answering, Paolo

Nobody is calling you a liar, and there is no need to over react. 

CharlesA was answering your original question:

> **nodnolse1 said:**
> [FONT="Lucida Sans Unicode"]Please, let me know the reason why Ubuntu put customers at security and privacy risk? [/FONT]

Port 22 is not open by default:

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

> No Open Ports

Default installations of Ubuntu must have no listening network services after initial install. 

You may also be interested in:

[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)

Most likely you, or someone else, installed openssh server at some point, perhaps as a dependency to something else.

Other possibilities would be that you are scanning the wrong IP or your router or who knows ?

Of course if is possible someone else installed it =)

What other open ports do you have ? Who else has physical or root access ?

Please use the default forms font / colors in future posts and please be respectful to those trying to help you sort this out.

---

