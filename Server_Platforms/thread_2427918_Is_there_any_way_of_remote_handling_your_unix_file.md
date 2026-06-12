---
title: "Is there any way of remote handling your unix files like a local folder on a Windows"
date: 2019-09-27
forum: Server Platforms
---

### Post by MariosFFX on 2019-09-27
Hello!


I'm learning about Linux System Administration.
I have a Ubuntu 16.04 Server LTS, there's no GUI (I don't need one anyway) and I'm handling everything from a terminal and because I have to do "file hunting" and handling, for me terminal is not speedy enough.


For example let's say I want to configure my Bind9 DNS settings, the main configurations are:
```
/etc/bind/named.conf
/etc/bind/named.conf.options
/etc/bind/named.conf.local
```


so I'll have to do:


```
nano /etc/bind/named.conf
nano /etc/bind/named.conf.options
nano /etc/bind/named.conf.local
```
as long as I am logged in as root, if not logged in as root I'll have to use sudo as well.


and I've been thinking wouldn't it be nice, if there was any way to have remote access to all of my files in server?


For example:
I would like to use my Windows/Linux Machine and Visual Studio Code and treating those Linux files like they are a folder on my C:\ 


Is it possible?

---

### Post by LHammonds on 2019-09-27
You could use WinSCP and connect via SSH to Ubuntu Server like a file manager/browser.  But to manage files that requires root privileges can become a sticky matter.

You could configure samba shares to expose your files to Windows.  Map a network drive.

You could use NFS shares to expose your files to Linux.  Mount a folder as a share.

Keep in mind that configuring your system to expose system files decreases its security.

LHammonds

---

### Post by TheFu on 2019-09-27
You don't need to edit all of those.  You need to 
[B]sudo vim  /etc/bind/named.conf.local
[/B]
Then setup your zone files.

Nano is a terrible editor. Much to inefficient and it isn't available universally on all platforms.  Routers don't have nano, but they do have vi.  Watch an expert use vi for an hour to see the capabilities. Watching an expert in a terminal is sorta amazing to people who've never seen that as well.

IMHO, allowing Windows access to edit Unix system files is a terrible security risk.  No way would I allow that.

---

