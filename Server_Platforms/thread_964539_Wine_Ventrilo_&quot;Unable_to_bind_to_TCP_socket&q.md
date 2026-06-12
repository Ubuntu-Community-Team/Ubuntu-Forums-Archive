---
title: "Wine Ventrilo &quot;Unable to bind to TCP socket&quot;"
date: 2008-10-31
forum: Server Platforms
---

### Post by cj_g0bl1n on 2008-10-31
I installed wine finally, and got Ventrilo on it.  I can run vent, but I get the error message: "Unable to bind to TCP socket."

I copied the ventsrv folder (this contains all the vent stuff) and put it on my windows laptop.  Ran ventrilo_srv.exe and bam, it binded and ran perfectly.  This rules out my router.

Now I have a linux version on vent on the machine too (it doesn't run at the same time, or one wouldn't be able to bind, but I was sure to turn it off).  Now I thought that if I could run the linux version that it wasn't my firewall.  However, could running it off wine cause it to be blocked by my firewall?  How can I check this?

If the firewall isn't the problem, what else could be the problem?

Thanks!
goblin

---

### Post by Verdeski on 2010-03-06
I'm pretty sure you have to setup an allowance for the TCP socket on both the router, and your computer. Still looking for more information on the topic. I was actually looking to do the same thing, and I just recently moved from Windows. Still taking classes and the like to learn some more.

---

### Post by NullHead on 2010-03-06
Well, it's probably your firewall or another instance of vent running. Check the running processes with ```
ps aux | grep ventrilo_srv
```Once you locate the process, use *"kill <process number"* to kill it; if it's even running. 

You should be running the linux version. There's no need to be running it in wine.

---

