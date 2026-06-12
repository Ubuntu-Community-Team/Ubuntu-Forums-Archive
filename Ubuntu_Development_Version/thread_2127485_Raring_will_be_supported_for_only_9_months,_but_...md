---
title: "Raring will be supported for only 9 months, but ........."
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-03-20
I first caught the news regarding this on the Lubuntu QA mailing list:

[http://fridge.ubuntu.com/2013/03/19/ubuntu-technical-board-looks-at-shuttleworths-proposal-for-release-management-methodology/](http://fridge.ubuntu.com/2013/03/19/ubuntu-technical-board-looks-at-shuttleworths-proposal-for-release-management-methodology/)

Of importance ATM:

> What does this mean for users?

This means that the TB voted that **[COLOR="#FF0000"]the 13.04 release will get nine months of support[/COLOR]**. There was discussion about applying the principle retroactively, back to the 12.10 release; however, the TB felt this was backing out a promise and they did not want to set such a precedent.

But there is a "but":

> What does this mean for users?

This is akin to providing what Rick Spencer had labelled a “rolling release”. The general idea being that a user could opt for continuous upgrades on what is essentially the development release. For example, if a user was running the development series and updating daily then when 13.04 became a standard/non-LTS release, that user wouldn’t have to to do anything to then start getting updates for the 13.10 release.

The TB voted to allow the development team to enable this capability of tracking the development release without intervention. However, **[COLOR="#FF0000"]the specific implementation questions yet to be determined include how to enable users to continuously track the development focus of Ubuntu without having to explicitly upgrade[/COLOR]**.

So the support period is determined but all else is still TBD :)

I honestly think this sounds good :guitar:

---

### Post by mikewhatever on 2013-03-20
Shortening the non-LTS support cycle is, IMHO, a good idea, but the development release can be a nightmare from the support point of view, if not done right. Hope it will be clearly labeled as unstable.

---

### Post by dino99 on 2013-03-20
AS i've understood, the "stable" upstream package will be landing into the repos, instead of the actual release freeze. I think its way better than the backports system. And the good thing is about bugs being "on progress" instead of being left over when a new u+1 is built. I suppose the "montly" cadence will be followed now.

---

### Post by grahammechanical on 2013-03-20
I think that Mark put it well and shows the way things are going to go. If you want stable Ubuntu install an LTS. There will be point 4 releases in the first two years for those who need LTS on the latest hardware and after that there will be the new LTS (14.04).

If you want "bleeding edge" (to quote Mark) then you run the development branch. At the moment the name of the repositories is the same as the release code name. That is precise, quantal, raring. At the moment we edit the sources list every six months to change to the next development branch. How will this be handled in future? Will there be one development branch repository that gets updated daily for ever and ever? Or will there be a development branch repository that will last for 2 years and then have a restart with the fresh code of the LTS release. This, I think, has to be worked out. Awaiting for information with interest.

The news that Raring will only get 9 months support is a big hint that there will not be a 13.10 release. Although they do say: [COLOR=#333333][FONT=Lucida Grande] > effective in 13.04 release _and later_[/FONT][/COLOR] So, we take it one day at a time.

---

### Post by craig10x on 2013-03-20
One of the ubuntu developers mentioned something about using a "symlink" so that you wouldn't have to upgrade to move to the next version of ubuntu being developed in development branch..
Anyone have any idea of what that is and how that might work?

Also, this is the first time i have run development branch (with 13.04) and it's been very reliable for me as far as updates is concerned (except for the brief sound breakage in VLC media player)...and using this new "system" they are supposed to put in for 13.04 (where you could just roll into the next version) i am tempted to stay on it...

My question is: Was 13.04 this reliable (in the updates) in it's early stages as it has been the last 2 months or so (that's when i installed it)...?

By the way, it was mentioned that the change will be effective as of 13.04 (that you will be able to start rolling with development, although they are not going to call it "rolling"....lol)...
[http://www.webupd8.org/2013/03/ubuntu-technical-board-meeting.html](http://www.webupd8.org/2013/03/ubuntu-technical-board-meeting.html)

---

### Post by sgage on 2013-03-20
> **craig10x said:**
> One of the ubuntu developers mentioned something about using a "sim file" so that you wouldn't have to upgrade to move to the next version of ubuntu being developed in development branch..
Anyone have any idea of what that is and how that might work?

Also, this is the first time i have run development branch (with 13.04) and it's been very reliable for me as far as updates is concerned (except for the brief sound breakage in VLC media player)...and using this new "system" they are supposed to put in for 13.04 (where you could just roll into the next version) i am tempted to stay on it...

My question is: Was 13.04 this reliable (in the updates) in it's early stages as it has been the last 2 months or so (that's when i installed it)...?

By the way, it was mentioned that the change will be effective as of 13.04 (that you will be able to start rolling with development, although they are not going to call it "rolling"....lol)...

Raring has been quite reliable for me, and I've been on it for at least 2 months as my main system. However, I only use Gnome Shell, so I have not been exposed to any bugs/regressions/etc. that might occur in Unity.

---

### Post by craig10x on 2013-03-20
thank you, sgage...actually, the unity updates have been 100% trouble free all along (i have found)...if anyone else ran 13.04 since early in the development, i would not mind your feedback as well...was curious whether it was as reliable in the early stages as it has been since i installed about 7 weeks ago...

and i think i understand what a "symlink" is now...got this explanation from a debian "wiki"...sounds simple to setup...not sure if we would have to do it, or if ubuntu would set it up for us...
[http://wiki.debian.org/SymLink](http://wiki.debian.org/SymLink)

---

### Post by grahammechanical on 2013-03-20
> [COLOR=#000000]was curious whether it was as reliable in the early stages[/COLOR]

I have been running Raring since November when I converted a quantal install into Raring by editing the sources lists. There is a command that will do it easily. Some of us had issues when the kernel was changed from 3.5.0 to 3.7.0. I could not get a desktop with 3.7.0.1 to 3.7.0.5 but 3.7.0.0 was fine for me and from 3.7.0.6 onwards. Some others had different experiences. The other day an update to udev seriously broke Raring but an update the next day fixed it. 

I also found the development branch of 12.10 to be usable from the start in May 2012. There was a period when I could not use it. This was due to kernel changes along with an Xserver change and busted Nvidia drivers, which seem to be doing much better now.

The development branch has become a bit boring but I do not mind. I use it every day. I also have other installs of Raring where I can experiment with beta or earlier upstream code if I wish. So, I am experimenting with MIR on another Raring install. It is broken at the moment. That is very bleeding edge.

Regards.

---

### Post by craig10x on 2013-03-20
so it does sound like that in the development branch, the quality control on the updates have become quite excellent...I use to run Linux Mint LMDE which was pointed to debian testing, and i have to note that this has been FAR FAR more reliable for me then that was...i got seriously borked on that twice and had to end up re-installing...not the case with 13.04 development at all...

Boring on here is actually a GOOD THING :D

---

### Post by zika on 2013-03-20
Decision to make "proposed" into a sandbox was very good indeed...

---

