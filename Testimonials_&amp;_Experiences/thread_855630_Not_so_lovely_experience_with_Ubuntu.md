---
title: "Not so lovely experience with Ubuntu"
date: 2008-07-10
forum: Testimonials &amp; Experiences
---

### Post by parlance on 2008-07-10
Hi. I'm a long time Windows user who decided recently to load Ubuntu onto an old machine to use it as a basic desktop and backup storage space.

I've used various linux distros briefly over the last 8 years, usually starting out with excitement and always coming away with a bad taste in my mouth. I've heard a lot of good things about Ubuntu and how it is solving all the problems that desktop users have had with linux in the past so I thought I'd give it a try.

So here we go. I downloaded and burned the install / live CD disc for Ubuntu 8.04.1 (AMD64 version). The first thing I notice when going to install it is that there *still* isn't any hardware RAID support. I was hoping to this machine as a backup storage device so data integrity is important to me. I looked around at a few different ways to setup software RAIDs with Ubuntu but the only ways to do this involved a lot of terminal / configuration file editing so I decided to just say **** it and move on with a standard installation.

I noticed that you can actually use all the features of the live CD while installing Ubuntu. I thought that was kind of neat, I guess.

Installation completed I'm logged in and I see Ubuntu has let me know that it could use ATI drivers for my video card (ATI HD 2400XT) to improve performance, I allow Ubuntu to download and install them and I reboot afterwards. I rather liked the simple notification and install process.

I get back into Ubuntu and I go to turn on graphical effects on my desktop because I've heard a lot of good things about how Ubuntu can look so much better than Vista with a lower resource footprint. For a few moments I am able to experience wobbly windows, sliding between desktops, fading menus and it looks pretty good, again, this is a good thing.

And then it freezes. I can still move my mouse around but the desktop has completely locked up. I tried conventional key combinations to see if there was a way to terminate and perhaps restart X / Gnome but to no avail. With a **deep sigh** I hard restart the machine. I am able to login again but without fail the desktop will freeze within 2 seconds of clicking on anything. Please note to the billion people who would reply to this to suggest there is a problem with my hardware configuration: No, everything works fine in Windows and is 100% stable 100% of the time outside of Ubuntu.

Wow, so here I am with a permafucked Ubuntu installation within 15 minutes of installation. At this point I could either scour these forums and other places for a fix to this kind of inane problem, probably involing dropping to a terminal and manually editing score configuration files scattered all over the place, or I could reformat the system and hope it doesn't happen again, **or** I could just give up and remember that Linux still doesn't live up to its heavily evangelized promises.

Thanks guys, I'd like the last 4 hours of my life back.

tl;dr Linux *still* sucks.

---

### Post by jimv on 2008-07-10
Linux is hit and miss, no doubts about that.  It runs like a dream on my desktop, but needed a lot of tweaking on my laptop.

ATI support sucks currently, even with the official drivers.  Also, a lot of people have been reporting lockups in the most recent release of Ubuntu.  I solved the issue on my laptop by installing the -RT kernel.  Of course, you shouldn't have to install a different kernel to get your OS working correctly.

The only thing I'd recommend is trying the 32 bit version and see if you fair any better.

---

### Post by dracayr on 2008-07-10
try booting safe mode>repair x server

dracayr

---

### Post by Sealbhach on 2008-07-10
> No, everything works fine in Windows and is 100% stable


Sorry to hear that.

You might as well stick with windows then. Looks like your hardware is not compatible.


.

---

### Post by parlance on 2008-07-10
> **dracayr said:**
> try booting safe mode>repair x server

dracayr

I did that before I posted the first message. What happened after the repair was instead of seeing my desktop after the login screen where it would freeze AFTER I clicked on anything I just got a completely white screen instead (still able to move and see the mouse however).

---

### Post by dracayr on 2008-07-10
can you still switch to tty using Ctrl+alt+F[1-6] ?

if not, can you still reboot using the linux kernel magic keys:

Alt+Sysrq+R+E+I+S+U+B

?

dracayr

---

### Post by parlance on 2008-07-10
> **Sealbhach said:**
> Sorry to hear that.

You might as well stick with windows then. Looks like your hardware is not compatible.


.

This is the other cliche response I expected to hear from "Linux" people. If anything goes wrong it must be because you're using obscure hardware or a weird system configuration or etc (basically, it isn't Ubuntu's fault).

My hardware profile configuration is extremely common and and is in no way atypical, that's the part that is perhaps the most distressing and the reason why I see this kind of buggy behavior as a huge smudge on the face of the desktop linux community.

Of course I don't expect perfect compatibility with obscure hardware, but we're talking about an Nforce chipset with a common and new ATI graphics card and common AMD processor.

And that completely aside, failure of this kind should never be fatal to the level that it was. Where the hell is the driver or settings rollback in the recovery menu? (as it suddenly dawns on the linux evangelists that maybe a neatly organized tree of well defined data elements for software and hardware settings (windows registry) is better than thousands of scattered configuration files in different formats).

For that matter, there is basically nothing useful in the recovery menu at all unless you're familiar with the intimate details of the OS and could solve a problem like this from the terminal. I'm not saying Windows's safe mode is perfect either it seems to be infinitely more useful than anything Ubuntu has to offer at the moment and in the interest of robustness I'd say Ubuntu should put a higher priority on something similar.

How am I supposed to recommend Ubuntu to anyone I know with a straight face after seeing this kind of stuff?

---

### Post by parlance on 2008-07-10
> **dracayr said:**
> can you still switch to tty using Ctrl+alt+F[1-6] ?

if not, can you still reboot using the linux kernel magic keys:

Alt+Sysrq+R+E+I+S+U+B

?

dracayr

I tried that before posting the first message as well, but no, I could not.

---

### Post by dracayr on 2008-07-10
checked your xorg.0.log?

dracayr

---

### Post by L0cKd0wN on 2008-07-10
What's performance like when you're not using compiz-fusion (special windows effects)?  

And, I'm probably not the only one thinking this when I read it, but I would hardly relegate Ubuntu to the same heap that you'd classify the other distributions you've "used" over the past 8 years.  

This is clearly a configuration problem on your end.  (Coincidence that you're using an ATI card?)  Anyway, I can appreciate that you're frustrated as anyone would be, but reading the same old tired complaints that GNU/Linux hasn't changed in a decade (and "sucks") is childish and, quite frankly, retarded.  Leave the attitude out of your post or just go back to Windows.  You may not deserve Ubuntu.

---

### Post by Vadi on 2008-07-10
That's unfortunate, and thanks for letting us know!

---

### Post by parlance on 2008-07-10
> **dracayr said:**
> checked your xorg.0.log?

dracayr

No, I haven't, because I don't know what that is. I'm not trying to make the point that my problem isn't fixable, because I'm sure that it is.

My main point is that Ubuntu will never amount to anything more than a cute novelty unless the roots of these kinds of problems with robustness are addressed. Windows does this to people too of course, it just usually takes longer than 15 minutes to reach that point and the tools they include to recover from something like this are usable by average users. I **am** capable of sifting through logs and editing configuration files, my girlfriend however is not, etc.

---

### Post by parlance on 2008-07-10
> **L0cKd0wN said:**
> What's performance like when you're not using compiz-fusion (special windows effects)?  

And, I'm probably not the only one thinking this when I read it, but I would hardly relegate Ubuntu to the same heap that you'd classify the other distributions you've "used" over the past 8 years.  

This is clearly a configuration problem on your end.  (Coincidence that you're using an ATI card?)  Anyway, I can appreciate that you're frustrated as anyone would be, but reading the same old tired complaints that GNU/Linux hasn't changed in a decade (and "sucks") is childish and, quite frankly, retarded.  Leave the attitude out of your post or just go back to Windows.  You may not deserve Ubuntu.

It's this kind of arrogant attitude that is going to prevent Ubuntu from reaching mainstream viability as a desktop operating system. "If you have problems and can't use a terminal to fix them then screw you!".

To be honest my tone might be a little harsh here and I apologize because I am speaking out of frustration. Taking a step back and looking at it with a bit more of a level head I am going download and try using the standard i386 distribution and see if my luck improves.

---

### Post by Vadi on 2008-07-10
Um, did someoene ask you to come here argue this point?

It's not usable for you, fine. It is usable for millions of others though, so don't try and prove that everyone is wrong.

Don't like it - here's your refund of $0, sorry for the wasted time, but now you know. See you!

Edited: Or I hope you have better luck with the other method, but if it doesn't work, don't stress :)

---

### Post by dracayr on 2008-07-10
well in most cases, your girlfriend won't have too... Ubuntu normally *works*, you know ;)

Now, what if this happened to you on windows? There are not many possibilities to correct such an error in windows. 


The real problem is that the hardware industry manufactures their hardware for windows, not for linux... This is a problem with the hardware industry (and everyone who buys PCs), not with linux. If the hardware is made for linux, nothing ever fails :) precisely the reason servers run linux

dracayr

---

### Post by parlance on 2008-07-10
> **Vadi said:**
> Um, did someoene ask you to come here argue this point?

It's not usable for you, fine. It is usable for millions of others though, so don't try and prove that everyone is wrong.

Don't like it - here's your refund of $0, sorry for the wasted time, but now you know. See you!

Edited: Or I hope you have better luck with the other method, but if it doesn't work, don't stress :)

Well even if it may well work for millions of others, Ubuntu is relying on word of mouth at the moment to build it's reputation. 

Just as an example I was telling my girlfriend about how Ubuntu could breathe a lot of performance into her old laptop which is routinely infested with spyware and has shoddy performance with XP in general; she really only uses it to browse the web, download music, etc. Before I had this experience I was feeling very confident that everything I had heard about Ubuntu was going be different than the pre-2000 Linux experience, but afterwards I have to worry that it may not work well or at all for her and end up reverting her laptop back to XP, which is a nontrivial amount of work.

I too am hoping that I have better luck with the i386 version. I'm mad because I **want** it to work.

---

### Post by Vadi on 2008-07-10
Also, I've heard the alternate cd can perform better in some configurations where the usual one fails. But if you'll have any problems, feel free to post.

---

### Post by parlance on 2008-07-10
> **dracayr said:**
> well in most cases, your girlfriend won't have too... Ubuntu normally *works*, you know ;)

Now, what if this happened to you on windows? There are not many possibilities to correct such an error in windows. 


The real problem is that the hardware industry manufactures their hardware for windows, not for linux... This is a problem with the hardware industry (and everyone who buys PCs), not with linux. If the hardware is made for linux, nothing ever fails :) precisely the reason servers run linux

dracayr

If this happened in Windows? The problem was caused by some kind of bug related to the interoperation of the proprietary ATI graphics driver and the advanced visual effects being enabled in Gnome. If this happened in Windows I could easily boot into safe mode (disables proprietary graphics driver but still displays a user friendly interface) and I could roll back the driver using a nice GUI.

---

### Post by phidia on 2008-07-10
I'm not into the argument end of this but > If this happened in Windows I could easily boot into safe mode (disables proprietary graphics driver but still displays a user friendly interface) and I could roll back the driver using a nice GUI. is exactly possible with ubuntu too. You boot into failsafe and disable compiz and/or the ATI driver and logout-in.
And to be in the argument it isn't the linux communities fault that people often come to linux expecting there to be no learning curve-no reading-and everything works just like they're use to.

---

### Post by jimv on 2008-07-10
> **parlance said:**
> It's this kind of arrogant attitude that is going to prevent Ubuntu from reaching mainstream viability as a desktop operating system. "If you have problems and can't use a terminal to fix them then screw you!".

Just need to correct a few misconceptions:

First, Linux has no goals.  It's not here to make money, it's not trying to gain market share.  It just IS what it is, and if people start using it more, that's exciting, but it's not a goal.

Second, calling people who're trying to help new users "arrogant" isn't going to get you much help.  No one on this board is paid to help anyone...it's all charity from people interested in Linux.  No one really cares if you use Linux or not, so there's not much incentive for good attitudes aside from just being nice.

---

### Post by Vadi on 2008-07-10
Well, it sorta does - popularity would make more cross-platform apps / better compatible hardware.

---

### Post by Sealbhach on 2008-07-10
If Linux devs havent't been given the information to make your hardware work, what can we do?


.

---

### Post by Mrmental on 2008-07-10
I've got to say, Ubuntu Hardy is by far the most frustrating version of the OS I've ever encountered. 
I say this not a newbie who doesn't know anything about it, but as someone who has been using GNU/Linux in various for nearly five years. I've managed to cure Hardy of its random freezing problem* but now it's frustrating me on mpeg playback. There are dozens of niggling little issues I've found that really stack up badly.

It's such a shame because I adore Ubuntu, on the whole. Ubuntu Hardy, however, is the one version of Ubuntu I would not recommend to my Windows using friends. Indeed, it is the one version of Ubuntu I won't show off to people in case it crashes embarrassingly.

I'm not a serious programmer by anybody's standards, and Lord knows I couldn't write an OS, but it seems to me that Hardy just has too many bugs to be considered a production-ready OS. The crashing randomly without an experimental Kernel is especially bad, as when it freezes it gives no errors, leaves no logs, and it more or less un-recreatable.
I'm not trying to go down the "boo-hiss, Hardy sucks" route, because I know that a lot of people have given a lot of their time to make it what it is, and receive very little credit for their trouble. That said, I am disappointed. I'm especially disappointed because Hardy is so great when it's actually working.
Sam B

*(By installing the rt kernel. It might work for the poster, although I tried it on 1386, it may not work for amd64.)

---

### Post by bmac on 2008-07-11
Why does the forum continue to respond to the incidental few that feel somehow they have been slighted by Ubuntu. "Hello", it's an OS...

If Ubuntu doesn't work for you, find something else. Bashing Ubuntu because your system isn't compatible, reeks of bad behavior. Not to mention it's annoying to the rest of us that have found Ubuntu fully functional and haven't whined every time we had a problem. 

I started with 3.1 and quit with Vista. Since that time I've installed Ubuntu on my 4 systems and numerous machines belonging to friends and family. Not one of those machines failed or experienced any issues that I couldn't solve with the help of this forum. All the issues were relative simple and none of the machines I've converted to Ubuintu have returned to M$. 

Gee, a success story - imagine that. From Feisty to HH, I've enjoyed the experience and all it cost me was a little time, an open mind and a desire to learn (still learning). Amazing....

In my opinion, it's just petty to complain about an OS compatibility issue when so many OS's are available. The Linux list alone would keep one busy for awhile. At least longer than 4 hours.... Sometime I wonder if it isn't just Ubuntu envy...:cry: 

I suggest we express some apathy the next time someone feels the need to bash Ubuntu. Imagine if no one responded to this post and only the OP continued bumping it.... Doesn't that bring a smile to your face? We must stop patronizing these types of posts or risk perpetuating them... Including this post....


Just a thought....

---

### Post by mdsmedia on 2008-07-11
Have you had a look at this thread? Similar problem, different advice.

I've pointed you to page 4 of the thread. It basically sums it up.

[http://ubuntuforums.org/showthread.php?t=854423&page=4](http://ubuntuforums.org/showthread.php?t=854423&page=4)

---

### Post by Canis familiaris on 2008-07-11
> **bmac said:**
> Why does the forum continue to respond to the incidental few that feel somehow they have been slighted by Ubuntu. "Hello", it's an OS...

If Ubuntu doesn't work for you, find something else. Bashing Ubuntu because your system isn't compatible, reeks of bad behavior. Not to mention it's annoying to the rest of us that have found Ubuntu fully functional and haven't whined every time we had a problem. 

I started with 3.1 and quit with Vista. Since that time I've installed Ubuntu on my 4 systems and numerous machines belonging to friends and family. Not one of those machines failed or experienced any issues that I couldn't solve with the help of this forum. All the issues were relative simple and none of the machines I've converted to Ubuintu have returned to M$. 

Gee, a success story - imagine that. From Feisty to HH, I've enjoyed the experience and all it cost me was a little time, an open mind and a desire to learn (still learning). Amazing....

In my opinion, it's just petty to complain about an OS compatibility issue when so many OS's are available. The Linux list alone would keep one busy for awhile. At least longer than 4 hours.... Sometime I wonder if it isn't just Ubuntu envy...:cry: 

I suggest we express some apathy the next time someone feels the need to bash Ubuntu. Imagine if no one responded to this post and only the OP continued bumping it.... Doesn't that bring a smile to your face? We must stop patronizing these types of posts or risk perpetuating them... Including this post....


Just a thought....

well said

---

### Post by arandomkiwi on 2008-07-11
Run a virtual machine(ubuntu 8.04) on your windows and see how you will like ubuntu the. :]

---

### Post by Canis familiaris on 2008-07-11
> **arandomkiwi said:**
> Run a virtual machine(ubuntu 8.04) on your windows and see how you will like ubuntu the. :]

Especially if you get [this]("http://amitech.50webs.com/ultimate.html")

---

### Post by steveneddy on 2008-07-11
I read the thread up to here.

So, basically, you didn't do any hardware research and when a piece of hardware doesn't work right, the whole distribution sucks.

Hardy works fine on my laptop.

I use 64 bit.

If the ATI graphics card isn't working with Compiz, which looks like the main reason you installed it anyway, then leave Compiz (the eye candy) turned off.

Many people have said before that hardware compatibility with any operating system is as important as the operating system.

If your hardware doesn't work well with Linux, either change to a different Linux distro, leave the desktop effects off, or go back to Windows.

Ubuntu Linux works very well for millions of users worldwide, and rants like yours are splattered about in these forums daily. So, **you didn't ask for help**, and now it's our fault?

The advice here is free, as was the OS, so maybe you would prefer to have paid support, like Windows, so you can call someone and tell them that you aren't happy with the operating system you downloaded for free.

Here's the link:

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

Now please post a support question in the appropriate area so that those that are familiar with the ATI graphics issues can help you.

BTW, those of us who have the best luck with Ubuntu and Linux in general have made sure that the hardware is compatible with Linux, just like you would do if you were buying a Windows system.

Hardware vendors are out there who can help you with a prebuilt system that has Ubuntu already installed. I bought a laptop from

**[www.system76.com](www.system76.com)**

so I could have a laptop that I knew worked with Ubuntu. 

You know what? It works great!

Good luck.

---

### Post by hyper_ch on 2008-07-11
> **parlance said:**
> If anything goes wrong it must be because you're using obscure hardware or a weird system configuration or etc (basically, it isn't Ubuntu's fault).
Well, did you consider it might be a hardware problem? ATi is known for not working nicely on linux ;) So it's ATi to blame... 

> **parlance said:**
> My hardware profile configuration is extremely common and and is in no way atypical,
What is common? What is atypical? One could also say a lot of extremly common devices do not run on VISTA either.. so this "common" and "atypical" doesn't help a dime ;)

> **parlance said:**
> a neatly organized tree of well defined data elements for software and hardware settings (windows registry) is better than thousands of scattered configuration files in different formats).
That comment just made me laugh... windows registry "neatly"? ^^ what different formats of configuration files? They are all text files ;) and there's basically only two places you need to look for depending on whether it's system-wide or user-related ;)

> **parlance said:**
> For that matter, there is basically nothing useful in the recovery menu at all unless you're familiar with the intimate details of the OS and could solve a problem like this from the terminal. I'm not saying Windows's safe mode is perfect either it seems to be infinitely more useful than anything Ubuntu has to offer at the moment and in the interest of robustness I'd say Ubuntu should put a higher priority on something similar.
Boot the live cd, ask on forums, irc, ...... way more helpful than the windows recovery menu


> **parlance said:**
> How am I supposed to recommend Ubuntu to anyone I know with a straight face after seeing this kind of stuff?
Who expects you to recommend it?

> **parlance said:**
> My main point is that Ubuntu will never amount to anything more than a cute novelty unless the roots of these kinds of problems with robustness are addressed.
I'd vote for powering off for 1 day all linux devices in the world... (Good-bye internet) - so much for "novelty"... as you might not know, there are way more devices running linux out there than windows, so much to "cute novelty".

> **parlance said:**
> Well even if it may well work for millions of others, Ubuntu is relying on word of mouth at the moment to build it's reputation.
Ubuntu has already a very good reputation ;)


> **parlance said:**
> Just as an example I was telling my girlfriend about how Ubuntu could breathe a lot of performance into her old laptop which is routinely infested with spyware and has shoddy performance with XP in general; she really only uses it to browse the web, download music, etc.
Well, ubuntu can do that ;)

> **jimv said:**
> First, Linux has no goals.  It's not here to make money, it's not trying to gain market share.  It just IS what it is, and if people start using it more, that's exciting, but it's not a goal.
Linux does not... Ubuntu does... see Ubuntu Bug #1

---

### Post by Mrmental on 2008-07-11
"It's the hardware's fault." is not a reasonable excuse for something not working on the latest version of an OS when it worked on the last version.
Ubuntu is an OS, not a religion. If something doesn't work, one gains precisely nothing by ignoring it or being an apologist for it. 

Dealing with the problems I've had with Hardy, I've encountered rather snotty replies to honest questions from other posters over and over again. They usually follow the same pattern:

"Well, mine works just fine, it must be your hardware."
"You should learn how to use Linux before you install it."

and my all-time favourite:

"Just because you're an <insert insult here> doesn't mean it's Ubuntu's fault."

I shouldn't need to point out to an educated reader the problems with these arguments. They're not arguments at all, you see. They're merely defensive little pieces of non-communication that we could all do well without.

I don't consider myself an Ubuntu basher; Ubuntu is my primary OS and my experience on the whole has been overwhelmingly positive. Hardy has shaken my faith in it, but I'm not ready to abandon it for one middling release after a series of excellent releases.
That said, I have had problems with Hardy, and when I express my opinion in civil terms I expect to be answered in civil terms, or not at all. I think everybody else is entitled to the same expectation.
Peace
Sam B

---

### Post by Vorian Grey on 2008-07-11
> **steveneddy said:**
> 
If the ATI graphics card isn't working with Compiz, which looks like the main reason you installed it anyway, then leave Compiz (the eye candy) turned off.


Yeah, that's what I was thinking. Compiz is nice and all but not really necessary.

---

### Post by hyper_ch on 2008-07-11
well, he's using ATi and ATi is known to perform poorly on Linux in general as the drivers aren't open and the devs aren't given the specs... so it is the hardware ;)

---

### Post by armandh on 2008-07-11
some dogs just wont hunt
and you never know until you try 'em
first thing I would have done is tried a well supported video card from the spare parts box. last time that cured a problem.
but my last time with a lock up problem [?] was using totem 
I got impatient and kept clicking. 
better luck with whatever


we are assuming enough and good mem right?
almost all of my problems have been hardware or me.

---

### Post by steveneddy on 2008-07-12
> **armandh said:**
> some dogs just wont hunt
and you never know until you try 'em
first thing I would have done is tried a well supported video card from the spare parts box. last time that cured a problem.
but my last time with a lock up problem [?] was using totem 
I got impatient and kept clicking. 
better luck with whatever


we are assuming enough and good mem right?
almost all of my problems have been hardware or me.

I will agree that some of it may be software.

But my experience is that the machine in question has unsupported, partially supported or poorly supported hardware in Linux or Ubuntu.

Some hardware works better with other distributions.

You don't have to stay with Ubuntu. Try OpenSUSE or Redhat. Those are great Linux releases that may give you better results with hardware that is buggy under Ubuntu.

And yes, having enough memory is a key factor in Windows, Linux or Mac installs.

---

### Post by L815 on 2008-07-12
There are a lot of complaints of ATI drivers for Linux. It's not surprising it didn't work well with compiz. Try turning it off and seeing if it helps any.

---

### Post by Mechaphoenix25 on 2008-07-12
Personal suggestion: if you like Ubuntu, and are able to manually fix it by changing config files, by all means do so, Linux without customization would be to a large degree defeating the entire purpose.  If your point is that your girlfriend can't use Ubuntu without doing so, then I think most people already know this, Ubuntu is designed to work mostly without the command line, but a few fixes and tricks still rely on it, and I (on a solely personal level) prefer it that way myself.  Being able to think "I want a play icon for my website" and type in

eog $(locate play | grep svg)

and get a browse-able filmstrip of results in 5 seconds, not to mention ones that I can freely put up on my website (without copyright hassles), is something I just plain can't do normally in windows (without Cygwin at least).  If you want a Linux distro that doesn't touch the command line, I'd recommend **Linux Mint**, I've seen it work beautifully, even be confused for an XP theme at first sight.  See [http://www.fsckin.com/2008/01/10/state-of-affairs-the-linux-girlfriend-project-two-months-in-the-trenches/](http://www.fsckin.com/2008/01/10/state-of-affairs-the-linux-girlfriend-project-two-months-in-the-trenches/) which appears to be a rather amusingly similar case to yours if I do say so. :)

Best of luck to you, and if nothing else you can always dual boot, (Ubuntu HH/Vista HP myself by the way).

---

### Post by Jadd on 2008-07-12
> **Mrmental said:**
> "It's the hardware's fault." is not a reasonable excuse for something not working on the latest version of an OS when it worked on the last version.True, partially. Actually, it's not the hardware's fault, it's the driver's fault. When you installed ATI's closed-source freedom restricting driver, this disclaimer was clearly displayed:
"Proprietary drivers do not have public source code that Ubuntu developers are free to modify. They represent a risk to you [...] Ubuntu cannot fix or improve these drivers"
> Ubuntu is an OS, not a religion. If something doesn't work, one gains precisely nothing by ignoring it or being an apologist for it.Ubuntu is community driven project, and it's also a philosophy. What are *you* gaining by doing precisely nothing by ignoring or being an apologist against it? 

> Dealing with the problems I've had with Hardy, I've encountered rather snotty replies to honest questions from other posters over and over again. They usually follow the same pattern:What questions? You never asked a question, to my memory, you just stated your opinion, and then we stated ours, offering advice. There's what you got from a discussion forum.

> "Well, mine works just fine, it must be your hardware."Not 'snotty', the poster just stater their opinion just like you stated yours. Their opinion is as valid as yours.
> "You should learn how to use Linux before you install it."Nobody said that.

> and my all-time favourite:

"Just because you're an <insert insult here> doesn't mean it's Ubuntu's fault."Nobody said that either, although I admit one member did call you childish.

> I shouldn't need to point out to an educated reader the problems with these arguments. They're not arguments at all, you see. They're merely defensive little pieces of non-communication that we could all do well without.The problem is that these arguments are straw men. Besides, we're not in an argument, are we? Is this even a debate?

> I don't consider myself an Ubuntu basher; Ubuntu is my primary OS and my experience on the whole has been overwhelmingly positive. Hardy has shaken my faith in it, but I'm not ready to abandon it for one middling release after a series of excellent releases.
That said, I have had problems with Hardy, and when I express my opinion in civil terms I expect to be answered in civil terms, or not at all. I think everybody else is entitled to the same expectation.
Peace
Sam BPrecisely. Bashing Ubuntu is one thing, but bashing people on this forum is another (even if you never mentionned one by name), and is technically a violation of the Ubuntu Code of Conduct, and this forum's guidelines.

I myself posted a thread here expressing my [disappointment with Hardy Heron](http://ubuntuforums.org/showthread.php?t=766997), but I didn't blame anyone for sharing their experiences, for trying to help me overcome the problems, for blaming hardware manufacturers, (even when I felt it was clearly Ubuntu's fault) or for suggesting that Windows might suit me better.

I recommend that this thread be closed. We heard your opinion, we've stated ours.

---

### Post by CC_machine on 2008-07-12
#1: whilst ATI's drivers have been improving, they still suck for a large number of their cards.

__especially on 64bit__

#2: guess what? desktop effects are unstable on bad drivers. and since they need to take control of the screen (and the core of X.org) they can result in a complete system lockup.

so either disable desktop effects or install the 32bit edition. or upgrade to a nvidia card. =]

---

### Post by Methuselah on 2008-07-12
I'm sorry to hear your ubuntu experience wasn't good.
It happens that way sometimes.

Personally, I'm very happy with it.
My only annoyance is 3D not being supported with my ATI card.

---

