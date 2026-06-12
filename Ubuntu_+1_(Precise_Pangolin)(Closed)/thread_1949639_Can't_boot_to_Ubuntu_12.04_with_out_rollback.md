---
title: "Can't boot to Ubuntu 12.04 with out rollback"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Johnny3 on 2012-03-30
I did and up now can't but into 12.04 with out hitting shift key and doing a rollback the will boot it is still 12.04 after the rollback. I did updates, sudo apt-get update, and sudo apt-get install. Any ideas what I mite could do? 
Thanks and God Bless Johnny3 65+++
PS it was dumb luck I could remember to hit the shift key and do a rollback.

---

### Post by cariboo on 2012-03-30
What happens when you try to boot the 3.2.0-21-generic kernel?

---

### Post by Johnny3 on 2012-03-30
> **cariboo907 said:**
> What happens when you try to boot the 3.2.0-21-generic kernel?

If I try to boot to the 3.2.0-21 generic kernel it stop with a blinking _ in the top left cornet. I can boot into 3.2.0-21 recovery mode and ran all the things it listed. But to boot up I have to use 3.2.0-20 then will work. Hope this makes sense.
Thanks and God Bless Johnny3 65+++

---

### Post by netherblood on 2012-04-02
> **Johnny3 said:**
> If I try to boot to the 3.2.0-21 generic kernel it stop with a blinking _ in the top left cornet. I can boot into 3.2.0-21 recovery mode and ran all the things it listed. But to boot up I have to use 3.2.0-20 then will work. Hope this makes sense.
Thanks and God Bless Johnny3 65+++

Same problem here.

---

### Post by netherblood on 2012-04-02
> **Johnny3 said:**
> I did and up now can't but into 12.04 with out hitting shift key and doing a rollback the will boot it is still 12.04 after the rollback. I did updates, sudo apt-get update, and sudo apt-get install. Any ideas what I mite could do? 
Thanks and God Bless Johnny3 65+++
PS it was dumb luck I could remember to hit the shift key and do a rollback.

The workaround I'm using is removing the new kernel:

```
$ sudo apt-get purge linux-headers-3.2.0-21 linux-headers-3.2.0-21-generic linux-image-3.2.0-21-generic
$ sudo update-grub
```

---

