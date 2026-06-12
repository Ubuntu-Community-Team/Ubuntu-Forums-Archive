---
title: "An aggrivatedly reluctant Windows user"
date: 2005-09-27
forum: Testimonials &amp; Experiences
---

### Post by Scuddie on 2005-09-27
Over the years, I have been eagerly curious of successfully running linux on my PC, but have been scared off by each attempt.  I started out with RedHat 5, which turned out to be a royal pain, as nothing worked.  I tried Mandrake, and things worked, but I had dependancy problems up to my armpits.  I tried slackware, and I didnt get anywhere because of the fact that there were absolutely no instructions to follow whatsoever.  I tried Gentoo, but it took three days and six attempts just to successfully install it.

Finally a few months ago, I came about finding this distro.  Installation was quite easy, configuration was also relatively simple, and all seemed well.  However, as I continued to install more programs, and use more devices, the true nature of linux finally became apparent.  It appears that there is no uniform or standard whatsoever; seems the only thing anything has in common with anything else is that is uses the Linux kernel.

For example, when I installed Hoary, I was not expecting to have to deal with four different sound daemons constantly conflicting with eachother, nor would I expect a sound daemon conflicting with itself.  I don't want to have to disable Gnome's daemon instance in order to run VLC, and I don't want to have to disable a game's daemon instance in order to listen to my audio CDs as background music.  And I also don't want to see "device is busy" every time I don't release the sound card.  Windows doesn't always say "device is busy", but why does linux?

Also, while I was getting things not from the repository, I was shocked to see the amount of dependancies that were required for each program.  Sure it wasn't like Mandrake, but it still kinda got to me.  The part that irked me the most was that some programs required gcc 2.x to compile, and some required gcc 3.x.  I was not in the mood to switch between two very seperate compilers often, just so I could install a program.  All Windows has for libraries is DirectX and MSVC++ runtime and a couple others that are at the core of the OS, which are backwards compatible with previous versions.  Anything proprietary would be coded into the program itself, or linked to a DLL in the same directory.  Windows doesn't have a timely problem with conflicting dependancies, but why does linux?

I also don't like the fact that when I update or modify drivers, I have to rebuild the kernel.  And every time I do that, I end up wrecking the OS.  I would much rather just install the drivers in a directory and be done with it.  However, that doesn't seem to be easy.  I'm going to miss the days where I run an executable and follow onscreen instructions and be overwith.  It makes me wonder why I should even bother with drivers.  Windows doesn't have (many) driver installation difficulties, but why does linux?

Sorry for the vent, but I am a bit angry that it seems I won't be able to use a PC once Vista is out, for two reasons: Vista will be the MS OS that goes too far, and I am inexperienced when it comes to OSes where the only thing that is common is the kernel.  And yes, I know these problems are solveable, but I cant see linux coming into the home for a substantial part if this continues the way it is going, especially if the user isn't given any direction.

Again, sorry for the vent.

---

### Post by weasel fierce on 2005-09-27
I've never really had a lot of dependency issues, but then, I've mainly installed things from the repo's, and compiled a single game.

I've never compiled a program for windows though, so I have no idea of how it works there. 

Ultimately though, some OS's simply wont fit some people. Its about finding the one that works for you, I think.

---

### Post by BoyOfDestiny on 2005-09-27
[QUOTE=Scuddie]
For example, when I installed Hoary, I was not expecting to have to deal with four different sound daemons constantly conflicting with eachother, nor would I expect a sound daemon conflicting with itself.  I don't want to have to disable Gnome's daemon instance in order to run VLC, and I don't want to have to disable a game's daemon instance in order to listen to my audio CDs as background music.  And I also don't want to see "device is busy" every time I don't release the sound card.  Windows doesn't always say "device is busy", but why does linux?
Again, sorry for the vent.[/QUOTE]

Heh, again ESD rears it's ugly head. 
I did a poll on it, and it seems it works about 50/50. I'm happily running multiple sounds with ALSA, and ESD off. 

try this in a terminal: "sudo killall esd"

should eliminate the problem. 
If you like this, go to System->Preferences->sound and uncheck the box about enabling sound server. 

Then in Sytem->Preferences choose multimedia selector (choose alsa for the output and then hit test, you should hear a nice annoying hum).

For my games etc, I apt-get install libsdl-all (or something similar, going from memory here)

The only "downside" is I don't have gnome system sounds (but I didn't want them anyway)

---

### Post by matthewv on 2005-09-27
I think the sound problem is fixed in Breezy... I had the same problem with Hoary

---

### Post by poofyhairguy on 2005-09-27
> **Scuddie] It appears that there is no uniform or standard whatsoever said:**
> 

And the xserver. Kinda.

> 
For example, when I installed Hoary, I was not expecting to have to deal with four different sound daemons constantly conflicting with eachother, nor would I expect a sound daemon conflicting with itself.  I don't want to have to disable Gnome's daemon instance in order to run VLC, and I don't want to have to disable a game's daemon instance in order to listen to my audio CDs as background music.  And I also don't want to see "device is busy" every time I don't release the sound card.  Windows doesn't always say "device is busy", but why does linux?

Because sound was a big problem in Hoary. This is fixed in Breezy (as far as I can tell using it everyday).

[QUOTE]
Also, while I was getting things not from the repository, I was shocked to see the amount of dependancies that were required for each program.  Sure it wasn't like Mandrake, but it still kinda got to me.  The part that irked me the most was that some programs required gcc 2.x to compile, and some required gcc 3.x.  I was not in the mood to switch between two very seperate compilers often, just so I could install a program.  All Windows has for libraries is DirectX and MSVC++ runtime and a couple others that are at the core of the OS, which are backwards compatible with previous versions.  Anything proprietary would be coded into the program itself, or linked to a DLL in the same directory.  Windows doesn't have a timely problem with conflicting dependancies, but why does linux?

Because its chaos. Thats why we have the whole repository system. Outside it is chaos. I only stick to apt-get.

> 
I also don't like the fact that when I update or modify drivers, I have to rebuild the kernel.  And every time I do that, I end up wrecking the OS.  I would much rather just install the drivers in a directory and be done with it.  However, that doesn't seem to be easy.  I'm going to miss the days where I run an executable and follow onscreen instructions and be overwith.  It makes me wonder why I should even bother with drivers.  Windows doesn't have (many) driver installation difficulties, but why does linux?

Because Windows, not Linux, has 98% of the desktop market. Good drivers aren't made for a third ran desktop OS like Linux as much.

> 
Sorry for the vent, but I am a bit angry that it seems I won't be able to use a PC once Vista is out, for two reasons: Vista will be the MS OS that goes too far, and I am inexperienced when it comes to OSes where the only thing that is common is the kernel.  

Your XP copy will never fade away.

> 
And yes, I know these problems are solveable, but I cant see linux coming into the home for a substantial part if this continues the way it is going, especially if the user isn't given any direction.


TiVo enters the home today- in TiVos, in Razor cell phones, in wireless routers.

Oh....you mean as a desktop OS. Well.....its on this nerds desktop. One at a time I guess. Sorry it didn't work for you.

Push comes to shove, there is always Apple and OSX.

PS: had to move thread

---

### Post by Turtle.net on 2005-09-27
I am not a specialist, but I agree with the first post. Linux is not ready to be the first and only OS for everybody.
I really think that Linux is not intended for everybody. You need to be a little bit passionate to invest enough time to have linux working correctly. You need to spend a lot of time to learn how to fix problems when they come up.
But all this work will give you the best OS and desktop you have ever seen : yours

---

### Post by nocturn on 2005-09-27
[QUOTE=Turtle.net]I am not a specialist, but I agree with the first post. Linux is not ready to be the first and only OS for everybody.
I really think that Linux is not intended for everybody. You need to be a little bit passionate to invest enough time to have linux working correctly. You need to spend a lot of time to learn how to fix problems when they come up.
But all this work will give you the best OS and desktop you have ever seen : yours[/QUOTE]

While I agree partially with your comment, I do not think WinXP is the first and only OS for everybody.  Sure, anyone can run it, but installing the anti-virus, firewall etc software it so desperately needs is beyond 90% of its users.
At leatst Ubuntu comes with no open ports and the Linux design makes it more resilient against virusses.

---

### Post by jdong on 2005-09-27
[QUOTE=matthewv]I think the sound problem is fixed in Breezy... I had the same problem with Hoary[/QUOTE]

Not completely; it works better for some cards, but not others (I have no clue why)

---

### Post by dcraven on 2005-09-27
Aside from the sound server thing, which is being slowly remedied, the other annoyances you list are actual strengths for some people. True, apps for other operating systems don't need external dependancies as they are statically linked. That's also why these applications ship on a full CD. 

~djc

---

### Post by Turtle.net on 2005-09-28
[QUOTE=nocturn]While I agree partially with your comment, I do not think WinXP is the first and only OS for everybody.  Sure, anyone can run it, but installing the anti-virus, firewall etc software it so desperately needs is beyond 90% of its users.
At leatst Ubuntu comes with no open ports and the Linux design makes it more resilient against virusses.[/QUOTE]

I do not say that Win XP is the only OS for everybody (i do not know MacOS but I heard a lot of good things about it), let say that WinXP has the avantage to work on every machines (they are designed for it...so...) and that with the strictly minimum of knowledge you can secure your PC for external threats (just tell to someone to have a look to [www.secuser.com](www.secuser.com) will be sufficient and in few clicks to install firewall AND antivirus.and to understand why).

My point is : if Linux is a far better system than WinXP, it is only designed for people ready to learn and who want to learn...

---

### Post by matthew on 2005-09-28
[QUOTE=Turtle.net]My point is : if Linux is a far better system than WinXP, it is only designed for people ready to learn and who want to learn...[/QUOTE]
From a security standpoint, this is true of any OS. If you want to be secure from viruses, attacks, worms, spyware, adware, etc. you will have to learn something. If you want to use Windows you have to learn how to scan for, find, and combat each of these problems regularly. If you want to avoid many of them you can learn MacOS, Linux, BSD or something else. Security demands education of one sort or another. I just tell people to choose to learn the one they are most comfortable with and quit complaining about the other options.

---

### Post by brentoboy on 2005-09-28
scuddie is right

linux is a hobby until they get thier stuff together.

The extreem number of choices in linux is the biggest flaw - and biggest advantage.

But just because the greater linux community thrives on choice, doesnt mean ubuntu needs to have 14 different ways to control network settings. or 3 sound servers, or 10 ways to configure printers.

The reason I like ubuntu over suse is that adding a printer in suse has about 7 different wizards in different areas of the menu system for adding a printer or chaning its settings.

dangit, pick a good one, and add features in it that others have so people dont miss the alternative, and then DUMP the excess crap.  Honestly you dont need synaptic and kynaptic.  Synaptic works perfectly well in KDE - why have 2 seperate programs to build/test/debug/and answer questions about.

Maybe, for serious applications, like web browsers, have 2 or 3 options - choice is good, but when the choices are 93% underdeveloped kids toys, dont offer them - only offer the 2 or 3 "real" alternatives.

Ubuntu doesnt need to support kdm and gdm - just use gmd and allow people to run KDE on gdm.  It works perfectly well, why deal with the other?

Linux is about choice - choice to pick a new distro if you dont like this one - let people who dont like the control panel apps you choose go elsewhere - just make sure yours are the best, and no one will ditch out over it.

-i'm done venting.

---

### Post by Kyral on 2005-09-29
Here we have a classic example of two dueling philosophies.

One says "There should be only one program to a purpose!" and the other says "There should be many choices so people can use what they like!"

While I agree that having 4 sound daemons is frickin' ludicris, on other things I agree that there should be infinite amount of choices. You don't like Mozilla, use Firefox. Don't like Firefox, use Opera. Don't like Opera, use Konqeror. Don't like Konqeror, use Epiphany, etc. 

Linux is all about choice, choose your path and stick to it :D

---

### Post by mstlyevil on 2005-09-29
[QUOTE=brentoboy]scuddie is right
linux is a hobby until they get thier stuff together.
The extreem number of choices in linux is the biggest flaw - and biggest advantage.[/QUOTE]

  I have to dissagree that linux is just a hobby. If pc makers like Dell had pc's that were built and optimised for let's say for Ubuntu preinstalled. I think many noob's would not notice much of a difference. All these issues we have to work out on our own would already be worked out by the hardware vendor and it would just work the way it was advertised. If you ever build your own windows pc you will find out what I am talking about. I had driver issues, bios issues and dependency problems with XP when I built this machine. I have 99% of those problems worked out after 2 years, but they still show their ugly heads every now and then. Just go and build your own pc and find out for yourself if you think I am full of it.

---

### Post by jdong on 2005-09-29
[QUOTE=brentoboy]scuddie is right
linux is a hobby until they get thier stuff together.[/QUOTE]
I wouldn't say so. Linux already has established roles with purposes ranging from high-performance enterprise servers to centralized neural network intelligence in next-generation US Military combat systems.

What you put into Linux is what you get out -- just like Windows. Any OS takes a considerable amount of tweaking before it suits the user. Any OS takes a while to get used to -- think about the learning process of someone taking the jump from Win98->XP... There's *still* a considerable learning curve (guess and check process, if you will) and that's a mere version jump between the same basic GUI. Hopping over to Linux is learning a whole new environment with limited parallels to the all-familiar Windows OSes, so naturally it'd take even more time to learn.


I usually show both Windows and Linux to the first-time computer users, and a significant majority of them prefer Linux over Windows after using both for a few days.

---

### Post by angrykeyboarder on 2005-10-04
[quote=dcraven]Aside from the sound server thing, which is being slowly remedied, the other annoyances you list are actual strengths for some people. True, apps for other operating systems don't need external dependancies as they are statically linked. That's also why these applications ship on a full CD. 

~djc[/quote] 
Windows which has been cursed for years for "DLL hell" in fact borrowed that concept from UNIX. Of course, so did Linux.

The fact is regdless of OS, having all these library files that are used (ore can be used) by multiple programs is a major cause of instability everywhere.

The whole reason for thier existance dates back to the days of hard drives that maxed out at 350 MB.

In this day and age, they aren't necessary anymore and software would run better if it "shipped on a full CD".

Actually, most sofware that does that is Windows based and it **still** thows libraries in the system folder.

Frankly there are things I like and dislike about both Linux and Windows. The would do good to borrow more from one another (more than they already do).

The main thing that will keep Linux off the desktop is the poor multimedia support (when compared to Windows OR MacOS). Until that's resolved it will remain popular only with geeks like us.

---

### Post by aysiu on 2005-10-04
[QUOTE=angrykeyboarder]
The main thing that will keep Linux off the desktop is the poor multimedia support (when compared to Windows OR MacOS). Until that's resolved it will remain popular only with geeks like us.[/QUOTE] Or the fact that every mainstream retailer preinstalled computers with Windows XP.

If people want multimedia support, they can use Linspire, Mepis, or Blag. I don't know anyone (in real life--not on forums) who has actually tried any Linux distribution (ever) and said, "You know. I absolutely love it. I would adopt it completely. It's just the multimedia support is so bad." In fact, I know only one person who tried it, and she stopped because Thunderbird was having issues with her Hotmail account (a known problem in Windows as well).

---

### Post by doclivingston on 2005-10-04
> **angrykeyboarder]The fact is regdless of OS, having all these library files that are used (ore can be used) by multiple programs is a major cause of instability everywhere.[/quote]

Windows' "DLL Hell" is caused when programs which are designed to use their own copies of DLLs accidently use a different copy. The problem was mostly caused by programs throwing their DLLs in the system directory, and hoping that nothing had one with the same name.

This was solved by each application keeping it's DLLs in the application's directory. The downside of this, is that they cannot share DLLs (obviously, as that is the point) said:**
> . If you have one application which uses Howl (one implementation) and another application that uses Avahi (a different implementation), you simply cannot run both application at one - it doesn't matter if they use shared libraries, are statically linked or whatever.


[QUOTE=angrykeyboarder]The whole reason for thier existance dates back to the days of hard drives that maxed out at 350 MB.
In this day and age, they aren't necessary anymore and software would run better if it "shipped on a full CD".

Taking up more hard-drive space isn't the only disadvantage the occurs when application keep their own copy of libraries. With shared-libraries only one copy of the library needs to be loaded into memory, even if more than one application is using it. Would you be happy if running a Linux desktop suddenly requires twice as much memory, because application weren't sharing libraries?


Another disadvantage is that upgrading a library is no longer simple. Take one of the security flaws found in zlib (a compression library) a while back. With Linux you just have to upgrade the one shared library, and then the security problem is gone.

On Windows (because applications don't share libraries like this), you would need to update *every* application that has a copy of this library, and for something common like zlib you might have ten or twenty applications that use it. More importantly you a) may not know which application use the library, and b) will have to wait until the application author released an updated version with the fix (which may take a long time).


[0] Well, actually you can - for a short time, before errors start ocurring and they explode.

---

### Post by drgreborn on 2005-10-05
I believe that the root of the issue is this. Ability to use an OS straight out of the box with a STANDARD GENERIC system or spend time and effort to CUSTOMISE the OS to FIT YOU. I've spent 1 week with Hoary and I'm still not finished setting it up. But thats the thing with linux, it's non standardization. You can set your OS and optimize it to what you use it for. For me I'm a student doing Game Dev so now I'm setting the Hoary up for such. 

I'm not saying that LINUX could not be used straight out of the box as it is but it need that personal touch from its user. Similarly I am not saying that LINUX is just for those geeks and techies who gets a kick from customising and tweeking thing an dnot for the so called everage Joe or Jill.

It is a matter of choice, isn't that what this is all about? Each OS has its strength and weaknesses, Mac OS for its power in processing graphics and media, linux for its powerfull ability to run multiple processes at the same time and Windows for its ease of usage.

---

### Post by RawMustard on 2005-10-13
I think the biggest problem with linux is graphic support.  I've never understood why I can see a beautifull installer screen with mouse and buttons and all the glitz(As in Anaconda), but once the install is done, and x tries to load gdm or visa versa, you get x failed blah blah blah, why can it not just default back to whatever it was running on when the install process was happening?  I can't count on all my fingers and toes the amount of people that just wiped their drives and went back to windows in disgust over this problem.  Windows doesn't have support for new cards either, but it doesn't give you a black screen!

The next hurdle to adoption IMHO is Sound.  Even with a supported sound card, sound is still very problematic in linux and that's not even accounting for patented file formats, even open formats don't always work out of the box.  and then there's the problems already mentioned with conflicting daemons.  This is 2005, nearly 2006 and still linux can't get sound to work with supported cards???
Windows users just laugh at this and you all know that to be true!

Now, once we have a working system up and running, lets install our favourite linux supported games, lets choose a really popular one and see what happens, Quake3Arena anyone?  How do you get sound to work in Q3a even in Breezy???

So you can see where I'm heading with this, these things need to be made 100% rock solid which they pretty much are in windows land.  And don't say "but these things were made for windows", because everything I've have mentioned is made for linux too!

I love Breezy, it is without doubt the best distro out there, but I could not install it for 998% of my windows brain-washed friends.  I would spend more time helping them sort out these silly little problems, than I would sitting back and enjoying my own computing experience; hell, I have that problem with windows ](*,)

I think anyone with a little more knowlege than the average joe when it come to computers, if they really are honest with themselves, will deep down know that linux is still a way off being used by the masses. Sad, but true :(

Just my thoughts on the subject, your milege may vary :D

---

### Post by jatos on 2005-10-13
I think the only way that linux is going to become suitable for the mases is if everyone doing anything related to linux joins in as **organised** team to iron the many problems in linux.

---

### Post by weasel fierce on 2005-10-13
The only way linux is going to be suitable for the masses is if the hardware manufacturers actually start making drivers for us

---

### Post by erikpiper on 2005-10-13
I have an IBM thinkpad that runs beautifully with only OSS. Windows software is so hard to install! And why does it install at 800/600? I cnt move my panels! Darn it crashed.


That is my windows experience :p 


If you grew up with linux, you would be saying bad things about windows.

---

### Post by angrykeyboarder on 2005-10-13
[quote=weasel fierce]The only way linux is going to be suitable for the masses is if the hardware manufacturers actually start making drivers for us[/quote] 
And if Linux came from one place (Like Windows and OS X do) they would have done so long time ago.

Instead it comes from ***hundreds*** of places.

It's getting better but Linux needs to standardize even further so that many more hardware vendors will consider it. 

I'd like to see improvmernt but it won't bother me if it doesn't gain mass appearl. As long as it's usable without constant headaches. 

Frankly Windows XP is more stable.  I hate to say it but it's true. And it works out of the box.

That's the other obstacle to Linux acceptance. Multimedia support. The other day I said (here) that if you want that you need to get a commercial distro such as SuSE or Mandriva. Even those have some problems. (At least SuSE 9.1 did for me a few years ago).

But for geeks like me, the extra work to get Linux running right is (usually) worth it.

---

### Post by aysiu on 2005-10-13
[QUOTE=angrykeyboarder]
It's getting better but Linux needs to standardize even further so that many more hardware vendors will consider it. [/quote] That's not the issue. Many hardware vendors make their drivers closed source, so that Linux developers can't make Linux versions of those drivers.

> 
Frankly Windows XP is more stable.  I hate to say it but it's true. And it works out of the box. Preinstalled always works out of the box.

> 
That's the other obstacle to Linux acceptance. Multimedia support. The other day I said (here) that if you want that you need to get a commercial distro such as SuSE or Mandriva. Even those have some problems. (At least SuSE 9.1 did for me a few years ago). You're not going to get that out of the box for Ubuntu--it's a free OS in every way; no proprietary stuff. Linspire and Mepis seem to "just work" as far as that's concerned (I, too, have had issues with SuSE and Mandriva).

---

### Post by randomnote1 on 2006-03-08
I tell you who does program installs the smart way.  MAC.  All you have to do is drag the files from a CD over to a folder and it is installed.  I haven't really used a MAC for about 10 years and I still remember how aggrivated I was going to Windows, running installs and all that crap.  Obviously there is a lot of program stuff in Linux that is hanging around from the days of limited HD space and limited processing power.  I think the question is how do we modernize our operating systems so that the average user who wants to just have the computer work can have that.

---

### Post by IYY on 2006-03-08
I love Linux and enjoy every moment of using it, but I agree with many of your arguments. 

I think that the main problems are with the X server. Mac OS X did the right thing and designed a whole new graphical system that's stable, fast, appealing, consistent, and easy to design programs for.

---

### Post by OffHand on 2006-03-09
I use XP, Ubuntu and OS X. There's no better compu experience than mac os x imo. It's about as easy as it gets. Drag and drop to install.... beautiful, just beautiful. That's what ordinary people want. I hope Linux will go that direction too.

---

### Post by Brunellus on 2006-03-09
don't be a menace to Ubuntu while drinking your juice n da hood.

Use whatever makes you happy.

---

### Post by garba on 2006-03-16
[QUOTE=Scuddie]

For example, when I installed Hoary, I was not expecting to have to deal with four different sound daemons constantly conflicting with eachother, nor would I expect a sound daemon conflicting with itself.  I don't want to have to disable Gnome's daemon instance in order to run VLC, and I don't want to have to disable a game's daemon instance in order to listen to my audio CDs as background music.  And I also don't want to see "device is busy" every time I don't release the sound card.  Windows doesn't always say "device is busy", but why does linux?
[/QUOTE]

i hear you, the state of sound daemons in linux is one of the most irritating issues we have to live with, luckily alsa can now do software mixing, i hope we'll soon get rid of all this esound/arts (which i hope will burn in hell) etc crap and define a standard interface for sound resources

---

