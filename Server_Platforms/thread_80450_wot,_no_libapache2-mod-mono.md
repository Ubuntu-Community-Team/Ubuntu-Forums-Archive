---
title: "wot, no libapache2-mod-mono?"
date: 2005-10-22
forum: Server Platforms
---

### Post by David Marrs on 2005-10-22
Does anyone know if I can get hold of a libapache2-mod-mono package for ubuntu, or if the debian equivalent will work? I'm a bit disappointed that it's still missing from breezy (especially since it's the original mod-mono). It's starting to get tiresome being stuck on apache1.3 and I don't really want to have 2 httpds running simultaneously if I can help it. Any suggestions?

---

### Post by ScaryTom on 2006-04-25
I'm also interested in an answer to this. Anyone?

---

### Post by SigmaX on 2006-07-28
It's in Dapper; just use apt-get.

SigmaX

---

### Post by az on 2006-07-28
:~$ apt-cache search mod-mono
libapache-mod-mono - Run ASP.NET Pages on UNIX with Apache and Mono
libapache2-mod-mono - Run ASP.NET Pages on UNIX with Apache 2 and Mono
mono-apache-server - backend for mod_mono Apache module
mono-apache-server2 - backend for mod_mono2 Apache module


Both the apache1.3 and apache 2 versions are there.

Enable the universe repository and install it.

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

