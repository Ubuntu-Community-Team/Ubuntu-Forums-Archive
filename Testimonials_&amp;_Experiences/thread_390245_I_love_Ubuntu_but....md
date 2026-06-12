---
title: "I love Ubuntu but..."
date: 2007-03-21
forum: Testimonials &amp; Experiences
---

### Post by fluoblack on 2007-03-21
Ubuntu is really a great OS, I use it since about a year now and I recently got rid of XP and turned into a fresh and complete Ubuntist. I really enjoy the freedom of choosing my softwares, being able to configure every bit of the system and that's really cool. I owe you a beer for that.

BUT...

At every upgrade, I turn into a Ninja-brain-eater, trying to install these Goddamn graphic drivers, struggling all day long, installing crashing, reediting, rebooting, (these days I almost bless XP) just to get my good old GeForce4 working. I try everything I can, how to's, script, black magic, everything and at the end of the day (week) all I got working is this damned "nv"...  It just piss me off.

Why is it so difficult to install and/or configure these drivers?! Is there something going on to make it easier? 
I hope so because if not, it's certainly the best reason to keep MS in the box and to stay away from Linux.

---

### Post by chalimac on 2007-03-21
Try the envy script:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by beniwtv on 2007-03-22
I also own a GeForce 4 on my desktop PC, and it's really easy to install.

Here's what I have to do:

1. Install nvidia-glx, either from the command line ("apt-get install nvidia-glx") or from the Synaptic package manager

2. Then I edit the file "/etc/X11/xorg.conf", and change the "vesa" (sometimes "nv") in the Device section to "nvidia".

3. Reboot or restart X and there I go.


Even easier than in Windows, having to hunt for the drivers on Nvidia's webpage...

EDIT: You have do to this only once, after upgrading all still will be fine.

---

### Post by Adamant1988 on 2007-03-22
> **fluoblack said:**
> Ubuntu is really a great OS, I use it since about a year now and I recently got rid of XP and turned into a fresh and complete Ubuntist. I really enjoy the freedom of choosing my softwares, being able to configure every bit of the system and that's really cool. I owe you a beer for that.

BUT...

At every upgrade, I turn into a Ninja-brain-eater, trying to install these Goddamn graphic drivers, struggling all day long, installing crashing, reediting, rebooting, (these days I almost bless XP) just to get my good old GeForce4 working. I try everything I can, how to's, script, black magic, everything and at the end of the day (week) all I got working is this damned "nv"...  It just piss me off.

Why is it so difficult to install and/or configure these drivers?! Is there something going on to make it easier? 
I hope so because if not, it's certainly the best reason to keep MS in the box and to stay away from Linux.
Well, it is a shame that you're having such a time with it, but you need to remember a few things: 
[INDENT][list=123]
[*] No one is forcing you to upgrade.  I know it can feel a bit like if you don't you're behind the times, but honestly If it weren't for Feisty I would still be running Dapper.  Don't like edgy.
[*] Feisty will go a LONG way to fix your problem as it contains a program called "restricted-manager" which will download, install, and configure your graphics drivers for you (after a warning about their non-free nature of course)
[*] Please try to remember that some work has to be put into every OS, even Linux.  Whereas Windows requires more work as time goes on, Linux needs more work at the start and then never really needs it again until you reinstall or do some such thing.  
[/list][/INDENT]

I hope that helped a bit.

---

### Post by fluoblack on 2007-03-22
I haven't been forced to upgrade indeed, but I thought (a bit too fast maybe) that this driver manager would make my life easier (it didn't, yet). I know it takes more time to make things go right in the Linux galaxy, I don't want blame anybody. 
But when you take a global look at Ubuntu, the whole thing is pretty smooth from the begining: you can install whatever you want in 3 clicks/command lines. That one of the reasons why I choosed this distribution. 
In the contrary, when you put your hand in the hardware stuff (Xorg, kernels & Cie), you'd better learn chinese and get a life vest. And it's the same for most of the Linux distro.
There is a lot of people who reinstall the whole OS because they can't start X when they install the graphic drivers (or other stuff), and after 3 reinstallation, I can undersand why they get rid of it.
Linux is made first for developpers, but mostly for obstinate people. 
I stick to Ubuntu because I love it, it will stay on my computer and I will use it for a long time. The expression "Linux for Human beings" just makes me laugh sometimes.

---

### Post by eentonig on 2007-03-22
It shouldn't make you laugh.

Human beings don't go upgrading their system. They just go browsing the internet and sending mails.And now and then they install something simple. And Ubuntu is perfect for that.

Geeks try to run the latest of the latest and make assumptions that things will work when they do this or that. 

That being said. I'm a geek, and occasionally I break my system. I must say that Ubuntu is by far (for me) the friendliest system to restore if I screwed up.

---

### Post by 3rdalbum on 2007-03-23
Unfortunately, although Ubuntu is designed for everyday people, some companies simply REFUSE to make it easy to install their proprietry software.

I had a dickens of a time installing Unreal Tournament on Ubuntu, simply because I had bought the Anthology and the software company had hardcoded their downloadable Linux installer to only work on non-Anthology discs. 3D drivers are also stupidly difficult to install - I mean, if some open-source hackers can create an easy installer in Envy, why the ******** can't ATI? And Nvidia is probably worse - you can't even run X while installing the driver!

---

### Post by fluoblack on 2007-03-23
> **eentonig said:**
> Human beings don't go upgrading their system. They just go browsing the internet and sending mails.And now and then they install something simple. And Ubuntu is perfect for that.

I agree but what's the point of making upgrades then? I think Human beings who browse the internet need some non-free stuff such as real player flash, java, audio and video codecs etc. which are not (or not entirely) provided by Ubuntu, and then same problem: you have to tweak the OS, even if it's simpler than installing graphic drivers, it's boring. 
And what about Human Beings who don't have (at least) 150$ to put in an OS who provides just an OS and nothing else, people who who anyway need a computer for their everyday life, for work or for studying (which is the main goal of Ubuntu). I am personally in this case, I learn myself 3D design and without 3D acceleration, I'm screwed.
Non-free stuff are not expensive, they are mostly free of cost but not of source. So what's the problem?! I'm not asking for another driver if it works, I just want to get an easy way to install it. Nvidia drivers are given for free, done by people who are investing their money and work to make it possible and to make our virtual life better, but they just want to keep their jobs. Everybody doesn't want to work for free! 
On the other side (and correct me if i'm wrong), people don't want to work on that because it's closed source, and it's stupid. GNU/Linux programmers fought for ages trying to get that kind of things, and when they finally get it, they just turn their back and say 'no thanks, it's closed source'. Isn't it a bit childish?
I'm aware that I certainly don't understand what's going on behind, but what I see is that great possibilities are there but nobody wants to touch it.
Neverending story...

---

### Post by manicka on 2007-03-24
the heading of this thread says it all really

---

### Post by 23meg on 2007-03-24
> I agree but what's the point of making upgrades then? I think Human beings who browse the internet need some non-free stuff such as real player flash, java, audio and video codecs etc. which are not (or not entirely) provided by Ubuntu, and then same problem: you have to tweak the OS, even if it's simpler than installing graphic drivers, it's boring.

If you find installing the non-Free stuff boring and/or difficult, use something like Linux Mint, Ubuntu Ultimate etc.


> Non-free stuff are not expensive, they are mostly free of cost but not of source. So what's the problem?!The problem is that you can't work to improve non-Free drivers, since they don't disclose the source code, let alone give you permission to modify and redistribute it.>   I'm not asking for another driver if it works, I just want to get an easy way to install it.

You're getting it in Feisty, as Adamant1988 said; it's called restricted manager.

> On the other side (and correct me if i'm wrong), people don't want to work on that because it's closed source, and it's stupid. GNU/Linux programmers fought for ages trying to get that kind of things, and when they finally get it, they just turn their back and say 'no thanks, it's closed source'. Isn't it a bit childish?

Not that they don't want to work on it because it's closed source, but they can't. They didn't fight for ages to get a binary blob, stick it in their OS and hope that it works. Yet they're doing their best to work around the restrictions and present it to you in an easily installable way.

> 
I'm aware that I certainly don't understand what's going on behind, but what I see is that great possibilities are there but nobody wants to touch it.
Neverending story...

Trying to understand what's going on behind at least to some degree is a good idea when you're planning to make bold comments.

---

### Post by kirenpillay on 2007-03-27
I thought I loved ubuntu but...

I've been struggling for almost half a year to get a bluetooth dial-up working on Edgy (6.10). I've checked the forums, and there are a number of hacks to get it working. I've tried going through a lot of them with no success.

My concern is that these fixes are hacks and not the way the systems should be working. One post recommended using dbus to get bluetooth working, and later i read that dbus was no longer the recommended way. There should be some kind of documentation saying how this stuff should work. The How-to is good, except if one of the steps don't work, then you are stuffed.

I'm a user that doesn't want to get into the technical details. I want someone to say this is how you do it.  If X doesn't work, try Y. If Y doesn't work, try Z.End of story.

I had a problem with MSSQLServer today to fix a problem. Problem was solved (albeit a tardy reason for having the problem in the first place). There was no need to guess what to do. The steps for resolving the problem is documented in online help, no hacks necessar
y. 

Ubuntu's online forums are cool, but I'm sure a lot of the people are answering questions that have already been answered before. There needs to be better trouble-shooting documentation. Development teams should provide better manuals on how subsystems should work.

(I'll get off my soap-box now).

---

### Post by fluoblack on 2007-04-20
Ok now that I installed feisty, I can change my testimony...

I F**KIN' LOVE IT !!!

Installed flawlessly, i kept my /home sweet /home intact, graphic drivers installed in 10sec+1reboot, Desktop effects available out of the box (useless but cool for those who can't live without it), I got sound, I got video, I got the tablet, I got everything. 

Man, I DIDN'T EVEN TOUCH XORG !!!!!

Feisty Install time 30-45min (and i messed the first install, my bad) and thats it, nothing to tweak, it just works, and it works like a charm (it's almost boring, lol). 

For info: Edgy complete Install time 2-5 days, including tweaking, graphic drivers install, research for vital help, heart attacks and mass murders.

Great GREAT job guys, congratulations, you made me happy for a while :D
Thanks a lot!

---

