---
title: "qustion about worl flow :stateless in snort rule"
date: 2009-09-05
forum: Security
---

### Post by TUDORS on 2009-09-05
dear all 
what the word (**[COLOR="Red"]stateless[/COLOR]**) in below snort rule refer to 
log tcp any <> any 20:21 (msg:“FTP incoming”; flow:stateless; flags:S+;)
thanks in advance

---

### Post by TUDORS on 2009-09-06
up

---

### Post by The Tronyx on 2009-09-06
Hello,

I believe that is referring to a stateless protocol such as UDP or ICMP.

---

### Post by Kinstonian on 2009-09-06
No, that's not it, The Tronyx.  TUDORS, read [this](http://www.informit.com/articles/article.aspx?p=101171&seqNum=6).  Generally I find it not only easier, but quicker to google for questions I have and then if I can't find the answer there, I ask on a forum.  There is a lot of documentation on snort rules out there.

---

