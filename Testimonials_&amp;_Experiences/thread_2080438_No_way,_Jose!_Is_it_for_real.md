---
title: "No way, Jose! Is it for real?"
date: 2012-11-04
forum: Testimonials &amp; Experiences
---

### Post by DDDa on 2012-11-04
This an overview of the steps I had to take to come here. A little background on me: I'm a pragmatic guy, so I don't love Linux. I don't love tools. I love what works for me. But I do give preference to open stuff if I can, because it benefits me in the end.

[SIZE="3"]**- My problem with Windows**[/SIZE]

Using Windows is like computing with one hand tied to my back.

[LIST][*]**Flexibility **is nonexistent, nothing like bash et al, and doing stuff actually requires freewares. And pray that you won't need to mix functionality, as GUI freewares are a one trick poney.
[*]**Android SDK tools** and stuff run much slower on Windows (details later). And it I don't know if it's just me, but programming on anything other than MS tools on Windows is never even good enough.
[*]And all the usual stuff: fear of malware, AV and firewall slows down everything, gluttony for memory... the usual joke.[/LIST]

But at least I could work and do stuff on 7. It gets stuff done.

[SIZE="3"]**- Windows advantages**[/SIZE]

About the flexibility, yes, it's the command line again. But because I like the command-line doesn't mean I want it always: I want it when I want, because I want, not because I need. If I don't know where to start, I want a GUI. And that was a common Linux problem, and still is a bit. So...

[LIST][*]**Easy of use.**
[*]**Software** compatibility. In my case, Photoshop only.
[*]**Heat management**. Being a notebook-only user since 2003, it compensated everything. Or so I though...[/LIST]

[SIZE="3"]**- My problem with Linux**[/SIZE]

Just to give you an idea of my recent past with Linux in general, look at [this]("http://ubuntuforums.org/showthread.php?t=1497505"). More than 2 years ago. And there are the ***years*** before that (Hoary being my first Ubuntu... and Mandrake, Slackware and Red Hat way before that...).

[LIST][*]**Hardware support**: improved a lot in recent years.
[*]Heat hadn't, as the topic above illustrates. Since 2010, that's what made me stay away from Linux and with Windows 7 Pro x64.
[*]The constant need for a command line.[/LIST]

[SIZE="3"]**- The change**[/SIZE]

During these 2 years, I accepted living Windows. I even had Cygwin stuff to pretend to do things I needed. But after looking at the direction Windows is taking with Windows 8, and having used it for a long period, I said to myself that enough is enough.

But Linux was out of choice, I started to consider moving to macs (if OS X worked on my X201, I would have jumped). But since I had cleaned the HDD, I decided to try something different: Xubuntu 12.10, out of nowhere. I always tried Ubuntu, and I didn't like Unity. So why not?

And it all changed. No, really. There's a say in my country that "when the alms are too much, the saints suspects", so I waited to see if it was real. Now, I can say it is real folks! Using for a few days now... *and I didn't go back to Windows! For the first time, I don't want to.* I actually tried to believe, and I wanted to go back to Xubuntu.

[SIZE="3"]**- Xubuntu 12.10 advantages**[/SIZE]

[LIST][*]**Heat is now less!** I couldn't possibly believe that the fan was working less on Xubuntu than under Windows 7. Not only the fan, but the notebook was cooler, too. So it's the real deal. Unfortunately, I'm with a dead battery to test, but doesn't change.
[*]**Android SDK** and tools run waaaaaaay faster on Xubuntu than under Windows. Don't ask me why, but it does. Too much free memory? I dunno. Pragmatically I say: it does. The emulator images run faster as well (note: no, I'm not talking about GPU emulation and Intel images).
[*]**Much less use of command line**: unfortunately, it is not eliminated as I wish it was (in the perfect world, I'd like a Google Voice or Siri that I say "do this" and it understands and does it). But it is much, much better, almost satisfies considering my knowledge level. I mean, all hardware and printer working perfectly out of the box? Configuration is a different issue though.[/LIST]

So, that's it. With heat finally solved for my notebook, and all the other advantages, I can now safely say that I'm here to stay. Hope you all appreciate the feedback. I still keep Windows on dual boot because of one software that does not play nice (or I can't make it work).

Best regards and kudos to the Ubuntu (focus on the Xubuntu) team! You got the wrong impression with the title, didn't you? :)

:guitar:

**Now, minor things I had to take care of (please guys, fix it!!)**

[LIST][*]Dark background on tooltips: mess everything in Eclipse IDE.
[*]Provide selectable CPU governors on the panel. Couldn't make the Gnome panel stuff work, so I had to pick the CL to give rights to cpufreq-set and put script shortcuts on the panel. Works fine, but I'd rather have a panel widget do that out of the box.
[*]I've seen rare crashes. Mostly 3rd party apps from apt. Don't disturb me, and it's not frequent, so not a problem.[/LIST]

**And my curses:** 

[list][*]Curse you Oracle! Installing the JDK/JRE is still non trivial. Curse you a thousand times! :)
[*]Curse you Adobe! Put Photoshop on Linux![/list]

---

### Post by coldraven on 2012-11-04
I recently installed Xubuntu on a friends Asus eee 900 tiny notebook. Everything worked out of the box and it's fast! You can pick them up cheap, especially if you get a white one.
> Curse you Adobe! Put Photoshop on Linux!
Try playing around with the G'MIC Gimp plugin. Lots of other plugins also available here:
[http://registry.gimp.org/popular](http://registry.gimp.org/popular)

---

### Post by mastablasta on 2012-11-04
so first off... the heat issue was in kernel. if you used newer kernel you would likely not be having it before. and again the hardware was buit for windows. if you used one that came ubuntu preloaded or is certified for ubuntu you wouldn't have this issue. unfortunatelly usually only lower end or business models come linux preloaded. dell is plannign to turn this arround a bit as i read.

and second - gnome is made to hide advances settins and options from user. which is probably why you needed command line i am guessing. XFCE lately porgressed as well as KDE where you can see most settings in GUI. and i each edition they add more to GUI. so i rarely use a command line there. usually to torubleshoot something.

> **DDDa said:**
> 
**And my curses:** 

[LIST]
[*]Curse you Oracle! Installing the JDK/JRE is still non trivial. Curse you a thousand times! :)
[/LIST]


what do you mean not trivial? download the file, tell system it's an executable file (OS security feature), double click it.
as i know all things that come out of respositories are done like that unles they are only source code and still need to be compiled. 

as for Adobe... unless you are a pro in the Photography business i think GIMP can do it. especially with plugins.

---

### Post by Lars Noodén on 2012-11-04
About the Eclipse IDE and crashes, file bug reports to let them know of the problems.  The developers don't read the forums and the correct channel for bugs is launchpad.  Use the program 'ubuntu-bug' to help collect the data needed for a bug report.

About Photoshop, I think the first petition I saw for Linux was over 10 years ago.  There are apparently some other external factors working against Adobe.  Otherwise we'd have a port by now.  Apparently, WINE does a good job on some versions of Photoshop.  Check to see how your version is rated:
[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)

---

### Post by DDDa on 2012-11-04
For what I've read, this section is not the best one to have extended debates, so excuse me in advance. I'll just clear some things so I won't leave a bad impression (just in case). Hopefully the opposite, as I'm very happy with XFCE/Xubuntu:

> **mastablasta said:**
> so first off... the heat issue was in kernel. if you used newer kernel you would likely not be having it before. and again the hardware was buit for windows. if you used one that came ubuntu preloaded or is certified for ubuntu you wouldn't have this issue. unfortunatelly usually only lower end or business models come linux preloaded. dell is plannign to turn this arround a bit as i read.

I know it's in the kernel. About hardware, to put it simply: the hardware choice (X201) had a higher value to me than explicit Linux support. I'm now glad I have both.

> and second - gnome is made to hide advances settins and options from user. which is probably why you needed command line i am guessing. XFCE lately porgressed as well as KDE where you can see most settings in GUI. and i each edition they add more to GUI. so i rarely use a command line there. usually to torubleshoot something.

Tried to avoid the ancient-old Gnome vs. KDE debate, feature creep vs. feature drain. I second the CL comment about XFCE, and like I said, *one* of the reasons why I'm glad! =D> ***To me***, the perfect balance.

> what do you mean not trivial? download the file, tell system it's an executable file (OS security feature), double click it.
as i know all things that come out of respositories are done like that unles they are only source code and still need to be compiled. 

Chromium plugin needed a symlink to one specific library file. Not hard to find on the net, just not trivial. Hence my choice of word: "not trivial", not "not easy". Perhaps I could use OpenJDK, but I've heard about issues with my home banking. Maybe later I can test and file a bug (if needed).

> **Lars Noodén said:**
> About the Eclipse IDE and crashes, file bug reports to let them know of the problems.  The developers don't read the forums and the correct channel for bugs is launchpad.  Use the program 'ubuntu-bug' to help collect the data needed for a bug report.

I know a testimonial is not a place to fill bugs. Consider it more as a tongue-in-cheek, because there are bugs already filled and I had made sure to mark the relevant bugs as "affecting me as well". Anyway, sorry for the misunderstanding, I'm horrible with happy humorous posts. :)

About wine, I've tried and couldn't make CS2 work for now, too much errors (probably my mistake, oh well). Since I'm very busy and don't have much time to test (and dual boot works fine), I'm not "scratching the itch" for now.

Best regards all.

---

### Post by Linuxisfast on 2012-11-04
Unless you have super cutting edge brand new hardware, the heat issue usually is a matter of installing proper video drivers, in this case proprietary and it goes away.

---

### Post by mastablasta on 2012-11-05
> **DDDa said:**
>  
I know it's in the kernel. About hardware, to put it simply: the hardware choice (X201) had a higher value to me than explicit Linux support. I'm now glad I have both..
yes it's hard to find the hardware that pleases the user and that has full linux compatibility. i still think the fault here is with manufacturers (for not releaseing the drivers at least proprietary ones) not linux as an OS.
 
>  
Chromium plugin needed a symlink to one specific library file. Not hard to find on the net, just not trivial. Hence my choice of word: "not trivial", not "not easy". Perhaps I could use OpenJDK, but I've heard about issues with my home banking. Maybe later I can test and file a bug (if needed).
 
i wonder if that is not the Chromium issue. and i wonder if it would also appear in Chrome. In any case that would be something for Chromium/Chrome developers and google to think about and still am not sure it has much to do with linux. at least i haven't seen any issue in windows. then again it could be Oracle's fault.

---

