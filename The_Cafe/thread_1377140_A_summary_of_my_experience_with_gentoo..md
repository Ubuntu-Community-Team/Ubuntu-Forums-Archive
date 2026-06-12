---
title: "A summary of my experience with gentoo."
date: 2010-01-09
forum: The Cafe
---

### Post by dragos240 on 2010-01-09
Ever since I heard about linux in 2008, I've always heard about gentoo. So I thought in late 2009, 'why not test it out'? So I did. I went through a lot of troubleshooting with the kernel and Xorg. A few other things I worked out myself.

      My experience with everything set up is less than a day. However, even so, I would recommend at least trying gentoo. It really helps you to understand what makes up your system, how things work, and how to do every day stuff from the command line. Arch can do all of that, only gentoo forces you to learn it. You need not compile your own kernel, you can use genkernel. Everything is done for you there.In the end, you have a nice organized system that is 100% compatible with your computer (if you did everything right).

      Xorg is a pain. Your make.conf file tells your compiler what to do, if your use flags are incorrect you may have quite a few headaches  on your hand. For example, if a - is applied before installing something that requires that flag, it will not compile. This can be good, and bad. Speaking of which, Xorg is a great example of this. I had -X in my use flags, so that Xorg files did not get loaded before I installed Xorg. Silly me, I left it on while installing X. 3 pages on the forums got me nowhere until I realized what went wrong. Some xorg files I installed previously, blocked other packages, and that was an issue too. This shows that your greatest strength can also be your greatest weakness.

      Gentoo is a very stable system if set up correctly, and is a great learning experience. I'm using it right now, and I'm actually impressed that Xorg finally installed.

      Some prerequisites for future gentoo users:


[LIST]
[*]Patience. You absolutely need this. Without it, gentoo may not be installed correctly.
[*]Some hard drive space.
[*]And the strength needed to go on when it seems all hope is lost.
[/LIST]

---

### Post by magmon on 2010-01-09
I'm glad you had a positive experience with gentoo, but I'm more of a "if it works, don't question it" kind of guy. Sure, I know what guts I have, but I don't care what they do xD.

---

### Post by AllRadioisDead on 2010-01-09
Your story changed my life.

---

### Post by blithen on 2010-01-09
Very nice story, I've tried multiple times with gentoo, and arch, and I'm missing the entire patience thing, so one day I will eventually get them installed.

---

### Post by squilookle on 2010-01-09
I tried the live cd a few times, just to test it before taking the plunge - and it wouldn't even start. Then I tried the install disc and I had the same problem and gave up. 

It sounds too time consuming to me anyway. 

Well done for getting it up and running though.

---

### Post by Icehuck on 2010-01-09
> **squilookle said:**
> I tried the live cd a few times, just to test it before taking the plunge - and it wouldn't even start. Then I tried the install disc and I had the same problem and gave up. 

It sounds too time consuming to me anyway. 

Well done for getting it up and running though.

The Gentoo install CD's have been broken for a long time. They know this and don't care to fix it(even though they make new cds every other week). This might have changed in the last few months but I seriously doubt it.

---

### Post by witeshark17 on 2010-01-09
That's pretty cool. I suppose I might set a test box for it for fun! :popcorn:

---

### Post by RiceMonster on 2010-01-10
> **dragos240 said:**
> [LIST][*]Patience. You absolutely need this. Without it, gentoo may not be installed correctly.[/LIST]

This where you lose me. I'm WAY too impatient to go with Gentoo :p.

---

### Post by Linuxforall on 2010-01-10
How bout using something like Toorox which is Gentoo based and easy to install. It also follows strict Gentoo guidelines and no modification is done. Take a look here at [http://toorox.de/](http://toorox.de/)

---

### Post by QwUo173Hy on 2010-01-10
Nice job dragos240. I tried to install Gentoo a few years ago - in search of the leanest install possible. I don't think I made it past stage 2 LOL.

But I did find a new reverence for the Mandrake installer, at the time. ;)

---

### Post by schauerlich on 2010-01-10
> **dragos240 said:**
> I went through a lot of troubleshooting with the kernel and Xorg. A few other things I worked out myself.

only gentoo forces you to learn it. 

In the end, you have a nice organized system that is 100% compatible with your computer (if you did everything right).

      Xorg is a pain. 

if your use flags are incorrect you may have quite a few headaches  on your hand. 

it will not compile. This can be good, and bad. 

Xorg files did not get loaded before I installed Xorg. 

3 pages on the forums got me nowhere until I realized what went wrong. Some xorg files I installed previously, blocked other packages, and that was an issue too. 

if set up correctly, 

I'm actually impressed that Xorg finally installed.

Patience. You absolutely need this. Without it, gentoo may not be installed correctly.

And the strength needed to go on when it seems all hope is lost.

No thanks.

---

### Post by dragos240 on 2010-01-10
> **RiceMonster said:**
> This where you lose me. I'm WAY too impatient to go with Gentoo :p.

You're not alone RiceMonster. Most people don't have the patience to install gentoo.

---

### Post by NoaHall on 2010-01-10
> **dragos240 said:**
> 
[LIST]
[*]Patience. You absolutely need this. Without it, gentoo may not be installed correctly.
[*]Some hard drive space.
[*]And the strength needed to go on when it seems all hope is lost.
[/LIST]

I'd add a relativity good CPU to the list. If it's too slow, it takes forever.

---

### Post by insane_alien on 2010-01-10
last time i tried gentoo i spent a week on it and just about managed to get a barely working GUI.

they really need to get an installer sorted out for it.

---

### Post by dragos240 on 2010-01-10
> **NoaHall said:**
> I'd add a relativity good CPU to the list. If it's too slow, it takes forever.

Yes, but that's recommended.

---

### Post by NoaHall on 2010-01-10
> **dragos240 said:**
> Yes, but that's recommended.

Regardless, I have known people to try and run it on very very slow systems :)

---

### Post by dragos240 on 2010-01-10
> **NoaHall said:**
> Regardless, I have known people to try and run it on very very slow systems :)
 
Yeah, which is probably not the best idea.

---

### Post by Eisenwinter on 2010-01-11
I'm not patient enough to install Gentoo.

I tried it once, and after 7 hours of downloading sources and compiling, I was sick of it, so I aborted the installation.

---

### Post by taipan67 on 2010-01-17
I was a ***"Gentooligan"*** for 5 years before recently installing Ubuntu over one of my Gentoo systems - haven't touched my other, remaining Gentoo system in weeks! Right now, i couldn't be happier with the Ubuntu experience.:cool: 

I have no regrets regarding my time using Gentoo - i'm quite sure i know a hell of a lot more about Linux now than i would if i'd been on anything more *"user-friendly"* instead.

I've also built a few [Linux From Scratch]("http://linuxfromscratch.org") systems, and subscribed to their mailing-lists for a long time. If you ever want an education, i highly recommend it. ;) 

I mention **LFS** because i get the distinct impression that one of the architects of it's build-process, Greg Schafer of the related [DIY-Linux]("http://www.diy-linux.org/") project, has been less active in recent months at least partly because he's predominantly using Ubuntu now, as well...

...My point being that the sheer workload of maintaining a manually-compiled system seems to be the proverbial *"straw that breaks the camel's back"*...

...I'd be interested in hearing the views of any other Ubuntu-users with a source-based background. :?

---

### Post by dragos240 on 2010-01-17
> **taipan67 said:**
> I was a ***"Gentooligan"*** for 5 years before recently installing Ubuntu over one of my Gentoo systems - haven't touched my other, remaining Gentoo system in weeks! Right now, i couldn't be happier with the Ubuntu experience.:cool: 

I have no regrets regarding my time using Gentoo - i'm quite sure i know a hell of a lot more about Linux now than i would if i'd been on anything more *"user-friendly"* instead.

I've also built a few [Linux From Scratch]("http://linuxfromscratch.org") systems, and subscribed to their mailing-lists for a long time. If you ever want an education, i highly recommend it. ;) 

I mention **LFS** because i get the distinct impression that one of the architects of it's build-process, Greg Schafer of the related [DIY-Linux]("http://www.diy-linux.org/") project, has been less active in recent months at least partly because he's predominantly using Ubuntu now, as well...

...My point being that the sheer workload of maintaining a manually-compiled system seems to be the proverbial *"straw that breaks the camel's back"*...

...I'd be interested in hearing the views of any other Ubuntu-users with a source-based background. :?

Still using gentoo now! I have gnome, kde, openoffice, and firefox installed, ALL built from source! Works great for me!

---

### Post by RedSquirrel on 2010-01-17
> **taipan67 said:**
> ...My point being that the sheer workload of maintaining a manually-compiled system seems to be the proverbial "straw that breaks the camel's back"...

...I'd be interested in hearing the views of any other Ubuntu-users with a source-based background. 

I like to try out each new Ubuntu release but I don't usually keep them around for very long.  Gentoo is my main OS.

I hadn't synced the Portage tree for a few days and when I did so yesterday, I was presented with a rebuild of gcc and an update to glibc. :lol:

The rebuild of gcc was something I could have ignored since it was just removing some USE flags that I had not set in the first place. However, I decided, you know, just for fun, to perform a gcc version update that I had been masking for a while. Everything worked out fine, but this morning, I began to wonder just how much my computer appreciated working its way through that update. I have a bad feeling that one day my computer's hardware is going to suffer a Gentoo-induced calamity. :) (I've masked the glibc update for now.)

I like to try out other distributions to see what they're up to. There have been quite a few times that I've installed other distributions in an attempt to leave Gentoo behind, but I always find enough issues with them that Gentoo seems like a better fit (for me). Right now, though, I've got a tiny craving for the convenience of pre-compiled binaries.

---

### Post by yabbadabbadont on 2010-01-17
Masking glibc was probably a good idea.  From what I've read on fgo, it appears to have broken name resolution.  Then you would be stuck booting a live cd and chrooting in order to fix it.  :lol:

---

### Post by dragos240 on 2010-01-17
> **RedSquirrel said:**
> I like to try out each new Ubuntu release but I don't usually keep them around for very long.  Gentoo is my main OS.

I hadn't synced the Portage tree for a few days and when I did so yesterday, I was presented with a rebuild of gcc and an update to glibc. :lol:

The rebuild of gcc was something I could have ignored since it was just removing some USE flags that I had not set in the first place. However, I decided, you know, just for fun, to perform a gcc version update that I had been masking for a while. Everything worked out fine, but this morning, I began to wonder just how much my computer appreciated working its way through that update. I have a bad feeling that one day my computer's hardware is going to suffer a Gentoo-induced calamity. :) (I've masked the glibc update for now.)

I like to try out other distributions to see what they're up to. There have been quite a few times that I've installed other distributions in an attempt to leave Gentoo behind, but I always find enough issues with them that Gentoo seems like a better fit (for me). Right now, though, I've got a tiny craving for the convenience of pre-compiled binaries.

I usually use a set of applications, while waiting for something to compile. Or if I'm compiling my system, I usually have another OS that I chroot from.

---

### Post by QwUo173Hy on 2010-01-18
My will to put work in to get a usable and enjoyable system is reducing every year. Over five years ago, there was a lot of work involved for a newbie to get a system working - and those were binary systems. Today, if it doesn't install and run as well as Ubuntu with something that is (for me) easy to use -  I'll get a notebook!

---

### Post by Sporkman on 2010-01-18
> **taipan67 said:**
> 
...My point being that the sheer workload of maintaining a manually-compiled system seems to be the proverbial *"straw that breaks the camel's back"*...


Yes - Ubuntu provides this extra value for free (by teams of people much more qualified than I) - why not take advantage of it?

---

### Post by taipan67 on 2010-01-18
> **yabbadabbadont said:**
> ......<Snipped>......
Now where do i know that username from..? :lol:

---

### Post by hessiess on 2010-01-18
I have played around with Gentoo in the past, however I don't have anywhere near enough time to maintain a distro which compiles everything from source. Arch provides a comparable level of customisability with a fraction of the install/maintenance time because of the use of binary packages.

The only Program I normally compile is Blender, checked out directly form the SVN repo.

---

### Post by HermanAB on 2010-01-18
Howdy,

My take on it is that Gentoo, LFS and others are nice for learning Linux, but one should dedicate a machine to it.  One's main system should be a separate Ubuntu, Fedora or Mandriva machine, in order to be able to get some real work done too.

---

### Post by Sporkman on 2010-01-18
> **HermanAB said:**
> One's main system should be a separate Ubuntu, Fedora or Mandriva machine, in order to be able to get some real work done too.

Ouch! :lol:

---

