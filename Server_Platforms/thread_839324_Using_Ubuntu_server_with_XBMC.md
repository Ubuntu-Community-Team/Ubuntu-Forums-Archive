---
title: "Using Ubuntu server with XBMC"
date: 2008-06-24
forum: Server Platforms
---

### Post by Svetgar on 2008-06-24
Will this software work with Xbox Media Center?

---

### Post by stokedfish on 2008-06-24
No, it needs X11 and a GUI.

---

### Post by Svetgar on 2008-06-24
???

What is X11, and what needs it? The xbox or the server?

---

### Post by stokedfish on 2008-06-24
[http://en.wikipedia.org/wiki/X11](http://en.wikipedia.org/wiki/X11)

XBMC needs it.

---

### Post by cariboo on 2008-06-24
If you are asking if you can store media files on an Ubuntu server the answer is yes, otherwise maybe expand your question a bit.

Jim

---

### Post by stokedfish on 2008-06-24
I thought he was talking about the linux port of XBMC...sorry!  :\

---

### Post by Svetgar on 2008-06-24
All I want to know is if I set up a ubuntu file server is can I use it to send my music and movies to a XBMC.

---

### Post by emid on 2008-06-24
> **Svetgar said:**
> All I want to know is if I set up a ubuntu file server is can I use it to send my music and movies to a XBMC.

Yes, I do this at home over a wireless connection. Video and audio files on a pc and xbmc(on an xbox) hooked up to my tv.

If the xbox is hooked up to your network, then just use samba to share the directories with movies/music on the server.

---

### Post by Svetgar on 2008-06-24
Thanks, thats the info I was looking for.

I still don't know what samba is, but I suppose that is a topic for another thread.

---

### Post by emid on 2008-06-25
> **Svetgar said:**
> Thanks, thats the info I was looking for.

I still don't know what samba is, but I suppose that is a topic for another thread.

Samba is among other things the equivalent of windows file sharing for linux.

I forget if Samba is installed by default on Ubuntu Server.  If it isn't then go to the command line and type:
```

sudo apt-get install samba

```

Here is a link for configuring it from the command line.

[Samba Config]("https://help.ubuntu.com/community/SettingUpSamba#head-d2b25687b553d3737873748f613fb60558db7c4d")

---

