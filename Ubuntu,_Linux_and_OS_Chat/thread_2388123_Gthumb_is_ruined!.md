---
title: "Gthumb is ruined!"
date: 2018-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by futz2 on 2018-03-28
What happened? I run Ubuntu 14.04 on my main box and have been happily using Gthumb there (I ran Gthumb for many, many years before that too). I just set up another box with 16.04 and installed Gthumb only to find that the idiots working on it have broken it so completely that it's unuseable. So sad...

Reminds me of the kind of stupidity that ruined Nautilus - I have to run Nemo now because Nautilus is useless. What is wrong with developers?! They take perfectly good programs and remove all the features and useability - just neuter them. Why?! Oh ya, another one that got wrecked was Disks - good useful program - then one day it didn't do anything anymore. I don't get it. 

Anyone doing a fork of Gthumb from the time when it still worked?

I have found [this link]("https://askubuntu.com/questions/789400/how-to-downgrade-gthumb-in-16-04") that explains how to downgrade to an older version. Guess I'll try that and see how it goes.

---

### Post by kerry_s on 2018-03-28
so the developers are wrong for trying to keep up with the ever changing pace of code? i'm all for living in the past, but tech moves forward.

gthumb? eog is standard
i have no issues with nautilus, what kinda special need you have.

as code changes, software is changed, old apps are dropped for something else, it's how things work.

developers work there butts off so you can have software, is it going to work for everyone, no! does it work for the majority, yes!
there's a sea of software, swim my friend, swim.

---

### Post by ajgreeny on 2018-03-29
I have some sympathy with futz2, but that is the way that many gnome applications have gone recently; look at nautilus as an example. It is not actually broken but just changes and the menus and missing icon actions can still be carried out once you have found the way around the new GUI

However in fairness to gnome and its moves recently, ie, since somewhere around 14.04 versions, it is the simplification of everything that causes this heartache to you; it is nothing to do with Ubuntu, other than the choice of gnome behind the standard Ubuntu version.

If you don't like that version have a look at something else, including another photo/image manager; there are plenty of them. I have not used it but many users of the "old" Ubuntu versions love Ubuntu Mate, which looks and acts very like gnome-2 used to.

---

### Post by mastablasta on 2018-03-29
from wiki: > [FONT=sans-serif]Version 3.0.0 is based on GTK version 3, and supports high quality SVG zoom[/FONT]

look slike an upgrade... 

Anyway there is many pic managers including the full-of-features DigiKam. But for viewing and light editing i find that nomacs works well. very similar to irfanview.

---

### Post by futz2 on 2018-03-29
> **futz2 said:**
> Reminds me of the kind of stupidity that ruined Nautilus - I have to run Nemo now because Nautilus is useless. What is wrong with developers?! They take perfectly good programs and remove all the features and useability - just neuter them. Why?! Oh ya, another one that got wrecked was Disks - good useful program - then one day it didn't do anything anymore. I don't get it.

Thought of another example of stupidity: The Amarok 1.4/2.0 debacle. Amarok 1.4 was a pretty good program. A few bugs - it wasn't perfect, but for people with massive music collections it was pretty much the only way to go.

Then 2.0 came along. It was garbage! Just another crappy small-collection player program. 

So 1.4 got forked and became Clementine. And it was good, but then it got super buggy. I seem to remember it finally getting somewhat better again - foggy memory. I still have it installed, but don't use it much anymore. I'm old and I work too much - don't have the time to listen to music as much these days.

---

### Post by futz2 on 2018-03-29
> **kerry_s said:**
> so the developers are wrong for trying to keep up with the ever changing pace of code? i'm all for living in the past, but tech moves forward.
Tech moving forward should not mean taking good working software and dumbing it down to uselessness.

For your amusement, here is a quote from someone  when Gthumb first got "ruined" back in (I think) 2010 - I totally agree with him. Gthumb did become useable again, though not as good as before. 
> **some guy-in-2010]To sum it up, it seems that gThumb has lost its powerful features to follow the mass of Mac-style, elegant, pretty, stupid 'apps' so many people seem to love.[/quote]

[quote=kerry_s said:**
> gthumb? eog is standard
EOG is fine for what it is, but it's just not capable of meeting my, or many other peoples', needs.

> i have no issues with nautilus, what kinda special need you have.
My computers have a file manager running 100% of the time they're turned on. I have a lot of storage, filled with a lot of files, and new stuff coming in constantly. I need to be able to quickly and effectively keep things organized. The old Nautilus was fine, but the new one is useless. Just yet another dumbed down program for noobs. Thus the Nemo fork - Nemo is everything the old Nautilus used to be and has even been improved somewhat.

> developers work there butts off so you can have software
Yes they do, and I am very grateful to them.

> there's a sea of software, swim my friend, swim.
I have tried all the image viewers. 99% are pretty little small-collection viewers - useless dumbed down things. Great if you have a few hundred or even a few thousand pics. But they just don't cut it when dealing with large collections, spread over multiple drives and multiple file servers. Gthumb did, but now it has become just yet another dumbed down small-collection viewer. In its current state it is useless to me. I could maybe live with a small-collection viewer if any were nice to use, but nothing even comes close to old Gthumb for comfy.

I'm going to take a look at the source and see if I can do anything with it. I'm not a desktop app programmer (was a little in the 80's, but things have changed drastically), but I do a fair bit of C and C-like language work (and many flavors of assembly language) with various microcontrollers, and have dabbled in Python, Ruby, Perl, and probably half a dozen other languages. Maybe I can get up to speed enough to fork the thing, even if it's just enough to offer a working Gthumb for people who loved it. Probably not - I have limited free time - too much work.

---

### Post by kerry_s on 2018-03-29
i think the reason for the dumbing down, is because a lot of apps are having to be rewritten to keep pace with new code.
if your a developer and you want to make it as simple as possible for future changes, your going to try & cut it down, less changes/fixes for future versions.
i see a very huge trend towards apps that only do 1 thing, but do it well.

have a look at elementary os if you have time, just run it live, there curated apps. if your looking for a app to just format a disk, they have that, it has only 3 choices & all it does is format the drive you select.
they have a growing stable of 1 shot apps, made for only 1 purpose.

i'm playing with pop!_os 18.04 & even it is moving towards simpler apps, there usb flasher compared to ubuntu's startup disk creator is dead simple.

---

### Post by futz2 on 2018-03-29
> **kerry_s said:**
> i think the reason for the dumbing down, is because a lot of apps are having to be rewritten to keep pace with new code.
if your a developer and you want to make it as simple as possible for future changes, your going to try & cut it down, less changes/fixes for future versions.
i see a very huge trend towards apps that only do 1 thing, but do it well.
Well... The trend is getting real tiresome. A lot of the software I use and love is getting destroyed. I'm getting pretty sick and tired of it.

> have a look at elementary os if you have time, just run it live, there curated apps. if your looking for a app to just format a disk, they have that, it has only 3 choices & all it does is format the drive you select.
they have a growing stable of 1 shot apps, made for only 1 purpose.
I tried Elementary a few years back and did not like it. I hear quite a few Linux people crowing about it lately. I should give it another spin and see how it's coming.

> i'm playing with pop!_os 18.04 & even it is moving towards simpler apps, there usb flasher compared to ubuntu's startup disk creator is dead simple.
I just installed Pop in a VM the other day. Seems good, but I really hate Gnome 3. I am giving it a fair trial though - maybe I can learn to live with it. I tried a Budgy spin a while back - I think I could live with that maybe. Too bad Unity is going away - I've been pretty happy with it (after initially thinking it was going to be terrible). I'll probably run that 14.04 box until I'm forced to up it.

> their usb flasher compared to ubuntu's startup disk creator is dead simple.
I didn't look at it. Are they using Etcher? Now that's a nice simple program that does one thing and does it well.

---

### Post by kerry_s on 2018-03-29
> I didn't look at it. Are they using Etcher? Now that's a nice simple program that does one thing and does it well. 

not etcher, there doing there own. if you think about it all you really need is a nice gui to wrap around the dd command. lol

it's all the same underneath, no matter the linux, it's all just a change of clothes. i find gnome very easy to use, but i've always been able to adapt no matter the gui, i can easily get use to all the other de's.

the only 1 that caught my attention this week was that new slax 9, i installed it to a very old lappy. [https://distrowatch.com/](https://distrowatch.com/)
try that in vm, talk about really dumbing down.

---

### Post by futz2 on 2018-03-29
> **mastablasta said:**
> Anyway there is many pic managers including the full-of-features DigiKam.
I tried DigiKam years ago and it was no good for me at the time. I should try it again and see how it's coming along.

> **mastablasta said:**
> But for viewing and light editing i find that nomacs works well. very similar to irfanview.
Hey! I'm trying out Nomacs - never heard of it before - and I'm not immediately hating it. Think I'll give it a longer term test. It's not good right out of the box, but neither is Gthumb. It is snappy quick, which is a plus. Has lots of parameters to set - I may be able to get it set up good enough to be a credible replacement for Gthumb. We shall see. Thanks for the suggestion.

> **kerry_s said:**
> not etcher, there doing there own. if you think about it all you really need is a nice gui to wrap around the dd command. lol
Yup. Not much to it.

> **kerry_s said:**
> it's all the same underneath, no matter the linux, it's all just a change of clothes. i find gnome very easy to use, but i've always been able to adapt no matter the gui, i can easily get use to all the other de's.
True. Back in the day I used to try all kinds of distros, but I gradually realized that after I got each one customized to suit me they all turned into "Ubuntu" sorta (imagine Fedora and Gentoo "becoming" Ubuntu), so I just dropped the distro hopping and stuck with Ubuntu. 

> **kerry_s said:**
>  the only 1 that caught my attention this week was that new slax 9, i installed it to a very old lappy. [https://distrowatch.com/](https://distrowatch.com/)
try that in vm, talk about really dumbing down.
May give it a whirl. I sometimes have a use for tiny Linuxes. Still run CrunchBang occasionally on a netbook.

---

### Post by kansasnoob on 2018-03-29
The GNOME devs seem hell bent on wrecking everything from GTK+ 3 upwards and outwards so I'm seriously looking at QT. KDE PLasma is a bit too bloated for my liking but I see that Budgie is changing to QT. And eventually LXQt will get the wrinkles ironed out. Deepin seems to have the wrinkles ironed out already but I'm not quite ready to make that leap.

For now I can live with (but not love) Ubuntu 16.04 tweaked to my liking and keep playing until 2021 grows nearer before making a decision. I'm pretty sure I'm not alone when it comes to wanting an OS that I can truly love again. But for now anything GTK based is pretty much off the list, unless MATE totally revives GTK +2.

---

### Post by futz2 on 2018-03-31
> **kerry_s said:**
> the only 1 that caught my attention this week was that new slax 9, i installed it to a very old lappy. [https://distrowatch.com/](https://distrowatch.com/)
try that in vm, talk about really dumbing down.
Oh man! I like that little thing. Tiny and simple, yet still useful. Not as your main machine, obviously, but Slax 9.4 is pretty cool for what it is.

---

### Post by kerry_s on 2018-03-31
> **futz2 said:**
> Oh man! I like that little thing. Tiny and simple, yet still useful. Not as your main machine, obviously, but Slax 9.4 is pretty cool for what it is.

lol, i know right. throw that puppy in memory & wohooo.
i wish it had a normal type installer though. coping the /slax folder & running the .bat file was a chore, i ran another live linux to do the work of formatting the disk, coping the folder & running the bootinst.bat

---

### Post by futz2 on 2018-04-16
Haha! Found another great quote.

"This is my workbench, dammit. It's not a pretty box to impress people with graphics and sounds.  When I work at this system up to 12 hours a day, I'm profoundly uninterested in what user interface a novice user would prefer."[INDENT]   – [Erik Naggum, 1997-02-16]("http://groups.google.com/group/comp.lang.lisp/msg/6dd13ffe0e273031") 

 [/INDENT]

---

### Post by thenailedone on 2018-04-19
I think this example shows two of the things that make Linux so powerful (and interesting) to me:

[LIST=1]
[*]Developers can scratch their own itches and do as they like.
[*]Users have choices, Nautilus not doing it for you anymore than use Nemo (or Thunar or PCManFM or Dolphin (not sure how well that works outside full blown KDE)... heck Ranger is also an option :KS
[/LIST]

---

### Post by hrsetrdr on 2018-04-19
I was massively put off by the whole Gnome 3 thing, was placated somewhat with being able to use fallback mode, but that has since been scrapped.

But, I'm really pleased with MATE, I feel like a grownup again.

---

### Post by venetin on 2018-04-22
I think you can try xnviewmp

---

