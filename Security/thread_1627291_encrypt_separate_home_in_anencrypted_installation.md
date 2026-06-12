---
title: "encrypt separate /home in anencrypted installation?"
date: 2010-11-21
forum: Security
---

### Post by newboyo on 2010-11-21
Hi All,

I've been using separate / and ~ partitions. I recently installed 10-4 LTs with encrypt home option - thinking that it would encrypt my separate /home partition, only to realise that it puts the encrypted ~ in the /.

I now plan to use Dustin's instructions (see [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")  to move to a separate encrypted ~.

Question - will it work with the existing setup or will I need to reinstall 10-4 all over again? (I hope not, the missus will have a fit!!!). 


Rgds


New

---

### Post by movieman on 2010-11-21
The encrypted files go under /home, but not /home/user. So you need a separate /home partition to make it work by default.

I believe those are the instructions I used to set up my encrypted 10.04 installation on my netbook after initially installing without encryption, so they should work OK.

---

