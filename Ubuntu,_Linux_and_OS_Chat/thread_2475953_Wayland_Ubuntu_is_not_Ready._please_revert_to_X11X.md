---
title: "Wayland Ubuntu is not Ready. please revert to X11/Xorg..."
date: 2022-06-13
forum: Ubuntu, Linux and OS Chat
---

### Post by r3vd3l0x3 on 2022-06-13
Introduction:

   At First glance Wayland is great, i would say that. but. it's not ready for beta testing while it's on Alpha state. Ubuntu 18.0.4 was the best and was the competitively stable publish ubuntu has provided. It runs well on low-end devices that are 10-15 years old, and still impresses me. the window manager uses X11/Xserver/Xorg. that use the good old client-server request. the latency is somewhat ok back then. and it got worse in ubuntu 22.04. POP os runs X11 fine but it runs system76. arch and other variants performance drops relatively lower than the ubuntu 18.04 X11. theoretically Wayland should be faster. well that's not the case. thermally wayland runs horrible. software? C libxserver doesn't work and only shows the mouse.(Colorpicker find it on github.) well it's light on resources and responds very fast but there's always *FRAME DROPS*. 

The Problem

    To Determine Valid use-case scenario. firstly we have to determine what are the apps that affects this thread; and also the workarounds that doesn't work for some reason that i don't know. i wont post thread without doing Homework hence here what i came up so far.

    1. The Screen Recording Delimma (Every Body hates OBS because not everyone  have the money to RTX3080 for their laptops.)
    2. Ubuntu on Xorg have this Black screen and slow Animations. plus when it loads you'll only see the ubuntu logo weirdly displayed on your screen.
    2.a. Workaround 1: xorg.conf (Doesn't work)
    2.b. Workaround 2: /etc/environment (Doesn't work)
    2.c. Workaround 3: [COLOR=#E6DB74][FONT=Consolas]sudo[/FONT][/COLOR][COLOR=#E6DB74][FONT=Consolas]apt[/FONT][/COLOR][COLOR=#E6DB74][FONT=Consolas]install[/FONT][/COLOR][COLOR=#F8F8F2][FONT=Consolas] xubuntu-desktop[/FONT][/COLOR] (Works But i want GNOME as my DM.)
    3. C xorg lib doesn't work
    4. Where the **** is the Xwayland? to solve these issues.
    5. Application Side faults for not making wayland support Applications.
    6. Lack of Research and Testing.
    7. Funding of course. everyone needs to eat to work grave hours.

Hypothesis

    I sense that there are many threads posting somewhat the same stuff i do but that doesn't also means that those who are not participating are not struggling. My hypothesis are that you keep wayland in the ISO for further testing and waiting for the apps to move towards wayland. for the moment revert the next UPDATED ISO to default X11.

---

### Post by coffeecat on 2022-06-13
> **r3vd3l0x3 said:**
> My hypothesis are that you keep wayland in the ISO for further testing 

Us?

Ubuntuforums is a peer-to-peer volunteer forum consisting of end-users such as yourself, forum staff included. We are not employed by Canonical. This is not the place to communicate ideas and feedback to the developers. For the same reason, the results of your "petition" might be interesting, but will not achieve anything.

Welcome to the forum!

---

### Post by zebra2 on 2022-06-13
@OP, 
Thanks for your perspective.  I use Ubuntu/Gnome/Wayland 22.04 and didn't even know that I had a problem so I'm pleased to know how bad off I am. It beats going through life blissfully satisfied.

---

### Post by grahammechanical on 2022-06-13
I think a bit of history will give us some perspective on this subject.

Some years ago Canonical, the sponsor of Ubuntu, was heavily criticised for not supporting the development of Wayland display compositors. Canonical wanted to develop it own display server called Mir as well as its own desktop environment called Unity. After awhile Canonical dropped the intention of using Mir and Unity and accepted everything the Gnome developers had to offer. This included the Gnome Wayland compositor which is now used in Ubuntu on Wayland. Which incidently is the default for recent versions of Ubuntu with a login option to use Ubuntu on X-Server.

Keep in mind that the X Windowing System is now 38 years old and there are potential security vulnerabilities that cannot be addressed by rewriting the code. Please read the FAQ provided by the Wayland people.

[https://wayland.freedesktop.org/faq.html](https://wayland.freedesktop.org/faq.html)

In switching to a Wayland compositor Ubuntu is only keeping pace with the present development path of Linux distributions. As it does with many other developments

P.S. Remember, Ubuntu is not a democracy.  If you want a say in Ubuntu development then become a Ubuntu developer and earn the right to have an opinion.

Regards

---

### Post by poorguy on 2022-06-13
I'm using Wayland on ***22.04 ***and*** 20.04 ***and have never had any issues and my computers are 2007 and 2013 desktops.

Graphics cards ***ASUS* *EN8400GS* **and the other is an ***Intel 4 Series Integrated Graphics ******Q45/Q43* **both work good using Wayland.

---

### Post by QIII on 2022-06-13
The Wayland developers got off on the wrong foot with their "we know what you should and should not do with your desktop, so keep your mouths shut" attitude.  That was my gravest misgiving with Wayland.

 They have since come to their senses.  However, I think that time kept them from from taking care of some basic userland difficulties people were encountering and they have had to scramble to keep up.  Unfortunately, there are still hiccups and burps.  But at least now they aren't saying "Neener, neener, no fix coming because you should not be doing that in a GUI anyway and should be using the terminal."

---

### Post by Perfect Storm on 2022-06-14
I have seen people with couple of problems with Wayland on different boards. I support the idea of Wayland, but I'll give it a couple of more years to make it standard.

---

### Post by web-user on 2022-06-18
Well, seems like Wayland is still immature while Xorg is stable. This is the reason why everyone still use Xorg. And when everyone uses Xorg, Wayland community stays small &#8212; like a chicken and egg problem.

---

### Post by VMC on 2022-06-18
I have had no issues using Wayland on Ubuntu or any other Gnome OS. KDE is another story.

---

### Post by agentl074 on 2022-06-18
Wayland is WAY better for newer GPUs.

---

### Post by kurt18947 on 2022-06-18
The GPU in my desktop machine is not new - Radeon HD7450 - but it had the occasional glitch in 20.04 xorg and doesn't seem to have those glitches in Wayland. The MoBo is AMD B450 which may enter into it. It's certainly easy enough to switch from one to the other with a restart.

---

### Post by TheFu on 2022-06-19
In Wayland, how to you setup automation like text screen captures inside specific programs?  I use cnee for that today, but it is tied to X/Windows and doesn't work under Wayland.  

Lots of excellent capture tools don't work with Wayland and the Gnome Screen Capture tool doesn't provide the control over options that the X11 solutions do.

---

### Post by grahammechanical on 2022-06-19
It is a tradition in Open Source Software to release code before it is polished and ready. The user becomes the tester. It can be many months before new software reaches even version 1.0. This is the way things are done in Free and Open Source Software. The alternative is to have no alternative to Microsoft and Apple products.

Regards

---

### Post by TheFu on 2022-06-19
> **grahammechanical said:**
> It is a tradition in Open Source Software to release code before it is polished and ready. The user becomes the tester. It can be many months before new software reaches even version 1.0. This is the way things are done in Free and Open Source Software. The alternative is to have no alternative to Microsoft and Apple products.

Regards

True.  Wayland was release about 7 yrs ago.  In 2017, Canonical made Wayland the default display server, which failed with similar issues that are still complaints today.  I suppose many things have been addressed in the last 5 yrs.  Things which are probably important even to me, but that I'll never try because the mouse and keyboard automation just aren't there yet.

There are a few more screen capture tools now than in 2017, which is good.  And since most people don't seem to use the things that are critical to a subset of users like me, I'm not against Wayland being a reasonable default in 22.04.  

But it still lacks some critical features needed by many users.  How many is unknown.  The same can be said about snap/flatpak packages, systemd (especially timed and resolved and mountd), netplan, pulseaudio.  IMHO, Wayland makes more sense than snap packages.  This isn't to say that there aren't brilliant people working on all those programs and they are doing some amazing work.  I think the design of snaps is broken, but the others can all be fixed, probably.  I stopped ripping out netplan and pulseaudio a few years ago.  I don't know how to rip out systemd-mountd, or I would.  The snap subsystem is removed on most of my systems, but I really like lxd, so 2 systems have snap support here.  
The other listed subsystems get removed. They break more than I'm willing to put up with and there are well proven alternatives.

Of course, if your use cases don't see any issues, you'll likely think things are great.  Anyone with an nvidia GPU, knows that Wayland isn't ready - or more likely that nvidia drivers aren't ready, but if you have a $500 GPU, guess which is more important?  

Remember when LTS releases mostly worked and didn't introduce alpha-code?  Perhaps it is just my rose-colored glasses, but the last time I remember not having any surprises was 10.04.  That was a beautiful OS. Everything worked as expected.  I understand that new users probably have a completely different view, since many things were manually controlled via text config files in 10.04, but if you knew what Unix configs were, then 10.04 just worked.

Canonical has taken up the "Power of the Default" in all their releases, beginning around 11.04 (Unity DE), even when some of those defaults just aren't ready.  I expect non-LTS releases to try new things, push the envelop, and for things to break.  That's expected and good for an OS distro to keep moving forward.  An LTS shouldn't do that, unless they've changed the definition.  If I wanted an unstable, broken system, due to updates once a month, I'd use something like Arch.

There's a reason I want LTS releases and only LTS releases.

Sorry for a bit of a rant.

---

### Post by r3vd3l0x3 on 2022-06-20
We all know the risk and the benefits. Perhaps it's the documentation of how to setup X11/Ubuntu on XORG that has these gray lines that we as testers and user don't understand.

the concern here is make Ubuntu Work on older PC like 2010 old PC.(Because one time i tried installing Groovy Gorilla on Intel Pentium 4 2.20GHZ 2x, 2GB Ram(Upgraded to 4GB Because it's 2020).) 

It showed me a broken black screen.

Application side things are really hard to argue and has a lot of bugs and glitches to fix. that's the Deep Black stuff...

Here are the app and commands that are not usable/sometimes it does. idk that kind of weird... (Ubuntu 22.04 "LTS" Wayland)
> 1. xmodmap (Obviously its a xwayland bug)
> 2. include <X11/Xlib.h> (Totally Not Working)
> 3. simplescreenrecorder (Bugged, records a black screen)
> 4. OBS (My specs are low said by 2020 (Intel Celeron N3060, 4GB ram.))
> 5. since no.2 is Bugged or not totally working. C applications doesn't work.
> 6. I dont want to cover gaming stuff since wayland is designed to be compatible with Xwine and Xproton libraries. thats why new graphics card works properly as they should.
> 7. Maybe i'm broke and i just don't realize it.

Edited:

Also for some reason Jammy Jellyfish doesn't detect my simcard.
but it works fine on my raspberry pi and my pentium 4. (Module Model: Huawei E1552)
I already researched pppd and mmcli/nmcli workaround.

the last time i use this module was Ubuntu Bionic Beaver 18.04 LTS.

---

### Post by r3vd3l0x3 on 2022-06-20
> **coffeecat said:**
> Us?

Ubuntu forums is a peer-to-peer volunteer forum consisting of end-users such as yourself, forum staff included. We are not employed by Canonical. This is not the place to communicate ideas and feedback to the developers. For the same reason, the results of your "petition" might be interesting, but will not achieve anything.

Welcome to the forum!


Thank you,

I don't plan to give wayland a bad image which definitely is happening here in this forum.
yes, itself wont have impact, but it can provide solid source for statistical reference for the media. and researchers such as myself.

I do understand that you don't have the ability to change or modify the ubuntu source as i state to demand in my thread. *ehhmm*

My aim is to give users, testers and developers that contribute to this thread. Awareness of what are missing and needed some attention.
I envision the users to empower themselves to contribute, research, and document better choices that is favorable to themselves, testers, and freelance developers.

Regards.

---

### Post by yaminb on 2022-06-20
Maybe I'm missing something, but I don't see what the issue is.
It's not like Xorg is not available.

I personally think Ubuntu is handling this transition quite nicely. I have a Nvidia GPU which had numerous problems with Wayland. 
They kept it disabled by default for a long time. It was actually a problem to enable it to even try it out.
Then I had the option to enable it, but it would have problems coming out of sleep.
Now it behaves okay as far as I can tell.

In terms of handling transitions, they've done a pretty good job. 
If you're having problems with Wayland as I did, I just continue to use Xorg.

---

### Post by kurt18947 on 2022-06-20
At least we have a choice to choose an older proven solution if that seems the best way forward. The only app I've used that works in X.org and not in Wayland is Shutter. I've found Libre Office Draw adequate to the rare occasion I wish to annotate an image.

---

