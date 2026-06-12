---
title: "PHP5 not working with Apache2 :( :("
date: 2010-11-26
forum: Server Platforms
---

### Post by POQbum on 2010-11-26
Hi

I've been trying this for hours and can't for the life of me figure this out.

I have a simple glype proxy I'm trying to run here:
[http://69.10.40.18/upload/index.php](http://69.10.40.18/upload/index.php)

As you can see, the php page loads perfectly fine. The problem is that it only seems to be loading the html aspects of it (I may be wrong).

So when I go to use the proxy, I only get a blank page.

Can someone let me know what I'm doing wrong?

Cheers.
 - Paul


*********
Edit:
nvm, I found the solution.

I didn't enable cURL in PHP5 and that was causing the problems. Working like a charm now.

---

