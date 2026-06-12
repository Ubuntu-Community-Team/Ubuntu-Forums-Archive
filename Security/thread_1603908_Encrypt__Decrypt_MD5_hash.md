---
title: "Encrypt / Decrypt MD5 hash"
date: 2010-10-23
forum: Security
---

### Post by karthick87 on 2010-10-23
How to encrypt and decrypt MD5 hash...?

---

### Post by BkkBonanza on 2010-10-23
Do you mean to ask how to check a md5 checksum of a file?

**md5sum filename**

If you don't have md5sum installed then you need to **sudo apt-get install coreutils** first.

Otherwise, not sure what you mean here.

---

### Post by karthick87 on 2010-10-23
This is MD5 Hash

[SIZE=4] [COLOR=Red]4786f3282f04de5b5c7317c490c6d922[/COLOR][/SIZE]

How to decrypt this..?

---

### Post by Dave_L on 2010-10-23
You can't.

You can compute the MD5 hash of a file to see if it matches that one, but you can't recover a file from its MD5 hash.

---

### Post by anomie on 2010-10-23
[QUOTE=getyourkarthick]How to encrypt and decrypt MD5 hash...?[/QUOTE]

Recommended reading: [http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)

The best you can do is brute force it. (Actually that's not exactly true, but if you have to ask this question my guess is you won't be cryptanalyzing it.)

---

### Post by wacky_sung on 2010-10-23
> **getyourkarthick said:**
> This is MD5 Hash

[SIZE=4] [COLOR=Red]4786f3282f04de5b5c7317c490c6d922[/COLOR][/SIZE]

How to decrypt this..?

I bet you are trying something malicious to crack the userpassword.

Just a hint:use rainbow table.

Password = vvv

---

### Post by mainerror on 2010-10-24
> **wacky_sung said:**
> I bet you are trying something malicious to crack the userpassword.

Just a hint:use rainbow table.

Password = vvv

You know it might not really add to security if you help someone to crack a password. You should point him in the right directions at most in my opinion.

---

### Post by BkkBonanza on 2010-10-24
I thought linux passwords were hashed with SHA256 and salted. I don't see how rainbow tables would help with that - or maybe I'm wrong. Based on the question and level of knowledge the OP doesn't appear to be trying to do this anyway. This thread has gotten way off track.

---

### Post by wacky_sung on 2010-10-24
> **BkkBonanza said:**
> I thought linux passwords were hashed with SHA256 and salted. I don't see how rainbow tables would help with that - or maybe I'm wrong. Based on the question and level of knowledge the OP doesn't appear to be trying to do this anyway. This thread has gotten way off track.

FYI it has nothing to do with linux passwords.The md5sum is found through SQL injection in the web application where you can found the username and password in md5sum.

> **mainerror said:**
> You know it might not really add to security if you help someone to crack a password. You should point him in the right directions at most in my opinion.

He shall be social responsibility for his own action.Probably he just wanna use it for learning.

[[IMG]http://img253.imageshack.us/img253/1613/screenshotubuntuforumsm.th.png[/IMG]](http://img253.imageshack.us/i/screenshotubuntuforumsm.png/)

---

### Post by Ahava591 on 2010-10-24
> **wacky_sung said:**
> 


He shall be social responsibility for his own action.Probably he just wanna use it for learning.





And you are "social responsibility," for contributing to every suspicious question and activity.

That said, I sincerely wish the OP good luck if they're conducting legitimate activity.

---

### Post by BkkBonanza on 2010-10-24
This forum is not for posting information about how to crack passwords. There are other places on the net for that. I'll report this thread and suggest it be closed.

---

### Post by wacky_sung on 2010-10-24
> **BkkBonanza said:**
> This forum is not for posting information about how to crack passwords. There are other places on the net for that. I'll report this thread and suggest it be closed.

I think it better to get enlightened than being ignorance about it.I do read before Ubuntu has an alternative of using md5sum in which i have read it before.Beside that, md5sum is use to verify the integrity of downloaded ISO image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

It is just like you have a gun to kill or protect the innocent.It just a thin line of choice to make.

---

### Post by BkkBonanza on 2010-10-24
There is no problem with discussing md5sum here. The problem is with directing people on how to use rainbow tables for cracking passwords along with sql injection. As I said, there are places where that is appropriate but not here. This forum is intended as a help resource for Ubuntu users, not a cracking tutorial site.

---

### Post by wacky_sung on 2010-10-24
> **BkkBonanza said:**
> There is no problem with discussing md5sum here. The problem is with directing people on how to use rainbow tables for cracking passwords along with sql injection. As I said, there are places where that is appropriate but not here. This forum is intended as a help resource for Ubuntu users, not a cracking tutorial site.

I only show people how to md5sum is being crack by using rainbow table.I only trying to tell you that md5sum password can be retrieved when cracker use it for SQL injection.I do not think you know what you are talking about.

I bet you do not understand what is cyber security as my intended intension.I do not think you are deem fit to write here as a moderator since you do not even know how to distinguish black / white hat.

FYI:NO offenses to what i wrote.

---

### Post by bodhi.zazen on 2010-10-24
> **wacky_sung said:**
> I bet you do not understand what is cyber security as my intended intension.I do not think you are deem fit to write here as a moderator since you do not even know how to distinguish black / white hat.

FYI:NO offenses to what i wrote.

These things are tools and can be used by all hats (white/gray/black). We do not know the intentions of the OP.

IMO if you are passing passwords over the internet to a web site you should use ssl (https).

---

