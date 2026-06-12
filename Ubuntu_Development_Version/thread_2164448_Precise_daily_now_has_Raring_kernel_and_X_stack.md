---
title: "Precise daily now has Raring kernel and X stack"
date: 2013-07-31
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-07-31
Not a whole lot to add to the title, but 12.04.3 is due 20130824 and the Raring kernel and X stack have hit the repos over the past week or so.

I tested it today and it seemed quite stable ................. and fast!

I hope the Saucy kernel and X stack will hit 12.04.4 but I have doubts.

Regardless it's all still fun :D

---

### Post by ventrical on 2013-07-31
Thanks for the update.

btw .. having fun is the main thing :)lol

---

### Post by QDR06VV9 on 2013-07-31
> > **kansasnoob said:**
> Not a whole lot to add to the title, but 12.04.3 is due 20130824 and the Raring kernel and X stack have hit the repos over the past week or so.

I tested it today and it seemed quite stable ................. and fast!

I hope the Saucy kernel and X stack will hit 12.04.4 but I have doubts.

Regardless it's all still fun :D

kernel 3.11 on raring is lighting fast

> **ventrical said:**
> Thanks for the update.

btw .. having fun is the main thing :)lol

ventrical its good to see you made it back!!

---

### Post by ventrical on 2013-07-31
> **runrickus said:**
> 

kernel 3.11 on raring is lighting fast



ventrical its good to see you made it back!!

Thanks for making my day! :)

Honestly .. I haven't had the time to test the new kernel. With kansasnoob working as hard as he does, I'll bet it's awesome :)

---

### Post by NikTh on 2013-07-31
> **kansasnoob said:**
> Not a whole lot to add to the title, but 12.04.3 is due 20130824 and the Raring kernel and X stack have hit the repos over the past week or so.

I tested it today and it seemed quite stable ................. and fast!

I hope the Saucy kernel and X stack will hit 12.04.4 but I have doubts.

Regardless it's all still fun :D


Ohh, why you told me ? Why you told me ? :P 

Now  it's time for a new installation, ya ? 12.04.2 sat too long on my laptop :) 

Thanks for the update !

---

### Post by QDR06VV9 on 2013-07-31
> **ventrical said:**
> Thanks for making my day! :)

Honestly .. I haven't had the time to test the new kernel. With kansasnoob working as hard as he does, I'll bet it's awesome :)

3.11.0-031100rc3-generic on raring with nvidia-325 is a noticeable improvement for my useage.
Havent tested thourghly on saucy yet! having to much fun on raring:D

---

### Post by NikTh on 2013-08-01
Something else about the Daily iso. I saw that it has the proposed repositories enabled by default. /etc/apt/sources.list.d/proposed.list. I removed them before a full system upgrade.

---

### Post by ventrical on 2013-08-01
Mixed results here for today. On nVidia based machine (GeForce 210/218) I just get the purple screen with the keyboard  and the man in the circle. It will not budge.

On ATi I can get to live but there is a lot of weird screen while booting and it is very slow to boot.

---

### Post by kansasnoob on 2013-08-01
> **ventrical said:**
> Mixed results here for today. On nVidia based machine (GeForce 210/218) I just get the purple screen with the keyboard  and the man in the circle. It will not budge.

On ATi I can get to live but there is a lot of weird screen while booting and it is very slow to boot.

I'd only tried it on my Intel box :(

Maybe the X-stack is not yet complete.

---

### Post by QDR06VV9 on 2013-08-01
> **ventrical said:**
> Mixed results here for today. On nVidia based machine (GeForce 210/218) I just get the purple screen with the keyboard  and the man in the circle. It will not budge.

On ATi I can get to live but there is a lot of weird screen while booting and it is very slow to boot.

Ventrical i had to install nvidia-325 I had noticed it it did not like nvidia-310
But 325 works good for me, our cards are close.

---

### Post by ventrical on 2013-08-01
> **kansasnoob said:**
> I'd only tried it on my Intel box :(

Maybe the X-stack is not yet complete.

On my Intel machine I am getting the same as ATi...an opening screen with top bars and an IBus message .."super + Space is now the default Hotkey" and then it goes to Ubiquity.

Here is Intel and ATi (Radeon) towers .. same image.. saucy-desktop-i386 today's daily current:

---

### Post by ventrical on 2013-08-01
@kansasnoob

  I just noticed that this is Precise update  Raring kernel topic forum ... boy oh boy .. I got too much saucy on my mind :)lol

---

### Post by NikTh on 2013-08-01
> **ventrical said:**
> @kansasnoob

  I just noticed that this is Precise update  Raring kernel topic forum ... boy oh boy .. I got too much saucy on my mind :)lol

Come on man.. you scared me.. :P 

Precise daily it's working very good. Stable and Fast. 

Again : Thank @kasanoob for the update. 

**Question:** When the stable version released (22th August), If I would not reinstall but stick with this daily iso instead , do I miss something ? any side effects ?

Thanks

---

### Post by ventrical on 2013-08-01
> **NikTh said:**
> Come on man.. you scared me.. :P 

Precise daily it's working very good. Stable and Fast. 

Again : Thank @kasanoob for the update. 

**Question:** When the stable version released (22th August), If I'm not re-install and stick with this daily iso, do I miss something ? any side effects ? 

Thanks

Ok.. I zsynced it and it *is* really fast.. it is faster on my USB 3.0 than the hardrive.!! :)  Who needs hdds  anymore jk :)lol

---

### Post by kansasnoob on 2013-08-02
> **NikTh said:**
> Come on man.. you scared me.. :P 

Precise daily it's working very good. Stable and Fast. 

Again : Thank @kasanoob for the update. 

**Question:**[B][COLOR="#FF0000"] When the stable version released (22th August), If I would not reinstall but stick with this daily iso instead , do I miss something ? any side effects ?
[/COLOR][/B]
Thanks

Hmmm, that's not something I can answer with a simple yes or no. [As you mentioned here]("http://ubuntuforums.org/showthread.php?t=2164448&p=12741541#post12741541") Precise LTS dev and maintenance releases handle proposed updates different than later dev releases. I can't quite remember if that changed in Quantal or Raring?

So, ***to be safe***, I'd say an LTS maintenance release should be installed post-release if it's going to be used on a production machine or any machine where security is a huge issue. In my case I test these maintenance releases to check for problems that may have been created while upgrading the kernel and X-stack (also patches to grub-pc).

Ultimately the past few dev cycles have introduced a great number of changes and it requires some serious thought to put all of the changes into context. Most recently the support cycle for "normal/interim" releases dropped from 18 months to 9 months, but before that the LTS desktop support increased to 5 years.

That LTS support change included upgrading the kernel and X-stack along with any needed patches for grub-pc to support newer hardware. Of course the LTS will typically still have the older and more stable versions of apps unless some dev or maintainer went through the difficult exception process.

Have I totally confused you yet?

---

### Post by NikTh on 2013-08-02
> **kansasnoob said:**
> Hmmm, that's not something I can't answer with a simple yes or no. [As you mentioned here]("http://ubuntuforums.org/showthread.php?t=2164448&p=12741541#post12741541") Precise LTS dev and maintenance releases handle proposed updates different than later dev releases. I can't quite remember if that changed in Quantal or Raring?

So, ***to be safe***, I'd say an LTS maintenance release should be installed post-release if it's going to be used on a production machine or any machine where security is a huge issue. In my case I test these maintenance releases to check for problems that may have been created while upgrading the kernel and X-stack (also patches to grub-pc).

Ultimately the past few dev cycles have introduced a great number of changes and it requires some serious thought to put all of the changes into context. Most recently the support cycle for "normal/interim" releases dropped from 18 months to 9 months, but before that the LTS desktop support increased to 5 years.

That LTS support change included upgrading the kernel and X-stack along with any needed patches for grub-pc to support newer hardware. Of course the LTS will typically still have the older and more stable versions of apps unless some dev or maintainer went through the difficult exception process.

**Have I totally confused you yet?**

Completely :P 

So, If I want to be sure that I have a stable LTS release, I have to reinstall in 22th August, regardless if the daily iso seems stable and without problems. When I installed it, I disabled the proposed repositories, before upgrade the system and during installation I didn't tick the box of "installing updates during install.." . But I think it would be more safe to reinstall when the stable release comes out on 22th August. We will see until then :-)

**EDIT:** 
And for the first time after almost 2 years, Fn+F4 works !!! (suspend). This kernel is good !

---

