---
title: "Access Samba shares from Win problem"
date: 2006-04-01
forum: Server Platforms
---

### Post by frio on 2006-04-01
Hello all. I am new to Linux but not new to networking, although I am far from an expert.

First a little about my setup.
[LIST]
[*]This is part of a home network
[*]Experimental Ubuntu Toshiba a75-s229 laptop using wireless w/ WPA, hostname tlt1-linux (currently dual boot w/ WinXP pro)
[*]Win 2003 server using NTFS, hostname svr1 (this is what I plan to replace with Ubuntu, as a minimum)
[*]D-link DI-624 Router
[*]I am using hosts and lmhosts for name resolution. This seems to work fine when I ping by hostname.
[/LIST]
Ok, here is my issue.
Using Samba, I can access Win shares without issue from Ubuntu. I can also access Ubuntu shares from Win but ONLY after pinging Win from Ubuntu. Even then, after some time of inactivity, I lose connectivity and have to re-ping Win. I can then access the Ubuntu shares from Win.

I verify this with 'ping tlt1-linux /t' from svr1. I get timeouts until I send a ping to svr1 from tlt1-linux. Pretty much immediately, I start to get returned packets and can then access the Ubuntu shares...???](*,) 

Here is my smb.conf file:
```
[global] 
    workgroup = homenet
    server string = Samba Server on TLT1
    security = user
    browsable = yes
    local master = yes
    wins support = no
#    name resolve order = lmhosts bcast host wins

### Logging ###
    log file = /var/log/samba/log.%m
    max log size = 1000

### Authentication ###
    security = user
    encrypt passwords = yes
    passdb backend = tdbsam guest
    obey pam restrictions = yes

### Misc ###
    socket options = TCP_NODELAY

### Shares ###
[homes] 
    guest ok = no 
    browsable = no
    writable = yes
[temp] 
    path = /tmp
    public = yes
    comment = Test share...
    available = yes
    browseable = yes
    writable = yes
[tlt1-sharedvolume] 
    path = /media/hda6/tlt1-share
    public = yes
    comment = Shared Volume on TLT1
    available = yes
    browseable = yes
    writable = yes

```
Any suggestios?
Thanks in advance for any replies.

####################################
An update... I have realized since posting this that while I am pinging Ubuntu from Win, and getting no response, that if I connect to a Win share from Ubuntu, packets start getting returned to Win and I can access Ubuntu shares. It is almost as if Samba is sleeping until it makes an outgoing connection and then it allows incoming connections.

---

### Post by frio on 2006-04-08
Has anyone been able to duplicate this...?? I have had no luck in figuring out why this is happening and it has to be resolved before I can even consider replacing the windows server with Ubuntu.

---

### Post by frio on 2006-05-04
Since no one answered this I figured it was fairly unique so I decided to take the chance and install Ubuntu on the server (scrapping Windows Server). This time I read AND followed the How To's in the Samba docs. This led me to using Wins whereas I was using hosts, lmhosts before.
 
File sharing and browsing has never worked better (or as fast). I now have another question that I'll post in a new thread...
 
Frio

---

### Post by frio on 2006-05-09
This post from **javiwwweb** cured the last problem with all this...
 
[http://www.ubuntuforums.org/showthread.php?p=479798#poststop]("http://www.ubuntuforums.org/showthread.php?p=479798#poststop")

---

