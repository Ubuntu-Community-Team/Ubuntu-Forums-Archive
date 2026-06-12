---
title: "How do I?  NAS, Firewall, NAT, WebGUI?"
date: 2006-06-07
forum: Server Platforms
---

### Post by TwiceOver on 2006-06-07
This may really be a lot to ask.  If this is inappropriate for this forum, then just disregard.  I would like to roll all my misc. PCs all into one Ubuntu server to take care of some of my needs... and some things I don't need, but want :D

Here's some things I am looking for:

NAT/Firewall w/ web gui interface:
I currently use monowall and I really enjoy it.  It does everything I need it to, unfortunately it takes up an entire box.

NAS w/ Web GUI Interface:
Preferably IP accessible.  Have a Win2K box doing this now, thought about going FreeNAS but might as well try to roll this all into one!?

Radius Server:
This is an eventual project, not too worried about it now, but figured I would throw it in there.

FTP Server:
Virtual directories, user management, SFTP, Web GUI would be nice if it even exists.  

WebServer:
This is pretty well documented, I can probably figure this out on my own.

Mail Server:
This is also pretty well documented, so I'm not too worried here... This is an in the future type thing.


I hope I am not asking for too much.  I am willing to learn and also dive into the command line aspect.  I currently use Ubuntu Desktop for my primary desktop and was able to get my laptop working good enough with it to rarely log into Windows.  Again, if this long request is inappropriate please just disregard this post.

---

### Post by Iowan on 2006-06-07
Just my opinion...
I'd leave the firewall on the separate box - but maybe I'm fooling myself by thinking that another box provides an additional layer of security.
I also have a box set up pretty much as a NAS, although not NASLite or FreeNAS.  It's a small distro with Samba added.  But I also have a general-purpose box set up to provide many of the services you're proposing (including Samba to file-share.) 
[http://howtoforge.com/perfect_setup_ubuntu_5.10]("http://howtoforge.com/perfect_setup_ubuntu_5.10")

---

