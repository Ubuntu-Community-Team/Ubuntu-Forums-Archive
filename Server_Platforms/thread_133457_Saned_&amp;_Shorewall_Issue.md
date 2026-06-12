---
title: "Saned &amp; Shorewall Issue"
date: 2006-02-20
forum: Server Platforms
---

### Post by compmodder26 on 2006-02-20
I posted this 2 days ago in the wrong forum, asked the mods to move it but it still hasn't been moved so I'm going to go ahead and add another thread here.  Sorry for the double-post.

I'm having a problem with getting saned and shorewall to play nice together. I've got my scanner attached to a server and the idea is for my computers in my home lan to be able to use the scanner. The problem is that according the the saned manual, saned needs to be able to access a random data port greater than 1024 in addition to the standard sane-port of 6566. For security purposes, I would rather not open up all my ports greater than 1024. It would be great if I could tell saned what data port to listen on but I haven't been able to find a way to do that. Has anybody dealt with this issue? If so, can you tell me how you got around it?

---

### Post by ZungBang on 2007-03-07
Check out:
[http://machine-cycle.blogspot.com/2007/02/scanner-darkley.html](http://machine-cycle.blogspot.com/2007/02/scanner-darkley.html)
Hope this helps (I'm running Debian "Etch", but it should be close enough).

---

