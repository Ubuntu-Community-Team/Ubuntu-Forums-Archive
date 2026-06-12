---
title: "Back to Square -1"
date: 2009-12-10
forum: Server Platforms
---

### Post by Vegan on 2009-12-10
OK, lets see, got LAMP working nominally on the new disk.

Problems:

1) Telnet is still being refused, FTP and HTTP are operational on the LAN

Backing up /home has been awkward. Can SAMBA be configured to make this easier to access on the LAN.

Also is SAMBA able to support ISP like serving with a browser so I can perhaps backup more easily that way?

I noticed last night this forum was down due a SQL error message, but obviously a backup/repair was successful.

On the CD there is this cloud, I have avoided it for now.

---

### Post by jonabyte on 2009-12-10
have you added /home as a share for other computers on the network to see it?

---

### Post by sndnichols on 2009-12-10
Have you thought of WebDav? [http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10-p2]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10-p2")

---

### Post by Vegan on 2009-12-10
My German is a tad rusty for that product.

I was thinking about using Samba setup to use "home" directories.

I was thinking instead of a single folder asssigned to nobody:nogroup was a cludge that did not work as well as I wanted.

So I am thinking of user accounts and set Samba to use /home folders.

Still having telnet problems, connection refused even though ftp and http and working.

**I noticed this site was sick too, seems I am not the only one with headaches.**

---

### Post by Vegan on 2009-12-10
So I now have all of the user accounts setup manually. I have also defined a /home/*/www with a default index.html in them.

I also have set the www directories to 777 so that apache will not choke.

So any thoughts on vsftp for supporting user logins.

---

