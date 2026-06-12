---
title: "FreeBSD, It's a Shame..."
date: 2009-07-20
forum: The Cafe
---

### Post by raronson on 2009-07-20
Hi.  I just wanted to your take on the issue of community and commercial support for FreeBSD compared to GNU/Linux...

I used FreeBSD for a number of years and finally switched back to Linux after the binary compatibility layer came out (this allows FreeBSD to run native Linux applications--like the Linux version of Firefox, which had better support for flash at the time).  "What's the point now?", I reasoned.  "All of the development effort is going toward Linux these days."  This was also true for driver support, bleeding edge software, innovation, and public mindshare.

As I cut ties with FreeBSD, I just remember thinking, "What a shame."  FreeBSD has its merits; first and foremost that it is a complete operating system:  has its own kernel, userspace, services, applications, package manager, documentation, etc.  By way of comparision, Linux-proper is just a kernel, relying on GNU for the other half of the OS.  Now arguments aside about technical differences and performance related issues, the two systems are roughly equivocal.  It's just that FreeBSD was still caught up in legalities while nascent Linux quickly grew a huge following and corporate support from companies like IBM.

Though consider:  if everyone had jumped onboard with FreeBSD, we wouldn't have a million different distributions and all of the disconnected collaboration spent on, making a better package manager, for example.  With the full support of the FOSS community, FreeBSD could have taken us farther and faster than we've come with Linux(?).  I mean, it's only just now that Ubuntu is winning the distro wars and causing GNU/Linux to shape up as a bona fide replacement for commericial OS offerings.  In the popular mind, Ubuntu *is* Linux today.  Who knows, maybe tomorrow it will be Google's Chrome--which will cause another split, but hopefully stabilize out and draw the full attention of the FOSS community and commericial sector.

My intention isn't to compare this-thing-to-that, but only to pose a couple of questions: should everyone be on the same page?  Do you think better progress could be made if everyone developed and advocated from a single platform?

Some of my own objections / counter arguments:

- Diversity in GNU/Linux distributions is a strength--not a weakness.
- Too many cooks would spoil the broth
- A project so large couldn't be effectively organized (i.e., it wouldn't be productive).
- People would lose freedom by having to agree and make compromises about how to best do things.
- Isn't this already happening now with GNU/Linux?  (Yeah, but there's no standard).
- FreeBSD would've fragmented off in a myriad of incarnations (there's already OpenBSD, NetBSD, Dragonfly, etc.).
- Farther or faster than what? Farther in software per se (see this post: [http://ubuntuforums.org/showthread.php?p=7629147#post7629147](http://ubuntuforums.org/showthread.php?p=7629147#post7629147)).

This is just brainstorming out loud about an idea that's always been rolling around in my mind.  I'm not trying to convince anyone of anything.  I guess just reply to any of the above spew that catches your attention.

-Cheers.

---

### Post by SunnyRabbiera on 2009-07-20
Well the major reason why open source developers avoided BSD is because of the old BSD license.

---

### Post by Grant A. on 2009-07-20
> **SunnyRabbiera said:**
> Well the major reason why open source developers avoided BSD is because of the old BSD license.

Exactly. I don't think IBM would be too keen on helping out with FreeBSD's development, only to have Microsoft or Apple legally embrace, extend, and extinguish.

---

### Post by raronson on 2009-07-20
> **SunnyRabbiera said:**
> Well the major reason why open source developers avoided BSD is because of the old BSD license.

Bah.  I knew I forgot to mention something in my objections (I tried to account for possible arguments).

Though really.  A license, like any other cog in the system could evolve and take on a life of its own.  No different than a software package changes.

The license probably is the single greatest factor--but it side-steps the main question of whether the community could have advanced software further by cooperation instead of competition.  Sorry I failed to include that.

---

### Post by bodhi.zazen on 2009-07-20
IMO the biggest problems with BSD were :

1. The installer is a real pain. Every time I suggested that to the BSD community they say well but bal bla bla.

Ubuntu took off because they took a very solid distro (Debian) and gave it a user friendly installer. At the time Anaconda was one of the only user friendly alternates, but installing Debian was similar to BSD (and not too new user friendly).

As an aside, Arch Linux has the same problem. Not many new users want to edit config files with vim / nano to install Arch (would help if the config files were a bit more "standard"). On the flip side, the installer forces you to understand how to sys admin so it is a trade off.

This is changing, but too little too late.

2. Number 2 is package management. The ports system is awesome, but, too complex for new users. if you look on these forums you will see new users want an easy way to install applications.

3. A real lack of live CD. I think the FreeBSD community seriously misjudged these tools, PC-BSD and Desktop BSD were largely ignored by the grater BSD community.

Don't get me wrong, I am a command line junky, and I can sys admin BSD no problem.

Once FreeBSD sets attracting new users and sets up a new user friendly set of basic sys admin apps and sets up a forums like Ubutnu they will be good to go.

Last time I checked the FreeBSD community, welcoming new users was low on the priority list. I do not think Arch is catering to new users either, just not a goal of the distro.

---

### Post by ghindo on 2009-07-20
As sort of an aside, wasn't FreeBSD given US government funding for a while?  Or is that another BSD I'm thinking of?

---

### Post by froggyswamp on 2009-07-20
I think for every argument there is a counter argument (as you seem to give in).

However, I would say **people** are the most precious resource, not the business model.
To me, a company can succeed or fail with any OS and any business model (open or closed source) as long as they have professional programmers and an administration that takes  fast and wise decisions.

---

### Post by DeadSuperHero on 2009-07-20
I happen to be tinkering with PC-BSD at the moment. I really love the Ports system, and the simplified app installation tool is pretty sweet.
 
But this has always been an issue for me: most FreeBSD distributions are binary and source compatible with one another. They derive from a standard codebase, with standard libraries. Most of them use the same ports trees.
 
My biggest beef with Linux sometimes is just the sheer diversity of it all. Packaging a game to work across distributions is frustrating due to different packaged library versions. The problem is less pronounced than it used to be, but it's still a fairly formidable problem for game developers.

---

### Post by aysiu on 2009-07-20
> **bodhi.zazen said:**
> 
Ubuntu took off because they took a very solid distro (Debian) and gave it a user friendly installer. At the time Anaconda was one of the only user friendly alternates, but installing Debian was similar to BSD (and not too new user friendly). I'm going to have to disagree with you there, bodhi. I wasn't around for Warty, but I have been using Ubuntu since Hoary, and it was all the buzz even back in 2005, back when it was still using the ncurses Debian installer (in those days, there were two CDs you got from ShipIt--one was a live CD, the other an installer CD). Anaconda was user-friendly, and Mepis' custom installer was user-friendly (and a lot like Ubuntu's later Ubiquity).

I have my own theories about [how Ubuntu ended up so popular among Linux distros](http://www.psychocats.net/ubuntucat/how-did-ubuntu-end-up-so-popular/).

> **raronson said:**
> 
Some of my own objections / counter arguments:
- Diversity in GNU/Linux distributions is a strength--not a weakness. Well, in theory, yes. Part of the problem we see is unnecessary diversity... or a lack of *enforced* standards. There should be an agreed-upon way to organize application files and libraries so that if I *alien* an .rpm, it should install flawlessly even on my .deb-based system. Either KDE should not put that hidden .desktop file on the desktop or Gnome shouldn't show it. > - Too many cooks would spoil the broth Too many cooks is actually an argument against the closed source model of development, in which there is one project, and everyone working on that project has to agree on one way to go. With open source, there are many cooks, but they aren't all working on the same broth, and they are sharing all of their recipes with the other chefs. I cannot think of a more efficient way for a recipe to get better.

---

### Post by moster on 2009-07-20
This problems you mention is old as Jesus's donkey. BSD has its advantage, but I think if BSD is in linux boots it would be just same.

For me, flaw NO.1 is there is not standard packaging. And if you do get .deb for frikin Ubuntu 9.4 it still do not mean that you can 100% install it off line. It is too arrogant to ask that EVERYONE have flat broadband in this harsh world. It is just utterly stupid and everybody who needs to care shut their eyes for some reason.

---

### Post by HappinessNow on 2009-07-20
> **Mr. Psychopath said:**
> I happen to be tinkering with PC-BSD at the moment. I really love the Ports system, and the simplified app installation tool is pretty sweet.
 


PC-BSD is a very nice BSD Distro and one I consider the best of the best.

It is ashamed it is lacking in popularity on the Developer's side, it does have the potential to be one of the best Operating Systems. If it had the developers community that Ubuntu has it would shine. On it's own and in of itself it is doing rather nicely

> **aysiu said:**
> I'm going to have to disagree with you there, bodhi. I wasn't around for Warty, but I have been using Ubuntu since Hoary, and it was all the buzz even back in 2005, back when it was still using the ncurses Debian installer (in those days, there were two CDs you got from ShipIt--one was a live CD, the other an installer CD). 

Ubuntu buzz I agree started way back with Hoary, most people were excited about the free ship-it CDs. I remember tons of people exclaiming they ordered hundreds of ship-it CD's even though they had no idea or concept what Ubuntu or even Linux was. This obviously was not the intent of Mark Shuttleworth, but he does understand that it was mostly a numbers game. Get the CD's into as many hands as possible and like seeds in a garden they will take root and grow, this growth is exponentially increased with the more CD's that are shipped out.

I believe the free CD's were the catalyst that helped Ubuntu and Ubuntuforums grow to what it is today.

If anything it gave it notoriety, and a buzz among social networks and blogs that other distros simply never had.

Google with the induction of Google Chrome OS, brings Linux into the mainstream, beyond anything that Canonical/Ubuntu could have ever done. This will unite the development efforts considerably, and benefit Ubuntu greatly.

PC-BSD is an excellent operating system, let's hope they are here for the longevity.

> **SunnyRabbiera said:**
> Well the major reason why open source developers avoided BSD is because of the old BSD license.

Not being a lawyer I am not sure what to make of peoples commits about the BSD license, the latest BSD license is essentially the same as the MIT/X11 License which has been held as more substantial and better by many then the GPL. This is something I suspect that has yet to be proven in a court of law and all license have their strengths and weaknesses, GPL included.

EDIT: SunnyRabbiera, I just realized you stated the "Old BSD license"; "Old" being the key word here. Yes! the "Old BSD license" did have it's weaknesses, that were resolved (potentially) with the "New" BSD License but the confusion is the lack of the naming differential, substantial enough for people to realize the change. Yet, once the change took place the window of opportunity passed over BSD and was bestowed upon Linux by default.

---

### Post by forrestcupp on 2009-07-20
> **raronson said:**
> 
Though consider:  if everyone had jumped onboard with FreeBSD, we wouldn't have a million different distributions and all of the disconnected collaboration spent on, making a better package manager
You kind of disproved that point with this:

> **raronson said:**
> - FreeBSD would've fragmented off in a myriad of incarnations (there's already OpenBSD, NetBSD, Dragonfly, etc.).
There already *are* different forms of BSD.  If everyone would have went that way, there would be even more, and there would be just as many variations as there are Linux distributions.

---

### Post by raronson on 2009-07-20
> **froggyswamp said:**
> I think for every argument there is a counter argument (as you seem to give in).

However, I would say **people** are the most precious resource, not the business model.
To me, a company can succeed or fail with any OS and any business model (open or closed source) as long as they have professional programmers and an administration that takes  fast and wise decisions.

Yeah, I was chatting once in a Gentoo IRC channel and a guy said something that always stuck with me, "It's not that Linux is technically superior to BSD, it's the Linux Community."

---

### Post by Dr. C on 2009-07-20
> **Grant A. said:**
> Exactly. I don't think IBM would be too keen on helping out with FreeBSD's development, only to have Microsoft or Apple legally embrace, extend, and extinguish.

The biggest reason why FreeBSD will never get the kind of support that GNU / Linux has is because it is not licensed under a strong copyleft such as the GPL.

---

### Post by raronson on 2009-07-20
> **forrestcupp said:**
> You kind of disproved that point with this:


There already *are* different forms of BSD.  If everyone would have went that way, there would be even more, and there would be just as many variations as there are Linux distributions.

I was anticipating arguments which didn't address the main question...

---

### Post by moneysfire0 on 2009-07-20
:popcorn:The biggest reason why FreeBSD will never get the kind of support that GNU / Linux has is because it is not licensed under a strong copyleft such as the GPL.


Duh.

---

### Post by swoll1980 on 2009-07-20
> **raronson said:**
> I was anticipating arguments which didn't address the main question...

So what? Are you you waiting for some one to say freeBSD is better? I don't get what the point of this is. If you think it's better, that's all that matters. Why do you need to hear it from some one else?

---

### Post by Grant A. on 2009-07-20
> **FineE said:**
> The biggest reason why FreeBSD will never get the kind of support that GNU / Linux has is because it is not licensed under a strong copyleft such as the GPL.

Read what I was quoting... you just said exactly what I said.

---

### Post by moster on 2009-07-20
Not so long ago I installed one unamed OS that suppose to be next-big-thing. In installation it asked me if I have "PS/2 mouse or what?" It could not guess even that.

If I was Ballmer and trying other OSs I would laugh so hard that my big belly would hurt. So pathetic.

---

### Post by raronson on 2009-07-20
> **Mr. Psychopath said:**
> I happen to be tinkering with PC-BSD at the moment. I really love the Ports system, and the simplified app installation tool is pretty sweet.
 
But this has always been an issue for me: most FreeBSD distributions are binary and source compatible with one another. They derive from a standard codebase, with standard libraries. Most of them use the same ports trees.
 
My biggest beef with Linux sometimes is just the sheer diversity of it all. Packaging a game to work across distributions is frustrating due to different packaged library versions. The problem is less pronounced than it used to be, but it's still a fairly formidable problem for game developers.

Yeah, Psych--this is essentially what I was asking:  would things be further along if people stopped reinventing the wheel, and just agreed on a few standards?  As a technofuturist, I have this hypothesis that computing will be at the heart of a handful of technologies that will change the world for the better.  In order for this to happen, software needs to be emancipated from the confines of the operating system as we know it.

We get there sooner by agreeing upon a shared OS base from which to spring.  The OS will be just another protocol in a larger meta-system, and as standard as TCP/IP is today.

My real gripe with Microsoft is that they've held back legitimate computing by generations through the reinvention of a product that doesn't need to be sold anymore--the operating system.  They should accept the reality of Linux and get back to writing software; which they could still sell and make money from.

---

### Post by raronson on 2009-07-20
> **&#20170 said:**
> PC-BSD is a very nice BSD Distro and one I consider the best of the best.

Yeah.  Kris Moore's done a great job with PC-BSD.  I've test driven it and have been really impressed--it's just that I loathe KDE(3 & 4).  But he's got the right idea--and I picked FreeBSD for the discussion because of its largely unified system/codebase.  It's just too bad that Kris' project isn't getting a huge following.  It's things like this that will ultimately relegate FreeBSD to academia at UCLA Berkely.  Which is why I said it was a shame.

---

### Post by raronson on 2009-07-20
> **bodhi.zazen said:**
> IMO the biggest problems with BSD were :
...
As an aside, Arch Linux has the same problem. Not many new users want to edit config files with vim / nano to install Arch (would help if the config files were a bit more "standard"). On the flip side, the installer forces you to understand how to sys admin so it is a trade off.


Yeah.  I've been using Linux in one form or another since 1997, and it's finally okay to let the distribution do things for me in a sensible manner.  I'm reminded of ESR's, "How to Become a Hacker" ([http://catb.org/~esr/faqs/hacker-howto.html#believe3]("http://catb.org/%7Eesr/faqs/hacker-howto.html#believe3")) where he says that such things are actually "evil" because it falls under the category of drudgery. Brilliant document, but I personally think he's a self-aggrandising tool.

> 
...
Once FreeBSD sets attracting new users and sets up a new user friendly set of basic sys admin apps and sets up a forums like Ubutnu they will be good to go.
Bsdforums.org used to be awesome, but its sadly disappeared.

Thanks for your comments.

---

### Post by raronson on 2009-07-20
> **swoll1980 said:**
> So what? Are you you waiting for some one to say freeBSD is better? I don't get what the point of this is. If you think it's better, that's all that matters. Why do you need to hear it from some one else?

Not at all.  I was asking a question that pertained to cooperation versus competition.  FreeBSD was just used to illustrate the point.

---

### Post by DeadSuperHero on 2009-07-20
I'm currently looking into helping the PC-BSD project package up important apps for the pbiDIR service. I'm running into some snags with KDEnlive due to a problem compiling opencv.

I really think this project deserves some dedicated community support. The FreeBSD kernel and system is absolutely excellent. And the thing is, if you don't like the BSD license you can re-license everything that isn't a binary blob to be GPL, or proprietary. 

Another thing: I've never seen a single FreeBSD developer claim "It's the year of the FreeBSD desktop!" year after year. Their developer blogs are fairly calm, even if they're delivering a somber truth. They admit that their system is imperfect, and I respect them a lot for not sugar-coating things. Also, their announcements are actually a bit more interesting than the standard "Linux distribution x is out! Yay!", it's more like "FreeBSD 8 is almost out. On another note, libqt 4.5.3 has been moved to our testing area. After bugfixes and patching, it will hopefully be fully released to the community next month."

I think Linux developers could learn a lot from this sort of honesty, instead of tooting their own horns.

---

### Post by Methuselah on 2009-07-20
FreeBSD's sysinstall installer is not pretty but actually pretty easy to use.

The ports system is not really that hard to use:

cd ports/application
make install clean

But there are also binary packages for most software that can be installed with:
pkg_add -r application
That's not much harder that sudo apt-get install application.
And there is the wonderful side effect that ports get updated in a rolling manner separate from the base system so you can opt to stay quite up-to-date.

I used it for a while before linux and found it quite solid.
The reason I switched was a smaller and less accessible/friendly community and more hardware/software support difficulties than linux.
I mean, if I'm running things under linux binary compatibility why not just use linux when it's also free and open source?

---

### Post by swoll1980 on 2009-07-20
> **raronson said:**
> Yeah, Psych--this is essentially what I was asking:  would things be further along if people stopped reinventing the wheel, and just agreed on a few standards?  As a technofuturist, I have this hypothesis that computing will be at the heart of a handful of technologies that will change the world for the better.  In order for this to happen, software needs to be emancipated from the confines of the operating system as we know it.

We get there sooner by agreeing upon a shared OS base from which to spring.  The OS will be just another protocol in a larger meta-system, and as standard as TCP/IP is today.

My real gripe with Microsoft is that they've held back legitimate computing by generations through the reinvention of a product that doesn't need to be sold anymore--the operating system.  They should accept the reality of Linux and get back to writing software; which they could still sell and make money from.

Yeah Linux has way to many things going on, for sure. I wish there were some standards, but it's not going to happen. As far as how it would have been had freeBSD flourished. Forrestcup answered that question, and you blew him off. freeBSD would have 100 distros, and be as unstandardized as Linux is. In a free environment their is no way to enforce standards. I don't know why you think it would have ended up any differently. Would some BSD developer have held all the distros at gun point, and said "you have to do it this way"

---

### Post by DeadSuperHero on 2009-07-20
> **swoll1980 said:**
> Yeah Linux has way to many things going on, for sure. I wish there were some standards, but it's not going to happen. As far as how it would have been had freeBSD flourished. Forrestcup answered that question, and you blew him off. freeBSD would have 100 distros, and be as unstandardized as Linux is. In a free environment their is no way to enforce standards. I don't know why you think it would have ended up any differently. Would some BSD developer have held all the distros at gun point, and said "you have to do it this way"


Well, at least FreeBSD doesn't have that problem now...

---

### Post by raronson on 2009-07-20
> **swoll1980 said:**
> 
...
As far as how it would have been had freeBSD flourished. Forrestcup answered that question, and you blew him off.


Yes, because again, I'm not comparing the two (please see the bottom of my original post).  In plain English I'm saying two things:

- FreeBSD had great potential, it's a shame that it doesn't enjoy the popularity that Linux does.  Why?  Because it's closer to a unified system.  A unified system whether Linux, BSD, or BeOS would be better to spring from that a million projects all trying to accomplish the same thing.

- Second, *if* the community were to agree on a unified base (remember I mentioned Google Chrome) would it be better for the advancement of software?

What I'm not saying is that FreeBSD is better is Linux.  I posted arguments and oppositions to address that (so hopefully no one would lose focus and talk about them specifically), and then I went on to say that I'm not comparing this versus that.

Sorry if I confused you.

---

### Post by swoll1980 on 2009-07-20
Your confusing the  heck out of me. I thought you wanted to know what we thought would happen if it had been the other way. I guess I don't understand.

---

### Post by andrew.g on 2009-07-20
Sorry for the off-topic. Should I start a new thread?

I've looked at both PC-BSD and Desktop-BSD and both seem to be based on KDE, of one version or another. I'll get back to KDE 4 in the near future. 

The question I wish to ask is there any version of *BSD that is based upon Gnome or XFCE that is similar in ease of use and install as the two aforementioned distros?

---

### Post by swoll1980 on 2009-07-20
> **Mr. Psychopath said:**
> Well, at least FreeBSD doesn't have that problem now...

No it doesn't. PC-BSD is very well put together. It's a shame they don't have the driver support that Linux has.

---

### Post by raronson on 2009-07-20
> **swoll1980 said:**
> Your confusing the  heck out of me. I thought you wanted to know what we thought would happen if it had been the other way. I guess I don't understand.

Lol.  It's all the rambling that I do.   I tend to talk a long way around to come a short distance.  Too much coffee, methinks.

---

### Post by swoll1980 on 2009-07-20
> **andrew.g said:**
> Sorry for the off-topic. Should I start a new thread?

I've looked at both PC-BSD and Desktop-BSD and both seem to be based on KDE, of one version or another. I'll get back to KDE 4 in the near future. 

The question I wish to ask is there any version of *BSD that is based upon Gnome or XFCE that is similar in ease of use and install as the two aforementioned distros?

The best way to get Gnome on BSD is to install freeBSD and start from scratch, but this is not for the faint of heart. There is a Gnome distro, but I can't think of the name, and it is no where near as nice as PC-BSD

---

### Post by swoll1980 on 2009-07-20
> **raronson said:**
> Lol.  It's all the rambling that I do.   I tend to talk a long way around to come a short distance.  Too much coffee, methinks.

I will say that freeBSD is good stuff. Perhaps Debian's free BSD will bring it to the forefront.

---

### Post by iponeverything on 2009-07-20
I feel that a very large part of the reason for Ubuntu's success is Mark Shuttleworth. 

He had a vision and the means to bring that vision into reality. 

I have been linux user since 1993. I used slackware, then jumped ship for Red Hat. I, like many others felt we had been betrayed by Red Hat after their main focus shifted too much on making a profit, at the expense of the community. The same happened several other distro's Corel, Suse, etc. 

Shuttleworth has stuck to his guns and always put community over profit.  Mind share quickly shifted to Ubuntu when they felt that they were not going to be exploited. It all has to do with one unselfish person with a clear a vision -- making the world a better place through free software.


IMO

---

### Post by andrew.g on 2009-07-20
> **swoll1980 said:**
> The best way to get Gnome on BSD is to install freeBSD and start from scratch, but this is not for the faint of heart. There is a Gnome distro, but I can't think of the name, and it is no where near as nice as PC-BSD

Thanx, I'll consult Google. :D

---

### Post by yabbadabbadont on 2009-07-20
> **andrew.g said:**
> Thanx, I'll consult Google. :D

You can simply use pkg_add to install a binary package of gnome on FreeBSD.  Just like you could use apt-get to install KDE on Ubuntu.

---

### Post by nitehawk777 on 2009-07-20
> Bsdforums.org used to be awesome, but its sadly disappeared.

What about:

[http://forums.freebsd.org/](http://forums.freebsd.org/)

This forum seems pretty active,....

---

### Post by windows-killer on 2009-07-20
I should agree with the original poster. Linux devs should not fork other projects and make their own. They waste time and it becomes more complicated and inefficient. forking should be allowed only when a project is dead. By now if everyone was contributing code to the original projects Linux would have been a revolutionary OS with less bugs and more innovative features. Good point there buddy!

---

### Post by steveneddy on 2009-07-20
Well looky here - another Ubuntu convert.

---

### Post by clonne4crw on 2009-07-20
It's not only FreeBSD that's been left out in the cold to die. Solaris is very underdeveloped for the typical user enviroment.

---

### Post by Jimleko211 on 2009-07-20
> **windows-killer said:**
> I should agree with the original poster. Linux devs should not fork other projects and make their own. They waste time and it becomes more complicated and inefficient. forking should be allowed only when a project is dead. By now if everyone was contributing code to the original projects Linux would have been a revolutionary OS with less bugs and more innovative features. Good point there buddy!
You enjoy using Ubuntu, no?  Ubuntu is a "fork" of the Debian Operating System.  If we followed your rules we would have the original GNU/Linux OS and that's it.

---

### Post by HappinessNow on 2009-07-20
> **raronson said:**
> Yeah.  Kris Moore's done a great job with PC-BSD.  I've test driven it and have been really impressed--it's just that I loathe KDE(3 & 4).  But he's got the right idea--and I picked FreeBSD for the discussion because of its largely unified system/codebase.  It's just too bad that Kris' project isn't getting a huge following.  It's things like this that will ultimately relegate FreeBSD to academia at UCLA Berkely.  Which is why I said it was a shame.

> **andrew.g said:**
> Sorry for the off-topic. Should I start a new thread?

I've looked at both PC-BSD and Desktop-BSD and both seem to be based on KDE, of one version or another. I'll get back to KDE 4 in the near future. 

The question I wish to ask is there any version of *BSD that is based upon Gnome or XFCE that is similar in ease of use and install as the two aforementioned distros?

> **swoll1980 said:**
> The best way to get Gnome on BSD is to install freeBSD and start from scratch, but this is not for the faint of heart. There is a Gnome distro, but I can't think of the name, and it is no where near as nice as PC-BSD

**If you want Gnome on PC-BSD just install the pbiDIR for Gnome:**
[http://www.pbidir.com/bt/pbi/132/gnome](http://www.pbidir.com/bt/pbi/132/gnome)

They also have XFCE:
[http://www.pbidir.com/bt/pbi/200/xfce](http://www.pbidir.com/bt/pbi/200/xfce)

and enlightenment:
[http://www.pbidir.com/bt/pbi/201/enlightenment](http://www.pbidir.com/bt/pbi/201/enlightenment)

also here is the most recent changelog for PC-BSD 7.1.1 put out on 07-06-09

> PCBSD 7.1.1 - Changelog (07-06-09)
--------------------------
* Updated 7.2-Stable to 06242009
* Updated KDE to 4.2.4
* Updated Nvidia driver to 185.14 - [4071]("http://trac.pcbsd.org/changeset/4071") 
* Update the Nvidia driver 71.86.09 -> 71.86.11 which fixes the kernel panic - [URL="http://trac.pcbsd.org/changeset/4157"]4157
[/URL] * Fixed a bug when running Dolphin in root mode - [URL="http://trac.pcbsd.org/changeset/4176"]4176
[/URL] * Fixed bugs in py-cups port, which corrects "Print a test page" failure from the GUI - [URL="http://www.freebsd.org/cgi/query-pr.cgi?pr=ports/135675"]PR135675
[/URL] * Fixed bugs in ksyslog program, now finds /var/log/messages properly - Port Commit 
* Added gvim to the menu - [4114]("http://trac.pcbsd.org/changeset/4114") 
* Removed obsolete printing menu icons - [4115]("http://trac.pcbsd.org/changeset/4115") 
* Improved the system updater tray, don't issue popup on failure, change icon instead - [4100]("http://trac.pcbsd.org/changeset/4100") 
* Improved stability with intel graphics cards
* Updated included Wine to 1.1.24, which fixes issues with certain 3D Games
* Fixed issues with using the fetch ports GUI causing a crash in kcmshell4. - [4069]("http://trac.pcbsd.org/changeset/4069") 
* Improved the System Updater Tray to not use annoying popups and instead just change the icon - [4103]("http://trac.pcbsd.org/changeset/4103") 
* Added the older Nvidia 71.86.xx driver - [4066]("http://trac.pcbsd.org/changeset/4066") 
* Fixed issues with kppp, which needs suid permissions to function - [4061]("http://trac.pcbsd.org/changeset/4061") 
* Moved /PCBSD to /usr/PCBSD and created sym-link to allow small root partitions - [3999]("http://trac.pcbsd.org/changeset/3999")  - [4004]("http://trac.pcbsd.org/changeset/4004")  - [URL="http://trac.pcbsd.org/changeset/4008"]4008
[/URL] * Fixed bugs when "upgrading" a system that uses ZFS root partition - [3995]("http://trac.pcbsd.org/changeset/3995")  - [3997]("http://trac.pcbsd.org/changeset/3997") 
* Added support to give higher / lower priority to wifi connections - [3871]("http://trac.pcbsd.org/changeset/3871") 
* Added ability to edit saved wifi profiles - [3870]("http://trac.pcbsd.org/changeset/3870") 
* Added ability to "ignore" updates in the updater tool - [3842]("http://trac.pcbsd.org/changeset/3842") 
* Improved the system updater and tray application interaction - [3832]("http://trac.pcbsd.org/changeset/3832") 
* Fixed CUPS issues not finding all .ppd files correctly - [3833]("http://trac.pcbsd.org/changeset/3833")  - [3834]("http://trac.pcbsd.org/changeset/4834")  - [URL="http://trac.pcbsd.org/changeset/3822"]3822
[/URL] * Fixed bugs with xterm not running - [3804]("http://trac.pcbsd.org/changeset/3804") 
[COLOR=Black]*** Improved the default fluxbox configuration**[/COLOR] - [3793]("http://trac.pcbsd.org/changeset/3793")  - [3794]("http://trac.pcbsd.org/changeset/3794")  - [3798]("http://trac.pcbsd.org/changeset/3798")  - [3808]("http://trac.pcbsd.org/changeset/3808")  - [URL="http://trac.pcbsd.org/changeset/3809"]3809
[/URL] * Improved the KDE4 default theme - [3805]("http://trac.pcbsd.org/changeset/3805")  - [URL="http://trac.pcbsd.org/changeset/3810"]3810
[/URL] * Updated the KDM theme - [3812]("http://trac.pcbsd.org/changeset/3812")  - [3817]("http://trac.pcbsd.org/changeset/3817") 
* Improved the KSplash Theme - [3811 ]("http://trac.pcbsd.org/changeset/3811") 
* Misc other bugfixes [http://www.pcbsd.org/content/view/126/5/](http://www.pcbsd.org/content/view/126/5/)

---

### Post by raronson on 2009-07-20
Like I said, I never meant to talk specifically FreeBSD versus Linux.  From another writing, here's where I'm going with this (this was written for a non-technical audience some time ago; it's more futuristics and philosophy):

> 
 [FONT=DejaVu Sans Mono, sans-serif]
...

The Future of GNU/Linux[/FONT]
 [FONT=DejaVu Sans Mono, sans-serif]-----------------------[/FONT]
 
*[FONT=DejaVu Sans Mono, sans-serif]... I could go off into a tangent about how we need to save the masses from Microsoft, and mainly because we need open standards in all areas before the human race can really start using information technology for something meaningful ...[/FONT]*

 [FONT=DejaVu Sans Mono, sans-serif]I foresee a time in the future where all software is operating system agnostic; and going a bit further, that selling proprietary operating systems will cease to be a business altogether (selling support and services is another story). "Linux", like GNU before it, will play an important part in making this happen by offering free stable replacements to software, services, and standards that are not inherently open (note: GNU did this by replacing the pieces of UNIX itself that were not free and open). [/FONT] 
 

 [FONT=DejaVu Sans Mono, sans-serif]In the end, we'll all be "thin clients" attached by our various devices to something that I call in my fictional writing, "The Evernet." The Evernet too will be modularized into services, and our devices will connect to one or all of them powered by a tailored versions of the main standardized open operating system. That operating system will be "Linux"--and everything and everyone will use it. Operating system sales will cease (unless a software company is getting paid to create a tailored version of the main meta-distribution for a target product; note: they'll be paid for coding and support, not for the code itself), support services will rise, and "software" companies will go back to actually writing software-proper (but that's another story, and yes, they will still make plenty of money). [/FONT] 
 

 [FONT=DejaVu Sans Mono, sans-serif]So what am I saying here? That Linux *is* the future of computing. Once standards are completely opened up and legitimate progress in information technology is unhindered by companies unintentionally stifling it through the old world capitalistic model of selling something that doesn't need to be sold anymore, then real advances can be made. We're not fully cognizant yet of what computing can offer us, but it, along with a handfull of other technologies will shape the future for the benefit of everyone in ways that we can scarecly fathom today.

...
[/FONT][FONT=DejaVu Sans Mono, sans-serif]

And what are some of the things I'm referring to (from another thread)?

[/FONT]> 
...

The point of this is: focusing on operating system development has held back software, and thus put legitimate computing behind by light years. Just think of the software that we could all be using now if long ago in a perfect world everyone agreed to work on a mutually open foundation.

Who'd like to be able to walk into their house, say "lights", and have the lights turn on? Who'd like to be able to video conference with family and friends through your HD television instead of using cell phones? Who'd like to have bona fide virtual reality? Or a voice activated holographic mistress that performs a strip tease while you're watching the news. Who'd like to have a voice activated robot to fetch you a beer? Who'd like to see artificial intelligence aiding humanity in solving some of its biggest problems?

I'm just sick about it!  I want my damn holographic mistress.
[FONT=DejaVu Sans Mono, sans-serif]

Thanks for the conversation.

[/FONT]

---

### Post by phrostbyte on 2009-07-20
I think the biggest failure of BSD is it's license. You simply will not get massive commercial support with a license that allows a company like Microsoft to just copy/paste stuff from the OS into their OS without sharing back anything. How will get competitors to Microsoft to agree to put code in a license like that? It just seems unrealistic.

---

### Post by raronson on 2009-07-20
> **phrostbyte said:**
> I think the biggest failure of BSD is it's license. You simply will not get massive commercial support with a license that allows a company like Microsoft to just copy/paste stuff from the OS into their OS without sharing back anything. How will get competitors to Microsoft to agree to put code in a license like that? It just seems unrealistic.

It's funny you mention that.  I predicted long ago that Microsoft, in response to the threat of Linux, would gut its OS (keeping the graphical shell) and insert FreeBSD under the hood.

Well, I was wrong, but only about which company did it first (Apple).  Microsoft seems content to just keep polishing up reinvented versions of the Wheel.

---

### Post by ghindo on 2009-07-21
> **raronson said:**
> It's funny you mention that.  I predicted long ago that Microsoft, in response to the threat of Linux, would gut its OS (keeping the graphical shell) and insert FreeBSD under the hood.

Well, I was wrong, but only about which company did it first (Apple).  Microsoft seems content to just keep polishing up reinvented versions of the Wheel.If I'm not mistaken, Microsoft used a BSD's TCP/IP stack in pre-NT Windows.

---

### Post by raronson on 2009-07-21
> **ghindo said:**
> If I'm not mistaken, Microsoft used a BSD's TCP/IP stack in pre-NT Windows.

Yes, they did.  And if I'm not mistaken, Microsoft developed it's own version of UNIX which later became SCO... (Xenix, I think it was originally).  They also used FreeBSD to run their Hot Mail servers for the longest time.  How embarassing.. /snicker.

---

### Post by Grant A. on 2009-07-21
> **raronson said:**
> Yes, they did.  And if I'm not mistaken, Microsoft developed it's own version of UNIX which later became SCO... (Xenix, I think it was originally).  They also used FreeBSD to run their Hot Mail servers for the longest time.  How embarassing.. /snicker.

Ironically, FreeBSD was the operating system used to originally host the Ubuntu Forums.

Blame the Dong. :oops:

---

### Post by amitabhishek on 2009-07-21
> **swoll1980 said:**
> No it doesn't. PC-BSD is very well put together. It's a shame they don't have the driver support that Linux has.

I second that; I think its great when it comes out doing stuff right out of the box. The downer: It just can't run alongside Ubuntu. Neither of them acknowledge presence of the other while installing. :(

---

### Post by Darkhack on 2009-07-21
I've tried both FreeBSD 7.2 and 8.0-BETA2.  Both were a no go for me.  I get my internet access through a wireless USB adapter.  FreeBSD has drivers for the wireless adapter itself, but it chokes on my USB controller; meaning no USB devices work at all.  The chipset is an ATI SB400 which has no problems on Linux.

> **phrostbyte said:**
> You simply will not get massive commercial support with a license that allows a company like Microsoft to just copy/paste stuff from the OS into their OS without sharing back anything.

I actually prefer the BSD license.  I wouldn't mind if Microsoft used my code or the community's.  If it helps them to produce a better product, then I'd encourage it.  I actually worry about the GPL sometimes.  Some of the restrictions for GPLv3 software are very concerning to companies.  Google is avoiding GPLv3 software on Android because it would require them to allow third-parties to modify the software on the device itself.  This practice is also known as 'Tivoization', which I would discourage, but wouldn't outright ban the way GPLv3 does.

> **phrostbyte said:**
> How will get competitors to Microsoft to agree to put code in a license like that? It just seems unrealistic.

That actually sounds like an argument against open source as a whole rather than just the BSD license.  One could argue that they shouldn't put code under the GPL because their competitors could still benefit from it, even with the requirement to disclose changes.

Companies do release code under the BSD.  Apple has released [LLVM]("http://en.wikipedia.org/wiki/LLVM") under a BSD-style license.

---

### Post by raronson on 2009-07-21
> **clonne4crw said:**
> It's not only FreeBSD that's been left out in the cold to die. Solaris is very underdeveloped for the typical user enviroment.

Every time I walk into a "work environment" that has rows and rows of Windows machines, I just shake my head and feel bad for Sun Microsystems.  They made much better desktops and workstations with these specifically environments in mind.

It's a shame about that too...

---

### Post by lykwydchykyn on 2009-07-21
Seems that your original post is asking if the cathedral is better than the bazaar.  I guess I'm sold on the bazaar.  

I don't see all the diversity as waste or reinventing the wheel.  It's like natural selection, or the free market, or democracy.  It's slow, and inefficient; the majority don't survive.  But those that do survive are stronger and better.

We could have said ten years ago "let's all get behind red hat", but instead we had a lot of people that said "I can do better than red hat".  Most of them didn't, but the ideas they came up with (e.g., liveCD installation) lived beyond the distros and now Ubuntu has eclipsed red hat using many of those ideas.

What a shame if we now said "let's all get behind ubuntu and forget everyone else".  Because the distro that eventually replaces Ubuntu is likely to be more awesome than any Ubuntu we could create that way.

---

### Post by haemulon on 2009-07-21
Can anyone explain how the BSD license is workable when something as foolish as a "software patent" is allowed to exist?

It's a better license all around but not with the stupid concept of a "software patent" lurking around, the GPL is better for this environment.

---

### Post by lykwydchykyn on 2009-07-21
> **haemulon said:**
> Can anyone explain how the BSD license is workable when something as foolish as a "software patent" is allowed to exist?


I don't know.  Can you explain how it's not?

---

### Post by kk0sse54 on 2009-07-21
> **haemulon said:**
> Can anyone explain how the BSD license is workable when something as foolish as a "software patent" is allowed to exist?

It's a better license all around but not with the stupid concept of a "software patent" lurking around, the GPL is better for this environment.

Actually to many in the *BSD community the GPL is seen as more damaging than proprietary companies stealing code.

> GPL fans said the great problem we would face is that companies would take our BSD code, modify it, and not give back. Nope -- the great problem we face is that people would wrap the GPL around our code, and lock us out in the same way that these supposed companies would lock us out. Just like the Linux community, we have many companies giving us code back, all the time. But once the code is GPL'd, we cannot get it back
^Theo de Raadt, [http://undeadly.org/cgi?action=article&sid=20070901041657](http://undeadly.org/cgi?action=article&sid=20070901041657)

---

### Post by raronson on 2009-07-21
> **lykwydchykyn said:**
> Seems that your original post is asking if the cathedral is better than the bazaar.  I guess I'm sold on the bazaar.  

I don't see all the diversity as waste or reinventing the wheel.  It's like natural selection, or the free market, or democracy.  It's slow, and inefficient; the majority don't survive.  But those that do survive are stronger and better.

We could have said ten years ago "let's all get behind red hat", but instead we had a lot of people that said "I can do better than red hat".  Most of them didn't, but the ideas they came up with (e.g., liveCD installation) lived beyond the distros and now Ubuntu has eclipsed red hat using many of those ideas.

What a shame if we now said "let's all get behind ubuntu and forget everyone else".  Because the distro that eventually replaces Ubuntu is likely to be more awesome than any Ubuntu we could create that way.

Thanks for that.  I've also likened the process to biological evolution with the most prominent and lasting changes coming from the bazaar and incorporated into the genome.  It's just that evolution is a blind process that sometimes works too slowly.

For example, evolution has given us the ability to contemplate its own process, and to a limited degree, take control of the wheel.  This happens all the time with artificial selection (plants, dog breeds, etc.).

Nature abhors instability and works toward the replication of stable structures--though it doesn't always go about it in an optimal way.  Consciousness and creative intelligence exist to arrive at better solutions.

---

### Post by swoll1980 on 2009-07-21
> **&#20170 said:**
> [B]If you want Gnome on PC-BSD just install the pbiDIR for Gnome:

The problem with that is the fact that you can't uninstall KDE, or can you? I was under the impression that KDE is tied to the system.

---

### Post by Cracauer on 2009-07-21
> **swoll1980 said:**
> The problem with that is the fact that you can't uninstall KDE, or can you? I was under the impression that KDE is tied to the system.

I think the package installer is a KDE program. It might not react favorable on removing the KDE libs.

Why would you want to actively remove it? You can have a GNOME desktop and call a KDE program.  Myself, I used a GNOME desktop with fvwm2 for a while and my pdf viewer is kpdf. No problems whatsoever.

%%

Anyway...

Everybody has their own views on why Linux hit it big and *BSD didn't.

Today I have to say that although FreeBSD is still the weapon of choice for me, the port system is a total pain. `portupgrade -a` on my notebook takes about a week, with all the failed things that hold up every other port further down the dependency tree. Debian/Ubuntu's binary packages are a little more convenient here.

I still love the ports system because I can have local modifications to applications very easily, not to mention modifications of the base system.

When it come to kernel subsystems, pseudo-devices in particular, FreeBSD makes so many things so much easier. All that mess with half-integrated layers of things in Linux doesn't compare to how easy e.g. GEOM makes things. And you always have the right userland control utilities for pseudo-devices with your kernel. This particular aspect in Linux is simply insane. The kernel should have a /usr/src/linux/userland section that comes with the right sources for the controls present in the same kernel package.

I could go on and on about things that take 2 minutes to set up for the first time (that means starting with no clue and googleing) in FreeBSD and can take hours in Linux thanks to messy subsystems, and the documentation either being absent, splattered everywhere or impossible to find because long outdated HOWTOs block access to it from a search engine.

---

### Post by HappinessNow on 2009-07-21
> **swoll1980 said:**
> The problem with that is the fact that you can't uninstall KDE, or can you? I was under the impression that KDE is tied to the system.

I am pretty sure KDE is not tied to the system but Fluxbox may be.

> PCBSD 7.1.1 - Changelog (07-06-09)
--------------------------
[COLOR=Black]*** Improved the default fluxbox configuration**[/COLOR] - [3793]("http://trac.pcbsd.org/changeset/3793")  - [3794]("http://trac.pcbsd.org/changeset/3794")  - [3798]("http://trac.pcbsd.org/changeset/3798")  - [3808]("http://trac.pcbsd.org/changeset/3808")  - [3809]("http://trac.pcbsd.org/changeset/3809")[URL="http://trac.pcbsd.org/changeset/3809"]
[/URL][http://www.pcbsd.org/content/view/126/5/](http://www.pcbsd.org/content/view/126/5/)

---

### Post by yabbadabbadont on 2009-07-21
I seriously doubt that *any* window manager/DE is required at all.  pkg_add and ports are both command line utilities and are all you need to manage the packages on your system.  Indeed, the BSDs are often used only as headless servers with no X installed at all.

---

### Post by HappinessNow on 2009-07-21
> **yabbadabbadont said:**
> I seriously doubt that *any* window manager/DE is required at all.  pkg_add and ports are both command line utilities and are all you need to manage the packages on your system.  Indeed, the BSDs are often used only as headless servers with no X installed at all.

Good point. :P

---

### Post by Cracauer on 2009-07-21
> **yabbadabbadont said:**
> I seriously doubt that *any* window manager/DE is required at all.  pkg_add and ports are both command line utilities and are all you need to manage the packages on your system.  Indeed, the BSDs are often used only as headless servers with no X installed at all.

We were talking about PC-BSD, which has a graphical package/application installer. The KDE libs (or whatever) might be required for this.

FreeBSD doesn't need anything X11 for any of it's ports system, in fact I know a considerable number of FreeBSD machine that do not have libX11.so

---

### Post by HappinessNow on 2009-07-21
> **Cracauer said:**
> We were talking about PC-BSD, which has a graphical package/application installer. The KDE libs (or whatever) might be required for this.

FreeBSD doesn't need anything X11 for any of it's ports system, in fact I know a considerable number of FreeBSD machine that do not have libX11.so

It would be good to find out from the PC-BSD devs. directly on this subject.

---

### Post by Cracauer on 2009-07-21
> **&#20170 said:**
> It would be good to find out from the PC-BSD devs. directly on this subject.

How does it matter?

Why would the presence of KDE or whatever the installer uses be a problem for you if you don't have to use it as your desktop?

Granted, if you don't want to use X11 then PC-BSD won't work for you, but again, where is the question to ask?

---

### Post by swoll1980 on 2009-07-21
> **Cracauer said:**
> How does it matter?

Why would the presence of KDE or whatever the installer uses be a problem for you if you don't have to use it as your desktop?

Granted, if you don't want to use X11 then PC-BSD won't work for you, but again, where is the question to ask?

I use all Gnome apps, or all KDE. I don't mix them. You end up loading whole libraries to run a couple apps. This may be ok with most people. I don't know, I just don't like doing it.

---

### Post by HappinessNow on 2009-07-21
> **swoll1980 said:**
> I use all Gnome apps, or all KDE. I don't mix them. You end up loading whole libraries to run a couple apps. This may be ok with most people. I don't know, I just don't like doing it.

It would seem like if your using Gnome it would dump the KDE aps? or you may have to initiate it?

---

### Post by swoll1980 on 2009-07-21
> **&#20170 said:**
> It would seem like if your using Gnome it would dump the KDE aps? or you may have to initiate it?

I'm sure there might be a way around it.

---

### Post by Cracauer on 2009-07-21
> **swoll1980 said:**
> I use all Gnome apps, or all KDE. I don't mix them. You end up loading whole libraries to run a couple apps. This may be ok with most people. I don't know, I just don't like doing it.

Er? 

I was talking about on disk. Why would you insist on uninstalling KDE?

---

### Post by linuxguymarshall on 2009-07-21
> **SunnyRabbiera said:**
> Well the major reason why open source developers avoided BSD is because of the old BSD license.

I realise I am one of the few with this view but I personally prefer less restrictive licenses like the BSD license (Personally I go for the zlib/libPNG license) but thats just my thought.

---

### Post by KinKiac on 2009-07-21
> **raronson said:**
> Yeah, Psych--this is essentially what I was asking:  would things be further along if people stopped reinventing the wheel, and just agreed on a few standards?  As a technofuturist, I have this hypothesis that computing will be at the heart of a handful of technologies that will change the world for the better.  In order for this to happen, software needs to be emancipated from the confines of the operating system as we know it.

We get there sooner by agreeing upon a shared OS base from which to spring.  The OS will be just another protocol in a larger meta-system, and as standard as TCP/IP is today.

My real gripe with Microsoft is that they've held back legitimate computing by generations through the reinvention of a product that doesn't need to be sold anymore--the operating system.  They should accept the reality of Linux and get back to writing software; which they could still sell and make money from.

Yeah but MS is still making billions off of bundling their OS with new PC 's and the licensing that comes with that.  Not to mention what they make licensing it fro businesses.  There is no way in my mind they would stop selling their OS until it lost all its market share, which could take a very long time.  As long as they are still making money off of it, they wont change.

---

### Post by raronson on 2009-07-22
That's very true.  Microsoft owns the default install.  However, PC sales are at an all time low ([http://www.lubbockonline.com/stories/071509/bus_463863326.shtml](http://www.lubbockonline.com/stories/071509/bus_463863326.shtml), the first hit from Google on the topic).  The advent of the web caused a 20 year boom in sales, because not everyone owned computers.  That's obviously changed now and people are hesitant to replace their 5 and even 10 year old machines because they still do the very thing that they were purchased for: browse the web and use email.

We're also dealing with a slightly smarter consumer now.  Before you have something, you're not sure what the limitations of the product are, so FUD (fear, uncertainty, and doubt) can be used as leverage against the consumer.  But now people are more competent and knowledgeable.  I almost laughed myself to tears when Microsoft came out with Vista and just expected everyone to fall in line.  It's as though they were saying, "C'mon guys, new OS!  It's really really good!!  You can't be without it!!!  <clap> <clap> Let's go!!!!"  But people have played this game before.  They've finally caught on that there's nothing new, or at least nothing revolutionary that demands their hard-earned money.  And most damaging for them is the business sector who's been similarly minded.

So even though they win the default install, more and more, it will be less to brag about it.

---

### Post by thisllub on 2009-07-22
> **clonne4crw said:**
> It's not only FreeBSD that's been left out in the cold to die. Solaris is very underdeveloped for the typical user enviroment.

I think that Solaris is a sleeper that could easily awake in a big way.
They still have some problems integrating Gnome( e.g. Network-manager basically overwrites your networking config every time the wireless network drops out ) but on this laptop with ZFS it is more solid than any Linux I have used. 
Firefox crashes less frequently and I can only put that down to better memory management. Once Linux fills up and starts swapping in a big way you might as well cycle the power. Solaris seems to handle this much more gracefully.

If and it might as well be "when" enough user apps are browser or client based like OpenERP businesses will finally drop MS.
I suspect that if I were a solution provider it would be easier for me to sell a Solaris network than a Linux one.
I think Solaris will push BSD aside for many.

The big thing  in favour of Linux is change. 
Users love new features, sys admins hate them. The ports collection is pretty up to date.
One of the attractions of Ubuntu is the new look and feel that has accompanied revisions. 
Compare this with Arch which is the most up to date of all operating systems and distros. Theming is up to the user.

---

### Post by raronson on 2009-07-22
Some good points regarding OpenSolaris, but it brings up a point I made earlier about technical superiority versus mindshare/marketshare.

When even Sun Microsystems uses Linux in its latest workstation offerings ([http://www.sun.com/desktop/index.jsp](http://www.sun.com/desktop/index.jsp)), it's a little hard to see OpenSolaris making big inroads.  At the end of the day, "Linux" is the only alternative to the commercial OS's, and improvements and features from other open systems (like ZFS and Dtrace), will either have to find their way into the 'default' mix, or be recoded as a work-a-like in Linux.

---

### Post by moster on 2009-07-24
Truth is, SUN release Solaris "free" because they do not want to see it dead. And only thing that is actually good on it, is ZFS. When linux get stable BTRFS, every need for Solaris will be gone.
I do not know what SUN expected. To everybody leave linux start working on their SuperOS? 4 years pass and nothing really happend. Linux has its momentum and I cannot think of anything right now that can change it.

Microsoft hit wall with win7. They do not know where to run anymore and linux is slowly catching up. I personally think win7 is best OS that microsoft can create, and it is really good but it is not worth all that money if you have free alternative.

Others, they just do not have manpower and charisma to get anywhere. Lunux last frontier is desktop computing. That is only thing that it needs to finally explode. Today OS need more people behind it then before. That is why only microsoft with their army of programers that counts up to 100 000 and linux that has almost fanatic followers that is every day more and more and I know, they will never give up. Dark ages are behind. If computing can have its own God, his name is certainly Linux. Question is, are you believer or not :)

BeOS prove that "best" alone is not good enough. OS must have something else. It was certainly one of best desktop OS ever. That is why all those "one man show" OSs will simply fail.

edit:
sorry for little off topic, I cannot sleep :)

---

### Post by raronson on 2009-07-24
> **moster said:**
> 

BeOS prove that "best" alone is not good enough. OS must have something else. It was certainly one of best desktop OS ever. That is why all those "one man show" OSs will simply fail.

edit:
sorry for little off topic, I cannot sleep :)

That's absolutely right.  Technical superiority gets you nowhere when there's not sufficient mindshare.  There are a lot of people still frosty about BeOS not making it as far as Linux.  In fact, I think my next thread will be: BeOS, It's a Shame...

No, no.  I wouldn't dare try this again :)

---

### Post by moster on 2009-07-24
@raronson
Haiku, open source BeOS will be done in few years, wait, relax :D

To continue little on this interesting subject. I was watching SkyOS for a while. You believe it or not but that whole OS from scratch came from only one man. And it was not freakin no-GUI OS. Now, man has to be nearly genius to make something like that from scratch alone. At last, it was killed just while ago because no hardware support. How he not see it before that his little OS was doomed at start. It was so obvius. Many years of his effort is gone like piss in the river. He can open it now like solaris, but it is gone already. Just another failed windows killer added to the list.

Why I am telling all this...  Collaborate effort is the key, but how to convince such brilliant people to contribute to linux where their hard work will be more visible and not to isolate themselves where they will be, if nothing else squashed by microsoft.

I am willing to pay to see, just from curiosity, how will computing look like 15 years from now :D Fingers crossed, and with power of mass broadband internet, linux at 15% :D

---

### Post by raronson on 2009-07-24
> **moster said:**
> @raronson
Haiku, open source BeOS will be done in few years, wait, relax :D

To continue little on this interesting subject. I was watching SkyOS for a while. You believe it or not but that whole OS from scratch came from only one man. And it was not freakin no-GUI OS. Now, man has to be nearly genius to make something like that from scratch alone. At last, it was killed just while ago because no hardware support. How he not see it before that his little OS was doomed at start. It was so obvius. Many years of his effort is gone like piss in the river. He can open it now like solaris, but it is gone already. Just another failed windows killer added to the list.

Why I am telling all this...  Collaborate effort is the key, but how to convince such brilliant people to contribute to linux where their hard work will be more visible and not to isolate themselves where they will be, if nothing else squashed by microsoft.

I am willing to pay to see, just from curiosity, how will computing look like 15 years from now :D Fingers crossed, and with power of mass broadband internet, linux at 15% :D

Yes, the very thing indeed that I was talking about.  It's a shame about SkyOS too, but here's why:  it wasn't initially an open project.  Now I won't pretend to know his mind about why--maybe he thought he could sell it?  Or maybe it was just his hobby OS that he wanted singular control over.  Robert Szeleney did an amazing job, and I've been watching it here and there for 10 years become not only a good looking OS, but a good OS in general.  What finally broke him was manpower and the exponential speed of developing hardware not easily tested by a small group.  Last I recall, he either has, or plans to open it up.  Though I bet he was hoping some handheld startup would snatch it up.  Can't say I blame him--he did devote a decade of a time to its developement.  Like you though, I'm just wondering what he could have contributed to GNU/Linux...

He's certainly welcome to now, and I hope he does :)

---

### Post by zdude on 2009-07-25
When I decided to switch my server software from windows in 2003, I used FreeBSD and then Xandros but eventually settled on Warty 4.10 - mostly due to all the hardware working. After using it for my server I then moved my desktop to 5.10 Ubuntu and have stuck with it through the upgrades (currently at 8.10)  although I am now also using OSX86 more and more in dual boot on my PC (I also own some Macs due to my wife's preferences)! I rarely if ever use windows and I don't see that changing and my main server now has 12TB of storage and is now s running 8.04 quite flawlessly. I am wanting to use a more robust FS and I am looking hard at ZFS and BTRFS but it seems to be coming along a lot slower than I thought it would. Not sure about the next turn in the road but I am now testing stormOS and it looks promising but I still like Ubuntu and want to stick with it but it now seems slower than some of the OSes I am now testing.

---

