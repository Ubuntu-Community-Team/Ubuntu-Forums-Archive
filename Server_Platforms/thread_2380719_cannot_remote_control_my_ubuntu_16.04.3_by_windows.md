---
title: "cannot remote control my ubuntu 16.04.3 by windows 10 computer?"
date: 2017-12-21
forum: Server Platforms
---

### Post by apwforeman on 2017-12-21
Hello, 

  I have use terminal command:
sudo apt-get install xrdp

to install ssh, but the screen just show some Grey and quit when I use windows 10 computer to telnet it.
So, what is the problem?
I have install:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update sudo apt-get install -y screen g++ libboost-all-dev subversion git-core python-
numpy

but still get Grey and Quit

THANKS

how to make my ubuntu support server verification?

---

### Post by howefield on 2017-12-21
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-12-21
For default ssh installation you need openssh-server, not xrdp package.

You can administer your linux server from windows using putty and ssh command line session.

---

### Post by apwforeman on 2017-12-21
by the way, can anyone tell me how to open teamviewer ?
I have double click the deb file 5 times, but no result when I search "teamviewer"(no icon provide me to double click)

---

### Post by apwforeman on 2017-12-21
where can i call activities in 16.04LTS

---

### Post by darkod on 2017-12-21
What are "activities in 16.04"?

---

### Post by LHammonds on 2017-12-22
During installation of Ubuntu Server 16.04, you are eventually presented with this option:

```
Set the following and press [COLOR=green]{ENTER}[/COLOR] to continue:
Uncheck - Manual package selection
Uncheck - DNS server
Uncheck - LAMP server
Uncheck - Mail server
Uncheck - PostgreSQL database
Uncheck - Samba file server
**Check** - standard system utilities (enabled by default)
Uncheck - Virtual Machine host
**Check** - OpenSSH server (allows us to use PuTTY after installation to connect to the server)
```
Make sure to place a checkmark beside "OpenSSH server" and you will be able to access it from any operating system using [PuTTY]("https://portableapps.com/apps/internet/putty_portable").
[Reference of install steps]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p446")

If you forgot to do this during install, issue the following command to install it:
```
apt-get install openssh-server
```

If you have the software firewall enabled on the server, you need to open port 22 to allow access to it.  Assuming your LAN is 192.168.1.xxx, here is an example of doing that with UFW:
```
ufw allow from 192.168.1.0/24 to any port 22 comment 'SSH via LAN'
```
or if using iptables directly:
```
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```
[Reference to my firewall management script]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p458")

LHammonds

---

