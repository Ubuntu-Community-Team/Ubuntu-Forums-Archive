---
title: "secure-delete wont work on larger files?"
date: 2010-09-16
forum: Security
---

### Post by Ferrat on 2010-09-16
I'm trying to clean a hard drive and I'm using secure-delete but it just stands there and takes cpu power but nothing happens, I used -r switch first and nothing, so I tried it on single files, small pictures worked as intended but a simple 50MB MPG file just stands there as well and nothing happens.

I left it running for 24 hours and nothing happened but the cpu was working at 90-100% all the time :/ 

Any one know what's wrong? I'm using 10.04 UNR

---

### Post by rookcifer on 2010-09-16
try shred

```
shred -v file
```

---

### Post by Ferrat on 2010-09-16
shred works on files but doesn't have recursive does it? but anyway thank =) at least I can script it or something =D

---

### Post by jbrown96 on 2010-09-16
You shouldn't securely erase at the file system level. Read shred's manpage. 
Run shred at the parition or device level.

---

### Post by Ferrat on 2010-09-16
> **jbrown96 said:**
> You shouldn't securely erase at the file system level. Read shred's manpage. 
Run shred at the parition or device level.

Since I want to keep the system and it's on the same device and partition I don't have much choice or is there a better way?

---

### Post by rookcifer on 2010-09-16
> **Ferrat said:**
> shred works on files but doesn't have recursive does it? but anyway thank =) at least I can script it or something =D

No, but you said you only wanted to delete one large file.  If you need to securely erase directories you will have to delete all the files within it with a wildcard (*).

---

### Post by Ferrat on 2010-09-17
> **rookcifer said:**
> No, but you said you only wanted to delete one large file.  If you need to securely erase directories you will have to delete all the files within it with a wildcard (*).

Yes I know but the recursive worked for secure-delete, just not big files, I did say "I used -r switch first and nothing" in the beginning but I should have been clearer on that :P 

anyway solved it by making a bash script that just takes a argument for number of shreds and then multiple targets to shred including folders you want to shred recursively :)  that made it really easy to target a lot of files in different places at once =)

---

### Post by HermanAB on 2010-09-17
Howdy,

There are many kludgy programs to supposedly erase files, but the real solution is to use EncFS or LUKS.

---

### Post by Ferrat on 2010-09-17
> **HermanAB said:**
> Howdy,

There are many kludgy programs to supposedly erase files, but the real solution is to use EncFS or LUKS.

Depends on what you want and in this case it's like saying

"You should play soccer on grass not gravel, to the guy in the store buying shoes for the big match on gravel the next day" 

:P

---

### Post by HermanAB on 2010-09-17
Hmm, it is probably faster and easier to simply re-install Ubuntu, since that only takes about 30 minutes.  Not to mention that the OP already wasted a day...

---

### Post by BkkBonanza on 2010-09-17
I've used secure-delete many times on multi GB files. It works fine. The only thing is you DON'T want to use the crazy full 38 pass mode. That does take forever and gives you no benefit. Try again with,

srm -flz ...  or even srm -fllz

I've also used the sfill command to wipe about 90 GB in an hour or two. Again using the fast, low security, zero modes.

Nowadays it's pointless running 38 random sweeps over the disk. That's why it takes so long - generating random data in huge qty to spew all over the drive.

---

