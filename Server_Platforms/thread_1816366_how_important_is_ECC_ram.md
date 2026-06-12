---
title: "how important is ECC ram?"
date: 2011-08-01
forum: Server Platforms
---

### Post by 007casper on 2011-08-01
how important is ECC ram?

---

### Post by HermanAB on 2011-08-02
You may get one to three cosmic ray effects per year on a server that is running 24/7/365.  However, those effects likely will not affect anything noticeable. 

So, worry about it if you are doing banking.

---

### Post by 007casper on 2011-08-02
so, does that mean you dont need xeon chips unless you are doing banking sites

---

### Post by TheR on 2011-08-02
> **007casper said:**
> so, does that mean you dont need xeon chips unless you are doing banking sites

:-)

I have one of my servers using non ECC RAM and running 24/7/365. In 4 years of time I had 2 strange lockups which could be or could not be attributed to RAM type.

In reality It depends what do you need server for. Mine is for archive and it doesn't matter if it locks from time to time. But personally I wouldn't run 24/7 server without ECC memory. It doesn't  cost that much more and it is one worry less. And if you have strange lockups on server, you know it is not because of nonECC memory ;-)

Any decent service support would probably signed you off if you would tell them that your falling server is using nonECC RAM


by
TheR

---

### Post by 007casper on 2011-08-03
I thought ECC Ram is really to prevent corruption in files.  

I heard people use non ECC ram on their servers and they state the corruption rate is minimal to point that it just doesnt matter.

I didnt know it prevented lock up issues.

---

### Post by doas777 on 2011-08-03
> **007casper said:**
> I thought ECC Ram is really to prevent corruption in files.  

I heard people use non ECC ram on their servers and they state the corruption rate is minimal to point that it just doesnt matter.

I didnt know it prevented lock up issues.
well, it prevents corruption of data in ram, whether that data be the kernel images footprint, or a file. you use it to make sure that the data in ram is always accurate (or at least remains the way it was set).

---

