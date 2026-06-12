---
title: "My experience with (k)ubuntu"
date: 2009-10-20
forum: Testimonials &amp; Experiences
---

### Post by g.a. on 2009-10-20
I would like to share with you my experience with the last distributions of (k)ubuntu.

In spring 2009 I installed kubuntu 8.10 on my new laptop, a Dell Precision M2400. It was fine and I had the bad idea to install the 9.04 version.

I started experiencing a lot of troubles concerning: audio, webcam, wifi, freezing, kernel panic and few minor issues with plasma. I wasted tons of time trying to solved all these problems and partially achieved it.

I then decided to move to ubuntu and made a

```
sudo aptitude install gnome-desktop

```

that solved all the problems but the kernel panic.

Again, a lot of time wasted trying to understand the problem when I finally installed from stretch ubuntu 9.04.

It is now two weeks that I'm finally (back) an happy Linux user. No serious problem and no more kernel panic.

With the kubuntu 9.04 release I really started thinking that, with all these bugs and special effects, it seemed more a microsoft-like distribution than a Linux one.

Best,
g.

---

### Post by SuperSonic4 on 2009-10-20
Kubuntu isn't that bad but each to their own. Perhaps it didn't just play nice on your machine

---

### Post by iTheBadGuy on 2009-10-20
i installed Kubuntu 9.04 like 2-3 days ago, but i was a Ubuntu user for about 4 months. I removed Kubuntu the same day.

I didn't have any problems like the one you mentioned.. But i did have one, not the OS's fault i guess..

My friend came over my house one day and saw me using Ubuntu, his first words were "damn, what's that? o.O, looks awesome!". After installing Kubuntu i thought "well, this kinda looks to much like Vista/7". he latter came over after i had Kubuntu installed and said "Oh, so no more Ubuntu?, thought you didn't want to use Vista anymore?."

I just think it looks to much like the thing i've been trying ot get away from all this time - Windows. But other than that, i thought it was pretty solid.. i only used it for one day tho :P

---

### Post by gunksta on 2009-10-20
Kubuntu 9.04 was really a transition release for Kubuntu. Distributions like Kubuntu made the difficult choice to jump onto the KDE 4 bandwagon early in the process. This decision had pros and cons.

Pros - Lots of eyes meant lots of bugs were identified and stomped.
Cons - Lots of eyes had to see these bugs.

I'm been using Kubuntu 9.10 at home and at work (since the BETA) and I have to admit that this is one of the nicest looking OS's I have ever used. Most of the bugs/quirks from 9.04 are gone, things look incredible, and it uses fewer system resources (Plasma was a pig in 9.04). The Vista-esque color theme has been replaced by a very smooth light gray theme that I didn't like at first (a bit too Apple-ish) but it has grown on me and I really like it now.

These days there are really only 4 GTK apps that I use and I couldn't see any reason to install Gnome. None of these apps depend on Gnome in any real way (beyond GTK, which is technically a separate project).

[LIST=1]
[*]FireFox - I may replace this with Chrome (also GTK based) if it continues to improve. I'd love to find a GOOD open-source web-browser based on QT/KDE. Maybe Arora or Rekonq?
[*]PSPP (the GUI is in GTK)
[*]The Gimp - home only.
[*]Vim - GVim is a GTK based GUI, but I usually just use the console version.
[/LIST]
Over-all I like the KDE apps better. They just tend to be more powerful. F-Spot and Digikam are both good tools for organizing your photos, but I almost feel guilty comparing them. F-Spot is probably adequate for many people, but Digikam is basically a professional level tool, with tricks added on to it.

Either way, use Linux. I'll forgive you for using Gnome but I couldn't forgive you for using Windows. :P

---

### Post by QIII on 2009-10-20
Ah, the beauty of Ubuntu.

You are not stuck with the vanilla wrapper that comes out of the box, but you can make it look as different from Windows as you choose.

Gnome, KDE, Xfce, etc. are in themselves choices.  But each can be highly customized from there.

Think it looks too much like Windows?

Change it.  That's half the fun.

---

### Post by solwic on 2009-10-20
> **QIII said:**
> Think it looks too much like Windows?

Change it.  That's half the fun.

+1.  That's one of the things I love the most about Ubuntu, and Linux in general.  Don't like it?  Change it. Simple as that.  

:cool:

---

### Post by g.a. on 2009-10-21
thanks to all of you for your replies.

first of all let me reinforce that, after a couple of years of dual boot windows/linux, since last year my new laptop only has linux and this choice will not change in the short term.

i do not want to repeat here the tons of reasons why i do prefer to use linux instead of windows.

IMHO, the only weak point of these discussions is that we are talking about graphics/feelings/themes etc. and not about functionality.

the price to pay to have plasma out (which is wonderful, i agree) is to loose functionality? (i will not forget the dozens of posts read to understand why my audio was not working under kubuntu 9.04).

best,
g.

---

### Post by gunksta on 2009-10-21
> **g.a. said:**
> 
 IMHO, the only weak point of these discussions is that we are talking about graphics/feelings/themes etc. and not about functionality.


Well, since you asked . . . . 

I think the improvements in KDE 4 go far beyond graphics/feelings/themes and in many ways I expect Gnome 3 to be a similar, although hopefully less painful transition/improvement.

KDE 4 was a complete over-haul of the underlying KDE libraries and systems  (QT 3 -> Qt 4, new libraries, etc.). The Gnome developers are doing something similar as they prep for Gnome 3, although it appears that their restructuring is less invasive/thorough. KDE 4 introduces a number of new sub-systems which users do not directly interact with but these systems are fundamentally important to KDE 4. Google for the "Pillars of KDE" to see  what I'm talking about. These include funny sounding things like Phonon and Akonadi. 

Phonon is a KDE sound system which makes it possible to use multiple sound-systems, depending on the operating system or user need. This makes it much easier to port KDE applications to Windows and Mac. Eventually, you will be able to use KDE on all three platforms. Akonadi is PIM system. It will be a system for interacting with PIM data, either stored locally or remotely. More importantly, it will provide a common API to access this data, making it possible for multiple applications to interact with the same data and having it be synced perfectly. For example, it would be possible for KMail and Evolution (if Evolution is ported to use Akonadi) to share one or more address books. But, Akonadi can do more and is really a super-set of what Canonical appears to be interested in doing with their use of the CouchDB, but Akonadi has the advantage that it is built into the system intentionally and is not tacked on for a single service (UbuntuOne).

In the 3.x days, many users criticized KDE for not paying close attention to implementing a common set of Human Interface Guidelines (HIG). The implementation/enforcement of the HIG in Gnome 2.x has been a real success and the KDE developers recognized this. When developing KDE 4, there was a conscious effort to use to develop and implement a KDE HIG AND to work with experts in human interface design to make KDE 4 easier to use. Of course, some of these changes have taken time to be seen, and there are several application that need some serious TLC. In my opinion the KDE Control Center is still a bit of a mess and Kontact could use some TLC but the progress is undeniable. Applications like Gwenview are much easier to use in KDE 4.x than they were in 3.x. As these applications have success, it will encourage more developers to adhere to this philosophy, just like it did in Gnome.

> **g.a. said:**
> 
the price to pay to have plasma out (which is wonderful, i agree) is to loose functionality? (i will not forget the dozens of posts read to understand why my audio was not working under kubuntu 9.04).


Audio was a problem in 9.04, although that had nothing to do with Plasma and was a problem for many Gnome users as well. That had to do with the sound-system and the fact that Canonical shipped a sound-server which some have argued was not ready for prime-time. It has worked well for me, so I won't complain but I do understand the frustration of others who had things break. In fact, this was a problem with KDE 4.0 in general. It pushed many systems farther than they were really prepared for. It revealed problems in the XServer (aRGB problems), graphics drivers (AAHH!) and the sound system that other desktop shells had not revealed because they didn't push as hard. These weren't bugs that KDE could fix, but they had a huge impact on the user experience.

And, you're right. When KDE 4 was released, Plasma only provided a sub-set of the functionality found in the KDE 3.x desktop shell. There's no question about that. It was a radically new system and wasn't fully mature. KDE developers did warn the distros that KDE 4.0 wasn't a prime-time system, but many distros shipped it anyway. This was a problem for many, myself included, but I REALLY appreciate how quickly it has matured since it was released. 

In this respect, I think the Gnome developers have approached Gnome 3 in a tactically better way. Because their changes to the underlying libraries are not as dramatic, they are able to release a preview of the new Gnome shell with the current Gnome release. This lets adventurous users test out the new toys and gets more developers involved, but doesn't force users to use a system that is by all accounts, not complete. +1 for the Gnome developers. It will be interesting to compare the two desktops after Gnome 3 has been out for a year or so and has really matured. I think we will see some real innovation on the Linux Desktop from both camps.

And while the transition was painful, Plasma is now really coming into it's own. I'm not going to write a book on why plasma is cool as #$%^&* but a little research might change your tune. Go and read some of Aaron Seigo's blog entries. Plasma is basically the result of his vision for a desktop shell and he has some interesting things to say about it. While the plasma of KDE 4.0 was a joke, the Plasma of KDE 4.3 is very functional. KDE 3.x seems like a toy in comparison. It is just that easy to work with/use. Modifying the desktop and shell are so much easier and visual in KDE 4.3. And, like I said, while Plasma is cool as beans, it's not the only thing that got revamped for the 4.x series.

KDE 4.4's plasma will also be really neat. Plans include combining virtual desktops with specific task functions will make it much easier to leverage the flexibility of this environment. And, we will see increased integration between the desktop shell and KDE native applications.

Amarok was the first application to do integrate plasma into itself and admittedly their 2.0 release . . . . sucked. But, the new releases do show how much Amarok has matured (features are back!) and how integrating an application with Plasma can have a nice impact on application design and flexibility. Because plasma widgets can share common data back-ends, KDE will become increasingly tight-knit. Widgets will reflect the state of applications and changes made in a widget, will be automatically reflected in the parent application. Of course, some of this was possible before but Plasma makes it easier, and I suspect that we will see more and more applications taking advantage of this. I would love to see a picture widget based on my digikam tags.

Ehh. I guess I should get back to work now.

---

### Post by g.a. on 2009-10-22
Dear gunksta,

thanks for your exhaustive reply.

My post was too short and technically wrong. I did not want to say, and I do not think at all, that functionality is out of the KDE project.

As you noticed, my impression is that its release has been too early and the software did need some further development.

My computer science skills are not deep but I'm not a newbie neither. When I installed Kubuntu I wasted a lot of time in making work stuff that should be considered established for a popular o.s. I'm strongly motivated in using Linux and I tried several alternative solutions, partially written above. I gave up with a kernel panic for which I really did not have additional ideas. I mean, ideas that could be solved in a decent amount of time considering that I use the laptop for work and I do not want to spent all the week end on it.

I installed a couple of distributions on an old laptops and finally installed Ubuntu on this one. 

Ubuntu is fine, I can work with it without significant problems.

The question is, how many users simply come back to Windows after having experienced a so large number of troubles as I did? 

Best,
g.

---

### Post by gunksta on 2009-10-22
> **g.a. said:**
> 
The question is, how many users simply come back to Windows after having experienced a so large number of troubles as I did? 


That's always the million dollar question. If you browse these (and other) forums, you'll find posts of people abandoning Linux for Windows for various reasons. Software glitches, lack of specific software, incompatibility, trolling, and many other reasons appear to contribute to this.

Windows gets off easy. Most people get the newest version of Windows when they buy a new computer. Obviously, before Dell, HP or anyone else sells someone a computer, they will test it first to make sure everything works as advertised. When you get this computer, the OS is installed and set-up. The drivers are installed and configured. If life kills Windows, you have a nice set of disks that will ghost the machine and reinstall everything, install/configure the drivers, etc. 

When you download a Linux CD, people expect it to work with x,y and z hardware -- just like Windows but it is much more complicated because Canonical can't test it against everyone's hardware before hand. When you really think about it, getting all of this to work is incredibly hard. It's remarkable that it works at all.

---

### Post by iTheBadGuy on 2010-01-05
I know this is somewhat "bumping" but I'd like to add that before I completely switched to Ubuntu, I downloaded and installed Ubuntu about 3 times. I formatted and re-installed because I was new to it, and new stuff tend to scare me :P.

In the end, I use Ubuntu as my day-to-day OS. It's been a while since my last boot into Windows, only when I can't do something in GIMP (usually because I don't know how) I turn to Photoshop in Windows. But only then would I even touch my Windows partition..

---

