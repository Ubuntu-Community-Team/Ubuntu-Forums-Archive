---
title: "Stack/segment protection in Kbuntu?"
date: 2007-10-13
forum: Server Platforms
---

### Post by IceDane on 2007-10-13
Hey there.

I am required to take a course in school wherein we experiment with exploitation of buffer overflows among other common vulnerabilities.

However, after having installed Slack 12.0 and giving up due to not being able to execute it, and then installing Ubuntu, I still get problems.

So far, I've found these things as possible counter-measures against stack-smashing attacks:

NX-bit - Supported in most newer x86 processors, but not implemented by default in most kernels. I'm about to recompile now, to see if I can disable it, if it's on.

PaX - A collection of kernel security patches meant to emulate the NX-bit, or something in that direction. I downloaded paxctl, and it doesn't seem to be on.

Virtual address space randomization - On by default in the 2.6 kernels, but I've disabled it.

SSP(Stack smashing protection) - On by default in GCC 4.0+ in ubuntu, or something like that, been using the -fno-stack-protector. 


Anyway, I was wondering. Which one of those measures is the one that's ruining this for me? I read somewhere that there was something besides the SSP implemented in GCC by default, and that I could download gcc 3.3?

All help greatly appreciated.

---

### Post by Adnarim on 2007-10-13
As I said in this post yesterday (you should have searched the forum first before posting): [http://ubuntuforums.org/showthread.php?t=570676](http://ubuntuforums.org/showthread.php?t=570676) , Ubuntu uses VASR in the kernel and Stackguard in gcc. Read my answer in this post how to switch it off.

Read this how to defeat VASR: [http://www.tty64.org/doc/expwlnxgateso1.txt](http://www.tty64.org/doc/expwlnxgateso1.txt) and this how to defeat Stackguard: [http://www.phrack.org/issues.html?issue=56&id=5](http://www.phrack.org/issues.html?issue=56&id=5) . But at least Stackguard is an advanced topis which could be over your skills s you're better of with just switching these protection shemes off.

---

### Post by IceDane on 2007-10-13
> **Adnarim said:**
> As I said in this post yesterday (you should have searched the forum first before posting): [http://ubuntuforums.org/showthread.php?t=570676](http://ubuntuforums.org/showthread.php?t=570676) , Ubuntu uses VASR in the kernel and Stackguard in gcc. Read my answer in this post how to switch it off.

Read this how to defeat VASR: [http://www.tty64.org/doc/expwlnxgateso1.txt](http://www.tty64.org/doc/expwlnxgateso1.txt) and this how to defeat Stackguard: [http://www.phrack.org/issues.html?issue=56&id=5](http://www.phrack.org/issues.html?issue=56&id=5) . But at least Stackguard is an advanced topis which could be over your skills s you're better of with just switching these protection shemes off.

I did search, and I've read both your and many other similar posts multiple times.

As you can see by reading my post again, I mention both Stack protection AND VASR(Virtual address space randomization). 
Stack protection is switched off by using the -fno-stack-protector flag, and VASR is done, well, you know how it's done.

Anyway, using gcc 4.1, no exploits work. Even with the switch mentioned above. However, I just got gcc 3.3, compiled the exploit, and it works just as intended.

Is there some feature in gcc 4,0+ that needs to be configged when you compile it to switch the protection scheme off?

I'm about to go through the GCC 4.1 docs right now to see if there's something I can do.

---

