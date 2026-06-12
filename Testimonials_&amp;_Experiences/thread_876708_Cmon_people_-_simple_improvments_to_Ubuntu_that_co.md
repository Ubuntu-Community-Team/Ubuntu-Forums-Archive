---
title: "Cmon people - simple improvments to Ubuntu that could drastically make things easier"
date: 2008-08-01
forum: Testimonials &amp; Experiences
---

### Post by fd9_ on 2008-08-01
I posted a thread not too long ago about 12 things that would make Ubuntu more user-friendly. After reading through the responses and coming up with new ideas, I think I've narrowed down the problems quite a bit. One of the major issues I still see is the fact that packages need to be more accessible, especially to new users. Some examples:

1) I have to install flash for firefox, and I'm given three choices when I go to a site that needs flash. How am I supposed to know which one to install when there's absolutely no description for any of them?

2) Well it turns out (after installing all three) that the only one that works is Adobe's version. But why am I taken to Adobe's website to download and install myself when flashplugin-nonfree is the same thing?

3) Totem doesn't play sound for quicklime videos. Turns out I needed some codecs. I had to right click the video, say "Open with Totem" and then Totem was smart enough to install the codecs for me. Took me forever to figure that out. Why didn't firefox prompt me for the missing codecs like it does for flash?

4) I need to configure my touchpad since it's way too sensitive. So I go through the menu and find the mouse options - unfortunately there weren't enough options available for what I wanted to do. Turns out I needed to install gsynaptics or something similar. Why isn't there a button in the menu options that says "advanced options" which automatically downloads gsynatpics so I don't have to waste a perfectly good Saturday morning on Google trying to figure out which program I need to install? Sure, it doesn't need to be *installed by default*, but at least let me know about it.

5) I want to really rock out my desktop, so I go to desktop effects and select the highest option. Don't you think I might want compiz-manager too? At least let me know it exists. After all, I've already told you I want to max out my effects.

I see the same type of questions being asked all the time, over and over again. In general this is how it goes:

OP: "How do I [fill in the blank]?"
Reply: "It's easy! sudo apt-get install ..."

The problem is simply, people don't know what packages to install. The result is that they end up wasting time here on the forums asking the same questions that have been asked countless times before, or increasingly rely on Google to figure it out. There are hundreds of great apps out there sitting in the repositories that we need to make more accessible WITHOUT Google or Joe Shmoe's random coding blog - because that's how a lot of users are getting their help, and it's not right! Especially when they shouldn't have to.

If people are in the mouse settings, tell them about gsynaptics. If people are maxing out their desktop effects, give them a clue about compiz-manager, etc... They don't need to be installed by default, but that doesn't mean users should have to find this stuff on their own, right?

BTW, where is the "Suggestions for Ubuntu" forum? Because for the life of me I can't seem to find it.

---

### Post by tiachopvutru on 2008-08-01
> **fd9_ said:**
> 
BTW, where is the "Suggestions for Ubuntu" forum? Because for the life of me I can't seem to find it.

I suppose the closest thing you can find is [Ubuntu Idea Pool]("http://ubuntuforums.org/forumdisplay.php?f=306").

I agree with most of your points. However, isn't being taken to Adobe website to download & install Flash suppose to be Firefox's behavior?

---

### Post by SunnyRabbiera on 2008-08-01
well if adobe didnt bog down flash with their proprietary nonsense then we can ship the default flash no sweat... but its a company in Microsofts back pocket.

---

### Post by Methuselah on 2008-08-01
> 

OP: "How do I [fill in the blank]?"
Reply: "It's easy! sudo apt-get install ..."



That gave me an idea for a funny/geeky tshirt.
sudo apt-get install <aomething_funny>.
Who would wear it though !?

Anyway, maybe people need to be pointed to Add/Remove programs after instalaltion.
In ubuntu most applications are free and Add/Remove is your gateway to customising your system.

So when I type touchpad in the Add/Remove search box guess what comes up? Yup, GSynaptics.
And if I type in 'desktop effects? lo and behold...compiz config settings manager!
Really, now...typing quicktime can't bring up the very GStreamer plugins I need. That would be too much!

No need to search google at all, most things are a few clicks away for the newbie.
Unfortunately most new ones are used to the windows' way of doing things where add/remove only removes and you have to scour google for useful programs.
If they do that with ubuntu they might end up finding mystical things like rpms, debs and the dreaded tar.gz containing things called makefiles and source code.

Maybe a very short and skippable post-installation 'welcome to ubuntu' video introducing a few system fundmentals (a kind of "what's next") woudln't be a bad idea.
[I think you mentioned this among your original 12]
It might help new ones who didn't do much research (probably relying on windows knowledge of limited applicability) be more productive.

I think the user needs to be empowered but I don't know if linux should be 'chatty'.
It's just going to mean additional thought burden and more clicks.
It's not a nice feeling when on OS brings up a dialog asking a question you have no clue how to answer but you can't proceed unless you say *something*.
There will be that fear about possible permanent negative consequences of your choice and you'll have to do research right then if you're concerned enough.

Windows frequently interrupts you volunteering to do all manner of things you never cared about and weren't thinking of at the time.
Thinking back, the contrasting quietness of linux is one of the things I like about it.

---

### Post by Elfy on 2008-08-01
> **tiachopvutru said:**
> I suppose the closest thing you can find is [Ubuntu Idea Pool]("http://ubuntuforums.org/forumdisplay.php?f=306").

I think the ideas pool will be stopped eventually reference this sthread 

[http://ubuntuforums.org/showthread.php?t=841326&highlight=idea+pool](http://ubuntuforums.org/showthread.php?t=841326&highlight=idea+pool)

Brainstorm is the place to go now it seems

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by tiachopvutru on 2008-08-01
> **forestpixie said:**
> I think the ideas pool will be stopped eventually reference this sthread 

[http://ubuntuforums.org/showthread.php?t=841326&highlight=idea+pool](http://ubuntuforums.org/showthread.php?t=841326&highlight=idea+pool)

Brainstorm is the place to go now it seems

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Isn't the Idea Pool subforum suppose to be a more organized Brainstorm?

I hear that Brainstorm is rather messy.

---

### Post by Elfy on 2008-08-01
> I hear that Brainstorm is rather messy.You hear right - I'm just tacking on what I read a while back.

---

### Post by L815 on 2008-08-01
I agree with some of your points. Especially the fact that new people to Ubuntu/Linux, do not know package names. (I still have this issue sometimes).

The problem with Add/Remove is there is only a certain amount of packages listed. Synaptic shows much more, BUT sometimes you need to know the name of the package anyway.

In the end, you will find terminal a much faster shortcut when you DO know the name of the package. 

So it's like a double edged sword right now. Hurts from both sides :lolflag:

---

### Post by fd9_ on 2008-08-01
> **Methuselah said:**
> 
Anyway, maybe people need to be pointed to Add/Remove programs after instalaltion.

So when I type touchpad in the Add/Remove search box guess what comes up? Yup, GSynaptics.
And if I type in 'desktop effects? lo and behold...compiz config settings manager!
Really, now...typing quicktime can't bring up the very GStreamer plugins I need. That would be too much!


The point is not to make Add/Remove or Synaptics easier (although it can be, like you said). Pointing them to Add/Remove programs after installation wouldn't make much sense since they don't already know what's installed. After a fresh install, you can't expect a new user to know exactly what packages they want right off the bat.

Instead, the idea is to let users know about packages depending on what they're doing at the time. If they're in the mouse options, and they go to the advanced tabs, needless to say they probably want more mouse options. So if there's a package available in the repositories that gives them exactly that, how are they supposed to know about it? The answer: Google. And that's not a good thing.

> **Methuselah said:**
> 
I think the user needs to be empowered but I don't know if linux should be 'chatty'.
It's just going to mean additional thought burden and more clicks.


Absolutely not. In fact it's going to mean quite the opposite. I don't see how what I'm proposing here would make it seem "chatty" at all.

---

### Post by Methuselah on 2008-08-01
> 
The point is not to make Add/Remove or Synaptics easier (although it can be, like you said). Pointing them to Add/Remove programs after installation wouldn't make much sense since they don't already know what's installed. After a fresh install, you can't expect a new user to know exactly what packages they want right off the bat.


i didn't type in the package names, just something related to them.
when the list comes up you get a description and an indication as to whether the given program is already installed.
so if they know what hey want to do and know enough to type it into add/remove they'll probably get back useful options.

i don't say your idea isn't useful but i was looking at the other side. 
programs occasionally being proactive and suggesting options isn't necessarily bad but it can be overdone.
ubuntu generally does exactly what i tell it with little additional fuss which i like.

i think newbie friendly features are overrated because users are newbies for a small fraction of their interaction time with a system.
i mean, in short order people are loving their terminals and won't have any use for hand-holding!

---

### Post by steveneddy on 2008-08-03
a - make me a sandwich

b - no!

a - sudo make me a sandwich

b - ok

old joke

Try some of the links in my sig for many of the questions that you have.

---

### Post by tuxerman on 2008-08-03
If you're really looking to easily customise stuff and more 'advanced options', I suggest you get Kubuntu. It offers a lot of stuff you can change and customise easily, unlike GNOME, which doesnt show that many options in any tool. I guess that's the way KDE and GNOME are.

---

### Post by Jordanwb on 2008-08-03
> **fd9_ said:**
> 1) I have to install flash for firefox, and I'm given three choices when I go to a site that needs flash. How am I supposed to know which one to install when there's absolutely no description for any of them?

I agree.

> **fd9_ said:**
> 3) Totem doesn't play sound for quicklime videos. Turns out I needed some codecs. I had to right click the video, say "Open with Totem" and then Totem was smart enough to install the codecs for me. Took me forever to figure that out. Why didn't firefox prompt me for the missing codecs like it does for flash?

Same for me but for mp3 files. But even after installing the codecs in Banshee or Rhythmbox, it still won't play(:confused:). So I installed VLC because they were smart enough to include mp3 support automatically.

> **fd9_ said:**
> OP: "How do I [fill in the blank]?"
Reply: "It's easy! sudo apt-get install ..."

The problem is simply, people don't know what packages to install. The result is that they end up wasting time here on the forums asking the same questions that have been asked countless times before, or increasingly rely on Google to figure it out. There are hundreds of great apps out there sitting in the repositories that we need to make more accessible WITHOUT Google or Joe Shmoe's random coding blog - because that's how a lot of users are getting their help, and it's not right! Especially when they shouldn't have to.

What I did was in Synaptic was search the description for something like "Hex Editor" or "C#".

> **steveneddy said:**
> a - make me a sandwich

b - no!

a - sudo make me a sandwich

b - ok

old joke

Try some of the links in my sig for many of the questions that you have.

Yeah I have the xkcd comic printed out and posted on my wall.

> **tuxerman said:**
> If you're really looking to easily customise stuff and more 'advanced options', I suggest you get Kubuntu. It offers a lot of stuff you can change and customise easily, unlike GNOME, which doesnt show that many options in any tool. I guess that's the way KDE and GNOME are.

That's why I like Kubuntu. It's easy on my laptop and it looks damn cool.

---

### Post by tuxerman on 2008-08-03
> **Jordanwb said:**
> 
That's why I like Kubuntu. It's easy on my laptop and it looks damn cool.

Exactly. And even a layman can change anything he wants. Well, *almost* anything. I wonder why GNOME 'hides' things. Isn't that too much of a price to pay for simplicity and neatness?

---

### Post by Jordanwb on 2008-08-03
> **tuxerman said:**
> Exactly. And even a layman can change anything he wants. Well, *almost* anything. I wonder why GNOME 'hides' things. Isn't that too much of a price to pay for simplicity and neatness?

Also all the settings are in one location. In Gnome there's Administration and something else. I always forgot what Printing was under.

---

### Post by Ms_Angel_D on 2008-08-04
I think I agree with the OP on most all of his points, I personally have had to write out my own instruction manual for things I must do once I've installed ubuntu. Nobody should have to do that. Granted there are some things On my little manual that only apply to my particular install but the point is that I had to make the little manual at all. Some things such as the need to enable effects, and and install codecs should be easy information to find without having to search the forums or google.

---

### Post by Jordanwb on 2008-08-04
Also I wanted to compile my own kernel. I downloaded the source code from kernel.org, and there's so much crap that Ubuntu feels I need that I don't know what I need and what I don't need, examples: 

Token Ring
AppleTalk
ISA cards
WAN Routing
Point to Point Protocol
Macintosh Drivers

Okay those are examples where I know that I don't need them. But there's also stuff that I include just because the descriptions are as clear as mud.

---

