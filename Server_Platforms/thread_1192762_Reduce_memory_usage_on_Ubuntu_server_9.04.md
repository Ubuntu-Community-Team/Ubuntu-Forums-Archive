---
title: "Reduce memory usage on Ubuntu server 9.04?"
date: 2009-06-20
forum: Server Platforms
---

### Post by garton on 2009-06-20
I have a fresh install of an Ubuntu server 9.04. No GUI, just text-based login. This is the output from "free":

             total       used       free     shared    buffers     cached
Mem:        508828     311116     197712          0     108060     162892
-/+ buffers/cache:      40164     468664
Swap:       875500          0     875500

300MB of allocated RAM on a system that does nothing seems a bit much to me. Is there a way to reduce this?

---

### Post by philcamlin on 2009-06-20
what do you mean its doing nothing its doing alot of things like it has your apache thats ubing up memory or lamp or whatever 

same with any os itll always use up memory :popcorn:

no matter what your doing

---

### Post by zekica on 2009-06-20
> **garton said:**
> 
```

             total       used       free     shared    buffers     cached
Mem:        508828     311116     197712          0     108060     162892
-/+ buffers/cache:      40164     468664
Swap:       875500          0     875500
```


The last column (**cached**) displays how much of your **used** memory is in fact disk cache, so your system should be able to free a lot of that when it needs more memory. So, in your case, your actual used memory is a little above 150MB.

---

### Post by garton on 2009-06-20
I just realized that I installed ubuntu-virt-server during the installation! That's becuase I was going to run virtualbox on this machine. 

Now I realize that virtualbox may not be using ubuntu-virt-server at all. That's going to go then, and I'll see if that reduces RAM usage.

---

### Post by garton on 2009-06-20
> **philcamlin said:**
> what do you mean its doing nothing its doing alot of things like it has your apache thats ubing up memory or lamp or whatever 

same with any os itll always use up memory :popcorn:

no matter what your doing

I know that. But an OpenSUSE box with no X idles at about 5MB. So the question in this thread was; why is an Ubuntu server idling at 300MB?!

---

### Post by garton on 2009-06-20
> **garton said:**
> I just realized that I installed ubuntu-virt-server during the installation! That's becuase I was going to run virtualbox on this machine. 

Now I realize that virtualbox may not be using ubuntu-virt-server at all. That's going to go then, and I'll see if that reduces RAM usage.

Right... that reduced memory usage with 200MB. 

Sorry for starting a thread without checking this first.

---

