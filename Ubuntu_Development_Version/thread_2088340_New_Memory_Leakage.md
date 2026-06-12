---
title: "New Memory Leakage?"
date: 2012-11-26
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2012-11-26
Has anyone else noticed significant memory leakage with the 3.7 kernel and raring packages?

Now, I don't usually panic when I see my RAM usage get high; I generally assume that it's just doing disk caching.  However, in the last week or two not only have I seen my RAM in the 90%+ range, but this morning I noticed my swap file was getting used as well.

I don't believe this should be happening on a system with 12GB of RAM and hardly nothing running.  I did not notice this at all when running quantal or previous versions.

EDIT:  I think Milos_SD below has identified the correct bug.  Glad to know it's already been identified.

---

### Post by dino99 on 2012-11-26
is it on a fresh install ? or an old one rolling ?

clean, as much you can, the system and use htop to know which app/process is eating memory.

---

### Post by Milos_SD on 2012-11-26
It is not used by any app/process. It is a bug with incorrect NR_FREE_PAGES accounting. It is fixed in new 3.7-rc7 kernel.

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386)

---

### Post by zika on 2012-11-26
> **Milos_SD said:**
> It is not used by any app/process. It is a bug with incorrect NR_FREE_PAGES accounting. It is fixed in new 3.7-rc7 kernel.

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386)For which to get we will have to wait for mainline to recover or proposed, if we are lazy enough to compile...
I know (and You know) that I do not have proper excuse since I successfully did that several times...

---

### Post by ventrical on 2012-11-26
> **3vi1 said:**
> Has anyone else noticed significant memory leakage with the 3.7 kernel and raring packages?

Now, I don't usually panic when I see my RAM usage get high; I generally assume that it's just doing disk caching.  However, in the last week or two not only have I seen my RAM in the 90%+ range, but this morning I noticed my swap file was getting used as well.

I don't believe this should be happening on a system with 12GB of RAM and hardly nothing running.  I did not notice this at all when running quantal or previous versions.


 Funny you mentioned this.  I am assuming it is firefox. What happened to me thismorning is that I have another system that has been running on my KVM in the backgorund, haven't checked it for a few days , but it is always running. I am using Oneiric on it for utility purposes. When I checked into it early thismorning it was very sluggish and almost non-responsive. The culprit was firefox taking up almost 600Mibs of RAM (and a large chunk of swap was being used also) . I  created a post here about ff with Raring. I'll see if I can dig it up. 

   I am NOT saying that it is firefox , but , from what I have seen, it appears that there is something there.

 Did you check that out ? Are you using ff?

*edit*

Whoops .. ok .. just seen where you said you are no using any apps.

---

### Post by zika on 2012-11-27
> **Milos_SD said:**
> It is not used by any app/process. It is a bug with incorrect NR_FREE_PAGES accounting. It is fixed in new 3.7-rc7 kernel.

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386)You're right...
```
:~$ uname -a
Linux ********* 3.7.0-999-generic #201211260421 SMP Mon Nov 26 09:21:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3954       1250       2703          0         56        696
-/+ buffers/cache:        497       3456
Swap:         4093          0       4093
:~$ uname -a
Linux ********* 3.7.0-030700rc7-generic #201211252135 SMP Mon Nov 26 02:35:53 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3954        980       2974          0         42        626
-/+ buffers/cache:        311       3642
Swap:         4093          0       4093

```

---

