---
title: "Dual Boot Virus"
date: 2009-02-19
forum: Security
---

### Post by athealwashington on 2009-02-19
Hi, I have a little question here.


My question won't make any sense if you don't know my hard drive configuration. Here it is:


40GB Maxtor with Windows XP on it. NTFS.


320GB with Ubuntu on it. Ext2.


 I use windows a lot for running unknown programs, to tell you the truth I am down right careless with Windows.  I use avast! though.

I don't log in to any of my accounts thorw windows.

I DO LOG INTO my bank accounts throw ubuntu though.

I am very very careful with Ubuntu (security wise).


So I am wondering if my Windows gets infected is there any viruses designed to infect Linux while running on windows?

---

### Post by whoop on 2009-02-19
No

---

### Post by howefield on 2009-02-19
> **athealwashington said:**
> .....to tell you the truth I am down right careless with Windows.  I use avast! though.

I don't log in to any of my accounts thorw windows.

I DO LOG INTO my bank accounts throw ubuntu though.

I am very very careful with Ubuntu (security wise).


So I am wondering if my Windows gets infected is there any viruses designed to infect Linux while running on windows?

The worst virus a computer comes up against tends to be the one sitting in front of the keyboard, and given your self confessed disregard for one of your operating systems, well, you get the drift... ;)

But you are unlikely to be infected by a virus crossing from your windows partition, but it is software, anything is possible.

---

### Post by bodhi.zazen on 2009-02-19
> **athealwashington said:**
> Hi, I have a little question here.


My question won't make any sense if you don't know my hard drive configuration. Here it is:


40GB Maxtor with Windows XP on it. NTFS.


320GB with Ubuntu on it. Ext2.


 I use windows a lot for running unknown programs, to tell you the truth I am down right careless with Windows.  I use avast! though.

I don't log in to any of my accounts thorw windows.

I DO LOG INTO my bank accounts throw ubuntu though.

I am very very careful with Ubuntu (security wise).


So I am wondering if my Windows gets infected is there any viruses designed to infect Linux while running on windows?

None have been reported, does not mean tomorrow it will not be written.

---

### Post by Slim Odds on 2009-02-20
> **whoop said:**
> No

LOL, the naivete.

Listen, you may not know of any, but it's not only possible, it's not really **that** difficult.

Read my post in this thread: [http://ubuntuforums.org/showthread.php?t=1071615](http://ubuntuforums.org/showthread.php?t=1071615)

If you need more details, I'll try to get to it later.....

---

### Post by Tubes6al4v on 2009-02-20
This is what I thought: If you have Ext2/3/4 drivers on your windows side, a virus could scan your linux drive for sensetive information.

Is this right?

---

### Post by cariboo on 2009-02-20
@Slim Odds

You are making an assumption that can't happen, the Windows Administrator account is not like the root account in Linux. 

You say that it is easy to become root in Windows and then infect a Linux distribution, please show us how.

Even if you can copy a malware executeable to a linux partition, you still have to make it executeable and have it start at boot. The only way you are going to be  able to do that is to have physical access to the computer.

Jim

---

### Post by Slim Odds on 2009-02-20
> **Tubes6al4v said:**
> This is what I thought: If you have Ext2/3/4 drivers on your windows side, a virus could scan your linux drive for sensetive information.

Is this right?

Mostly....

If you have an active internet connection and a virus gets control of your windows machine (while it's running windows), it could download **anything** it wants. Including file system drivers, etc.

Once it does that, it can read and write **any** part of the file system it wants.

This means that it can read **any** information (sensitive or not), as well as write **anything** it wants (meaning that it can compromise your linux installation). This means that even when you boot into linux, you might have some of **their** code running on your machine **with root access.**

---

### Post by xzero1 on 2009-02-20
For critical access on the net use a read only live cd (with no room for extra sessions).  You might even store critial data encrypted on a removeable drive and only access it from your live cd. The live cd may not be up to date security wise, but at least it could not be infected by windows.

---

### Post by Slim Odds on 2009-02-20
> **cariboo907 said:**
> @Slim Odds

You are making an assumption that can't happen, the Windows Administrator account is not like the root account in Linux. 

You say that it is easy to become root in Windows and then infect a Linux distribution, please show us how.

Even if you can copy a malware executeable to a linux partition, you still have to make it executeable and have it start at boot. The only way you are going to be  able to do that is to have physical access to the computer.

Jim

Jim, I'm not making any assumptions. The Administrator account in windows is **equivalent to **the root account in linux. It allows the user to do what they want. They can access any hardware that they want and install any drivers that they need.

I'm not a virus writer, but you must know that there are plenty of ways to get "root" access on windows machines remotely. Do a little research if you've never heard of this before (try some of these in google: "internet explorer", botnet, rootkit). There are plenty of known weaknesses on a very high percentage of windows machines that connect to the internet.

For your third paragraph, you couldn't be more wrong. Once a windows machine is compromised and the remote user has administrative access, they don't need to be "on site". They have access to your hardware and all they need to do is write to your hard drive. Heck, they could just replace your linux kernel. They could erase everything and install OpenBSD.

---

### Post by Hyper Tails on 2009-02-20
That depends what virus it gets infected by
because if you have wine or any other linux emulator, some windows viruses can run with wine.

thats only if you mount the partition

---

### Post by xzero1 on 2009-02-20
> For your third paragraph, you couldn't be more wrong. Once a windows machine is compromised and the remote user has administrative access, they don't need to be "on site". They have access to your hardware and all they need to do is write to your hard drive. Heck, they could just replace your linux kernel. They could erase everything and install OpenBSD.So the question becomes is there any way to detect that linux has been compromised? I would say yes, (using signatures for critical files) but *only* if that detection was external to linux itself.

---

### Post by Slim Odds on 2009-02-20
> **xzero1 said:**
> So the question becomes is there any way to detect that linux has been compromised? I would say yes, (using signatures for critical files) but *only* if that detection was external to linux itself.

Exactly.

My point is that disks are just bit and bytes. And that in any dual boot system either OS has **complete and total access** to the data on the drives.

Each OS knows how to limit access to it's own file system **when it's the one that's running.** So, for example, when linux is **not running**, it cannot protect it's file system. Simple as that.

And the same goes for **any two** operating systems.

---

