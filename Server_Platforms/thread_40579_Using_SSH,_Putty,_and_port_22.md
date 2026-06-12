---
title: "Using SSH, Putty, and port 22"
date: 2005-06-09
forum: Server Platforms
---

### Post by echokilo on 2005-06-09
I just installed Ubuntu as a server and would like to login via SSH from another machine using putty.

How do I start SSH and make that port available?

---

### Post by BimberiDreamer on 2005-06-09
Hi,

Hopefully this will do the trick:

[http://www.ubuntuguide.org/#installssh](http://www.ubuntuguide.org/#installssh)

Cheers, Dave.

---

### Post by echokilo on 2005-06-09
Yeah, tried that. Unfortunately that link leads to a link that has nothing on installing SSH.

Anyone else?

---

### Post by kvidell on 2005-06-09
[QUOTE=echokilo]Yeah, tried that. Unfortunately that link leads to a link that has nothing on installing SSH.

Anyone else?[/QUOTE]
 sudo apt-get install openssh-server

```
5/kvidell: apt-cache show openssh-server
Package: openssh-server
Priority: optional
Section: net
Installed-Size: 608
Maintainer: Matthew Vernon <matthew@debian.org>
Architecture: i386
Source: openssh
Version: 1:3.9p1-1ubuntu2
Replaces: ssh (<< 1:3.8.1p1-9), openssh-client (<< 1:3.8.1p1-11)
Provides: ssh-server
Depends: libc6 (>= 2.3.2.ds1-4), libpam0g (>= 0.76), libssl0.9.7, libwrap0, zlib1g (>= 1:1.2.1), debconf (>= 1.2.0), libpam-runtime (>= 0.76-14), libpam-modules (>= 0.72-9), adduser (>= 3.9), dpkg (>= 1.9.0), openssh-client (= 1:3.9p1-1ubuntu2), lsb-base (>= 1.3-9ubuntu3)
Suggests: ssh-askpass, xbase-clients
Conflicts: ssh-nonfree (<< 2), ssh-socks, ssh2, sftp, rsh-client (<< 0.16.1-1)
Filename: pool/main/o/openssh/openssh-server_3.9p1-1ubuntu2_i386.deb
Size: 259550
MD5sum: 36f60f71f6bb9c6619a476e316ac96da
Description: Secure shell server, an rshd replacement
 This is the portable version of OpenSSH, a free implementation of
 the Secure Shell protocol as specified by the IETF secsh working
 group.
 .
 Ssh (Secure Shell) is a program for logging into a remote machine
 and for executing commands on a remote machine.
 It provides secure encrypted communications between two untrusted
 hosts over an insecure network.  X11 connections and arbitrary TCP/IP
 ports can also be forwarded over the secure channel.
 It is intended as a replacement for rlogin, rsh and rcp, and can be
 used to provide applications with a secure communication channel.
 .
 This package provides the sshd server.
 .
 --------------------------------------------------------------------
 .
 In some countries it may be illegal to use any encryption at all
 without a special permit.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by BimberiDreamer on 2005-06-09
[QUOTE=echokilo]Yeah, tried that. Unfortunately that link leads to a link that has nothing on installing SSH.[/QUOTE]Yes it was a little further up the page:
[B]
sudo apt-get install ssh[/B]

(installs both client and server)

Dave.

---

### Post by kvidell on 2005-06-09
[QUOTE=BimberiDreamer]Yes it was a little further up the page:
[B]
sudo apt-get install ssh[/B]

(installs both client and server)

Dave.[/QUOTE]
 > Description: Secure shell client and server (transitional package)
 This is a transitional package depending on both the OpenSSH client and
 the OpenSSH server, which are now in separate packages. You may remove
 it once the upgrade is complete and nothing depends on it.From apt-cache show ssh

Adding or removing it doesn't seem to do.. well.. anything.
- Kev

---

### Post by echokilo on 2005-06-09
Thanks, I'm all set now!

---

