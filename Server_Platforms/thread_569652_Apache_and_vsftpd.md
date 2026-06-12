---
title: "Apache and vsftpd"
date: 2007-10-07
forum: Server Platforms
---

### Post by Jeff Gaines on 2007-10-07
I have just installed Ubuntu 7.04 Desktop which I want to use as a server for my home network.
I have Apache, samba, php and vsftpd installed. Apache works in that I get the 'It Wordks!' page when I use a browser from a machine on the network.
I want to upload a web site from another machine and I'm not sure what the 'proper' way to do it is.
Ideally I would just use ftp and put it straight in the Apache directory. Is this the 'correct' way? What permissions do I need to set so that I can point my ftp app on another machine directly to this directory?

---

### Post by HermanAB on 2007-10-07
The easiest way is to create a new user with his home directory set to the exact directory where you wish to upload to.  Then when you do a default vsftpd install, you can simply log in with FTP and you are right there, ready to do your damndest.

Be sure to specify long passwords of at least 9 characters for *all* users on a Linux system.

Cheers,

H.

---

