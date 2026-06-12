---
title: "Repositories and browser problems"
date: 2004-12-21
forum: Repositories &amp; Backports
---

### Post by viboranegra on 2004-12-21
When I first installed Ubuntu I did not get any problems but know I have. When I try to activate the universe repositories in Synaptics, everytime I use Synaptics I see an error message saying:
```
Couldn't stat source package list http://archive.ubuntu.com
warty/universe Packages (/var/lib/apt/lists/
archive.ubuntu.com_ubuntu_dists_warty_universe_binary-
i386_Packages) - stat (2 No such file or directory)
```
This error occurs for every repository I try to add, using all the steps on Ubuntu guide.

Another thing that I suspect is related to the same problem is with internet browsers. It takes to long to load websites, it takes to long "resolving host". I tried to change IPv6 values using about:config on the browser but it doesn't help.

Any ideas?

---

### Post by bob k on 2004-12-21
[QUOTE=viboranegra]When I first installed Ubuntu I did not get any problems but know I have. When I try to activate the universe repositories in Synaptics, everytime I use Synaptics I see an error message saying:
```
Couldn't stat source package list http://archive.ubuntu.com
warty/universe Packages (/var/lib/apt/lists/
archive.ubuntu.com_ubuntu_dists_warty_universe_binary-
i386_Packages) - stat (2 No such file or directory)
```
This error occurs for every repository I try to add, using all the steps on Ubuntu guide.

Another thing that I suspect is related to the same problem is with internet browsers. It takes to long to load websites, it takes to long "resolving host". I tried to change IPv6 values using about:config on the browser but it doesn't help.

Any ideas?[/QUOTE]
 try  sudo apt-get update

---

### Post by viboranegra on 2004-12-21
Thanks. That solved the problem.

---

