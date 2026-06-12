---
title: "ubuntu already with FTP Server?"
date: 2011-03-01
forum: Server Platforms
---

### Post by jaya28inside on 2011-03-01
Very strange... But I dunno who install the FTP Server in
my local Ubuntu.

If I run this command;
> $> sudo dpkg -s ftp 

It gives me this
> 
Package: ftp
Status: install ok installed
Priority: standard
Section: net
Installed-Size: 168
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: netkit-ftp
Version: 0.17-19build1
Replaces: netstd
Depends: libc6 (>= 2.11), libncurses5 (>= 5.6+20071006-3), libreadline6 (>= 6.0)
, netbase
Description: The FTP client
 ftp is the user interface to the ARPANET standard File Transfer Protocol.
 The program allows a user to transfer files to and from a remote network
 site.
Original-Maintainer: Alberto Gonzalez Iniesta <agi@inittab.org>


But, that makes me confused.
What FTP Server is this? ???

It's not VSFTPD,
nor ProFTPD...

Is there anyone already know this? My debian is Ubuntu Server, no interface, just command line, thanks.

---

### Post by arrrghhh on 2011-03-01
lol, it's not a server at all... look at the description:

**```
Description: The FTP client
```**

---

### Post by jaya28inside on 2011-03-03
> **arrrghhh said:**
> lol, it's not a server at all... look at the description:

**```
Description: The FTP client
```**

lol... yeah you're right...
it's not ftp server... 

i guess i didn't notice that tiny text.... lol.
so it's solved sorry! (^^'

if there's anyone who got the tutorial of how to 
use this ftp client named as I posted earlier...

please don't mind to post up the thread,
before i closed the thread. (^^'a

:P

---

### Post by bsntech on 2011-03-03
To use the FTP client, you have to use it at the command-line.

If you have a GUI installed, I'd recommend using filezilla.  Much easier to use.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

---

### Post by jaya28inside on 2011-03-03
> **bsntech said:**
> To use the FTP client, you have to use it at the command-line.

If you have a GUI installed, I'd recommend using filezilla.  Much easier to use.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

surely, yes it's all CLI (Command line interface) within my machine... no GUI. 

FileZilla is okay, i guess. yes, I done using it in windows,
nice one.

anyway, again... like I said previously, if 
somebody know about how to use that small tiny ftp clients that appeared at the first post (upper) than... share it, lol. :P

---

### Post by arrrghhh on 2011-03-04
> **jaya28inside said:**
> anyway, again... like I said previously, if 
somebody know about how to use that small tiny ftp clients that appeared at the first post (upper) than... share it, lol. :P

man ftp.

There's a couple of options, all explained in there.

---

### Post by jaya28inside on 2011-03-04
> **arrrghhh said:**
> man ftp.

There's a couple of options, all explained in there.

:P lol. ok, ya.

---

### Post by Lars Noodén on 2011-03-04
> **jaya28inside said:**
> surely, yes it's all CLI (Command line interface) within my machine... no GUI. 

FileZilla is okay, i guess. yes, I done using it in windows,
nice one.

anyway, again... like I said previously, if 
somebody know about how to use that small tiny ftp clients that appeared at the first post (upper) than... share it, lol. :P


If you have SSH working, then you already have SFTP available.  Filezilla is one graphical SFTP client.  There are many other [graphical clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients), some of which may already be installed on your system.

---

