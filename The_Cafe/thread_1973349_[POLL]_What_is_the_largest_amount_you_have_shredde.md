---
title: "[POLL] What is the largest amount you have shredded a file by?"
date: 2012-05-04
forum: The Cafe
---

### Post by xdragonforce on 2012-05-04
So yeah, what is the largest number you have put in a shred option. I think the largest I entered was 10000000. So 
```
shred -u -z -v 10000000 hello.c
```

---

### Post by blithen on 2012-05-04
What? lol I don't get it. What does Shred even do?

---

### Post by Lightstar on 2012-05-04
0 !

---

### Post by pqwoerituytrueiwoq on 2012-05-05
the max amount spybot S&D's secure shredder will let you been a few years since i messed with it since i dont use windows

---

### Post by jespdj on 2012-05-05
> **blithen said:**
> What? lol I don't get it. What does Shred even do?

```
man shred
```

---

### Post by forrestcupp on 2012-05-05
> **jespdj said:**
> ```
man shred
```

We're too lazy to look. Just tell us. :)

And where's the poll?

---

### Post by Bandit on 2012-05-05
> **forrestcupp said:**
> We're too lazy to look. Just tell us. :)

And where's the poll?

I think Shred replaces files that are still on your system that you deleted (i.e. just removed entry from the file system table) with 1s and 0s repeatedly until it cant be recovered..

Then again I just woke up and havent had any caffine. So I can be wrong..

---

### Post by zombifier25 on 2012-05-05
Seriously, noone here used shred? (and again, in order to wipe a hard drive completely, DiskDestroyer (dd) is more popular :P )
shred overwrite a file with random bytes repeatedly (can use /dev/random or urandom as a source of random bytes) n times, so that it's completely unrecoverable.

---

### Post by Bandit on 2012-05-05
> **zombifier25 said:**
> Seriously, noone here used shred? (and again, in order to wipe a hard drive completely, DiskDestroyer (dd) is more popular :P )
shred overwrite a file with random bytes repeatedly (can use /dev/random or urandom as a source of random bytes) n times, so that it's completely unrecoverable.

Really for your average user and even myself, dont really have a need for it unless I need to destroy data. I have used it in windows to make sure the temp folder data was completely dead. But really dont see the need for it here. If I am selling a computer, I will use dd on the drive in it before installing a fresh copy of ubuntu. But thats about it for me. I guess if I had been up to qustionable activity I might have a failsafe setup to run and remove files and replace them with garbage. But I do no wrong these days O:)

---

### Post by HermanAB on 2012-05-05
Just encrypt your data partitions.  Shred is kinda useless.

---

### Post by Bandit on 2012-05-05
> **HermanAB said:**
> Just encrypt your data partitions.  Shred is kinda useless.

** I tend to agree, if your data security is that important **

---

### Post by forrestcupp on 2012-05-05
Shred is useless, but it's still kinda fun. :)

---

### Post by Old_Grey_Wolf on 2012-05-05
> **xdragonforce said:**
> So yeah, what is the largest number you have put in a shred option. I think the largest I entered was 10000000. So 
```
shred -u -z -v 10000000 hello.c
```

10000000, why? Anything over 7 is probably a waste of time.

---

### Post by synaptix on 2012-05-05
[delete]

---

### Post by Paqman on 2012-05-06
> **xdragonforce said:**
> So yeah, what is the largest number you have put in a shred option.

Probably about 3. 

You only ever need to overwrite once, all that Gutmann stuff is just voodoo nonsense, as Gutmann himself explained. No one is going to be checking your platters with an electron microscope, and one pass will prevent software tools from recovering anything.

But yes, encryption is even easier. You don't need to lift a finger, then when you want to get rid of the drive just delete the partitions and rest easy. Overwriting whole drives is sloooooow.

---

