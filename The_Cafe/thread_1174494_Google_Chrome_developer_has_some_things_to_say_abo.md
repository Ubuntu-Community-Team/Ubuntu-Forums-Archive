---
title: "Google Chrome developer has some things to say about Linux"
date: 2009-05-31
forum: The Cafe
---

### Post by jrusso2 on 2009-05-31
[http://arstechnica.com/open-source/news/2009/05/hands-on-google-chromium-browser-alpha-for-linux.ars](http://arstechnica.com/open-source/news/2009/05/hands-on-google-chromium-browser-alpha-for-linux.ars)

In an early discussion thread about the strategy for porting the Chrome user interface to Windows, Google Chrome developer Ben Goodger expressed frustration with Linux user interface toolkits and commented that the platform's lack of consistency makes it difficult to know what to target.

    In an update that was posted a month after the initial discussion, Chrome developer Evan Martin described the Linux port as a "511MB executable that brings up an empty window."

"First of all let me generally comment that this entire situation is a clusterf*ck. I am not happy with the technical constraints imposed by Linux and its assorted UIs on Chrome's UI and feature set," he wrote. "There isn't dominant consensus around toolkit and HIG, there seems to be variance in commonly used software as to how it's constructed and what it matches, and I've not heard anyone glow about how they can create the coolest looking UIs with GTK."

For those who are unaware, Ben Goodger is a former employee of Mozilla and used to be the lead developer of the Firefox project. In his work on the Chrome browser he is drawing from his extensive experiences with the Firefox codebase. In his comment in the discussion thread, he suggests that Mozilla's approach--where a single user interface toolkit is made to reflect the native look and feel of each platform--is always going to produce imperfect results.

---

### Post by Darkhack on 2009-05-31
I've been following Ben Goodger's comments for a while now.  I don't think anyone should take him seriously.  He's a complete toolbag.  In fact, I'm surprised Google hasn't fired him.  He's been nothing but a nuisance to the project and he blames everyone but himself.

[LIST]
[*]Didn't have the foresight to consider writing Chrome in a cross platform way.  Only after it was heavily developed for Windows was it decided that it would also be ported to Mac and Linux.
[*]Reinvented the wheel with Skia.  Instead of using the existing WebKit ports (Windows, Qt, GTK+, Cairo, etc) he decided to make their own graphics toolkit and port WebKit to that.  It's almost an identical clone to Cairo.
[*]Had it written so heavily for Windows they even ran parts of the Windows kernel through a disassembler to be able to figure out how to use some undocumented features.
[*]Reinvented the wheel with V8.  WebKit had been working on SquirrelFish and SFX, but Goodger ignored that in favor of writing a new one for scratch.  For the record, SFX is on-par with V8 and in some benchmarks surpasses it.
[*]To say that Chrome completely ignores the Windows HIG is an understatement.  He goes to great lengths to give Chrome a "unique look and feel" and then bitches when it becomes harder to port.
[/LIST]

Basically Goodger screwed the whole project.  Rather than admit to this, he rather blame the development tools.  The Linux community is actually handpicking this quote, but Goodger has been known to be just has harsh to Windows and Mac when things don't go his way.  Goodger is also the reason Chrome has taken so long to receive extension support.  To put this in perspective, Christian Dywan, the developer of Midori was able to implement extension support faster than the entire Chrome team.

---

### Post by jrusso2 on 2009-05-31
Interesting comments.  I had not heard what he said about Windows and OS X.

---

### Post by Darkhack on 2009-05-31
I'm trying to digg up some quotes on him.  Goodger has an obvious bias (which he has admitted in an interview) against Linux.  He claims to be a Mac user at home but he obviously also does a lot with Windows.

Here's more of him trashing Linux: [http://groups.google.com/group/chromium-dev/browse_thread/thread/b89ab99a0c848b89/f3507e2ded99b354?#f3507e2ded99b354](http://groups.google.com/group/chromium-dev/browse_thread/thread/b89ab99a0c848b89/f3507e2ded99b354?#f3507e2ded99b354)

I'm trying to find more quotes of him where he shows his true colors.  He tends to be more defensive of Apple than the other platforms.  The thing is that you notice how he casually brushes off the fact that the Mac port has to be almost completely rewritten from scratch but that using Qt or GTK+ would "speak with a foreign accent" and is an atrocity to mankind and the universe would implode if Chrome was made in a cross platform way.

He criticized Windows for having to disassemble the kernel and he later criticized Mac for making a multi-process design more difficult than it needed to be.  I'm having trouble finding those quotes now, but if someone else can link to them, you'd see how whiny he can get.

---

### Post by Script Warlock on 2009-05-31
if thats his attitude towards us then throw him to the dungeon where dragons and gremlins live, he's LAZY...
he's not human he is a robot....
robots are slave for humans....

---

### Post by FuturePilot on 2009-05-31
> **Darkhack said:**
> 
[LIST]
[*]To say that Chrome completely ignores the Windows HIG is an understatement.  He goes to great lengths to give Chrome a "unique look and feel" and then bitches when it becomes harder to port.
[/LIST]


I think this is the biggest problem right here. The whole interface is heavily Windows centric. But even then it still has its own unique look and feel. Trying to port a heavily customized interface like that to other platforms isn't going to be easy, especially if it relies on something that is unique to a particular OS. Did he expect it to be easy? If you look at all the other programs that are cross platform, they all have an interface that is relatively identical across all OSes. I'm not sure how relevant "too many toolkits" is anymore. There's really only 2 that are mainly used. GTK and Qt.

---

### Post by MikeTheC on 2009-05-31
Sounds like another idiot programmer to me.

I'm mostly a Mac person. But if I was developing an app with the intention of making it cross-platform, I'd do what I needed to do to get it equal everywhere and not make it a complete kludge.

Have you folks seen or used Chrome? (I'm sure you have, I'm just sayin'...) The thing is very non-standard in a lot of respects. I'll give it props for some of it's features, but Firefox is still my daily driver and is going to be for the foreseeable future.

---

### Post by MikeTheC on 2009-05-31
> **Script Warlock said:**
> if thats his attitude towards us then throw him to the dungeon where dragons and gremlins live
+1

BTW, Script Warlock, don't hold back. Tell us what you *really* think! :)

---

### Post by mohitchawla on 2009-05-31
> **Darkhack said:**
> I've been following Ben Goodger's comments for a while now.  I don't think anyone should take him seriously.  He's a complete toolbag.  In fact, I'm surprised Google hasn't fired him.  He's been nothing but a nuisance to the project and he blames everyone but himself.

[LIST]
[*]Didn't have the foresight to consider writing Chrome in a cross platform way.  Only after it was heavily developed for Windows was it decided that it would also be ported to Mac and Linux.
[*]Reinvented the wheel with Skia.  Instead of using the existing WebKit ports (Windows, Qt, GTK+, Cairo, etc) he decided to make their own graphics toolkit and port WebKit to that.  It's almost an identical clone to Cairo.
[*]Had it written so heavily for Windows they even ran parts of the Windows kernel through a disassembler to be able to figure out how to use some undocumented features.
[*]Reinvented the wheel with V8.  WebKit had been working on SquirrelFish and SFX, but Goodger ignored that in favor of writing a new one for scratch.  For the record, SFX is on-par with V8 and in some benchmarks surpasses it.
[*]To say that Chrome completely ignores the Windows HIG is an understatement.  He goes to great lengths to give Chrome a "unique look and feel" and then bitches when it becomes harder to port.
[/LIST]

Basically Goodger screwed the whole project.  Rather than admit to this, he rather blame the development tools.  The Linux community is actually handpicking this quote, but Goodger has been known to be just has harsh to Windows and Mac when things don't go his way.  Goodger is also the reason Chrome has taken so long to receive extension support.  To put this in perspective, Christian Dywan, the developer of Midori was able to implement extension support faster than the entire Chrome team.

Thanks for the informative post. I almost had a sinking feeling when I read the title post !

---

### Post by ghindo on 2009-05-31
Interesting posts, Darkhack - I didn't know about all of this non-standard, reinventing the wheel business that Google is doing with Chrome/Chromium.  I like Chrome for its simplicity and speed, but between the Linux difficulties, the data mining, and the lack of open video support, I think I may just stick with Firefox.  

I saw this story on /. earlier today, and somebody commented asking why Google didn't just use Qt for Chrome, as it would allow easy cross-platform porting.  I guess we now have a bit of a guess.

---

### Post by Mr. Picklesworth on 2009-05-31
Blatant duplicate of my comment on Ars:


Regarding the continual "I hate building for Linux because I have to figure out different toolkits" complaint, I feel I need to explain something really obvious.

The kernel does not define the desktop environment. If all you care about is making a program run on a kernel, you have already failed. When you are developing high level software, the kernel does not exist.

GNOME and KDE are modular, portable free software platforms. You target those. Now, you can either build Chromium for GNOME, or you can build it for KDE. Or, if you feel really generous, you can do both! One handy detail is they are compatible on some lower levels by being built on the same open source ecosystem. There, isn't that easy?

This fellow, in his complaining, failed to realize that Google themselves have a troublesome Linux platform: Android. Does porting to the Linux kernel mean we have to support Android and its GUI toolkit? (Ooooh the pain! The trouble! Soo many choices! I'm never writing for Linux again because of Google and their extra platform I have to choose between!)

---

### Post by -grubby on 2009-05-31
> **FuturePilot said:**
> The whole interface is heavily Windows centric.

Please tell me how the interface looks "heavily Windows centric."

I also don't think the problem is just choosing/implementing the interface.

Take a look at Opera's Linux packaging, for one: [http://www.opera.com/browser/download/?os=linux-i386&ver=9.64&local=y](http://www.opera.com/browser/download/?os=linux-i386&ver=9.64&local=y)

That's for one version. On one architecture. They undoubtedly have some way to automate this, but they still have to add a new layer of automation every time the packaging system gets updated. Linux doesn't seem to get backwards compatibility.

I can run stuff from the Windows 95-era in Windows 7. Try doing that in Linux.

---

### Post by Tibuda on 2009-05-31
> **grubby- said:**
> I can run stuff from the Windows 95-era in Windows 7.Sorry, but there are some old games I can't even play in XP.

Packaging is not the problem either. They don't have to do it. Instead, they can just have their own binary installer (like most Windows software) or just compress the binaries in a popular archive format (like Mozilla does).

---

### Post by Hells_Dark on 2009-05-31
By the way, chromium really looks good now.
(The animated tabs & co are here&#8230;)

---

### Post by jrusso2 on 2009-05-31
> **grubby- said:**
> Please tell me how the interface looks "heavily Windows centric."

I also don't think the problem is just choosing/implementing the interface.

Take a look at Opera's Linux packaging, for one: [http://www.opera.com/browser/download/?os=linux-i386&ver=9.64&local=y](http://www.opera.com/browser/download/?os=linux-i386&ver=9.64&local=y)

That's for one version. On one architecture. They undoubtedly have some way to automate this, but they still have to add a new layer of automation every time the packaging system gets updated. Linux doesn't seem to get backwards compatibility.

I can run stuff from the Windows 95-era in Windows 7. Try doing that in Linux.

This was the example I used in another thread.

---

### Post by jrusso2 on 2009-05-31
> **danielrmt said:**
> Sorry, but there are some old games I can't even play in XP.

Packaging is not the problem either. They don't have to do it. Instead, they can just have their own binary installer (like most Windows software) or just compress the binaries in a popular archive format (like Mozilla does).

HOw come I can't run Firefox 3 on my older version of Linux?

It won't run on them or even start.

---

### Post by t0p on 2009-05-31
> **grubby- said:**
> 
I can run stuff from the Windows 95-era in Windows 7.

> **jrusso2 said:**
> HOw come I can't run Firefox 3 on my older version of Linux?

It won't run on them or even start.

Wow, you guys are *intense*!  Running 14 years old software on a modern OS... or modern software on an aged OS... why?  Other than for geek props...

---

### Post by jrusso2 on 2009-05-31
> **t0p said:**
> Wow, you guys are *intense*!  Running 14 years old software on a modern OS... or modern software on an aged OS... why?  Other than for geek props...

By older I mean two years not 14

---

### Post by Xbehave on 2009-05-31
> **jrusso2 said:**
> HOw come I can't run Firefox 3 on my older version of Linux?

It won't run on them or even start.
Because it relies on libraries, if you take a [statically linked program]("http://www.opera.com/browser/download/?os=linux-i386&ver=9.64&local=y") you could easily run it on any 2.6 kernel (probably any 2.x kernel)

grubby your either a troll or a tool.
> Take a look at Opera's Linux packaging, for one: [http://www.opera.com/browser/downloa...r=9.64&local=y](http://www.opera.com/browser/downloa...r=9.64&local=y)
There are basically 2 versions over 5 years, there are clearly just 2 actual files with clever links and nice debs so that the metadata is correct! [windows]("http://www.opera.com/browser/download/?os=windows&ver=9.64&local=y") has 3 versions :O. The linux userspace API is very stable and so quite backwards compatible. The only thing that is less stable are the usespace libraries, however changes that only require 1 recompile in 5 years is hardly excessive.

Speaking of trolls, I've always taken anything Ben says with a pinch of salt he seams to criticize others a lot yet chrome on windows is rife with bugs! Chrome developers complaining about a lack of HIG just takes the biscuit though, chrome doesn't follow any trends on windows and is very light on GUI anyway. Neither Mozilla(gtk) nor Opera(qt) waste time complaining about how the available toolkits suck. And it's a trivial choice given that
1) qt apps run fine on gnome/any DE (even if gnome users are too dumb to theme them and complain they look bad)
2) gtk apps run fine on kde/any DE
3) webkit is already ported to both qt and gtk
4) the only GUI that needs to be written is chromes lightweight interface which is very none standard anywhere
5) all modern WM obey several standards so if google want to do their silly tabs as window decoration trick they just have to follow them

---

### Post by Polygon on 2009-05-31
yeah it seems a bit weird that he is complaining about gnome HIG standards when chrome is a black sheep when it comes to Microsoft's own HIG and interface practices. I think they even use their own close/minimize/expand buttons, lol

---

### Post by toupeiro on 2009-05-31
> **grubby- said:**
> 

I can run stuff from the Windows 95-era in Windows 7. Try doing that in Linux.

I've taken source code from an application written for a circa 1990's SGI and compiled it on a brand spanking new 64-bit AMD box running RHEL5 and it works flawlessly.  For the record, thats a cross-hardware and software platform migration.  Try doing that with windows...

As for Chrome, I *was* excited about a linux port, but this programmer is definitely more into himself than anything else.  He can keep google chrome.

---

### Post by lisati on 2009-05-31
> **grubby- said:**
> I can run stuff from the Windows 95-era in Windows 7. Try doing that in Linux.
There's one piece of software I developed on a Windows 98 machine that loses some of its functionaility because of differences I did not anticipate with XP. Enough said?

---

### Post by jrusso2 on 2009-05-31
> **toupeiro said:**
> I've taken source code from an application written for a circa 1990's SGI and compiled it on a brand spanking new 64-bit AMD box running RHEL5 and it works flawlessly.  For the record, thats a cross-hardware and software platform migration.  Try doing that with windows...

As for Chrome, I *was* excited about a linux port, but this programmer is definitely more into himself than anything else.  He can keep google chrome.

How many regular users are capable of recompiling an app; from one platform to another?  Lets get real.

---

### Post by Tibuda on 2009-05-31
> **jrusso2 said:**
> How many regular users are capable of recompiling an app; from one platform to another?  Lets get real.

Or how many applications have the source code available?

---

### Post by y6FgBn)~v on 2009-05-31
I don't see Googles logic in keeping someone on a project who is either unable and or unwilling to do the job.

---

### Post by toupeiro on 2009-05-31
> **jrusso2 said:**
> How many regular users are capable of recompiling an app; from one platform to another?  Lets get real.

typing make install?  It took me 5 minutes.  3 seconds of that five minutes was typing.  C is C...

---

### Post by happysmileman on 2009-05-31
> **jrusso2 said:**
> How many regular users are capable of recompiling an app; from one platform to another?  Lets get real.

How many regular users want to use 14 year old software? Let's get real.

---

### Post by happysmileman on 2009-05-31
> **grubby- said:**
> I can run stuff from the Windows 95-era in Windows 7. Try doing that in Linux.

There are plenty of Windows XP apps that don't work in Vista, so I wouldn't really use Windows as a shining example of backwards compatability anymore.

Windows 7 basically uses a Virtualised copy of Windows XP to run older programs, and if that counts then I can run (and have run) Windows 95 programs in Linux using a virtual machine.

---

### Post by Polygon on 2009-05-31
also, try running anything that requires ipx libraries (read, really old games that you want to LAN with) in windows vista or 7. Oops! microsoft removed those libraries. I guess they could not afford a few more KB of drivers in an already 8+ gb install.

---

### Post by Xbehave on 2009-05-31
> Or how many applications have the source code available?
There are 3 types of app:
open source -> just recompile 
closed source -> just use a static version of the app
leaches, closed source but using open source libraries -> these will not work

Seriously backwards compatibility is mostly irrelevant in an open source eco system, just move forward! Only 2 types of people care about backwards compatibility, trolls and people who consider linux as another way to run closed apps!

---

### Post by etnlIcarus on 2009-06-01
> **Darkhack said:**
> I've been following Ben Goodger's comments for a while now.  I don't think anyone should take him seriously.  He's a complete toolbag.  In fact, I'm surprised Google hasn't fired him.  He's been nothing but a nuisance to the project and he blames everyone but himself.

[LIST]
[*]Didn't have the foresight to consider writing Chrome in a cross platform way.  Only after it was heavily developed for Windows was it decided that it would also be ported to Mac and Linux.
[*]Reinvented the wheel with Skia.  Instead of using the existing WebKit ports (Windows, Qt, GTK+, Cairo, etc) he decided to make their own graphics toolkit and port WebKit to that.  It's almost an identical clone to Cairo.
[*]Had it written so heavily for Windows they even ran parts of the Windows kernel through a disassembler to be able to figure out how to use some undocumented features.
[*]Reinvented the wheel with V8.  WebKit had been working on SquirrelFish and SFX, but Goodger ignored that in favor of writing a new one for scratch.  For the record, SFX is on-par with V8 and in some benchmarks surpasses it.
[*]To say that Chrome completely ignores the Windows HIG is an understatement.  He goes to great lengths to give Chrome a "unique look and feel" and then bitches when it becomes harder to port.
[/LIST]

Basically Goodger screwed the whole project.  Rather than admit to this, he rather blame the development tools.  The Linux community is actually handpicking this quote, but Goodger has been known to be just has harsh to Windows and Mac when things don't go his way.  Goodger is also the reason Chrome has taken so long to receive extension support.  To put this in perspective, Christian Dywan, the developer of Midori was able to implement extension support faster than the entire Chrome team.

I was LMAO at this post. Excellent pwning, Darkhack.

---

### Post by sanderella on 2009-06-02
Am I the only one who likes Google Chrome because it greys out the adverts?;)

---

### Post by omar8 on 2009-06-02
> **Darkhack said:**
> I've been following Ben Goodger's comments for a while now.  I don't think anyone should take him seriously.  He's a complete toolbag.  In fact, I'm surprised Google hasn't fired him.  He's been nothing but a nuisance to the project and he blames everyone but himself.

[LIST]
[*]Didn't have the foresight to consider writing Chrome in a cross platform way.  Only after it was heavily developed for Windows was it decided that it would also be ported to Mac and Linux.
[*]Reinvented the wheel with Skia.  Instead of using the existing WebKit ports (Windows, Qt, GTK+, Cairo, etc) he decided to make their own graphics toolkit and port WebKit to that.  It's almost an identical clone to Cairo.
[*]Had it written so heavily for Windows they even ran parts of the Windows kernel through a disassembler to be able to figure out how to use some undocumented features.
[*]Reinvented the wheel with V8.  WebKit had been working on SquirrelFish and SFX, but Goodger ignored that in favor of writing a new one for scratch.  For the record, SFX is on-par with V8 and in some benchmarks surpasses it.
[*]To say that Chrome completely ignores the Windows HIG is an understatement.  He goes to great lengths to give Chrome a "unique look and feel" and then bitches when it becomes harder to port.
[/LIST]

Basically Goodger screwed the whole project.  Rather than admit to this, he rather blame the development tools.  The Linux community is actually handpicking this quote, but Goodger has been known to be just has harsh to Windows and Mac when things don't go his way.  Goodger is also the reason Chrome has taken so long to receive extension support.  To put this in perspective, Christian Dywan, the developer of Midori was able to implement extension support faster than the entire Chrome team.

I don't think he should be fired at all.
[LIST]
[*]From the start of the project it was decided that each port of Google Chrome would use the native toolkit - which has worked out very well for both Mac and Windows it appears by the great performance and great reviews it seems to have been recieving.
[*]There isn't anything wrong with reinventing the wheel and you never know, because of this we might end up with a new graphics toolkit that everyone prefers - it is opensource so you will benefit even if it is minimal.
[*]This isn't even a point to argue against, infact this is potentially a benefit as it shows Google is willing to optimise each port with great detail.
[*]Chrome looking how it does on Windows means nothing since they intend to start from scratch anyway.
[/LIST]
The funny thing is, we need developers like him who will speak their opinion when things don't seem to work right, it is because of people like him that Windows, Mac and Linux have ended up with such great APIs. When you see something that could be improved it is better to state that there is something wrong rather than keep your mouth shut and let the issue stay.

---

### Post by blackened on 2009-06-02
> **omar8 said:**
> The funny thing is, we need developers like him who will speak their opinion when things don't seem to work right, it is because of people like him that Windows, Mac and Linux have ended up with such great APIs. When you see something that could be improved it is better to state that there is something wrong rather than keep your mouth shut and let the issue stay.

Agreed, though there is a thin, fuzzy, and highly subjective line between someone who speaks their mind when they think something is awry and drama queens who can't keep their mouths shut long enough to hear the opinions of others and/or just generally enjoy causing problems. 90% of the people I work with fall into the latter category. Which is he?

---

### Post by gnomeuser on 2009-06-02
> **Darkhack said:**
> I've been following Ben Goodger's comments for a while now.  I don't think anyone should take him seriously.  He's a complete toolbag.  In fact, I'm surprised Google hasn't fired him.  He's been nothing but a nuisance to the project and he blames everyone but himself.


His complaint is that there is no uniform API to code a GUI for and unsurprisingly he is right. If he elects to do the Linux port for GTK+ the QT crowd gets pissy and vice virsa. Then there's all the other millions of toolkits they could pick. It is impossible for them to get a native look and feel on Linux regardless of what they elect to do. His complaint that we are making it hard for ISVs is absolutely valid.

Chrome and others are left with a number of unappealing options:
1) Pick one toolkit and piss off everyone else.
2) Attempt a uniform look adapter like Mozillas XUL, which will never look like it fits in and it is slow.
3) doing a separate gui for each toolkit, which adds to the support burden.

There is no good option for them, we suck and we should admit it. We need more unification and we need to stop making life hard for companies like Google who actually want to port their application to Linux.

> 
[LIST]
[*]Didn't have the foresight to consider writing Chrome in a cross platform way.  Only after it was heavily developed for Windows was it 
decided that it would also be ported to Mac and Linux.
[*]Reinvented the wheel with Skia.  Instead of using the existing WebKit ports (Windows, Qt, GTK+, Cairo, etc) he decided to make their own graphics toolkit and port WebKit to that.  It's almost an identical clone to Cairo.
[*]Had it written so heavily for Windows they even ran parts of the Windows kernel through a disassembler to be able to figure out how to use some undocumented features.
[*]Reinvented the wheel with V8.  WebKit had been working on SquirrelFish and SFX, but Goodger ignored that in favor of writing a new one for scratch.  For the record, SFX is on-par with V8 and in some benchmarks surpasses it.
[*]To say that Chrome completely ignores the Windows HIG is an understatement.  He goes to great lengths to give Chrome a "unique look and feel" and then bitches when it becomes harder to port.
[/LIST]


Let's do thes one by one:

1. All indications is that the code was written to live up to a number of standards, they have unit and other manners of testing. The code except for the parts that need to be separate such as the security model since there is no crossplatform way of doing the level of separation they desired should be very portable. It would be untrue to say that they never considered a port. On launch day I got the kind message that they were working on a Linux version, they could have easily instructed people to use Wine or refused a port. We are around 1% of the market, of course they are going to complete the Windows port first.

2. I am unaware of their decision making with regards to SKIA, there is likely a good reason for this but till a developer is asked as to this decision I think it's largely unfair to call them names due to their choice of toolkit on separate platforms. I think they had the same problem as on Linux, there are many toolkits to pick from and they had to settle on one. 

3. The GUI code is tied to your toolkit and we already established that you cannot get true integration that is cross platform with one toolkit. Aside that naturally the security model needs to have certain specializations as the underlying systems doesn't have a unified model (like OS X's sandboxing API), hell in Linux we can't even agree on one method of doing this and Windows doesn't allow for the level of separation they wanted so they needed to do deep inspection of the kernel.

4. V8 was at the time it came out outperforming every Javascript engine on the market, it continues to get faster. The reason to develop a brand new engine was to develop a Javascript engine that would not just be fast now but we well suited for the future with JS applications getting more complex. None of the existing implementations at the time, nor now outperform V8 for those very complex cases (see the V8 page and their benchmark suite, it's open and I encourage people to run it against other engines and review the tests). It has also proven very well suited for additional performance work and is with the release of Chrome 2 50% faster in many cases.

You do not cite data for your claim that SFX is faster especially for the cases V8 is targeting. V8 is a great piece of engineering, also you seem to be under the impression that Ben did the work, it was in reality done by a small group of developers stationed in my very own Århus, Denmark in connection with the university here where Google has an office.

5. see 1-4.

And regardless all of that does not at all relate to the truth of his actual complaint that we offer no unified toolkit for Linux and that the camps are so split that regardless of what he does he will get grief. It's basically just avoiding the truth of what Ben is saying, we suck. Rule one about suckage is definitely acknowledging that suckage exists, not going on personal attacks on the person making the claim.

> 
Basically Goodger screwed the whole project.  Rather than admit to this, he rather blame the development tools.  The Linux community is actually handpicking this quote, but Goodger has been known to be just has harsh to Windows and Mac when things don't go his way.  Goodger is also the reason Chrome has taken so long to receive extension support.  To put this in perspective, Christian Dywan, the developer of Midori was able to implement extension support faster than the entire Chrome team.

Ben is a talented programmer, he is also right when he complains about the tools we present on Linux. There are certain things that are easier in doing a port to Linux such as the security model where he can use tools like SELinux and avoid having to examine the bowls of the kernel (sadly we can't even agree in Linux with regards to using SELinux) but for his actual complaint regarding the toolkits, we do not offer an obvious choice that integrates well with every desktop. 

Your comparison with Midori is also dishonest, Midori does not implement a security model akin to what Chrome does making it significantly easier to both code and port, also significantly less secure by design (if you claim otherwise, go see the interviews with the participates of the last pwn2own contest, Chrome was the only browser to remain uncompromised largely thanks to it's design according to leading security professionals). 

The same goes for the extension layer, they could have thrown together a quick extension layer but instead they elected to do the right thing and work with Mozilla to develop a way that is truly easier and fixes a number of the problems with current plugin models such as having to restart the browser. Now you have an easy to work with layer that is programmable in Javascript and CSS. Much easier to get into and using a very common language. Additionally this extension model should allow us to write a plugin once and have it deployed regardless of future versions of the browser.

Good design takes time, both in porting and in developing. It does however pay off. We can either help make those tools available to ISVs and not split our community down the middle based on tool preference or we can continue the path we are on now. Even ISVs that do share code under OSI approved licenses have a hard time serving us, which is definitely a sign that we are doing something wrong. 

Ben is right, we need to do better instead engaging in ad hominem attacks on the person who points it out to us with a real world example of our suckage.

---

### Post by Polygon on 2009-06-02
what other major toolkits are there besides qt and gtk? There are random other ones like wxwidgets and such, but all of those are ment to end up looking like qt and gtk.

---

### Post by Random-penguin on 2009-06-02
Gnomeuser, you made some valid points but surely Linux is about freedom, choice..etc 

Why should one toolkit be chosen over others for commercial reasons???

---

### Post by gnomeuser on 2009-06-02
> **Random-penguin said:**
> Gnomeuser, you made some valid points but surely Linux is about freedom, choice..etc 

Why should one toolkit be chosen over others for commercial reasons???

Not for purely commercial reasons, to define the platform and let developers do their work. We really have a problem defining what the Linux platform is, underneath we might be lucky to have LSB but that is a poorly designed standard. Above that we have nothing (there is Portland but that is a poor compromise that accomplices nothing).

We can have separate toolkits, that is how progress is made. Those good changes could then be merged back into the one true platform blessed toolkit or a major framework change can be announced once the APIs are solid and we have porting guides. There are way to avoid the problems of uniformity while gaining the benefits and retaining the means of exploration.

I hate that every time someone complains about the platform being undefined it immediate complaint is about freedom. Who is taking your freedom away by defining a standard? Can you not go out and do your work however you please using what ever tools you like because we created one standard of tools and APIs for developers to use?

Why do we need a ton of toolkits that must be treated equally. GTK+, QT, TK, EPL, SWIG, SWF (WinForms) and countless others. It's time to grow the up, grow a pair and define a full platform.

This also extends beyond toolkits, what about things like security APIs, we want applications to expand into using sandboxing more like what Chrome does. it good for our users and our platform that we have a reputation for safety. But we have SELinux, AppArmor, TOYMOTO, SMACK and PaX (I hope I got all those names right, security developers pick the strangest names) all contending in some form to be the Security framework of choice. Just pick one and let the rest be research projects and specialty deployments, build a good set of APIs on top of that one framework to easily do things.

We have properly 10 libraries to do the same thing for pretty much any task you can imagine. Which one should we use? 

The platform needs to be defined.

---

### Post by Random-penguin on 2009-06-02
But linux is **[COLOR=black]more[/COLOR]** than compatibility for the sakes of compatibility. It is about freedom of choice etc. Ok one choice of toolkit would possibly kick off development with the wider computing community, (ie Google), but why should we limit ourselves to that. Choice is one of our greatest assets!

---

