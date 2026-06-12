---
title: "How do you see &quot;Linux Hater's Blog&quot;"
date: 2008-07-18
forum: The Cafe
---

### Post by Jim! on 2008-07-18
[http://linuxhaters.blogspot.com/](http://linuxhaters.blogspot.com/)

How many people here read this? Personally I think this guy makes some great points and knows exactly what he's talking about.

For those of you that can't be bothered checking out the link heres his latest 'article':

> The fallacy of choice

I'm sure by now I don't really have to describe in detail this phenomenon: Whenever you criticize a luser about his choice of OS, he'll inevitably come back with, "at least it gives me choices." Choice in window manager, choice in terminal application, choice in file manager, choice in desktop environment, choice in kernel version, you name it.

This "choice", as loudly as it is trumpeted, is a key reason that Linux has not made it on the desktop. Let me attempt to show you why.

Every argument for "choice" is usually accompanied by a statement along the lines of, "there are many different kinds of users that prefer different choices, therefore we need to support all of them." In terms of distribution of choices, given 10 choices, this statement implies the following type of distribution.

[IMG]http://bp2.blogger.com/_0mQ1y_9kwxI/SH7Tf3RjCsI/AAAAAAAAAA8/2V1g8Ng4VxQ/s1600-h/equalchart.png[/IMG]

> In other words, ten equal choices with ten roughly equal-sized groups each preferring a different choice. For some limited version of the world, this may be true (for example, existing people who are FOSS users already, fighting amongst themselves). But if you look at the general population at large, I claim a different picture emerges:

[IMG]http://bp0.blogger.com/_0mQ1y_9kwxI/SH7TZcbHaCI/AAAAAAAAAA0/RhK5YCl024w/s1600-h/majoritychart.png[/IMG]

> Here, the blue represents the people who don't care about a particular choice, and actively do not want to have to make a choice. They just want things to work. They will take "working" over "choice" in an instant. They essentially want the developers to make choices for them.*

Linux and FOSS so far have optimized for the former picture of the world, not the latter. In doing so, they've concentrated on inserting abstraction layers and decoupled mechanisms at every layer of the stack: kernel, graphical toolkit, command line shell, terminal program, text editor, office suite, window manager, desktop environment, sound system, etc. etc.

In adding choice after choice, Linux moves farther and farther from what the mainstream user wants.

Furthermore, any developer will tell you that each time a new layer of "choice" is added, the possible number of configurations multiplies. This means more untested configurations, more bugs, and more brokenness. Not necessarily due to incompetence of developers, but rather simply due to the sheer number of configurations that are possible.

So not only does the addition of so many choices alienate would be users, it also makes it difficult for developers to create tested, working configurations. It's a double whammy. Obsession with providing choice it every level actively works against efforts that would otherwise push Linux to provide what the mainstream wants.

Look at OSX. The amount of choice you have in OSX is minuscule compare to what you get with Linux. Yet, do you see the majority of mac users complaining? Look at the internet, look at how IE still has a huge market share. People like to think that it's because people don't know any better and that they need to be educated. My experience says otherwise. People don't care. They want what works for them. For the vast majority of cases IE works for people. It may not be optimal, but people just don't care.

I've said it before, and I'll say it again. Even current lusers don't want choice between two or more options that are broken. They want a working baseline, and then they want to be able to make all the choices they personally care about. Unfortunately, there are very few projects that are concentrated on developing this working baseline. Instead they usually try to build one small piece of the puzzle, then make it interface with as many other parts in numerous and useless ways.

Let's look at the server side. Why does Linux succeed here? One of the big reasons is that there is a working baseline. Everyone knows what it's called: LAMP. If in doubt, start with LAMP. Yes, there are still other options. Different webservers, different databases, different programming languages, even different OS'es (WIMP anyone?). The point is that if you don't want to make any of these choices, and instead you want a proven base starting point, you have one.

Unfortunately on the desktop side, no such "non-choice" choice exists. In addition, there are many more pieces that need to work together to provide a friendly experience. What is the LAMP of the desktop? Whatever it is, it's going to have a lot more letters. I claim it still doesn't exist. Everyone disagrees what the desktop should be. Everyone wants choice. Everyone except the mainstream users that the desktop is supposed to be built for.


* In some sense, distros try to do this. But this fails for a few reasons. 1) There are too many distros. 2) Distros aren't the ones with the expertise to make the right choices.

What do you think?

**EDIT: For some reason the images aren't showing, so this article won't make complete sense to you unless you visit the link.**

---

### Post by MaxIBoy on 2008-07-18
I'd like to counter this guy's argument. 

[LIST=1]
[*]Many people would love to have those choices if they knew they were available.
[*]So you mean we're all going to have to agree on a standard configuration? No way! Many of these are developed by a community, not a company, or with help from both. The only way you can get a community to agree to work together is if each member gets what he wants. That means reconfigurability. If we forced all users of Ubuntu derivatives to pick one desktop environment, majority rule, and the loosers have to leave, the Ubuntu family of distros would disappear. Perhaps the sole remaining Ubuntu would carry on, but without the support from those who used Kubuntu or Xubuntu. After all, these people are contributing to every Ubuntu variant, not just theirs.
[*]There are so many configurations which don't have any kind of impact on how buggy a system is (the choice of gtk+ or emerald themes being examples.) Not even these choices are available on Windows or Mac.
[*]Many of these plugins (such as Compiz) are their own projects, with an entire community just for them. It is the responsibility of Compiz's development team to make sure that it works well on as many platforms as possible. You might say it's more work, and it probably is, but they seem to be doing fine so far. I haven't had any problems with it (okay, I have, but they were easily fixable with help from people on this forum, and it was my mistake that caused them.)
[*]One of the great things about Ubuntu's development model is that the developers collaborate with the community. Bug reports are actually responded to and sometimes the problems are even fixed by community members. This development model isn't unique to Ubuntu, and it works very well wherever it's used.
[*]Setting up a vanilla system without any customization is quite easy; people on forums like these are very willing to help those who do want to customize.
[*]There are distributions which are designed to "just work" (such as the Knoppix live CD or Ubuntu,) and there are distributions which are designed for hobbyists who like to tinker (like Gentoo and Arch.) It's a matter of personal preference. I would not say that these are "warring factions" at all; undoubtedly there are many here who dual-boot Ubuntu and Arch, and use the Knoppix CD occasionally when they need a liveCD environment. I bet that there are plenty of programmers who actively contribute to multiple distros. I think they've done a fine job so far.
[*]Most people expect that they can have the freedom to use an operating system on any hardware configuration possible, but OS X is only legally usable on Mac hardware (which is overpriced.) Not even Microsoft does that. 
[/LIST]

---

### Post by Morty007 on 2008-07-18
There is a much simpler reason.

People are sheep. They take what they are given and what is most widely publicized. Hence Windows or Mac.

---

### Post by vikramaditya on 2008-07-18
Let's just forget the "choice" dynamic for now.  It can be argued that a so-called "mainstream" user would be pleased enough with the default configuration of any *buntu distro, dutifully installing updates as prompted, yet seldom exploring "advanced" options.

---

### Post by Yes on 2008-07-18
He makes it seem like the devs are adding choices for the sake adding choice, which I don't think is right - I think when a dev decides to add a choice (new WM, new music player, etc.) they're doing it because they want to use that new choice, and they're just kind enough to release it to the public so that we might enjoy it too.

Why should we be catering to the "mainstream user"?  I love the choices in Linux, I think that the number of choices is one of the most important features Linux has.  If that means that it never gets the "mainstream user", so be it.

---

### Post by aktiwers on 2008-07-18
Haha I have read this blog for a while..  one of my favorites are:
[http://linuxhaters.blogspot.com/2008/06/suck-my-codec.html](http://linuxhaters.blogspot.com/2008/06/suck-my-codec.html)

> OMG. The Linux Hater ****** up! He got p0wned! He forgot about codec-buddy, one of Ubuntu's great achievements over Windows.

Uh huh. I knew I shouldn't have started that **** with you guys.

If y'all just take one giant ******* step back, you'd maybe notice that 99%  of the computing population ***doesn't even ******* know what a codec is***. And you know what, they ***don't give a *******. You see, they go to youtube, or abc.com, or hulu, click a few buttons, and they're watching the stuff they want to see.

Why? I shouldn't have to tell you this. It's because the codecs that they actually want either ship with their platform, or are installed automatically for them.

---

### Post by mlentink on 2008-07-18
sigh.
Why bother?

---

### Post by adamogardner on 2008-07-18
Well said, MaxIboy!

---

### Post by Canis familiaris on 2008-07-18
@Jim!
I do not mean offense and I understand you want to discuss that site but I wish to inform you that since you have linked to that blog, you are literally bumping it and helping the original author unintentionally.
I would recommend you to edit the link and put it in code so that it does not appears as link, and Google does not index it.
In future, kindly post on such topics in OMGPP as it is not indexed.

Regards 
Anurag Panda

---

### Post by teamkiller87 on 2008-07-18
> **Anurag_panda said:**
> @Jim!
I do not mean offense and I understand you want to discuss that site but I wish to inform you that since you have linked to that blog, you are literally bumping it and helping the original author unintentionally.
I would recommend you to edit the link and put it in code so that it does not appears as link, and Google does not index it.
In future, kindly post on such topics in OMGPP as it is not indexed.

Regards 
Anurag Panda

So what if it is indexed? Feeling threatened by something?

---

### Post by MaxIBoy on 2008-07-18
Actually, I think it's a good idea if our rebuttals are also in the search results.




I think what this guy was getting close to with his argument is the whole Qt vs. Gtk+ thing. The two toolkits both work in KDE *and* GNOME, but of course Qt applications sometimes look odd in GNOME, and Gtk+ applications can look weird in KDE. Very often there are ports of an application for each. If you look through the Add/Remove Programs listings, for almost every program using Qt, there's a similar program that uses Gtk+, and inter-compatibility between the two is only going to improve. I really don't think that it's catastrophic, I've never had problems with it. I would say that it's a weak point of ours, though.

---

### Post by wrtpeeps on 2008-07-18
> **Morty007 said:**
> There is a much simpler reason.

People are sheep. They take what they are given and what is most widely publicized. Hence Windows or Mac.

Or, they will take what suits them best, what they can install without worrying about compatability etc.

Hence windows and mac. :)

If the entire population of computer users were introduced to linux, do you honestly think everyone would switch over? :confused:

---

### Post by MaxIBoy on 2008-07-18
I bet you quite a few would. You'd just have to introduce it properly and be completely candid. So for instance you could show them compiz fusion, but you'd also have to show them the steps required to get graphics card drivers working. 


Otherwise, could you imagine the number of help/hate threads we'd have to deal with?!

---

### Post by tuxxy on 2008-07-18
>  They just want things to work. They will take "working" over "choice" in an instant. They essentially want the developers to make choices for them.*


Thats funny as its the exact reason I left Windows and choise Ubuntu :lolflag:

---

### Post by geoken on 2008-07-18
> **tuxxy said:**
> Thats funny as its the exact reason I left Windows and choise Ubuntu :lolflag:

Apparently you missed his entire argument. He never said people like you don't exist. He simply said they're in the vast minority of general computer users.

I can't say he's wrong.

---

### Post by wrtpeeps on 2008-07-18
> **MaxIBoy said:**
> I bet you quite a few would. You'd just have to introduce it properly and be completely candid. So for instance you could show them compiz fusion, but you'd also have to show them the steps required to get graphics card drivers working. 


Otherwise, could you imagine the number of help/hate threads we'd have to deal with?!

Yea. A few.

But then you'd have the gamers, graphic designers (don't even try and counter this argument with gimp :lolflag: ), .net guys, non technical people, people who like windows, people who like os x, people with strange hardware, etc, etc, etc, etc.

---

### Post by Canis familiaris on 2008-07-18
> **teamkiller87 said:**
> So what if it is indexed?
It is pushing his site up the google search index. As a result He is achieving what he wants: More visitors to his blog, and gets amused by the effect he has created.

> **teamkiller87 said:**
> Feeling threatened by something?
Threatened? Me? Why?

---

### Post by Canis familiaris on 2008-07-18
> **wrtpeeps said:**
> Yea. A few.

But then you'd have the gamers, graphic designers (don't even try and counter this argument with gimp :lolflag: ), .net guys, non technical people, people who like windows, people who like os x, people with strange hardware, etc, etc, etc, etc.

Linux is not for everybody, period. And he said few of them could. Those few would not be in this list.

---

### Post by wrtpeeps on 2008-07-18
> **Anurag_panda said:**
> It is pushing his site up the google search index. As a result He is achieving what he wants: More visitors to his blog, and gets amused by the effect he has created.


Threatened? Me? Why?

He is achieving what he wants by the fact that people care enough to change how they link to the post. :lolflag:

---

### Post by blazercist on 2008-07-18
The truth is that "linux hater" is right in a number of instances.  There are many many caviats that prevent the average joe user from being comfortable with linux Gnome or KDE.  I have used Linux for over a year now and I love it, but I was a Windows power user and am very computer inclined.  I still have problems every now and then with compatibility and configuration and lack of features that are standard on the mainstream OSes.  There are work arounds and I have gotten **almost** everything to work the way I want.  But I wouldn't expect "Joe User" to go as far in depth and have as much patience as I have.  On the mainstream OSes users need not worry about what hardware they buy what software they install how to install drivers or configuration.  They simple click next next next, although there are problems with this approach as well it saves "Joe User" from spending any time researching, installing or even having to understand what he is doing which, sadly, is perfect for most people.  "Linux Hater" is right about all the forked code and overabundance of choices, it confuses the average user who doesn't even know the speed of his CPU let alone how to compile software if it isn't packaged in the repos.  It is the same thing that makes Linux unique and beautiful that keeps it from being widely adopted.  I don't think that makes Linux any better or worse just different.  Linux is suitable for some novice users and it isn't for some others.  I disagree with the "hater" that Linux doesn't "do anything" and that you can do things with MacOS or Windows that cannot be done under linux because thats simply not true, the question is how much time, patience and frankly hastle are you willing to go through to accomplish the task.  That said, there are some things that are more easily accomplished under linux than under windows... I'm just trying to point out that his opinion although sharply embellished for the reader is not wrong and neither is anyone elses.  its a matter of taste and also a matter of pragmatically using what suits each particular computer users needs and wants.

---

### Post by Canis familiaris on 2008-07-18
> **wrtpeeps said:**
> He is achieving what he wants by the fact that people care enough to change how they link to the post. :lolflag:

No by the effect he has created. And the fact he has so many increased visits.

---

### Post by wrtpeeps on 2008-07-18
> **Anurag_panda said:**
> No by the effect he has created. And the fact he has so many increased visits.

So you want to stop people linking to his site, for the crime of having a different opinion to you?

---

### Post by toupeiro on 2008-07-18
I'm usually not one to generalize without some evidence to back it up, but it really seems to me that most people who "hate on" linux are those who fear change.  Most people who rip it will also tell you that they have not gone to vista yet.  Why?  Change!  they know their platform, and they never ever want it to go away, ever! No matter how innovative something will be, it will be lesser because it is different, therefore not as easy for them to use as what they already know.

Where I think the real break down is, is where people take complacency and actually try to stomp out the innovation of other developers and the desire to run and promote that innovation by its users.  If step back for a moment and try applying this logic to your life, you are in for an anxious and frustrating time.

---

### Post by teamkiller87 on 2008-07-18
From what I've read (and I read that blog almost daily because the guy amuses me) I got the message he's trying to put across. He's not a windows or mac fanboy. He's a hardcore, long time linux user who feels entitled to complain about linux's downsides. Because it's not perfect, despite anything any of you might say. I personally enjoyed and found he made a really compelling argument regarding the open source office suites, ie OpenOffice and KOffice and so on. What is the point in having so many? Why do you need choices when it comes to writing a friggin' letter or essay for example? I believe a bit of centralising would do the linux world a whole lot of good. A combined effort from the developers of needlessly "competing" software would create a far better experience for the end-user. I enjoy choice when it comes to different apps that have different ups and downs, not when it comes to apps different only by name.

---

### Post by wrtpeeps on 2008-07-18
> **toupeiro said:**
> I'm usually not one to generalize without some evidence to back it up, but it really seems to me that most people who "hate on" linux are those who fear change.  Most people who rip it will also tell you that they have not gone to vista yet.  Why?  Change!  they know their platform, and they never ever want it to go away, ever! No matter how innovative something will be, it will be lesser because it is different, therefore not as easy for them to use as what they already know.

Where I think the real break down is, is where people take complacency and actually try to stomp out the innovation of other developers and the desire to run and promote that innovation by its users.  If step back for a moment and try applying this logic to your life, you are in for an anxious and frustrating time.

Why change unnecessarily? If Windows XP or OS X perform the tasks you do perfectly, there is no need to change at all.

Waste of time, money and effort.

---

### Post by MaxIBoy on 2008-07-18
> **blazercist said:**
> The truth is that "linux hater" is right in a number of instances.  There are many many caviats that prevent the average joe user from being comfortable with linux Gnome or KDE.  I have used Linux for over a year now and I love it, but I was a Windows power user and am very computer inclined.  I still have problems every now and then with compatibility and configuration and lack of features that are standard on the mainstream OSes.  There are work arounds and I have gotten **almost** everything to work the way I want.  But I wouldn't expect "Joe User" to go as far in depth and have as much patience as I have.  On the mainstream OSes users need not worry about what hardware they buy what software they install how to install drivers or configuration.  They simple click next next next, although there are problems with this approach as well it saves "Joe User" from spending any time researching, installing or even having to understand what he is doing which, sadly, is perfect for most people.  "Linux Hater" is right about all the forked code and overabundance of choices, it confuses the average user who doesn't even know the speed of his CPU let alone how to compile software if it isn't packaged in the repos.  It is the same thing that makes Linux unique and beautiful that keeps it from being widely adopted.  I don't think that makes Linux any better or worse just different.  Linux is suitable for some novice users and it isn't for some others.  I disagree with the "hater" that Linux doesn't "do anything" and that you can do things with MacOS or Windows that cannot be done under linux because thats simply not true, the question is how much time, patience and frankly hastle are you willing to go through to accomplish the task.  That said, there are some things that are more easily accomplished under linux than under windows... I'm just trying to point out that his opinion although sharply embellished for the reader is not wrong and neither is anyone elses.  its a matter of taste and also a matter of pragmatically using what suits each particular computer users needs and wants.

Agreed. The learning process has been fairly painless and actually pretty fun for me. I mean, it helps that all the really essential, vital stuff that I needed for homework and so on was already there and working the whole time, so if I needed to get something serious done I could usually stop tinkering. It also helps if you know a computer genius who is willing to help you out just for fun!




> **wrtpeeps said:**
> don't even try and counter this argument with gimp :lolflag: Oh, I won't. The GIMP may be a powerful image editor, but the UI is way too confusing. I prefer to self-teach when learning new software, and the GIMP wasn't at all conducive to my efforts (I wound up longing for MS Paint.)

---

### Post by toupeiro on 2008-07-18
> **wrtpeeps said:**
> Why change unnecessarily? If Windows XP or OS X perform the tasks you do perfectly, there is no need to change at all.

Waste of time, money and effort.

Well for 1.  XP's and End of Life product, and patches and software will eventually begin to be written in such a way that its no longer supported on it.

2. OS/X doesn't do every task I want perfectly, at all.   And, its far too proprietary, I'd venture to say even moreso than windows.

My point has been made though, in a slight regard.  I realize you did not say vista.. :)  A persons natural upgrade path from the End of Life Windows XP is Windows Vista.  Will you just stop using your computer when XP isn't supported by anything anymore?  Will you use vista then, if there is something today you may be aware of that keeps you from using it now, Will you use OSX, the power of UNIX and Linux except that its innovation stifling IMO, or will you choose to run linux?  In my opinion, you have to face change either way.  People just need to pick their poision and stop complaining.

---

### Post by Canis familiaris on 2008-07-18
> **wrtpeeps said:**
> So you want to stop people linking to his site, for the crime of having a different opinion to you?

I am not stopping him, it was only my opinion that people should not link up in those sites in this forum at least.
That site was not an opinion. It is only a blog which is cleverly designed to start flames and get as many replies as possible which I consider as "trolling"
I have seen opinions against my own well balanced and right to great extent but not this one.
Anyway I did not ask the OP to remove the link, I only *requested* him to put it in code so that people in this forum could visit that site by cut, copy, paste and it does not get indexed by Google.
I think I have a right to make a *request*.

---

### Post by blazercist on 2008-07-18
He appears to be a linux user, his indepth knowledge and understanding make it pretty clear that he is a well informed computer user and is quite familiar with linux.  He also seems to be pissed off about some of the inadequacies he finds in linux and is trying to point them out as best he can... I thought bug finding and making suggestions to devs in order to improve the quality of the software was the point of Free Open Source in the first place?

Just because he makes fun and uses sarcasm and whit to point out problems doesn't make him a troll, it simply makes for entertaining reading in that form.

---

### Post by wrtpeeps on 2008-07-18
> **toupeiro said:**
> Well for 1.  XP's and End of Life product, and patches and software will eventually begin to be written in such a way that its no longer supported on it.

2. OS/X doesn't do every task I want perfectly, at all.   And, its far too proprietary, I'd venture to say even moreso than windows.

My point has been made though, in a slight regard.  I realize you did not say vista.. :)

I didn't mention vista cause I didn't need to. I like vista. It performs its tasks well. You don't need to learn an entire new way of doing things when you upgrade from xp.

---

### Post by blazercist on 2008-07-18
> **wrtpeeps said:**
> So you want to stop people linking to his site, for the crime of having a different opinion to you?

I have found recently in #ubuntu that a difference of opinion is enough to get banned, some of the zealots here are far too indoctrinated to understand that Operating Systems are all designed to complete the same basic task users SHOULD have the freedom to choose what works best for their specific use or isn't that what open source was intended for?  Its just a computer, no one should get angry about anything relating to computer software.

---

### Post by toupeiro on 2008-07-18
> **wrtpeeps said:**
> I didn't mention vista cause I didn't need to. I like vista. It performs its tasks well. You don't need to learn an entire new way of doing things when you upgrade from xp.
You think so?  wow, I disagree wholeheartedly.  One of my tasks at work involves helping transition my users into the interfaces and functions of Vista over XP, and Office 2007 over office 2003.  I must say there is a **VAST** amount of differences in how things are done, from a user perspective, and from an administrative one.

Comparatively thats somewhat like saying you don't learn an entire new way of doing things from driving a 2008 Cadillac and a 1959 Cadillac.  I used such a big gap in cars because technology doesn't change so fast in that industry compared to the IT industry.  So, yes, they both have steering wheels, a gas pedal, breaks, and 4 tires, but Things like power steering, Anti-lock breaking, traction control, a tiptronic transmission, a rev limiter, and a limited slip rear differential will greatly change the way you handle the car, for good or for bad. Chances are, you will be able to drive both, but not in the same way, and not without learning how to handle them.  Do you really think that logic is any different with anything else?

---

### Post by Canis familiaris on 2008-07-18
> **wrtpeeps said:**
> I didn't mention vista cause I didn't need to. I like vista. It performs its tasks well. You don't need to learn an entire new way of doing things when you upgrade from xp.
How many years did you use Windows before trying Linux?

How much time did it take you to learn installing programs in Windows, maintaing a Windows install, defragmenting, etc., etc?

How much time did you spend using programs like Photoshop, Office, etc.?

Compare it how much time did you spent in learning stuff in Linux. You'll get my point.

Windows may be suited to cerain range of users and Linux has certain flaws.
 But you have to learn things more in Linux is not a valid argument at all.

---

### Post by blazercist on 2008-07-18
> **Anurag_panda said:**
> 
Windows may be suited to cerain range of users and Linux has certain flaws.
 But you have to learn things more in Linux is not a valid argument at all.

Sure its a valid argument, why not, if im Joe Schmo I don't want to spend time learning anything I just want it to work, e.g. I dont want to google how to install my video driver I want to click next next next and its installed...  I don't want to research whether that webcam i want is supported under linux and find out what chipset it uses I just want to buy it and plugin it in and use it.

granted some hardware is like that under linux but some isnt.

---

### Post by Canis familiaris on 2008-07-18
> **blazercist said:**
> Sure its a valid argument, why not, if im Joe Schmo I don't want to spend time learning anything I just want it to work, e.g. I dont want to google how to install my video driver I want to click next next next and its installed...  I don't want to research whether that webcam i want is supported under linux and find out what chipset it uses I just want to buy it and plugin it in and use it.

granted some hardware is like that under linux but some isnt.

Read this: ;)
[http://ubuntuforums.org/showthread.php?t=120489](http://ubuntuforums.org/showthread.php?t=120489)

---

### Post by wrtpeeps on 2008-07-18
> **Anurag_panda said:**
> How many years did you use Windows before trying Linux?

How much time did it take you to learn installing programs in Windows, maintaing a Windows install, defragmenting, etc., etc?

How much time did you spend using programs like Photoshop, Office, etc.?

Compare it how much time did you spent in learning stuff in Linux. You'll get my point.

Windows may be suited to cerain range of users and Linux has certain flaws.
 But you have to learn things more in Linux is not a valid argument at all.

1. LOng time.

2. Installing on windows takes no longer than installing on office.

3. Photoshop, office, games, all the time. The first and last have no good alternatives on linux. openoffice is good.

4. Ubuntu is extremely simplified, so learning isn't required. 

ANd learning more things in linux wasn't what I was trying to say. :)

---

### Post by wrtpeeps on 2008-07-18
> **blazercist said:**
> Sure its a valid argument, why not, if im Joe Schmo I don't want to spend time learning anything I just want it to work, e.g. I dont want to google how to install my video driver I want to click next next next and its installed...  I don't want to research whether that webcam i want is supported under linux and find out what chipset it uses I just want to buy it and plugin it in and use it.

granted some hardware is like that under linux but some isnt.

Exactly.

Linux tends to focus too much on "why windows can be bad" rather than "why linux can be good".

Instead of getting people to tell you what reasons they have for staying with windows, you should tell them what reason you have for them to move to Linux.

And, in most cases, "it is GPL" isn't a good reason. :)

---

### Post by blazercist on 2008-07-18
> **Anurag_panda said:**
> Read this: ;)
[http://ubuntuforums.org/showthread.php?t=120489](http://ubuntuforums.org/showthread.php?t=120489)

clicking next next next is not on par with droppinig to virtual term, logging in, making sure you have build-essential installed, making sure you have the kernel headers installed, stopping gdm, chmoding the driver to make it executable, shing the driver, THEN CLICKING NEXT NEXT NEXT, restarting gdm and then repeating the process with each new kernel, I dont care about ayisu's post it doesnt apply here.  His example is not a good analogy... and he is wrong because chinese is spoken by more people than is english, infact spanish is the most popular language on the planet AFAIK.



Do not forget that I like linux more than windows you are not talking to a troll or a noob.

---

### Post by Canis familiaris on 2008-07-18
> **wrtpeeps said:**
> Linux tends to focus too much on "why windows can be bad" rather than "why linux can be good".

Linux is only a kernel how can it have an opinion. :lol:

Seriously, the developers of FLOSS like Linux have focused in strengths of Linux rather than weakness of Windows.
That is why Linux is so radically different from Windows.

Sure, There are plenty of entusiasts who keep on promoting Linux by bashing Windows, but that would be natural, considering the way MS has treated the Open Source Community.
I am not defending them, particularly not the Linux Zealots among them, I personally find them as bad as those Windows and Mac fanboys.

---

### Post by toupeiro on 2008-07-18
> **wrtpeeps said:**
> Exactly.

Linux tends to focus too much on "why windows can be bad" rather than "why linux can be good".

Instead of getting people to tell you what reasons they have for staying with windows, you should tell them what reason you have for them to move to Linux.

And, in most cases, "it is GPL" isn't a good reason. :)

Wow.. again, I feel that perception is extremely skewed from reality.  Its more like "Why linux is linux"  

I've never "forced" linux on anyone.  I just got a call from a friend of mine 3 days ago who applied the latest microsoft updates and could no longer boot, and he called me and asked me to help him install linux.  In my experience, the user already knows all the reasons.  Its a waste of breath and time to list them out.  If they have any desire to change, they act apon it themselves.  Linux is not like the borg, but windows is a whole heck of a lot like Rome...

---

### Post by dracayr on 2008-07-18
WOW, that guy is crazy^^

check out his post about viruses ([http://linuxhaters.blogspot.com/2008/06/at-least-we-dont-have-any-viruses.html](http://linuxhaters.blogspot.com/2008/06/at-least-we-dont-have-any-viruses.html)).. he claims linux doesn't have any viruses because the api isn't good enough for a virus, and that precicely is the reason why linux there is no good software for linux O_O

dracayr

---

### Post by karellen on 2008-07-18
I like that blog (now you can stone me :D), it kinda gives another point of view from somebody who obviously used (and I think he still does) Linux. I think the open source movement needs criticism of this sort, not simply stupid bashing (like on a well known forum ;) )
:)

---

### Post by Canis familiaris on 2008-07-18
> **blazercist said:**
> Do not forget that I like linux more than windows you are not talking to a troll or a noob.
I have gathered that already.

> **blazercist said:**
> clicking next next next is not on par with droppinig to virtual term, logging in, making sure you have build-essential installed, making sure you have the kernel headers installed, stopping gdm, chmoding the driver to make it executable, shing the driver, THEN CLICKING NEXT NEXT NEXT, restarting gdm and then repeating the process with each new kernel, I dont care about ayisu's post it doesnt apply here.  His example is not a good analogy... and he is wrong because chinese is spoken by more people than is english, infact spanish is the most popular language on the planet AFAIK.
Say your native language is English, and you have to learn Chinese, you will surely find Chinese difficult and its script will appear strange to you, and you will find Chinese difficult. But thus that makes Chinese difficult? No, it doesn't. Someone who has been born and brought up in China would find Chinese easy and rather English to be difficult.
What is my point?
What you learn something first makes it Easy but someone who has learned something differently would find the same thing difficult.
In this context Linux is not more difficult nor is Windows is easy/difficult in any order, just different.

And I dont think a person would find pre-configured desktop with Linux with all hardware installed or Linux installed on well supported hardware more difficult than Windows preconfigured when he is stepping foray to world of computing.

---

### Post by wrtpeeps on 2008-07-18
Criticism is a good thing, especially from people who understand Linux. 

Windows bashers, take note. ;) :lolflag:

---

### Post by Canis familiaris on 2008-07-18
> **wrtpeeps said:**
> Criticism is a good thing, especially from people who understand Linux. 

Windows bashers, take note. ;) :lolflag:

You mean "Constructive" criticism?
Then I agree.

---

### Post by phoochka on 2008-07-18
I havnt read each and every reply, so forgive me if this issue has been addressed but: 

Why do we care who's grandmother is able to use linux or not? Infact why the hell should we care about the mainstream win/mac users at all? 

Surely the number one priority is making the current user happy (i.e. us). 

I'm a dual booter and will probably remain one no matter how "mainstream" linux becomes but it seems to me that too many people are worried about what _other_ people think about linux than their own wants and needs. 

Once we take that issue out half the blog is meaningless.

---

### Post by geoken on 2008-07-18
> **Morty007 said:**
> 

People are sheep. They take what they are given and what is most widely publicized. Hence Windows or Mac.

I think that's a dangerous generalization. People only have a finite amount of time to become experts in various fields. Many of us consider ourselves computer experts, or at least well versed in that specific topic, and as such we can make highly informed decisions about various computer related choices.

Just because someone spends their time immersing themselves in a different field doesn't make them a sheep. If someone spent all their time devoted to some political cause, would you consider them sheep because they never had the time to familiarize themselves with computers and the various choices available to them.

---

### Post by Canis familiaris on 2008-07-18
> **phoochka said:**
> I havnt read each and every reply, so forgive me if this issue has been addressed but: 

Why do we care who's grandmother is able to use linux or not? Infact why the hell should we care about the mainstream win/mac users at all? 

Surely the number one priority is making the current user happy (i.e. us). 

I'm a dual booter and will probably remain one no matter how "mainstream" linux becomes but it seems to me that too many people are worried about what _other_ people think about linux than their own wants and needs. 

Once we take that issue out half the blog is meaningless.

I agree. You banged the nail right on the head.

---

### Post by blazercist on 2008-07-18
IMO almost any criticism is constructive.  He makes some valid points and is therefore constructive.

Back to out lingual analogy, I'm not disputing that anything new takes some getting used to and just because its new doesn't mean its inherently more difficult... what I'm saying is that: More non-repetitive steps like the ones I described are not just different they are more work physically and therefore inherently more difficult.

I do agree that a preconfigured system with preconfigured hardware does not apply  to my example and is just as easy as windows or Mac, HOWEVER, upgrading hardware and installing new applications on a preconfigured linux PC is still more work in SOME CASES than on windows, im not refering to the cases where the hardware is supported or the application is in a package in the repos obviously.  Windows and Mac are immune to this deficiency because Mac is meant to be installed only on certain hardware and because all hardware manufacturers write windows drivers for their devices.

---

### Post by blazercist on 2008-07-18
>   Originally Posted By Phoochka  View Post
I Havnt Read Each And Every Reply, So Forgive Me If This Issue Has Been Addressed But:

Why Do We Care Who's Grandmother Is Able To Use Linux Or Not? Infact Why The Hell Should We Care About The Mainstream Win/mac Users At All?

Surely The Number One Priority Is Making The Current User Happy (i.e. Us).

I'm A Dual Booter And Will Probably Remain One No Matter How "mainstream" Linux Becomes But It Seems To Me That Too Many People Are Worried About What _other_ People Think About Linux Than Their Own Wants And Needs.

Once We Take That Issue Out Half The Blog Is Meaningless.
> **anurag_panda said:**
> i Agree. You Banged The Nail Right On The Head.

+1

---

### Post by Canis familiaris on 2008-07-18
> **blazercist said:**
> IMO almost any criticism is constructive.  He makes some valid points and is therefore constructive.

Back to out lingual analogy, I'm not disputing that anything new takes some getting used to and just because its new doesn't mean its inherently more difficult... what I'm saying is that: More non-repetitive steps like the ones I described are not just different they are more work physically and therefore inherently more difficult.

I do agree that a preconfigured system with preconfigured hardware does not apply  to my example and is just as easy as windows or Mac, HOWEVER, upgrading hardware and installing new applications on a preconfigured linux PC is still more work in SOME CASES than on windows, im not refering to the cases where the hardware is supported or the application is in a package in the repos obviously.  Windows and Mac are immune to this deficiency because Mac is meant to be installed only on certain hardware and because all hardware manufacturers write windows drivers for their devices.

Yes this is true. Linux users have to sadly bear this side effect due to its low penetration.
Linux would improve by leaps and bound, um, atleast for its existing set of users just by more Hardware support.

As I maintain the various distributions of Linux including Ubuntu are NOT for everybody but with better Hardware support would fulfill the needs of at lot more users than it is doing now.

---

### Post by Yes on 2008-07-18
Just because hardware manufactures write drivers for Windows doesn't mean that it's easy to set up - I still haven't managed to get my networked printer working.  In Linux the hardest part was figuring out what IP address my router was giving it, after that it was a peice of cake.

I think phoochka really nailed it - we keep worrying about the "mainstream user", but why should we?  If they're happy with Windows or Mac, why try to change Linux so they'll like it?

---

### Post by aysiu on 2008-07-18
> **dracayr said:**
> WOW, that guy is crazy^^

check out his post about viruses ([http://linuxhaters.blogspot.com/2008/06/at-least-we-dont-have-any-viruses.html](http://linuxhaters.blogspot.com/2008/06/at-least-we-dont-have-any-viruses.html)).. he claims linux doesn't have any viruses because the api isn't good enough for a virus, and that precicely is the reason why linux there is no good software for linux O_O

dracayr
I can't take anyone seriously who says [quote=Linux Hater's blog]Besides, I can make my computer immune to viruses. Just watch. Pop! Did you see that? I unplugged my network cable.

The luser wretches, "Oh but that makes your computer useless!" Yeah, well so does putting Linux on it. What's your point?[/quote]

---

### Post by Erunno on 2008-07-18
> **dracayr said:**
> WOW, that guy is crazy^^

check out his post about viruses ([http://linuxhaters.blogspot.com/2008/06/at-least-we-dont-have-any-viruses.html](http://linuxhaters.blogspot.com/2008/06/at-least-we-dont-have-any-viruses.html)).. he claims linux doesn't have any viruses because the api isn't good enough for a virus, and that precicely is the reason why linux there is no good software for linux O_O

He's talking about the Linux ABI (application **binary** interface), not API and he's basically right. Linux ABI is an ever moving target which makes it more difficult for both virus and application developers.

---

### Post by JohnFH on 2009-03-24
Actually I don't, but this guy does:
[URL="http://linuxhaters.blogspot.com/"]
http://linuxhaters.blogspot.com/[/URL]

Absolutely great blog!  It may slander Linux to a level previously unimaginable, but I think it's hilarious!  I don't like some of the language he uses, but apart from that I like his style and the way he sees things.

For the record, I use Ubuntu exclusively at home so the opinions expressed in the link here are, let's say, not the same as mine.

---

### Post by chris200x9 on 2009-03-24
heh...I often thought about doing that just starting a FUD blog with no real content to get get people talking....more clicks = more money....spread the FUD :D....

---

### Post by Giant Speck on 2009-03-24
He brings up a lot of good points in each post, sprinkles it with a little satire, adds a cup of colorful language and stirs until boiling.  I like it. :)

People take things too seriously and they seem to dismiss all criticism against Linux as FUD.  That's too easy, I say.

---

### Post by clanky on 2009-03-24
Unfortunately this thread will probably be either masrked as solved and moved to recurring discussions, locked or just plain deleted soon, which is a huge shame because there is alot in the linux haters' blog which many of the linux zealots around could do with reading.

---

### Post by amadeus266 on 2009-03-24
I reject his reality and substitute my own. LOL

---

### Post by cc8balla on 2009-03-24
It's actually quite brilliant. 

Trolling is an art :D

---

### Post by JackieChan on 2009-03-24
I dislike people who hate Linux. :(

---

### Post by gn2 on 2009-03-24
> **cc8balla said:**
> Trolling is an art :D

But if it is perceived as trolling, then it has failed.

---

### Post by cc8balla on 2009-03-24
> **gn2 said:**
> But if it is perceived as trolling, then it has failed.

Ahh, good point.

---

### Post by clanky on 2009-03-24
> **JackieChan said:**
> I dislike people who hate Linux. :(

But let me guess, idiots whose every post contains at least one reference to M$ or windoze are really cool right, right?

---

### Post by Marlonsm on 2009-03-24
Stopped reading in the 3rd line booting up fast isn't only saving a few secs, it means that the OS itself is much lighter.

good for a laugh, tho... but nothing else.

---

### Post by Marlonsm on 2009-03-24
Sorry, double post.

---

### Post by TheLions on 2009-03-24
I completly agree with this the guy!
Instead making bootup faster fix that fracking PulseAudio and sluggish  Firefox!

> Here's something silly. It seems like y'all are concentrating on boot times these days. Boot in 20 seconds! no, 15 seconds! no 10 seconds! But first, you need to answer me this question:

Why the **** do I care?

Seriously, when's the last time I cold-booted my desktop? Uhh, a month ago? My laptop? ummm, three weeks ago? Oh, but I really wish I saved 10 seconds back then. I could have gotten a couple extra jerks in this month.

Or, is it that we're moving toward a Linux where the kernel updates every 30 minutes? So, if you want to stay on the train, then you better optimize your rebooting.

Those of you who still think boot time is important, go find your friend with a Mac. Ask them to show you how the desktop is back up even before they finish opening the lid. Ask them how many times a year they explicitly choose "Shutdown". Now multiply that by the number of seconds they could possibly save with a faster boot, and compare that total with the time they could save by not listening to your freetard come-ons.

The sad truth is, boot time hasn't mattered to most of the world's computer population in a long time. S3 sleep solved that problem. Perhaps this is Linux's totally awesome way of solving the same problem by ignoring existing technologies.

Think about your phone. When's the last time it booted? My blackbery takes minutes and minutes to boot, and yet nobody cares. Should RIM spend more time optimizing a process that happens maybe once every 6 months, or work on bettering their battery life, which affects me every day? Hmm, that's a toughie. Let me ask some freetards for some advice.

The only place where boot time kinda matters is for these bolted-on-the-side Linux firmwares like splashtop and such. But even then, who cares if I can get to a crippled desktop in 5 seconds when I could resume my suspended useful OS in just as much time?  Oh, but this is where Linux EXCELS. I mean, it's open source, so you can totally strip out all the features and BLOAT that you don't need, so that you can boot faster.

Hey guys, I have an OS that boots in like a nanosecond. It's called GRUB-OS. It even has a text editor, just hit "e". Pretty sweet huh?

---

### Post by BigSilly on 2009-03-24
Seen this site before. It's a grand laugh! I'm apparently a "freetard"! :biggrin:

It's nice to have a purpose. :biggrin:  That's how I'll describe myself from now on I think. "Hi. I'm Big S and I'm a freetard".

Actually, that might give people the wrong impression. It sounds a bit...rude.

---

### Post by Technoviking on 2009-03-24
It is good that Bill Gates found a hobby after retiring.

T-V

---

### Post by forrestcupp on 2009-03-24
Friday's post is right.  What's the point of bragging about up time *and* boot time.  If one is important, the other isn't.

---

### Post by nikislash on 2009-03-24
I agree that there are some linux people who need to read this lol

I've only just started using linux but the main reason its taken so long isn't about the operating system it was the linux people I met.

---

### Post by Giant Speck on 2009-03-24
Some of the posts in this thread are proving my point...

---

### Post by BigSilly on 2009-03-24
> **forrestcupp said:**
> Friday's post is right.  What's the point of bragging about up time *and* boot time.  If one is important, the other isn't.

Well it depends on who you are and how you use your computer doesn't it? Both are important to different types of users surely.

---

### Post by khelben1979 on 2009-03-24
I experience him to be a bit funny, actually, but I must confess that I'm much more interested in helping out in the Linux community myself so that Linux would get promoted as a good operating system rather than slamming it down.

---

### Post by TheLions on 2009-03-24
> **khelben1979 said:**
> I experience him to be a bit funny, actually, but I must confess that I'm much more interested in helping out in the Linux community myself so that Linux would get promoted as a good operating system rather than slamming it down.

negative publicity is still publicity!

Just look at some American star, most of them got to the scene by some scandal...

---

### Post by zeroandone on 2009-03-24
Maybe the guy is posting a new post from his Ubuntu box right now.

---

### Post by lswartz on 2009-03-24
I sure like it on my Mini 9. Guess that makes me a 'boot up' guy :p.

---

### Post by forrestcupp on 2009-03-24
> **BigSilly said:**
> Well it depends on who you are and how you use your computer doesn't it? Both are important to different types of users surely.

Well, you're right there.  I'm really for fast boot times more than up time.  I hate hearing people brag about up time when it's not necessary.  And I also hate it when people flaunt up time as something that Windows can't do.  It's just not the case.

---

### Post by gn2 on 2009-03-24
> **Technoviking said:**
> It is good that Bill Gates found a hobby after retiring.

T-V

He's actually doing some really worthwhile stuff, and I for one wish him all the best in his efforts.

[http://www.gatesfoundation.org/Pages/home.aspx](http://www.gatesfoundation.org/Pages/home.aspx)

---

### Post by Skripka on 2009-03-24
> **TheLions said:**
> I completly agree with this the guy!
Instead making bootup faster fix that fracking PulseAudio and sluggish  Firefox!

Firefox is not a Linux problem.  Firefox is a Mozilla problem.  

In any case, there are lots of FOSS out there that are FAR faster and smoother running than the bloated FoxFire.  Half the problem with FoxFire bloat and sluggishness is the very extensions which people write for it, and for which people praise it.

---

### Post by KCG102282 on 2009-03-24
> **Skripka said:**
> Firefox is not a Linux problem.  Firefox is a Mozilla problem.  

In any case, there are lots of FOSS out there that are FAR faster and smoother running than the bloated FoxFire.  Half the problem with FoxFire bloat and sluggishness is the very extensions which people write for it, and for which people praise it.
Maybe if you called firefox by the right name instead of foxfire people would take your negative comments about it more seriously.

---

### Post by inobe on 2009-03-24
i call it free advertisement ;)

---

### Post by Name change on 2009-03-24
WooHoo!!!
He's back. At first I didn't believe it. I read that Linux hater will "retire" but no he's back.
You also got Linux Hater's Redux a blog that filled the void while real thing was gone:
[http://linux-haters-redux.blogspot.com/](http://linux-haters-redux.blogspot.com/)

Anyway always fun to read this sort of blog.

---

### Post by mamamia88 on 2009-03-24
i hate to say he's right about boot times but honestly i rarerly reboot my computer and the only time i do is when it gets too hot and i feel like letting it get a fresh start

---

### Post by nath2008uk on 2009-03-24
What OS is he really using?

Surprised he isn't that there complaining about the BSOD or driver problems.

For all you know maybe his 'WINDOWS' has a virus, Controlling him and his posts.
We will never know.

---

### Post by Name change on 2009-03-24
> **nath2008uk said:**
> What OS is he really using?

Surprised he isn't that there complaining about the BSOD or driver problems.

For all you know maybe his 'WINDOWS' has a virus, Controlling him and his posts.
We will never know.
Or maybe he uses BSD? Ever thought of that?
Or even Linux. You can use Linux and still "hate" it.
I know that Linux Hater's Redux uses Ubuntu.

---

### Post by nath2008uk on 2009-03-24
Why use it if you hate it?

I mean, I hate the Xbox 360, And I don't play it :P

It's like hating someone, Then hanging about with them.
You just don't really hate it then.

---

### Post by Kareeser on 2009-03-24
Hm. His post about drivers is incorrect. Drivers are an essential first-step to getting hardware working. In many cases, out-of-the-box, Windows will only support a fraction of hardware... even less so the newer the computer is.

Macs also have "less" drivers not because they don't need drivers, but because Apple hand-picked hardware configurations for each mac model. Hence, unnecessary drivers are never compiled in the first place.

Most of his posts can be debunked similarly.

---

### Post by GepettoBR on 2009-03-24
I have the same thing to say about this blog as I have to say about 4chan's /g/ and /v/: trolls trolling trolls trolling fanboys trying to troll trolls.

I smirked on a few articles, didn't laugh though.

---

### Post by danillo on 2009-03-24
It's sarcasm! Actually this reminds me of Maddox, only he's not bashing linux. But he writes in a similar way. [http://maddox.xmission.com/](http://maddox.xmission.com/)

---

### Post by GepettoBR on 2009-03-24
> **danillo said:**
> It's sarcasm! Actually this reminds me of Maddox, only he's not bashing linux. But he writes in a similar way. [http://maddox.xmission.com/](http://maddox.xmission.com/)

I'm not too big on Maddox, though there are a few of his "articles" that I like.

What I really love, though, is that classic rant about how Lunix was developed by soviet hacker Linus Torovotos during the Cold War. That's priceless. And Linus's name links to a picture of Boris from Goldeneye.

---

### Post by cardinals_fan on 2009-03-24
> **JackieChan said:**
> I dislike people who hate Linux. :(
Really, that doesn't say anything about them as a person - unless you dislike people who hate anything.  But that would make you a hypocrite... :)
> **nath2008uk said:**
> What OS is he really using?

Surprised he isn't that there complaining about the BSOD or driver problems.

For all you know maybe his 'WINDOWS' has a virus, Controlling him and his posts.
We will never know.
I think he probably uses Linux.  It's an over-the-top look at valid criticisms.

---

### Post by lisati on 2009-03-24
> **nath2008uk said:**
> Why use it if you hate it?

I mean, I hate the Xbox 360, And I don't play it :P

It's like hating someone, Then hanging about with them.
You just don't really hate it then.
I don't even have an Xbox
> **Kareeser said:**
> Hm. His post about drivers is incorrect. Drivers are an essential first-step to getting hardware working. In many cases, out-of-the-box, Windows will only support a fraction of hardware... even less so the newer the computer is.

Macs also have "less" drivers not because they don't need drivers, but because Apple hand-picked hardware configurations for each mac model. Hence, unnecessary drivers are never compiled in the first place.

Most of his posts can be debunked similarly.

I think my MS-DOS/Windows experience is distracting me here, but what about BIOS? Depending on what you're doing, sometimes it's the BIOS that comes to the rescue as a first step to getting things working, and drivers either add to, or replace, what few capabilities the BIOS might have to offer.

---

### Post by bluelamp999 on 2009-03-24
Absolutely brilliant. 

He actually cares a lot and most of it is totally spot on...

---

### Post by Changturkey on 2009-03-24
It's good to have a critic.

---

### Post by liamnixon on 2009-03-24
> SUSE was born a crack baby, and has grown up to be a crack smoking crack dealer. Even their stupid lizard looks like it’s cracked out. I bet the lizard is really just a vessel used for crack smuggling.

Holy crap, that killed me!  :lolflag:

Oh god!

---

### Post by Giant Speck on 2009-03-24
> **Changturkey said:**
> It's good to have a critic.

It is good to have a critic.  We can't just sit here in a bubble thinking that Linux is perfect in every way.  People get way too offended at the sight of even a tiny criticism of Ubuntu or Linux in general. They would rather dismiss any criticism as FUD or, even worse, dismiss it as a non-issue because they themselves are either not experiencing the problem or because the problem does not affect them in any way.

Sure, the guy chooses a really colorful way of expressing his concerns about Linux, but if I was writing my own blog about what I found wrong with Linux, I'd sure as hell use any language I wanted.  The only reason I hold back my language here on Ubuntu Forums is because it is frowned upon and mostly censored.

His writing style also keeps it mildly entertaining.  It engages even readers who disagree with his claims.

---

### Post by pwnst*r on 2009-03-25
> Here's something silly. It seems like y'all are concentrating on boot times these days. Boot in 20 seconds! no, 15 seconds! no 10 seconds! But first, you need to answer me this question:

Why the **** do I care?

Seriously, when's the last time I cold-booted my desktop? Uhh, a month ago? My laptop? ummm, three weeks ago? Oh, but I really wish I saved 10 seconds back then. I could have gotten a couple extra **** in this month.

lulz.

---

### Post by Dekkon on 2009-03-25
Honestly, I actually love this post, he somewhat actually researches what he complains about and his post about boot times is funny, yet so freaking true. 

...And yes, my Blackberry takes 3 minutes to boot, yet all I care about it battery time.

---

### Post by t0p on 2009-03-25
I can't believe how many people have said this guy is somehow *good* for Linux!  And that comment,

> It's good to have a critic...

Lintards... Freetards... guy musta swallowed a thesaurus...

---

### Post by namegame on 2009-03-25
> **t0p said:**
> I can't believe how many people have said this guy is somehow *good* for Linux! 

So posting flamboyant, yet insightful, true, and constructive criticism is bad for Linux?

Somehow I don't get your logic.

---

### Post by t0p on 2009-03-25
> I feel sorry for you guys, really. All those little bits of frustration and anger that get built up everytime someone sends you a word document, or god forbid, a powerpoint with animations and video. It all gets piled up and unleashed on a poor unsuspecting soul, who, if anything, quite accurately represents the kinds of users that you can only dream about having.

Why don’t you guys just go back to your Slashdot circle-jerk and leave normal people alone. Your presence is not appreciated here in the real world."

Is that some of the "flamboyant, yet insightful, true, and constructive criticism" you were on about?

---

### Post by olskar on 2009-03-25
His latest post is so true!

I imagine the discussion goes something like this;

"Ah well, new ubuntuversion coming up guys, what should we improve?"

"Hm, batterytime seems to be popular? Perhaps we can try to improve that?"

"How do we do that? That sounds hard.."

"Well, perhaps we could give them nice new artwork?"

"New artwork?! We only have 6 months, we cant make a new theme in six months! I know! Let's improve the boot-time!"

---

### Post by Seaco on 2009-03-25
well whats the big problem?

I must say for a Linux hater he truly knows well problems with Linux,
normally people that hate linux dont care even to try it because they are happy with microsoft so they bash out linux, we have the same in the linux community in relation to microsoft. But he speaks of various linux distributions like he knows them.

Everybody says that we are a small community, that almost dosent have a really share of users. For me seeing someone that speaks about the problems in Linux with a know how, is better than all the pie charts saying that we are growing or not. 

I use Linux and i love it, i got problems with my linux like everybody that wants to experiment things, but in the end of the day i am happier with my choice. this guy dosent change a thing except that he points out some things that need improvement

---

### Post by pwnst*r on 2009-03-25
> **t0p said:**
> Is that some of the "flamboyant, yet insightful, true, and constructive criticism" you were on about?

lol, spot on.

---

### Post by zeroandone on 2009-03-25
> **Seaco said:**
> well whats the big problem?

I must say for a Linux hater he truly knows well problems with Linux,
normally people that hate linux dont care even to try it because they are happy with microsoft so they bash out linux, we have the same in the linux community in relation to microsoft. But he speaks of various linux distributions like he knows them.

Everybody says that we are a small community, that almost dosent have a really share of users. For me seeing someone that speaks about the problems in Linux with a know how, is better than all the pie charts saying that we are growing or not. 

I use Linux and i love it, i got problems with my linux like everybody that wants to experiment things, but in the end of the day i am happier with my choice. this guy dosent change a thing except that he points out some things that need improvement

Agree.

---

### Post by zeroandone on 2009-03-25
> **Giant Speck said:**
>  They would rather dismiss any criticism as FUD or, even worse, dismiss it as a non-issue because they themselves are either not experiencing the problem or because the problem does not affect them in any way.

Or "it is open source, so build your own software, idiot!" Does it sound familiar?

---

### Post by Giant Speck on 2009-03-25
> **zeroandone said:**
> Or "it is open source, so build your own software, idiot!" Does it sound familiar?

Yes.  It sounds very familiar.  It's the mentality that if you don't like something about a program, you don't have a right to complain about it.  It's the whole "I'd like to see you try to make a program like this.  Then you can complain about it all you want." mentality.

---

### Post by GepettoBR on 2009-03-25
> **Giant Speck said:**
> Yes.  It sounds very familiar.  It's the mentality that if you don't like something about a program, you don't have a right to complain about it.  It's the whole "I'd like to see you try to make a program like this.  Then you can complain about it all you want." mentality.

Even worse than that are the people who rant on about how it's free so you don't have the right to complain. "If you don't like it, you got your money's worth. Anything else is an improvement". There's nothing wrong with that per si, but they tend to think that every bit of criticism is in fact a complaint.


Honestly, I think a lot of people need to have this guy's blog shoved down their throats. Linux is a mess. Ubuntu is a mess. Windows is also a mess, albeit a different one. Ditto for OS X. People should make their choice depending on which defects they're less annoyed with.

---

### Post by Giant Speck on 2009-03-25
> **GepettoBR said:**
> People should make their choice depending on which defects they're less annoyed with.

Haha!  I like that.  :p

---

### Post by Glucklich on 2009-03-25
Yep. It's all in there. I just miss a couple of rants about how mods say "Linux gaming works great"! "Few games are supported but the ones that are, work flawlessly." And then you go to the gaming section and you see "random lag" threads, along with descriptions of "locks after a while". Yeah, Linux gaming is just great! And then someone tries to sell you that "maybe your graphic card was already broken". Yeah, it's an absolute miracle I spent so many hours on the weekends playing Urban Terror while on Windows.

---

### Post by Twitch6000 on 2009-03-25
I know alot of you fanboys won't admit it,but believe it or not this guy is right on alot of points...

Sure he is adding that extra bit of satire and such,but hey you gotta have fun when blogging :p.

If you reread his blog and think about the point of whatever the topic is I bet you can agree with him if you have an open mind.

Just think about it how many times do you really reboot or shutdown?

Wouldn't you rather have pulseaudio work on ubuntu like it does on fedora rather then it be broke?

So yeah think about it :).

---

### Post by fela on 2009-03-25
> **GepettoBR said:**
> Even worse than that are the people who rant on about how it's free so you don't have the right to complain. "If you don't like it, you got your money's worth. Anything else is an improvement". There's nothing wrong with that per si, but they tend to think that every bit of criticism is in fact a complaint.

I agree with you, but sometimes I find it very hard when people say such things as, 'I downloaded cinelerra and it doesn't do what Premiere Pro did. I downloaded GIMP and it doesn't do what Photoshop did'. I find it very hard not to think about the fact that the latter of each two programs costs 100s of dollars.

I also don't like it when people say the same thing, when they haven't used the program extensively. But worst of all, is when you comment on some blog telling them this, and they call you things like 'freetard' and bully you off the whole blog. Not very constructive now is it?

---

### Post by fela on 2009-03-25
> **Twitch6000 said:**
> I know alot of you fanboys won't admit it,but believe it or not this guy is right on alot of points...

Sure he is adding that extra bit of satire and such,but hey you gotta have fun when blogging :p.

If you reread his blog and think about the point of whatever the topic is I bet you can agree with him if you have an open mind.

Just think about it how many times do you really reboot or shutdown?

Wouldn't you rather have pulseaudio work on ubuntu like it does on fedora rather then it be broke?

So yeah think about it :).

I boot the computer every time I use it, unless it's been downloading stuff.

---

### Post by icp on 2009-03-25
I have no word!!!
:lolflag:

---

### Post by fela on 2009-03-25
> **GepettoBR said:**
> Of course those are unfair comparisons (though there are plenty of clueless "freetards" who will swear that GIMP does everything that Photoshop does, even though they've never used either). I was thinking more about people who cover up flaws with that argument (like that Nautilus bug about resizing dialogs, or the way jockey crashed all the time in early Intrepid).

Oh yeah I hate people who cover up flaws. People claim that open source software gets bugs fixed quicker and yet often the same people pretend those flaws don't exist. That's just stupid.

But anyway about specifically Photoshop and GIMP - I know this is a bit off topic - but the GIMP does seem to lack less and less of Photoshop's features these days. And I do have Photoshop CS4 Extended and GIMP (the second-latest version) so I'm not a "freetard" (that word sounds immature and disgusting even). Also I get the feeling that one of the main reasons alot of people don't like the GIMP is because of its user interface. I was accustomed to the GIMP before PS and, surprise surprise, I now prefer GIMP's interface!

Have a nice day,
Fela

---

### Post by GepettoBR on 2009-03-25
> **fela said:**
> Oh yeah I hate people who cover up flaws. People claim that open source software gets bugs fixed quicker and yet often the same people pretend those flaws don't exist. That's just stupid.

But anyway about specifically Photoshop and GIMP - I know this is a bit off topic - but the GIMP does seem to lack less and less of Photoshop's features these days. And I do have Photoshop CS4 Extended and GIMP (the second-latest version) so I'm not a "freetard" (that word sounds immature and disgusting even). Also I get the feeling that one of the main reasons alot of people don't like the GIMP is because of its user interface. I was accustomed to the GIMP before PS and, surprise surprise, I now prefer GIMP's interface!

Have a nice day,
Fela

I'm also much more comfortable with GIMP's interface, probably because I had been using it for years before I started using PS. If there were something around that does what GIMPshop does but the other way around I might use Photoshop more than I do now. But Photoshop has enough not-in-GIMP features to make a whole new program out of, and unlike most bloated commercial software this includes many that are actually useful. Just to name the one I use the most, GIMP lacks layer styles.Most of the layer style effects can be achieved through combining a few filters, but with Layer Styles you can turn the results on and off and change them around without committing to the image. It's much easier and much more flexible. GIMP has been playing catch-up rather nicely, but there's still a ways to go.

As for "freetard", it's just a word. I get called a lot worse on a regular basis at 4chan, so I guess I'm desensitized :roll:

---

### Post by scottuss on 2009-03-25
I used to read this quite a while ago and just came across this thread. Is it just me or does anyone else suspect that he doesn't actually hate Linux, but is having an elaborate joke?

He knows way too much about Linux not to use it... maybe I'm just stating the obvious here. Ah well......

---

### Post by fela on 2009-03-25
> **GepettoBR said:**
> I'm also much more comfortable with GIMP's interface, probably because I had been using it for years before I started using PS. If there were something around that does what GIMPshop does but the other way around I might use Photoshop more than I do now. But Photoshop has enough not-in-GIMP features to make a whole new program out of, and unlike most bloated commercial software this includes many that are actually useful. Just to name the one I use the most, GIMP lacks layer styles.Most of the layer style effects can be achieved through combining a few filters, but with Layer Styles you can turn the results on and off and change them around without committing to the image. It's much easier and much more flexible. GIMP has been playing catch-up rather nicely, but there's still a ways to go.

As for "freetard", it's just a word. I get called a lot worse on a regular basis at 4chan, so I guess I'm desensitized :roll:

Well to be honest, I think the skill of the artist contributes a damn sight more than extra features...even when they're useful.

I guess I just don't do enough advanced image editing to notice the extras in Photoshop. BTW what PS version do you use?

---

### Post by jimi_hendrix on 2009-03-25
the lies burn my skin, next blog please

---

### Post by t0p on 2009-03-25
If Adobe released Photoshop for Linux platform, would you buy it?

---

### Post by khelben1979 on 2009-03-25
> **t0p said:**
> If Adobe released Photoshop for Linux platform, would you buy it?

I wouldn't, but others would. Gimp is a dissipointment for everyone which migrates off from Windows to Linux, I think.

---

### Post by scottuss on 2009-03-25
> **khelben1979 said:**
> I wouldn't, but others would. Gimp is a dissipointment for everyone which migrates off from Windows to Linux, I think.

I like GIMP but my girlfriend uses Photoshop professionally and had a go on GIMP. Lets just say she still uses Photoshop...

---

### Post by GepettoBR on 2009-03-25
> **fela said:**
> Well to be honest, I think the skill of the artist contributes a damn sight more than extra features...even when they're useful.

I guess I just don't do enough advanced image editing to notice the extras in Photoshop. BTW what PS version do you use?

I use CS2, though I've had a go at CS3 on a coworker's computer. Most of the more advanced features in Photoshop that GIMP lacks only really matter with larger files, print-size, but others are really useful even for simple tasks.

And for the sake of completeness, you can do anything PS does in MS Paint, pixel by pixel.

> **t0p said:**
> If Adobe released Photoshop for Linux platform, would you buy it?

If the price weren't too unreasonable (and by that I mean not more unreasonable than it already is) I probably would. One less chain keeping my Windows partition alive can't be a bad thing.

---

### Post by Seaco on 2009-03-25
I dont understand why people that migrate off windows are disappointed its better than paint

but being real, Gimp is a alternative, a free alternative, i understand people that pay for photoshop, but for me that i am not a professional Gimp is enough

---

### Post by GepettoBR on 2009-03-25
> **Seaco said:**
> I dont understand why people that migrate off windows are disappointed its better than paint

but being real, Gimp is a alternative, a free alternative, i understand people that pay for photoshop, but for me that i am not a professional Gimp is enough

Indeed, GIMP is more than enough for the casual user. I only just recently started using Photoshop because I didn't really feel the need to do anything that GIMP couldn't do.

And comparing GIMP to MS Paint just isn't fair. It's like comparing OpenOffice with WordPad. You can't do that just because they're both the defaut software that comes bundled with the OS for performing the same task :roll:

---

### Post by Dekkon on 2009-03-25
> **Seaco said:**
> I dont understand why people that migrate off windows are disappointed its better than paint

but being real, Gimp is a alternative, a free alternative, i understand people that pay for photoshop, but for me that i am not a professional Gimp is enough

The problem is, that many people state that Gimp is at equal or greater features then Photoshop, which is certainly is far behind in usability and features and most professionals realize this.

---

### Post by asifnaz on 2011-01-01
[http://linuxhaters.blogspot.com/](http://linuxhaters.blogspot.com/)

This guy has some incredible knowledge of Linux . He comes with some very valid points and points out holes and issues with Linux .

His blog is very humorous (sometimes he crosses limits btw) 

I think Linux community should take his criticism positive and try to fix things that he mentions .

A wise enemy is better than a foolish friend

---

### Post by NightwishFan on 2011-01-01
No, my only answer to this guy is he can learn to write better and code some of his complaints himself. :KS

---

### Post by jroa on 2011-01-01
Looks like good reading.  I don't have time right now, so I am going to print it up so I can read it on the toilet.  Then, afterwards, I can use it to wipe with, but it looks a little rough and I might even have trouble flushing it.:lolflag:

---

### Post by Hur Dur on 2011-01-01
I enjoyed [this entry](http://linuxhaters.blogspot.com/2008/06/how-to-be-linux-user.html). Most of the articles on the blog are great reads, but the comments just make me lol. So many people in denial about flaws.

---

### Post by inobe on 2011-01-01
i won't read it but here's what i think, if you don't understand something, you'd be best off not commenting.

anyone else can take it from here :p

---

### Post by Idefix82 on 2011-01-01
It's not like the Linux community is oblivious to issues and flaws with Linux and needs some bored trolls to point them out. I pity these bloggers for the poor upbringing that they seem to have received, judging by the choice of words (provided it's similar to last time I looked, which was two years ago). My sentiments would be the same towards someone who calls himself a Windows hater and uses similarly disgusting language. 

I also pity these people for the fact that they can hate something because it has flaws and some things don't always work. In my mind, you need to have a pretty unstable psyche for that, or you don't know what "hate" means (which is also quite plausible, considering that the entries don't exactly betray a great mastership of the English language).

The irony is that these so called "haters" must actually spend a fair amount of time staying abreast of developments in the Linux world. Poor creatures. It would be so easy to avoid the thing that they hate so much, but then they wouldn't be able to hate it so strongly. Tough dilemma there.

---

### Post by murderslastcrow on 2011-01-01
Hah, I do find it amusing, since it shows how far you shouldn't go, when you should really stop and evaluate what you're doing.

But, for the most part, it's overdramatic and choosy. You can be ignorant in many ways, even if you embrace several operating systems. If you don't admit to your faults, you can't fix them. However, there is a difference in between a fault and a lack of Windowsiness. Anyone who thinks Linux's sole responsibility is to replace Windows, rather than simply to be the best Linux it can be, is probably not going to get a lot of attention.

If you don't acknowledge the small array of limitations Linux has, your hopeful thoughts may end you up in a rough spot. Ie. If you know you're using Linux, don't assume any old piece of hardware will work perfectly with it- do a little bit of research. Even though mostly everything is supported, some of it isn't supported as well as other hardware. And if you can't make a commitment to using an open format, but you need a closed program to use the format you're used to, do what you need to to continue using that program.

I hate these people who think it has to be all or nothing. Better that you have some open source than none, I say.

---

### Post by Ichtyandr on 2011-01-01
I had a look, he seems a smart guy who knows a lot on the subject matter. 
His attitude is questionable though. On the one hand he claims that Linux users are 'losers' who are in denial, on the other hand he himself sounds like one. 
anyways being in denial cannot be proven or disproven (because it consists in denial, like the liar paradox) and being a loser is either and opinion or an attitude (which he seems on the first glance to share)

---

### Post by nrs on 2011-01-01
He has some valid criticisms but I think most of the time he's nitpicking and being overly dramatic.

---

### Post by alexan on 2011-01-01
There are blog nearly for everything: its basically the Rule34 for people personal ego.

*If it can be thought, it can be made a blog of it*

---

### Post by wyliecoyoteuk on 2011-01-01
Just had a quick look.
Not changed,still the same foul-mouthed, badly written puerile rubbish that it was last time I looked.

---

### Post by MooPi on 2011-01-01
The Rant about ogg ranks up there with (Net Neutrality is slowing down innovation). Pointless mess that says little :(

---

### Post by Arex Bawrin on 2011-01-01
I thought it was funny and nothing more.

---

### Post by Paqman on 2011-01-01
He seems like he gets a kick out of making Linux fans dance :lolflag:

---

### Post by muuwt1 on 2011-01-01
this guy sucks. stop blogging get a life. like reading up on ubuntuforums

---

### Post by Dustin2128 on 2011-01-01
I think it's funny if he's trolling. If not, I think he needs to get out of the year 1993.

---

### Post by TNT1 on 2011-01-01
To para-phrase: 'foul mouthed puerile rubbish...' that just about sums it up.

---

### Post by realzippy on 2011-01-01
"*This guy has some incredible knowledge of Linux*"
[B]
? [/B]



...you know him,eh?

---

### Post by gnomeuser on 2011-01-01
Miguel de Icaza once mentioned in an interview that he knew who the Linux Hater was. Apparently he works with supporting Linux and knows about our deficiencies both in providing a platform and our current state.

*edit*

Found it, for reference the Linux Hater bit starts around 28mins in.

[http://herdingcode.com/?p=109](http://herdingcode.com/?p=109)

---

### Post by aysiu on 2011-01-01
Merged.

---

### Post by jshepherd on 2011-01-01
I thought he was quite funny really.
And as much as I don't want to admit it, a lot of what he's saying is true.

---

### Post by Giant Speck on 2011-01-01
> **muuwt1 said:**
> this guy sucks. stop blogging get a life. like reading up on ubuntuforums
The above post contains irony.

---

### Post by johntaylor1887 on 2011-01-01
*"This "choice", as loudly as it is trumpeted, is a key reason that Linux has not made it on the desktop."*

Who says linux has to "make it" on the desktop to be successful? Too many of these "writers" are just too full of themselves, and think their wisdom is gospel. Plus, it only leads to arguments that are not productive. 


> **Paqman said:**
> He seems like he gets a kick out of making Linux fans dance :lolflag:
Exactly. 

I may lurk just to have a good laugh.

---

### Post by Old Marcus on 2011-01-01
I'd like to chip in here, and mention that there are people who are utterly *terrified* of choice. I was in Subway the other day and this lady was in front of me. She was scared by the choice of fillings on offer, and kept forgetting what she had ordered, then harangued the man behind the counter saying she didn't even like Subway anyway, and only came because her friend made her. I walked out roaring with laughter, I must admit.

---

### Post by Austin25 on 2011-01-01
I don't mind if someone prefers their operating system over mine. I can tolerate (to an extent) if people believe their operating system is better. Why I really support Linux with such zeal is when standards are made that make my system appear to those without perspective as inferior, then using this illusion of inferiority as propaganda to discourage the curious, then use the small trial rate as further propaganda supporting those companies that create said closed standards. It's a loop of pain that only benefits the brave and the evil.

Then again, here on ubuntuforums I'm just preaching to the choir.

---

### Post by Ahava591 on 2011-01-01
These were funny:

*..."You can go on and continue to waste keynotes at conferences (yea, I'm  sure the the organizers are super happy about that) to complain about  people "stealing" your code. Waaa Waaa. Someone took my hippy license  and took my code and isn't giving it back. Waaa....."*


[I]"Some other notes for yahoo:

 - These are Linux users. They are too cheap to click on your ads.

 - These are freetards. They think it's cool to use adblock and pirate music...."[/I]


He's cute, ultimately annoying; I imagine sits at his computer ranting more than the "freetards," sit at theirs' writing code.

---

### Post by Austin25 on 2011-01-01
Maybe he should try FreeBSD.:lolflag:

---

### Post by loell on 2011-01-01
It's Funny when you have deep understanding with the current free software ecosystem. many developers did concur with some of his points.

But make no mistake, it's a troll trap for noobs and an entertainment for the savy. :p

of course one might conclude that he prolly moved on to better and more awesome  things, his last entry was on July last year. ;)

---

### Post by ninjaaron on 2011-01-02
That website is great. I like Linux just fine, but I'm glad that are people around to tell us that our **** stinks too. Someone's got to take us down a notch.

---

### Post by barx on 2011-01-02
What can I say, some people look that kind of attention, you know, they try to do something to be the center of the attention.

Whatever.

Maybe,yes, don't like it or they love it so much, who cares.

I'm glad that there are few people that know and enjoy linux.

The more are pribative programs, the more  malaware.

Seems that our infamous operating system give certain advantages instead of contaminating like WInbug$, and recently Mac is introducing malaware . . What the heck with that guys? 

They think that creating the poison they can find the cure?

Selling antivirus programs don't resolve anything.

That why my first choice is linux, is secure becuase remains unknown to bad hands. Nothing's imposible, remember that there's always a way to waste everything in sake of "$ell".

Anyway i like to discover new things like try to fix my laptop problems. It's such interesting and sometimes usless, but make me more wise compling and that kind of stuff xD.

---

### Post by juancarlospaco on 2011-01-02
A nice Engrish funny blog.

---

### Post by Evil-Ernie on 2011-01-02
Just another blog to wind up fanboys and watch the fireworks.
Mildly amusing but thats all.

---

### Post by cf0531 on 2011-01-03
I went to the link and this guy doesn't seem educated at all. Grammar and spelling errors aside, the last article posted that I looked at was talking about 3d graphics and computer games. If your using linux it isn't for game compatibility, it's being used by people who are actually being productive. And the way he brought up screenshots made it sound like it was his only window, pardon the pun, into the linux world. Granted, I can see how most people with little or no knowledge of computers would prefer windows. It's meant to pretty much work out of the box, it's great if your only use for a computer is playing fallout3 and call of duty or whatever the kids are doing these days, but some people like flexibility and like community and for some the other option works better. I dunno, i guess this guy just seems ill-informed.

---

### Post by jasonshim on 2011-01-03
Wow.. I'm shocked

I expected some kind of incoherent ramblings and rants upon seeing the word "hater".

Contrary to my expectations, I found all of the excerpts very compelling and coherent.

He does know what he is talking about. 

Actually, the excerpts reminded me of several books, like How We Decide and Nudge, on

decision-making process and psychology I read few months ago.

Throwing bunches of choices simply doesn't work well for most people like he said.

The sheer number of choices tends to baffle and overwhelm people and prevents them from 

making choices.

---

### Post by matt_symes on 2011-01-04
> freetard

? Luddite

---

### Post by Evil-Ernie on 2011-01-04
> **jasonshim said:**
> Throwing bunches of choices simply doesn't work well for most people like he said.
 
The sheer number of choices tends to baffle and overwhelm people and prevents them from making choices.
 
Are people on here familiar with Father Ted?
 
This comment makes me think of Dougal and his inability to make simple choices to such a degree he nearly has a mental breakdown when faced with a decision on 'heads or tails'! I can imagine some users when faced with Linux being in a somewhat similar situation
:lolflag:

---

### Post by 3Miro on 2011-01-04
> **cf0531 said:**
> I went to the link and this guy doesn't seem educated at all. Grammar and spelling errors aside, the last article posted that I looked at was talking about 3d graphics and computer games. If your using linux it isn't for game compatibility, it's being used by people who are actually being productive. And the way he brought up screenshots made it sound like it was his only window, pardon the pun, into the linux world. Granted, I can see how most people with little or no knowledge of computers would prefer windows. It's meant to pretty much work out of the box, it's great if your only use for a computer is playing fallout3 and call of duty or whatever the kids are doing these days, but some people like flexibility and like community and for some the other option works better. I dunno, i guess this guy just seems ill-informed.

I agree with almost everything that you say. My only objection is about Linux not being suitable for windows games. It is true that many games do not run (or do not run well), but once something runs under wine, then it runs. I have been making a huge mod for Civilization IV for couple of years now and I am using Linux. In fact, I could not have been as productive, if I had to work under Windows. I tried using Windows first, but oh the horror of having 10 windows open on one workspace, not to mention how easy it is for the game to crash the entire system. Under Linux, I can open/move/edit code many times faster, with multiple workspace I can be much better organized and regardless of what I do to crash the game, Linux doesn't crash.

Linux being bad for games is a myth (just as much as the rest of that nonsense that they are spewing on that blog).

---

### Post by kevxh on 2011-01-05
> **Evil-Ernie said:**
> Are people on here familiar with Father Ted?
 This comment makes me think of Dougal and his inability to make simple choices to such a degree he nearly has a mental breakdown when faced with a decision on 'heads or tails'! I can imagine some users when faced with Linux being in a somewhat similar situation


Now I'm smiling! If you ever respond to the linux hater guy I think he should be called Dougal!

I've always been of the opinion that the diversity in Linux is the single reason for the general fear of it. The 'Linux is for nerds' response is just a garbage excuse, the real problem is fear of change, the unknown and having to make decisions. It took a long time (and many distros) for me to decide on Ubuntu, and I've recently switched to Xubuntu (yesterday in fact). Funny how the linux hater uses Google Blogger.

There are those of us that have the mental capacity to relish choice, sadly the majority of people are sheep. Why? That would be an ecumenical matter.

---

### Post by cf0531 on 2011-01-05
> **3Miro said:**
> 
Linux being bad for games is a myth (just as much as the rest of that nonsense that they are spewing on that blog).

There have been many strides to make games work better in linux, especially with a distro like ubuntu. All i'm saying is that if thats a chief complaint, it's not a good one. Not to mention the guys excessive use of profanity. We all use it from time to time, but when trying to make your points seem valid it doesn't help you to seem intelligent. And I haven't had compatibility issues for a while now, the oldest distro i've used was gutsy. lucid and mav have worked right off on any system I've put them on. Of course I see the last post was July, perhaps he ran out of things to complain about or he finally realized ubuntu actually works.

---

### Post by fabricator4 on 2011-01-05
> **Jim! said:**
>  Personally I think this guy makes some great points and knows exactly what he's talking about.

Personally I think this guy has completely **_missed_** the point and hasn't really got a clue.

I have to ask myself why anyone would bother wasting their time unless they are a M$ employee or have some other axe to grind.  I read a couple of those "articles" and came to the conclusion that there was no way he would get the point - he's not interested in discussion and is quite happy to follow the rest of the sheep into the slaughter house.  Worse than that, he wants everyone else to follow as well, and fails to see why we want to remain as wolves.

Baaaaa!


Chris

---

### Post by Windows Nerd on 2011-01-05
His obsessive use of profanity makes me lose any respect I would have had.

Note that below when I mention hacker/hack, I _do not mean cracker_ or anything below that sense. I mean the original connotation, before Hollywood/other media changed it.

He does make a good point, though he does forget one key point: Linux began as a hacker's operating system, designed by one for one. Until about 5-ish years ago, Linux made almost no effort at all to be easy to use. You would have to be willing to learn a lot. One would have to have the type of personality where they loved learning about things, even if they never really use that knowledge. They had to be the type that liked to know how stuff works. All these are traits of a hacker, and a geek. All of this is still present (but less so than it was) within the Linux community, and among many, many developers. Because the developers are "in charge" to some point, this attitude still lives on. Additionally, many members of the vast Linux community are a person with those traits I outlined, and computers are their passion.

Linux is moving forward as fast as it ever has, and issues are always trying to be addressed by some member of the community or community groups or devs that care about the issue. This is the power of the Linux community in a nutshell: if you want to make it happen, _you can_.

Linux has its faults sure enough, we admit them, but people have to remember that:
-Linux is free/open-source/libre/open/whatever. There is no company managing it with the intent to get at your money, information, ect. Your freedom is preserved.
-Linux costs you nothing (unless, of course, you choose a distribution that does cost something), so if you are not satisfied with it, no big deal, because you don't lose any money.

A little more than just my 2 cents.

Scott

---

### Post by sparky295 on 2011-01-06
I have rather enjoyed reading all of the replies to this post but in the end, for me it all boils down to stability and performance in the areas for which i use an os ! after a 10 year hiatus i descided to try win7 (who knows mabe they got something right this time) well after that orchestrated nightmare of repartitioning 3 times (the install took 22gig instead of the required 16 Grr) than after getting it running properly i installed the "required" security updates (which totally messed the MBR) so on and so fourth !
now after a day i already have a virus. as well the mbr could only be fixed using a linux live cd since the windows rescue disk would just hang up!!!
    Ubuntu i use for most everything  though i prefer mint for multimedia, Fedora for social networking, Sabayon for gaming but i use puppy and Crunchbang for most partitioning and system maintenance. 
I all comes down to personal choice and no one OS will ever be able to meet everyones needs! 
LOL now i just have to figure out how to port mac/os to my aspire5532 and see how it runs

---

### Post by Evil-Ernie on 2011-01-06
> **kevxh said:**
> The 'Linux is for nerds' response is just a garbage excuse, the real problem is fear of change, the unknown and having to make decisions. 
 
Gah! Too true. Its been proved it can be used by non-nerd people perfectly fine in the mobile OS's of many phones (yet people are just not aware that they are using a Linux based system) and in places like France there is some agencies using Linux as a day-to-day office tool. 
 
Its the learning curve that seems to be the stumbling block, but even if you go from lets say Win98 to Win7 (which some people do!) that is a lot to learn new, just like going from XP to Ubuntu.

---

### Post by cf0531 on 2011-01-10
I don't really see where there is much to learn from the switch from windows to ubuntu. I think it boils down to misconceptions. I didn't want to make a complete switch because I thought I'd be completely screwed somewhere down the line. I find that there hasn't come a situation that I haven't been able to complete a task or to even do it better. of course 10 years ago that switch was way harder to make unless you really new what you were doing, but now it's rather easy. People still have this idea that linux is complicated and you can't do anything unless you know how to do it via command-line, and at one time that was true, but now it's getting to the point where it is an actual alternative for the average desktop user. Thank god for that.

---

### Post by eddier on 2011-01-11
I like the bit about Linux users being freeloaders/booters(wow,was that a pun?).

PAY for software thats going to phone home...Hmmmmmmmmmmmm.

I like to think that those who (use otherwise) might just be persuaded to PAY us to use Linux. You know,get them to click on a few pop-ups,watch some flash presentations,redirect them to a begging site and explain how Grandpa left us Millions in ....etc.

On the other hand they might just report us 'Pirates and Hackers' to the Authorities for using Hacking Software on 'Cracked' PC's.

Oh I give up--as long as people pay me to fix their broken (Other) machines I couldnt give a toss!

eddie

---

