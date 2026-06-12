---
title: "End Of Tree Packages"
date: 2005-08-11
forum: The Cafe
---

### Post by DarkT on 2005-08-11
Hi, if this is a question that's been asked before I'm sorry but it's something I've been very curious about. I also just want to make clear I'm not bashing Ubuntu in asking it. 
 
Basically I've been wondering why end of tree packages such as (and these are ones I use regularly) blender, yafray, inkscape etc. are not kept relatively up to date? By end of tree I mean dependancy tree, where nothing else depends on them except maybe a couple of other related packages in a circular manner. 

I understand the debian philosophy of keeping packages in a stable state and testing them thoroughly but surely for end of tree packages where the chances are they have no real threat to the security of a system can be kept up to date? If there is so much concern over package stability then why now keep up to date end of tree packages in a seperate repository for those who know what they are doing?

I also know about the backports project but again this is purely dependant on the breezy tree which still seems to keep end of tree packages not very up to date and in *this* sense it is somewhat flawed (although I really appreciate what the backport folks do). Would it be possible at some point for the ubuntu team to provide up to date packages in a seperate repository or something similar?

If you've read this through thanks for hearing me out on this as I know debian-esk packaging policy can get a bit flamey at times.

---

### Post by Stormy Eyes on 2005-08-11
I'd say it's because there are only so many people doing the work, and their time is limited, especially since Ubuntu is supposed to do a release every six months. They have to set priorities, and it looks like they're more concerned with making the underlying system work better than with applications.

---

### Post by fng on 2005-08-11
Did you take a look at the ubuntu backports?
It's a community driven project for getting the latest version of packages in the last official ubuntu release.

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by DarkT on 2005-08-11
**Stormy Eyes:** 
I do see your point, but one thing that keeps people using a distro is that they can be pretty sure their more used apps will be kept up to date. However, ubutnu is still young relatively speaking. 
I'd be interested to see if the ubuntu team would be willing to get such a project going (where there's a seperate repo' for end of tree apps) and recruit people for it as they are understandabely busy. My worry is that if Ubnuntu becomes too insular and unwilling to welcome or create new projects to deal with the app side of things - look at the original reception to backports - the whole project may get as stale as debian is (IMHO).

**fng:** 
> I also know about the backports project but again this is purely dependant on the breezy tree which still seems to keep end of tree packages not very up to date and in this sense it is somewhat flawed (although I really appreciate what the backport folks do). Would it be possible at some point for the ubuntu team to provide up to date packages in a seperate repository or something similar? :)

---

### Post by fng on 2005-08-11
oops :)
I'm having trouble waking up this week :)

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=DarkT]I do see your point, but one thing that keeps people using a distro is that they can be pretty sure their more used apps will be kept up to date. However, ubutnu is still young relatively speaking.[/quote]

It is. Hoary is only the second release. It does do to keep in mind that Ubuntu's plan is *not* to release brand-new packages willy-nilly, but to release an improved version every six months. To keep to that schedule, the developers have to set a deadline after which there will be no new features or packages added so that they can focus on testing and bugfixes prior to release.

Ubuntu can't be all things to all people. Trade-offs have to be made, and it appears that Ubuntu is more focused on producing a stable system that is reasonably current than on tracking new releases of popular apps. 

I personally think that Ubuntu's focus on stability is reasonable. Being somebody who has used Linux for years, if I *wanted* new releases right away, I would either compile it myself, or go back to running Gentoo.

[QUOTE=DarkT]I'd be interested to see if the ubuntu team would be willing to get such a project going (where there's a seperate repo' for end of tree apps) and recruit people for it as they are understandabely busy. [/quote]

Then ask. Or, better yet, volunteer to start it yourself if you have the skill and the time. I've noticed that "I'd like to help $DISTRO out by doing $TASK" gets a better reception than "I think that $DISTRO should do $TASK".

[QUOTE=DarkT]My worry is that if Ubnuntu becomes too insular and unwilling to welcome or create new projects to deal with the app side of things - look at the original reception to backports - the whole project may get as stale as debian is (IMHO).[/quote]

If that happens, people will either abandon Ubuntu, or fork it. Why worry?

---

### Post by DarkT on 2005-08-11
[QUOTE=Stormy Eyes]Then ask. Or, better yet, volunteer to start it yourself if you have the skill and the time. I've noticed that "I'd like to help $DISTRO out by doing $TASK" gets a better reception than "I think that $DISTRO should do $TASK".
[/QUOTE]
Hmm the thing is I tend to assume I really don't have the know how to say that I want to do it myself (although to some extent I have the time)... maybe I'll have to read up on debian packaging etc .and see if I can at the least make an offer.
 
> If that happens, people will either abandon Ubuntu, or fork it. Why worry? 
Because for the first time in several years I've found a distro which I'm comfortable to use for my desktop (other than slackware, which is o.k) :)

---

