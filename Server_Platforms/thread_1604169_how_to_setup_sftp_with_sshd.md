---
title: "how to setup sftp with sshd"
date: 2010-10-23
forum: Server Platforms
---

### Post by K. Hendrik on 2010-10-23
Hi,
I've got a ubuntu server 10.04.1 running with ssh.

now i want to be able to access my home through ftp, also i need ftp access for to new users without admin rights and one new with admin. the normal users don't necessarily need ssh terminal access the admin and i do.
Also my home is encrypted ecryptfs (standard home folder encryption) if possible it should stay that way and the new users home should be too.
the new users should be able to create stuff in the ftp directory (backup directory for my sis and my bro)

the transmissions should be secure so i guess sftp with sshd should be used but i didn't find a good tutorial or howto for that.

Thx in advance
Hendrik1

---

### Post by BkkBonanza on 2010-10-24
Don't get confused between sftp and ftps. sftp is natively already available using ssh. That is, you don't have to do anything more to install it and it is fully secure by working over ssh. However, ftps is the old "ftp over ssl" protocol and requires installing an ftp server with ssl support and does not use ssh at all.

On Ubuntu sftp is already usable in Nautilus as long as the server has ssh running.

You just type in a path like **[NOPARSE]sftp://user@myserver:pwd/mypath[/NOPARSE]** and it will mount it. (If using keys rather than pwd then you can leave that out and the key agent will provide it). This is the easiest secure use mode. And you can create bookmarks to specific network locations for one-click use. However, this method does not provide for anonymous/public access. For that you may want to also install an ftp server, if that's what you need. 

sftp may also work with a "guest" account but I've never tried it that way for non-authenticated access.

The sftp access will auto-login using ssh and that should cause encrypted homes to mount. If you create a common ftp directory for backups and give it lenient permissions then all users could use it but it would be more secure to have user backups within their own /home so that other users can't get into their files. Or create separate backup folders with each user's permissions.

rsync is very useful for backups and also runs natively over ssh so that you can do this kind of thing, eg.

**[NOPARSE]rsync -vztpr /home/me me@server:pwd/backups/me[/NOPARSE]**

which will also auto-login over ssh and then run rsync to copy only changed files efficiently across the network.

---

### Post by HermanAB on 2010-10-24
Nautilus, File Menu, Connect to Server.  Select SSH protocol on port 22.

---

### Post by K. Hendrik on 2010-10-24
BkkBonanza:
ahh ok thx for the tip did'nt know i already had it running that way. I'll try if windows can connect too my relatives don't use linux ...

best,
Hendrik1

---

### Post by BkkBonanza on 2010-10-24
Windows clients can connect too as long as you use an sftp client like [WinScp]("http://winscp.net/eng/index.php"). I think putty also has an sftp client.

Don't use an "ftp/ftps only" client (unless you also setup an ftp server).

---

### Post by K. Hendrik on 2010-10-24
Ok, i don't need a public ftp and windows works too :D.
But what i forgot to mention i would like to limit the normal users to their home directory they shouldn't be able to browse the whole file-tree is that possibel (i know they only got write permission in home but the shouldn't even be able to viewthe others without changing the file permisions of every directory)?

---

### Post by BkkBonanza on 2010-10-24
I haven't had to do that myself so I'm not sure but I believe there is a sshd config option to do with chroot for that. I would use search on the forums here because I know I've seen it posted several times now. Or, wait, someone will likely chirp in about to limit sftp access. If in a hurry then **man sshd_config** may help.

---

### Post by K. Hendrik on 2010-10-24
I found this guide but i don't understand why he used / as home directory [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by BkkBonanza on 2010-10-24
That doesn't look right to me. He is changing his home to be / and modifying the user to use / as well. I would not do that. I'm busy at the moment but if Ic an shortly I'll find some better info and post a link here.

---

