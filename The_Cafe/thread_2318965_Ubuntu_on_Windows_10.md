---
title: "Ubuntu on Windows 10"
date: 2016-03-30
forum: The Cafe
---

### Post by grahammechanical on 2016-03-30
[http://blog.dustinkirkland.com/2016/03/ubuntu-on-windows.html](http://blog.dustinkirkland.com/2016/03/ubuntu-on-windows.html)

Whatever next! Were rumours of this project the source of rumours of Microsoft buying Canonical?

Regards.

---

### Post by vasa1 on 2016-03-30
I don't know what to say. I don't even know which emoticon is appropriate. If true, that would remove my puzzlement over why [the Canonical version of LibreOffice doesn't appear to have "certain" fonts]("http://ubuntuforums.org/showthread.php?t=2318372&p=13461524#post13461524").

---

### Post by montag dp on 2016-03-30
It makes me feel uneasy, I'm not really sure why. I guess I just don't trust Microsoft's motives about all this open source stuff.

---

### Post by bashiergui on 2016-03-30
[http://www.hanselman.com/blog/DevelopersCanRunBashShellAndUsermodeUbuntuLinuxBinariesOnWindows10.aspx](http://www.hanselman.com/blog/DevelopersCanRunBashShellAndUsermodeUbuntuLinuxBinariesOnWindows10.aspx)

> Today at BUILD in the Day One keynote Kevin Gallo announced that you can now run "Bash on Ubuntu on Windows." This is a new developer feature included in a Windows 10 "Anniversary" update (coming soon). It lets you run native user-mode Linux shells and command-line tools unchanged, on Windows. After turning on Developer Mode in Windows Settings and adding the Feature, run you bash and are prompted to get Ubuntu on Windows from Canonical via the Windows Store

edit: grahammechanical beat me to it: [http://ubuntuforums.org/showthread.php?t=2318965](http://ubuntuforums.org/showthread.php?t=2318965)

---

### Post by bashiergui on 2016-03-30
It's not April 1 yet, right? 

This must be Ubuntu's version of cygwin. I can't figure out how it would be done technically.

---

### Post by cariboo on 2016-03-30
Merged two similar threads

---

### Post by mikodo on 2016-03-31
I see it as boon to Ubuntu and I guess Linux in general.

The communities might, want to brace themselves for a bunch of newbs asking questions.

As far as fearing it individually, I am sure there will be lots of distros that will shun this due to philosophical Floss principles. 

Linux is still open-source and will continue to survive even if, Microsoft wants to lay down and marry it.

---

### Post by stevecook on 2016-03-31
[FONT=Ubuntu]I don't like it.[/FONT]
[FONT=Ubuntu]
At all.[/FONT]
[FONT=Ubuntu]
I also don't care if that's regarded by some as an overreaction.

Form what i have read, thus far, this will run Ubuntu Linux inside MS Windows. It wont be a virtual Linux, it will be an *actual* Ubuntu Linux running inside MS Windows due to Microsoft having recently and quietly introduced Linux subsystems in a new Windows 10 Redstone build.
[/FONT]
[FONT=Ubuntu]My first thoughts are that this is just another way in which Cannonical are trying to monetise Ubuntu. That, in itself, does not cause me any intrinsic concerns since there are plenty of Linux distros whose philosophy is strictly the opposite of that. It's why I left Ubuntu with the advent of Unity and all of the Amazon nonsense and it is why I came back with the rebirth of Gnome 2 via Ubuntu Mate, as well as Canonical ditching the default Amazon stuff.[/FONT]

[FONT=Ubuntu]However, by throwing their lot in with Microsoft, Cannonical are basically acting as scabs (an old British term used to describe when some workers continued to go into work when all of their comrades were out on strike, thus weakening the strike) on the rest of the entire Linux eco-system. By allowing Microsoft to gain access to and so provide to their own customers under their own MS brand, all of the Linux world, they get all of the long term benefits.
[/FONT]
[FONT=Ubuntu]This will do to the Linux world, potentially, what was done to the Liberal Democrats when they teamed up with the Tories. Short term gains for Cannonical will be overwhelmed by long term losses to the Linux eco-system. In short, this is a *very* bad thing for the wider Linux world.
[/FONT]
[FONT=Ubuntu]If this really is what, on first reading, it appears to be, I am leaving Ubuntu and this time it will for good. I hope I am wrong on this and will be the first to admit it if so. But, the above is my understanding so far.[/FONT]

---

### Post by buzzingrobot on 2016-03-31
> **bashiergui said:**
> It's not April 1 yet, right? 

This must be Ubuntu's version of cygwin. I can't figure out how it would be done technically.

It's not a Cygwin-like approach.  Seems to translate Linux system calls to equivalent Windows calls, more than a bit like WINE does.

There are developers who use both Windows and Linux tools, or who want/need to.  I.e, run Windows development tools on Windows that "talk" to Linux back ends, for eventual deployment to, say, Azure. I think Microsoft hopes this will be cleaner, hence, more attractive, than a VM.  Think corporate developers who have to use Windows but who are paid to build things that run on the Linux servers their corporation depends on.

Sustaining a developer community is important to companies like Microsoft an Apple because they need independent developers and vendors to push apps and other software for the increasingly closed ecologies those corporations are betting their futures on. This move is an effort to keep those folks working on Windows. It's really something of an acknowledgement of the role Linux plays.

E.g., MS also talked about bots and an expanded Cortana yesterday, and showed off a bot apparently jumping into a Twitter chat and making hotel reservations.  For that kind of world to happen, Microsoft needs people to build bots, etc., and the back ends that make them possible, on all kinds of platforms. For example,selling this kind of tech to hotel chains that run their reservation systems on Linux.

---

### Post by buzzingrobot on 2016-03-31
> **stevecook said:**
> [FONT=Ubuntu]By allowing Microsoft to gain access...[/FONT][FONT=Ubuntu].[/FONT]

Since Linux is open source, I think Microsoft could have easily done this without Canonical's cooperation or involvement. 

That they did secure Canonical's involvement seems to me a rather explicit acknowledgement that Linux is a serious player for Microsoft's customers and that Microsoft has decided to accommodate those customers, rather than follow the Ballmeresque fantasy that everyone will use Windows for everything.

---

### Post by RichardET on 2016-03-31
I think the real loser is VMWare - suddenly does one really need it anymore?

---

### Post by montag dp on 2016-03-31
So, would this allow me to compile executables for Windows using GCC (without MinGW/Cygwin)?  If so, it would actually be quite useful to me, despite my misgivings. I'm guessing it would still produce Linux binaries, like running Linux in a VM.

---

### Post by Xelort on 2016-03-31
> **RichardET said:**
> I think the real loser is VMWare

> **montag_dp said:**
> despite my misgivings 


[https://en.wikipedia.org/wiki/Embrace,_extend_and_extinguish](https://en.wikipedia.org/wiki/Embrace,_extend_and_extinguish)

---

### Post by grahammechanical on 2016-03-31
It is wubi from the dark side of the force. :)

---

### Post by RichardET on 2016-03-31
> **Xelort said:**
> 

That's not my quote.

---

### Post by Xelort on 2016-03-31
Sorry, bad copy/paste.

---

### Post by RobGoss on 2016-03-31
Hello everyone, I was hoping someone here could explain what exactly does this mean[https://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/?utm_source=ubunteu&utm_medium=url_shortner&utm_term=RBOWP7&utm_campaign=shortner]("https://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/?utm_source=ubunteu&utm_medium=url_shortner&utm_term=RBOWP7&utm_campaign=shortner")

I'm trying to figure out is this just a command line thing within Windows? Or will Windows users be able to run Ununtu within Windows interface. Thanks for any insight on this...... I guses Microsoft see how great Ubuntu really is now.

---

### Post by slickymaster on 2016-03-31
> **RobGoss said:**
> Hello everyone, I was hoping someone here could explain what exactly does this mean[https://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/?utm_source=ubunteu&utm_medium=url_shortner&utm_term=RBOWP7&utm_campaign=shortner]("https://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/?utm_source=ubunteu&utm_medium=url_shortner&utm_term=RBOWP7&utm_campaign=shortner")

Merged with this thread, which address your query.

---

### Post by grahammechanical on 2016-03-31
A discussion between those who know on Channel 9 Build 2016.

[https://channel9.msdn.com/Events/Build/2016/C906](https://channel9.msdn.com/Events/Build/2016/C906)

More accurately called Bash on Ubuntu On Windows 10. No Linux kernel. Bash on a Ubuntu root file system. No GUI stuff. Not Ubuntu Desktop but the Ubuntu that is for the cloud and for MAAS.

Regards

---

### Post by deadflowr on 2016-03-31
WINE in reverse?

---

### Post by bashiergui on 2016-03-31
> **RichardET said:**
> I think the real loser is VMWare - suddenly does one really need it anymore?Enterprises use vmware to run virtualized servers. I can't see how this would affect their market share in any measurable way.

---

### Post by Geoffrey_Arndt on 2016-03-31
+1 bashiergui . . . . Additionally, as long as Canonical doesn't enter into exclusive "patent" exemption & exclusive use contracts with MS . . . , then this is pnly another agreement allowing easier development of cross functionall apps.     

If Canonical were to pull off agreement similar to MS-Novell in 2006 (or thereabouts), then there would be cause for concern (big time).   That's why I quit use Suse that year, despite it being a great OS, with much better gui tools for hardware config. than any other distro with possible exception of Mageia et-all.  (no, . . . system settings not even close to Yast in functionality).

---

### Post by QDR06VV9 on 2016-03-31
> **Geoffrey_Arndt said:**
>  system settings not even close to Yast in functionality).
+1 Agreed I was using Suse as a tester in thoses days got tired of listening to them complaining about MS and the deal they had struck(Signed) with them at the time...bailed ship and landed here.
But I do miss the YAST(Yet Another Software Tool).

---

### Post by Old_Grey_Wolf on 2016-03-31
> **bashiergui said:**
> Enterprises use vmware to run virtualized servers. I can't see how this would affect their market share in any measurable way.

+1

Before I retired I was involved in building a few virtualized data centers.

---

### Post by slooksterpsv on 2016-03-31
I wanted to voice my thoughts on this move... surprisingly, I'm glad Canonical and Microsoft are working together on this. The thing is, the more cross-platform we can integrate environments without having to using VMs, Shared Drives, etc. the easier it becomes for development overall. Granted, this isn't for GUI services, but suffice to say I'm excited. There are so many things I've wanted in the Windows CLI that Command Prompt and Powershell just couldn't do, even with the .NET integration. Fluid tools were missing, especially those I've grown very accustomed to such as awk, sed, and nano.

I know a lot of people may be on the fence, but here's the thing. Microsoft is adding Linux architecture to Windows, granted in a fenced user session, but still. Whose to say that they won't benefit Ubuntu in the long run? Developers will love these tools, I myself will. [PIPE DREAM] Bundle in some QT, a translation from X/Wayland (whichever) to Win32, guess what? More native apps for Linux, built on Windows, using Linux. [/PIPE DREAM]

Now this could, in theory, translate to more apps available for Linux. Get the backend done, slap on a GUI and guess what, more native apps. [PIPE DREAM] Bundle GL, more games[/PIPE DREAM]

I really like the new CEO, he has a strong vision and dream. Let's work together, not separate.

---

### Post by montag dp on 2016-04-01
I really don't see how this promotes development of apps for Linux.  Wouldn't it be just as easy to run Linux in a VM if one wanted to do that?  The major barrier is not having the tools available to make cross-platform apps, but rather convincing developers to use them in the first place.  That means using Qt and OpenGL instead of .NET and DirectX, for example.  If developers are invested in MS tools and libraries for creating applications, I don't think this will change that.  

No, this is all about removing the benefit of using Linux in the first place, at least from MS's point of view.  At least, that's how I see it.

---

### Post by ian-weisser on 2016-04-01
Does this mean that Microsoft just added an entire GPL'd shell (and supporting stack) to Windows?

If so, does this mean that MS-ecosystem applications that use the stack must give up the use of secret APIs? (since they can't modify the source code without sharing)

Does it also mean the writing cross-platform applications just got a whole lot easier?

---

### Post by buzzingrobot on 2016-04-01
> **montag dp said:**
> 
No, this is all about removing the benefit of using Linux in the first place, at least from MS's point of view.  At least, that's how I see it.

Seems to me an effort to keep developers -- and their employers -- who use Windows in environments that also use Linux in some fashion and who need to write Linux code and/or talk to Linux processes from Windows, within the Windows camp. In that sense, it's an acknowledgment that Linux is legitimate. I don' think Canonical's involvement was strictly necessary to get a Linux subsystem running on the Windows kernel.   Access to Canonical repos from "Bash on Windows" would, I'm sure.

We shouldn't expect Microsoft to do anything that makes it easier to leave Windows altogether. 

Canonical has said it won't sign any patent deals with MS, which is pretty much the same stance Red Hat is taking in is dealings with the company.

---

### Post by klytu on 2016-04-01
> **stevecook said:**
> [FONT=Ubuntu]I don't like it.[/FONT]
[FONT=Ubuntu]
At all.[/FONT]
[FONT=Ubuntu]
I also don't care if that's regarded by some as an overreaction.

Form what i have read, thus far, this will run Ubuntu Linux inside MS Windows. It wont be a virtual Linux, it will be an *actual* Ubuntu Linux running inside MS Windows due to Microsoft having recently and quietly introduced Linux subsystems in a new Windows 10 Redstone build.
[/FONT]
[FONT=Ubuntu]My first thoughts are that this is just another way in which Cannonical are trying to monetise Ubuntu. That, in itself, does not cause me any intrinsic concerns since there are plenty of Linux distros whose philosophy is strictly the opposite of that. It's why I left Ubuntu with the advent of Unity and all of the Amazon nonsense and it is why I came back with the rebirth of Gnome 2 via Ubuntu Mate, as well as Canonical ditching the default Amazon stuff.[/FONT]

[FONT=Ubuntu]However, by throwing their lot in with Microsoft, Cannonical are basically acting as scabs (an old British term used to describe when some workers continued to go into work when all of their comrades were out on strike, thus weakening the strike) on the rest of the entire Linux eco-system. By allowing Microsoft to gain access to and so provide to their own customers under their own MS brand, all of the Linux world, they get all of the long term benefits.
[/FONT]
[FONT=Ubuntu]This will do to the Linux world, potentially, what was done to the Liberal Democrats when they teamed up with the Tories. Short term gains for Cannonical will be overwhelmed by long term losses to the Linux eco-system. In short, this is a *very* bad thing for the wider Linux world.
[/FONT]
[FONT=Ubuntu]If this really is what, on first reading, it appears to be, I am leaving Ubuntu and this time it will for good. I hope I am wrong on this and will be the first to admit it if so. But, the above is my understanding so far.[/FONT]

+1 

I agree with a lot you've stated and more. As a friend of mine told me, this is likely the "embrace" phase of [Embrace, Extend, and Extinguish]("https://en.wikipedia.org/wiki/Embrace%2c_extend_and_extinguish")

---

### Post by mikodo on 2016-04-01
> **Geoffrey_Arndt said:**
>  -snippets - Additionally, as long as Canonical doesn't enter into exclusive "patent" exemption & exclusive use contracts with MS . . . , then this is pnly another agreement allowing easier development of cross functionall apps.

> **buzzingrobot said:**
>  - snippets - Seems to me an effort to keep developers -- and their employers -- who use Windows in environments that also use Linux in some fashion and who need to write Linux code and/or talk to Linux processes from Windows, within the Windows camp. In that sense, it's an acknowledgment that Linux is legitimate. I don' think Canonical's involvement was strictly necessary to get a Linux subsystem running on the Windows kernel.   Access to Canonical repos from "Bash on Windows" would, I'm sure.Canonical has said it won't sign any patent deals with MS, which is pretty much the same stance Red Hat is taking in is dealings with the company.

Informed, rational comments like these are needed. I for one, appreciate the information and perspectives.

No doubt, there will be much fear-mongering about this. It is very helpful to have these informed perspectives to balance the other.

Thank you.

---

### Post by bashiergui on 2016-04-01
> **ian-weisser said:**
> Does this mean that Microsoft just added an entire GPL'd shell (and supporting stack) to Windows?

If so, does this mean that MS-ecosystem applications that use the stack must give up the use of secret APIs? (since they can't modify the source code without sharing)Intriguing.

---

### Post by ZannaStar on 2016-04-02
> **klytu said:**
> +1 

I agree with a lot you've stated and more. As a friend of mine told me, this is likely the "embrace" phase of [Embrace, Extend, and Extinguish]("https://en.wikipedia.org/wiki/Embrace%2c_extend_and_extinguish")

I agree with you & **stevecook **too, I felt dismayed to see this in puffy fanfare on @ubuntu twitter account with RTs from @windowsdev etc

[https://twitter.com/ubuntu/status/715486946777124864](https://twitter.com/ubuntu/status/715486946777124864)

 Looking at @windowsdev though, no ubuntu logos in sight. They generally call it 'bash on windows'. Canonical are projecting a lot more excitement about the whole thing, but it's hard to read the situation accurately. But I think it's clearly one less argument to persuade people to ditch windows =/ Ethical arguments usually get ridiculed by people who are invested in/used to doing the thing that is being pointed out as unethical. I'm vegan, so I'm thinking about how the vegan movement has gained traction recently as more evidence accumulates that it's a really healthy diet. People who go vegan for health reasons seem to quickly become proponents of the ethical arguments! So it's helpful to have some arguments that are pragmatic and not based on ethics. (Or is that what dilutes movements and allows co-optation?) Anyway we will see what happens =S

---

### Post by grahammechanical on 2016-04-02
"Embrace, Extend, and Extinguish." Well, that certainly is an improvement. It used to be just "Extinguish."

---

### Post by montag dp on 2016-04-02
Linux has been the beneficiary of many improvements in the last decade due to contributions from large corporations (e.g., Intel, Red Hat, and others). I think that's in large part due to the GPL's requirement of open source licensing, so these commercial improvements make their way back to the broader community. I can only hope that a similar effect results from this situation, but I really do not trust Microsoft for that. Who is going to challenge them in court for GPL infringements? I think it's more likely that they try to claim it as their own IP.

---

### Post by stevecook on 2016-04-02
Microsoft is a company with one goal; to make money. Everything they do is an attempt to help them achieve this goal. Currently their business model is selling OS licenses and every computer running Linux is a lost sale of a Windows license - at least in the eyes of a corporate economist. There shouldn't be any doubt at all that MS wants as few people as possible using Linux, unless they create something which allows them earn money from it.


If Microsoft say they love Linux it's in the same way as a paedophile "loves" children. They do not want what's best for Linux or its community. If they do anything which might be good for Linux we must do like Agatha Christie's Poirot and ask ourselves "cui bono" - who benefits? Or more precisely, how does MS benefit from this? We've already established that they don't benefit from people running Linux, so the only answer that remains is that they hope to attract companies and developers that would otherwise use Linux. In turn, bleeding valuable talent and potential income from the Linux world with all of the very difficult to predict but nevertheless very real negative consequences for that world.


I'm now running Mate on Debian Jessie as of this Morning.  It's a definite step down in terms of usability and smoothness compared to Ubuntu Mate, which is what i have been hitherto using for the last year or two, but I can get used to it and, I should stress here, I have nothing but good things to say about UM and its devs. UM is a wonderful distro. But, I simply cannot be associated with an organisation (Canonical) even if only indirectly (via UM) that has behaved in this way. I know and understand why Canonical have done it and it will be the money (Canonical is also a company that is in the business of making money). But, in doing what they have done, they are undermining the longer term prospects of Linux as whole. And that is unforgivable as well as unbelievably short-sighted.

---

### Post by buzzingrobot on 2016-04-02
The goal of every business is "to make money".  Has to be.  No profit, no company.

So, by itself, that's not much of a pejorative. Linux would be considerably different without the contributions made possible by corporate profit.

I don't think it is, or should be, the goal of Linux to put Microsoft out of business or to punish it for bad behavior.  Both should focus on making the best software they can.  Microsoft does not expect people to use its products for ideological reasons.  Neither should Linux.  It's certainly not why I do.

---

### Post by mikodo on 2016-04-02
Gnu/Linux with its' contribution to the open-source community by its' licensing is, a legacy for Unixes. As long as people want to develop and enjoy using products with those and similar type licenses, it will thrive. 

For that, we owe a huge debt to people like Richard Stallman and Ian Murdock.

There are no doubt financial reasons why Canonical is involved in this that, it hopes to benefit from. So what? It could only help solidify the financial backing of Ubuntu. Many people are recipients of that. But, even if it doesn't, Floss will remain and thrive, as long as people want it to.

---

### Post by The Cog on 2016-04-02
I can't imagine why people would want to run Linux programs on Windows. Lipstick on a pig or castles on sand come to mind. I can't imagine anything working as well on Windows as it would on Linux, even if it works at all given some of the oddities of Windows file handling. Unless they're already hamstrung with Windows for political reasons.

---

### Post by buzzingrobot on 2016-04-02
> **The Cog said:**
> I can't imagine why people would want to run Linux programs on Windows.

Developers who live in both worlds are the targets here. People, say, who support an RHEL or Ubuntu network but have Windows sitting on their desks. This is supposed to make their lives easier by allowing them to administer, or develop for, that Linux network with standard Linux tools without leaving Windows. 

That, at least, is Microsoft's hope.

It's not at all relevant to the typical Linux desktop user.

---

### Post by bashiergui on 2016-04-02
> **The Cog said:**
> I can't imagine why people would want to run Linux programs on Windows. Lipstick on a pig or castles on sand come to mind. I can't imagine anything working as well on Windows as it would on Linux, even if it works at all given some of the oddities of Windows file handling. Unless they're already hamstrung with Windows for political reasons.
I can't tell you how many times I've wanted to tail some logs or grep for a file in Windows. Just a simple cat even! Or just drop to a ruby shell. 

It will be nice to type ifconfig everywhere. I had to alias it in powershell because I'd type it wrong every damn time.

---

### Post by Afisamuleal on 2016-04-03
I work at a tech firm and I told all my coworkers this was an april fools joke. If it isn't, I wish they had waited till April 2nd. Where's the code to try! I have to use Windows all day for work, but I much prefer the unix ecosystem. So this is awesome! Can't wait to try it, and dump cygwin for more up to date ubuntu repos. I wonder if windows parses input all funny running as bash; just the other day I had a coworker ssh into a unixbox to use curl, because example commands didn't parse correctly on windows...

The next step to make me happy is for Microsoft to rewrite Windows to use the xserver, so I can use awesome to manage my windows windows.

---

### Post by deadflowr on 2016-04-03
> **Afisamuleal said:**
> I work at a tech firm and I told all my coworkers this was an april fools joke. If it isn't, I wish they had waited till April 2nd. <snip>

Yep, An April fool's day joke, that they announced in March.:D 
[https://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/](https://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/)

---

### Post by Afisamuleal on 2016-04-03
March 30th, to be precise. You made me check! Yeah, I told all my coworkers it was an april fools joke on March 30th. lol.

It's april 2nd, so I feel like they would've taken it back by now if it really was an april fools joke. :guitar:

---

### Post by grahammechanical on 2016-04-03
> Where's the code to try!

I think that a person has to be a Windows Insider to get advance copies of the code. It is supposed to be available in the Windows store but I do not think that beta code would be in the store.

Regards.

---

### Post by justen_m on 2016-04-03
I've got a Win 10 Pro Insider Preview box (bld 14295.1000) and I can't find Ubuntu in the store.

---

### Post by light_yagami2 on 2016-04-05
I don't really see why Conical is helping Microsoft when Microsoft doesn't even support linux in terms of software avalibility. I hope Micro$oft didn't buy Conical. Otherwise I'd install another distro :(

---

### Post by grahammechanical on 2016-04-05
Someone once criticized Canonical for putting fewer patches into the Linux kernel than Microsoft had done. Are you now going to stop using Linux?

> Among other notable changes, Microsoft fell off the list after  briefly being one of Linux's most prolific contributors. Microsoft's 688  changes accounted for one percent of the total in the 2012 list.

 Microsoft, in 2009, submitted drivers for its Hyper-V virtualization  platform to the Linux kernel. The project hit a bunch of delays, with  Microsoft struggling to get its drivers out of the staging area and into  the mainline kernel. In 2011, Microsoft became the [fifth largest corporate contributor]("http://www.networkworld.com/news/2011/071811-microsoft-hyperv-linux.html")  to Linux kernel version 3.0 as it attempted to clean up its  code. Redmond's contributions have predictably dropped off now that the  code is more stable.



[http://arstechnica.com/information-technology/2013/09/google-and-samsung-soar-into-list-of-top-10-linux-contributors/](http://arstechnica.com/information-technology/2013/09/google-and-samsung-soar-into-list-of-top-10-linux-contributors/)

> Ubuntu is about showing humanity to one another: the word itself captures the spirit of being human.

> We invite anybody, from any company, to participate in any aspect of the  project. Our community is open, and any responsibility can be carried  by any contributor who demonstrates the required capacity and  competence.

[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

> It is our mission to make open source software available to people everywhere.

> We partner with the biggest names in hardware, software and on the cloud  to help them optimise, extend and deliver Ubuntu at scale.

[http://www.canonical.com/](http://www.canonical.com/)

And that includes running Ubuntu on Microsoft's Azure Cloud offering. 

A Q&A with Dustin Kirkland who was the Canonical engineer who worked with Microsoft's engineers on this project.

[https://www.youtube.com/watch?v=cdLobNoCbxw](https://www.youtube.com/watch?v=cdLobNoCbxw)

You have only just joined us and already you are promising to leave.

---

### Post by buzzingrobot on 2016-04-06
Ars Technica has an interesting piece today: "Why Microsoft Needed To Make Windows Run Linux Software". ([http://arstechnica.com/information-technology/2016/04/why-microsoft-needed-to-make-windows-run-linux-software/)]("http://arstechnica.com/information-technology/2016/04/why-microsoft-needed-to-make-windows-run-linux-software/")

It reinforces the notion that this is all about keeping developers inside the Windows universe by making available the ability to use the non-Windows tools they've been using.

Also contains the assertion that Microsoft is having to spend time teaching new hires how to develop the Windows way. I.e., they aren't doing development on Windows in school or in their previouos jobs.

"Linux *software*" is  reminder that there's no kernel in this mix.  Anything that depends on the kernel won't be available.

---

### Post by montag dp on 2016-04-06
> **buzzingrobot said:**
> It reinforces the notion that this is all about keeping developers inside the Windows universe by making available the ability to use the non-Windows tools they've been using.Which begs the question, why would Canonical want to help them do that?

I guess the answer is, because Canonical cares about *Ubuntu*, not Linux*.  *At least, that's the conclusion I'm drawing from it.

---

### Post by ian-weisser on 2016-04-06
While it's fun to read malevolent motives into a group that you're not part of, do please remember the Code of Conduct.

Every member of Canonical that I have met has been _*deeply*_ committed to Linux, and to the mission of Free and Open Source Software. Many of their whole lives are built around it.

The Ubuntu community is not so terribly big, and meanspirited words spoken publicly in haste you may someday regret.

---

### Post by montag dp on 2016-04-06
Not mean spirited at all.  I'm just trying to understand this move on Canonical's part, and I'd love to hear a different take.  It's been stated that MS's motive in all this is to keep developers with Windows instead of moving to Linux.  So the question remains, why would Canonical want to assist with that endeavor?  To me, the logical conclusion is that Canonical wants developers to use Ubuntu, even if it keeps them from using Linux.

I suppose another motive could be to introduce them to Linux in the hopes that they will switch.  But then that conflicts with MS's motive, so it becomes a gamble as to which way it would turn out.

Also, I certainly wasn't commenting on the motives of individual developers, but rather the organization as a whole.  

One more thing, I think my previous comment came across more harshly than intended.  Of course Canonical cares about Linux.  Maybe I should have just said that they care primarily about Ubuntu, and then about Linux.

---

### Post by grahammechanical on 2016-04-07
This is a Ubuntu users forum. What do we know about the motivations of the management at Canonical? Only what we learn from public statements made in blog posts & interviews.

Mark Shuttleworth was once voted the Most Disruptive Name in Computing by Forbes magazine. And that award would have pleased him. He wants Ubuntu to be disruptive. He believes it will stimulate others to innovate with Ubuntu. And why not "with Ubuntu?" Why is it wrong for the Company that sponsors Ubuntu to promote Ubuntu?

[http://www.omgubuntu.co.uk/2013/03/mark-shuttleworth-named-most-disruptive-name-in-computing-2013](http://www.omgubuntu.co.uk/2013/03/mark-shuttleworth-named-most-disruptive-name-in-computing-2013)

[URL="http://www.wired.co.uk/news/archive/2013-08/13/mark-shuttleworth-canonical-ubuntu"]http://www.wired.co.uk/news/archive/2013-08/13/mark-shuttleworth-canonical-ubuntu

[/URL][http://insights.ubuntu.com/2016/04/07/ubuntu-is-everywhere/](http://insights.ubuntu.com/2016/04/07/ubuntu-is-everywhere/)

A Canonical community manager once said: "When it comes to the desktop there is an elephant in the room. When it comes to mobile phones there are two elephants in the room." What do you do in situations like that? You do something different.

Regards.

---

### Post by izznogooood on 2016-04-08
Here's another view:

Apple has become what Microsoft once was. Your environment is locked, its not yours to control.
Microsoft is altering course. With this they open their "environment" (ever so slightly)

I for one am exited to see where this leads, the possibilities are endless. 

(As for why "open source ONLY" will never work in a society that runs on money. Well, that's another discussion all together ;))

---

### Post by justen_m on 2016-04-09
> **justen_m said:**
> I've got a Win 10 Pro Insider Preview box (bld 14295.1000) and I can't find Ubuntu in the store.
It's here with 14361.1000
[COLOR=#000000][FONT=verdana]Insider Preview fast ring system just updated from 14295 to 14361. Differences...
1) The black screen with big blue progress ring during the update reboots is gone. In its place is my user background color, and just white text showing the percentage.
2) After last reboot and logging in, system hung. None of my taskbar launchers were present, couldn't launch any apps, open the start menu, or even launch task manager via ctrl-alt-del, etc. After waiting five minutes, I rebooted (hardware power switch), and all is now fine. The last big update required an extra reboot too.
3) Checked my privacy settings after the upgrade. Location was turned from off to on, and all Background apps were turned from off to on. Fixed that.
4) Fast Startup was turned from off to on. Again. This happens with every major update. The system is dual boot (Ubuntu 16.04LTS Beta Linux), and with fast startup Linux sees the Windows drives as having hibernate data and won't mount them rw. Since I have them automounted via fstab, this causes my Linux boot to drop to a terminal instead of launching my window manager. Keep having to turn this off.
5) Edge has two more extensions! Yay! They are as useless to me as the first three. Boo! Clicking get extensions in Edge now loads the web page in Edge, instead of the default browser. Previously, it would load the Edge extensions page in Chrome, my default. Probably makes sense.
6) Edge can now import bookmarks from IE, Chrome, and Firefox. I think Firefox is new. Or Chrome. One or the other is new. Edge _still_ seems to lack a bookmark/favorites manager, but you can move bookmarks around a bit easier, like in other browsers.
7) Doesn't have the modified Start menu unveiled at Build2016.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana] use grep and find very often. find seems heck of a lot faster than the Windows search box. It even comes with some some aliases for grep and ls and improved vi. ssh works, but the bash shell doesn't inherit the hosts file from Windows, so I had to cp that.

Definitely still a beta, as some basic commands seem buggy, like ps -ef, and top. Both screw up the terminal. htop installed successfully, but doesn't seem to run. byobu comes installed, but doesn't work. I wonder if gcc, g++, gdb will install and work. More to explore. java isn't installed, but it does come with python 2.7.6, which isn't that old (Jun 2015). It's using linux kernel, 3.4.0, (Aug 2013), which is newer than what's in 15.04.[/FONT][/COLOR]

---

### Post by qyot27 on 2016-04-09
> **bashiergui said:**
> I can't tell you how many times I've wanted to tail some logs or grep for a file in Windows. Just a simple cat even! Or just drop to a ruby shell.
> **Afisamuleal said:**
> and dump cygwin for more up to date ubuntu repos.
The solution for full integration has and always will be to use MSys to augment native Windows with most of the typical GNU userland (just add MSys' /usr/bin to Windows' %PATH%).  [MSys2](https://msys2.github.io/) is kept up-to-date, and actually uses a Windows port of pacman to keep its packages managed.  It's obviously not endorsed by Microsoft and would therefore probably be unpalatable to many corporate interests that want to pay for dedicated tech support, but it's the closest thing short of running a full - and slow - Cygwin environment.


Not that *nix integration is somehow new for Microsoft;  I wouldn't be surprised if this is simply going to end up being considered the spiritual successor to [Windows Services for Unix/Interix](https://en.wikipedia.org/wiki/Windows_Services_for_UNIX), considering how ridiculously outdated the tools in that setup are.

---

### Post by Wadim_Korneev on 2016-04-10
Very impressive technology. I tried to set up an Android build environment under it but I was hampered by this open Ubuntu bug from 2014.

---

### Post by atrab101 on 2016-04-13
As a new Ubuntu user, this issue is surprising to me.  I now have a dual boot system with Ubuntu and Windows XP.  Microsoft did not provide an upgrade path for XP except via Vista in the past (wich I heard was awful.  I do have some Windows programs that I currently want to continue using, hence dual boot.  Not wanting to be a Windows proprietary prisoner in the future, I opted for Linux and am very happy with the result.  As long as Windows does not infiltrate my Linux drive, I guess I am OK with Microsoft getting involved with Linux.  They have a right to do that unless they violate the license agreement.  It does appear that the 800 pound gorilla may have lost a little weight but only down to 795 or so.  In the future more pounds may come off, as more users like me that are fed up with Microsoft arrogance move to Linux.

---

### Post by grahammechanical on 2016-04-13
I would not call it arrogance. I see no need to repeat what others have said to give a different understanding.

Microsoft is still a profit making organisation and it is not the American way of doing business to let every one have a fair slice of the pie, even if it is "mom's apple pie." :)

And the American way is no different from anyone else's way of doing business. Including businesses that make money from Linux. No employee is going to be happy to be told that they could not have a pay increase because the company decided not to go after a lucrative contract because it was only fair that some other company have an opportunity to make money.

Regards

---

### Post by ventrical on 2016-04-13
North Americans are suckers for punishment.  I remember when  they advertised that Win XP was the "most secure ever" when actually it was a malware beehive.  People are fascintated with virus and malware. And they continue to pay for the punishment. 

Ignorance is bliss.
Ubuntu is effervescent.

Regards..

---

### Post by ventrical on 2016-04-13
> **stevecook said:**
> [FONT=Ubuntu]I don't like it.[/FONT]
[FONT=Ubuntu]
At all.[/FONT]
[FONT=Ubuntu]
I also don't care if that's regarded by some as an overreaction.

Form what i have read, thus far, this will run Ubuntu Linux inside MS Windows. It wont be a virtual Linux, it will be an *actual* Ubuntu Linux running inside MS Windows due to Microsoft having recently and quietly introduced Linux subsystems in a new Windows 10 Redstone build.
[/FONT]
[FONT=Ubuntu]My first thoughts are that this is just another way in which Cannonical are trying to monetise Ubuntu. That, in itself, does not cause me any intrinsic concerns since there are plenty of Linux distros whose philosophy is strictly the opposite of that. It's why I left Ubuntu with the advent of Unity and all of the Amazon nonsense and it is why I came back with the rebirth of Gnome 2 via Ubuntu Mate, as well as Canonical ditching the default Amazon stuff.[/FONT]

[FONT=Ubuntu]However, by throwing their lot in with Microsoft, Cannonical are basically acting as scabs (an old British term used to describe when some workers continued to go into work when all of their comrades were out on strike, thus weakening the strike) on the rest of the entire Linux eco-system. By allowing Microsoft to gain access to and so provide to their own customers under their own MS brand, all of the Linux world, they get all of the long term benefits.
[/FONT]
[FONT=Ubuntu]This will do to the Linux world, potentially, what was done to the Liberal Democrats when they teamed up with the Tories. Short term gains for Cannonical will be overwhelmed by long term losses to the Linux eco-system. In short, this is a *very* bad thing for the wider Linux world.
[/FONT]
[FONT=Ubuntu]If this really is what, on first reading, it appears to be, I am leaving Ubuntu and this time it will for good. I hope I am wrong on this and will be the first to admit it if so. But, the above is my understanding so far.[/FONT]

Nice write up. Remember... with Windows comes vulnerabilites  for malware and the vulnerability of all the exploitable ports to spy in on Ubuntu behaviour. Malware writers have had a hard time breaking and interfecting Ubuntu and , now , Windows has opened the door and Canonical has allowed it. Remember .. you read it here first.

regards..

---

### Post by ventrical on 2016-04-13
> **grahammechanical said:**
> I think that a person has to be a Windows Insider to get advance copies of the code. It is supposed to be available in the Windows store but I do not think that beta code would be in the store.

Regards.

@graham

[http://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/](http://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)

---

### Post by ventrical on 2016-04-13
Mark Shuttleworth quote

"full Ubuntu environment on Windows"

[http://www.techrepublic.com/article/the-truth-comes-out-microsoft-needs-linux/](http://www.techrepublic.com/article/the-truth-comes-out-microsoft-needs-linux/)

---

### Post by atrab101 on 2016-04-14
Yes, they are entitled to be the 795 pound gorilla if the free market supports them.  Nothing is wrong with the profit motive for a corporation, which stockholders and employees all appreciate.  That does not necessarily translate into arrogance.  But in Microsoft's case, as relates to my experience, I think it has at least in part become that.  I have a Windows 8.1 tablet purchased a few years with limited memory, but it serves its purpose of convenience in some situations.  The free Windows 10 nags began many months ago, first after an “important” update to Windows 8.1 downloaded for no other reason than to tell me about Windows 10.  I had to reverse that update to stop the nag.  I don't need or want Windows 10 which my limited tablet memory would not support, even though they said I was Windows 10 ready.  They kept telling me what I want and need with further updates that also included Windows 10 nag components.  Now I carefully review all updates to insure I don't get another nagging one, although they are clever in their update descriptions about enhancing the “windows experience” but never mention Windows 10.  The latest issue was an Internet Explorer 11 “security” update that also included a Windows 10 nag component (without mentioning in description).
 

 This is the more narrow view of arrogance that troubled me a great deal.  I read about the many users that ended up with a download and installation of Windows 10 they did not want, which in some cases resulted in a computer that no longer worked.  Maybe they were not vigilant enough to prevent it, but should Microsoft's customers be put into the position of defending themselves against a product they don't need or want, if they are perfectly happy with Windows 7 or another version?  This is a personal slice of “mom's apple pie” that Microsoft is trying to shove down each of her children's throats.   :D

 

 This is what pushed me to my decision to install Ubuntu on my desktop, only retaining a Windows XP drive for limited use with certain old programs in the future, which have needed history or I still find useful.  I am so glad that I made the switch.  Just the other day I encountered an issue where the Shutterfly website would not accept photo uploads by my wife to make prints.  Others had reported the same problem.  She was on the XP drive where the old photos were located.  I switched to the Linux drive and uploaded the photos with no problems.  Ubuntu just works!

---

### Post by ventrical on 2016-04-14
> **atrab101 said:**
> Yes, they are entitled to be the 795 pound gorilla if the free market supports them.  Nothing is wrong with the profit motive for a corporation, which stockholders and employees all appreciate.  That does not necessarily translate into arrogance.  But in Microsoft's case, as relates to my experience, I think it has at least in part become that.  I have a Windows 8.1 tablet purchased a few years with limited memory, but it serves its purpose of convenience in some situations.  The free Windows 10 nags began many months ago, first after an &#8220;important&#8221; update to Windows 8.1 downloaded for no other reason than to tell me about Windows 10.  I had to reverse that update to stop the nag.  I don't need or want Windows 10 which my limited tablet memory would not support, even though they said I was Windows 10 ready.  They kept telling me what I want and need with further updates that also included Windows 10 nag components.  Now I carefully review all updates to insure I don't get another nagging one, although they are clever in their update descriptions about enhancing the &#8220;windows experience&#8221; but never mention Windows 10.  The latest issue was an Internet Explorer 11 &#8220;security&#8221; update that also included a Windows 10 nag component (without mentioning in description).
 

 This is the more narrow view of arrogance that troubled me a great deal.  I read about the many users that ended up with a download and installation of Windows 10 they did not want, which in some cases resulted in a computer that no longer worked.  Maybe they were not vigilant enough to prevent it, but should Microsoft's customers be put into the position of defending themselves against a product they don't need or want, if they are perfectly happy with Windows 7 or another version?  This is a personal slice of &#8220;mom's apple pie&#8221; that Microsoft is trying to shove down each of her children's throats.   :D


 More corporate bullying along with forced obsolescence  of slightly older hardware. That's why we have to lobby to keep Ubuntu pure. The new motherboard one has bought 6 months ago depreciated 50%  after the first update and then another 25% after it's 6 months run so it is guaranteed  that your investment in your personal hardware is money in the waste basket if you don't flip it. Ubuntu (along with other Linux derivatives) is probably the only way you can appreciate your hardware and save money without the headaches.

regards..

---

### Post by grahammechanical on 2016-04-14
MIcrosoft is probably still smarting over the mess it got into with XP. It had to pay employees to keep putting security fixes into an obsolete & security vulnerable OS because so many users had no reason to junk working hardware to buy new Windows machines. And they didn't and then they howled when Microsoft first stopped supporting XP.

A golden goose is great until it eats more gold than it lays.

Regards.

---

### Post by ventrical on 2016-04-14
And the golden geese in question were mostly graphical with feathered arrangements and pecking orders. Vista offered .. uhm... errr .. some sort of Areo-Dashboard which took hours (if not days)  of sitting time to configure properly. Once past that and you then had resource problems to contend with. It was a three step process and it worked well. Razzle, Dazzle and Dump.

1. Razzle. This is the part where  they used security parlance to fear monger on the unsuspecting and potential upgraders. After trying all different kinds of anti-malware removal processes and firewalls , end_users were convinced that their hardware was bricked.  The company even went as far as to personalize a bot to tell you that your current system was  'Upgrade Ready' only to completely brick it or leave it severely  broken - which then justified  buying new metal and a new OS.

2. Dazzle. It is always the 'shiny new thing' that would get an end_user to upgrade to a new system and once there then there was always something else that needed attention , ie; like more memory and more processor speed so , say  the goose had laid three golden eggs but in the meantime she is not eating gold. She is eating lead and you know that that bird is just not going to fly. Then, turns out that the golden eggs are only gold plated.

3. Dump. And thats it. Gold plated lead eggs. Then you get EULA spammed about how you only have a license and do not actually 'own' your operating system. So what you have is a goose that cannot fly, lead balls all around you and machine the size of a small laundry hamper  that is supposed to be taking care of your computer needs .. always  with the caveat that you will never need to upgrade again. And btw .. you never really 'owned' your computer hardware either. Microsoft owned it along with some third-party anti-virus company.

  Never mind about new Vistas. With Ubuntu we have new Horizons and your PC hardware has been returned back to  you in working order.  :) (with some bugs) but the goose will take care of those.;)

regards..

---

### Post by atrab101 on 2016-04-14
Love the analogies.  I never moved from XP to Vista after exposure 8 years ago via my daughter's laptop bought for college use.  Looked to me like Vista would have more bugs than XP and less freedom to try to fix them.  Yes, I have laboured over the years with registry editing, etc.  She eventually became so frustrated with Vista that she bought a Mac ($$$).  The ensuing years brought me a low cost desktop experience, finding compatible parts (sometimes used on Ebay), but at least the system worked well albeit slow.  My wife's complaints attested to that.  The ancient XP system's final failure three months ago (yes, I had another used spare Athlon XP 2700+ processor but chose instead to launch into the future) brought a pleasant surprise with a brand new system and dual boot:  the XP dino preserved for occasional use (but not yet fossilized) and new Horizons indeed with Ubuntu.  

Regards

---

### Post by ventrical on 2016-04-14
In all fairness to the OP...bash  or any ubutnu on Windows 10 is like mixing oil and water. What concerns me most about this is that it was originally  a secret between a Canonical rep and Microsoft. This is the opposite of transparency and the open source concept. However,  if there is a bridge of trust built between the two companies then both may fare well from this joint venture but history tells us that far too often  the secret ventures of Microsoft has lead  to tremendous amounts of down time for end_user space and you will never get paid for the work you did for Microsoft.

Regards..

---

### Post by vasa1 on 2016-04-14
> **ventrical said:**
> ... Ubuntu (along with other Linux derivatives) is probably the only way you can appreciate your hardware and save money without the headaches.
...
Well, Ubuntu and certain other desktop environments may not be suited for some older hardware.

---

### Post by atrab101 on 2016-04-15
My understanding of software development and the markets in which it operates is quite limited.  It seems that a very important market is made up of lots of individuals like me that want their computer to be a useful tool with a reasonably long life.  They also want it to work with few troubles and at a reasonable cost over that time.  Microsoft gained market share early but continues to dominate due to the inertia of its size, even though on these points it has failed in many ways.  More individuals that are not satisfied with their products and aggravated by their methods will continue to migrate, but it will take time. Rome wasn't built in a day.  I suppose I don't necessarily see a negative with Ubuntu moving into the Microsoft space, as long as Ubuntu is properly recognized and not violated.  I am certain that I do not want to see Microsoft move into my new Ubuntu desktop space.  A big attraction to me was just by virtue of the fact that it was a viable *alternative* that would meet my needs.  I have thus far found it to be extremely useful, trouble-free and obviously very cost effective.  :D

Regards

---

### Post by ian-weisser on 2016-04-15
> **atrab101 said:**
> It seems that a very important market is made up of lots of individuals like me that want their computer to be a useful tool with a reasonably long life. They also want it to work with few troubles and at a reasonable cost over that time.
Perhaps to you and me. Vendors may see that market as unprofitable, hence unimportant.

> **atrab101 said:**
> More individuals that are not satisfied with their products and aggravated by their methods will continue to migrate, but it will take time.
Satisfaction is less important to the business model than income.
Satisfaction can always be improved later, if it turns out to be an important element of platform choice.
So far, not really. Imprinting, being the first OS people learn, seems to be more important.

---

### Post by ventrical on 2016-04-15
> **vasa1 said:**
> Well, Ubuntu and certain other desktop environments may not be suited for some older hardware.

Why yes, of course. There is no dispute there , at least from my end. On the average, though, many frameworks from 2004 and up have a really good chance of installing a reliable ubuntu-linux system that is current in development.

regards..

---

### Post by ventrical on 2016-04-15
> **ian-weisser said:**
> Perhaps to you and me. Vendors may see that market as unprofitable, hence unimportant.


Satisfaction is less important to the business model than income.
Satisfaction can always be improved later, if it turns out to be an important element of platform choice.
So far, not really. Imprinting, being the first OS people learn, seems to be more important.

And that's one of the phemons of Ubuntu. It is the rejection of that imprinting along with the downtime and compromised user_space that make Ubuntu the logical alternative. People somehow just find it and get it running no matter how hard it is.  That's a big message sent to the corporate side of hardware/software buisness models.

regards..

---

### Post by buzzingrobot on 2016-04-15
> **ian-weisser said:**
> ...being the first OS people learn, seems to be more important.

We see this happen in all sorts of areas:  Technological change present a business opportunity. A batch of new ventures jump in with products. Sooner rather than later, almost all leave the market.  A very few vendors, sometimes one, dominate the market. The conventions they establish become the de facto standards everyone else must follow.  Others vendors who want to sell into that market shape their products to work with the market leader's product.  Users become accustomed to the specific ways that product tackles generic tasks and quickly find it very difficult to learn new habits.  Eventually, the need to sustain compatibility with its own previous products and installed base,  and with the products of the industry it has fostered, stifles innovation and leads those vendors to look new ways to sustain their profitability.

That's obviously a synopsis of the PC industry, but much the same has happened in most other markets built around what was once innovative engineering.

---

### Post by mikodo on 2016-04-22
Snippets
> **ventrical said:**
> North Americans are suckers for punishment.  I remember when  they advertised that Win XP was the "most secure ever" when actually it was a malware beehive.  People are fascintated with virus and malware. And they continue to pay for the punishment. 

> **ventrical said:**
> Nice write up. Remember... with Windows comes vulnerabilites  for malware and the vulnerability of all the exploitable ports to spy in on Ubuntu behaviour. Malware writers have had a hard time breaking and interfecting Ubuntu and , now , Windows has opened the door and Canonical has allowed it. 

Being N.American and respectful of your work in malware removal, I hope you are wrong.

---

### Post by T.J. on 2016-04-22
Ladies and Gentlemen.
 
 
 If I might say so, I believe the entire business behind the Linux for Windows subsystem is simply to court developers.  Windows has a lost a lion's share of the developer favor over the last few years to Android and iOS.  By supporting basic Linux tools on Windows, Microsoft hopes to slow the exodus of commercial developers off of Windows for alternative platforms, by letting them work on Windows while still using the tools they have become accustomed to.

 It&#8217;s wise move, although I believe it is far too late.  Outside of corporate offices and programmers, Windows is already dead.  

It's share of the  world's computer devices is stagnant at around 14%.  Windows' use is  certainly not climbing, nor as it seen a serious prospect for the future  non-PC era device designs.  Microsoft has burned too many bridges with  their former hardware partners, so even their former partners are  betting on an opensource, non-Windows future.  As I see it, Windows as a consumer platform is basically a thing of the  past, outside of PC gaming.  

Microsoft was one of the original signatories to the POSIX standard. I do believe that returning to being a strong advocate for the POSIX standard is their best hope, not some half-baked compatibility layer with Ubuntu as pleasant as it might be.  I don&#8217;t see this new Linux subsystem having much effect.  Virtualization is too entrenched and offers other tangible management benefits besides a simple programming tool, so I think this initiative will be entirely stillborn.

You might say I sound overly zealous to one point of view.  That's all right.  I've been working in or around programming and computer science for over 25 years.  I've seen the tides rise and fall more times than I can remember. In my opinion, this is little more than stopgap strategy to keep Windows in the news and relevant for a little while longer.

---

### Post by sammiev on 2016-04-22
> **T.J. said:**
> 
Outside of offices and programmers, Windows is dead.  It's share of the world's computer devices is stagnant at around 14%.

Would like to read the article with all this info. Please post the link.

Thanks

---

### Post by T.J. on 2016-04-22
Certainly! 

"The reality is the world's shifted, the world's evolved. We now measure  ourselves in the total device space. And in the total device space we  have a 14% share of devices, total worldwide devices."

  -- Kevin Turner, Microsoft Chief Operating Officer, at Microsoft's Worldwide Partner Conference in Washington DC, 2014. ([http://www.computerworld.com/article/2490008/microsoft-windows/microsoft-gets-real--admits-its-device-share-is-just-14-.html](http://www.computerworld.com/article/2490008/microsoft-windows/microsoft-gets-real--admits-its-device-share-is-just-14-.html))

Please do a simple Google search if you wish to verify attribution.  Have a wonderful evening! =)

---

### Post by atrab101 on 2016-04-23
```
It's share of the  world's computer devices is stagnant at around 14%.
``` 

                        This number looked crazy to me.  I guess since I only used Windows for 24 years until I recently built a dual boot WinXP/Ubuntu desktop, I thought Microsoft still enjoyed a dominant market position.  After looking at the Gartner web site, I clearly see where the 14% number is coming from.  Desktop devices were only about 10% of total shipped devices in 2015 (including tablets, phones, etc.).  Microsoft has almost none of the tablet and phone markets, so the number makes sense.  Very surprising to me!  I personally enjoy using a desktop, and I am not a gamer. I am not interested in giving my life to Google on a phone or tablet, and I don't think I am alone with that feeling. I guess I am part of a coming niche market!  Of course, a few hundred million PC's is still quite a few, and they are much more substantial platforms that users will invest more dollars in than any phone, which will probably one day become near give-away items (many are getting close). It does not cost much to make a phone in China. Please continue to support my niche, Ubuntu!  Strange thoughts, indeed, but apparently Microsoft may have a rough road ahead.

  
Regards

---

### Post by T.J. on 2016-04-23
>   Desktop devices were only about 10% of total shipped devices in 2015 (including tablets, phones, etc.).  Microsoft has almost none of the tablet and phone markets, so the number makes sense.  Very surprising to me!  I personally enjoy using a desktop, and I am not a gamer.

I am not interested in giving my life to Google on a phone or tablet, and I don't think I am alone with that feeling.



I know. I feel much the same way, except that I like games.  

As a developer, I have seen the consumer market move off of the desktop.  It makes me glad actually.  Desktop workstations are overkill and the average users simply do not need that level of computing power.  What we are seeing today is simply the long delayed transition of regular users to  less costly devices.  It was something that was inevitable. Microsoft  and Apple actually knew this back in the 90's and 2000's but Microsoft in particular went out of its way to prevent  it because its largest products: Windows and Office - are designed  around a keyboard and mouse - using a lot of screen real estate.  If you need proof, look up the Newton or Courier tablets.  
.

As a rule, Windows - because it is closed and proprietary -  has been a  tech support nightmare for most OEMs.  An alternative tablet running opensource -  by design -  is a simple flash/restore  because most of their data is stored elsewhere. I'm not an advocate for cloud use or the massive privacy invasions that it invites. I actually despise it.  I simply recognize the reality of others' use patterns, and cultivate the necessary tools to do my job.


In my experience, while acknowledging their contributions, front running tech giants like Intel, Apple and  Microsoft aren't visionaries, as much as they are restraining forces. I  can give you many examples I have seen in my career of how we would have  been better off without them, and their legions of lawyers; who are  responsible for killing off real advancements in technology.  It's very  sobering. The reason Microsoft is so far behind now is that their corporate culture wouldn't let them acknowledge the fact that they can't control everything.

> 
  I guess I am part of a coming niche market!  Of course, a few hundred million PC's is still quite a few, and they are much more substantial platforms that users will invest more dollars in than any phone, which will probably one day become near give-away items (many are getting close).


To some degree, certainly. You can rest assured that they will never fully "go away."  What you call a "PC" was called a "workstation" in the pre-PC days.  Workstations are not going to go away, because like a consumer tablet, they serve a specific design purpose.  A developer does probably 90% of their actual work on a workstation. An office worker perhaps uses it approximately 60-80% of the time  at a rough guess.



I use mine nearly 100% of the time because I prefer having the ability to run Windows and Linux simultaneously, rather than dual boot.  I develop on both platforms.  I see Windows as a "dead end" not because it is bad, but because it is closed source on a highly restrictive license. Microsoft is simply becoming too costly for developers to maintain on a profit margin, now that opensource runs most devices.  

> 
 !  Strange thoughts, indeed, but apparently Microsoft may have a rough road ahead.


We will see.  I hope they come to their senses, and start making Windows more open and relax the license.
  
Take care

---

### Post by Konjad on 2016-04-28
I'm curious to see where it all goes and what will be consequences of this. Well, time will tell.

---

### Post by ventrical on 2016-05-01
> **mikodo said:**
> Snippets




Being N.American and respectful of your work in malware removal, I hope you are wrong.

I hope I am wrong too but the history of corporate software development has proven otherwise. There is no end to the way these companies 'vault' their software and then they blame hackers for exposing vulnerabilities.

regards..

---

### Post by grahammechanical on 2016-05-01
I am reminded of the old American saying: "There is no such thing as a free lunch." Even in Linux there are organisations whose motive is the continued funding of the project. To put it politely.

---

### Post by ventrical on 2016-05-01
Another old American saying .. 'Buyer Beware". I just  listened to a direct testimonial about a person who had paid $375.00 to get their Windows 7 repaired from malware. Remember .. the most secure ever , ever. Ok.. so she went on to tell me about getting the Windows 10 upgrade notification and how the ITs told her that Microsoft 'controls' the way the upgrade is installed. Then they told her that one day Windows 7 will just disappear. (Keep in mind that these are people who say 'uh' when you mention the word Ubuntu).

  She tells me she could have bought a new tower with the money she paid to have her malware removed. I thought to my self of the other old American saying "There's a sucker born every minute."

Funding a novel project for eventual wolrd wide community use is a far cry from "selling the farm" "lock,stock and barrel". Those are two other old American sayings.  Then .. across the pond .. there are servral famous English lyrixs that I won't get into here :)

regards..

---

### Post by grahammechanical on 2016-05-01
"Here's to the new boss. Same as the old boss. We won't get fooled again." :)

---

### Post by ventrical on 2016-05-01
hehehe .. 'got to keep the loonies on the path'.. :)

---

### Post by mikodo on 2016-05-01
Well, I am no longer a noob.

If I see any of those worms, I'll blast him with a shotgun, err... I mean dd

---

### Post by ventrical on 2016-05-01
Almost 8 years of Ubuntu here. Nothing. Ever.  I have had firefox crash once in a while but malware in the wild is rendered silent here. Malware is rendered silent when you install Ubuntu over  Windows. It is a refreshing bonus of having an Ubuntu install. There is no operating system that can even touch the freedom-factor that Ubuntu provides.

 I even have ComodoAV (linux-Ubuntu-version) running on one install. The only thing it has ever detected was EICAR which I download from time to time just to make sure it is working.

Of course .. my point again.. with Ubuntu-bash now being mothered by Windows 10: will these these things change? Certainly not with current Windows malware  but somebody might decide to try and convert windows malware code to Ubuntu code. I don't like bringing this up. I revealed a lot of weakness with MS IE and all I got was hollered at and bullied by MS MVP ITs until they got hit with major malware. Then they ate crow. It is always the case after the fact.  All I am saying is that it is something to think about.

regards..

---

### Post by grahammechanical on 2016-05-01
It underlines the importance of replacing X Server. I don't remember anybody speaking of the vulnerabilities in X Server until someone wanted to replace it with something else. Then we started to get all the talk about why we need a replacement.

How many times have we heard the expression "An accident waiting to happen" and "Someone will have to die before something is done about this?"

Regards

---

### Post by atrab101 on 2016-05-02
> There is no operating system that can even touch the freedom-factor that Ubuntu provides.

 Could not agree more after my first few months of use.  I went a couple of decades without a significant malware or virus issue in Windows; however, this was largely due to the fact that half the "fun" of Windows was always thinking about threats and how to mitigate them.  I stopped with WinXP and still have that on my dual boot WinXP/Ubuntu 14.04 system.  I still have a program on my XP drive called Norton Go Back, which I have read that many people hated much.  I have never had a problem with it.  On a number of occasions, when I have suspected some issue due to malware or virus, I was able to reboot easily and restore every sector on my hard drive to a few minutes, hours or days earlier.  It's nice to have tools that mitigate threats and can calmly "rewind" to an earlier time if necessary.  Much better than throwing your computer at the wall out of frustration.  Of course, I also always had the best Internet Security programs that money could buy.

Many users don't have the inclination or time available to deal with these things on a continuing basis, so they might end up like a friend of mine that received the malware message about a virus that was (but not really) on his system, called the phone number and ended up giving remote access to his system to a scam outfit.  Yes, it was a Windows computer.  Luckily he lost only a little money, not his identity to the thieves (at least not to this date).  

All indications that I can see from many sources show that the risks with Ubuntu are minuscule by comparison.  Some risk always exists, and all computer users should stay informed.  It is a question of how much time and effort must be invested.  This is real "overhead" to productive work and use of resources.  The overall cost is enormous.  Not so with Ubuntu!  I hope it is never contaminated with Windows risks.

Freedom Indeed! :D

Regards

---

### Post by ventrical on 2016-05-02
I would say that from 1992 to 2010 the lore of malware/virus consumed 70% of user_time space. It was so much so for me that 90% of my time was devoted to protecting and cleaning other peoples systems. Windows malware was so prevalent that I was even forced to second my time away from working with Linus Torvalds and his LINUX project in 1995 on the FIDO network echo forums.

  I was not one that had much money to throw away on expensive security suites and so I had to improvise. I admit it was intriguing.. umm .. perhaps even fun but it was not why I went to university to study programming. I did not aspire that I would one day be spending most of my time cleaning malware. Ok .. I confess.. I got used to it.  I became very proficient at manually removing crapware. 

btw . .those fake 'windows' ITs representing Microsoft are still out there. They still call me. There are a lot of people I know they call and a lot of people still get duped.

regards..

---

### Post by ventrical on 2016-05-02
> **grahammechanical said:**
> It underlines the importance of replacing X Server. I don't remember anybody speaking of the vulnerabilities in X Server until someone wanted to replace it with something else. Then we started to get all the talk about why we need a replacement.

How many times have we heard the expression "An accident waiting to happen" and "Someone will have to die before something is done about this?"

Regards

I have read some 'scratch the surface' proof of concept' snippets about this. Perhaps snappy_personal with mir will lock these problems down or even a more secure xserver.

Regards..

---

### Post by DMcCunney on 2016-06-04
What Canonical has done is work with MS to develop libraries that will be used in providing bash and friends in a CLI under Windows.  This [i]won't[/t] be a full GUI Ubuntu installation.

It's possible to get bash and friends now via other means.  One way I used to run is to install Cygwin.  Cygwin is a project of Cygnus Development (which is part of Red Hat these days) to host a full Gnu/Linux toolchain under Windows, with GCC and all of the associated development utilities.

Rather than rewrite everything to use Windows runtimes, the Cygwin developers created a POSIX emulation layer and encapsulated it as a DLL.  A lot of *nix code builds under Cygwin "out of the box", because it links against the DLL and sees the *nix system calls it expects.  There was a beta project back when to get KDE under Windows using Cygwin, and it did actually run.

The problems with Cygwin are speed, and the differences between Linux and Windows from a command line.  Speed can be an issue because there aren't Windows equivalents of some *nix syscalls, and they must be emulated.  ("fork()" is a thorny example.)  How fast your code will run will likely depend on exactly what it does and what *nix calls it tries to use.

At a command line, in a terminal, you run into problems with things like path delimiter chars (because / in Windows is an option prefix, and  is a path delimiter) and the fact that bash doesn't like files with spaces in the name, so quoting is required.  There are various work arounds and wrappers in Cygwin to make it easier to deal with native Windows stuff from withing bash.

More recently, we've gotten MinGW and MSYS.  MinGW is GCC built to compile using native Windows runtimes, and MSYS is a set of utilities similat to what Cygwin offers.

What I have at the moment is provided by the Git for Windows implementation, which appears to be based on the MinGW/MSYS work.  It installs a version of git that runs native on Windows, and includes bash and friends as part of the package.

I run Win10, and I'll be curious to see what MS did when this stuff gets released as part of an official update.

(I'll be startled if MS actually tries to buy Canonical, and more startled if Canonical accepts if they do.)
______
**Dennis**

---

