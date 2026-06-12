---
title: "Linux Kernel keeps crashing after installing today's updates in Ubuntu 12.04 LTS!"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-01-17
Built In Linux Kernel keeps crashing after installing today's updates in Ubuntu 12.04 Long Term Support DVD Nightly Build after using sodo apt-get update, and sudo apt-get upgrade! Just for your information! Bug report Filed!

---

### Post by ranch hand on 2012-01-17
Well I just update/upgraded this install in chroot from my other drive and it seems to be working fine now that I have come over to visit it.

This is Xubuntu 12.04 though so that may be the difference.  Could be a couple critical packages are just not working quite right with the new kernel.

Watch your bug for comments and see if a later update/upgrade cycle fixes it.  Sounds like something that should be fixed pretty quick.

---

### Post by xyzzyman on 2012-01-17
If you opened up a bug report you should post a link to it. It makes it easier for others to add their name to it if they are having the same crash.

---

### Post by kevpan815 on 2012-01-20
> **xyzzyman said:**
> If you opened up a bug report you should post a link to it. It makes it easier for others to add their name to it if they are having the same crash.

I would if I could, but it looks like all 3 of my Bug Reports have all ready been closed due to it being an External Issue or something else.

---

### Post by Harry33 on 2012-01-20
Linux kernel (from Precise repos) 3.2.0-10.17 works fine here. Absolutely no crashes.

---

### Post by xyzzyman on 2012-01-20
> **kevpan815 said:**
> I would if I could, but it looks like all 3 of my Bug Reports have all ready been closed due to it being an External Issue or something else.

Even if it's been closed since, when you say a bug report has been filed it would still give you a link to it. Most likely you're not giving enough information and detective work to tell them what's actually crashing and being vague like in your original post here.

It's like calling a mechanic and saying your car doesn't start and wanting them to tell you why. Log files are needed but in this stage of alpha testing we need to look at them ourselves and find out what's going on. Even if we can't fix it or don't know why, they'll know what to look for. **The thing to remember is more information is better than not enough.** That's why watching what updates are incoming is important, and knowing how to chroot from another install or at least knowing how to look at log files from a livecd is important.

---

### Post by Ibidem on 2012-01-20
Is it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917971](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917971)?

---

### Post by kevpan815 on 2012-01-21
> **Ibidem said:**
> Is it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917971](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917971)?

Yes, that is the Bug Report, and the Kernel Panic is still occuring on my Dell Netbook as of the 01/20/2012 Nightly Build with no updates installed.

My only Work Around to the Problem is to log into the Guest Account instead of my Kevin John Panzke User Account and then the Kernel Panic does not occur.

---

### Post by kevpan815 on 2012-01-21
> **Harry33 said:**
> Linux kernel (from Precise repos) 3.2.0-10.17 works fine here. Absolutely no crashes.

That's because you don't have the same hardware that is causing the crash as I do, as I think that this constant crashing is hardware related, due to the fact that my Dell Inspiron 1012 Net Book is the only one of my test machines that is having the problem! Just for your information.

---

### Post by kevpan815 on 2012-01-21
> **kevpan815 said:**
> That's because you don't have the same hardware that is causing the crash as I do, as I think that this constant crashing is hardware related, due to the fact that my Dell Inspiron 1012 Net Book is the only one of my test machines that is having the problem! Just for your information.

P.S. Looking at the Bug Report more closely, it looks like the Kernel Panic is being caused by an incompatibility problem with my Integrated Sound Card in my Dell Inspiron 1012 Net Book! Just for your information.

---

### Post by NCLI on 2012-01-21
Your bug hsnøt been closed, it's just been marked as a duplicate of another bug, which is currently in the process of being fixed.

---

### Post by forcecore on 2012-01-21
Strange was i got kernel panics when i used memory card reader on my Thinkpad x201,when memory card was in sometimes it was 10 sec sometimes 1-2 min when panic occurred.

---

### Post by xyzzyman on 2012-01-21
> **kevpan815 said:**
> That's because you don't have the same hardware that is causing the crash as I do, as I think that this constant crashing is hardware related, due to the fact that my Dell Inspiron 1012 Net Book is the only one of my test machines that is having the problem! Just for your information.

You may want to be careful with your frequent use of 'Just for your information'. Especially in the way that you phrase it as the end of your statements. Many people are going to take that as condescending or patronizing, which is uncalled for as people have been very polite to you on here.

---

### Post by kevpan815 on 2012-01-22
> **xyzzyman said:**
> You may want to be careful with your frequent use of 'Just for your information'. Especially in the way that you phrase it as the end of your statements. Many people are going to take that as condescending or patronizing, which is uncalled for as people have been very polite to you on here.

Ok, sorry about that, for some reason or another i can't stop myself from ending all my statements with just fyi at times. I will try to stop my self from using that in the future.

---

### Post by xyzzyman on 2012-01-22
> **kevpan815 said:**
> Ok, sorry about that, for some reason or another i can't stop myself from ending all my statements with just fyi at times. I will try to stop my self from using that in the future.

Yeah, better than sometime taking offense and starting an argument later.

---

### Post by kevpan815 on 2012-02-02
> **forcecore said:**
> Strange was i got kernel panics when i used memory card reader on my Thinkpad x201,when memory card was in sometimes it was 10 sec sometimes 1-2 min when panic occurred.

You were right and I was wrong: It was the Realtek USB Memory Card Reader that was the problem.

---

