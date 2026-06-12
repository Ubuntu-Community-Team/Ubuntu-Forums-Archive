---
title: "Why my sister will not be using Ubuntu"
date: 2009-09-22
forum: The Cafe
---

### Post by Duncan J Murray on 2009-09-22
My sister is a relatively normal person who uses computers mainly to access the internet and type up documents.  Recently, Win XP on her laptop died, and she was quite happy for me to install ubuntu onto her laptop.  It had been working fine until she started a recent job which required research on the internet, and the creation of a document formatted in a very specific way for the client.

This is where the problem started.  The file was a microsoft word file, quite specifically formatted with titles, sections, etc...  On loading this file in Ooo Word, my sister discovered that the formatting was suddenly chaos.  Not hugely, but enough to cause several problems, including the moving of tables and sections onto the wrong pages due to slight differences in the line spacing.

On my laptop I attempted to install Wine and my own copy of MSWord, which loaded up the file without any problems, except that still, the fomatting was not correct.

So far, I have not found any other way for my sister to carry on her work in Ubuntu (unless anyone has any ideas).

I am sure that this will always be the case, but you have to wonder how many more people would switch if Microsoft and Adobe were to release their software onto the platform (ok, hugely unlikely).  It may be that despite how good linux and ubuntu is, it will never really take off unless it can get this very common software onto the platform.

Any ideas, thoughts?

Duncan.

---

### Post by bailout on 2009-09-22
Unfortunately OOo isn't fully compatable with MS office files. You just have o use office in these cases. Interested to hear that office under wine worked but wouldn't display the file properly. I have to use office for work and currently boot into windows but had thought of trying office under wine instead.

---

### Post by Moop on 2009-09-22
I think you should direct your complaint to microsoft. Shouldn't you be able to open a word doc with any office program and have it be right?

Have you tried installing windows and MS Office in a virtual machine like vbox? I don't know but it seems like it should work. Vbox is easy to install in Ubuntu. 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by JillSwift on 2009-09-22
> **Duncan J Murray said:**
>  On my laptop I attempted to install Wine and my own copy of MSWord, which loaded up the file without any problems, except that still, the fomatting was not correct.Sounds like it may be the fonts are missing.

---

### Post by MC707 on 2009-09-22
> **Duncan J Murray said:**
> My sister is a relatively normal person 

So more advanced linux people are 'abnormal'? :P

---

### Post by Xbehave on 2009-09-22
[LIST=1]
[*]IN XP+real office: Safe documents in an old word format,
[*]anywhere: open in OO,
[*]anywhere: save in OO format
[*]then: go troll elsewhere
[/LIST]

---

### Post by Aearenda on 2009-09-22
> **JillSwift said:**
> Sounds like it may be the fonts are missing.

In my experience missing fonts is indeed the most likely cause of mismatch in MS-Office+Wine, and it might also be the cause in OpenOffice - but OOo has other layout differences too. Printer metrics can muck up MS-Office from one system to the next. Sorting this kind of thing out is why PDF was invented.

To address the OP's question:
> I am sure that this will always be the case, but you have to wonder how many more people would switch if Microsoft and Adobe were to release their software onto the platform (ok, hugely unlikely). It may be that despite how good linux and ubuntu is, it will never really take off unless it can get this very common software onto the platform.
Linux isn't Windows. The world is changing, as more apps are becoming available online, and people are realising they don't need to pay the Microsoft tax. I don't think we need specific commercial apps on Linux (unlikely, as you say) in order to achieve wide uptake; but we do need to make sure that the experience of the average user is a good one, perhaps in this case by having OOo indicate that it is substituting for missing fonts.

---

### Post by praveesh on 2009-09-22
> **Duncan J Murray said:**
> My sister is a relatively normal person who uses computers mainly to access the internet and type up documents.  Recently, Win XP on her laptop died, and she was quite happy for me to install ubuntu onto her laptop.  It had been working fine until she started a recent job which required research on the internet, and the creation of a document formatted in a very specific way for the client.

This is where the problem started.  The file was a microsoft word file, quite specifically formatted with titles, sections, etc...  On loading this file in Ooo Word, my sister discovered that the formatting was suddenly chaos.  Not hugely, but enough to cause several problems, including the moving of tables and sections onto the wrong pages due to slight differences in the line spacing.

On my laptop I attempted to install Wine and my own copy of MSWord, which loaded up the file without any problems, except that still, the fomatting was not correct.

So far, I have not found any other way for my sister to carry on her work in Ubuntu (unless anyone has any ideas).

I am sure that this will always be the case, but you have to wonder how many more people would switch if Microsoft and Adobe were to release their software onto the platform (ok, hugely unlikely).  It may be that despite how good linux and ubuntu is, it will never really take off unless it can get this very common software onto the platform.

Any ideas, thoughts?

Duncan.

the latest development version of wine 1.0.29 runs ms office 2007 really fine. It's in their website. You can subscribe to their own repository to get the latest developing version of wine.

---

### Post by hoppipolla on 2009-09-22
I was gonna chuck something in but I think everything's already been said! lol :)

---

### Post by Bill Blevins on 2009-09-22
I've never been a fan of Wine. My suggestion would be to do what I did and install VirtualBox by Sun Microsystems. You may then install a copy of Windows in a virtual box within Linux. This would give you the option to install whatever Windows programs you require without the headache of setting up a dual boot system.

---

### Post by praveesh on 2009-09-22
If the office didn't work find under wine, you can do two tweaks.
1. Change the windows version that the program sees from xp to 98. It can be done at applications -> Wine-> wine control panel. 
2. Install the playonlinux . It's a front end of wine. It does a lot of tweakings to make a software work under wine.

---

### Post by MC707 on 2009-09-22
> **Bill Blevins said:**
> I've never been a fan of Wine. My suggestion would be to do what I did and install VirtualBox by Sun Microsystems. You may then install a copy of Windows in a virtual box within Linux. This would give you the option to install whatever Windows programs you require without the headache of setting up a dual boot system.

That is actually a good idea. If you are working in your linux installation and want to do something in windows, just pop open virtual box and way to go. No need to restart, go to windows, restart, back to linux :-x

---

### Post by Frak on 2009-09-22
Why not just reinstall Windows on her laptop. It was working for her just fine before, I assume. I hate to rain on the Ubuntu crowd, but even though XP broke, I don't think putting something that doesn't immediately fulfill the needs of her job is a good substitute.

---

### Post by magmon on 2009-09-22
I feel your pain. Im probly going to have to set up a dual boot for itunes =/.

---

### Post by Chronon on 2009-09-22
Why dual boot just for iTunes when it works fine in Vbox?

OP: I don't know what the expectations of the client are but if the goal is to produce a document formatted in a certain way, it seems it would be better to spec that and then allow your sister to typeset the document accordingly.  It seems rather poor form to make a non-portable document format (as office suite documents tend to be) the basis of something like this.

---

### Post by Dimitriid on 2009-09-22
There are 2 solutions that I implemented for having to use office documents from my job at my (formely) linux only home computer:

1) VirtualBox running windows xp. Did the trick well enough

2) Standing up to my boss a bit so he would assign either more people or more realistic deadlines so I don't have to work at home on my own time anyway. :D

---

### Post by magmon on 2009-09-22
> **Chronon said:**
> Why dual boot just for iTunes when it works fine in Vbox?

It would take quite alot of file moving and time, where as I have a hard drive which already has windows on it. Add ubuntu, and I'm done =P.

---

### Post by pwnst*r on 2009-09-23
> **Frak said:**
> Why not just reinstall Windows on her laptop. It was working for her just fine before, I assume. I hate to rain on the Ubuntu crowd, but even though XP broke, I don't think putting something that doesn't immediately fulfill the needs of her job is a good substitute.

this^^

---

### Post by Dimitriid on 2009-09-23
I never had a windows system "break" on me. Ubuntu has more friendliness, more stability and a lot less notoriety, however nothing can substitude good computer practices.

In my experiences the vast majority of people left without a usable windows install its because they click on every single email they receive or install every single piece of software they can find without thought of possible consequences.

---

### Post by keiichidono on 2009-09-23
Have you tried using Koffice?

---

### Post by Viva on 2009-09-23
The openoffice format is awesome, but unfortunately, not many offices/colleges have openoffice installed. You can't really blame openoffice for not properly opening an encrypted proprietary format like MS Office's. Have you tried staroffice? It is a commercial version of openoffice and supposedly has better compatibility.

---

### Post by GrfyGrumpyBear on 2009-09-23
what?:)

---

### Post by t0p on 2009-09-23
> **Dimitriid said:**
> I never had a windows system "break" on me. Ubuntu has more friendliness, more stability and a lot less notoriety, however nothing can substitude good computer practices.

In my experiences the vast majority of people left without a usable windows install its because they click on every single email they receive or install every single piece of software they can find without thought of possible consequences.

And one of Linux's greatest strengths is that it lets its users act as dumb as they like - clicking on attachments, downloading porn - without hosing the OS.  Linux may not be bullet-proof.  But it might as well be, compared to that other system.

---

### Post by gordintoronto on 2009-09-23
Page setup aften messes up formatting in Word or OO.

---

### Post by Lemmy's Wart on 2009-09-23
Microsoft Office file format compatibility is always going to be a moving target, that is the way Microsoft designed it from the start. How could they sell you Office 2007 if your ever faithful copy of Office 2000 had complete compatibility with all it's successors. I have simple Word documents made with Office 2000 that don't always display correctly in Office 2003 let alone 2007.

Open Office is a reasonable and capable product with many flaws, but to expect 100% compatibility with Microsoft Office when Microsoft themselves don't always guarantee this between versions is a  little too much to expect. Microsoft may define the standard, but it is one that is always fluid and in motion. And this is Open Office's fault?

I'm with Frak and others, you should have just reinstalled Windows XP from the start. Sometimes the best tool for the job is simply that.

> **Frak said:**
> Why not just reinstall Windows on her laptop. It was working for her just fine before, I assume. **I hate to rain on the Ubuntu crowd**, but even though XP broke, I don't think putting something that doesn't immediately fulfill the needs of her job is a good substitute.

Are you sure about that Frak? You sound so sincere. ;-)

---

### Post by earthpigg on 2009-09-23
i did not read the whole thread.

however,

if your sister's employer expects her to work on work-related stuff at home, then it is the ***employer's responsibility*** to provide her with a computer and ***the full software stack required*** to do so.

---

### Post by keiichidono on 2009-09-23
Hmm, who put those tags there.

---

### Post by praveesh on 2009-09-23
Which version of wine are you using ? The latest stable version (1.0.1)? Or latest development version (1.0.29)? The latest development version supports a lot more apps . I feels it sufficiently stable . You can try it

---

### Post by 3rdalbum on 2009-09-23
> **Xbehave said:**
> IN XP+real office: Safe documents in an old word format

You mean "in XP + Microsoft Office". Your instructions don't make sense if you try to perform them in a REAL office.

---

### Post by 3rdalbum on 2009-09-23
> **CalvinB said:**
> Have you tried using Koffice?

Last time I checked, the Koffice developers were saying "Microsoft Office compatibility isn't a priority".

---

### Post by Duncan J Murray on 2009-09-23
Thanks for all the replies.

Can I just start with a slight clarification, as I seem to have got the back up of a few people - sorry about that.

I think ubuntu is terrific, and I'm not apportioning blame when I say that, as much as I would like my sister to be able to use and enjoy ubuntu, she won't be.

Of course it isn't openoffice's fault when they try to maintain compatibility with a closed format.  Nor is it really Microsoft's fault for not devoting any effort into making their file formats open.  Ok, maybe they put effort into keeping it closed, but again, they're a business, and philanthropy just isn't the way they work.  I'm not blaming anyone.

Win XP did actually 'break'.  It's not my laptop, so I don't know what happened to it, but it died.  It was acting poorly beforehand.  I have about 6 years experience with Win XP, and I found that it needed a lot of maintenence to keep it running well.  Ideally it needed reinstalling every 6 months to keep it running smoothly.  I think this is something to do with the way it installs and deinstalls programs.

I did install one of the latest versions of WINE (it says 1.1.27 do correct me if I'm wrong), and I also followed a guide which supposedly maximised compatibility.  In all fairness it does a great job of running MS Office, but I have compared the document between Win 7 and Ubuntu+Wine, and there are subtle differences (as you say, largely down to fonts) which makes collaboration on the document difficult (if you are adding 'new lines' to tidy up a page, your collaborator will be removing them on their screen).  Arrows are missing, pages don't quite fit on a page etc...

Yes, one can argue that using a heavily formatted Word file for a report is a stupid idea, and I would probably agree.  That isn't, however, going to change.  Nor is the fact that my sister will continue to use 'new lines' and 'spaces' over 'page breaks' and 'tabs' - but then, most people I know do this too.

I need to look into the box for running WinXP.  That sounds like an idea.  But I think the argument is lost for my sister, sadly - she needs to get something done, and it looks like Win XP is what she needs to do it.

My dad, on the other hand, has stopped using his Win XP box because it has slowed to an unuseable crawl, and is only too happy to give Ubuntu a try.  I will do that and see how it goes (though slightly worried, as he lives in France, and if anything goes wrong, it's going to be my fault, and I can't easily cross the channel to help).

Anyway, thanks for the replies.  Microsoft retains another customer, but loses three (me, my partner and maybe my dad...)


All best,

Duncan.

P.S.  I just booted up Win 7 to compare the files - it's amazing how just a few months of ubuntu makes you cringe using Win 7.  Feels so fussy and outdated!  My RC version is already asking me to activate the software, and repeatedly creating pop-ups to make it like hell using it.  Well, that won't be a problem for me!

---

### Post by MC707 on 2009-09-23
> **magmon said:**
> I feel your pain. Im probly going to have to set up a dual boot for itunes =/.

I'm glad I don't use Itunes, even though I have an ipod!

---

### Post by Dullstar on 2009-09-23
> **Dimitriid said:**
> I never had a windows system "break" on me. Ubuntu has more friendliness, more stability and a lot less notoriety, however nothing can substitude good computer practices.

In my experiences the vast majority of people left without a usable windows install its because they click on every single email they receive or install every single piece of software they can find without thought of possible consequences.

Actually, I got a Windows system that came crappy out of the box once.

EDIT:  I should clarify that at the time the computer wasn't connected to the Internet.

---

### Post by burntresistor on 2009-09-23
Did you try Crossover I heard about it on Wine HQ. There's suppose to be a free trial cause its a pay program.  [http://www.codeweavers.com/products/cxlinux/]("http://www.codeweavers.com/products/cxlinux/")

---

### Post by Frak on 2009-09-23
> **burntresistor said:**
> Did you try Crossover I heard about it on Wine HQ. There's suppose to be a free trial cause its a pay program.  [http://www.codeweavers.com/products/cxlinux/]("http://www.codeweavers.com/products/cxlinux/")
Seriously, if I have to pay $70 for Crossover, I'll just use Windows.

---

### Post by pwnst*r on 2009-09-23
> **earthpigg said:**
> i did not read the whole thread.

however,

if your sister's employer expects her to work on work-related stuff at home, then it is the ***employer's responsibility*** to provide her with a computer and ***the full software stack required*** to do so.

this is true for our corporation.

---

### Post by Bachstelze on 2009-09-23
> **Moop said:**
> I think you should direct your complaint to microsoft. Shouldn't you be able to open a word doc with any office program and have it be right?

Of course not. Word files are meant to be opened in Word. If you're using another application, well, sucks to be you. That's how it works in the other world. :p

---

### Post by nmccrina on 2009-09-23
Seriously, anyone who for the most part likes using Linux but needs 1 or 2 programs that require Windows should look at virtualbox. It is not an emulator, it is an actual windows installation running within ubuntu. It can even access the host's usb/CDROM/network stuff. I didn't look to hard into it at first either, but I finally got around to installing it yesterday and it is incredible. No rebooting or anything needed to get at windows from ubuntu.

---

### Post by Chronon on 2009-09-23
> **nmccrina said:**
> Seriously, anyone who for the most part likes using Linux but needs 1 or 2 programs that require Windows should look at virtualbox. It is not an emulator, it is an actual windows installation running within ubuntu. It can even access the host's usb/CDROM/network stuff. I didn't look to hard into it at first either, but I finally got around to installing it yesterday and it is incredible. No rebooting or anything needed to get at windows from ubuntu.

While it is perhaps strictly true that Virtualbox is not simply an emulator, it does make heavy use of hardware emulation in order to provide a functional virtual machine for you to run various operating systems on.  

An emulator instantiates a model of hardware in software.  You run real software designed for specific hardware on an emulator.

---

### Post by pwnst*r on 2009-09-23
> **nmccrina said:**
> Seriously, anyone who for the most part likes using Linux but needs 1 or 2 programs that require Windows should look at virtualbox. It is not an emulator, it is an actual windows installation running within ubuntu. It can even access the host's usb/CDROM/network stuff. I didn't look to hard into it at first either, but I finally got around to installing it yesterday and it is incredible. No rebooting or anything needed to get at windows from ubuntu.

sucks for games

---

### Post by MasterNetra on 2009-09-23
> **Duncan J Murray said:**
> Thanks for all the replies.

Can I just start with a slight clarification, as I seem to have got the back up of a few people - sorry about that.

I think ubuntu is terrific, and I'm not apportioning blame when I say that, as much as I would like my sister to be able to use and enjoy ubuntu, she won't be.

Of course it isn't openoffice's fault when they try to maintain compatibility with a closed format.  Nor is it really Microsoft's fault for not devoting any effort into making their file formats open.  Ok, maybe they put effort into keeping it closed, but again, they're a business, and philanthropy just isn't the way they work.  I'm not blaming anyone.

Win XP did actually 'break'.  It's not my laptop, so I don't know what happened to it, but it died.  It was acting poorly beforehand.  I have about 6 years experience with Win XP, and I found that it needed a lot of maintenence to keep it running well.  Ideally it needed reinstalling every 6 months to keep it running smoothly.  I think this is something to do with the way it installs and deinstalls programs.

I did install one of the latest versions of WINE (it says 1.1.27 do correct me if I'm wrong), and I also followed a guide which supposedly maximised compatibility.  In all fairness it does a great job of running MS Office, but I have compared the document between Win 7 and Ubuntu+Wine, and there are subtle differences (as you say, largely down to fonts) which makes collaboration on the document difficult (if you are adding 'new lines' to tidy up a page, your collaborator will be removing them on their screen).  Arrows are missing, pages don't quite fit on a page etc...

Yes, one can argue that using a heavily formatted Word file for a report is a stupid idea, and I would probably agree.  That isn't, however, going to change.  Nor is the fact that my sister will continue to use 'new lines' and 'spaces' over 'page breaks' and 'tabs' - but then, most people I know do this too.

I need to look into the box for running WinXP.  That sounds like an idea.  But I think the argument is lost for my sister, sadly - she needs to get something done, and it looks like Win XP is what she needs to do it.

My dad, on the other hand, has stopped using his Win XP box because it has slowed to an unuseable crawl, and is only too happy to give Ubuntu a try.  I will do that and see how it goes (though slightly worried, as he lives in France, and if anything goes wrong, it's going to be my fault, and I can't easily cross the channel to help).

Anyway, thanks for the replies.  Microsoft retains another customer, but loses three (me, my partner and maybe my dad...)


All best,

Duncan.

P.S.  I just booted up Win 7 to compare the files - it's amazing how just a few months of ubuntu makes you cringe using Win 7.  Feels so fussy and outdated!  My RC version is already asking me to activate the software, and repeatedly creating pop-ups to make it like hell using it.  Well, that won't be a problem for me!

In all fairness though M$ warns you a head of time that after a certain date those pop-ups will start occurring. It will also start shutting down every 2 hours...I forget which month that starts, goes on for two months I believe before dying completely.

> **nmccrina said:**
> Seriously, anyone who for the most part likes using Linux but needs 1 or 2 programs that require Windows should look at virtualbox. It is not an emulator, it is an actual windows installation running within ubuntu. It can even access the host's usb/CDROM/network stuff. I didn't look to hard into it at first either, but I finally got around to installing it yesterday and it is incredible. No rebooting or anything needed to get at windows from ubuntu.

If I had another GB of ram I would. I use Adobe CS3 for my college classes, just no real good WYSIWYG alternatives for Dreamweaver, nor any good Flash Pro alternatives. :/ Putting them through wine results in worse glitching then normal windows install. :/ I also I'm a fan of Oblivion which for me doesn't work for me under wine...probably due lack of OpenGL 2 support for Intel cards.

---

### Post by ChrT on 2009-09-23
To be a true Free Software user, you must not only use Free software alone, but also use it only in unison with Free/Open source codecs, file formats, etc. The solution to the OP's sister's problem is obviously to switch all her office stuff to OpenDocument (or the OOo implementation of it) and abandon all her education/work/friends that demand MS office files. If enough people do that, our society will eventually abandon proprietary file formats along with proprietary software, and humanity as a whole will advance.

---

### Post by MasterNetra on 2009-09-23
> **ChrT said:**
> To be a true Free Software user, you must not only use Free software alone, but also use it only in unison with Free/Open source codecs, file formats, etc. The solution to the OP's sister's problem is obviously to switch all her office stuff to OpenDocument (or the OOo implementation of it) and abandon all her education/work/friends that demand MS office files. If enough people do that, our society will eventually abandon proprietary file formats along with proprietary software, and humanity as a whole will advance.

Not happening anytime soon.

---

### Post by MC707 on 2009-09-23
> **pwnst*r said:**
> sucks for games

Not necessarily. I recall a video in youtube that showed a desktop computer with ubuntu, compiz with desktop cube, while running virtualbox and a **game** playing in it! I'll dig some in youtube and post a link to the video, plain amazing. And remember you don't need an nvidia 290 gt or whatever it is called in order to do this.

EDIT: [_Here the dude has compiz_]("http://www.youtube.com/watch?v=XiZyigv_aRc"), linux and virtualbox. Plus a little gamin' inside the virtualbox

---

### Post by #11u-max on 2009-09-23
> **ChrT said:**
> To be a true Free Software user, you must not only use Free software alone, but also use it only in unison with Free/Open source codecs, file formats, etc. The solution to the OP's sister's problem is obviously to switch all her office stuff to OpenDocument (or the OOo implementation of it) and abandon all her education/work/friends that demand MS office files. If enough people do that, our society will eventually abandon proprietary file formats along with proprietary software, and humanity as a whole will advance.
i smell a zealot... :) :popcorn:

---

### Post by etnlIcarus on 2009-09-23
> **#11u-max said:**
> i smell a zealot... :) :popcorn:

No, just a troll (read some of his other posts).


Anyway, I recently encountered this issue with my sister's PC, only the document she was sent by someone was an Open Office format and she was using MS Word. Solution: I installed Open Office. :P


Seriously, though, it would be *super* if all parties involved could just get together, decide upon a default, open format and have that be the end of it. Sadly, I think the only chance of this happening will be if MS' corporate partners get sick of all the dicking around their employees have to do, and put pressure on MS to do more than simply include an odf importer *that doesn't bloody work*.

---

### Post by sloggerkhan on 2009-09-23
Font differences are not an ubuntu problem, or a wine problem.

Even on windows MS documents will get messed up if you use a font that's not on the computer you open a document on. 

The solution should be to get the fonts you're missing or not use fonts that can't be shared intra-organization.

Fonts cause lots of problems and that's why many organizations have fancy dancy schemes for organizing and standardizing on them.

---

### Post by Chronon on 2009-09-23
@sloggerkhan: too true.  If you want a portable document then you either need to render images of the pages or embed the fonts in each document.  I have seen many Powerpoint presentations peppered with the empty box character or other arcane glyph substitutions due to font substitution.

@etnlIcarus: Yes, it would be nice.  Unfortunately, Microsoft's track record in this regard should not give anyone much hope of this.  Microsoft doesn't seem to have much respect for standards.  Java, anyone?  Non-standard HTML extensions for IE?

---

### Post by moe_syzlak on 2009-09-23
SUSE Linux Enterprise Edition has their own version of Open Office. It's called "OpenOffice.org 3.0 Novell Edition." Their version of Open Office has modifications that enhance or simplify interchange and exchange with MS Office and windows machines.[1] These changes and enhancements are not present in OpenSuse, so you have to be using SLED to benefit.

I quote:
> SUSE Linux Enterprise Desktop includes the Novell Edition of OpenOffice.org, a full office productivity suite on Linux that provides word processing, spreadsheet, presentation, drawing and database capabilities. OpenOffice.org Novell Edition works like Microsoft Office and is interoperable with Microsoft Office file formats. In addition, OpenOffice.org Novell Edition contains key enhancements not found in the upstream version of OpenOffice.org. This includes improved compatibility with Microsoft Excel, stronger Visual Basic macro support, and richer file import capabilities (e.g., ability to read Microsoft Works, WordPerfect, and scalable vector graphics files).

That is one of the many reasons why I think Linux is better when you pay for it. "Paid Linuxes" have more development power behind them.

Remember kids, pay for your Linux (by buying product support) and support you devlopers so they can have food to eat and feed their kids.

One last thing, I recommend you install SLED on her laptop. Novell has a thing where they allow you to use SLED for 6 months (I think) with support before they cut you off and ask you for support costs (updates, bug fixes, enhancements, etc.)

Sources:
1) [http://www.novell.com/products/desktop/features/productivity.html](http://www.novell.com/products/desktop/features/productivity.html)

---

### Post by HappinessNow on 2009-09-24
> **Duncan J Murray said:**
> My sister is a relatively normal person who uses computers mainly to access the internet and type up documents.  Recently, Win XP on her laptop died, and she was quite happy for me to install ubuntu onto her laptop.  It had been working fine until she started a recent job which required research on the internet, and the creation of a document formatted in a very specific way for the client.

This is where the problem started.  The file was a microsoft word file, quite specifically formatted with titles, sections, etc...  On loading this file in Ooo Word, my sister discovered that the formatting was suddenly chaos.  Not hugely, but enough to cause several problems, including the moving of tables and sections onto the wrong pages due to slight differences in the line spacing.

On my laptop I attempted to install Wine and my own copy of MSWord, which loaded up the file without any problems, except that still, the fomatting was not correct.

So far, I have not found any other way for my sister to carry on her work in Ubuntu (unless anyone has any ideas).

I am sure that this will always be the case, but you have to wonder how many more people would switch if Microsoft and Adobe were to release their software onto the platform (ok, hugely unlikely).  It may be that despite how good linux and ubuntu is, it will never really take off unless it can get this very common software onto the platform.

Any ideas, thoughts?

Duncan.Google Documents can create and read Word documents have your sister try it.

---

### Post by pwnst*r on 2009-09-24
> **MC707 said:**
> Not necessarily. I recall a video in youtube that showed a desktop computer with ubuntu, compiz with desktop cube, while running virtualbox and a **game** playing in it! I'll dig some in youtube and post a link to the video, plain amazing. And remember you don't need an nvidia 290 gt or whatever it is called in order to do this.

EDIT: [_Here the dude has compiz_]("http://www.youtube.com/watch?v=XiZyigv_aRc"), linux and virtualbox. Plus a little gamin' inside the virtualbox

that actually doesn't look too shabby, but the latest games will probably tax a decent system. i'll have to give it a go.

---

### Post by Exodist on 2009-09-24
> **Duncan J Murray said:**
> My sister is a relatively normal person who uses computers mainly to access the internet and type up documents.  Recently, Win XP on her laptop died, and she was quite happy for me to install ubuntu onto her laptop.  It had been working fine until she started a recent job which required research on the internet, and the creation of a document formatted in a very specific way for the client.

This is where the problem started.  The file was a microsoft word file, quite specifically formatted with titles, sections, etc...  On loading this file in Ooo Word, my sister discovered that the formatting was suddenly chaos.  Not hugely, but enough to cause several problems, including the moving of tables and sections onto the wrong pages due to slight differences in the line spacing.

On my laptop I attempted to install Wine and my own copy of MSWord, which loaded up the file without any problems, except that still, the fomatting was not correct.

So far, I have not found any other way for my sister to carry on her work in Ubuntu (unless anyone has any ideas).

I am sure that this will always be the case, but you have to wonder how many more people would switch if Microsoft and Adobe were to release their software onto the platform (ok, hugely unlikely).  It may be that despite how good linux and ubuntu is, it will never really take off unless it can get this very common software onto the platform.

Any ideas, thoughts?

Duncan.


Checked the Fonts yet?  Slight font hight can throw cells over to other pages and so forth.

---

### Post by Exodist on 2009-09-24
> **Chronon said:**
> Why dual boot just for iTunes when it works fine in Vbox?

OP: I don't know what the expectations of the client are but if the goal is to produce a document formatted in a certain way, it seems it would be better to spec that and then allow your sister to typeset the document accordingly.  It seems rather poor form to make a non-portable document format (as office suite documents tend to be) the basis of something like this.
Dont understand why she is using her "personal" laptop for work. The company should buy her a work laptop for "work".

---

### Post by Chronon on 2009-09-24
Now that you mention it, something does seem fishy about the arrangement.  For some reason I was imagining freelance work (e.g. as an independent contractor) but that doesn't seem to be the case upon a second reading.

---

### Post by Swagman on 2009-09-24
Actually that's becoming standard practice in the UK.

Companies are shifting the overheads ...anywhere bar themselves. Ultimately it ends up with **YOU** paying.

It's happening all over.

Did you get a proper restore disc with that new computer or did you have to burn it yourself ?

I'm a trucker and when we make a **Collection** we are now only given **ONE** P.O.D. So what's the receiving customer going to sign ? Yup, WE have to do 2 photocopies and staple them to original.

re: Ms office @ home. Almost certainly her company will not give a dead rats **** how she gets Ms Office as long as they are not implicated !!

I suspect Microsoft actually relies on this fact as the ***home*** piracy of Office strengthens its grip on the corporate world.

---

### Post by Tristam Green on 2009-09-24
> **etnlIcarus said:**
> No, just a troll (read some of his other posts).

Holy crap, you're right lol.


> Anyway, I recently encountered this issue with my sister's PC, only the document she was sent by someone was an Open Office format and she was using MS Word. Solution: I installed Open Office. :P


Seriously, though, it would be *super* if all parties involved could just get together, decide upon a default, open format and have that be the end of it. Sadly, I think the only chance of this happening will be if MS' corporate partners get sick of all the dicking around their employees have to do, and put pressure on MS to do more than simply include an odf importer *that doesn't bloody work*.

Hey, Microsoft office 2007 removed import from Lotus 1-2-3 capabilities in Excel, but OpenOffice still has that legacy support.  A boon for OO, but it still begs the question of *why?*

---

### Post by toupeiro on 2009-09-24
Dont know if this has been tried, but have her open the document in word on another computer, then save it as a different file type (maybe rtf?)  then send that over to Open Office.  Google Docs might be another option to try.

---

### Post by pwnst*r on 2009-09-24
> **Exodist said:**
> Dont understand why she is using her "personal" laptop for work. The company should buy her a work laptop for "work".

unless she is using VPN, then the company doesn't have to buy her anything.

---

### Post by Earl_Maroon on 2009-09-24
> **MC707 said:**
> So more advanced linux people are 'abnormal'? :P

People who can use computers with a reasonable degree of proficiency are abnormal.

---

### Post by MC707 on 2009-09-24
> **Earl_Maroon said:**
> People who can use computers with a reasonable degree of proficiency are abnormal.

Hmmm up to what extent of the word?

---

### Post by Exodist on 2009-09-24
> **pwnst*r said:**
> unless she is using VPN, then the company doesn't have to buy her anything.
The company "doesn't" have to buy her anything. But she doesn't have to use her own laptop for work either. That being said every company I have worked for gladly purchases the worker a laptop when their job requires it. But if she is just trying to get out of the office more, thus doing more work at home on her own. Then thats on her own dime.

---

### Post by pwnst*r on 2009-09-24
> **Exodist said:**
> The company "doesn't" have to buy her anything. But she doesn't have to use her own laptop for work either. That being said every company I have worked for gladly purchases the worker a laptop when their job requires it. But if she is just trying to get out of the office more, thus doing more work at home on her own. Then thats on her own dime.

agreed. it's also called time management ;)

---

