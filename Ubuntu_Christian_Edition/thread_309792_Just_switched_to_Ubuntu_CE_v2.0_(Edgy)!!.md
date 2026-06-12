---
title: "Just switched to Ubuntu CE v2.0 (Edgy)!!"
date: 2006-11-30
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2006-11-30
Well, I am so happy with how well Ubuntu CE v2.0 (Edgy) has turned out that I decided to switch myself. This was actually a very hard decision since I really had a nice Dapper setup. 

The install went without a hitch, everything worked perfect including my wireless, and all of my tools for building Ubuntu CE are funtioning correctly (so far :)).

I was even able to get VMware server working for testing the iso. I had a few bumps in that process due to some changes in Edgy.

Anyway, I just wanted to let you know how things went with my install.

God Bless, Jereme

---

### Post by doobit on 2006-11-30
Maybe you could list what are the bumps? :)

---

### Post by Darrious on 2006-11-30
That is very good news. It works pretty good for me.

---

### Post by mhancoc7 on 2006-11-30
> **doobit said:**
> Maybe you could list what are the bumps? :)

Yes, I plan to do a post on getting VMware Server working on Ubuntu CE once I get a little time.

> **Darrious said:**
> That is very good news. It works pretty good for me.

Thanks, just let us know if you have any issues.

Jereme

---

### Post by Darrious on 2006-11-30
Well, there is one small problem.

Actually... more of a BIG problem. Because right now I'm running off of the liveCD.
 
When I boot into grub it comes up saying this.
```
Starting Up ...
             [012840124.123] crc error
             [012840124.123] Kernel Panic - not syncing: VFS: Unable to mount root fs on un-known-block(0,0)
             [012840124.123]
```And there is no second choice for me to boot into. This happened after I used the convert script and then rebooted and this happened. I just wonder if I could add another option for me to boot into.:confused:

---

### Post by mhancoc7 on 2006-11-30
> **Darrious said:**
> Well, there is one small problem.

Actually... more of a BIG problem. Because right now I'm running off of the liveCD.
 
When I boot into grub it comes up saying this.
```
Starting Up ...
             [012840124.123] crc error
             [012840124.123] Kernel Panic - not syncing: VFS: Unable to mount root fs on un-known-block(0,0)
             [012840124.123]
```And there is no second choice for me to boot into. This happened after I used the convert script and then rebooted and this happened. I just wonder if I could add another option for me to boot into.:confused:

Wow, that is bizarre. I have not been able to recreate that issue. I will do some more testing.

Did you use the convert_me script (Edgy) on a fresh install of Edgy?

Thanks, Jereme

---

### Post by mysticrider92 on 2006-11-30
> **Darrious said:**
> Well, there is one small problem.

Actually... more of a BIG problem. Because right now I'm running off of the liveCD.
 
When I boot into grub it comes up saying this.
```
Starting Up ...
             [012840124.123] crc error
             [012840124.123] Kernel Panic - not syncing: VFS: Unable to mount root fs on un-known-block(0,0)
             [012840124.123]
```And there is no second choice for me to boot into. This happened after I used the convert script and then rebooted and this happened. I just wonder if I could add another option for me to boot into.:confused:

It looks like your GRUB boot loader configuration got messed up (not a serious problem, you just need to edit a few things). Do you have any live cds that let you access hard drives (such as a Knoppix one) or another computer you can put the drive in to check it? Boot the computer with that, open your Ubuntu partition and check /boot/grub/menu.list (or possibly menu.lst). This file should have an entry that says "title      Ubuntu". Can you post that entry?

---

### Post by Darrious on 2006-11-30
I think that I'm just going to reinstall edgy then CE 2.0 right after that.

---

### Post by mhancoc7 on 2006-11-30
> **Darrious said:**
> I think that I'm just going to reinstall edgy then CE 2.0 right after that.

Did you use the convert_me script initially or did you do a fresh install from the Ubuntu CE LiveCD?

Thanks, Jereme

---

### Post by Darrious on 2006-12-01
I used the convert_me_script. It is working perfectly fine now though.

---

### Post by Darrious on 2006-12-05
And Now it is not.

It was working fine until I just got another Kernel Panic!!! AHHH

I think it has to do with my burned Edgy disk. I think I might just go ahead and install Ubuntu... 6.06

Darn, I wish I could find a solution to this problem, because this has happened to a few other people also, and I can't find a solution.

---

