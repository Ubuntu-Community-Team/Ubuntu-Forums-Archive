---
title: "Simple file- and printer sharing..."
date: 2005-04-14
forum: Server Platforms
---

### Post by mark on 2005-04-14
MODS - As usual, I'm not sure if this is the right place - please move if not!

I have a desktop and a laptop, both running Ubuntu 5.04.  What I'm after is to be able to have my laptop print to the HP LaserJet 6P connected to my desktop and to be able to "browse" and share certain files between desktop and laptop (connected via a NetGear RP614 router/firewall).

I've done a couple of searches on the forum which seem to keep turning up bits about Linux/Windows sharing.  I've also done some research re: NFS and Samba, without coming up with a clear answer.  My questions are:

1 - How can I, as easily as possible, set up "Network Neighborhood"-type connections in Ubuntu?

2 - Can Samba be used for Linux-to-Linux?  Or is it strictly Linux-to-the-other-guys?

3 - Linux-to-Linux printer sharing?  IPP?  If so, how?

I'd love to find some GUI solution - but I can manually edit config files.  If the answers exist elsewhere I'd be glad to go fetch them - if someone can point the way.  As you can tell, I'm pretty ignorant about Linux networking (most of my LAN work was years ago, with NetWare) but I'm looking forward to learning...

---

### Post by wfx on 2005-04-15
This is not an easy step but i will try it:
Note:
If anything goes wrong dont hit me ;-)
I have not test any line here(it work but i user a other distro for my server)
Dont copy and paste any config edit it step by step.


I propose:
Domain: anchor (change it to anyone you like :-))
Network: 192.168.0.N

#1 SERVER SETUP:
Desktop as DHCP Server, Print Server (CUPS) and File Server(SAMBA)
IP: 192.168.0.1 (fixed)

#1.1 NETWORKING:

DHCP Config to share IP's on LAN:
```
option domain-name "anchor";
option domain-name-servers FIRST_OF_YOURE_ISP;
option domain-name-servers SECOND_OF_YOURE_ISP;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.10 192.168.0.80;
  default-lease-time 86400;
  max-lease-time 259000;
}
ddns-update-style ad-hoc;
``` 

Start up the dhcp server.
Ok, now laptop you should get an ip via dhcp client (test it)

#1.2 PRINT SERVER:
The configure youre cupsd.conf like this
Check where youre DocumentRoot folder is:
```

DocumentRoot /usr/share/cups/docs
LogLevel info
User lp
Group lp
Port 631
SystemGroup lp
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.
</Location>
<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.
#Encryption Required
</Location>

```

#1.3 FILE SHARING

```
[global]
        interfaces = 192.168.0.1/255.255.255.0
        bind interfaces only = yes
        smb passwd file = /etc/samba/private/smbpasswd
        dns proxy = no
        encrypt passwords = yes
        workgroup = ANCHOR
        server string = ANCHOR Server
        socket options = TCP_NODELAY
       SO_SNDBUF=8192 SO_RCVBUF=8192
        unix extensions = yes
        log file = /var/log/samba/log.%m
        bind interfaces only = yes
        os level = 20
        max log size = 50
        hosts allow = 192.168.0. 127.

[NAME_OF_THIS_VOLUME]
   comment = Public Share
   path = /PATH/TO/THE/PUBLIC/SHARE
   valid user = A_VALID_USER OTHER_VALID_USER
   public = no
   writeable = yes
   printable = no
   create mask = 0777

[NAME_OF_THIS_VOLUME]
   comment = Network directory of A VALID USER
   path = /PATH/TO/THE/USERS/DIRECTORY
   valid users = A_VALID_USER
   public = no
   writable = yes
   printable = no

[NAME_OF_THIS_VOLUME]
   comment = Network directory of OTHER VALID USER
   path = /PATH/TO/THE/USERS/DIRECTORY
   valid users = OTHER_VALID_USER
   public = no
   writable = yes
   printable = no
```

On youre Server the users (replace the name to the one you have or like):
A_VALID_USER and OTHER_VALID_USER

ok i hope it helps (i know im not very good in tutor writing).
and make of all files you change a backup (cp NAME NAME.MARK.BACKUP)

---

### Post by mark on 2005-04-16
wfx, thanks.  Hopefully I'll find time to try your suggestions this weekend.

However - is it just me or is this stuff more difficult than it should be?  I hate drawing comparisons but Windows-to-Windows F&P sharing is a lot easier...

Mark

---

### Post by wfx on 2005-04-18
>  Windows-to-Windows F&P sharing is a lot easier 
you are right.

Maybe with webmin it is easyer but im not sure.

---

