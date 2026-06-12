---
title: "Ubuntu Server Project for School.."
date: 2011-04-28
forum: The Cafe
---

### Post by cptrohn on 2011-04-28
Any advice LOL

I am setting up a network for a small charter school as a school project and am planning on using Ubuntu Server 10.04LTS as a headless server for a small network that will have 24 clients running Windows XP for some educational programs for the school.  There is no network printer, but they want SAMBA for file sharing and their will be no email host either.   They also want to be able to filter All Social Networking sites and limewire, frostwire etc (plus the pirates bay etc..)  which I think I can do effectively from the Integrated Services Router they use as an acess point.  Also they want to keep an image for the 24 PC's on the server so I am thinking of using Clonezilla since it is easy to use and they really don't have a full time Network Administrator on staff and don't have the money to contract out for support.

But any suggestions on any issues I might run into with the Server Edition?

---

### Post by jerenept on 2011-04-28
Problems you may run into:
1) Not using [FreeNAS]("http://freenas.org/").

Edit: I suppose I'm gonna have to back that up with evidence :P
*FreeNAS has a simple and convenient web interface.
*It supports SMB, FTP, AFP (apple ftp protocol), NFS (UNIX filesharing)
*Also RAID and multiple network cards 'out of the box'

Although some hacking is required to set it up as a proxy server (to filter out unwanted websites)

---

### Post by cptrohn on 2011-04-28
> **jerenept said:**
> Problems you may run into:
1) Not using [FreeNAS]("http://freenas.org/").

Edit: I suppose I'm gonna have to back that up with evidence :P
*FreeNAS has a simple and convenient web interface.
*It supports SMB, FTP, AFP (apple ftp protocol), NFS (UNIX filesharing)
*Also RAID and multiple network cards 'out of the box'

Although some hacking is required to set it up as a proxy server (to filter out unwanted websites)


I did consider using FreeNAS but the instructors  didn't want us to use it.. (reason why I don't know)

---

### Post by jerenept on 2011-04-28
> **cptrohn said:**
> I did consider using FreeNAS but the instructors  didn't want us to use it.. (reason why I don't know)

It may be because it's too easy, maybe you have to learn the command line?

Anyway, some problems you may see: None, really, as there are great guides both here, on the forums, as well as on the wiki.

---

### Post by juancarlospaco on 2011-04-28
If you are not PowerUser i suggest:

Clonezilla--->[http://redobackup.org/](http://redobackup.org/)

---

### Post by CharlesA on 2011-04-29
I thought Squid could filter sites. Might look into that.

---

### Post by Artemis3 on 2011-04-29
Yes, you can do that with Ubuntu, Freebsd, Freenas or many more distros just fine. It depends on your preference and experience of course.

For the ultra cheap, you could even just use opendns filtering. Of course samba can filter, with squidguard and/or dansguardian; with the added benefit of an actual web cache; but that means the server would also act as a gateway, firewall (transparent proxy), nat, etc. In addition to the samba service, which is pretty easy to do.

So for the super cheap (quick), use opendns in their router and set your box as a simple samba server only.

More advanced, set it up as gateway (between the router an LAN), and do all of the above. This requires more time to set up and test, or even maintain until you get it right.

Have fun!

---

