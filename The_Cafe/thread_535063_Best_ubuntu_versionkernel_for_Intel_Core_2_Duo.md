---
title: "Best ubuntu version/kernel for Intel Core 2 Duo?"
date: 2007-08-26
forum: The Cafe
---

### Post by user1397 on 2007-08-26
So I've just bought a new computer with an Intel Core 2 Duo processor.

I know it is 64-bit, and I also understand there are some problems with the 64-bit versions of Ubuntu.

Now, if I install from the 32-bit Ubuntu feisty i386 desktop cd, the default kernel I believe is the i686 SMP kernel.

So for both of my cores to be used, I don't have to do anything?

Also, why do they call the 64-bit version of Ubuntu the "AMD64"
 version...does it not also work with Intel 64-bit processors?

---

### Post by mikewhatever on 2007-08-26
> So for both of my cores to be used, I don't have to do anything?

Also, why do they call the 64-bit version of Ubuntu the "AMD64"
version...does it not also work with Intel 64-bit processors?

That's right.

I think that is a tradition, since Intel's 64 bits cpus are relatively new.

---

### Post by be4truth on 2007-08-26
I am using  2.6.20-16-generic  SMP with Fesity 32bit installed and it works great; both CPU in action.

---

### Post by user1397 on 2007-08-26
Hmm I jsut notcied that they're actually saying "for 64-bit amd64 and **Intel **computers" now for the 64-bit option.

Thanks for the info though, I appreciate it.

---

### Post by stmiller on 2007-08-26
The 64bit version has a kernel that is compiled as "x86_64 generic" so it runs on AMD or Intel similarly.

---

### Post by jinx099 on 2007-08-26
> **ubuntuman001 said:**
> So I've just bought a new computer with an Intel Core 2 Duo processor.

I know it is 64-bit, and I also understand there are some problems with the 64-bit versions of Ubuntu.

Now, if I install from the 32-bit Ubuntu feisty i386 desktop cd, the default kernel I believe is the i686 SMP kernel.

So for both of my cores to be used, I don't have to do anything?

Also, why do they call the 64-bit version of Ubuntu the "AMD64"
 version...does it not also work with Intel 64-bit processors?
What "problems" have you heard about with the 64-bit version?  Everything works great for me.  If you are talking about the problem where Adobe and Sun are too lazy to make 64-bit versions of flash and java plugins, then this is easily fixed just by running a script.  Search the forums.

---

### Post by agurk on 2007-08-26
64-bit will give you a performance hit when it comes to memory bandwidth. Especially if it's a notebook, I'd go with 32-bit instead.

---

### Post by RageOfOrder on 2007-08-26
64 bit would be better if you choose KDE (I guess Kubuntu for you people) since pre-linking makes an astounding difference in performance on a 64 bit cpu. 

But you do lose flashplayer and stuff. I run 64 bit gentoo and 32 bit slackware. No difference between em really, but you do have to find 64 bit wireless drivers if you're stuck using ndiswrapper.

---

### Post by Andrewie on 2007-08-26
you can use nsplugin not sure the actual name to use the 32-bit flash with 64-bit. I don't have any studies but I did notice a speed improvement uisng 64-bit. All kernels are compiled to take advantage of dual-core and single-core cpu so using the default kernel you should be ok.

---

### Post by user1397 on 2007-08-27
Thanks for all the replies.

---

### Post by ~LoKe on 2007-08-27
It's only called AMD64 since AMD had released the Opteron earlier, as the first 64bit processor (x86_64).  Intel has the IA64 or something similar.

Then again, I think it's possible that the AMD in the two names mean two completely different things.

---

### Post by user1397 on 2007-08-29
All I can say, is that I was able to run both the 32-bit and the 64-bit live CDs of feisty successfully on my new computer.

Thanks again for all the info.

---

