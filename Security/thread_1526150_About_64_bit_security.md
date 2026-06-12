---
title: "About 64 bit security"
date: 2010-07-07
forum: Security
---

### Post by fipz on 2010-07-07
Hello everyone,

since all what I can find on google is about benchmarks I'd like to ask you if a 64 bit kernel would be more stable , secure and reliable than a 32 bit one.

I ask this question because apparently the 64 bit instruction set offers more advanced security features (i'm saying apparently because I'm not able to give details since it been a really fast read) which would be used by a 64 bit Operating System (Apple also stated that 64 bit applications are less likely to be "attacked").

I have to assume that a 32 bit one does not use them right? Should I stick to 64 bit? (to be honest that "not for everyday" thing on ubuntu download pages made me wonder lol, because since intrepid i ALWAYS used the 64 bit version)

My "lowest" computer has a pentium processor (1,6 ghz dual core) according to lshw I have NX enabled and my ram is 2GB (might seem useless using a 64bit kernel on 2 GB but i'm more concerned about security now)

thank you in advance


ps: i hope you will forgive any skipped detail or error in this post, its pretty late and i been googling this (and something else i might ask later) all day lol.

---

### Post by johngreth on 2010-07-07
I've always found 32 bit to be more stable and reliable, but now a days they are about the same. The only reason it really matters is if you have a system with more than 4 gig ram, then you should get 64 bit. Many people have strong feelings about which one to use for different reasons, but I don't think it really matters.

I don't know anything about a difference in security.

---

### Post by rookcifer on 2010-07-07
> **fipz said:**
> Hello everyone,

since all what I can find on google is about benchmarks I'd like to ask you if a 64 bit kernel would be more stable , secure and reliable than a 32 bit one.

I ask this question because apparently the 64 bit instruction set offers more advanced security features (i'm saying apparently because I'm not able to give details since it been a really fast read) which would be used by a 64 bit Operating System (Apple also stated that 64 bit applications are less likely to be "attacked").

It's because 64 bit processors (at least x86_64) have the NX bit, which makes certain regions of memory unable to execute.  This helps protect against certain types of exploits.  (Micro$oft calls this DEP.  With Linux, we call it "NX").

Another benefit is due to the larger registers, one can utilize other techniques like ASLR which, although available on 32 bit machines, are very weakly implemented due to the smaller memory registers. 64 bit platforms don't have that issue.

Bottom line: if you have a 64 bit CPU, you should use a 64 bit OS.  There is zero reason not to in 2010.  Even if you don't have 4+ GB of memory, there are security and performance advantages to using a 64 bit kernel.

---

### Post by uRock on 2010-07-08
I have a 64bit system that I was running Ubuntu 64bit on with only 1 GB RAM. It worked great and worked even better when I added a GB.

As far as security is concerned, one would still have to penetrate the firewall in your router and get your system to respond, which, unless you have installed a serving program,  is very hard to do unless you fall victim to social engineering and install something from a third party. Of course the software would have to be of the correct architecture.

Cheers & Beers,
uRock

---

### Post by bodhi.zazen on 2010-07-08
The 64 bit kernels are more secure then 32 bit kernels.

Search for things such as memory protection

[http://en.wikipedia.org/wiki/NX_bit](http://en.wikipedia.org/wiki/NX_bit)

You will see the nx bit is available on a 32 bit kernel, but you need the PAE kernel.

See also :

[https://wiki.ubuntu.com/Security/Features#Non-Exec%20Memory](https://wiki.ubuntu.com/Security/Features#Non-Exec%20Memory)

---

### Post by bodhi.zazen on 2010-07-08
> **johngreth said:**
> I've always found 32 bit to be more stable and reliable, but now a days they are about the same. The only reason it really matters is if you have a system with more than 4 gig ram, then you should get 64 bit. Many people have strong feelings about which one to use for different reasons, but I don't think it really matters.

I don't know anything about a difference in security.

32 bit kernels support up to 64 Gb of RAM via the PAE kernel. The PAE kernel is available in the Ubuntu repos.

---

### Post by uRock on 2010-07-08
> **bodhi.zazen said:**
> 32 bit kernels support up to 64 Gb of RAM via the PAE kernel. The PAE kernel is available in the Ubuntu repos.

After reading your link I think I will be installing the PAE kernel on my Netbook. The wiki seems to imply that the NX bit will be activated on 64bit CPUs running 32bit PAE, does it also instill the NX bit into a 32bit OS on a 32bit CPU?

Thanx,
uRock

---

### Post by bodhi.zazen on 2010-07-08
> **uRock said:**
> After reading your link I think I will be installing the PAE kernel on my Netbook. The wiki seems to imply that the NX bit will be activated on 64bit CPUs running 32bit PAE, does it also instill the NX bit into a 32bit OS on a 32bit CPU?

Thanx,
uRock

They are calling it "nx emulation" but I do not honestly know what that means exactly.

---

### Post by uRock on 2010-07-08
I'll give it a try anyway. Maybe the PAE will have something that will make my WiFi work better on the Netbook.

Thanx,
uRock

---

### Post by fipz on 2010-07-08
Thanks for all your answers, especially for wikipedia links, though I knew what NX was (i been general saying it was an instruction set feature), it just didn't seem clear how it was listed on ubuntu web page (about using pae kernel on 32bit), thank you very much for all the explanations and details you given me.

PS: they should remove the "not for everyday" thing near 64 bit edition -.-, since intrepid i never had problem with 64 bit (except some security concerns which been explained by you all right now).

---

### Post by bodhi.zazen on 2010-07-08
> **fipz said:**
> PS: they should remove the "not for everyday" thing near 64 bit edition -.-, since intrepid i never had problem with 64 bit (except some security concerns which been explained by you all right now).

That has been filed as a bug report (not for everyday .... )

---

### Post by cariboo on 2010-07-08
Have a look at the link in [this]("http://ubuntuforums.org/showpost.php?p=9563043&postcount=15") post.

---

### Post by fipz on 2010-07-08
lol yes i seen it on launchpad XD

to be honest i didnt notice many differences, just that concern

---

### Post by Alver on 2010-07-08
> **rookcifer said:**
> It's because 64 bit processors (at least x86_64) have the NX bit, which makes certain regions of memory unable to execute.  This helps protect against certain types of exploits.  (Micro$oft calls this DEP.  With Linux, we call it "NX").

Another benefit is due to the larger registers, one can utilize other techniques like ASLR which, although available on 32 bit machines, are very weakly implemented due to the smaller memory registers. 64 bit platforms don't have that issue.

Bottom line: if you have a 64 bit CPU, you should use a 64 bit OS.  There is zero reason not to in 2010.  Even if you don't have 4+ GB of memory, there are security and performance advantages to using a 64 bit kernel.
I have an issue with the 64 bit version. This is my story: I run an ageeing desktop (512 MB ram, some  7 years old) in dual boot mode Win XP/9.10 32 b. The installation was uneventfull and everything runs fine. Early this year I purchased an Epson SX 410 Stylus all-in-one. It ran well out of the box, both printer and scanning functions (hurray!). Last May I upgraded to 10.04, a little boring perhaps because it took some 3.5 hours, but all went well and my all-in-one continued to perform well (hurray again!).
I recently bought a brand new Toshiba Satellite L505-10M with W7 64 bits and 6 GB ram. I installed a dual boot with 10.04 64 bits, everything went well and performs well EXCEPT the scanner portion of my all-in-one. It simply will not work. Do I have to go back to the 32 bits version? Life without a scanner is difficult for me.

---

### Post by CharlesA on 2010-07-08
Go back to the 32 bit version. Why this is in a thread about 64-bit security is beyond me.

---

### Post by Alver on 2010-07-08
> **CharlesA said:**
> Go back to the 32 bit version. Why this is in a thread about 64-bit security is beyond me.
You are right of course, I was only reacting to the statement in the bottom line of the quoted post. Shall I withdraw my post?

---

### Post by uRock on 2010-07-08
If the software for the scanner is 32bit, then yes you have to install the 32bit OS to use it. I would search really hard for another app to run the scanner before doing a complete reinstall.

---

### Post by OpSecShellshock on 2010-07-08
Don't mean to encourage the OT-ness, but if the all-in-one has a place to connect a removable storage device then you can probably scan directly to that and then connect the drive to the computer in order to transfer and edit the file.

---

### Post by fipz on 2010-07-08
massive off topic? i join, xfce 64bit would be as good as gnome? (i ask that because i noticed of some thousands of bugs corrected in kde lol and few were critical but i think the lightest the DE is the safer you are?)


ps: i know that sounds pathetic but if a little effort would give me a better stability//security i'd go for it, i think i'm ok with any of the 2, tho at the moment i have xubuntu 64 bit alternate cd but not ubuntu lol

---

### Post by oldos2er on 2010-07-08
Xfce and Gnome are two very different DEs (desktop environments). Bitness and/or security aren't really dependent on or related to either, in my opinion.

---

