---
title: "[SOLVED] Apt-cacher question"
date: 2008-10-22
forum: Server Platforms
---

### Post by bigbrovar on 2008-10-22
I have apt-caher installed in the school where i work. its based on and installed on a ubuntu hardy heron server and the clients are also hardy heron based. apt-cacher is an awesome tool that help save the school bandwidth and time.now that ibex is in the coner and i will be migrating some system to ibex. i was wondering if its possible to use one apt-caher server with multiple  ubuntu releases. for example is it possible to use the same apt-caher with ibex based clients when it is released. thanks in advance

---

### Post by bigbrovar on 2008-10-23
It seems to have worked .. all i did was picked the old source.list for hardy and replaced ever instance of hardy  with intrepid. when i reloaded everything worked. am updating now i will post here how things go.

. my main concern and fear is for the apt-cacher cache on the server side should not get corrupted by the mixture of packages btw hardy and intrepid. .. but i doubt if that would be any problem since i have many PPA repos mapped on the apt-cacher. and so far there has been no problem whatsoever.

---

### Post by bluelightav on 2008-10-31
I am wondering if the Hardy and Ibex packages should be in different folders. How does a Hardy client know what is a Hardy package and not a Ibex one?

---

