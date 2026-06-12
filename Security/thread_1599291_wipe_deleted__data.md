---
title: "wipe deleted  data"
date: 2010-10-17
forum: Security
---

### Post by tony van on 2010-10-17
I was using dd if=/dev/zero of=/dev/user name/wipe.conf
however i got a message that my hard drive is full.
 
lots of this is scary - dangerous.
 
what is the best way to fill in random or zeros in deleted files without the hard drive filling up ?
thank you

---

### Post by BkkBonanza on 2010-10-17
Install the secure-delete package and use **sfill -flz /path/to/wherever**.

Wiping the free space will always fill up your drive during the process. That's how it wipes the free space. It allocates it all, fills with zeros/random data and then deletes it. When it's done it returns to being free again but clean as well.

---

### Post by tony van on 2010-10-17
thank you

---

### Post by HermanAB on 2010-10-18
Hmm, the better way is to encrypt the file system.

---

### Post by tony van on 2010-10-18
you might be right. i tried **sfill -flz and**  i get not enough disk space again. then i rebooted and ran
repair because i lost my desktop icons but was able to recover.:(

---

### Post by BkkBonanza on 2010-10-18
Do not use your system while you're wiping free space. As mentioned the process involves allocating all free space so you will have issues if you are working while it is wiping. It takes quite a while too, depending on how much free space there is to wipe. As long as you let **sfill** finish it will return the disk space to being free again and you shouldn't need to repair anything.

---

### Post by tony van on 2010-10-20
yes, you are right. my mistake was when the poppup said "running out of space", I stopped the process. I then ran it again and when the message box came of i let the process continue and it worked.
 
thanks again:P

---

### Post by bodhi.zazen on 2010-10-20
dd is sufficient , you need to delete the file is all.

/dev/zero will do as well.

```
sudo -i
dd if=/dev/zero of=/tmp/wipe.conf
rm /tmp/wipe.conf
```

```
sudo -i
cat /dev/zero > /tmp/wipe.conf
rm zero.file
```

Yes you will get messages that the disk is full, :lolflag:

---

### Post by steve161 on 2010-10-20
bleachbit (in the repos) has a gui option to wipe free space with a single zero pass. It is faster than sfill, even when using sfill's quickest wipe method (for me, at least).  Not better or worse than the the options mentioned previously, only another choice.

---

### Post by bodhi.zazen on 2010-10-21
> **steve161 said:**
> bleachbit (in the repos) has a gui option to wipe free space with a single zero pass. It is faster than sfill, even when using sfill's quickest wipe method (for me, at least).  Not better or worse than the the options mentioned previously, only another choice.

bleachbit is a nice application, the only "problem" you might have is getting over zealous with what you "clean".

Be sure you understand what you are removing before you remove it. If you are not sure, either google search or leave it.

---

