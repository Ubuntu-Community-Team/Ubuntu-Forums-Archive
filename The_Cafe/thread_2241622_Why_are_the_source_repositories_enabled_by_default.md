---
title: "Why are the source repositories enabled by default?"
date: 2014-08-27
forum: The Cafe
---

### Post by user1397 on 2014-08-27
I did a bit of searching, and couldn't find information about this.  Is there a particular reason why it's the default?  I mean, when would a regular user need to download the source code of a program, in 99.99% of usage cases?

Just doesn't add up...

---

### Post by TheFu on 2014-08-27
GNU license terms.
This is part of our freedom and we should be extremely thankful for it.

---

### Post by kostkon on 2014-08-27
That's the nature of the beast. Free Open Source OS, easy access to the source code..

---

### Post by user1397 on 2014-08-27
> **TheFu said:**
> GNU license terms.
This is part of our freedom and we should be extremely thankful for it.

> **kostkon said:**
> That's the nature of the beast. Free Open Source OS, easy access to the source code..
I didn't mean to come off as an ungrateful open-source hater.  Quite the opposite.  I just mean from a main user base point of view.

I get it if they include it as part of the GPL license terms (do all distros do this?)

If not though, then it can only be negative for the average user, which is the user base canonical tailors to the most.  On the one hand, it takes more time to fetch the data from the source repositories when doing a sudo apt-get update (yes this is minor), but on the other hand an average user may download source code accidentally or without knowing what it is exactly, and perhaps bork something in his system.

I just can't see any positives to including it *by default*, unless of course like I said earlier it is simply because of license terms.

Cheers.

---

### Post by The Cog on 2014-08-27
The source code is not installed by default. You have to ask for the source packages to be installed if you want them. 
But the repositories are enabled, so you can select the packages for installation easily. 
I think there has been some confusion about "enabled by default" and "installed by default" here.

---

### Post by QIII on 2014-08-27
Source code isn't dangerous.  It does nothing in and of itself.  In some ways it's similar to a pattern in a tailor's shop.  Changing a pattern in a drawer does not change anything on the tailor's shelves.

---

### Post by Warren Hill on 2014-08-27
Since all the software is open source we have to make the source code available to anyone who wants it so its available in the repositories.  That does not mean you have any of it installed on your machine.  If you want the source for a particular package open a terminal and enter

```
apt-get source package
```

replace package with the name of the package you want the source code for.

You would probably be surprised how many people do download the source, either to make something similar or to help fix bugs and improve Ubuntu.

But if you are not interested in developing and just want to use your PC that's fine too.  Your hard disk is not full of source code or anything. It is just a quick download away for anybody who wants it.

---

### Post by vasa1 on 2014-08-27
> **ubuntuman001 said:**
> ... it takes more time to fetch the data from the source repositories when doing a sudo apt-get update (yes this is minor) ...
Hi, was the source code box ticked in "Software & Updates" (or whatever it's called on your system)? I can't remember what the default was on my clean install. Anyway, that's part of the ritual I go through on a clean install. 

I agree that it could be a drag for people with slow connections or for people with limited usage plans. Otoh, a cynic may feel this is a good way to thin the herd.

---

### Post by user1397 on 2014-08-28
> **The Cog said:**
> The source code is not installed by default. You have to ask for the source packages to be installed if you want them. 
But the repositories are enabled, so you can select the packages for installation easily. 
I think there has been some confusion about "enabled by default" and "installed by default" here.Indeed, this is why I said "enabled by default" in the title of this thread, and not the other way around.  No confusion on my end.

> **QIII said:**
> Source code isn't dangerous.  It does nothing in and of itself.  In some ways it's similar to a pattern in a tailor's shop.  Changing a pattern in a drawer does not change anything on the tailor's shelves.I'm not saying that either, but like I said, maybe if someone were to accidentally download source code and didn't install/configure it correctly he might not install a program correctly or lead to dependency issues, all things that could drive this person to say "ubuntu is too complicated"

> **Warren Hill said:**
> Since all the software is open source we have to make the source code available to anyone who wants it so its available in the repositories.  That does not mean you have any of it installed on your machine.  If you want the source for a particular package open a terminal and enter

```
apt-get source package
```

replace package with the name of the package you want the source code for.

You would probably be surprised how many people do download the source, either to make something similar or to help fix bugs and improve Ubuntu.

But if you are not interested in developing and just want to use your PC that's fine too.  Your hard disk is not full of source code or anything. It is just a quick download away for anybody who wants it.I understand you don't have any installed on your machine, I never argued that.  I will however argue your point about how many people download the source code, I know it is impossible to know, but maybe we can set up a poll in a separate thread.

> **vasa1 said:**
> Hi, was the source code box ticked in "Software & Updates" (or whatever it's called on your system)? I can't remember what the default was on my clean install. Anyway, that's part of the ritual I go through on a clean install. 

I agree that it could be a drag for people with slow connections or for people with limited usage plans. Otoh, a cynic may feel this is a good way to thin the herd.Yes, it is ticked in the default clean install.  It's also part of the ritual when I configure a clean install.  Now, what do you mean by the whole cynic thing?

---

### Post by buzzingrobot on 2014-08-28
> **The Cog said:**
> The source code is not installed by default. You have to ask for the source packages to be installed if you want them. 
But the repositories are enabled, so you can select the packages for installation easily. 
I think there has been some confusion about "enabled by default" and "installed by default" here.

This.

FOSS licensing requirements do not require source to be force fed on any and every binary install.

---

### Post by grahammechanical on 2014-08-28
I am reminded of a time when a friend of mind went to his local authority to claim financial assistance for his family. The person at the information desk told him that he had to make the claim at a specific department but that she was not allowed to say where in the building the department was situated!

Obtaining the source code should not be like that. We should not need to jump through hoops to get source code. I think that making the source code available but very, very difficult to get would be against the spirit of FOSS licensing.

Canonical makes the source code of all the FOSS packages in Ubuntu available in a repository and that repository is enabled by default. We can disable that repository. I think that the right balance has been struck.

Regards.

---

### Post by buzzingrobot on 2014-08-28
> **grahammechanical said:**
> IThe person at the information desk told him that he had to make the claim at a specific department but that she was not allowed to say where in the building the department was situated!


A test? At least she said it was in the same building.  

I remember when drives weren't cheap and huge and people complained if source came down the dialup link along with the binary:  Gobbled up drive space and sucked up expensive phone time.

Pushing source with binaries would also mean adding source files to install images, and they are already seen as too large by many.  (Could be a post-install option, though.)

Folks who want source are in the minority, so defaulting to enabled source repos but explicit installation seems a good compromise to me. If someone always wants source of every package, they could alias and/or script, apt-get to do that. (Or, maybe a flag to be set in apt.)

But, no, we shouldn't need to jump thru hoops to get it when we want it.

---

### Post by oldos2er on 2014-08-28
> **ubuntuman001 said:**
> I'm not saying that either, but like I said, maybe if someone were to accidentally download source code and didn't install/configure it correctly he might not install a program correctly or lead to dependency issues, all things that could drive this person to say "ubuntu is too complicated"


Source code does nothing but take up some hard disk space after it's downloaded; the user has to compile it (including downloading any dependencies it might need) and install it. This is not something that would occur accidentally.

---

### Post by Warren Hill on 2014-08-28
Are we really arguing about whether or not this check box should be ticked or not by default? ;)

Personally I don't have a problem either way.  The actual source code for the version of the program that we are using needs to be somewhere and the repositories is the obvious place to put it.  But I could care less about should those of us who want the source code need to select this option or should those who don't want to care about source have to deselect it.  

[ATTACH=CONFIG]255910[/ATTACH]

---

### Post by user1397 on 2014-09-03
I merely meant to open a discussion about this, as this is the perfect forum for it.

Ok, maybe no one can really damage their system or anything by "accidentally" downloading/installing source code, but what I and a couple others have said still holds true.  For people with less-than-ideal internet connections, having the source repos enabled by default means the more time it takes to sudo apt-get update and fetch data from the repos. All I'm saying is, not once since 2006 have I ever downloaded the source code through the repositories in ubuntu, and I really don't see a "reason" for your "average" user to use anything but the binaries.  So, I am not arguing *access* or whether we should *even have source repos.* Not at all, I am merely stating that maybe, just *maybe,* we shouldn't include them by *default.*

---

### Post by The Cog on 2014-09-03
No, I think it's only you that's getting offended. I'm not really sure why.

Now any misunderstandings about what you mean have been cleared up, it seems that Warren Hill is right, and we are arguing about whether that check box should be checked. Thinking about it (not having tested), I guess that downloading an index of the source code repo will probably take about as long as indexing the binary repo - doubling the time needed to update. For those with very slow internet, I guess this might be significant though I also guess it pales into insignificance against the time needed to actually download any updates. I don't have any strong feelings on the issue,  but then I'm not stuck on the end of a rural slow-as-molasses broadband. Perhaps you should file a bug report on launchpad. They do look at them all, and it's obviously an easy fix if they decide to make the change. Make sure it's clear that you mean it's the indexing time and not the source download time you are worried about or they may make the same mistake that I did and misunderstand you.

---

### Post by buzzingrobot on 2014-09-03
I think not installing source by default makes sense.  Pretty much by definition, users don't know what to do with it. If they do need it they will likely follow some blog post by rote, or already have necessary development skills and experience to know what to do, which really removes them from the typical user category.

The larger picture is that Linux distributions have become dependent on user access to sufficient broadband.  That penalizes people who lack, or can't afford,  that access.

---

### Post by vasa1 on 2014-09-03
> **buzzingrobot said:**
> I think not installing source by default makes sense.  Pretty much by definition, users don't know what to do with it. If they do need it they will likely follow some blog post by rote, or already have necessary development skills and experience to know what to do, which really removes them from the typical user category.

The larger picture is that Linux distributions have become dependent on user access to sufficient broadband.  That penalizes people who lack, or can't afford,  that access.
And even if there are no constraints, it's just wasteful for people who most probably do not need the source code to have it installed on their system; how wasteful it is is not material. That they can later untick it is also not the point.

I too feel it should be unticked by default.

Of course, if there are legal reasons for having source code installed by default, that's another matter.

---

### Post by user1397 on 2014-09-03
Thank you.

And just to be clear, I am not offended or anything, I just wanted to open a discourse on the matter, nothing more.  Doesn't really bother me, I just wanted to know why.  Doesn't bother me enough to file a bug report.

---

### Post by malspa on 2014-09-03
Don't feel bad, ubuntuman001. I thought it was a good question. The source repos are "available" whether they're enabled by default or not, so I see no reason why they should be enabled by default (unless there are legal reasons that I'm not aware of, of course). But, whatever, I simply disable them.

---

### Post by Warren Hill on 2014-09-03
> **vasa1 said:**
> 
Of course, if there are legal reasons for having source code installed by default, that's another matter.

There are no legal requirements for having source code installed, and in a default install you don't have any installed.  There is a legal requirement that we make the source available to anybody who wants it however.

The only reason having the repositories enabled by default is that it makes getting source code easier.  The downside is that when you run 

```
sudo apt-get upgrade
``` 

It downloads more and you get a larger database generated.  As said in one of my previous posts to this thread I have no particular objection to the check box being one you need to select to enable, not enabled by default.

Given the point you make that not everybody has high quality broadband and while I don't agree the number of people who want access to the source is tiny, it is certainly a minority of users so there are good arguments to not enable the repositories by default. :p

---

### Post by user1397 on 2014-09-03
Agreed Warren.

---

### Post by mc4man on 2014-09-03
some info, ect.
[https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747](https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-May/thread.html#14503](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-May/thread.html#14503)

---

