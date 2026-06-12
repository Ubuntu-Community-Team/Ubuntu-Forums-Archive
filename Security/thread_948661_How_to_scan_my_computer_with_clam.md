---
title: "How to scan my computer with clam"
date: 2008-10-15
forum: Security
---

### Post by Fertech on 2008-10-15
I'm trying to scan my computer with clam but i can't seem to find the program. i did a freshclam, but i don't have permission. i can i give it permission and run it. I have two operating system i want it to scan both the other operating system is windows xp.

---

### Post by bcom on 2008-10-15
I cant be sure from your post whether or not you have actually installed clamav on your system.  If not, this can be done via synaptic package manager.

Once clamav is installed you can type clamscan -r in Terminal.  This will scan your home directory and everything in it.

Here is a link that might help you to figure out how to scan your windows partition:  [http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html](http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html)

In Terminal type man clamscan for info on clamav.

---

### Post by cariboo on 2008-10-15
I've been playing with clamscan this afternoon, what I create a directory called infected in my home directory then in a terminal I cd in to /:

```
cd /
```

I then ran a recursive scan of the whole installation. I also mount my Vista partition and it is being checked as I type this:

```
sudo clamscan -r --move=/home/user/infected
```

I have a couple of windows viruses stored in another directory, so we will see what happens.

Jim

---

### Post by PocketDog on 2008-10-20
I use ```
sudo clamscan /media/Vista -r -i --bell
```
That will display affected files only, not move them, (If it's a false positive I'd rather not try and figure out where clamscan moved it from so I can put it back) and ring a bell when something suspicious is found.

---

### Post by Dr Small on 2008-10-20
Why do you need to use clamav?

---

### Post by PocketDog on 2008-10-21
[QUOTE=Dr Small]Why do you need to use clamav?[/QUOTE] My family use my laptop when the PC is occupied, which is the only reason Vista is still on it. I'd rather not boot into Vista myself just to scan it for nasties so I do that using clamAV.

---

### Post by hyper_ch on 2008-10-21
are you sure you even need antivirus?

---

### Post by Dr Small on 2008-10-21
> **PocketDog said:**
> My family use my laptop when the PC is occupied, which is the only reason Vista is still on it. I'd rather not boot into Vista myself just to scan it for nasties so I do that using clamAV.
ClamAV is not going to scan your Vista partition for viruses, and those virus won't spread and infect your Linux partition.

---

### Post by dave.com on 2008-10-24
I removed Vundo trojan, MicroAV 2009 from XP, 4 .dll's installed as service using Clamtk in my Ubuntu installation. Maybe Ubuntu don't need anti-virus but a) Windows does b) ClamTK is free if Windows aint just dandy. Its not a big deal to want AV in Linux as a fallback even if that is not Ubuntu's primary usefullness.

---

### Post by nubdora on 2008-10-24
> **Dr Small said:**
> ClamAV is not going to scan your Vista partition for viruses, and those virus won't spread and infect your Linux partition.

ClamAV can scan any partition if said partition is properly mounted. He may be using a live disk too, no?

I believe he was saying he didn't want to boot into Windows to scan for viruses, but would rather do it through Ubuntu. 

That being said, he is better off fixing windows problems with windows software as linux software tends to not work as well as expected (obviously) and create false positives.

---

### Post by PocketDog on 2008-10-25
Just to clear up a small point: This thread wasn't started by me, I was offering advice more than asking for it ;)
I know what I'm doing with Windows, my Vista and XP installations have security software coming out of their ears, yet I'm still more comfortable using HijackThis (for instance) to manually check my installed and running processes/services. I know what should be there and what shouldn't, what I put there and what I didn't.

I think, in answer to the original post (how to scan with clamscan), my reply was the best.

For my purposes...

---

### Post by Fertech on 2008-11-03
this post was created by me. i can also secure windows xp very good, and i also used Hijackthis. i was just asking cause sometimes my sisters computer gets infected and she comes to me, to fix it. i was just wondering if its best to scan her win xp with my clam. but i think since linux and windows have different maybe its not a good idea to scan windows from Linux.

---

