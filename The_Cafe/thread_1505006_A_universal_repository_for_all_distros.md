---
title: "A universal repository for all distros"
date: 2010-06-08
forum: The Cafe
---

### Post by Dustin2128 on 2010-06-08
while I was playing around with Slackware last night I realized something: unless you're running a more popular, user friendly distro like fedora, mint or ubuntu, software will be in tar files that you compile yourself. But also in my experience, compiling them tends to be rather simple process; the real problems are in resolving dependencies. To my understanding, debian and ubuntu repositories are organized into .deb packages so I had a thought: why couldn't there be a repository of tar files with some system to resolve dependencies and maybe even a macro to compile/install the software for newbies. Is this possible and if so why hasn't it been done, or would anybody be interested in starting a project with this goal? Again, I apologize if this is something rhetorical, but I'd like to know.

---

### Post by chris200x9 on 2010-06-08
you want every distro to become gentoo?

---

### Post by KingYaba on 2010-06-08
The internet is my repository.

---

### Post by VeeDubb on 2010-06-08
There are several reasons this doesn't exist.

First and foremost, is the fact that as you pointed out, all of the 'major' distributions already have very thorough software repositories set up.  It's extremely rare that I ever have to compile anything from source unless I'm testing new stuff, which wouldn't be in any kind of official repo anyway.  That makes the whole discussion more or less moot.

Second, compiling from source isn't really a "newbie" activity, especially these days.

Third, if you're looking for source code for anything other than really new and/or obscure stuff that wouldn't be in a repository anyway, it's trivially easy to find it.

Fourth, while compiling from source is pretty simple, it's not universally the same.  For such a repository to work, it would all have to be done under rigid guidelines.

Since it wouldn't replace package manager systems (since most people don't want to compile from source) you'd need a huge crew of people to maintain the repository, not to mention the cost of hosting, etc.

Fifth, if you just want to compile everything from source, there's distros for that.



In short, there's nothing to be gained, and it would be kind of a pain to set up.

---

### Post by szymon_g on 2010-06-08
i didn't dive into it, but it seems to be an answer (or "The Answer")- [http://www.netbsd.org/docs/pkgsrc/introduction.html#introduction-section](http://www.netbsd.org/docs/pkgsrc/introduction.html#introduction-section)

---

### Post by handy on 2010-06-08
Bugger compiling everything.

We need something (the market?) to cause either .rpm or .deb to dissapear.

When we have just one prime package type it will save so many people so much work in package maintenance. Which can only be a good thing for GNU/Linux in general. As many of those people would then be more productive in other ways.

---

### Post by snova on 2010-06-08
> **VeeDubb said:**
> There are several reasons this doesn't exist.

[...]

Sixth: After you've set up this repository, you now need every other distro to change their tools to make use of it, or write tools that can coexist with the official ones (and then it takes on a secondary role to the "real" package manager anyway, though that can be acceptable depending on your goals).

Seventh: Compilation can be very resource intensive and time consuming, especially on lower end devices. Binary packages exist for a reason, at which point it's just yet another package format that nobody is adopting.

---

### Post by juancarlospaco on 2010-06-08
*Yes, an universal suppository for Microsoft.*

---

### Post by SunnyRabbiera on 2010-06-08
> **handy said:**
> Bugger compiling everything.

We need something (the market?) to cause either .rpm or .deb to dissapear.

When we have just one prime package type it will save so many people so much work in package maintenance. Which can only be a good thing for GNU/Linux in general. As many of those people would then be more productive in other ways.

Yeh limit choice, next thing restrict people to the same distro and DE..
Meh

---

### Post by new_tolinux on 2010-06-08
> **Dustin2128 said:**
> Is this possible
Ofcourse it's possible. Technically.
That said.

Canonical probably won't put any effort in it, as it's not specific Ubuntu. Same goes probably for Novell and Suse and probably for all distributions.

So it will not be build into the different distributions by default.
And it will need a big crew to update those packages, because you will not be notified of any changes made by the different distributions.
And you will need a big lot of space to save those packages.
And you will need to bring it to the public's knowledge that it exist.
And you will need a big connection to serve the users which are downloading packages.

Well, since people are willing to do a lot for you if you pay them well and therefore time is "buyable"...... you just need very much money. 

spoiler: [COLOR=White]And if you had that much funds, you probably would spent it elsewhere first[/COLOR] ;)

---

### Post by -grubby on 2010-06-08
> **SunnyRabbiera said:**
> Yeh limit choice, next thing restrict people to the same distro and DE..
Meh

Yeah, limit duplicated work, next thing standards and ISVs release software for Linux.

---

### Post by Dustin2128 on 2010-06-08
Yeah, I didn't realize how often I'd have to update packages, this would be quite expensive. A better tool might be a universal package installer, install rpm's on ubuntu or deb's on gentoo, a tool to access all repositories would be a much easier project to maintain and wouldn't take too awfully long to get started as opposed to a universal repository. Sorry if I'm rambling or anything I'm half watching T.V.

---

### Post by snova on 2010-06-08
> **Dustin2128 said:**
> Yeah, I didn't realize how often I'd have to update packages, this would be quite expensive. A better tool might be a universal package installer, install rpm's on ubuntu or deb's on gentoo, a tool to access all repositories would be a much easier project to maintain

The former exists; it's called "alien", and I wouldn't be surprised to find tools to do the latter. As to being easier, you've changed your workload from "package everything in the world" to "support every package format in the world", which is at least less of a moving target.

At the most, however, the only benefit I can see is that it becomes easier for users of smaller distros to pick up (more common) packages built for bigger ones. And that just sounds like a stop-gap measure to get around the actual issue- incompatibility.

---

### Post by VeeDubb on 2010-06-08
> **handy said:**
> We need something (the market?) to cause either .rpm or .deb to dissapear.

I agree completely.

> **snova said:**
> 
Sixth...

Seventh...

I knew I was missing something.  Thanks.

> **SunnyRabbiera said:**
> Yeh limit choice, next thing restrict people to the same distro and DE..
Meh

Everything in life is a trade off. Having a single package format would mean a little less choice.  However, it would mean greater interoperability between distros, easier distribution of commercial software, and easier support for new users.  

It also would NOT eliminate the option of compiling from source, or get rid of distros like gentoo.  Nor would it mean that everyone had to use the same packages.  Each distro could still maintain their own repositories with packages divided up the way they see fit, as long as the packages are in a single format.

> **new_tolinux said:**
> Well, since people are willing to do a lot for you if you pay them well and therefore time is "buyable"...... you just need very much money. 

spoiler: [COLOR=White]And if you had that much funds, you probably would spent it elsewhere first[/COLOR] ;)

Pretty much.

---

### Post by handy on 2010-06-08
> **SunnyRabbiera said:**
> Yeh limit choice, next thing restrict people to the same distro and DE..
Meh

Did you get out of the wrong side of the bed this morning Sunny? ;)

If you think that that is what I meant, & that having .rpm & .deb somehow merge is going to somehow limit distro users freedom, you are seeing something I'm not.

I'm an Arch user. We don't use .deb or .rpm.

If there was one prime package format, it would save the poor package maintainers a great deal of work.

That is all I'm saying no more.

---

### Post by murderslastcrow on 2010-06-08
Yeah, it'd be nice if PackageKit were as user friendly as the Ubuntu Software Center. In fact, I wouldn't mind if they just patched PackageKit to look and act like the Software Center. I think, though, that it's not so bad as it is, and this will improve over the next few years since it's being worked on.

---

### Post by handy on 2010-06-08
> **murderslastcrow said:**
> ... 
I think, though, that it's not so bad as it is, and this will improve over the next few years since it's being worked on.

What's being worked on? Getting either Debian or Red Hat to let go of their packaging system... :shock:

---

### Post by kevdog on 2010-06-08
Handy

Welcome back -- and don't be so cranky.  Its not like you.

---

### Post by handy on 2010-06-08
> **kevdog said:**
> Handy

Welcome back -- and don't be so cranky.  Its not like you.

Hi kevdog, I haven't been anywhere? :confused:

Sorry if I seem cranky, I'm not. :)

I must need to put more smilies in my posts. :D

---

### Post by Shining Arcanine on 2010-06-09
> **Dustin2128 said:**
> while I was playing around with Slackware last night I realized something: unless you're running a more popular, user friendly distro like fedora, mint or ubuntu, software will be in tar files that you compile yourself. But also in my experience, compiling them tends to be rather simple process; the real problems are in resolving dependencies. To my understanding, debian and ubuntu repositories are organized into .deb packages so I had a thought: why couldn't there be a repository of tar files with some system to resolve dependencies and maybe even a macro to compile/install the software for newbies. Is this possible and if so why hasn't it been done, or would anybody be interested in starting a project with this goal? Again, I apologize if this is something rhetorical, but I'd like to know.

That has been done. It is called Gentoo Linux. There are distributions like Sabayon Linux that are forks of it to get the benefits of a large repository that comes with being a mainstream Linux distribution.

> **chris200x9 said:**
> you want every distro to become gentoo?

That is a good idea. We could start by having all binary distributions abandon their existing codebases and fork Sabayon Linux:

[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)


> **Dustin2128 said:**
> Yeah, I didn't realize how often I'd have to update packages, this would be quite expensive. A better tool might be a universal package installer, install rpm's on ubuntu or deb's on gentoo, a tool to access all repositories would be a much easier project to maintain and wouldn't take too awfully long to get started as opposed to a universal repository. Sorry if I'm rambling or anything I'm half watching T.V.

It is already possible to install .deb and .rpm packages on Gentoo Linux, but I am afraid that .deb and .rpm packages will often not work on Gentoo Linux. Being a rolling distribution, Gentoo Linux's ABI is constantly changing, so any binary packages that do work will eventually break. While in theory you can use Gentoo's ebuilds on distributions that use .deb or .rpm packages, the reverse cannot be done in general. This is because the ebuilds are usually wrappers for the tarballs developers usually distribute, although they can be wrappers for other things too, including binary software that is distributed with makeself installers.

This of course does not consider the issues inherent with root directory pollution when you install packages outside of the system package manager.

---

### Post by Dayofswords on 2010-06-09
> Since it wouldn't replace package manager systems (since most people don't want to compile from source) you'd need a huge crew of people to maintain the repository, not to mention the cost of hosting, etc.

just got me thinking........... what if someone made a bittorrent-like repo system, one where there is a main server that has all packages and each package is in a torrent and people request that torrent for the file, then they can help other get the file

---

### Post by VeeDubb on 2010-06-09
Torrents have advantages, like automatic crc checking, but I don't see that as being efficient for this kind of distribution.

Bittorrent is most efficient when distributing very large files to a very large number of users at the same time.  The more users, the faster they can all get it.  The larger the file, the longer people stay connected and sharing what they already have, making the whole thing smoother for everybody.

Most packages are relatively small, and only downloaded intermittently.  I suspect that even the most heavily downloaded packages are not downloaded by hundreds or thousands of people at the same time, which would make BT relatively inefficient. 

All you'd really gain is the error checking, which can be done other ways.  Add to that the fact that many ISPs block or throttle bittorrent traffic, and it starts to look like a bad plan pretty quickly.

---

