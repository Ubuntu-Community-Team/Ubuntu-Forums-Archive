---
title: "need a very lightweight server os [ubuntu server edition]?"
date: 2008-03-15
forum: Server Platforms
---

### Post by afeasfaerw23231233 on 2008-03-15
i need a super lightweight server os for my pentium 1 with 16 MB RAM. it  will be acted as a torrent and samba server. i don't mind using CLI without graphic. but i am a noob. so please give as many instructions as possible. is ubuntu server edition possible? but my low spec doesn't even meet the min. requirement. i have heard of rtorrent. will it be a most suitable torrent client? thanks
edit: i want to test with the virtualbox first.

---

### Post by leroy_30 on 2008-03-15
I would personally recommend:

[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")
[http://www.damnsmalllinux.org/wiki/index.php/Installing_MyDSL_Extensions]("http://www.damnsmalllinux.org/wiki/index.php/Installing_MyDSL_Extensions")

I have a Pentium 233 laptop w/ 96MB RAM and it installed and worked great.

---

### Post by afeasfaerw23231233 on 2008-03-15
i've just install dsl on my virtual box . which torrent client should i use?

---

### Post by TenPlus1 on 2008-03-15
rTorrent is a great text-based client, although the one in the repo's is a little on the old side...  Go here [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/) for the latest...

---

### Post by Iowan on 2008-03-15
I have a Samba server based on the [ Freesco]("http://www.freesco.org/") single-floppy router. It uses the 2.0 kernel to keep things small.

---

### Post by netlogic on 2008-03-16
16megs? wow. sorry, it isn't enough as a torrent server. rtorrent (best cli torrent client) requires least 12 megs if you are planning on 50 or more connection. if this must be done, try arch with the original bittorrent cli.

---

