---
title: "64 Bit Server -- possibly not worth it?"
date: 2009-08-02
forum: Server Platforms
---

### Post by garfonzo on 2009-08-02
Hey folks,

I've got a 64 Bit AMD CPU and will be re-setting up my server and was considering installing the 64 bit version on the server OS. I had a look [at this sticky]("http://ubuntuforums.org/showthread.php?t=765428") regarding the differences, and came away with a decent understanding of the pros and cons.

Since the above link mainly discussed the desktop version of Ubuntu, I'm trying to deduce how it all applies to a Server install. I'm thinking that since I'll mainly just be serving files to my house LAN computers (no websites, no email services, or other fancy stuff) I beleive that I won't take advantage of the 64-Bit performance possibilities. 

Am I correct in this assumption?

---

### Post by LepeKaname on 2009-08-02
Unless your server has more than 4GB of memory I guess you will not see any difference. I personally will suggest you to stick to the 32bits as in general it has better support.

---

### Post by tubezninja on 2009-08-02
I would look at it this way: If you're running a 32-bit version of ubuntu on a 64-bit version of the processor, then you're *never* going to fully utilize the 64-bit capability of the CPU.

At the same time, if you encounter something that would in fact, run better on your server in 64-bit mode, then you're locked out of that.

I've been using 64-but ubuntu on my servers for a while now, as web/LAMP servers, media conversion systems, and file servers.  They've all run very well and the support has been just fine.  Maybe those application don't always fully utilize the 64-bit-ness of the CPU.  So what? Iv I installed the 32-bit version, the same thing would happen. :)

---

### Post by garfonzo on 2009-08-02
> **LepeKaname said:**
> Unless your server has more than 4GB of memory I guess you will not see any difference.
That's interesting. I've only got 2GB. 64BIT OS does better with 4GB or more of RAM? I didn't know that.
> **LepeKaname said:**
> I personally will suggest you to stick to the 32bits as in general it has better support. Kind of what I was thinking, in addition to what a lot of people were mentioning in that thread I linked to in the OP -- If it works in 32BIT just fine, why switch?

> **scaredpoet said:**
> I've been using 64-but ubuntu on my servers for a while now, as web/LAMP servers, media conversion systems, and file servers. They've all run very well and the support has been just fine. Maybe those application don't always fully utilize the 64-bit-ness of the CPU. So what? Iv I installed the 32-bit version, the same thing would happen See, but I'm only sharing files on a private LAN. With your setup, I could see a possible benefit of a 64BIT OS, but for my meager needs, I'm thinking 32BIT is just fine.

---

### Post by LepeKaname on 2009-08-02
> That's interesting. I've only got 2GB. 64BIT OS does better with 4GB or more of RAM? I didn't know that.

Yes, in 64bits 4GB+ is supported natively, let's said 100% performance, but if you have 4GB+ in a 32bits its kind of emulated which you may have a 80% performance. Of course those % are not exactly what it is, but its just to represent the meaning.

There are some threads about that around this forum... but I don't have the link right now.

---

### Post by garfonzo on 2009-08-02
> **LepeKaname said:**
> Yes, in 64bits 4GB+ is supported natively, let's said 100% performance, but if you have 4GB+ in a 32bits its kind of emulated which you may have a 80% performance. 

I don't understand what you're saying. Could you rephrase that?

---

### Post by LepeKaname on 2009-08-03
Sorry, check this link (it better explained): 

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Mainly:

> A 32-bit computer has a word size of 32 bits, this limits the memory theoretically to 4GB. This barrier has been extended through the use of 'Physical Address Extension' (or PAE) which increases the limit to 64GB _although the memory access above 4GB will be slightly slower_.

> If you are doing heavy work where you have started to hit the 4GB memory barrier, then 64-bit is for you. 

Their recommendation is to use 64bits if you don't have a strong reason to use 32bits. 

This is my personal experience: My CPU is an AMD Athlon 64 and the first think I did (when I bought it) was to rush and install Ubuntu 64bits (Hardy). But I had some problems... not very big problems, but somehow annoying. Looking for help in the forums, I realize that most of the people used 32bits version, and that many of the problems I had were related somehow to the 64bits. Then I changed to Ubuntu 32bits, and my problems were fixed. I feel that I made a good choice. 

I will use the 64bits version until most of the people are using it, so there is a higher chance to share the same problems. That is why I told you to stick to the 32bits if possible.

Many things have been fixed since Hardy, and my problems were more related to Desktop issues than to server issues. So I guess any choice would be fine. If its just for your local network I don't think you will feel the difference.

Cheers :-k

---

### Post by cariboo on 2009-08-03
32-bit and 64-bit operate exactly the same what  LepeKaname links to pretains to desktop systems, which don't count here as the server version has no gui.

I say if you have a 64-bit cpu use the 64-bit server version. I've been running 64-bit for the last 4 versions and have never had a problem.

---

### Post by dragos2 on 2009-08-03
A lot of myths around, the truth is that 64 OS on 64 bit hardware will perform better but don't
expect big differences. This is a rather technical discussion but you can have a look at Intel's
processor specifications (if you want to read hundreds of pages) and you'll probably understand.

---

### Post by insane_alien on 2009-08-03
a 64-bit server would be future proofed against a 64-bit only version of software and/or future memory upgrades. go 64-bit. you processor can handle it and there is no downside.

---

