---
title: "apache2: downloads of media files from my server stop at random point"
date: 2010-11-27
forum: Server Platforms
---

### Post by adieb on 2010-11-27
Hi everybody,

i'm having a very strange problem with my ubuntu apache2 server running wordpress.

i want do download media files (from within a flash-mp3-player onsite or by link [www.mysite.com/folder/file.avi](www.mysite.com/folder/file.avi)) but the file transfer just stops after a while. (at least sometimes) at random positions. after that i have to clear the browsers cache and try again.

it is really annoying, though it is my band's website and we want to share our songs with our friends.

i checked from several clients, seems to happen everywhere (linux, mac or windows clients)

the system:
```
Linux 2.6.32-24-generic-pae (as a virtualbox vm on any linux host)

apache2: 2.2.14-5ubuntu8.4
php5:    5.3.2-1ubuntu4.5

```


Thx a lot for your help!



[B]UPDATE: With wget it seems to work...
[/B]

---

### Post by SeijiSensei on 2010-11-27
Why not just create a YouTube channel and let them handle it all?

---

### Post by adieb on 2010-11-27
;) Nice idea. But i'd still be interested in fixing that issue...


UPDATE: With wget it seems to work...

---

### Post by elico on 2010-11-27
the first thing to try is to download the source file and to see whether your server is working properly for file transfer.

---

### Post by iNsOmNiOuS on 2010-11-27
Try to download from other locations. It could be your internet connection. Also what browser are you using ? I experienced problems like this with Firefox on Linux and Windows

---

