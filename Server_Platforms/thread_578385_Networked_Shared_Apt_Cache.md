---
title: "Networked Shared Apt Cache?"
date: 2007-10-17
forum: Server Platforms
---

### Post by regomodo on 2007-10-17
Is there anyone who knows how to do something like this in Ubuntu?

[http://wiki.archlinux.org/index.php/Network_Shared_Pacman_Cache](http://wiki.archlinux.org/index.php/Network_Shared_Pacman_Cache)

I used the NFS method in Arch as i couldn't get sshfs to work and it worked really well as my PC being the server and my laptop as the client. It made so much of a difference.

Do you think this guide will work just as well here?

---

### Post by /etc/init.d/ on 2007-10-17
[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

apt-proxy will let you share an APT cache between multiple machines.  It is available in the repos.

---

### Post by regomodo on 2007-10-18
Cheers for the link. I did a little more research into it and it looks like 1 hell of an undertaking just to share 1 folder

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

The only problem i can see with it is that if the client is not in the network it won't be able to install new apps as the sources.list will be wrong. At least that is how i see it.

I'm going to try the Arch method first.

---

### Post by regomodo on 2007-10-18
OK, it was fairly simple to do it with NFS

I've linked to my blog for my guide

[My Guide]("http://regomodoslinux.blogspot.com/2007/10/share-your-apt-cache-on-your-lan-with.html")

---

