---
title: "True Crypt 6 has been released"
date: 2008-07-05
forum: Security
---

### Post by hyper_ch on 2008-07-05
I just saw that TC 6 has been released... hidden partitions are now also possible on ext3 - if I read correctly :)

---

### Post by war59312 on 2008-07-06
Too bad I still can't encrypt the OS completely like in Windows...

---

### Post by hyper_ch on 2008-07-06
for that you have luks/dm-crypt ;)

---

### Post by Vivaldi Gloria on 2008-07-06
This looks good:

> Parallelized encryption/decryption on multi-core processors (or multi-processor systems). Increase in encryption/decryption speed is directly proportional to the number of cores and/or processors.

For example, if your computer has a quad-core processor, encryption and decryption will be four times faster than on a single-core processor with equivalent specifications (likewise, it will be twice faster on dual-core processors, etc.)

---

### Post by chrisby on 2008-07-06
I started using it on Saturday.  The Multi processor thing really speeds things up on my system.  Fat32 only by default still sucks, but the program is really improving.

---

### Post by chewearn on 2008-07-09
The old problem with v5, dead slow writing speed on gutsy/hardy.  Anyone seeing this for the new v6?  I'm still using v4.3a due to this problem, but if it's solved in v6, then I will upgrade.

.

---

### Post by hyper_ch on 2008-07-09
meanwhile is already an "a" out :) but multicore support speeds it up massively.

---

### Post by pofigster on 2008-07-09
I'm excited.  I started using v.5 when I read that article about the guy who's laptop was encrypted with similar software and the feds can't crack it and he doesn't have to give up his password.  Hopefully v.6 will really speed things up.

---

### Post by chewearn on 2008-07-09
Could I ask a favor from those already using v6 or v6a.  Try writing a large file to the truecrypt container (large as in few hundred megs).  Does the write speed consistently at 10MB/s or above?  Does the write speed stalling constantly?

I would greatly appreciate the feedback on this one.  Currently, using v4.3a, I have to custom patch the source code, and manual compile.  It would be tedious to install v6 to test this out, then revert back to v4.3a if it's still not solved.  Very much appreciate your assistance.

.

---

### Post by Xmister on 2008-07-09
> **AstalaVista said:**
> ...
I'm already using it on windows and hardy too. The speed is about the same on both systems(avr. 28-32 MB/s, but sometimes it goes up to 60), but on hardy both of my cores running at 70-90% while copying, but I think this is mostly because of the ntfs filesystem.

---

### Post by simonapnic on 2008-07-09
This new version should make things better for everyone using encryption software I guess.
Keep your data safe ! Encrypt it !
I still wonder if it's possible to fully encrypt your harddrive in a dual-boot context (Windows + Linux).

---

### Post by Xmister on 2008-07-09
It's possible, my dual-boot system is fully encrypted :)
See this article: [http://ubuntuforums.org/showthread.php?t=761530&highlight=dual+boot+encrypt]("http://ubuntuforums.org/showthread.php?t=761530&highlight=dual+boot+encrypt")

---

### Post by chewearn on 2008-07-10
> **Xmister said:**
> I'm already using it on windows and hardy too. The speed is about the same on both systems(avr. 28-32 MB/s, but sometimes it goes up to 60), but on hardy both of my cores running at 70-90% while copying, but I think this is mostly because of the ntfs filesystem.

Thanks!  That's what I'm looking for.  Appreciate it.

---

### Post by chewearn on 2008-07-10
Ok, I have installed Truecrypt v6a.  Here is the update:

Slow and stalling write of a large file is STILL a problem.

There is hope though.  When I mount an existing container (created by Truecrypt v4.3a), I got a message box:

[I]The volume you have mounted uses a mode of operation which is not supported by the Linux kernel. You may experience slow performance when using this volume. To achieve full performance, you should move the data from this volume to a new volume created by TrueCrypt 5.0 or later.
[/I]
So, I will now create a new volume and see if the problem goes away.  Further update in a couple of hours.

.

Final update:
Yes, it works.  Reformat old volume solved the problem.

.

---

### Post by bla on 2008-07-12
I would think that you can encrypt a dual boot as long as you install ubuntu as a 2nd OS and put its boot records on the partion that the ubuntu is installed to, rather than the MBR.

VISTA may complicate things but XP/unutu should work.

---

### Post by uzd4ce on 2008-07-13
Does anyone know if there's an option in the Linux version to have it auto-dismount on screensaver activation, like you can in Windows?

Or is there a simple way to have a script or something run a "truecrypt -d" whenever the screensaver comes on?

Thanks

---

### Post by hyper_ch on 2008-07-13
you can lock your computer on screensaver activation - not quite the same but one would have to guess first, that you are using encryption at all...

---

### Post by uzd4ce on 2008-07-13
> **hyper_ch said:**
> you can lock your computer on screensaver activation - not quite the same but one would have to guess first, that you are using encryption at all...

Yeah, but I wouldn't want the file browser to be just sitting there in the clear.  I really miss that auto-dismount feature.  The third-party GUI Forcefield used to do it, but it only works with Truecrypt 4.3.

Anyone still have a 4.3a deb?

---

### Post by hyper_ch on 2008-07-13
why in the clear?

---

### Post by uzd4ce on 2008-07-13
> **hyper_ch said:**
> why in the clear?

There are other users of the computer who may know the screensaver unlock password, but who I don't really want seeing the private stuff that I had mounted. Get it?

Thanks

---

### Post by hyper_ch on 2008-07-13
that's why linux was developped as multi-user system where each user has it's own login....

---

### Post by uzd4ce on 2008-07-13
> **hyper_ch said:**
> that's why linux was developped as multi-user system where each user has it's own login....

Yeah, but when one of those users is your non-techie wife, she'd kinda wonder what you're trying to hide by making her use her own profile... ;)

---

### Post by elfstone2 on 2008-07-15
Will TC6 get into the ubuntu repositories? I have truecrypt 4.2 in repo, but not 5 or 6.. it would like to keep everything i install from repos, so i dont have to take care of updates myself.

---

### Post by hyper_ch on 2008-07-15
download the deb...

---

### Post by elfstone2 on 2008-07-17
Hm, i also have dead slow speed and stalling after writing more than 100mb, even when i create a new volume using v6.

The volume is 180gb big, but that shouldnt be a problem...

---

### Post by chewearn on 2008-07-17
> **elfstone2 said:**
> Hm, i also have dead slow speed and stalling after writing more than 100mb, even when i create a new volume using v6.

The volume is 180gb big, but that shouldnt be a problem...


Unfortunately (fortunately?), I don't see this problem anymore.  I have been re-encrypting tons of data over the last few days, so it's pretty definite.  I have checked this using both hardy and gutsy.

In gusty, truecrypt v6 complains that the older kernel might have a bug that will cause this problem, but then I proceed anyway and it's fine.

---

### Post by elfstone2 on 2008-07-17
Astalavista which version are you using? 

Truecrypt 6? Ubuntu 8.04?

Are there any changes you made, to get it working? How big are your partitions, and how big are the files you're copying?

What filesystems do you use?

There must be a reason why it works for you, but not for me :(

Just in case: Does anyone have working debs for 4.3 and Kernel 2.6.24+?

---

### Post by chewearn on 2008-07-17
> **elfstone2 said:**
> Astalavista which version are you using? 

Truecrypt 6? Ubuntu 8.04?

I'm using truecrypt v6a, ubuntu 8.04 and ubuntu 7.10.

> 
Are there any changes you made, to get it working?
No (other than re-encrypting the containers from v4.3 to v6).

> 
 How big are your partitions, and how big are the files you're copying?

Partitions: Typically 233GB.
Files: few hundred megs to gigabytes in some instances

> 
What filesystems do you use?

fat32 (inside the container).



> 
Just in case: Does anyone have working debs for 4.3 and Kernel 2.6.24+?

I don't have a working deb.  Previously, I have to manually patch and compile the source code.

---

### Post by elfstone2 on 2008-07-21
Hm, strange.. i can see no difference (i also created a new volume with v6, but its horrible slow)

Where can i find the sourcecode for 4.3 and the patches i need for Ubuntu 8.04?

Thx for the help

---

### Post by hyper_ch on 2008-07-22
> **elfstone2 said:**
> Where can i find the sourcecode for 4.3

Where would you start looking for it?

---

### Post by elfstone2 on 2008-07-22
On the truecrypt homepage.

---

### Post by hyper_ch on 2008-07-22
is it there?

---

### Post by elfstone2 on 2008-07-22
Why do you think i ask here?

---

### Post by hyper_ch on 2008-07-22
so you did not check yourself?

---

### Post by elfstone2 on 2008-07-22
Of course i did. Its not there, so if somebody wants to help and knows where i can find the source for 4.3 and the patches, please tell me. 

And if you dont want to help hyper, just dont help me...

---

### Post by hyper_ch on 2008-07-22
> **elfstone2 said:**
> Of course i did.

How am I supposed to know that? ;)

---

### Post by chewearn on 2008-07-22
> **elfstone2 said:**
> Of course i did. Its not there, so if somebody wants to help and knows where i can find the source for 4.3 and the patches, please tell me. 

And if you dont want to help hyper, just dont help me...

Yeah, they removed the v4.3a source code from truecrypt.org website.  But I still have a copy of the source codes.  Send me a PM.

You can get the patch here (post #4), plus instructions:
[http://ubuntuforums.org/showthread.php?t=647339](http://ubuntuforums.org/showthread.php?t=647339)

---

