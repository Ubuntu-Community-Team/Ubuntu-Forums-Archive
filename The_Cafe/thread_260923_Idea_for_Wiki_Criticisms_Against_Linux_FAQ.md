---
title: "Idea for Wiki: Criticisms Against Linux FAQ"
date: 2006-09-19
forum: The Cafe
---

### Post by aysiu on 2006-09-19
I started writing this document a little while ago--intending for it to be a webpage--and I started thinking maybe we should have a Wiki page that answers criticisms of desktop Linux (or Ubuntu specifically, whichever makes more sense): > You've heard them many, many times--both made and refuted.
<p>
Here, I am outlining the frequent criticisms of desktop Linux and what I think they <i>really</i> mean. In other words, the perceived problems should not necessarily be solved in the way people think.
<p>
<b>Linux has terrible hardware support. It needs better/more drivers</b><br>
The typical Linux advocate response is that Linux actually supports more hardware than Windows does. Well, Windows doesn't really need to support PowerPC or SPARC, does it? When people make this criticism, what they mean is that they can't just buy a printer at a store and <i>know</i> it'll work with Linux. Then, you get the other typical Linux advocate response that you wouldn't buy a Gamecube game and expect it to work on the XBox.
<p>
Well, herein lies the real problem--not that Linux has terrible hardware support. It actually has excellent hardware support. The two real problems (one stems from the other) are that Linux hardware support isn't commercially nigh-universal and that information about compatibility is not easily available/understandable to everyday consumers.
<p>
Windows doesn't make drivers for all the hardware that works with it, but the hardware manufacturers do. If Windows doesn't recognize the new monitor you just bought, chances are the hardware came with a CD-ROM full of Windows drivers. Mac supports very little hardware--even less than Linux--but Mac-compatible peripherals, like Gamecube and XBox games--are clearly labeled with a blue smiley face that has a big scar down the middle, indicating the device is Mac-compatible.
<p>
This is the real problem. If I want to know if a peripheral (scanner, printer, monitor, sound card, wireless card) is Linux compatible, I have to track it down on a Linux compatibility list. I can tell without looking that almost every peripheral out there is either natively supported by Windows or comes with a Windows driver, and I can tell if it's Mac-compatible by just looking at the box.
<p>
Right now, our best bet would be to have one centralized location for Linux hardware compatibility--a professional-looking website that is easily searchable. When you found the device in question, you would get a list of which distros it's known to work with, workarounds that are necessary to get it to work if it doesn't already, or a question mark if there's not enough information about the device.
<p>
LinuxCompatible.org doesn't cut it right now.
<p>
<b>There are too many versions of Linux, making it hard for a new user to choose a distro. We need a unified distro.</b><br>
Choice is a good thing. When it comes to food, cars, houses, clothes, and vacation spots, no one complains about the existence of choice.
<p>
However, when it comes to choosing a retirement plan or a Linux distribution, suddenly the complaints come out. The reason for this isn't the existence of choice but the lack of easily understandable information about the choices. The problem is the need to make an <i>informed</i> choice.
<p>
If you're looking for a distribution to start with, take <a href="http://www.zegeniestudios.net/ldc/">this quiz</a>. If you want to compare distros, go to <a href="http://distrowatch.com/dwres.php?resource=major">DistroWatch</a>. Make an informed choice.
<p>
<b>In order for the average user to use Linux, it need to be easier to install</b><br>
Average users never install operating systems. If they don't install Windows, why would they install Linux? Preinstallation is the only viable solution for the average user not being able to use Linux. Either the manufacturer has to preinstall and preconfigure Linux or a friend of the average user has to. The idea isn't to say "I'm right and you're wrong."

The idea would be to achieve these goals:

1. Make critics of desktop Linux aware that their criticisms have already been voiced. They don't need to voice them again.

2. Redirect critics to what the *real* problems might be instead of what the *perceived* problems are.

3. Focus on practical solutions instead of complaining--what you and I can do to improve the situation of Linux on the desktop.

I started typing, and then I realized... I can't do this alone. So I'm open sourcing what I wrote and asking people to contribute, add, modify as they see fit.

I know nothing about creating or maintaining Wiki pages. I tried reading the Wiki beginner guide, but it didn't make sense to me. I'm not very tech-savvy in comparison to most regular users on these forums.

What do people think?

Is this necessary? Should it be approached in a different way?

I was just thinking, if we answer questions about sudo with this link: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo), why couldn't we answer criticisms against desktop Linux with a link from the FAQ instead of arguing back and forth for pages and pages...?

---

### Post by Brunellus on 2006-09-19
Go for it aysiu.

---

### Post by Pelekophori on 2006-09-19
A very sensible idea.

---

### Post by GeneralZod on 2006-09-19
I think this is an excellent idea.  I might go and raid the Autopackage site for answers to the old (and oft recurring) "Why are there no .exe installers for Linux?"  Your essay ([http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)) goes into very helpful detail about how to install things under Linux, but I'm betting many people are still in the dark about why installation of Linux apps proceeds in the way it currently does, so I might have a go at tackling that aspect :)

Edit:

"Why is Linux taking up all 1GB of my RAM!" might be another good one.

---

### Post by aysiu on 2006-09-19
Okay, the page is up.
[https://wiki.ubuntu.com/CriticismFAQ](https://wiki.ubuntu.com/CriticismFAQ)

Feel free to add, change, remove, reorganize as you see fit.

I'd never created a Wiki page before this, so the formatting and organization is way off. If someone wants to clean it up, I would be most appreciative.

---

### Post by Brunellus on 2006-09-19
I made some minor cleanups.  Otherwise an excellent start.

---

### Post by aysiu on 2006-09-19
> **Brunellus said:**
> I made some minor cleanups.  Otherwise an excellent start.
Thanks for that cleanup job.

---

### Post by ago on 2006-09-19
An excellent idea.  

> Right now, our best bet would be to have one centralized location for Linux hardware compatibility--a professional-looking website that is easily searchable. When you found the device in question, you would get a list of which distros it's known to work with, workarounds that are necessary to get it to work if it doesn't already, or a question mark if there's not enough information about the device.
That is why I made this proposal: [https://wiki.ubuntu.com/SupportedHardwareListProposal](https://wiki.ubuntu.com/SupportedHardwareListProposal)

---

### Post by aysiu on 2006-09-19
> **ago said:**
> An excellent idea.  


That is why I made this proposal: [https://wiki.ubuntu.com/SupportedHardwareListProposal](https://wiki.ubuntu.com/SupportedHardwareListProposal)
Right on!

---

### Post by ago on 2006-09-19
And I have another one for you

> Average users ''never'' install operating systems. If they don't install Windows, why would they install Linux? Preinstallation is the only viable solution for the average user not being able to use Linux. Either the manufacturer has to preinstall and preconfigure Linux or a friend of the average user has to.

[https://features.launchpad.net/distros/ubuntu/+spec/ubuntu-setup.exe](https://features.launchpad.net/distros/ubuntu/+spec/ubuntu-setup.exe)

---

### Post by maniacmusician on 2006-09-19
[http://dohickey.project.googlepages.com](http://dohickey.project.googlepages.com)  this project is still in super early development. right now we're basically just working on including more features for inputting information, and looking to create compatibility with all systems (had a spell before where it wouldnt run on 64bit systems). after that's confirmed (we havnt confirmed it yet because not too many people have stepped up to test it), the next few releases will concentrate on getting the server side of it set up.

if anyone would like to check it out and test it, it'd be a great help. instructions for feedback and whatnot are on the download page.

this program was started at the same time ago made that wiki page. that's when the idea was spawned at least, by DoctorMO. I personally think it has great potential. nice job on that wiki aysiu, it should save users plenty of back and forth posting on the forums lol.

---

### Post by ago on 2006-09-19
I didn't know you started the website! Good work! I might get involved, only problem is that any day I find a new project, I need a 48H day... :)

Please consider using the guidelines outlined in my proposal (see above)!

---

### Post by maniacmusician on 2006-09-19
> **ago said:**
> I didn't know you started the website! Good work! I might get involved, only problem is that any day I find a new project, I need a 48H day... :)

Please consider using the guidelines outlined in my proposal (see above)!
heh, i know what you mean. I wish i could help with the coding of Dohickey, but i can't code at all. so i just whipped up the website with googlepages, and i maintain it for martin. 

We havn't really gotten to the server aspect of it yet, but we will definitely consider those guidelines, they seem pretty well thought out. we might add more to it as well. trying to make it as comprehensive as possible.

---

### Post by henriquemaia on 2006-09-19
After "Posts: 15,971", I think I can understand what you feel.

---

### Post by ago on 2006-09-19
> **maniacmusician said:**
> heh, i know what you mean. I wish i could help with the coding of Dohickey, but i can't code at all. so i just whipped up the website with googlepages, and i maintain it for martin.

That type of project will certainly need a CMS and probably some custom plugins for the hardware list. Or maybe a RoR/TG website. If it was me, unless there is a CMS that fits the bill quite well (Drupal?) I would use TG (but I am biased, I do not know much of Ruby).

---

### Post by SoundMachine on 2006-09-19
> **aysiu said:**
> I started writing this document a little while ago--intending for it to be a webpage--and I started thinking maybe we should have a Wiki page that answers criticisms of desktop Linux (or Ubuntu specifically, whichever makes more sense):  The idea isn't to say "I'm right and you're wrong."

The idea would be to achieve these goals:

1. Make critics of desktop Linux aware that their criticisms have already been voiced. They don't need to voice them again.

2. Redirect critics to what the *real* problems might be instead of what the *perceived* problems are.

3. Focus on practical solutions instead of complaining--what you and I can do to improve the situation of Linux on the desktop.

I started typing, and then I realized... I can't do this alone. So I'm open sourcing what I wrote and asking people to contribute, add, modify as they see fit.

I know nothing about creating or maintaining Wiki pages. I tried reading the Wiki beginner guide, but it didn't make sense to me. I'm not very tech-savvy in comparison to most regular users on these forums.

What do people think?

Is this necessary? Should it be approached in a different way?

I was just thinking, if we answer questions about sudo with this link: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo), why couldn't we answer criticisms against desktop Linux with a link from the FAQ instead of arguing back and forth for pages and pages...?

I think it is a great idea, bookmarked and instead of posting a rebuttal i can just link to this, i'll contribute if and when i think i have something to add. :)


You made my life easier and probably a lot others, i'll spread this on all forums i think it's appropriate to spread it in.

Thanks.

---

### Post by SoundMachine on 2006-09-19
> **maniacmusician said:**
> [http://dohickey.project.googlepages.com](http://dohickey.project.googlepages.com)  this project is still in super early development. right now we're basically just working on including more features for inputting information, and looking to create compatibility with all systems (had a spell before where it wouldnt run on 64bit systems). after that's confirmed (we havnt confirmed it yet because not too many people have stepped up to test it), the next few releases will concentrate on getting the server side of it set up.

if anyone would like to check it out and test it, it'd be a great help. instructions for feedback and whatnot are on the download page.

this program was started at the same time ago made that wiki page. that's when the idea was spawned at least, by DoctorMO. I personally think it has great potential. nice job on that wiki aysiu, it should save users plenty of back and forth posting on the forums lol.

I really like this since it's not Ubuntu centered only, the drivers are in the kernel and pretty much every distro that uses one kernel will have the same driver support.

Good job. :)

---

### Post by maniacmusician on 2006-09-19
> **ago said:**
> That type of project will certainly need a CMS and probably some custom plugins for the hardware list. Or maybe a RoR/TG website. If it was me, unless there is a CMS that fits the bill quite well (Drupal?) I would use TG (but I am biased, I do not know much of Ruby).
****, i don't even know what most of that is. really, i'm pretty much a simpleton at development, etc. i just wanted to create a user-friendly space for dohickey that normal users could feel comfortable in. dohickey isn't a traditional program, it's a python script (which is why it's easily compatible with many systems). 

the best way to really support this project is to download, test, and provide feedback. To my knowledge, only 4 people have tested it, including the developer and myself. so more testing would be great. It's not hard to test, honest. just download and run the script, provide feedback like the info page says.

---

### Post by SoundMachine on 2006-09-19
> **maniacmusician said:**
> ****, i don't even know what most of that is. really, i'm pretty much a simpleton at development, etc. i just wanted to create a user-friendly space for dohickey that normal users could feel comfortable in. dohickey isn't a traditional program, it's a python script (which is why it's easily compatible with many systems). 

the best way to really support this project is to download, test, and provide feedback. To my knowledge, only 4 people have tested it, including the developer and myself. so more testing would be great. It's not hard to test, honest. just download and run the script, provide feedback like the info page says.

It's just ago trying to be cute, don't mind him, you are doing what he has been talking about for quite a while, keep going, you know for everyone who spreads the word there will be an exponential effect that will eventually lead to a lot, everything in FLOSS goes through a slow start, if you don't believe me, just ask Linus. ;)

---

### Post by maniacmusician on 2006-09-19
> **SoundMachine said:**
> It's just ago trying to be cute, don't mind him, you are doing what he has been talking about for quite a while, keep going, you know for everyone who spreads the word there will be an exponential effect that will eventually lead to a lot, everything in FLOSS goes through a slow start, if you don't believe me, just ask Linus. ;)
haha, yes i suppose. in the meantime, i'm just trying to post the link every time i get a chance. not like spamming or anything, of course. just spreadin the gospel ;)

---

### Post by SoundMachine on 2006-09-19
> **maniacmusician said:**
> haha, yes i suppose. in the meantime, i'm just trying to post the link every time i get a chance. not like spamming or anything, of course. just spreadin the gospel ;)

Put it in your signature on every forum you visit, notice mine below. ;)

---

### Post by aysiu on 2006-09-19
Wow!

Wow!

I go away for a few hours, come back, and the Wiki page is *loaded* with new questions and answers.

That's the community coming together. Thank you all for contributing and for continuing to contribute.

I really appreciate the effort you've put in.

---

### Post by maniacmusician on 2006-09-19
=-O hey, thanks! I suppose I should do that. But i never really notice people's sigs, so i assumed people wouldn't notice mine either. but thanks, i'll do that.

btw, weren't you the one who originally called the script worthless XD sorry it didn't work on your machine the first time around. does it work now? it was supposed to have been fixed.

---

### Post by maniacmusician on 2006-09-19
> **aysiu said:**
> Wow!

Wow!

I go away for a few hours, come back, and the Wiki page is *loaded* with new questions and answers.

That's the community coming together. Thank you all for contributing and for continuing to contribute.

I really appreciate the effort you've put in.
It was an awesome intitiative, aysiu. I can't believe it hasn't been done before. It already contains many of the matters that are most confusing for new users. i'll definitely be pointing any new users I come across to the page.

---

### Post by SoundMachine on 2006-09-19
> **maniacmusician said:**
> =-O hey, thanks! I suppose I should do that. But i never really notice people's sigs, so i assumed people wouldn't notice mine either. but thanks, i'll do that.

btw, weren't you the one who originally called the script worthless XD sorry it didn't work on your machine the first time around. does it work now? it was supposed to have been fixed.

You will find that i can be against something but not the idea of it, i'm from the BSD world where the hardware list is set in stone and all you need to do is look through one document, i realized that even the kernel does not have such a doc without going through hundreds of changelogs so i changed my mind.

I can't even test it at the moment, i'm on Vista right now but give me a day and i'll contribute.

---

### Post by maniacmusician on 2006-09-19
it's okay, no rush. 

err, oops. kind of got a little off topic.

---

### Post by coastdweller on 2006-09-19
Linked* great work =)

---

### Post by Brunellus on 2006-09-20
Further changes, minor edits, more cleanup.  Page is now organized into questions arising before, during, and after an install.

---

### Post by ago on 2006-09-20
> **maniacmusician said:**
> ****, i don't even know what most of that is.
My suggestion was mostly concerning the website required to display "the results". I.E. the website containing the hardware list itself. The Dohickey website can be a static one, but the one where you show the results must be dynamic. Probably thinking about the hardware list page is a bit premature ATM.

When the time will come consider investing some time to learn what a CMS is. It might come out really useful and save you a LOT of work in the future. Here is a good example: [http://drupal.org/](http://drupal.org/)

PS I will test Dohickey tonight

---

### Post by ago on 2006-09-20
As a note, some FAQ answers can be generic and apply to all Linux distros, but some answers (install/post-install) become confusing unless we tie them to a specific distro. Any guidline?

---

### Post by maniacmusician on 2006-09-20
> **ago said:**
> My suggestion was mostly concerning the website required to display "the results". I.E. the website containing the hardware list itself. The Dohickey website can be a static one, but the one where you show the results must be dynamic. Probably thinking about the hardware list page is a bit premature ATM.

When the time will come consider investing some time to learn what a CMS is. It might come out really useful and save you a LOT of work in the future. Here is a good example: [http://drupal.org/](http://drupal.org/)

PS I will test Dohickey tonight
of course, the server with the hardware list will be dynamic, there's no way we'd update that by hand lol. the script will send results of it's scan back to the server and it will organize the information categorically.

---

### Post by Brunellus on 2006-09-20
> **ago said:**
> As a note, some FAQ answers can be generic and apply to all Linux distros, but some answers (install/post-install) become confusing unless we tie them to a specific distro. Any guidline?
Since it's the Ubuntu wiki, I see no problem about keeping the scope on Ubuntu.  It is not, frankly, our job to be the apologists for everybody else's distro.

Also, dohickey devs and other interested persons:  maybe it's time to move technical discussion on your project to another thread.

---

### Post by maniacmusician on 2006-09-20
> **Brunellus said:**
> Since it's the Ubuntu wiki, I see no problem about keeping the scope on Ubuntu.  It is not, frankly, our job to be the apologists for everybody else's distro.

Also, dohickey devs and other interested persons:  maybe it's time to move technical discussion on your project to another thread.
:( yeah sorry got a little sidetracked. no more dohickey postings here.

---

### Post by ubuntu_demon on 2006-09-22
aysiu this is a great idea and project :
[https://wiki.ubuntu.com/CriticismFAQ](https://wiki.ubuntu.com/CriticismFAQ)

DoctorMO and maniacmusician good luck with Dohickey I hope it succeeds ! [http://dohickey.project.googlepages.com/home](http://dohickey.project.googlepages.com/home)

this specification written by Ago is great :
[https://wiki.ubuntu.com/SupportedHardwareListProposal](https://wiki.ubuntu.com/SupportedHardwareListProposal)

We have a great community :)

Let's get back on topic now :D

---

### Post by ago on 2006-09-22
> **ubuntu_demon said:**
> I'm not sure whether Ago is a member of the forums

:confused:

---

### Post by ubuntu_demon on 2006-09-22
> **ago said:**
> :confused:
Hey there!

Sorry :) 

Great work on that spec!!

---

### Post by B0rsuk on 2006-09-22
aysiu:
creating such FAQ would be like admitting a weakness. And it's like having a war with another country and fighting it on your territory.

---

### Post by Brunellus on 2006-09-22
> **B0rsuk said:**
> aysiu:
creating such FAQ would be like admitting a weakness. And it's like having a war with another country and fighting it on your territory.
the FAQ is already a fact, so you're a bit late to the party.

Once again guys:  this is NOT war.  If Microsoft is crushed by free software, that's an entirely unintended consequence, to paraphrase Linus Torvalds. 

The document, as I read it, addresses common concerns in a frank and open way.  We should not be afraid of the truth.

---

### Post by Carrots171 on 2006-09-22
> **B0rsuk said:**
> aysiu:
creating such FAQ would be like admitting a weakness. And it's like having a war with another country and fighting it on your territory.

What's wrong with admitting weaknesses? Actually,[ not admitting any weaknesses can lead to people being disappointed with Linux]("http://www.ubuntuforums.org/showthread.php?t=259479"). 

Also, I think that this FAQ deals with weaknesses that people often encounter, so there's nothing to admit.

---

### Post by DoctorMO on 2006-09-22
Just reading the backlog, the link to the project page is [https://sourceforge.net/projects/dohickey](https://sourceforge.net/projects/dohickey) but I'll post that to the main thread too.

---

### Post by maniacmusician on 2006-09-22
This FAQ is most certainly not a negative thing. All it does is save us from having to post the same stuff over and over. Now we just give them a link, and a bunch of their questions get answered all at once. Effective, educational, painless. What's not to like about it?

---

### Post by weatherman on 2006-09-22
shouldn't canonical's commercial support be mentioned in the "There is no support for Linux!" faq?

---

