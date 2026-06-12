---
title: "Wubi testing/need to know if this is a legal Win 8 DL"
date: 2012-01-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-01-27
Maybe this seems like a dumb question but I tend to think the only dumb question is the one you don't ask ;)

Many of you know that I do a lot of iso/upgrade testing and I'm preparing for Alpha 2 testing. I typically wait until Beta 1 to try anything Wubi, in fact I think I was once told to do that by either Colin Watson or Evan Dandrea, but look at this bug report:

[https://bugs.launchpad.net/wubi/+bug/907524](https://bugs.launchpad.net/wubi/+bug/907524)

This will be the first time Lubuntu should be supported by Wubi so, time allowing, I thought I'd give it a try. But my only old Win XP box is out on loan while I'm fixing someone else's computer. (Full disclosure: only the puter is out on loan with just Lucid installed).

But I'm thinking I could try a Wubi install with Win 8, but only if this is truly a legal DL!!!!!

Is it:

[http://www.forumswindows8.com/windows-8-download/](http://www.forumswindows8.com/windows-8-download/)

---

### Post by lucazade on 2012-01-27
What is Windows? :-k

---

### Post by bennachie on 2012-01-27
The Developer Preview images were released to the public by Microsoft some time ago, and copies can be found on the DVDs attached to several computer magazines. I think you would be perfectly safe to proceed. However, whether or not they will work with Wubi is definitely in the lap of the gods - the DP images are explicitly not feature complete, and seem to be mainly intended to showcase the new GUI).

---

### Post by kansasnoob on 2012-01-27
> **lucazade said:**
> What is Windows? :-k

I hear ya :lolflag:

But with my devotion to installation testing Wubi is part of it, especially since beginning with Maverick they introduced the "Wubi offered if four primary partitions already exist" option.

Really ............. it really does!

And IMHO they have ubiquity working well, although I still think they were foolish to drop the separate "use largest free" option, but I'm done with that argument as of:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

We are where we are, I'm just looking for the best possible testing options and I don't want to break any laws. I could alternatively install XP to test Lubuntu Wubi but it would only be good for 30 days :)

I'm not a thief!

---

### Post by lucazade on 2012-01-27
thanks for investing time in testing.. it'll surely help to get a better product!

---

### Post by kansasnoob on 2012-01-27
> **bennachie said:**
> The Developer Preview images were released to the public by Microsoft some time ago, and copies can be found on the DVDs attached to several computer magazines. I think you would be perfectly safe to proceed. However, whether or not they will work with Wubi is definitely in the lap of the gods - the DP images are explicitly not feature complete, and seem to be mainly intended to showcase the new GUI).

My only concern ATM is if they're legal :D

Were it not for Wubi testing I'd never look at Windows.

---

### Post by Megaptera on 2012-01-27
This Microsoft site is offering Windows 8 developer preview downloads:

[http://msdn.microsoft.com/en-us/windows/apps/br229516](http://msdn.microsoft.com/en-us/windows/apps/br229516)

I guess they're legal?!

---

### Post by kansasnoob on 2012-01-27
If anyone thinks I'm just talking BS look:

[http://ubuntuforums.org/showthread.php?t=1736586](http://ubuntuforums.org/showthread.php?t=1736586)

No one stepped up so I ended up here:

[https://bugs.launchpad.net/wubi/+bug/771517](https://bugs.launchpad.net/wubi/+bug/771517)

That was a damn tense several hours :)

I'm often full of BS but I never lie. No need because I'm not married :D

---

### Post by grahammechanical on 2012-01-27
As I was reading through that last thread that you posted, some words came to mind: "It seemed like a good idea at the time."

I guess that someone thought that WUBI would be a good idea. A lot of us do not appreciate that turning a good idea into something good takes a lot of effort and often by only a few people.

Well done!

I went to a Microsoft UK site and got the same link as megaptera provided. So, I guess that it is a legal download. And as no body is selling anything it is unlikely to be a fake site.

Regards.

---

### Post by pajn on 2012-01-27
Yep win 8 is fully legal to download. In some countries it may be illegal to download it from other places than Microsofts own homepage however...
But anyway I suggest you to download it directly from Microsoft as you in that way are sure of getting a version that isn't modified.

If it is a good idea to look for bugs in Wubi when it is running on a developer release is however questionable. The bugs may be because of
Windows and not Ubuntu/Wubi.

---

### Post by kansasnoob on 2012-01-27
> **grahammechanical said:**
> As I was reading through that last thread that you posted, some words came to mind: "It seemed like a good idea at the time."

I guess that someone thought that WUBI would be a good idea. A lot of us do not appreciate that turning a good idea into something good takes a lot of effort and often by only a few people.

Well done!

I went to a Microsoft UK site and got the same link as megaptera provided. So, I guess that it is a legal download. And as no body is selling anything it is unlikely to be a fake site.

Regards.

Wubi is a good idea. It's not as stable as a "hard" install, but a lot of new Win boxes and laptops have 4 primary partitions so it's super sweet to offer Wubi from the installer menu :)

I've done fairly extensive testing with the live-installer (ubiquity) and I'm about 95% happy, but some old GUI bugs have recently resurfaced :(

I think most of the GUI problems are either gtk or python related, and maybe some transition to qt, but that's all beyond my level of comprehension.

---

### Post by bcbc on 2012-01-27
I had a problem installing wubi with Win 8, but I think it's because I was running win8 in a virtual machine (and my win8 didn't work very well).

But I have seen threads where people have installed wubi with win8 so it seems like it should work fine. The problems mentioned were that upon restart Windows didn't offer the choice between Windows or Ubuntu (which happens in win7 as well), so you might need to go to "Startup & Recovery" settings and ensure that the 'Time to display operating systems' is set to 10. Or you can use bcdedit to do the same.

Good luck!

---

### Post by kansasnoob on 2012-01-27
> **bcbc said:**
> I had a problem installing wubi with Win 8, but I think it's because I was running win8 in a virtual machine (and my win8 didn't work very well).

But I have seen threads where people have installed wubi with win8 so it seems like it should work fine. The problems mentioned were that upon restart Windows didn't offer the choice between Windows or Ubuntu (which happens in win7 as well), so you might need to go to "Startup & Recovery" settings and ensure that the 'Time to display operating systems' is set to 10. Or you can use bcdedit to do the same.

Good luck!

Well, without that loaner box I have three choices:

(1) Don't bother and just wait until Beta 1.

(2) Load XP on my common test box which takes about 3 hours, and it expires after 30 days.

(3) Try Win 8.

I've been tossing around the thought that I may actually have to buy an OEM (system builders) copy of Win to do my testing :)

Worse things have happened.

---

### Post by ronacc on 2012-01-27
give win 8 a try its legal , it will even activate itself . Don't expect everything to work though MS hasn't updated all of their stuff to run on win 8 , if people are reporting it works go for it .

---

### Post by xyzzyman on 2012-01-28
It's legal but time limited. Eventually it won't even let you log in.

---

### Post by joeyignorant on 2012-01-28
Well considering that the download link points to microsofts servers it's a pretty safe assumption that it's legal although th beta will be out in a week or so personally I'd wait

---

