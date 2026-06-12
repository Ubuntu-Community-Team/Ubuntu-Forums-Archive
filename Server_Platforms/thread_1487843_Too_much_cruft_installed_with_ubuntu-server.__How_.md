---
title: "Too much cruft installed with ubuntu-server.  How to graefully remove it?"
date: 2010-05-19
forum: Server Platforms
---

### Post by paulgami on 2010-05-19
I'd like to remove some packages from a fresh default ubuntu-server install.  During the install I chose only "SSH server".

**dpkg --get-selections** tells me that all kinds of stuff is installed by default.  I don't want python, I don't want vim, I don't want some other things like rsync.  This is going to be a web server, why would I want NTFS support as standard, memtest86 or pppoeconf?

I started by trying to remove vim but it told me it would then break ubuntu-minimal which a little googling tells me is a required package.

Is it possible to get a minimal server system installed without extra cruft I don't want or need?

---

### Post by mnauman on 2010-05-19
If your server is a virtual then you could use jeos.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

---

### Post by stlsaint on 2010-05-19
To get a server edition smaller than ubuntu server, (as for as my knowledge goes) you will have to go virtualization. [http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)
OR
look into on server platform called proxmox.

---

### Post by paulgami on 2010-05-19
Thanks for the ideas.  I'll probably just go back to Debian which I know works.  This is my first real foray into Ubuntu on the server and, well, there's always Meerkat to look forward to ;)

---

### Post by windependence on 2010-05-19
Might want to have a try at FreeBSD and do a minimal install. There will be absolutely nothing you don't need there. This is what I use on all my web servers, and then just add the packages I need.

-Tim

---

### Post by paulgami on 2010-05-19
Again, that's not a bad idea.  The reason I had a look at Ubuntu is that it seems to be Debian++ and I like Debian, so...
I was also unable to get an SCP/SFTP client to connect in a satisfactory manner.  How do people using ubuntu to serve web pages copy files back and forth?  Samba?  Seems like the server version of Ubuntu was something of an afterthought.  NTFS and pppoe tools on a default server install?  Yikes.

---

