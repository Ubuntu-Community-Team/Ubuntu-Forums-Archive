---
title: "Fallout 3 in WINE on Ubuntu 11.04 Natty"
date: 2011-05-19
forum: Wine
---

### Post by irok30278 on 2011-05-19
Hey, guys!
Okay, so let me start by saying that I have been EVERYWHERE in search of an answer for this problem and have so found NO useful information.  What I'm trying to do is install Fallout 3 in WINE 1.3.15 (or for that matter in PlayOnLinux) and have so far been completely incapable of doing so.  I can get through the installation process, but I cannot seem to launch the game.  Every time I do, my computer freezes completely (Except for the mouse) and if Compiz is running, it crashes.  I really love this game and I used to play it all the time on Windows 7, so it sucks that it's not working on my favorite operating system.  After trying to run it in the console with the command
"wine fallout3.exe"
I got the errors
"fixme:actctx:parse_depend_manifests could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)"
and
"fixme:win:EnumDisplayDevicesW((null),0,0x32f55c,0x00000000), stub!"
Not sure what either of these mean, but I do know it's preventing me from using this game.
The tutorial I used to install it came from here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)
Any help on this subject would be greatly appreciated!  Thanks a lot!

---

### Post by gsmanners on 2011-05-19
Those aren't errors. That kind of thing comes up all the time. You're probably running into a conflict with compiz. You need to run either with classic or some other non-compositing window manager.

That said, FO3 and FNV are highly unstable. You should double-check whether you have done everything in that procedure you linked to.

---

### Post by bobwyajnr on 2011-05-20
Hi **irok30278**

I had a quick look at the comments for the *Fallout 3* page on AppDB. You're going have to be a very confident WINE/Ubuntu user to get this game working through WINE. I would say the game is being misrepresented as running at Gold standard - definitely **Silver** at most (perhaps even **Bronze**). One too many patches and hacks for my liking!

It's a dirty subject that is often overlooked on AppDB - but if you have the retail copy of Fallout 3 (i.e. not Direct-To-Drive or Steam) - you may need to apply a no-CD/DVD patch (due to the SecuROM v7 - thanks Sony you bunch of *****).

The "fixme:" comments, as **gsmanners** commented, are simply comments/reminders to (wanna be) WINE developers that a particular Windows API feature is not fully developed. An "err:" tag is a real error though - you have a problem then!

You probably won't get much help on these forums. I guess most Ubuntu users are more new to Linux - then say Arch users!

I would recommend taking full advantage of the fact that Fallout 3 has 4 Maintainers (!!) on AppDB. PM them individually and say exactly what steps you have taken to get Fallout 3 to run. I mean exactly! Detail! If you repeat your original post here you will get ignored or shot down in flames (there is no jolly "code of conduct" over at AppDB)! Personally if I get a sensible/reasonably in depth question on AppDB (about a game I maintain) I'll answer it (otherwise it goes in the recycler)! :D

I should also add that you are probably going to run into bugs related to your use of a 'bleeding edge'- new window manager. (Reason why I stick with KDE 4.x and Gnome 2.x - [Linux-Mint]("http://www.linuxmint.com/") ftw :D ) Both Unity and Gnome 3 users are reporting problems running applications through WINE - on the WINE bugs mailing list...

Sorry I cannot help more - but I'm not a Fallout 3 owner - I'll probably buy it in the Steam sales one day though! :popcorn:

Bob

---

### Post by irok30278 on 2011-05-20
> **bobwyajnr said:**
> Hi **irok30278**

I had a quick look at the comments for the *Fallout 3* page on AppDB. You're going have to be a very confident WINE/Ubuntu user to get this game working through WINE. I would say the game is being misrepresented as running at Gold standard - definitely **Silver** at most (perhaps even **Bronze**). One too many patches and hacks for my liking!

It's a dirty subject that is often overlooked on AppDB - but if you have the retail copy of Fallout 3 (i.e. not Direct-To-Drive or Steam) - you may need to apply a no-CD/DVD patch (due to the SecuROM v7 - thanks Sony you bunch of *****).

The "fixme:" comments, as **gsmanners** commented, are simply comments/reminders to (wanna be) WINE developers that a particular Windows API feature is not fully developed. An "err:" tag is a real error though - you have a problem then!

You probably won't get much help on these forums. I guess most Ubuntu users are more new to Linux - then say Arch users!

I would recommend taking full advantage of the fact that Fallout 3 has 4 Maintainers (!!) on AppDB. PM them individually and say exactly what steps you have taken to get Fallout 3 to run. I mean exactly! Detail! If you repeat your original post here you will get ignored or shot down in flames (there is no jolly "code of conduct" over at AppDB)! Personally if I get a sensible/reasonably in depth question on AppDB (about a game I maintain) I'll answer it (otherwise it goes in the recycler)! :D

I should also add that you are probably going to run into bugs related to your use of a 'bleeding edge'- new window manager. (Reason why I stick with KDE 4.x and Gnome 2.x - [Linux-Mint]("http://www.linuxmint.com/") ftw :D ) Both Unity and Gnome 3 users are reporting problems running applications through WINE - on the WINE bugs mailing list...

Sorry I cannot help more - but I'm not a Fallout 3 owner - I'll probably buy it in the Steam sales one day though! :popcorn:

Bob

Thanks a lot, man.  You helped more than you realize.  I got Fallout 3 working last night through a lot of poking and prodding at WINE settings and such, but as you said, it's definitely not running at gold standard. I am, however, able to play it and I will be going to AppDB to find out more on the subject.  But, yeah, thanks for the reply!  Oh, yeah, and I would DEFINITELY recommend that you buy it.  It's probably the best game I've ever played.

---

### Post by gsmanners on 2011-05-20
I have FO3 GotY edition. It's very nice, but it crashes and freezes up a LOT, even in wine. The frame rate isn't anywhere near what you get in native Windows (probably because of all the hacking the video drivers do to get a good frame rate in spite of how bad the game engine is). You really have to be a masochist like me to want to keep at it.

---

### Post by irok30278 on 2011-05-20
> **gsmanners said:**
> I have FO3 GotY edition. It's very nice, but it crashes and freezes up a LOT, even in wine. The frame rate isn't anywhere near what you get in native Windows (probably because of all the hacking the video drivers do to get a good frame rate in spite of how bad the game engine is). You really have to be a masochist like me to want to keep at it.

Haha, then I guess I'm a masochist like you!  I like a challenge every now and then, though.  It runs great on my windows installation (albeit buggy because Bethesda kinda sucks at making game engines) but with more tweaking, I've been able to get it to run very smoothly other than in VATS.  You were right about the Compiz conflict.  As soon as I shut off all the effects things started working the way they're supposed to, I just wonder what I'm going to do when 11.10 comes out with Unity and GNOME 3.

---

### Post by bobwyajnr on 2011-05-20
> **gsmanners said:**
> ...
You really have to be a masochist like me to want to keep at it.

+1

Linux is currently great as Server OS - but still not so great as a Desktop OS. The underlying problem is that FOSS programs are all ported to Windows - but it is a one way street - commercial programs are rarely ported to Linux. Hardware drivers still have to be reversed engineered. It's all a bit of an up-hill battle! :popcorn:


Bob

---

### Post by bobwyajnr on 2011-05-20
@ **irok30278**

np... Probably didn't help much! Do you want to mark the thread as solved? :)

Bob

---

