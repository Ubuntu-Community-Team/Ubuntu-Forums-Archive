---
title: "How to improve Ubuntu"
date: 2005-07-03
forum: The Cafe
---

### Post by WMCoolmon on 2005-07-03
I am a longtime Windows user, although in the last few years I've dabbled a bit in Linux here and there. Very recently, I upgraded to a SATA drive, and all my attempts to slipstream drivers onto the Windows 2000 install disc have failed, so I figured that I might as well make an attempt to move completely to Linux.

Well, it hasn't been that easy. Red Hat was bloated with unneeded apps and did very little. Yoper was good, but support was lacking. Gentoo was awful from the very start; no one bothered to update the manual to note the apparently-known fact that a certain combination of USE flags wouldn't work.

On the plus side, all the software is free. But I've yet to see the Linux that is reliable and flexible, rather than cumbersome, easily broken, and simply difficult to use.

So I've decided to try and document a list of all the problems I('ve) come across, in the hopes that something will be done in the next Ubuntu version. There are probably legal reasons behind some of these, but, well, these are probably things I took for granted in Windows.

**- Lack of out-of-the-box midi support**
Something that seems pretty major to me. At the very least, this should be an "apt-get install midi" (to make it optional and keep bloat down)

**- Lack of out-of-the-box DVD support**
Something relatively new, but still very nice to be able to pop in a DVD and be able to play it without any additional software. DVD players are pretty commonplace.

**- Lack of out-of-the-box MP3 support**
I'm actually not 100% sure on this one, but it seems to me that I had to install *something* to get MP3s to play. I believe it was beep-media-player; this is something that should be possible right out of the box.

**- WAV support**
Same deal as MP3s and DVDs, I believe I had to install something special to get this working.

**- Totem is basically worthless**
Why it's the default media player, I don't know. But it seems like it can't play anything it tries to open, unless you switch to totem-xine. Then, Totem becomes useful.

**- No easy way to get Java installed**
Again, this may be a legality issue, but it would be enormously handy to be able to be able to just throw in "apt-get install java-mozilla" and have the plugin and everything installed and ready to go (much like Flash). This is something of a pain on AMD64; on my previous Ubuntu install attempt, I installed Sun's JRE rather than Blackdown, which did not include a 64-bit plugin. I asked whether or not I could install over Sun's JRE, or how to uninstall, but was completely ignored.

**- Improved reliability**
So far, I've had crash issues (With no error message) with at least four separate apps - Firefox, xine-ui, gFTP, and Dark Horizons' Lore. In Firefox, its been pretty random, but may be connected with sound; in xine-ui, it occurs whenever attempting to open some .mov files with the open dialog (drag-and-drop with the same ones works fine); with gFTP, it occurs after large file transfers are finished and you attempt to start another one; and in Lore, it occured just before going in-game. The fact that the apps are so varied make me suspect something else is afoot, possibly with the sound subsystem (I'm not sure if gFTP does sound in any way).

**- Better ethernet support**
Very recently, I tried to set up (k)ubuntu on a dual-P3 system, with an Abit VP6, and a Linksys LNE-100tx ethernet card. When I wasn't able to get it working in any way no matter what I tried, I tried a D-Link DFE-530tx. Both seemed to be detected correctly, but were incapable of sending/receiving anything to other computers (despite both being tried on two different routers and cables.) If there is a solution, no one I've spoken to on IRC has managed to come up with one; and my thread in the Kubuntu forum has gone unanswered.

**- ubuntu-desktop**
I'm not sure what this is, exactly, but apparently I should keep it around so it's easy to upgrade when Breezy comes out. But it bugs me that I can't uninstall certain software (ie Evolution) because it would also remove this package.

**- Better Windows emulation/games**
I realize this is something that is mostly beyond the control of the Linux community at large, but this would definitely be something nice. Game development companies take note - if Linux binaries are available, I consider that a very positive aspect about that game, especially if those binaries are 64-bit.

**- Better support**
I'm not sure how this could be improved exactly - people simply be more helpful? Regardless, there've been times that I've asked for help on the forums, or in the chat, and gotten no response. Not even for overly complex things; it's usually been simple things like how to install a program or get a piece of software working. Eventually I may stumble upon the solution with a similar search, or after an hour of looking. But it's been the biggest contributor to pushing me off Linux. If not for my stubbornness, and my dislike of Windows XP's "piracy protection" system, I would've given up out of frustration long ago.

**_Good stuff**_
**The GIMP**
Kudos on having it installed by default. It's a big step up from paint ;).

**PDF Reader**
Amazing - a lightweight PDF reader already installed, it starts fast, and I don't feel like I'm churning through molasses while using it.

**Firefox**
It's a great browser - 'nuff said.

**OpenOffice**
Useful and free and installed with Ubuntu, it's a nice contrast to having to spend hundreds of dollars on Microsoft Office.

**apt-get/Synaptic**
It's very easy to find & manage software with these two; I always try to get .deb packages, if I can, when I have to get something not already in the repositories.

---

### Post by sethmahoney on 2005-07-03
Lots of people take issue with the lack of pre-installed support for various file formats, DVDs, and java, but the problem with having them installed by default in Ubuntu is that one of the Ubuntu goals is to have only totally free software installed by default, and all these formats are patent-encumbered.  Additionally, apparently DVD support in Linux is quasi-legal - in other words, depending in part on where in the world you are, it may actually prove to be illegal to install DVD support.  There's not a lot that can be done about that.  I totally agree, though, that Beep Media Player should be installed by default instead of Totem and that ubuntu-desktop should be removed (though you can safely remove it - if you do so and worry about upgrading to Breezy, just reinstall it before you do).  As far as Windows games support, have you checked out Cedega?  I've had no problems with any of the games I've installed with it, and with some games (ie Jedi Academy), the game has run faster and with fewer crashes than under Windows.  As far as support goes, I don't know what to say - I've had no problems with Ubuntu support - generally people on this forum have been extremely helpful and friendly, and it sure as hell beats Windows technical support.

---

### Post by WMCoolmon on 2005-07-04
Yeah, I've actually made a few forays into emulating various games with Cedega. Nothing's worked enough to actually be playable so far, though; that may be because of how I installed it - I used the instructions on the unofficial Transgaming wiki rather than simply installing it to a chroot'd 32-bit environment.

---

### Post by Big Venus on 2005-07-04
> **WMCoolmon]
**- Lack of out-of-the-box DVD support**
Something relatively new, but still very nice to be able to pop in a DVD and be able to play it without any additional software. DVD players are pretty commonplace.
[/QUOTE]
You can't legally include with a distro release libdvdcss which allows you to run most commerical dvds (the dvds you buy from a store)
[QUOTE=WMCoolmon]
**- Lack of out-of-the-box MP3 support**
I'm actually not 100% sure on this one, but it seems to me that I had to install *something* to get MP3s to play. I believe it was beep-media-player said:**
> 
Go and get gstreamer-plugins-mp3, because you can't include it with a distro release because of possible legal ramifications...
[QUOTE=WMCoolmon]
**- WAV support**
Same deal as MP3s and DVDs, I believe I had to install something special to get this working.
It has it in Rhythmbox by default or at least mine does...
> **WMCoolmon]
**- Totem is basically worthless**
Why it's the default media player, I don't know. But it seems like it can't play anything it tries to open, unless you switch to totem-xine. Then, Totem becomes useful.[/quote]
Totem is good you just need to know how to use it the same principles that apply to totem-xine also apply to totem, except playing DVDs works better with totem-xine.
[QUOTE=WMCoolmon]
**- No easy way to get Java installed**
Again, this may be a legality issue, but it would be enormously handy to be able to be able to just throw in "apt-get install java-mozilla" and have the plugin and everything installed and ready to go (much like Flash). This is something of a pain on AMD64 said:**
> 
I agree with you here, however not a lot of people are using 64bit stuff. You know most people like Intel and the new dual core and the old 32bit platforms, so I don't understand what you expected. Although I expected that too at one point...
[QUOTE=WMCoolmon]
**- Improved reliability**
So far, I've had crash issues (With no error message) with at least four separate apps - Firefox, xine-ui, gFTP, and Dark Horizons' Lore. In Firefox, its been pretty random, but may be connected with sound; in xine-ui, it occurs whenever attempting to open some .mov files with the open dialog (drag-and-drop with the same ones works fine); with gFTP, it occurs after large file transfers are finished and you attempt to start another one; and in Lore, it occured just before going in-game. The fact that the apps are so varied make me suspect something else is afoot, possibly with the sound subsystem (I'm not sure if gFTP does sound in any way).
I agree, but for what it is worth ubuntu is better than fedora core 3 in reliability and in my opinion way better than fedora core 4... So come on, was windows absolutely stable right out of the box, when windows 3.1 was released. I don't think so...
> **WMCoolmon]
**- Better ethernet support**
Very recently, I tried to set up (k)ubuntu on a dual-P3 system, with an Abit VP6, and a Linksys LNE-100tx ethernet card. When I wasn't able to get it working in any way no matter what I tried, I tried a D-Link DFE-530tx. Both seemed to be detected correctly, but were incapable of sending/receiving anything to other computers (despite both being tried on two different routers and cables.) If there is a solution, no one I've spoken to on IRC has managed to come up with one said:**
> 
If you go to distrowatch.com and see that ubuntu is the most used and kubuntu is down at like the tenth place or so. You should ask your questions here, but even then like a friend of mine said, its a hit or miss question because not alot of people use a particular model or type of linux router or switch, so it may or may not apply... For me I am planning on getting a Netgear long range router...
[QUOTE=WMCoolmon]
**- ubuntu-desktop**
I'm not sure what this is, exactly, but apparently I should keep it around so it's easy to upgrade when Breezy comes out. But it bugs me that I can't uninstall certain software (ie Evolution) because it would also remove this package.
read the description in synaptic on ubuntu-desktop. It is not required but is useful to reinstall most of the programs that lets say you decided you didn't need any more and just deleted them...

I'll leave the games to you because I don't do any linux gaming other than spider solitaire in Patience (kpat is the actual package)
[QUOTE=WMCoolmon]
**- Better support**
I'm not sure how this could be improved exactly - people simply be more helpful? Regardless, there've been times that I've asked for help on the forums, or in the chat, and gotten no response. Not even for overly complex things; it's usually been simple things like how to install a program or get a piece of software working. Eventually I may stumble upon the solution with a similar search, or after an hour of looking. But it's been the biggest contributor to pushing me off Linux. If not for my stubbornness, and my dislike of Windows XP's "piracy protection" system, I would've given up out of frustration long ago.[/quote]
This is linux and it is open source, so like some one in their news article said about linux desktop not being ready for the desktop market, you would and will need to know some programming skills to use linux properly...

For me I dislike firefox, Open Office doesn't print with the one that came with and is in the ubuntu repos, and GIMP is not all that great compared to Adobe Photoshop...

---

### Post by Optimal Aurora on 2005-07-04
Darn Venus,
You hit the points right on the head, wow...

I agree at the end I have problems with some hardware, graphics and OpenOffice.org and so on...

---

### Post by Big Venus on 2005-07-04
Just stating it as it is and not differing in my opinion...

---

### Post by dmn_clown on 2005-07-05
[QUOTE=Big Venus]You can't legally include with a distro release libdvdcss which allows you to run most commerical dvds (the dvds you buy from a store)[/QUOTE]

The original court ruling that brought about this says nothing about [distribution](http://www.eff.org/IP/Video/MPAA_DVD_cases/20011128_ny_appeal_decision.html) , only that DeCSS could not be posted or linked to (within the United States, anyway).  I may not be a lawyer, but to tell me that I cannot view a DVD that I purchased on a player of my choosing is a major violation of my Fair Use rights.  

DeCSS is not included in Linux distributions for the simple fact that none of the companies or groups releasing Linux has the money to fight the inevitable lawsuit from the MPAA which would spend countless $billions just to keep its monopoly on DVD players alive.  See, it's not that it is illegal, its that we can not afford to prove that it is legal in a court of law.

---

### Post by tread on 2005-07-05
Actually, you can have mp3, dvd support legally, but then it has to be paid for. Thats what  Linspire does.

---

### Post by Jet2k5 on 2005-07-05
Good stuff.  To tell you the truth I'm getting a 64-bit machine by the end of this month.  I'm scared as a turd going down the toilet about installing Ubuntu.  I've heard nothing but bad bad bad things about 64-bit version.  All this flash, firefox, cedega chroot 32 crap is beyong my knowledge of Linux.  I've been using Linux for a little over a year now and Ubuntu has been able to keep my system stable.  Until I update and then more problems come up and up and so on.  

Anyhow when the time comes to build my 64-bit PC and I have it all done, ubuntu is the first distro going on there.  I'm going to be playing a crap load of games, so I hope that I don't run into problems with cedega/firefox and any other stuff.  Fedora core and mdk and gentoo seem to have one of the best 64-bit distros as I read in tons of forums.

So off that topic now, I think that ubuntu is doing good as it is right now.  Just wish they would focus a tad bit more on 64-bit.  If I was a geek for computer programming I would help, but I have a hard time picking up computer languages.  Very hard time.  So besides donations I don't really know how else I can help to make 64-bit stronger.  Ubuntu is good, but it should be good on both sides 32 and 64 bit side :)

---

### Post by DancingSun on 2005-07-05
[QUOTE=Jet2k5]Ubuntu is good, but it should be good on both sides 32 and 64 bit side :)[/QUOTE]

Agreed.  AMD64 application support is really lacking.  libesd-alsa0 isn't even available for us 64-bit users.  So I can't even "correctly setup my sound system" according to the guides out there.

Also, this makes me think I shouldn't need to "correctly setup my sound system".  It should already be correctly setup, no?  Stuff like multiple sound should really be preconfigured to work out-of-the-box.

---

### Post by Big Venus on 2005-07-05
[QUOTE=dmn_clown]DeCSS is not included in Linux distributions for the simple fact that none of the companies or groups releasing Linux has the money to fight the inevitable lawsuit from the MPAA which would spend countless $billions just to keep its monopoly on DVD players alive.  See, it's not that it is illegal, its that we can not afford to prove that it is legal in a court of law.[/QUOTE]
You said it, "can't fight off  lawsuits" in my book that means that they can't include it legally...

---

### Post by Big Venus on 2005-07-05
[QUOTE=Jet2k5]Good stuff.  To tell you the truth I'm getting a 64-bit machine by the end of this month.  I'm scared as a turd going down the toilet about installing Ubuntu.  I've heard nothing but bad bad bad things about 64-bit version.  All this flash, firefox, cedega chroot 32 crap is beyong my knowledge of Linux.  I've been using Linux for a little over a year now and Ubuntu has been able to keep my system stable.  Until I update and then more problems come up and up and so on.  [/quote]
Well that is how I had some of my experiences with Fedora core 3 and 4, updating from the FC3 that I had been using for 4 months to FC4 cause my system to at first not want to install anything, the next try it did install but the LVM had a problem, the next try I didn't have sound, then I started playing around with setting and got found out that ALSA had critical problems on it from my system and had to use OSS as a Default Sink that you will see is used by ubuntu by default, type gstreamer-properties in the terminal to open it...

Ubuntu however, I didn't encounter a problem, except when trying to use dchroot and openoffice.org, they won't print or just plan screwed up my system...
[QUOTE=Jet2k5]
So off that topic now, I think that ubuntu is doing good as it is right now.  Just wish they would focus a tad bit more on 64-bit.  If I was a geek for computer programming I would help, but I have a hard time picking up computer languages.  Very hard time.  So besides donations I don't really know how else I can help to make 64-bit stronger.  Ubuntu is good, but it should be good on both sides 32 and 64 bit side :)[/QUOTE]
You could help by helping with finding bugs in the software and posting them here on the AMD64 forum. You know like saying, "I jsut got this from the universe repo. and it installed and I go to open it and it cause the system to freeze."

The only way to improve AMD64 over the i386 or up to its level is to have more people help in the debugging and programming and bug reporting of software. As well as documenting, like howto's and the amd64.ubuntuguide.org

---

### Post by dmn_clown on 2005-07-06
[QUOTE=Big Venus]You said it, "can't fight off  lawsuits" in my book that means that they can't include it legally...[/QUOTE]

Sad isn't it?  That we accept the trouncing of our rights as consumers so easily...

---

### Post by poptones on 2005-07-06
Rights to...?

If I write a book, is it your "right" to read it?

I do think the balance in copyright is off - if I write a book but let no one read it, I have no need for copyright and should not be allowed it. But if I write a book and say no one is allowed to copy it but anyone may come to my home and read my book, should I still be allowed copyright? I have shared it with society, and that addresses the primary matter of "to promote progress of the useful arts." 

Though my terms may seem unreasonable, does my unreasonable nature give you the "right" to come to my house with a copier? Ultimately, won't my being unreasonable just cause fewer people to read my book? Doesn't that just limit my own voice - and my ability to impact upon society and culture?

Doesn't that really mean that I am the only one who suffers my foolishness?

This problem has many sides. "Just take what we want" doesn't help any of them.

---

### Post by ACK!! on 2005-07-06
Interesting thread.

For almost every bit of the Java, codecs, and other multimedia complaints the easy answer is here:

Automate script for new users:

[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

It rocks btw.  mozilla mplayer-plugin is I believe the only missing piece in this puzzle.

But then again this is the AMD 64 section so I am not sure if that thing even works for AMD 64.  

Yes, btw not having this stuff by default does suck.  But then again, it is not a Ubuntu thing but common to most freely available distros.  

Most have already mentioned this.

**Reliability:**

Let us be honest people I agree and have no idea why Firefox seems to enjoy crashing as much as does but it has been a fairly random and annoying issue.

Evolution when using exchange-server seems to want to die off a lot too.  But then again a lot of people like the fact that Ubuntu is stays on the leading edge of most software builds and does not insist on staying one version back or something like some distros used to by default.

Yes, I think the original poster is right to include reliability but at least in Linux the app crashes and dies.  I find this to be much preferable to the Windows behavior of hanging and locking up my box and then refusing to die etc ....etc... and I have seen this behavior in a few windows apps.

**Ethernet support**

I have never experienced this problem so it is hard to comment but hw support in general will always be something of an issue --- why?  Hw vendors not releasing their specs turns out to be the major reason.  

**Ubuntu Desktop**

I do find it odd that this package is tied in so tightly with so many other apps but then again just remove the thing along with whatever other package it is tied to that you wanted to remove in the first place.  

I have done this before and was always a bit worried that I was missing something because of it.  

**Better Windows emulation/games**

Most people will NOT agree with me on this one and that is ok.  However, I believe that we need to look at the operating system a bit differently than Unix folks are used to looking at it.

    * Base layer--kernel, file system, and command line innards.

    * Compatibility layer--all the Wine tools needed to run MS-Office or other programs right out of the box.

    * Interface layer--an integrated desktop environment where everything, including all system tools, have the same look and feel. 

Yes, I feel if you are running on Intel hw and have the opportunity to include it you need a compatibility layer like Mac OS did going to OS X not because most people will use it.  They will not.  But instead it gives people the warm and fuzzies and there will be a few games that will be able to run in Wine that people lust over in the Linux-only world.

**Better Support**

I am truly puzzled at this one.  You have people here in the forums that have been generous enough in their time to post large How-Tos in the Customization section and then people who make the big Ubuntu FAQ and others who make new user automate scripts and then finally other people who design an entire menu editing app or the Ubuntu Bootup Manager or .....  

Perhaps you are specifically referring to help inside of the AMD 64 forum.  Well, until more people take the 64 bit dive (considering the number of systems shipping with those chips this will be rising like mad) and more people start working around the problem then this will be an issue.  I am sure the PPC people get this same frustration from time to time.

---

### Post by WMCoolmon on 2005-07-08
> I agree, but for what it is worth ubuntu is better than fedora core 3 in reliability and in my opinion way better than fedora core 4... So come on, was windows absolutely stable right out of the box, when windows 3.1 was released. I don't think so...

Mmm, no, but so far I've found Windows 2000 to be much more reliable. Seeing as how it's five years old, that should be an indication that something's up. I hear all these things about how Linux is so much more reliable, and people hate having to reboot Windows all the time. But frustratingly enough, this seems to be confined to server applications; there are all sorts of programs that have great potential, but are either not finished or unreliable/finicky. It's really a problem with OSS in general; almost nobody wants to bugfix and build a solid app when they could be adding all the features they wanted.

Six decent apps, IMHO, aren't as good as two quality ones if you have to use at least three to play the media files you use, rather than just one. If a program has a good design/interface, is stable, and does everything it should do, I can live with not being able to tweak it to be 5% more customized to what I want. And I think the majority of desktop users really just want something that works.

Basically, if I have a word processor, but it has a 50% chance of crashing when I save or copy text, it's worthless to me, no matter how customizable it is, no matter how many scripting languages it supports, because it simply doesn't do the job adequately enough to be useful.

---

### Post by dmn_clown on 2005-07-09
[QUOTE=poptones]This problem has many sides. "Just take what we want" doesn't help any of them.[/QUOTE]

I can't speak for other users of DeCSS, however, I am not "taking what I want."  I am merely viewing my legally acquired DVD's on a player of my choosing and making back up copies of same, well within my Fair Use rights, and yours as well.  Nothing I am doing here or suggesting is breaking Copyright.

What has been taken are your and my rights to view this media format on a player of our choosing.  We as a community should be upset and far more vocal about this than we are.  Corporate America has no right to dictate to anyone on this planet how or where we may use any of its products.

For instance if you were to publish your specified novel and release it to the public, you have no right to sue me when I use it as toilet paper or to roll a cigarette, that is well within my rights as an individual.

Would a boycott of the DVD format help?  Probably not, as the majority of people that view DVD's do so away from their computer.  With the advent of media center PC's this might change, especially as one can build a decent media center PC that runs Linux with existing components for less than the cost of a new Microsoft Windows Media Center PC from the local computer shop.  DeCSS would have a very valid use in this application.

---

### Post by poptones on 2005-07-09
*I can't speak for other users of DeCSS, however, I am not "taking what I want." I am merely viewing my legally acquired DVD's on a player of my choosing and making back up copies of same, well within my Fair Use rights, and yours as well. Nothing I am doing here or suggesting is breaking Copyright.*

Not true. That the DVD you bought "fits" in your computer is only an accident - and I, you, or anyone acting as publisher have every right to say "I don't want my publication distributed with that capability."

Is it your "right" to run OS X on your PC? It's just a bunch of bits purchased on a DVD, and every PC nowdays has a DVD player and is able to read it. So why not? 

It's your right to use my book as toilet paper only so long as it is not MY book you are using as toilet paper. And, as I pointed out the first time, we are indeed talking about "my book" - because I won't let you have a copy. So is it then your "right" to make massive quotations from my book that I have not shared? Am I denied copyright protection because I choose to keep my book unpublished? If so, then where is my ability to enforce my desires my book goes unpublished? If you could sneak into my house and obtain it, or quote it verbaitim from memory, then I am without recourse if I am denied copyright, as this is as much the job of copyright as anything else. 

Anais Nin wrote volumes through her lifetime. From the age of nine she kept a journal. As she grew older and was published she expressed a desire that certain works not be published until everyone involved with those writings had died. Imagine if someone had obtained *Henry & June* in the 1960s and published it against her wishes - because, as an unpublished work it had no copyright protection. Do you think she would have continued to produce? You don't think that sort of thing would send a chill throughout the entire creative community?

As a creator of a work I have every right to say where I think it should be published and even how, within just means, it should be used. 

People used to tell me I sound like Lessig. That was before I even knew who Lessig was. Now I know and I am a regular reader of his. I like much of what I hear - but I do not agree with all of it. Because while he and his crew speak about "the old world" of publishers being unable to adapt to this change, they ignore the fact that *this new media* brings with it all sorts of new preceedents and new tools. 

In other words: that book you bought might make fine toilet paper, and there are no practical means of enforcing any desire I might have to forbid you from wiping your butt with it...  but lets see you wipe your arse with a handfull of bits and ether.

---

### Post by Terracotta on 2005-07-10
The problem with dvd and mp3 for example is that to read it, you need either a hardware or a software algorithm to read it. So if you buy a dvd-player (I mean a player, not a drive) you pay for the algorithm through the purchase of the dvd-player, which you do not pay for when you buy a dvd-rom drive, hence a dvd-rom drive is cheaper than a dvd-player, the same goes for mp3, it's not a free codec. The rights for the algorithm can be purchased softwarematic from people who have bought a license for the codec, Although I think there should be a better arrangement in this case, for example at this moment, the manufacturor of the dvd-player has to pay an amount of money to the institution which holds the rights of the codec, and the people who distribute dvd's have to pay an amount of money as well to the rights-holding institution. The same goes for mp3 (whith every usb-key-mp3-player you buy an amount of money goes to whatever institution/company that holds the rights).
So you practically pay two times to have the rights to play a dvd, or an mp3, which is "in my point of view" a bit completely wrong. I think that the people who say are right when they say: I buy a legal dvd so I should be able to read it anyway, maybe they should charge more money per bought dvd/cd/musicfile/whatever, and they should stop charging the people who create means to read the damned stuff. In that way, the people who invent algorithms/standards/codecs/whatever get their money and you can read/see/hear what you pay for. and the problem is solved, so it comes down to this: charge the people who create files in your format more, and stop charging people who create means to read the files.

I appologise for my oh so s***y english skills, and I hope it's clear enough to explain my thoughts (although I'm not so sure about that  ](*,)  ).

---

### Post by dmn_clown on 2005-07-10
[QUOTE=poptones]Not true. That the DVD you bought "fits" in your computer is only an accident - and I, you, or anyone acting as publisher have every right to say "I don't want my publication distributed with that capability."[/QUOTE]

Actually the first DVD-ROM drive was built so that people could watch DVD's on their computer, the decryption mechanism was built within the media players, a process that works fine so long as one uses proprietary software.  We however are not, and to the best of my knowledge, the MPAA refused to write a media player for Linux, hence we are where we are now.  Correct this history if I am wrong.

> Is it your "right" to run OS X on your PC? It's just a bunch of bits purchased on a DVD, and every PC nowdays has a DVD player and is able to read it. So why not? 

This is comparing apples to oranges as Mac OS X has not been ported to run on the Intel compatible chips (Well, not available to license yet...), however, with this logic, one might ask if you have the right to run Ubuntu or any form of GNU/Linux on your PC,  the odds are that it was purchased with Microsoft Windows pre-installed.

> It's your right to use my book as toilet paper only so long as it is not MY book you are using as toilet paper. And, as I pointed out the first time, we are indeed talking about "my book" - because I won't let you have a copy. So is it then your "right" to make massive quotations from my book that I have not shared? Am I denied copyright protection because I choose to keep my book unpublished? If so, then where is my ability to enforce my desires my book goes unpublished? If you could sneak into my house and obtain it, or quote it verbaitim from memory, then I am without recourse if I am denied copyright, as this is as much the job of copyright as anything else.

No, copyright was designed to stop people profiting off the work of others.  Viewing a DVD within a GPL'ed media player privately and making back-up copies to protect my investment from harm is not going to net me a profit in any way shape or form.

> As a creator of a work I have every right to say where I think it should be published and even how, within just means, it should be used. 

Coming from someone with a creative bent, I must disagree with you here.  Once a work of art is published and available to the general public, you have no control or right to tell anyone how said piece of art may be used, interpreted, or even mis-used.

This is the nature of art, interpretation and use is up to the viewer / reader / user.

> People used to tell me I sound like Lessig. That was before I even knew who Lessig was. Now I know and I am a regular reader of his. I like much of what I hear - but I do not agree with all of it. Because while he and his crew speak about "the old world" of publishers being unable to adapt to this change, they ignore the fact that *this new media* brings with it all sorts of new preceedents and new tools. 

In other words: that book you bought might make fine toilet paper, and there are no practical means of enforcing any desire I might have to forbid you from wiping your butt with it...  but lets see you wipe your arse with a handfull of bits and ether.

It should be possible to grind up a lot of Microsoft Windows installation CD's and convert them into a very fine and nice toilet paper, though the process would probably be cost prohibitive. ;-)

---

### Post by dmn_clown on 2005-07-10
[QUOTE=Terracotta]I appologise for my oh so s***y english skills, and I hope it's clear enough to explain my thoughts (although I'm not so sure about that  ](*,)  ).[/QUOTE]

Your English is far better and clear than some native speakers with a good point being raised, they could also provide the community with a closed source media player that includes the decryption mechanism allowing DVD and mp3 playback.

---

### Post by poptones on 2005-07-10
> Actually the first DVD-ROM drive was built so that people could watch DVD's on their computer, the decryption mechanism was built within the media players...

"The first DVD ROM drive?" Perhaps you could give a link. While I'm sure "the first drive" very likely was not ATAPI compliant I have no idea if what you say is true and I doubt you do as well. Those drives came about when CPUs were relatively limited (450MHz was a very high end machine) and so they often came with proprietary *adapter cards* containing decode circuitry for playback... but I do not recall ever seeing a DVD drive like this.

At any rate that would also be moot. Because those old system didn't even put the data on the backplane - decss had not yet come about and even the media player software that shipped with the dvd drives pretty much just sent commands to the DVD drive itself. The decoder cards had two ports on them, and input and output for VGA, which was then daisy chained with the monitor. IOW they were basically just home DVD players without the box.

*and to the best of my knowledge, the MPAA refused to write a media player for Linux, hence we are where we are now.  Correct this history if I am wrong.*

There are allegedly linux compatible dvd players but I have never used it so I can't say how well it works. It really doesn't matter now though does it? Because anyone who wants to watch DVDs in linux just installs decss and mplayer or xine and that's it.

> This is comparing apples to oranges as Mac OS X has not been ported to run on the Intel compatible chips (Well, not available to license yet...), however, with this logic, one might ask if you have the right to run Ubuntu or any form of GNU/Linux on your PC,  the odds are that it was purchased with Microsoft Windows pre-installed.

Irrelevant. The windows license likely dictates that you cannot use that copy of windows on another machine, but I have never seen a manufacturer of *Windows* hardware (Cisco and the ilk are another matter) send a EULA covering the hardware purchase. It's your right to **not use** a license you have purchased, but it's not your right to change the terms of the agreement.

> No, copyright was designed to stop people profiting off the work of others.  Viewing a DVD within a GPL'ed media player privately and making back-up copies to protect my investment from harm is not going to net me a profit in any way shape or form.

Wrong. And precedent exists. Copyright was designed to protect the ability of the *owner of the copyright* to distribute the work as he or she sees fit. That means if I want to sell CDs but do not want my record played on radio, you do not co-opt it saying "if you didn't want it on the radio you never should have recorded it." If I want to write a book of erotica and post it on a website for free you cannot take that work and bind it in a book and sell it or even *give it away*. It has nothing to do with profit and everything to do with distribution. 

"Fair use rights" exist **only as a practical matter**. This is established precedent - look it up yourself. I have had this discussion MANY times with artists, law students, lawyers, librarians... fair use in our country has existed only by means of certain protections in the bill of rights. Protections like the imaginary "right to privacy" (there is no such right, but it can be argued this is the spirit) or the protection from unduie search and seizure. In other words I cannot come into your home and rifle through your record and tape collection looking for bootlegs without a very good reason.

But: if I can employ a non invasive means of enforcing my right to protect my work from copy **in any form** you do not have the "right" to stop me. In the most extreme example: if I want to write a book and yet do not want anyone to ever print it I have that right. So how can you say you have the "right" to make a copy of a book which I have agreed to publish at a fair price? You do not, and precedent agrees with this in spirit and in fact.

Ergo, you do not have the "right" to duplicate any recorded media which I can protect. This is a new world with new tools and new capabilities, we MUST have new laws to protect everyone's rights. You may object to the fact intellectual creations are treated the same as physical property, but we live in a world where there is no denying their value. If you want to be "fair" about it then stop **taking** from bad actors and *helping* them to propogate their creative output throughout culture. It's you, the people who "take what we want" because you imagine it your right who **strengthen** the stranglehold of these bad actors upon that very culture! 

If you do not use windows because you disdain their licenses and proprietary lockdowns how can you then embrace Sony and Universal and Disney?

> Coming from someone with a creative bent, I must disagree with you here.  Once a work of art is published and available to the general public, you have no control or right to tell anyone how said piece of art may be used, interpreted, or even mis-used.

Wrong. If I write a book you cannot make a movie of it without my consent. If I publish a song you cannot use it in your movie without my consent. If I write a song you cannot even reprint the lyrics in your book without my consent. And if I publish a DVD using encryption of my choosing you *do not* have the right to republish it on CD or film. The fact you are able to copy it, in the privacy of your home, is only a "right" of yours so long as you can obtain the tools to do so. But it's not your right to **profit** from providing tools that will allow others to do this or even your right to obtain those tools. 

The internet makes us all publishers. There are thousands of ways publishers can profit from their activity. But there is nothing stopping you from publishing works **anonymously** - in this regard every one of us has equal right to expression **and** distribution of that expression in a way that has never before existed. No one can stop you or me from, say, re-editing *The Phantom Menace* and posting it in public places as an anonymous work of art. But if you put your name in the corner of that canvas then you **are** profiting. You are recieving prestige for your work; you may get offers of work; you may get offers of intimate encounters with "fans" - you **are** profiting in many of the ways those children of the old school - the Mick Jaggers and the Steven Spielbergs - "profit." It's not just about money... *it never was.* Just ask Axel Rose.

Being a publisher brings with it lots of those old responsibilities publishers had to deal with. And one of them is to respect the copyrights held by others. What you do in your home **can** affect Millions of others; that's the very **point** of all this.

---

### Post by dmn_clown on 2005-07-10
[QUOTE=poptones]"The first DVD ROM drive?" Perhaps you could give a link. While I'm sure "the first drive" very likely was not ATAPI compliant I have no idea if what you say is true and I doubt you do as well. Those drives came about when CPUs were relatively limited (450MHz was a very high end machine) and so they often came with proprietary *adapter cards* containing decode circuitry for playback... but I do not recall ever seeing a DVD drive like this.[/QUOTE]

I do not recall ever seeing an OEM DVD-ROM drive with a decoder card, I am not saying that they did not exist, only that I have never seen one, CSS has been a part of the proprietary software media players since the adoption of CSS, just like a normal video codec..  A time line can be found [here](http://www.bydeluxe.com/resources/technology/dvdintro/).



> There are allegedly linux compatible dvd players but I have never used it so I can't say how well it works. It really doesn't matter now though does it? Because anyone who wants to watch DVDs in linux just installs decss and mplayer or xine and that's it. 

I have never heard of a proprietary media player that will work within Linux.  Which leads me to my original point, why is it wrong for us to install DeCSS and the media player of our choice?  Why is that "illegal" as the MPAA's website dictates?

>  The windows license likely dictates that you cannot use that copy of windows on another machine, but I have never seen a manufacturer of *Windows* hardware (Cisco and the ilk are another matter) send a EULA covering the hardware purchase. It's your right to **not use** a license you have purchased, but it's not your right to change the terms of the agreement.

This depends on the version of Windows that is installed, Corporate versions allows the installation on more than one computer, Professional allows for home networking, Home limits one to simpy surfing the web with only 5 digital devices attached to the computer and it is unclear as to what constitutes a digital device, but this is irrelevant to the discussion.

> Wrong. And precedent exists. Copyright was designed to protect the ability of the *owner of the copyright* to distribute the work as he or she sees fit. That means if I want to sell CDs but do not want my record played on radio, you do not co-opt it saying "if you didn't want it on the radio you never should have recorded it." If I want to write a book of erotica and post it on a website for free you cannot take that work and bind it in a book and sell it or even *give it away*. It has nothing to do with profit and everything to do with distribution.

Please don't put words into my mouth, I said nothing about distribution.  End-use does not involve distribution.  For example, you record and release song X, I, using my new fangled software skills, can take song X remixing it with song Y and place samples from recording Z producing song A and listen to song A for my own personal enjoyment.  It is where I take song A and start distributing this to friends, family, and the world, that copyright is broken.


> But: if I can employ a non invasive means of enforcing my right to protect my work from copy **in any form** you do not have the "right" to stop me. In the most extreme example: if I want to write a book and yet do not want anyone to ever print it I have that right. So how can you say you have the "right" to make a copy of a book which I have agreed to publish at a fair price? You do not, and precedent agrees with this in spirit and in fact.

Ergo, you do not have the "right" to duplicate any recorded media which I can protect.

On the contrary, I do, as do you, and everyone else that reads this forum within the United States.  The DMCA did not limit the ability to make archival copies of digital media.  [The theory is that since copying a work may be a fair use under appropriate circumstances, the DMCA does not prohibit the act of circumventing a technological counter measure that prevents copying. ](http://www.benedict.com/Digital/Internet/DMCA.aspx)

> This is a new world with new tools and new capabilities, we MUST have new laws to protect everyone's rights. You may object to the fact intellectual creations are treated the same as physical property, but we live in a world where there is no denying their value.

Agreed, we do need the current laws amended to protect everyone's rights with an interest on the consumer's and artists rights, away from the major record labels and movie studios.

> If you do not use windows because you disdain their licenses and proprietary lockdowns how can you then embrace Sony and Universal and Disney?

Sony, Universal, and Disney do not receive any money from me, I do not buy **their** products.  However there are several filmmakers that I am more than willing to support no matter which movie studio is the distributor, I support quality art and am not "taking" from the bad actors as you are insinuating.

> And if I publish a DVD using encryption of my choosing you *do not* have the right to republish it on CD or film. The fact you are able to copy it, in the privacy of your home, is only a "right" of yours so long as you can obtain the tools to do so. But it's not your right to **profit** from providing tools that will allow others to do this or even your right to obtain those tools.

Again, no one in this thread has mentioned republishing or distributing existing works, we only wish to view and listen to our legally acquired digital media in the media players of our choice well within our rights as consumers, and again there is nothing in the original DeCSS ruling that limits the distribution of DeCSS, if there is an existing statute that prevents said distribution please provide a link.

---

### Post by poptones on 2005-07-10
> I do not recall ever seeing an OEM DVD-ROM drive with a decoder card

If I still had my old NEC I would photograph it for you. 

When they first came out this was standard. ATAPI was not yet really established  and most adapter cards would have three or more IDE connectors that you would choose from depending on the brand of drive you had. And because the studios were leary of licensing software that put the unencrypted data on the backplane you generally had to have one of these combos in order to enjoy encrypted DVDs 

Keep in mind: not all use CSS. There is at least one major studio that does not use CSS on any of its titles. 

> CSS has been a part of the proprietary software media players since the adoption of CSS, just like a normal video codec..

CSS is **not** DeCSS. CSS is "content scrambling system" and that was indeed part of the plan from the beginning. But decss was NOT given to the world by hollywood and it was, in fact, some time before DVDs were "cracked." And it was... guess what? A css key given to one of those software players that led to it being cracked. Do not expect Hollywood to have not learned a lesson from this.

> Which leads me to my original point, why is it wrong for us to install DeCSS and the media player of our choice?

How can you not get this? Encrypted dvds use css. CSS is a licensed technology. It is both patented and the DVD (and the keys employed by css) copyrighted. When you use decss you infringe upon a patent not held by you. A patent holder is under no obligation to license it to everyone or to allow free use of the patented technology.. This is why no licensed players (may) exist and most certainly why decss is illegal in the US - and why the very act of watching a DVD using decss is illegal. You are infringing upon a patent.

> Please don't put words into my mouth, I said nothing about distribution.  End-use does not involve distribution.

I just pointed out to you why it very much does. When you copy a work you are in posession of an unlicensed copy. You have infringed upon copyright. No, you do not have this "right" any more than you have the "right" to patent infringement. This is the point of law. You may *feel* you have some moral right, but if you want to arguem moral rights then this discussion will quickly get even more mired down - this is why the US does not grant "moral rights" to creators of works.

> For example, you record and release song X, I, using my new fangled software skills, can take song X remixing it with song Y and place samples from recording Z producing song A and listen to song A for my own personal enjoyment.  It is where I take song A and start distributing this to friends, family, and the world, that copyright is broken.

If the copyright owner does not wish it, then it is infringement from the first illicit copy. In case law this has been referred to as "de minimus copying." The trivial name does not imply "right" it only points out that this is *the most minimal act of copyright infringement*. It is still, however, very much an act of infringement and you do not have a "right" to it. Your "right" to this sort of use has been afforded only by means of practicality. When it becomes a *practical* matter to  enforce, however, without violating your *inalienable rights*, then you will lose that "right" of de minimus infringement.

> The DMCA did not limit the ability to make archival copies of digital media.  The theory is that since copying a work may be a fair use under appropriate circumstances, the DMCA does not prohibit the act of circumventing a technological counter measure that prevents copying.

It does forbid the distribution of any tools that allow such infringement. Where did you get your copy of decss? If you downloaded it then you have violated the law; you have helped distribute it. You are also very likely guilty of violating import laws regarding illegal materials. 

But the biggest mistake you are making in all this is that nonsense about "fair use." I know where you're coming from, and you can argue until you are blue in the face that you should have some right because you always had it - but the reality is you never had much of those "rights" you imagine. 

From the Betamax case:

*Thus, although every commercial use of copyrighted material is presumptively an unfair exploitation of the monopoly privilege that belongs to the owner of the copyright, **noncommercial uses are a different matter. A challenge to a noncommercial use of a copyrighted work requires proof either that the particular use is harmful, or that if it should become widespread, it would adversely affect the potential market for the copyrighted work.***

Fact: if copying DVDs by home users became widespread it would, inarguably, damage the sales of home DVDs. Hollywood knows this and the low end is very, very competetive - you can buy DVDs that have lapsed into the public domain for as little as a buck. And you can buy DVD bundles of films now that may offer a dozen fairly contemporary movies for as little as 3 or 4 bucks each. Thus, the market exists and - most importantly - the copyright owners are actively addressing that market. The fact you don't **want** to pay twenty bucks for a more recent film doesn't mean they do not have the right to demand it. No one is forcing you to buy their films; if twenty bucks is too much then wait six months and it'll be half that.

*Notwithstanding the provisions of sections 106 and 106A, the fair use of a copyrighted work, including such use by reproduction in copies or phonorecords or by any other means specified by that section, **for purposes such as criticism, comment, news reporting, teaching (including multiple copies for classroom use), scholarship, or research, is not an infringement of copyright***

It does not say "personal enjoyment" anywhere in there. In fact, facilitating "personal enjoyment" is the primary objective of creating the content in the first place. Are you a library? If you are nto a library there is no precedent defending any "right" to reproduce entire works against the wishes of the copyright owner.

*Sony, Universal, and Disney do not receive any money from me, I do not buy **their** products.*

Do you pay for TV? Go to the mvoies? Subscribe to magazines? Do you watch ABC? If so then they do, in fact, get money from you. It may not be a direct transfer of funds, but you are, in fact, subsidizing their grasp on popular culture. This is inarguable; if no one watched ABC then ABC would go bankrupt. People watch ABC because they produce shows that are popular. If the shows became unpopular no one would watch - it's the circle of life. It's cultural biology. If you "consume" their product, you feed their cultural impact. and that cultural impact is the root of their economic existence... and, thus, their influence on government.

---

### Post by NoTiG on 2005-07-16
> I just pointed out to you why it very much does. When you copy a work you are in posession of an unlicensed copy. You have infringed upon copyright. No, you do not have this "right" any more than you have the "right" to patent infringement. This is the point of law. You may feel you have some moral right, but if you want to arguem moral rights then this discussion will quickly get even more mired down - this is why the US does not grant "moral rights" to creators of works. 

You want to get anal? consider this... whenever you watch a DVD... the information (0's and 1's) are read off the CD... and stored in memory where it is then used to become represented on the screen. So technically... whenever you watch a dvd no matter what decoder you are using, you are "copying it" because the bits exist in two places at once. That is why there is this thing called reason that the human mind is capable of using, which you seem to be forgetting.

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=dmn_clown] they could also provide the community with a closed source media player that includes the decryption mechanism allowing DVD and mp3 playback.[/QUOTE]

Thats what we like to call "Linspire" around here.

---

### Post by TravisNewman on 2005-07-17
linspire has DVD playing? I  had no clue

---

### Post by Stormy Eyes on 2005-07-17
[QUOTE=NoTiG]That is why there is this thing called reason that the human mind is capable of using, which you seem to be forgetting.[/QUOTE]

And let's not forget that a copy (albeit imperfect) exists in the mind of every person who ever viewed a given movie. Am I in violation of Mel Brooks' copyright because I can quote every line of *Spaceballs* from memory? Perhaps I am, from a strictly legalistic viewpoint. I, however, do not care. I will do as I please, so long as I do not do actual harm to others.

---

### Post by papangul on 2005-07-17
I am just wondering if Rox-filer could be provided as the desktop file manager instead of the stripped down version of nautilus.

---

### Post by dshadywun on 2005-07-18
[QUOTE=Big Venus]Just stating it as it is and not differing in my opinion...[/QUOTE]
 MAKE EASY MONEY ONLINE WITH PAYPAL!

PLEASE READ YOU WILL BE THANKING ME LATER   :)

Have you ever wanted to make some money online. I have not had much success up to this point. To be honest I am totally sceptical about any get-rich quick scheme I have ever heard about.

Well then I found this PayPal Money making guide. I read some more about it and saw people reporting that they had made a few thousands of dollars. Well of course I didn’t believe it. Would you.

Then I decided to try it. So I looked for a mailing list and sent 5 dollars to every person on that list then entered my name. It only cost me $25, which is cheap compared to what i made from it!!!

Now its time for the next stage,  posting my message on numerous message boards. The reason for posting messages is so u can get more people to send!

And the more people who send the more money you make and the more money they will eventually be making.

Hopefully there are enough people out there who will see this message and take the chance, so that this will work and make alot of people alot of money.

If you past this up now and relize later that this really works, you will regret not trying it sooner? If you start now just imagine all the money you will make in a few months it will definitly be in the thousands.

Ive been doing this for 3 months and already have $5,540. And theres still money coming in!! Im just trying to spread the word so that everyone can enjoy this as much as i am.

So here’s the 5 step plan.

1. Copy this letter and save it in your computer and/or on a floppy disk. I suggest you print this for future refrence. :)

2. Send 5 dollars to every PayPal account on the list below (If you don’t have PayPal sign up for one at this link: [https://www.paypal.com](https://www.paypal.com))

1) [email]krstic12@hotmail.com[/email]
2) [email]gatman973@yahoo.com[/email]
3) [email]nets45@walla.com[/email]
4) [email]tedd745@yahoo.com[/email]
5) [email]dshadywun1@yahoo.com[/email]

IMPORTANT: when u send the money please include the comments "Please add me on your mailing list" this makes this whole process legal.

Question:  Why send people money?         Answer: IF you dont send money to the e-mail addreses your chances of making money off this are slim. The reason for that is, When you send money and ask them to "Please add me on your mailing list" they will put your e-mail on there ads. Therefore your e-mail  will spread dramaticly over thousands of forums for people to see so will make you alot of $$$$$ MONEY $$$$$!!!!

 The next step is important so pay attention!

3. After sending the money to the paypal accounts, What you need to do is....

Remove the e-mail from the number 1 spot off the list. ( THIS PERSON IS NOW OFF THE LIST BUT IS NO DOUBT COUNTING ALL HIS MONEY!!!)
Then put the e-mail from the number 2 spot in the number one spot.
Then take the e-mail from the number 3 spot in the number 2 spot.
Then take the e-mail from the number 4 spot to the number 3 spot.
Then take the e-mail from the number 5 spot to the number 4 spot.

Ok now there is the last empty spot put your e-mail in this spot. So when your done it should look like the list below.

1) [email]gatman973@yahoo.com[/email]
2) [email]nets45@walla.com[/email]
3) [email]tedd745@yahoo.com[/email]
4) [email]dshadywun1@yahoo.com[/email]
5) YOUR E-MAIL

4. You could use this letter to send to your friends and post on forums. Try to post this on all the sites you possibly can because people who see this. The more money you will make.

5. Sit back and just watch your paypay account get filled with money. Dont spend it all at once!!!!!                     

Thank you

---

### Post by benplaut on 2005-07-19
^^ok, this is the last time, before i'm considered to be spamming  :roll: 

STOP!

---

### Post by poptones on 2005-07-19
[QUOTE=NoTiG]You want to get anal? consider this... whenever you watch a DVD... the information (0's and 1's) are read off the CD... and stored in memory where it is then used to become represented on the screen. So technically... whenever you watch a dvd no matter what decoder you are using, you are "copying it" because the bits exist in two places at once. That is why there is this thing called reason that the human mind is capable of using, which you seem to be forgetting.[/QUOTE]
 Gee, and no one ever thought of that before...

It's been addressed.. like a decade ago. A "copy in memory" would be called an *authorized* copy in that it is essentially required in order ot make use of the device. And when you use a DVD player you are also making use of css! It's *authorized* because the technology is licensed to someone who will make use of it in a way that is agreeable to the licensing bodies. When you watch a DVD the **entire** DVD is not copied in totality to the memory in the player. It is copied in "chunks" for the purpose of decoding the video and it is presented via an interface the licensing body has agreed upon.

Again: if their rules are unacceptable to you, you have many choices. Many of those choices will necessitate breaking the law. One can argue bad laws should be broken, but ripping a DVD to your home computer because you don't want to be bothered with the ads is not an act of civil disobedience, it's simply an act of piracy. Keeping yourself and your family and your friends addicted to the hollywood teat only helps those shark skin suits you're complaining about.

---

### Post by agger on 2005-07-19
[QUOTE=poptones]Gee, and no one ever thought of that before...

It's been addressed.. like a decade ago. A "copy in memory" would be called an *authorized* copy in that it is essentially required in order ot make use of the device.[/QUOTE]

A little off-topic: Some years back, a Danish content provider stated on their Web pages that "this content may only be read or studied online - it may not be downloaded or saved to disk in any form" - a rather comical proviso given that all browsers actually download everything to a disk cache, which meand it's impossible not to break it. Well, content providers have become more tech-savvy since then ...

[QUOTE=poptones]
Again: if their rules are unacceptable to you, you have many choices. Many of those choices will necessitate breaking the law. One can argue bad laws should be broken, but ripping a DVD to your home computer because you don't want to be bothered with the ads is not an act of civil disobedience, it's simply an act of piracy. Keeping yourself and your family and your friends addicted to the hollywood teat only helps those shark skin suits you're complaining about.[/QUOTE]

Anyway, this discussion mainly applies to the US: Here in Denmark, there is no patent or law that I know of that prevents me from watching a movie on a Linux box using DeCCSS.

In France, a court recently ruled that copy-protection DRM is illegal because it's an infringement of consumer's rights, a stance that I hope will become popular throughout the EU.

Fundamentally, I think society should exempt all de facto standards from patents: Meaning, that as soon as some technology becomes a standard (as TCP/IP and all RFC-defined protocols) or a de facto standard (such ad DVDs and CSS), all patents on these technologies should become null and void, with the possible payment of some sort of indemnification to the patent holder.

It stands to reason (anyway), which was the rationale behind the French court ruling, that the consumer must have a right to protect his/her investment by making a backup copy for personal use in case the original breaks.

It also stands to reason that the consumer *ought* to have the right to view a purchased DVD on the medium of his/her choosing.

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=agger]
Anyway, this discussion mainly applies to the US: 
[/QUOTE]

Yep. Unfortunatly, software must cater to the lowest common denominator. In the case of copyright laws that is the U.S.

(aka Ubuntu lacks a way to play dvds out of the box, even though its based outside of the U.S., because the developers (and Mark) don't want to worry about being arrested as they are leaving the plane the next time they come to the U.S. for a Linux conferance or something.)

---

### Post by poptones on 2005-07-19
> Anyway, this discussion mainly applies to the US: Here in Denmark, there is no patent or law that I know of that prevents me from watching a movie on a Linux box using DeCCSS.

Of course. But added to that is also the language and cultural barrier. Hollywood movies sell around the world as do danish movies and french movies. But in a relative manner one would expect an american movie in france to have a culturally larger influence than a french film in the US. There have been a few fairly popular french films in the US in recent years, but how often do Hollywood films make "blockbuster weekends" where ever and when ever they open? There are few countries where Hollywood films do not have a reasonably significant cultural impact. Therefore, this is not our problem in isolation. The US will twist arms and lobby and do all it can to keep the trade battle continuing. It's in everyone's interest to see Hollywood's legislative power reduced, and that battle begins at the wallet.

> It also stands to reason that the consumer *ought* to have the right to view a purchased DVD on the medium of his/her choosing.

This is fairly ridiculous. Should Sony be required by law to support VHS as well as Beta so I can be assured of playing my VHS rentals on their machines? The fact the media itself looks similar and physically fits another device is irrelevant. Look at the movies coming out now on PS3 discs - should the manufacturer of those discs be prohibited because they won't play on computers or DVD players? Should they be *obligated* to license players to their competition?

The solution is simple: if you do not like a publisher's behavior, don't give them your money. Paramount may have a "monopoly" on Star Trek, but no one is going to starve to death because you cannot watch Picard and crew on your desktop computer. This is not a "right for all mankind" it is simply diversion. If you resent the way a publisher is leading your culture, you stop supporting that publisher - it's no different if that publisher is Disney, or Larry Flynt.

---

### Post by tmartindub on 2005-12-02
I would definitely like to see a wizard type utility that loads drivers for Linux that come on disks and for new people don't require extensive Linux training to be able to do it.  Most drivers must be compiled and rarely do the directions given point you to how to do it.

Ubuntu has some good features, true, but it is lacking in the things that we all have become accustomed to.  Installations in general are a pain and I wonder why it cannot be much simpler and let the system do the work not have me tearing out my hair (well,what's left of it).

---

### Post by newbie2 on 2005-12-03
maybe more like PCLOS?

> [COLOR="Sienna"]Best linux Distro?

I am fairly new to Linux and dont claim to be a guru in any way. However, I do know what works and what doesn't atleast for me. I have Ubuntu and can not figure out why it is so popular. It (IMO) has poor hardware detection, various serious sound issues and is a configuration nightmare. I never could get it to successfully install my avertv card or play media from the internet and sound issues plagued my every step. On the Ubuntu forums the openly admit to the sound issues, couldn't figure out why my tv card didn't work and had lengthy processes for internet media, which after much effort failed to fix my problem. The Ubuntu forums, however, are filled with nice people willing to help. After reading the Sept 1st issue I tried opensuse 10.0 and it was beautifully laid out. Very professional, but again it was a little difficult to set up and when I asked for help at 2 seperate forums I did not recieve any. This brings me to Mepis and PCLOS. Mepis is great it has a huge repository, is very stable and is ready to use right after installation. Mepis, though feels outdated, it is still using kde 3.3.2 and you really cant upgrade to 3.4 without risking damaging the entire system. Also when you update via synaptic it asks questions that a new user doesn't know how to answer. PCLinuxos, installs easily and is ready to use right after installation. I did not have to do anything except insert disk, click install me and follow a few simple instructions. Pclos is fast,up to date, stable and exeptionally well laid out. Texstar must work around the clock to keep it very current. Being a recent windows convert and new enough to Linux that I am not comfortable digging and rewriting config files I would have to say that PCLOS is the absolute best distro for the new linux user. With PCLinuxos the user simply points, clicks and enjoys[/COLOR]
[http://www.tuxmagazine.com/node/1000151](http://www.tuxmagazine.com/node/1000151)

---

### Post by aysiu on 2005-12-03
[QUOTE=tmartindub]Most drivers must be compiled and rarely do the directions given point you to how to do it.[/QUOTE] Yeah, that's what I hate about installing Windows--that, and trying to find out which drivers I need and where to find them from reliable sources, especially if the manufacturer no longer has them available for download.

Luckily, I didn't have to bother with drivers for Ubuntu--everything was detected except my screen resolution. I just added a couple of lines to my /etc/X11/xorg.conf file, and everything was cool.

Not so lucky with my Windows installation... ah, those drivers!

I also sure wish Windows had an Automawindex or Easy Windows to install all my codecs and such. It was a pain trying to get VLC working with my DVDs in Windows.

---

### Post by prizrak on 2005-12-07
[QUOTE=poptones]Of course. But added to that is also the language and cultural barrier. Hollywood movies sell around the world as do danish movies and french movies. But in a relative manner one would expect an american movie in france to have a culturally larger influence than a french film in the US. There have been a few fairly popular french films in the US in recent years, but how often do Hollywood films make "blockbuster weekends" where ever and when ever they open? There are few countries where Hollywood films do not have a reasonably significant cultural impact. Therefore, this is not our problem in isolation. The US will twist arms and lobby and do all it can to keep the trade battle continuing. It's in everyone's interest to see Hollywood's legislative power reduced, and that battle begins at the wallet.



This is fairly ridiculous. Should Sony be required by law to support VHS as well as Beta so I can be assured of playing my VHS rentals on their machines? The fact the media itself looks similar and physically fits another device is irrelevant. Look at the movies coming out now on PS3 discs - should the manufacturer of those discs be prohibited because they won't play on computers or DVD players? Should they be *obligated* to license players to their competition?

The solution is simple: if you do not like a publisher's behavior, don't give them your money. Paramount may have a "monopoly" on Star Trek, but no one is going to starve to death because you cannot watch Picard and crew on your desktop computer. This is not a "right for all mankind" it is simply diversion. If you resent the way a publisher is leading your culture, you stop supporting that publisher - it's no different if that publisher is Disney, or Larry Flynt.[/QUOTE]

I'm sorry but here is the issue. The media in question is a DVD disk, my computer can read them (some computers can record them) every recent DVD that I have seen comes with a player embedded onto it and WILL install onto a Windows machine automagically (in fact you have to click the <Do Not Install> button to prevent it). If the DVD was legally purchased/rented did I not pay for the use of the said copyrighted material as well as the system it uses for replay? My right as a consumer is to use what I purchased/rented with accordance to the license. The DVD license that comes up in the beginning of any movie states that I am allowed to have a private viewing of it, it does not specify equipment. If I go to Radio Shack and build my own DVD player and write my own firmware for it should I not be allowed to use it? Also since the CSS is PATENTED (this is the keyword) it means that it can be reverse engineered including all the keys used and any and all information I can get out of it, such is the US patent law (and I have studied that as a part of class). This makes DeCSS quite legal to create and use since it is nothing but a reverse engineering. On the subject that DeCSS COULD POSSIBLY be used for illegal purposes does not make it illegal (VCR's and CD/DVD burners are legal and you can use those for illegal purposes), which means that it is legal for me to use as long as I do nothing more than watch DVDs on my Linux box. This would not be a huge issue if CSS was not a part of virtually every DVD that comes out and if MPAA didn't have the monopoly on movies in the US. However what is being done is an infringement on my rights as the consumer, effectively the MPAA tells me that I am not allowed to watch the movie that I bought/rented quite legally. This in effect is akin to ALL music CDs only working on the Sony and Audiovox CD players and not on Pioneers, Panasonic and Sanyo. 

The issue that you have so successfully ignored throughout this entire debate is that no one here is saying that we ought to be able to just make copies of any CD/DVD. What we have been saying is that we cannot watch our LEGALLY BOUGHT/RENTED DVDs on our Linux boxes, there are times when I am not able to use the DVD player that is connected to my TV (a trip) but have my Linux laptop with me that has a DVD drive providing such an ability, moreover the computer came with a DVD player installed on Windows, which means that I already paid for the use of a CSS decoder. 

Also why am I as a consumer being constrained as to what media I can use? I payed for the DVD if I prefer to store it as an .avi file then why not? As long as I don't watch the two at the same time I am well within the copyright. Why is it not allowed? It is no different than taking a book on tape and transcribing it for my own personal use when I cannot listen to it, for instance I'm on a train and need to hear the next stop. 

However even barring the copying issue, which is a very controversial one and will not be settled until there are new laws. My above statement still stands I payed for the right to watch the DVD as many times as I wish on any equipment capable of playing it, it is well within my rights as a consumer to install the DeCSS library that will play it on my Linux machine, I do not infringe on the copyright of the artist he/she/they still get paid for their work, I am not claiming any kind of ownership, I am not changing the content of the DVD I am simply doing what I payed for, which is viewing it. If the movie industry creates a proprietary closed source DVD player software that it will ship on DVDs same way they do with the Windows one at no extra cost to me, I will be more than happy to use it. I will also be happy to use any service that will sell movies in a divx format in the same way as iTunes sells music in the mp3 format. This is the biggest issue with MPAA, they are refusing to provide it's consumers with an ability to do what they have paid for and they take to court anyone who comes up with a way to excercize the rights that they are entitled to. You made a point earlier that Hollywood will not be making a Linux player because it's easy to extract information from it, however just because something is being developed for Linux doesn't mean it has to be open source, there is plenty of proprietary software availabe for Linux just of the top of my head Opera, Kerio Mail Server. Closed source on ANY platform makes getting into the innerworkings of software impossible without some specialized tools such as a hex viewer or a debugger, it also makes it illegal to do so (if they are copyrighted not patented). There is no reason why we can't have a DVD player on our Linux machine other than MPAA stopping us, this hardly seems fair.

---

