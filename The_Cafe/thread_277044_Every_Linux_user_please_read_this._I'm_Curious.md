---
title: "Every Linux user please read this. I'm Curious"
date: 2006-10-13
forum: The Cafe
---

### Post by motstudios on 2006-10-13
Greetings!

    Me and a friend of mine have been doing a lot of discussing while working on some linux projects and we got an idea. We are wondering what other Linux users think about it. The idea is as follows:


    Every Linux user knows that Linux lacks on some areas. For instance, there is no truely smart package system. Apt is about as close as I've found to a good package system. However it lacks a lot. For instance, last night I was doing some "cleaning" out of some unneeded packages and so forth. One in particular that bugged me a lot was I tried to remove the laptop-detect package because I use a desktop so have zero use for it. When I marked it in synaptic it wanted to remove what seemed like my entire system.

    Most people also know (even if they don't want to admit it) that the layout of the linux filesystem is old and outdated. There is also differences in the layout between the major distros.

    I'm also sure many many Linux users have many great suggestions for Linux in general that will make Linux better.

    So my friend and I were talking about these shortcommings. I think one of the biggest reasons some of these problems exist is because most developers of Linux distros aren't paid, or not paid enough. Also there is a sort of "war" between die hard users of "the big three" (Debian, Slackware and Red Hat/Fedora). Face it, if a Debian user told a Slackware user their distro is old outdated and a pain to use, the Slackware user will likely get pissed and fuss the debian user out.

    Ok so I know I said the idea was to follow, but I needed to say the previous before getting to the idea.

    The idea, short and simple: If every Linux user donated $10 towards a fund, the fund would be huge. This fund can then be used to offer huge cash rewards to any group of people who can complete various "goals" which will be voted on by the Linux community. For example, if there were lets say a $1 million reward for a package system that meets all the requirments the community sets, I'm sure it will get made and completed in a timely manner.

    Pretty much everyone can afford $10 to make Linux better. I know I'd be willing to donate a minimum of $10. My question is, who else is willing to donate cash funds to get some goals finished?

    If enough people feel this idea is a good one, then my friend and I may start it. We can get a website designed and such, probably find some hosting and get it advertised. However, we don't want to waste what little time we have if no one wants it. We have a lot on our plate as it is.

Peace be with you all,
Mark

---

### Post by nalmeth on 2006-10-13
Launchpad is doing something like that.
Bounties:
[https://launchpad.net/bounties/](https://launchpad.net/bounties/)

Money would help developers focus, and eat, but I don't think it's a deciding factor, most are developing without expectation of money. But it certainly would help a good deal for devs to get paid at least a little.

---

### Post by aysiu on 2006-10-13
I think *aptitude* is pretty damn smart, and I believe there is even a package manager *called* SMART package manager.

When you say it wanted to remove everything, are you talking about *ubuntu-desktop*, because that's just a metapackage that points to all the default packages in a Ubuntu installation. The metapackage is not a real package.

As nalmeth pointed out, bounties exist. Make one if you like.

Honestly, though, the way Ubuntu is constructed, you don't have to see the filesystem. Go ahead--open up Nautilus--it's just like  Mac OS X. You see your home folder (called simply your username), and you see the desktop and "filesystem."

Most of the time, all you need is your home folder.

The filesystem appears confusing only to those who feel the need to configure Ubuntu--and, thankfully, unlike Mac OS X, you don't have to do separate hacks to see it through the GUI. Seriously, why do users have to see the filesystem?

Do you think users find C:\WINDOWS and C:\Documents and Settings making sense would take that long to figure out /etc or /home? I can promise you most Windows users I know have no clue how the Windows filesystem is structured. They just click on My Documents and that's about it. In fact, even when I ask them to browse through My Network Places to just *browse*, they still want me to handhold them through which network shares to click.

---

### Post by IYY on 2006-10-14
The filesystem is a bit outdated, but it is kept not because they can't afford to make a new one but because they want to stay Unix-like. If they suddenly changed something as fundamental as the filesystem structure, they will lose 80% of the audience (users who like, or at least know the Unix model). That's the great thing about *nix: the skills you learn today will stay relevant in 20 years. 

Besides, the most newbie friendly OS out there, Mac OS X, didn't significantly change the Unix file structure and I don't hear anyone complaining.

---

### Post by RAV TUX on 2006-10-14
> **nalmeth said:**
> Launchpad is doing something like that.
Bounties:
[https://launchpad.net/bounties/](https://launchpad.net/bounties/)

Money would help developers focus, and eat, but I don't think it's a deciding factor, most are developing without expectation of money. But it certainly would help a good deal for devs to get paid at least a little.

I stand behind nalmeth on this one...

utilize launchpad bounties and stop reinventing the wheel.

Also read this article:

**                                         [The "Dunc-Tank Experiment": September 21, 2006]("http://cafelinux.org/forums/index.php/topic,342.msg1938.html#msg1938")                                     **

[URL="http://community.linux.com/community/06/09/21/1623232.shtml?tid=19"]
[/URL]

---

### Post by ericesque on 2006-10-14
Mots,

I think the biggest issue with the concept would be who controls this large sum of money?  You and your friends?  I'm not sure many people would donate.  The community?  Who decides how the community's money is spent?  Do we vote? How do you structure the vote?

My fellow board members and I would not discourage your enthusiasm for linux.  It's always been the people who think outside the box that make the greatest impact.  Then again, not every idea found outside eight corners is going to hold water.  

The beauty of the current system of innovation for linux is that people can jump onboard a project that they are interested in.  Money is typically not the major factor.  Organizing the community's skills as resources is a bigger issue.  If you and your friends can determine a way to do this, THEN you will surely have people's attention.

---

### Post by Mathiasdm on 2006-10-14
> **motstudios said:**
> Greetings!

    Me and a friend of mine have been doing a lot of discussing while working on some linux projects and we got an idea. We are wondering what other Linux users think about it. The idea is as follows:


    Every Linux user knows that Linux lacks on some areas. For instance, there is no truely smart package system. Apt is about as close as I've found to a good package system. However it lacks a lot. For instance, last night I was doing some "cleaning" out of some unneeded packages and so forth. One in particular that bugged me a lot was I tried to remove the laptop-detect package because I use a desktop so have zero use for it. When I marked it in synaptic it wanted to remove what seemed like my entire system.
Most of the packages you saw in synaptic were (probably) just meta-packages, that wouldn't have any effect.

Package management is fine, imho.

> Most people also know (even if they don't want to admit it) that the layout of the linux filesystem is old and outdated. There is also differences in the layout between the major distros.
Old, okay. Outdated: no way!
The reason this lay-out is still around, is two-fold:
-lots of old packages depend on it
-it's a good layout

You say it's outdated, I ask you: why?
Because it contains cryptic things like 'dev', 'usr' and such? There's nothing wrong with that, seeing as the average user is supposed to stay in his home directory.

I personally like what Apple has done with OS X: the filesystem is hidden, only /home is visible.

Concerning the rest of your post: most 'flaming' happens in good humour.

I support your idea of giving money, but I don't agree to the 'problems' in the Linux world.

---

### Post by tageiru on 2006-10-14
> **motstudios said:**
> 
    Every Linux user knows that Linux lacks on some areas. For instance, there is no truely smart package system. Apt is about as close as I've found to a good package system. However it lacks a lot. For instance, last night I was doing some "cleaning" out of some unneeded packages and so forth. One in particular that bugged me a lot was I tried to remove the laptop-detect package because I use a desktop so have zero use for it. When I marked it in synaptic it wanted to remove what seemed like my entire system.

Can you name one shortcoming of having the laptop-detect package installed on your desktop? Does it hinder your work? It is there because Ubuntu needs to work on a variety of computers. It is just a lowest common denominator, removing it without it causing issues is stupid.

> **motstudios said:**
> 
    Most people also know (even if they don't want to admit it) that the layout of the linux filesystem is old and outdated. There is also differences in the layout between the major distros.

This is a weird comment. The real bug is that users come in contact with the filesystem outside their home directory at all. The filesystem is fully abstracted by the package manager and the desktop environment.

The amount of work needed to change the hierarchy is enormous. You would actually have to change every single package there is. It is a waste of time just to please a few people that thinks that the hierarchy is somehow dated.

---

### Post by Bloodfen Razormaw on 2006-10-14
I removed laptop-detect without any problems.

---

### Post by picpak on 2006-10-14
> **aysiu said:**
> Do you think users find C:\WINDOWS and C:\Documents and Settings making sense would take that long to figure out /etc or /home? I can promise you most Windows users I know have no clue how the Windows filesystem is structured. They just click on My Documents and that's about it. In fact, even when I ask them to browse through My Network Places to just *browse*, they still want me to handhold them through which network shares to click.

Nowadays I find that hard to believe, but you're right. Three years ago, My Documents WAS my computer.

However, browsing the filesystem can be useful at times. For example, sometimes I forget the command to symlink, so I fire up *gksudo nautilus*, go to /usr/bin, and do the symlinking there.

---

### Post by prizrak on 2006-10-14
You are looking at the wrong end of the problem. It's not the package manager that is stupid, it's how the packages are done. When you package something it is up to you to provide dependancies whether they are real or not. You could create a package that will install pacman and depend on the bluetooth module despite them not being connected in any way shape or form. The way Ubuntu devs do it is they create a meta package that is nothing more than a list of dependancies that need to be installed when it's installed. It makes for very easy installation of the whole system. For instance if you want Xubuntu all you do is grab xubuntu-desktop and you will get everything you need to have Xubuntu. It also makes the upgrades easier, you just update the meta package and it pulls all the new stuff.

---

### Post by meng on 2006-10-14
As already mentioned, the problem is likely to lie with meta-packages which include laptop-detect as a dependency. Hardly worth doing a complete rewrite of package management for ... I don't mean to encourage complacency, simply to advocate that some thought should go into which areas need most development.

---

### Post by aysiu on 2006-10-14
> **picpak said:**
> Nowadays I find that hard to believe, but you're right. Three years ago, My Documents WAS my computer.

However, browsing the filesystem can be useful at times. For example, sometimes I forget the command to symlink, so I fire up *gksudo nautilus*, go to /usr/bin, and do the symlinking there.
I'm with you there, picpak, but I wasn't talk about users like me or you.

---

### Post by motstudios on 2006-10-14
> If they suddenly changed something as fundamental as the filesystem structure, they will lose 80% of the audience (users who like, or at least know the Unix model). That's the great thing about *nix: the skills you learn today will stay relevant in 20 years.
I do not agree with that statement. A change in the filesysytem wont scare off users. Even Windblows "updated" their filesystem between ME and 2000 and people seemed to like the new setup.

> Besides, the most newbie friendly OS out there, Mac OS X, didn't significantly change the Unix file structure and I don't hear anyone complaining.
I totally disagree with that statement. My wife used to have Mac OS X on a laptop. She had it because basically her sister ripped her off in my opinion. However my wife said that OSX was a total pain to work with and found Linux (Ubuntu) much easier to use and she enjoyed learning some of the more intricate parts of linux.

> think the biggest issue with the concept would be who controls this large sum of money? You and your friends? I'm not sure many people would donate. The community? Who decides how the community's money is spent? Do we vote? How do you structure the vote?
Well, we haven't planned that far ahead. We wanted to know what peoples opinions were before we did anything, even detailed planning. And yes voting was a possibility.

> Organizing the community's skills as resources is a bigger issue.
Actually I've been working on a "Unification Project" the past few months. Still only in planning stages though.

> I support your idea of giving money, but I don't agree to the 'problems' in the Linux world.
Most Linux users refuse to admit the problems with Linux. Just as Microsoft refuses to admit its problems. And no I'm not compairing Linux users to Microsoft. 

And I already know a lot of people will flame me, a lot of people will call me crazy or stupid or whatnot. However it never stops me. As for the package system needing something better, no matter what anyone says, there needs to be something better than there is now. The filesystem being old and outdated can wait but the package system needs updating and redoing.

I do like all the comments. A lot of responses overnight. Peace.

---

### Post by aysiu on 2006-10-14
> **motstudios said:**
> A change in the filesysytem wont scare off users. Even Windblows "updated" their filesystem between ME and 2000 and people seemed to like the new setup. It's not a matter of "scaring off" new users. It's a matter of *pissing off* existing users.

Most Windows users don't care as much about the filesystem structure as most Linux users do.

> I totally disagree with that statement. My wife used to have Mac OS X on a laptop. She had it because basically her sister ripped her off in my opinion. However my wife said that OSX was a total pain to work with and found Linux (Ubuntu) much easier to use and she enjoyed learning some of the more intricate parts of linux. I don't see what that has to do with the statement you were responding to. My wife also finds OS X a pain to work with, but it has nothing to do with the file structure and everything to do with the interface.

In fact, she doesn't even know about the file structure. As far as she can tell, there's just computer, Applications, and Documents. She doesn't know about /dev, /Users, /lib, /bin, /etc, etc. But those are all there in Mac OS X.

The point remains--OS X shares a file structure very similar to Linux distros, and OS X users don't care... they don't even know about the file structure most of the time.

> Well, we haven't planned that far ahead. I'll say.

> Actually I've been working on a "Unification Project" the past few months. Still only in planning stages though. Good luck.

> 
Most Linux users refuse to admit the problems with Linux. No. We just don't agree with what **you** see as problems... or "solutions." Go ahead, start a thread called "What problems do you find with Linux?" and I can guarantee no more than two responses will be "There are no problems."

**Edit**: In fact, can you find me (in the 578 posts in [this thread](http://ubuntuforums.org/showthread.php?t=57994)) where someone says "Linux is perfect"?

---

### Post by iovar on 2006-10-14
> **motstudios said:**
> Greetings!
    Most people also know (even if they don't want to admit it) that the layout of the linux filesystem is old and outdated. 


Honestly, I don't understand this statement. Can you please elaborate on
that? 

> If enough people feel this idea is a good one, then my friend and
I may start it. We can get a website designed and such, probably find
some hosting and get it advertised. However, we don't want to waste what
little time we have if no one wants it. We have a lot on our plate as it
is.

Seriously, come on!
If you want to gather money, you start a non-profit foundation, with
policies, goals and the likes. I mean you ask for 10$ a person which is
something like dozens of millions of dolars. Do you really believe that a
web-site will suffice? You might as well start sending unsolicited
emails. You'll get more money that way.

And to top that, you don't want to waste time? So what's going to be your
front page? 
"Drop ten bucks to us and if we find time and the money is good enough,
we'll do something with linux...?" 

There are already places , with goals and a history, where someone can
spend his 10$. And there are already alot of people that have contributed
money and time on these. In fact, there is a whole ecosystem, with money
and effort flowing on all directions, which you and your friend failed to see.


Oh, almost forgot... 1 million dollars is not enough to change package management universally... I mean, you have to hire assasins and bullies
to hunt down 1500 debian developers around the world. And then you have somehow to force Redhat to drop the rpm format. And if you succed with
that and still have money to develop your package manager, good luck getting Patrick Volkerding to agree. People are still trying to get him
to use 2.6 kernels for default...

---

### Post by Mathiasdm on 2006-10-14
> **motstudios said:**
> 
Most Linux users refuse to admit the problems with Linux. Just as Microsoft refuses to admit its problems. And no I'm not compairing Linux users to Microsoft. 

As for the package system needing something better, no matter what anyone says, there needs to be something better than there is now. The filesystem being old and outdated can wait but the package system needs updating and redoing.

-The package system, in my opinion needs only 1 change: a better way to install packages that aren't in the repositories (and I think people are working on that).
-What's wrong with the file system? Old is not necessarily bad. Give me a REASON.

---

