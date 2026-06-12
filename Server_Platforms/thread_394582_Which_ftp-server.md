---
title: "Which ftp-server?"
date: 2007-03-27
forum: Server Platforms
---

### Post by rurp on 2007-03-27
I planing to set up a ftp-server and need some advice concerning which server I should chose. I do not have so much experiences from ftp but I have used proftpd on a Debian system a couple of years ago. Which server would you recommend and why?

Thanks for the help!

---

### Post by 1/0 on 2007-03-27
Uhhm, none. Not to sound mean or anything but I wouldn't install an FTP server. I'm running a few SSH servers on non-standard ports and that's much more safe. 

So my suggestion is to set up an SSH server. You can use gFTP, winSCP or whatever to access the server via SSH/SFTP and you'll be much more safe. Don't use standard ports use a port above 10000. That way you won't have a bunch of crack attacks a day. 

If you really need FTP, secure it the best you can.

---

### Post by Mr. C. on 2007-03-27
There is nothing wrong with an anonymous FTP server for download-only.

Good choices are vsftpd or proftpd.

MrC

---

### Post by m83 on 2007-03-27
Yes. vsftpd or proftpd are very good. vsftpd is really fast; way faster than proftpd, but proftpd is more configurable (think LDAP support, SQL support, bandwidth limiting for clients and more). Anyway, for simple setups vsftpd should be enough.

---

### Post by nix4me on 2007-03-27
There is nothing wrong with a properly configured ftp server.  I use proftpd with TLS/SSL security on a non-standard port.  There is also nothing wrong with using ssh/sftp on a properly configured server.

If ftp is the choice, I would recommend either proftpd, pureftpd or vsftpd in that order.  Vsftpd is the best for anon server and/or speed is critical.  Proftpd has the most configurable options and purefptd is in the middle.

nix4me

---

### Post by rurp on 2007-03-28
Thanks for your inputs.

---

### Post by Aberrix on 2007-03-28
another vote for proftpd

---

### Post by aparigraha on 2007-03-29
no discussion... glftpd

---

### Post by coxy on 2007-03-29
vsftpd using SSL/TLS for encryption is pretty easy to setup.

The Gentoo Wiki has a good HOWTO that you could have a look at.

[http://gentoo-wiki.com/HOWTO_vsftpd](http://gentoo-wiki.com/HOWTO_vsftpd)

---

### Post by astrogazer on 2007-03-29
Just one more commnet for glftpd since it was mentioned earlier.

It is the most versatile ftp server I have come across. How about running a different
script for each user when they log in? If you need features like this then look no further.
No wonder why lots of warez sites use this one.

For simpler(regular) tasks vsftpd and proftpd will do just fine.

---

