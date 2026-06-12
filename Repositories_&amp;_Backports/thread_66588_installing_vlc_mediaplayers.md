---
title: "installing vlc mediaplayers"
date: 2005-09-17
forum: Repositories &amp; Backports
---

### Post by ravalox on 2005-09-17
I am trying to install a few media players with apt-get and it does not seem to want to cooperate.  I went  to videolan.org and followed their instructions([http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)) and added their apt repository to me /etc/apt/sources.list, then updated (apt-get update) and when I attempt to install:
```
@mediaserv:~$ sudo apt-get install vlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc
``` 

Is what the system gives me.  How do I make apt-get see the files I need it to see?

---

