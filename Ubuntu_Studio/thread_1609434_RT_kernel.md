---
title: "RT kernel"
date: 2010-10-30
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2010-10-30
So whats the deal with the availability of the RT kernels now?

Is there a replacement?

Is the replacement better?

How can i include the replacement into a new kernel compilation?

Thanks

---

### Post by Darknote on 2010-10-31
Yes I am also having trouble installing an RT Kernel. I've tried in Terminal:

> sudo aptitude upgrade && aptitude install linux-rt

and

> sudo apt-get install linux-rt linux-headers-rt

and many more options...

But I only get the message: 
E: Unable to locate package linux-rt
E: Unable to locate package linux-headers-rt

and so on and so fourth... Nothing happens.

Is there a way to get the kernel from the Ubuntu Studio 10.10 live CD?
But, I am new to Linux and I don't know anything about "building from source" or anything like that. I only know "sudo apt-get" and Synaptic.
I'm using Ubuntu Desktop 10.10 and I'm trying to install the Ubuntu Studio RT Kernel because I want to use all the audio software's from Studio with the low latency kernel.

---

### Post by Pablo_F on 2010-10-31
There is no rt patched kernel in Ubuntu maverick. Even mainstream, there is no rt patch for 2.6.35 to this day. (See [http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/)). 

linux rt kernel is only recommended under certain circumstances (depending on hardware configuration), not in all cases. If you really need a rt kernel, go for lucid. 

See also: [http://ubuntuforums.org/showthread.php?t=1602827](http://ubuntuforums.org/showthread.php?t=1602827)

Cheers! Pablo

---

### Post by AutoStatic on 2010-11-01
[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

---

### Post by pepsifx357 on 2010-11-03
> **Pablo_F said:**
> There is no rt patched kernel in Ubuntu maverick. Even mainstream, there is no rt patch for 2.6.35 to this day. (See [http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/)). 

linux rt kernel is only recommended under certain circumstances (depending on hardware configuration), not in all cases. If you really need a rt kernel, go for lucid. 

See also: [http://ubuntuforums.org/showthread.php?t=1602827](http://ubuntuforums.org/showthread.php?t=1602827)

Cheers! Pablo

Lucid has an RT kernel?  Good, thats what I'm working with.  Is it in the repositories?

---

### Post by Pablo_F on 2010-11-03
> Lucid has an RT kernel? Good, thats what I'm working with. Is it in the repositories? 

Yes, it is called linux-rt. 

Cheers! Pablo

---

