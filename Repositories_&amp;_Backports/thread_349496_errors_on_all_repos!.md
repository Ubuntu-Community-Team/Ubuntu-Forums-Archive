---
title: "errors on all repos!"
date: 2007-01-30
forum: Repositories &amp; Backports
---

### Post by kanpachi on 2007-01-30
hello 
i'm using edgy atm and whenever i tried updating via the repos i get all kinda weird errors (btw, a friend of mine also gets them in dapper)

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  The HTTP server sent an invalid reply header

i tried the israeli repos first (since i live in Israel) and they didn't work
so i thought something was wrong with them
so i tried the US then the UK
and nothing worked!
any ideas?
please...

---

### Post by jimbren on 2007-01-30
When did this start happening?

---

### Post by hal10000 on 2007-01-30
I found this posting which seems to be very similar to yours: [http://ubuntuforums.org/archive/index.php/t-189383.html](http://ubuntuforums.org/archive/index.php/t-189383.html) 
The solution might be to change all [http://.](http://.).... entries in your /etc/apt/sources.list by [ftp://.](ftp://.).....

---

### Post by jvc26 on 2007-01-30
Can you post up the contents of your /etc/apt/sources.list?
Il

---

### Post by fang2415 on 2007-01-30
I'm having a similar problem, but in my case I can't find gb.archive.ubuntu.com at all.  Like, it won't even answer a ping.  http, ftp, whatever.  Anybody know if there's a problem with the gb servers or something?

Replacing gb.archive.ubuntu.com with archive.ubuntu.com in my sources.list seems to work for me though (although it is a little slow).

---

