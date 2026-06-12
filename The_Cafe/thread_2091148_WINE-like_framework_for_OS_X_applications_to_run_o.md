---
title: "WINE-like framework for OS X applications to run on Linux?"
date: 2012-12-04
forum: The Cafe
---

### Post by Dragonbite on 2012-12-04
WINE is a great resource for running Windows-based applications on Linux but I have a question:

Could the same concept be done for Mac OS X applications?

My thinking is that since OS X is Unix-based (even if it is FreeBSD-based), could not the libraries that OS X applications use be copied in a WINE-like manner (MINE?)?

Being Unix-like, some features or pieces may already be present in Linux and would not need to be recreated.

I would think it could be "easier" to go Mac->Linux than Win->Linux.  This could open up a number of possibilities, not just things like iTunes but what about MS Office for Mac, Adobe Dreamweaver or iCloud?

What makes this not feasible, or is it feasible?  Since many programs are being made for Windows and Mac, imagine if instead of trying to use Windows applications and games, we were able to use Mac versions?

---

### Post by GameX2 on 2012-12-04
I haven't tried OS X for a long time, only in a Virtual Machine, but Wine does exist on OS X, if I'm right:

[http://winebottler.kronenberg.org/](http://winebottler.kronenberg.org/)

However, for some reasons, Wine doesn't start at all.  I need to install some kind of package that is now unsupported by Apple.  Wine redirect me to an invalid link.

---

### Post by Jakin on 2012-12-04
> **GameX2 said:**
> I haven't tried OS X for a long time, only in a Virtual Machine, but Wine does exist on OS X, if I'm right:

[http://winebottler.kronenberg.org/](http://winebottler.kronenberg.org/)

However, for some reasons, Wine doesn't start at all.  I need to install some kind of package that is now unsupported by Apple.  Wine redirect me to an invalid link.

I believe Dragonbite is refurring to the possibility of OS X compatibility layer in linux, implemented in much the way WINE give linux a windows compatibility layer.

While it sounds like a good idea, OS X Api is just as different from linux, as the windows Api's are, so i don't know if it would be "easier" to give OS X compat, vs windows compat.

---

### Post by Dragonbite on 2012-12-04
> **Jakin said:**
> I believe Dragonbite is refurring to the possibility of OS X compatibility layer in linux, implemented in much the way WINE give linux a windows compatibility layer.

Yes, exactly.

> **Jakin said:**
> While it sounds like a good idea, OS X Api is just as different from linux, as the windows Api's are, so i don't know if it would be "easier" to give OS X compat, vs windows compat.

That's what I am wondering.  I don't know all of the details about WINE, or how much of a benefit the UNIX underpinnings would provide (if any).

---

### Post by Lars Noodén on 2012-12-04
You can get a lot of Linux applications for OS X via [Mac ports](http://www.macports.org/).  There is also [Fink](http://www.finkproject.org/).  With Fink you can use apt-get and other Debian tools to install Linux apps.

---

### Post by dpny on 2012-12-04
It might be technically feasible, but I don't know if there's enough call for it to make anyone take on the work. Obviously, there's much more Windows software out there than there is software for any other desktop OS, so most of the work has gone into allowing OS X/Linux users to run Windows programs.

There may also be licensing issues. As we all know, Apple is pretty strict when it comes to the use of its software and hardware, so there may be legal reasons why no one has tried. Until recently Apple wouldn't even allow the virtualization of the desktop version of OS X under Parallels/VMWare/Virtualbox.

The closest thing I can think of right now would be running an instance of OS X in a virtual machine, but obviously that's not what you're talking about.

---

### Post by mamamia88 on 2012-12-04
maybe if the osx specific gui stuff was replaced with gtk or qt.

---

### Post by nerdopolis on 2012-12-04
There seems to be an early, relatively obscure, but active project called the darling project

[http://darling.dolezel.info/en/Darling;jsessionid=xzwrvtllkvxn15vmncg3ra4jr](http://darling.dolezel.info/en/Darling;jsessionid=xzwrvtllkvxn15vmncg3ra4jr)

---

### Post by Dragonbite on 2012-12-04
> **nerdopolis said:**
> There seems to be an early, relatively obscure, but active project called the darling project

[http://darling.dolezel.info/en/Darling;jsessionid=xzwrvtllkvxn15vmncg3ra4jr](http://darling.dolezel.info/en/Darling;jsessionid=xzwrvtllkvxn15vmncg3ra4jr)

Interesting.  Thanks for the link!

---

### Post by forrestcupp on 2012-12-04
Deja Vu. Haven't we had this very discussion on here?

Anyway, it's not as simple as MacOS X being based on BSD, so it would be easy. The BSD parts are just the very base parts of the whole OS. It's all of the proprietary stuff on top of it that makes MacOS X MacOS X. MacOS software is built to run on the proprietary stuff, it's not just BSD software.

It would take them years and years to reverse engineer that to the point to where it would be usable, just like it did with Wine. It seems like there's not really a big enough demand for it to justify that much work. Even the Darling project that nerdopolis linked to wouldn't do any good because Darwin is just the very core components of MacOS X. You can't run Mac software on Darwin alone.

---

### Post by TheMTtakeover on 2012-12-04
There is Crossover which is essentially Wine with some added hacks. This is what I use to run Microsoft Office on OSX

[http://www.codeweavers.com/about/](http://www.codeweavers.com/about/)

---

### Post by mamamia88 on 2012-12-04
> **TheMTtakeover said:**
> There is Crossover which is essentially Wine with some added hacks. This is what I use to run Microsoft Office on OSX

[http://www.codeweavers.com/about/](http://www.codeweavers.com/about/)

do people only read the title of thread before responding nowadays?

---

### Post by Artemis3 on 2012-12-05
Well the title is misleading and should be changed.

OP is talking about: running MacOS X apps in linux, same as windows apps run with wine.

Incidentally there IS a wine port for MacOSX, but the op mislead everyone ;)

The correct answer was that Darling project, good finding :)
[http://darling.dolezel.info/en/About_Darling](http://darling.dolezel.info/en/About_Darling)

---

### Post by forrestcupp on 2012-12-05
> **mamamia88 said:**
> do people only read the title of thread before responding nowadays?

The funny thing is that the last time we had this conversation a couple of months ago, that thread had a similarly misleading title. :)

---

### Post by Dragonbite on 2012-12-05
> **Artemis3 said:**
> Well the title is misleading and should be changed.

OP is talking about: running MacOS X apps in linux, same as windows apps run with wine.

Incidentally there IS a wine port for MacOSX, but the op mislead everyone ;)

The correct answer was that Darling project, good finding :)
[http://darling.dolezel.info/en/About_Darling](http://darling.dolezel.info/en/About_Darling)

Is this title any better?

---

### Post by Tibuda on 2012-12-05
> **Dragonbite said:**
> Is this title any better?

Yes, but it is only on your post, not on the thread

---

### Post by nothingspecial on 2012-12-06
> **Tibuda said:**
> Yes, but it is only on your post, not on the thread

Now it's on the thread.

---

### Post by LubosD on 2012-12-06
> **nerdopolis said:**
> There seems to be an early, relatively obscure, but active project called the darling project

[http://darling.dolezel.info/en/Darling;jsessionid=xzwrvtllkvxn15vmncg3ra4jr](http://darling.dolezel.info/en/Darling;jsessionid=xzwrvtllkvxn15vmncg3ra4jr)

Hi, thanks for spreading the word!

It is obscure because the project webpage is more of a diary / TODO list / whatever, which is logical given the fact that the project is in quite early stages and I'm the only one working on this. Well, except for the GNUstep guys, with GNUstep playing a pivotal role in the project.

Should anyone ever feel like helping out, I would be very grateful. No prior OS X programming experience is really neded, but may be helpful. Darling is my diploma thesis, so I'm not quitting anytime soon, but given the sheer extent of the task I've taken on, I won't have any quality results soon.

I have a lot of console apps working, but the real stuff comes with the GUI and all the Apple frameworks. But I do have a Hello Cocoa application working. See the images below for screenshots of an identical binary running on OS X and on Linux.

[IMG]http://www.dolezel.info/img/darling/helloworld-apple.png[/IMG]

[IMG]http://www.dolezel.info/img/darling/helloworld-dyld-gnustep.png[/IMG]

---

### Post by LubosD on 2012-12-06
> **forrestcupp said:**
> It would take them years and years to reverse engineer that to the point to where it would be usable, just like it did with Wine. It seems like there's not really a big enough demand for it to justify that much work. Even the Darling project that nerdopolis linked to wouldn't do any good because Darwin is just the very core components of MacOS X. You can't run Mac software on Darwin alone.

You're mistaken here. I'm not emulating Darwin only, though that's the most basic stuff that needs to/had to be done. Supporting console apps only woudn't make much sense.

And reverse engineering (as in dissassembling) proprietary Apple libs isn't needed that much. The documentation seems to be quite sufficient. I, however, did and do disassemble my own simple apps to analyze the compiler output (helpful for the dynamic loader and Objective-C support development).

---

### Post by forrestcupp on 2012-12-06
> **LubosD said:**
> 
I have a lot of console apps working, but the real stuff comes with the GUI and all the Apple frameworks. But I do have a Hello Cocoa application working. See the images below for screenshots of an identical binary running on OS X and on Linux.
Wow. So you're actually trying to implement the whole OS X environment? That would be amazing. It would especially be amazing if sometime down the road we were able to develop iOS apps in Linux.

---

### Post by LubosD on 2012-12-06
> **forrestcupp said:**
> Wow. So you're actually trying to implement the whole OS X environment? That would be amazing. It would especially be amazing if sometime down the road we were able to develop iOS apps in Linux.

Well, yeah. I am progressing quite fast, but if I want to have something semi-complete in this century, I'll need a few more team members :D

I have an outstanding C++ runtime issue that causes Apple's LLVM-GCC to generate empty output files - I know the reason, but need to find a reasonable workaround - but as soon as this gets fixed, you'll be able to compile apps for iOS on Linux. From console. No Xcode, just the compiler, but I guess this may be helpful too.

---

### Post by mythic97 on 2012-12-06
^I think you should call it vodka or ale to keep with naming thing

---

### Post by Jakin on 2012-12-06
Cider.

---

### Post by sdowney717 on 2012-12-07
Another way to think of this is use Google Chrome Remote Desktop.
You run the Mac machine inside the browser window. Works very well with win7 for me with streaming video and sound. And will work full screen.
It should work as I have read will work

> Chrome Remote Desktop is fully cross-platform.  Provide remote assistance to Windows, Mac and Linux users, or access your Windows (XP and above) and Mac (OS X 10.6 and above) desktops at any time, all from the Chrome browser on virtually any device, including Chromebooks.
[https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp)

---

### Post by forrestcupp on 2012-12-07
> **sdowney717 said:**
> Another way to think of this is use Google Chrome Remote Desktop.
You run the Mac machine inside the browser window. Works very well with win7 for me with streaming video and sound. And will work full screen.
It should work as I have read will work


[https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp)
Don't you actually have to have access to a Mac for that to work?

---

### Post by nerdopolis on 2012-12-07
> **LubosD said:**
> Hi, thanks for spreading the word!

It is obscure because the project webpage is more of a diary / TODO list / whatever, which is logical given the fact that the project is in quite early stages and I'm the only one working on this. Well, except for the GNUstep guys, with GNUstep playing a pivotal role in the project.

Should anyone ever feel like helping out, I would be very grateful. No prior OS X programming experience is really neded, but may be helpful. Darling is my diploma thesis, so I'm not quitting anytime soon, but given the sheer extent of the task I've taken on, I won't have any quality results soon.

I have a lot of console apps working, but the real stuff comes with the GUI and all the Apple frameworks. But I do have a Hello Cocoa application working. See the images below for screenshots of an identical binary running on OS X and on Linux.

[IMG]http://www.dolezel.info/img/darling/helloworld-apple.png[/IMG]

[IMG]http://www.dolezel.info/img/darling/helloworld-dyld-gnustep.png[/IMG]

Woah! That's pretty sweet. I think the best way to spread the word about this is by telling Phoronix...

---

### Post by sdowney717 on 2012-12-07
> **forrestcupp said:**
> Don't you actually have to have access to a Mac for that to work?

Yes, you do. I assume some people who want to run Mac programs have access to a mac computer, so it is just another way to do this relatively easily.

I have access to several win7 PC's and can operate both remotely at the same time. In fact I installed Ubuntu one on them and can use MS word saving files right to the cloud thru the Ubuntu PC running Chrome. 
I can also print using Google cloud print to my home printer when away from home.

It works very well. I can even stream Netflix.

---

### Post by Dragonbite on 2012-12-09
> **sdowney717 said:**
> Yes, you do. I assume some people who want to run Mac programs have access to a mac computer, so it is just another way to do this relatively easily.

I have access to several win7 PC's and can operate both remotely at the same time. In fact I installed Ubuntu one on them and can use MS word saving files right to the cloud thru the Ubuntu PC running Chrome. 
I can also print using Google cloud print to my home printer when away from home.

It works very well. I can even stream Netflix.

The idea behind the original question is if OS X applications work more easily and consistantly in Linux due to the Unix base than Windows then it could be beneficial to look at proprietary OS X applications rather than Windows.  

Applications like Dreamweaver or MS Windows for Mac available on Linux with a greater degree of certainty than the same running under WINE could be a benefit to Linux.  It may not be the same breadth of software titles as Windows has, but it is a large and growing number.

Something that makes Android Apps run on Linux would also be a benefit I guess, though it would be through something other than what would provide OS X applications to run on Linux.

---

### Post by Lars Noodén on 2012-12-09
Darling is getting a little more press:

[http://apple.slashdot.org/story/12/12/08/2330225/darling-run-apple-os-x-binaries-on-linux](http://apple.slashdot.org/story/12/12/08/2330225/darling-run-apple-os-x-binaries-on-linux)

---

### Post by 008bond on 2012-12-11
I think if you could get some of the multimedia apps from OSx running, that alone would be amazing and a hell of an achievement.

---

