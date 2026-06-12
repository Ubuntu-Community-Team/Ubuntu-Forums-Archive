---
title: "XGL/Compiz plugin called Lowfat"
date: 2007-03-28
forum: The Cafe
---

### Post by darkhatter on 2007-03-28
[http://www.youtube.com/watch?v=GkrM4ymkiDo](http://www.youtube.com/watch?v=GkrM4ymkiDo)

just watch the video

:popcorn:

UPDATE: I was reading digg some more and I just found out it wasn't compiz or xgl, so if you have a 3d card you should be able to use this

---

### Post by Chelives1928 on 2007-03-28
I seen the article on digg as well.  Do you have any  idea how to install it so that I can give it a test drive.  I'm not very familiar with linux yet but I'm interested in this lowfat because the video looks awesome.

---

### Post by darkhatter on 2007-03-28
[http://macslow.thepimp.net/?page_id=18](http://macslow.thepimp.net/?page_id=18)

I believe thats his web site, I think you have to compile it :(

---

### Post by prizrak on 2007-03-28
That's kind cool.
Darkhatter,
Come on it's not THAT scary ;)

---

### Post by pt123 on 2007-03-29
so no chance of a .deb file?

---

### Post by floke on 2007-03-29
Lowfat is out????
Have to go check this out....

---

### Post by plb on 2007-03-29
That video is from september and if lowfat was out I'm sure macslow would release a deb afaik he uses ubuntu

---

### Post by floke on 2007-03-29
...apparently not :( 

the README says this:

lowfat is far from done. So do not package it or something similar. It would imply to end-users that it is a "finished product", which it is not yet... by far not.
So for the sake of lowfat's reputation, please do not package it yet. It's only for developers atm.

---

### Post by Oen386 on 2007-03-29
I found directions for how to install (below). When I run it though I get stuck (either at configure or make). I will have to give the error output when I get home.

[http://forum.beryl-project.org/viewtopic.php?f=41&t=4296&st=0&sk=t&sd=a&sid=13d440e88c9619fb15032df641936a25&start=10]("http://forum.beryl-project.org/viewtopic.php?f=41&t=4296&st=0&sk=t&sd=a&sid=13d440e88c9619fb15032df641936a25&start=10")

> 
I GOT IT!!
I have lowfat and it is indeed awesome!
Here is how to get it! Install gitweb and then do a:
git clone git://people.freedesktop.org/~macslow/lowfat
A folder called lowfat will be created in your homefolder containing all needed files to compile it.
Open a terminal cd to the directory and type: ./autogen.sh then ./configure then make and sudo make install.
After that type lowfat and be happy.
Danke Mirco.


---

### Post by floke on 2007-03-29
Ok - so I get it working - but it doesn't seem able to do very much at the moment...

BTW: It depends on automake autoconf and libtools

---

### Post by darkhatter on 2007-03-29
thanks for the link Oen386

---

### Post by reacocard on 2007-03-29
> **Steve.K said:**
> Ok - so I get it working - but it doesn't seem able to do very much at the moment...

Yeah. If it did anything I'd build a deb, but its not worth the effort. The video says it all, really. Cool-looking, but not useful yet.

---

### Post by pt123 on 2007-10-30
Anyone got an update on this?

Because the author gave a talk at FossCamp

[http://arstechnica.com/news.ars/post/20071028-making-linux-application-user-interfaces-richer-with-opengl.html](http://arstechnica.com/news.ars/post/20071028-making-linux-application-user-interfaces-richer-with-opengl.html)

on his blog he has stated that he is in some sort of partnership with Canonical

---

