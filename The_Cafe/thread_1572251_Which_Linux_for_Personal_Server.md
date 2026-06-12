---
title: "Which Linux for Personal Server"
date: 2010-09-10
forum: The Cafe
---

### Post by takisan on 2010-09-10
I'm in the process of doing a practically complete hardware swap between my systems, and I've hit a slight cache.

It seems almost useless to ask, but I'm wondering what Server Distro to put on one. I'm not thinking Mac OS X or Windows or OS/2 or some other eccentric choice, but I'm really going to want to think this through so as to have the best distro for what I'm going to be using it for:

[LIST]
[*]HTTP
[*]FTP
[*]Gopher
[*]Samba
[*]IMAP
[*]POP3
[*]SMTP
[*]IRC
[*]XMPP
[*]Telnet Chat and Telnet BBS
[/LIST]
Opinions Please!

---

### Post by Sporkman on 2010-09-10
> **takisan said:**
> a slight cache

:lol:

---

### Post by jerenept on 2010-09-10
FreeBSD.

That is all.

---

### Post by Dr. C on 2010-09-10
I use [gNewSense]("http://www.gnewsense.org/") for a personal server. All the traffic in and out of the network has to go through this server and is subject to inspection and / or blocking by this server running 100% Free Software. This can be useful when a propriety application or OS in the network wants to "call home" for example Microsoft Windows computer, a PS3, a Blu-ray player etc. It also provides a 100% clean system to catch any violation of Canada's privacy laws, and this may be very relevant under the proposed amendments to Canada's Copyright Act. 

The idea is to place 100% Free Software in a critical choke point.

---

### Post by sandyd on 2010-09-10
> **takisan said:**
> I'm in the process of doing a practically complete hardware swap between my systems, and I've hit a slight cache.

It seems almost useless to ask, but I'm wondering what Server Distro to put on one. I'm not thinking Mac OS X or Windows or OS/2 or some other eccentric choice, but I'm really going to want to think this through so as to have the best distro for what I'm going to be using it for:

[LIST]
[*]HTTP
[*]FTP
[*]Gopher
[*]Samba
[*]IMAP
[*]POP3
[*]SMTP
[*]IRC
[*]XMPP
[*]Telnet Chat and Telnet BBS
[/LIST]
Opinions Please!
any would be quite fine, really. lemme see....
http -apache
ftp - pureftpd/proftpd/vsftpd (pureftpd has low mem usage)
Gopher -pygopherd
Samba - Samba
IMAP/Pop3/SMTP - Courier/PostFix
[IRC - ircd-hybrid]("https://help.ubuntu.com/community/IrcServer")
XMPP - OpenFire??

all of this stuff is avalible on debian/ubuntu/gentoo

all of them use the same amount of resources with this configuration, unless you really squish the use flags with gentoo

---

### Post by jerenept on 2010-09-10
> **FineE said:**
> I use [gNewSense]("http://www.gnewsense.org/") for a personal server. All the traffic in and out of the network has to go through this server and is subject to inspection and / or blocking by this server running 100% Free Software. This can be useful when a propriety application or OS in the network wants to "call home" for example Microsoft Windows computer, a PS3, a Blu-ray player etc. It also provides a 100% clean system to catch any violation of Canada's privacy laws, and this may be very relevant under the proposed amendments to Canada's Copyright Act. 

The idea is to place 100% Free Software in a critical choke point.

[IMG]http://i70.photobucket.com/albums/i117/tallykat668/tinfoilhat.jpg[/IMG]

---

### Post by takisan on 2010-09-10
Well, I've decided on Ubuntu (no suprises, but I was looking for opinions), because 1). I've used Ubuntu Server Edition Before (but I didn't know how to configure it), 2) I like APT, and 3) having sudo pre-configured is a lot easier than having to configure it by editing the sudoers file.

---

### Post by jerenept on 2010-09-10
> **takisan said:**
> Well, I've decided on Ubuntu (no suprises, but I was looking for opinions), because 1). I've used Ubuntu Server Edition Before (but I didn't know how to configure it), 2) I like APT, and 3) having sudo pre-configured is a lot easier than having to configure it by editing the sudoers file.

well, the sig kind of gives it away.... but i still recommend freebsd.

---

### Post by Sporkman on 2010-09-10
I highly recommend Ubuntu Server - it's rock solid, and easy to configure.

---

### Post by kaldor on 2010-09-10
Ubuntu's a great choice on the server. 

FreeBSD and CentOS make great choices too.

---

