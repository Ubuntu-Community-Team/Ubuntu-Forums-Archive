---
title: "Mir's strongest selling point was actually developed for Wayland by Jolla?"
date: 2013-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by tartalo on 2013-04-12
I thought that Mir's strongest selling point was that it would eventually be possible to use Android drivers with it. So this article was an eye opener for me:

[http://mer-project.blogspot.fi/2013/04/wayland-utilizing-android-gpu-drivers.html](http://mer-project.blogspot.fi/2013/04/wayland-utilizing-android-gpu-drivers.html)

---

### Post by sanderj on 2013-04-12
I'm not a Mir nor Wayland expert, but I would say 
- Mir has the Android-driver-stuff included in its project scope
- Wayland has no Android-driver-stuff included in its project scope, but someone else is working on it

Related reading:

[http://www.cnx-software.com/2013/03/05/future-versions-of-ubuntu-to-feature-mir-display-server-compatible-with-android-graphics-drivers/](http://www.cnx-software.com/2013/03/05/future-versions-of-ubuntu-to-feature-mir-display-server-compatible-with-android-graphics-drivers/)
[http://www.cnx-software.com/2013/04/08/libhybris-let-you-use-android-drivers-hw-libraries-in-linux/](http://www.cnx-software.com/2013/04/08/libhybris-let-you-use-android-drivers-hw-libraries-in-linux/)

---

### Post by tartalo on 2013-04-12
> **sanderj said:**
> I'm not a Mir nor Wayland expert, but I would say 
- Mir has the Android-driver-stuff included in its project scope
- Wayland has no Android-driver-stuff included in its project scope, but someone else is working on it

Related reading:

[http://www.cnx-software.com/2013/03/05/future-versions-of-ubuntu-to-feature-mir-display-server-compatible-with-android-graphics-drivers/](http://www.cnx-software.com/2013/03/05/future-versions-of-ubuntu-to-feature-mir-display-server-compatible-with-android-graphics-drivers/)
[http://www.cnx-software.com/2013/04/08/libhybris-let-you-use-android-drivers-hw-libraries-in-linux/](http://www.cnx-software.com/2013/04/08/libhybris-let-you-use-android-drivers-hw-libraries-in-linux/)

Precisely, the article I linked has been written by the Jolla engineer that develops libhybris, I'll quote the Ubuntu-related part:

> Open sourcing [libhybris] worked quite well - a small group of people got together, tested it,  improved it, got it running on a lot of multiple chipsets - thanks to OpenWebOS, Florian Haenel (heeen), Thomas Perl (thp), Simon Busch (morphis) and others. It turned the project from a late night hacking project into a viable solution for building device OS'es on top of. Or even running Android NDK applications using.

Earlier this year however, I discovered that a well-known company had taken the code - disappeared underground with it for several months, improved upon it, utilized the capability in their advertisements and demos and in the end posted the code utilizing their own source control system, detached from any state of that of the upstream project's. Even to the extent some posters around the web thought libhybris was done by that company itself.

That kind of behavior ruined the initial reason I open sourced libhybris in the first place and I was shocked to the point that I contemplated to by default not open source my hobby projects any more. It's not cool for companies to do things like this, no matter your commercial reasons. It ruins it for all of us who want to strengthen the open source ecosystem. We could have really used your improvements and patches earlier on instead of struggling with some of these issues.

But, I will say that their behavior has improved - they are now participating in the project, discussing, upstreaming patches that are useful. And I forgive them because they've changed their ways and are participating sanely now.

---

### Post by 3rdalbum on 2013-04-12
There's not really any details about how this feat is accomplished. It might be that Wayland is running on top of Android's windowing agent, or you have to patch Wayland for every different binary driver. Maybe only basic features in Wayland can be abstracted to the Android driver, without being able to support multitouch or video decode acceleration. Who knows? There's a second article coming out that will reveal how it's done.

---

### Post by tartalo on 2013-04-12
> **3rdalbum said:**
> There's not really any details about how this feat is accomplished. It might be that Wayland is running on top of Android's windowing agent, or you have to patch Wayland for every different binary driver. Maybe only basic features in Wayland can be abstracted to the Android driver, without being able to support multitouch or video decode acceleration. Who knows? There's a second article coming out that will reveal how it's done.

I found this in Slashdot. Does it answer any of the questions? 
[http://tech.slashdot.org/comments.pl?sid=3639581&cid=43430347](http://tech.slashdot.org/comments.pl?sid=3639581&cid=43430347)

If I undertand it correctly patching Wayland for every binary driver wouldn't be necessary, nor inviting Android's windowing agent to the party. Is that right?

---

### Post by grahammechanical on 2013-04-12
Suddenly, open source is not so open source after all. Anyone can, and often many people have, take code licensed under the GPL and use it for their own projects. But it seems that Canonical cannot do this without being called sneaky. Ubuntu is open source. Canonical code is open source. Plenty of people work on projects in secret or to put it more correctly, in private. What is wrong with that. Before you can make code available you first have to have code that works.

These people would be happy to take Canonical's money and deny Canonical influence in the development process. Oh, yes, for sure. Canonical makes money but it does not make a profit. Why? It spends its money hiring people.

If you do not want anyone that you do not approve of using your code, then do not release it under an Open Source license.

---

### Post by hainen on 2013-04-12
That is not true. It has always been bad style to fork something and make it hidden a long time before you release.
It is a different thing if its something you have done from scratch and not a fork of a already working project. But obviously so long you release the code when you distribute the binaries you are legally on secure ground.
But if you look at the kernel which has been culturally very important in the free software world I get the impression they usually develop  new functionality in the open from start.

---

### Post by mikodo on 2013-04-12
> **hainen said:**
> That is not true. It has always been bad style to fork something and make it hidden a long time before you release.
It is a different thing if its something you have done from scratch and not a fork of a already working project. But obviously so long you release the code when you distribute the binaries you are legally on secure ground.
But if you look at the kernel which has been culturally very important in the free software world I get the impression they usually develop  new functionality in the open from start.
  Are you saying that others before Ubuntu haven't taken open source code, developed it to their liking in house, before releasing the code hasn't been in practice?

If that is that the case, then things are changing. But, I doubt it isn't new. 

;p

---

### Post by JDShu on 2013-04-12
> **mikodo said:**
> Are you saying that others before Ubuntu haven't taken open source code, developed it to their liking in house, before releasing the code hasn't been in practice?

If that is that the case, then things are changing. But, I doubt it isn't new. 

;p

No. That's not what hainen said. He said that it has always been bad style to do what Canonical did, no matter who you are.

---

### Post by 3rdalbum on 2013-04-13
Sometimes, you just gotta do it to keep the project moving. Take KHTML - it was being developed very slowly, and then Apple ran with it and the end result became Webkit. Everyone benefitted from Webkit.

---

### Post by Gyokuro on 2013-04-13
> **grahammechanical said:**
> Suddenly, open source is not so open source after all. Anyone can, and often many people have, take code licensed under the GPL and use it for their own projects. But it seems that Canonical cannot do this without being called sneaky. Ubuntu is open source. Canonical code is open source. Plenty of people work on projects in secret or to put it more correctly, in private. What is wrong with that. Before you can make code available you first have to have code that works.

These people would be happy to take Canonical's money and deny Canonical influence in the development process. Oh, yes, for sure. Canonical makes money but it does not make a profit. Why? It spends its money hiring people.

If you do not want anyone that you do not approve of using your code, then do not release it under an Open Source license.

It's fine to use GPL code for own projects but it is the way how Canonical has announed MIR. Most of the stuff is not in-house developed (3rd party code) and they made false claims about Wayland in general. There is no single part of their requirement  which can not be done in Wayland or it is already in Wayland. As I have already posted in the forum but MIR is only Canonicals requirment to bring along their vision of Unity over various platforms and to have control of it's further development. The problem with Canonical is that they were not good team players in the past and not good at comuniticating and working upstream and in general they take much more from upstream as they are supporting them with their developers (check the commits for canonical of various projects like Kernel, GCC, Libc/eglibc and then you will see who is the biggest contributor). To act like a big contributor is easy but in the end it only counts how much LOCs you have have released in various upstream projcts and LOCs influence further development of projects not marketing fuss.

---

### Post by sanderj on 2013-04-13
> **Gyokuro said:**
> <snip> To act like a big contributor is easy but in the end it only counts how much LOCs you have have released in various upstream projcts and LOCs influence further development of projects not marketing fuss.

IMHO Canonical is the biggest contributor to making Linux mainstream. So, if contributing to the kernel is called "upstream", I would call Canonical the biggest "downstream" contributor: making Linux extremely user friendly. And Linux needs both to be successful and relevant

---

### Post by Gyokuro on 2013-04-13
> **sanderj said:**
> IMHO Canonical is the biggest contributor to making Linux mainstream. So, if contributing to the kernel is called "upstream", I would call Canonical the biggest "downstream" contributor: making Linux extremely user friendly. And Linux needs both to be successful and relevant

In polishing and packaging a nice distribuiton - yes I agree as nobody of the other big players managed it to deliver a product which can be used/tested by people without a degree in computer science. However if you look at their contributions from the technical site of OSS there is not much were upstream projects gained something back from said company. Bzr, launchpad, unity,.. are mostly used in Ubuntu's universe not outsite as too much ubuntu centric or not the best technical solutions and a lot of people do not like the Ubuntu developer license agreement. In my opinion they try to force with the amount of it's user base Mir as the standard X11 replacement whether it works time will show but as developers/maintainers in upstream projects can accept or deny MIR support patches it will get interesting how this get solved and that this MIR support patches have to be done in the next time is important otherwise a lot of applications will not work/limited (time frame between next Ubuntu and LTS is for such a task is really short). To maintain this patches outsite of various upstream projects (GTK, QT) get a burden over time and you lack behind of features in said libs in the same time but that's the price you have pay for to be the lone fighter.

---

### Post by hainen on 2013-04-13
Many GNU project use Bzr. 
And even if many has switched to systemd and systemd has more momentum today many distributions has used or use upstart today.

---

### Post by BigCityCat on 2013-04-13
So Ubuntu didn't do anything wrong but some people don't like the way they operate. Cry me a river already. Don't use it then. Problem solved but I'm tired of all the cry babies. Some people don't like the way Ubuntu operates. Okay and I don't like all the bitching and whining either. When they close the code then I'm moving on.

---

### Post by tartalo on 2013-04-13
Well, I think that both the state of two competing projects and the state of the relationship between Ubuntu and the rest of Linux related projects are interesting, worthy of discussion, and relevant to this "Ubuntu, Linux and OS Chat".

The relationship between Ubuntu and other Free Software projects has been a matter of discussion [since it's birth]("http://mako.cc/writing/to_fork_or_not_to_fork.html")

Ubuntu wasn't the first fork in the history of Free Software, there had and have been many forks for [many different reasons]("https://helda.helsinki.fi/handle/10138/36879").

I don't really know if I've heard more about Ubuntu's case because as a user of both Debian and Ubuntu I payed more attention, or because there was something different about it.

That was long ago and it's seldom a topic of discussion anymore, but since the relationship between [Canonical and Gnome]("http://news.slashdot.org/story/11/03/12/2329233/the-full-story-behind-the-canonical-vs-gnome-drama") deteriorated, Canonical's attitude towards upstream projects has changed in a bad way, or is it the other way around? Mark Shuttleworth keeps hinting hidden intentions in different projects, is he right?

In any case, more and more people in the Free Software world is expressing dissatisfaction with Canonical, and that is not a good thing, because Ubuntu depends on the work of many people that don't work for Canonical.

I guess that we will have many more opportunities to analyze the gray area between what's allowed by the license and what different people consider acceptable. The positions in the desktop are quite settled but there are real opportunities to gain relevance in the growing mobile market, and timing is crucial for that.

---

### Post by mikodo on 2013-04-13
@tartalo

I think you are probably correct. An epic battle has probably begun between the supporters of Gnome and Canonical because of the mobile market. Of course though, add in Mozilla, Android, OS X, MS and Google, to confuse things. 

There are too many self-interest groups with linux to not see this competition happen time and time again. Yes, it would be nice to have everything in FLOSS stay with all code being shared and worked on in fellowship together, but it isn't and won't. Companies are vying for their share of a growing territory and that is taking precedence.

Do I wish things were different. All the time. I try to choose the best options and at times it boils down to the lessors of evils. 

;p

---

### Post by BigCityCat on 2013-04-13
Yeh sorry bout that. I've been reading too much Phoronix. They have been very anti Ubuntu.

---

### Post by tartalo on 2013-04-14
> **BigCityCat said:**
> Yeh sorry bout that. I've been reading too much Phoronix. They have been very anti Ubuntu.

I just wanted to tell you that I fully understand your initial reaction, and also that I appreciate your later message, but in your spontaneous answer you said something that is very meaningful, and as the message I linked, you opened my eyes too, I just needed more time to let it sink. 

For many years Ubuntu has been the distro that has suited my needs best, and even if it doesn't now it's unfair to spoil it for those that still love it.

So, It's distro hoping time again!

PD: No sarcasm, no anger, and thank you.

---

