---
title: "Getting a Windows virus with  Ubuntu live CD"
date: 2009-12-07
forum: Security
---

### Post by marticc on 2009-12-07
Hi, I have a question regarding the security and Ubuntu live CD.

I have been for some days at my father's house, and he is using an old PC with XP. As I had to do some online banking, and as I don't trust Windows XP, I downloaded a Ubuntu 9.10 Karmic iso,  I burnt it, and I started a live CD Ubuntu session. I did my banking stuff without any problems, and then I read my e-mail. The problem was I openned an attachment (it was a link with  a silly video and I just openned it, but as far as i know i did not download anything). Despite the fact that I know the source, adn I feel it is safe, I was afraid that this video might be infected by some kind of malware. I turned that PC off, take out the live CD, started Windows XP and scanned  the PC with two AV, and  the PC was clean. But after that experience I have a question:

My question is can you infect a Windows PC when you are surfing the web during an Ubuntu live CD session?

Thanks.

---

### Post by cdenley on 2009-12-07
It is technically possible, but you don't have to worry about it. Even if there was an exploitable vulnerability on the livecd, and you exposed your system to such an exploit which happens to target linux systems, it would be very unlikely that the exploit would look for windows partitions on your system, then infect your windows partition with a windows virus.

---

