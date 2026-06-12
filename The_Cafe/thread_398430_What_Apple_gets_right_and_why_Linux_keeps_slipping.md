---
title: "What Apple gets right and why Linux keeps slipping behind..."
date: 2007-04-01
forum: The Cafe
---

### Post by karellen on 2007-04-01
just share here some ideas about:
[http://theosib.livejournal.com/1742.html](http://theosib.livejournal.com/1742.html)
maybe he has some good points imo :)...

---

### Post by aysiu on 2007-04-01
I have two gripes and an agreement with this:

1. Package management makes the "location" of applications irrelevant. In fact, even if the menu item doesn't populate (which is annoying and an *actual* Linux problem), you can Alt-F2 and type the name of the application to launch it and still not know "where" the application "lives." If you like the OS X way of managing applications, GoboLinux is Linux and handles things the same way.

In fact, if we lived in a Linux world, people would be writing articles about how Mac OS X and Windows need to "get it right" because it's dumb to have to have applications in charge of their own updating, and the user having to redownload installer files for each application to update all the applications on their systems. In the Linux world, wait six months, and all your applications get updated with the operating system.

2. .plists make my head hurt. Please, give me a text-based configuration file any day over a .plist. Even a .xml file is better than a .plist. Trying to figure out how to tweak my wife's OS X desktop is always an adventure in Google searching. I have to figure out which .plist to edit and where it lives. They are not obviously named or organized unless you're a Mac OS X guru. Tweaking my IceWm is a simple matter of opening up the text files in /home/username/.icewm and changing a few options. Text editor wins over .plist editor any day in my book.

3. I will agree with the part about clipboard management in Linux. It sucks, and the clipboard manager packages are just workarounds for something that's clearly missing. I've seen people complain about not being able to paste from one application to another (GIMP, Firefox, OpenOffice are usual culprits) or the clipboard forgetting what got copied once the source application was closed.

[quote=the article by theosib]One of the things I'm implying here is that the Linux community should form standards committees.[/quote] News to *theosib*: there *are* standards committees, and they're working on it!
[http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB)

---

### Post by FuturePilot on 2007-04-01
Meh, I'd rather not have a system wide registry. That's why Windows is so slow.

---

### Post by karellen on 2007-04-01
> **aysiu said:**
> I have two gripes and an agreement with this:
In fact, if we lived in a Linux world, people would be writing articles about how Mac OS X and Windows need to "get it right" because it's dumb to have to have applications in charge of their own updating, and the user having to redownload installer files for each application to update all the applications on their systems. In the Linux world, wait six months, and all your applications get updated with the operating system.

:) totally agree with you, it's a matter of perspective and wide spreading of something that becomes ultimately a norm

---

### Post by aysiu on 2007-04-01
Reading over the comments, it seems a lot of other readers are on my wavelength.

And, contrary to what some new users critical of Linux seem to think, Linux users actually do admit the faults of Linux when they are *actual* faults. Two people in comments agreed the clipboard problem was a genuine issue (my commenting in this thread makes that three people).

I will say my wife *loves* her Mac, and I would never give her anything else. I'm glad Mac works for her and that Ubuntu works for me and that Windows works for some of our friends and family. She was totally amazed, though, when she found out you could install twenty programs in Ubuntu with one command: ```
sudo apt-get update && sudo apt-get install package1 package2 package3 package4... package20
``` Please don't make me Google all over for and download and launch a bunch of .dmg files that I then need to open and drag some icon from the white disk to the Applications folder... twenty times.

---

### Post by karellen on 2007-04-01
I believe maybe one of linux's greatest strenghts and also greatest misunderstandings/fear-generator for new users it's the terminal/command line. simply speaking, a very powerful tool. If you are willing to learn how to use it. Or better explained, if you want to learn anything new. everybody can point-and-click

---

### Post by aysiu on 2007-04-01
Ah, but that's also one of the beauties of OS X--it has a terminal, too. That's why I actually like working on OS X over Windows. The *cmd* DOS emulator is just not the same...

---

### Post by FuturePilot on 2007-04-01
If there's anything I like about Mac OS it's that it's a lot more related to Linux than Windows is. Some of those DOS commands are really weird.:-?

---

### Post by DoctorMO on 2007-04-01
> Linux keeps slipping behind

Just this in the title is emotive and not really right, Linux doesn't slip behind Apple because apple makes hardware not software that can be run on any machine so the points are more moot than even the fact that linux isn't slipping it's developing in the ways it wishes to.

Damn Mac fellows, I have a perfectly good Powerbook 17" I could drag out and use but I just don't get along with Mac OSX; it's just not me. why can't these dasterly chaps just say that Linux isn't for them.

What I find painfully ironic is that 'At Microsoft or Apple, a committee decides on APIs' But Apple and Microsoft APIs are the worst; why do people always fall back to open source libs and open source apis? is it because perhaps the developers do the right thing instead of the quick thing.

---

### Post by prizrak on 2007-04-01
I love the whole "well we got more resources now than in the 70's so lets waste them" argument. It's just great, why in the world would I run an OS that (even with Compiz) uses about 1% of my system resources when I can run Vista that will use 50% of them just idling? Maybe because I don't want my OS overtaking my system and instead actually use the damn applications. 

Another funny thing is that his not saying a thing that others don't know about/working on already. Most applications are moving over to XML config files, hell GNOME has gconf, which is basically Windows registry. Klik already rolls all the applications into their own dirs, when you compile no one is stopping you from picking out the location (before I knew how to change it all my compiles were sitting in my /home). To make even more interesting, there is an initiative to create fully self contained applications, by that I mean that a package contains it's own OS that is stripped down to run just that application and uses a VM. Another funny thing is that with all the power and resources Java is still damn slow ;)

---

### Post by graabein on 2007-04-01
Thread titles like this in the community cafe pisses me off. Same as with the Linux is not ready fud. Just had to get that off my chest ;-) I'll read the article now.

---

### Post by koshatnik on 2007-04-01
> Linux keeps slipping behind

Eh?

---

### Post by darweth on 2007-04-01
> **aysiu said:**
> I have two gripes and an agreement with this:

1. Package management makes the "location" of applications irrelevant. In fact, even if the menu item doesn't populate (which is annoying and an *actual* Linux problem), you can Alt-F2 and type the name of the application to launch it and still not know "where" the application "lives." If you like the OS X way of managing applications, GoboLinux is Linux and handles things the same way.

In fact, if we lived in a Linux world, people would be writing articles about how Mac OS X and Windows need to "get it right" because it's dumb to have to have applications in charge of their own updating, and the user having to redownload installer files for each application to update all the applications on their systems. In the Linux world, wait six months, and all your applications get updated with the operating system.


Heh.  I have not read the article and do not care to so I cannot comment on what was said there, but I have mixed feelings about package management.  Sure, I am now a Linux snob and appreciate the ease and simplicity of it all, but I am a different kind of user and still think and go about things in the non-nix way.  When I find out about apps, it is usually from the project page, a forum, etc.  Never while browsing through Synaptic or something.  Then a sudo apt-get install often is not enough because the official rep often does not have the latest version.  This means I still have to go hunt down someone's third-party deb or download the source and build it myself.  Though I suppose this problem is almost non-existent in a distro like Arch or Gentoo, but then you have other issues. ;)  

But anyway... I somewhat miss the Windows way of doing things and using installers and updating.  It was kind of exciting and charming in its own way, and it continues to be how I do things even on Ubuntu for the most part. :)

BTW --- I know that there is often not much of a reason for updating to the latest version of many apps, but I still have the itch to do so.  :)  I am not representative of the casual user who just wants their machine to work.  Even though I only do casual things (surf, music, chat), I still feel naked without bleeding edge applications!  Eeek!  I do use Ubuntu though because I like a stable libraries, desktop environments and foundation. But individual apps need to be bleeding!

---

### Post by prizrak on 2007-04-01
> **darweth said:**
> Heh.  I have not read the article and do not care to so I cannot comment on what was said there, but I have mixed feelings about package management.  Sure, I am now a Linux snob and appreciate the ease and simplicity of it all, but I am a different kind of user and still think and go about things in the non-nix way.  When I find out about apps, it is usually from the project page, a forum, etc.  Never while browsing through Synaptic or something.  Then a sudo apt-get install often is not enough because the official rep often does not have the latest version.  This means I still have to go hunt down someone's third-party deb or download the source and build it myself.  Though I suppose this problem is almost non-existent in a distro like Arch or Gentoo, but then you have other issues. ;)  

But anyway... I somewhat miss the Windows way of doing things and using installers and updating.  It was kind of exciting and charming in its own way, and it continues to be how I do things even on Ubuntu for the most part. :)

BTW --- I know that there is often not much of a reason for updating to the latest version of many apps, but I still have the itch to do so.  :)  I am not representative of the casual user who just wants their machine to work.  Even though I only do casual things (surf, music, chat), I still feel naked without bleeding edge applications!  Eeek!  I do use Ubuntu though because I like a stable libraries, desktop environments and foundation. But individual apps need to be bleeding!
Just use the dev versions of Ubuntu and you'll have new stuff all the time ;) I'm glad that you admit that you are not a typical user. The point that the article is trying to make is basically the "Linux is not ready for the desktop" one that is concentrating on the wrong side of things as usual.

---

### Post by Bloodfen Razormaw on 2007-04-01
> I will agree with the part about clipboard management in Linux. It sucks, and the clipboard manager packages are just workarounds for something that's clearly missing. I've seen people complain about not being able to paste from one application to another (GIMP, Firefox, OpenOffice are usual culprits) or the clipboard forgetting what got copied once the source application was closed.
You have been misinformed by the article.   [X has a clipboard system](http://en.wikipedia.org/wiki/X_Window_selection).  The weakness of that system is that it requires the applications to be running, which was fixed in KDE in 1998, and contrary to the mistakes of the article, *Klipper works with all GUI frameworks that use the X11 protocol properly*.  Any application which does not function with it is not properly using the X clipboard system or has a bug in negotiating formats (both which are possible problems in any desktop).  GIMP, for example, has a series of ugly hacks for trying to work around the historic lack of clipboard management in GTK environments, which can interfere with utilities that use the X11 standard for clipboard management.

---

### Post by cowlip on 2007-04-01
.

---

### Post by macogw on 2007-04-02
> **darweth said:**
> Heh.  I have not read the article and do not care to so I cannot comment on what was said there, but I have mixed feelings about package management.  Sure, I am now a Linux snob and appreciate the ease and simplicity of it all, but I am a different kind of user and still think and go about things in the non-nix way.  When I find out about apps, it is usually from the project page, a forum, etc.  Never while browsing through Synaptic or something.  Then a sudo apt-get install often is not enough because the official rep often does not have the latest version.  This means I still have to go hunt down someone's third-party deb or download the source and build it myself.  Though I suppose this problem is almost non-existent in a distro like Arch or Gentoo, but then you have other issues. ;)  

But anyway... I somewhat miss the Windows way of doing things and using installers and updating.  It was kind of exciting and charming in its own way, and it continues to be how I do things even on Ubuntu for the most part. :)

BTW --- I know that there is often not much of a reason for updating to the latest version of many apps, but I still have the itch to do so.  :)  I am not representative of the casual user who just wants their machine to work.  Even though I only do casual things (surf, music, chat), I still feel naked without bleeding edge applications!  Eeek!  I do use Ubuntu though because I like a stable libraries, desktop environments and foundation. But individual apps need to be bleeding!

Ubuntu does need to keep up with newer versions of packages.  You can wishlist newer versions in the Universe...  Fedora keeps very up to date though.  Their packages are often much much newer than Ubuntu ones.  I run unstable to keep up with the latest and see what's going to be new in Ubuntu.  I like what I see, though I'm rather tempted to reinstall Feisty's daily build just so I can see the new installer.

---

### Post by darweth on 2007-04-02
> **prizrak said:**
> Just use the dev versions of Ubuntu and you'll have new stuff all the time ;) I'm glad that you admit that you are not a typical user. The point that the article is trying to make is basically the "Linux is not ready for the desktop" one that is concentrating on the wrong side of things as usual.

Hey.  I was never complaining about having to put a little work in to build stuff from source or hunt down third-party packages. ;)  I was merely stating that it it is not much of an issue for me.  I actually enjoy doing a little grunt work.  It also, in some bizarre way, gives me more of a feeling of ownership and control over my PC.  I just still stick with Ubuntu over something like Arch because I do appreciate MOST of the general convenience and simplicity. :)

---

### Post by igknighted on 2007-04-02
> **darweth said:**
> Heh.  I have not read the article and do not care to so I cannot comment on what was said there, but I have mixed feelings about package management.  Sure, I am now a Linux snob and appreciate the ease and simplicity of it all, but I am a different kind of user and still think and go about things in the non-nix way.  When I find out about apps, it is usually from the project page, a forum, etc.  Never while browsing through Synaptic or something.  Then a sudo apt-get install often is not enough because the official rep often does not have the latest version.  This means I still have to go hunt down someone's third-party deb or download the source and build it myself.  Though I suppose this problem is almost non-existent in a distro like Arch or Gentoo, but then you have other issues. ;)  

But anyway... I somewhat miss the Windows way of doing things and using installers and updating.  It was kind of exciting and charming in its own way, and it continues to be how I do things even on Ubuntu for the most part. :)

BTW --- I know that there is often not much of a reason for updating to the latest version of many apps, but I still have the itch to do so.  :)  I am not representative of the casual user who just wants their machine to work.  Even though I only do casual things (surf, music, chat), I still feel naked without bleeding edge applications!  Eeek!  I do use Ubuntu though because I like a stable libraries, desktop environments and foundation. But individual apps need to be bleeding!

If you want to stay bleeding edge, try using Debian Sid (or a release based more directly on it than Ubuntu).  Ubuntu syncs with Debian Sid every 6 months to get caught up, but you go 6 months without the updates.  If you used, say, KANOTIX or Sidux then you could install a nice, stable system and update whatever apps you want (or the whole system if you prefer) as often as new versions come out.  And the newest version is usually in the repo's within a day or two (with the exception of right now due to the Etch freeze on the Debian repo's).  If thats not quick enough, there are also many SVN repo's you can use as well.

IMHO Ubuntu errs on the side of caution when upgrading apps, so I prefer a distro like Fedora or Sidux to stay more cutting edge with the package manager.  But the weakness is not the package management system, it is the repo's you choose to use.

---

### Post by darweth on 2007-04-02
Yeah, I have also given thought to switching to Debian Sid (Or Sidux) for a more 'rolling' distro, if I ever decide to do so.  I still think Arch would be the first I'd try though.  I am just a little too lazy to do so right now and my Edgy desktop is working fine and dandy, so I have little reason to. :)  Maybe in a month when Feisty drops, I will finally give everything a spin.

The funny thing is while I still have yet to use Arch, I have convinced three people to give it a shot. :x  Two of them were (then) Gentooholics, so it was not much of a stretch.  Every single one of them has adopted Arch as their main distro.  Maybe I should start taking my own advice!  lol :D

Is there any reason that one would prefer Debian Sid/Sidux over Arch (besides comfort with apt)?

---

### Post by igknighted on 2007-04-02
> **darweth said:**
> Yeah, I have also given thought to switching to Debian Sid (Or Sidux) for a more 'rolling' distro, if I ever decide to do so.  I still think Arch would be the first I'd try though.  I am just a little too lazy to do so right now and my Edgy desktop is working fine and dandy, so I have little reason to. :)  Maybe in a month when Feisty drops, I will finally give everything a spin.

The funny thing is while I still have yet to use Arch, I have convinced three people to give it a shot. :x  Two of them were (then) Gentooholics, so it was not much of a stretch.  Every single one of them has adopted Arch as their main distro.  Maybe I should start taking my own advice!  lol :D

Is there any reason that one would prefer Debian Sid/Sidux over Arch (besides comfort with apt)?

I've never used Arch, but to my knowledge (and I could be way off base here) it doesn't have that really strong central package manager like apt, or yum, or portage, etc.  You are a little more on your own, though not Slackware bad in this regard :P

---

### Post by darweth on 2007-04-02
> **igknighted said:**
> I've never used Arch, but to my knowledge (and I could be way off base here) it doesn't have that really strong central package manager like apt, or yum, or portage, etc.  You are a little more on your own, though not Slackware bad in this regard :P

Well... Arch has both Pacman (comparable to apt) and ABS (comparable to portage).  Both are supposed to be quite strong and very well-maintained.

---

### Post by mikeym on 2007-05-01
The package manager has to be the way to go for a open source based project like ubuntu as it is the only way you can keep some level of control over what is available for use and so what is supported by your system. It is also a great way of installing applications when it is a well established application i.e. it doesn't matter too much if it's not the latest version. 

But to claim that there is no difference to where the application is installed is silly. I guarantee that you will on occasion have to do some kind of search of the system to find a application folder to link to or put a plug-in in. Even worse is the spread of configuration files around the file-system. This is one area where apple got it right - keep it all in the same place. By all means have a package based install system but put it in a consistent and self contained place. 

It's good to see people taking some constructive criticism on-board. I sometimes think the Linux community can be a little too defencive about this kind of thing. Perhaps it's the underdog syndrome. But for most it's a case of trying to think of how to improve Linux and make it the best that it can be. If Mac has something good then lets have it too and do it better.

The clipboard thing is ridiculous that it has lasted so long without a standard being set. Another thing that I think is holding back Linux is that you still have to resort to the command line for too may tasks because there are still things that don't have graphical equivalents. 

There are some definite strong points to the GUI in OSX that could be used in Linux. I never thought I would find the menu bar at the top of the screen so useful but it has completely changed the way I navigate round applications. [Apple] + [tab] to move to the right application then [apple] + ['] to find the right window within it. 



There are some definite strong points to the GUI in OSX that could be used in linx. I never thought I would find the meu bar at the top of the screen so usefull but it has completely changed the way I navigate round applications. [Apple] + [tab] to move to the right aplication then [apple] + ['] to find the right window within it.

---

### Post by aysiu on 2007-05-01
If the model is good and the implementation is bad, fix the implementation--don't change the model.

We just need consistent inclusion of a .desktop file for /usr/share/applications with packages. If that happens, you *don't* need to know "where" applications "live."

---

### Post by mikeym on 2007-05-01
OK 2 examples from the last few days:

JDK - I had to search for the path to include when I was compiling something - fair enough it's something that you should know what you're doing with but I still was left looking around for it. 

Epiphany - trying to remove those pesky mplayer real media plugins. 

This is not a major gripe for me it's on the list of would be nice but I don't realy see why there would be that much difficulty in moving toward a single application location. It would just require a directive to change new packages to behave in this new way and a slow migration should follow.

---

### Post by prizrak on 2007-05-01
> **aysiu said:**
> If the model is good and the implementation is bad, fix the implementation--don't change the model.

We just need consistent inclusion of a .desktop file for /usr/share/applications with packages. If that happens, you *don't* need to know "where" applications "live."

Sometimes you do actually. When you want to install certain plug ins you might need to know where the program itself lives. However I think that's a shortcomming of the application as plugins and settings should be in ~ directory. In a multi user environment you might not want people using all available plug ins. For instance you don't want to run Java for someone who visits very random sites.

---

### Post by prizrak on 2007-05-01
> **mikeym said:**
> OK 2 examples from the last few days:

JDK - I had to search for the path to include when I was compiling something - fair enough it's something that you should know what you're doing with but I still was left looking around for it. 

Epiphany - trying to remove those pesky mplayer real media plugins. 

This is not a major gripe for me it's on the list of would be nice but I don't realy see why there would be that much difficulty in moving toward a single application location. It would just require a directive to change new packages to behave in this new way and a slow migration should follow.

I kinda agree with you there, I think that a common filesystem format should be established between distros and the file system needs to be simplified. 
I mean do we really need /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin and these are just the ones I can remember. 
A single /bin directory for all the executables would make quite a bit more sense. It can be divided into subdirectories for daemon executables and such.

---

### Post by mech7 on 2007-05-01
Pretty much agree with everything being written on that blog.. especially the app locations / menu entries and not having a single installer is very annoying.

Unfortunatly i doubt anybody is ever going to change this Apple and Microsoft are both 1 company making 1 os, while linux distro's are dozens of individual projects pasted togheter, and i doubt that is ever going to change :(

---

### Post by ThinkBuntu on 2007-05-01
I wholeheartedly agree about consistent user interfaces. On a Mac, **every single program** uses Apple+Q to exit. A similar standard needs to be implemented for Linux developers...often times I enter Ctrl+Q, then Ctrl+W when that doesn't work, and then have to resort to Alt+F4. Also, Preferences need to always be in the same place. On a Mac, they're always in the File menu. But on Linux, they could be in File, could be in Tools, could be in Settings, or could be in Edit.

But I deal with it because I'm a cheap bast*rd and I like my ThinkPad as much if not more than my MacBook.

---

### Post by Bloodfen Razormaw on 2007-05-01
> I wholeheartedly agree about consistent user interfaces. On a Mac, every single program uses Apple+Q to exit. A similar standard needs to be implemented for Linux developers...often times I enter Ctrl+Q, then Ctrl+W when that doesn't work, and then have to resort to Alt+F4. Also, Preferences need to always be in the same place. On a Mac, they're always in the File menu. But on Linux, they could be in File, could be in Tools, could be in Settings, or could be in Edit.
You are comparing apples and oranges.  Not all OS X applications actually are consistent, only those which use the same framework for building applications.  Most software available for OS X was not actually made for it, and will not behave that way.  You only get that behavior when the application is built on the framework Apple provides, By the same token, you always get consistent behavior using the same framework on Linux.  KDE and GNOME have consistent behavior for their desktops.  In fact, they are much, much more consistent than OS X, which is has absurdly inconsistent interfaces for every application.

---

### Post by mech7 on 2007-05-01
But you always know where your files are with linux it's very messy file system every app installs in a different place. :( 

> **Bloodfen Razormaw said:**
> You are comparing apples and oranges.  Not all OS X applications actually are consistent, only those which use the same framework for building applications.  Most software available for OS X was not actually made for it, and will not behave that way.  You only get that behavior when the application is built on the framework Apple provides, By the same token, you always get consistent behavior using the same framework on Linux.  KDE and GNOME have consistent behavior for their desktops.  In fact, they are much, much more consistent than OS X, which is has absurdly inconsistent interfaces for every application.

---

### Post by prizrak on 2007-05-02
> **mech7 said:**
> But you always know where your files are with linux it's very messy file system every app installs in a different place. :(

Not really. Your settings are kept in your /home directory in hidden files. On Ubuntu using repo's apt-get installs into /usr/bin and shared stuff resides in /etc. It's not THAT difficult but the issue is that while Ubuntu is set up this way other distro's are setup in another way. Also not all applications can be gotten from the repo's and might install somewhere else. 

The reason why Linux does it's thing this way is mainly because it was always a multiuser system. You can't install applications into a user directory if you want others to access it. It's complicated but the system should (and can) be a bit simplified.

---

### Post by euler_fan on 2007-05-02
I don't think I agree with the article's comments about config files entirely. In my experience, a well documented and laid out config file is not a problem to edit and understand. I agree it is all the ones that are not this way that are the problem. However, messy config files are an artifact of the way in which the app was written--to need a messy config file--not because there is anything wrong with config files or the use of them by an OS.

---

### Post by macogw on 2007-05-02
I'd much rather have the plain text config files we have than Windows' registry

---

### Post by mikeym on 2007-05-03
The problem as I see it with text config files is the same one I see in other parts of the OS. Most people using computer systems (not your traditional linux users) don't want find anything that they can't do in a graphical context.

I don't see how linux can reach the masses while it still relys so heavily on the terminal to be able to do tasks. By all means have the terminal functionality and the text config files but you have to provide people with a graphical alternative.

I seems to me that linux in it's early days came up with this really great terminal (command) system and it's never really been able to let go of it.  I still see people saying "of course you can do that. You just type XYZ into the terminal." 

However the gap is closing - it would be nice if it was recognised that this was a specific aim for development to cover these functions.

---

### Post by aysiu on 2007-05-03
> **mikeym said:**
> 
I don't see how linux can reach the masses while it still relys so heavily on the terminal to be able to do tasks. By all means have the terminal functionality and the text config files but you have to provide people with a graphical alternative. It doesn't rely that heavily on the terminal for tasks. Right now, there's only one common task that requires the terminal, and that is usually optional and then only for the computer administrator, not the everyday user--editing the /boot/grub/menu.lst file. There's another common task that sometimes requires a terminal, also only for the computer administrator, and that's editing the /etc/fstab file.

Again, those are not for everyday users--only the system administrator of the computer--and those are not Linux issues but Ubuntu issues.

Other Linux distros have graphical ways to edit Grub options and don't need the manual editing of the /etc/fstab file (when's the last time you heard of someone using Mepis who had trouble mounting a partition?).

In the meantime, you can check email, log in, browse the web, word process, change the desktop background, install new packages, remove old packages, edit the applications menu, configure sound options... all through pointing and clicking.

Seriously, I had to use the terminal on my wife's Mac to fix her widgets, as there was no *sudo* for Finder in OS X. But in Ubuntu, I could have just done an Alt-F2 ```
gksudo nautilus
``` to do it graphically.

---

### Post by n&amp;70{s&gt;,PGh on 2007-05-12
> **aysiu said:**
> It doesn't rely that heavily on the terminal for tasks.

The problem is, people still by-and-large *think* that it does. This isn't helped by common verbose Linux boot sequences and references to sudo, apt-get, fsck, make, and what-have-you, although Ubuntu has gone quite a long way towards lessening the need for these.

---

### Post by tehkain on 2007-05-12
> **Larry V said:**
> The problem is, people still by-and-large *think* that it does. This isn't helped by common verbose Linux boot sequences and references to sudo, apt-get, fsck, make, and what-have-you, although Ubuntu has gone quite a long way towards lessening the need for these.
I agree. It is easier to tell someone to open a  terminal and type "sudo aptitude install vi" rather they synaptic. So it is partially our fault because we are proving simple one shot fixes rather then explaining the gui method to the new users so they don't have to come back to ask everytime.

---

### Post by yoasif on 2007-05-12
> **aysiu said:**
> She was totally amazed, though, when she found out you could install twenty programs in Ubuntu with one commandWhat, ```
sudo fink install xxx etc
``` not good enough?

---

### Post by jerrylamos on 2007-05-12
From my very limited experience with Apple, it's great if you happen to conform to their idea of what you should be doing.  If you want to do something different, good luck.

What I like about Linux is being able to pick and choose, try different versions, upgrade, downgrade, different applications, the whole bit.  

There's one thing lately that Ubuntu is cramming down my throat whether I like it or not, and whether I wanted it or not, that's Network Manager.  Removing the Network Manager package doesn't even work, because it is active during boot whether you've removed the package or not, and what it does to me is disable the only working wired network connection during boot.  Every time.  Then after boot, I select it, select wired network, and after a few seconds comes right up.  Why couldn't it have either done that in the first place, or else not done anything??

Hopefully Ubuntu won't add too many more things in main line code and in main line boot that I have to have whether I want them or not.

Cheers, Jerry

---

### Post by Rhox on 2007-05-12
> I love the whole "well we got more resources now than in the 70's so lets waste them" argument. It's just great, why in the world would I run an OS that (even with Compiz) uses about 1% of my system resources when I can run Vista that will use 50% of them just idling? Maybe because I don't want my OS overtaking my system and instead actually use the damn applications. 
Actually that's a valid argument. A sometimes it isn't worth the effort to make it faster. Although that often isn't the case with OSs.

>  To make even more interesting, there is an initiative to create fully self contained applications, by that I mean that a package contains it's own OS that is stripped down to run just that application and uses a VM. Another funny thing is that with all the power and resources Java is still damn slow ;)
Theoretically that would be harder, slower, and take more memory.

---

### Post by aysiu on 2007-05-12
> **yoasif said:**
> What, ```
sudo fink install xxx etc
``` not good enough? Yes, not good enough because:
1. You have to really figure out how to install Fink first
2. The Fink repositories are limited and not updated very often
3. The Fink software is usually not Mac-native software

I did use Fink to install Gnocatan for her, and she liked that for a while, but figuring out how to make it a button on her Dock took me a while. It also takes a while to load, since it has to load X11 first.

---

### Post by yoasif on 2007-05-12
> **aysiu said:**
> Yes, not good enough because:
1. You have to really figure out how to install Fink first
2. The Fink repositories are limited and not updated very often
3. The Fink software is usually not Mac-native software

I did use Fink to install Gnocatan for her, and she liked that for a while, but figuring out how to make it a button on her Dock took me a while. It also takes a while to load, since it has to load X11 first.No need to figure out how to install Ubuntu, I suppose. 

The Ubuntu repos are also limited compared to debian, even. 

What constitutes "Mac Native"? It runs on Mac OS without emulation, I'd say it's "Mac Native"... 

Either way, if you had taken a few minutes to look around, you would have found "[App Update]("http://blog.gkaindl.com/downloads/app-update")" -- no, it's not "automated", but it works with any software on your machine, not just ones in the repositories. 

Mac OS X and Ubuntu are very different, and have their own advantages and disadvantages -- personally, I think Linux package managers are pretty bad, and that Mac OS has a pretty nice scheme for App installs.

---

### Post by aysiu on 2007-05-12
> **yoasif said:**
> No need to figure out how to install Ubuntu, I suppose.  Not if you buy it preinstalled. We aren't talking about installing the operating system. We're talking about installing programs. And I actually found Ubuntu easier to install than Fink, anyway, if you want to compare the two.

> The Ubuntu repos are also limited compared to debian, even. But not as limited as the Fink repositories.

> What constitutes "Mac Native"? It runs on Mac OS without emulation, I'd say it's "Mac Native"...  You're just arguing semantics. Call it whatever you want, but it's annoying to have to run X11 before running the program.

> Either way, if you had taken a few minutes to look around, you would have found "[App Update]("http://blog.gkaindl.com/downloads/app-update")" -- no, it's not "automated", but it works with any software on your machine, not just ones in the repositories.  Sorry I couldn't find that. Geez.

> Mac OS X and Ubuntu are very different, and have their own advantages and disadvantages -- I can agree with this. I don't appreciate Mac or Ubuntu bashing. > personally, I think Linux package managers are pretty bad, and that Mac OS has a pretty nice scheme for App installs. And personally I disagree.

---

### Post by yoasif on 2007-05-12
how is downloading a .deb file different from a .dmg?
after you download a .deb file, you might have to download a host of other dependencies -- this is a linux specific issue, obviously, but to the end user, i think mac os has a nicer scheme. 

not all software is in the repositories, just like how all software for mac os isn't necessarily listed on apple's web page. still, mac os makes it easy to back up applications, and install new ones. 

how easy is it to install the gimp .2 nowadays, if you aren't doing it from source? compare to running an old copy of a Mac app -- much simpler, and generally very feasible. even windows is generally better at this than linux is.

i guess my opinion is that the repository/package manager system is a nice workaround for the kludge of application install on linux, but it misses features that mac os x and windows have, even with the absence of this "nicety". the fact that windows and mac os get along fine without package managers really speaks more to the problem  of package management in linux -- although linux thankfully does it better than windows -- the registry sucks.

---

### Post by aysiu on 2007-05-12
Well, everything I need is in the repositories, so I much prefer that to tracking down a whole bunch of .dmg files, downloading them individually, clicking on them to get that white disk thingy, opening up the white disk thingy, dragging it to the Applications folder, closing the white disk thingy, ejecting the white disk thingy, and then trashing the .dmg file.

I guess it depends on the user and her needs, just like anything to do with computers.

---

### Post by Polygon on 2007-05-13
i dont know if someone has said this before in this topic, but if you copy something in like thunderbird, and then close thunderbird and try to paste it in firefox, it wont do it because i think linux "forgets" whats copied from a specific program once that program is closed for security reasons.


what mac does with its programs is pretty nice, how they are all included in one file and then you just have preferences in your home folder like linux does, and if i had a choice between windows traditional files all over the place, hope the un-installer program works and mac's .app's, i would choose the mac .app's. But with linux and synaptic, you dont even need that. you download a deb and it installs it and adds the entry, then you can update, remove and do other stuff for every program that is installed on your machine from one central place. No need for  one file applications when you can just do whatever with a right click in synaptic.

i have never experienced the thing where it says when a application gets upgraded,all of your config gets erased.

it says config files are placed in random places.... every config file ive ever had to edit has been under /home/mark/.(application name)

and isnt gconf (and whatever KDE has.... if it has something like that) what the guy is taling about with ascii xml files with key/pair values?

i kinda discredit this article with the fact that it was written two months ago and he doesn't even know about programs like synaptic, apt, rpm, etc.

---

### Post by aysiu on 2007-05-13
My wife's Powerbook just got foobarred. All her Adobe CS2 applications crashed upon launch. The error output was not helpful (Google searches on the error turned up nothing). Launching those applications from the terminal turned up nothing (no error in the terminal). I found that by launching CS2 apps in the Guest account that it wasn't a system-wide problem but a local user problem.

So I tried using Disk Utility to repair permissions. Still crashing. I tried renaming ~/Library/Application Support and ~/Library/Preferences, but it still kept crashing.

The only other thing I could think to do was create a new user account and migrate over all the important settings. That was a real pain and took me about three hours total, mainly because I had no idea where all the settings were *and* there was no equivalent of *gksudo nautilus* for Finder, so I had to do everything via the terminal. It would be nice if all the Mail settings were in ~/.mail and all the iPhoto settings were in ~/.iphoto, but that's not the case. I know in Ubuntu if I want to copy over my Firefox settings, they're all in ~/.mozilla. In Mac OS X, I had to track down some .plists, some Application Data folders, and then I had to keep doing ```
sudo chown -R username:username ~/folder/folder/folder
``` The whole process was really arduous and would have taken me less than half the time to do in Ubuntu.

I'm not bashing Mac OS X. I just hate it when people make it sound as if Mac is perfect. It's not. It's a piece of software, and it has problems just like any other piece of software.

---

### Post by yoasif on 2007-05-13
Some apps do save data in .dot folders in your home folder.

However, everything else is generally stored in ~/Library or ~/Documents.

The system is just as logical as Ubuntu's... you make it sound as if you were looking all over the place, outside of the home folder for all of this data -- just because Mac OS apps stores the data inside ~/Library instead of just ~ (inside folders like .iphoto) doesn't mean that it's worse -- just different. 

You did point out that you didn't know where to look, but is that really a reason to bash it? To a newbie, having the files in a visible folder like ~/Library is probably a lot more intuitive than not ever seeing the files at all, and having to dig into a "root" like view. 

As far as you needing superuser permissions to move some files over -- that's utterly hilarious -- you're complaining that by default both Nautilus nor the Finder show hidden files by default. This is not a permissions or "rights" issue at all, it's simply a UI issue. 

If you wanted to see hidden files in OS X or Nautilus, you could -- google for help with that (granted, it'd be nice to have an option to do that right in the Finder): here are some resources:

[http://www.macosxhints.com/article.php?story=20030409015020645](http://www.macosxhints.com/article.php?story=20030409015020645)
[http://kb.iu.edu/data/ajyj.html](http://kb.iu.edu/data/ajyj.html)

The first link is probably the most useful, since it makes it easy to toggle the viewing of hidden files. 

Also, there are plenty of Finder alternatives (just as there are alternatives for Nautilus) -- if you had looked around instead of simply assuming that it was "Mac OS X's fault" you might have found apps like mucommander and Path Finder, which would have solved your issue very easily (as would have showing hidden files in the Finder).

Your complaints with Mac OS X are really quite minor, and quite funny, especially since you are coming from a Linux background -- stop thinking that everything is the same -- or expecting it to be! Again, Mac OS X is different (I think it's better in some ways), so use it differently!

EDIT: As far as the issues that you were having with the Adobe CS2 apps -- why didn't you simply try removing the preferences for the applications? I'm sure a search for CS2 or Adobe or something similar (if necessary, see Adobe support or google) would have revealed them. Would you have immediately created a new user account and migrated settings over if ktorrent suddenly stopped working? Or would you simply delete ~/.ktorrent (not the right folder) and try it again?

---

### Post by aysiu on 2007-05-13
> **yoasif said:**
> 
However, everything else is generally stored in ~/Library or ~/Documents. ~/Library is a pretty big folder with a lot of different subfolders. I had to poke around quite a bit. And, as I said before, some configuration files are in ~/Library/Application Data; others are in ~/Library/Preferences. Some are .plists; others are actual folders. The .plists are standalone configuration files--not within the subfolder attached to the application folder's name.

> The system is just as logical as Ubuntu's... you make it sound as if you were looking all over the place, outside of the home folder for all of this data No, I was specifically looking in the /Users/username folder. As I'm trying to tell you, there are a lot of subfolders within ~/Library. >  -- just because Mac OS apps stores the data inside ~/Library instead of just ~ (inside folders like .iphoto) doesn't mean that it's worse -- just different.  ~/.nameofapplication holding everything for that application makes it pretty simple to move settings over. Having some of it in ~/Library/Application Data/nameofapplication, some of it in ~/Library/nameofapplication, and some of it in ~/Library/Preferences/nameofapplication, and some in ~/Library/Preferences/com.apple.nameofapplication.plist, makes the backing up process more complicated.

> You did point out that you didn't know where to look, but is that really a reason to bash it?  I didn't think I was bashing anything. I specifically said I just don't like people making it sound as if Mac OS X is perfect and has no problems. I have experienced problems in all the OSes I've used--Mac, Windows, and Ubuntu. Problems are a part of software. No software is perfect. Some people idolize Macs and make it sound as if having a Mac means never having computer problems. I'm just trying to say that hasn't been what I've seen. > To a newbie, having the files in a visible folder like ~/Library is probably a lot more intuitive than not ever seeing the files at all, and having to dig into a "root" like view. I don't see how this is relevant to the issue at hand.

> As far as you needing superuser permissions to move some files over -- that's utterly hilarious -- you're complaining that by default both Nautilus nor the Finder show hidden files by default. This is not a permissions or "rights" issue at all, it's simply a UI issue.  I don't see what hidden folders have to do with anything. If you're trying to move files, especially configuration files, from one user's folder to another user's folder through Finder, good luck. You won't even have permission to view certain folders, let alone move anything. That's why I had to use the terminal and *sudo* to move stuff over and then *chown* the folders afterwards.

> If you wanted to see hidden files in OS X or Nautilus, you could -- google for help with that (granted, it'd be nice to have an option to do that right in the Finder): here are some resources: I'm sorry, but when did I ever mention not being able to see hidden folders? You're getting overly defensive about an issue I didn't even bring up. I was talking about ```
gksudo nautilus
``` the ability to launch a file manager with root privileges within a user account, not the ability to view hidden folders, which you can easily do with Control-H in Ubuntu, but requires a cryptic command to do in Mac OS X (I Google the command when I need it).

> Also, there are plenty of Finder alternatives (just as there are alternatives for Nautilus) -- if you had looked around instead of simply assuming that it was "Mac OS X's fault" you might have found apps like mucommander and Path Finder, which would have solved your issue very easily (as would have showing hidden files in the Finder). So in order to fix my wife's computer, I have to "look around" for alternatives to Finder? Why?

> EDIT: As far as the issues that you were having with the Adobe CS2 apps -- why didn't you simply try removing the preferences for the applications? Why don't you re-read my post? That was one of the first things I did, and it made no difference.

You obviously didn't read what I wrote. Your eyes skimmed over my post, and you decided to "read" whatever you wanted to argue with and then start an argument over nothing. I didn't bash Mac OS X, didn't complain about hidden folders, and I did try what you think I didn't try.

Are you just a troll?

---

### Post by yoasif on 2007-05-13
You're the one that seems like a troll to me... you're complaining about things that are easily fixed, and aren't necessarily that different from your experience in Ubuntu.

You're pointing out these differences as if they are flaws in Mac OS X, when the same things are found in Ubuntu. 

as far as not being able to use the finder with superuser privs, I'll grant you, is an annoyance -- but one that is easily fixed. 

As far as you renaming the various folders within ~/Library --

a. that doesn't necessarily imply that you removed or made the adobe prefs take effect (i read your post correctly)
b. it doesn't sound as if adobe was looking in ~/Library, which sounds wrong, since it works in another user account.

So I would say that you probably overlooked something, or that the prefs were resident in memory (did you try logging in and out), or the application was simply looking for the presence of the prefs in the home folder -- which is something that adobe may be doing -- deleting the files is probably simpler and safer than renaming the folders that the prefs reside in...

EDIT: I found the repeated reference to "gksudo nautilus" annoying, since it may imply that mac os x doesn't have sudo -- which is obviously false. if you had simply pointed out that the Finder can be an annoyance to work with in superuser mode, that would be more accurate, and I wouldn't have bothered to respond (except to point out alternatives). 

and I'm not sure about nautilus, but i know you can install konqueror on OS X, so yes, it's entirely possible, just a bit of a hassle with the Finder.

---

### Post by aysiu on 2007-05-13
> **yoasif said:**
> You're the one that seems like a troll to me... you're complaining about things that are easily fixed, and aren't necessarily that different from your experience in Ubuntu. They're not easily fixed. How are they easily fixed? And I wasn't trying to say Ubuntu is perfect (though you appear to think Mac OS X is). My point was simply that *all* operating systems have their problems, and that includes Mac OS X. A lot of Mac OS X users seem to think it never has problems. It has problems, just like Ubuntu, just like Windows.

Noting that there are problems in all OSes is not trolling.

Picking arguments with people about points they didn't even make in the first place is trolling. Take a look--seriously.

You said I didn't even try getting rid of the configuration folders when I did.
You argued with me about hidden folders when I hadn't even brought hidden folders up in the first place.
And you said I was bashing OS X when all I said is that it's not perfect, just like all operating systems.

---

### Post by yoasif on 2007-05-13
> **aysiu said:**
> TYou said I didn't even try getting rid of the configuration folders when I did.
You argued with me about hidden folders when I hadn't even brought hidden folders up in the first place.
And you said I was bashing OS X when all I said is that it's not perfect, just like all operating systems.I didn't know that "renaming" meant "removing" -- wait, it doesn't. 
The hidden folders thing was a mistake on my part -- I misinterpreted what you were trying to do. 
As far as accusing you of bashing OS X -- no, I am not doing that, just saying that that is how it comes off, especially if you misrepresent what OS X can and cannot do -- see my edit to my previous post.

EDIT: just verified that I can install nautilus on OS X, so you can simply do: ```
gksu nautilus
```

---

### Post by argie on 2007-05-13
Quite a few applications I've used in the past come as a .bin installer and when they install (into the home directory) they have all their libraries in that folder (.so files?). I don't particularly like that way of doing it. The Package Manager I like very much. 

Polygon: I think I read somewhere that that is an unintentional effect, the clipboard thing, and has something to do with how X does clipboards, or doesn't. In any case, perhaps, Klipper or Glipper might help?

---

### Post by Polygon on 2007-05-13
asyiu, did you keep having to chown every single individual folder? if so, you could of made it a lot easier and done "chown -hR whatever whatever" which makes it be recursive and chown all of the subfiles as well.

and asyiu was complaining that you cant do something like "gksudo finder.app" to make it open a finder window with root privileges.

and i think the fact that it forgets what you copied is a feature (security reasons) but the issue at hand is that there is no standard for "the clipboard". something along the lines like copying some text in a kde program and then trying to paste it in a gnome application might not work very well. i might be wrong however

---

### Post by aysiu on 2007-05-13
I didn't chown every single subfolder. I chowned some parent folders I copied over but didn't want to do a chown on the entire ~/ just in case that screwed something up. Since things were already screwed up, I wanted to proceed with caution as much as possible.

---

### Post by picpak on 2007-05-13
> But an even bigger problem, the one thing that made me ditch Gentoo completely and get frequently very annoyed at Ubuntu, is the nightmare of application upgrades. If you have made any changes at all to an application's config data, and then you want to upgrade that app, you have three choices: (1) Keep the old config file, not benefitting from any new options or defaults provided by the upgrade; (2) use the new config file, tossing out all of your changes, requiring you to redo them all; or (3) go through a painful largely-manual merge process, often guessing about the meanings of any new options you find and whether or not your old change is appropriate for the new version. From first-hand experience, I can tell you that this is a very tedious and error-prone process that can leave applications completely broken. For instance, every minor KDE upgrade under Gentoo would leave me finding that some standard KDE app was completely missing, and no one in the Gentoo forums could help me figure out what happened. (And that was after manually sifting through a few hundred config files that were updated.)

Has he ever seen the hidden files in his home folder? He can just change the configuration through there. No messing with /etc, no messing up upgrades, just plain simple per-user configuration. Oh, and you can keep the configuration between different distros too (I did that with Arch and Ubuntu). Way better than what he's trying to do here.

I will agree with him on the clipboard though. I shouldn't have to keep track of two clipboards. I shouldn't have to leave a program open just to safely copy text and paste it into another one. The clipboard is such a total "just-do-it-and-forget-about-it" thing, it's confusing to be fully aware of it each time you copy and paste something.

---

### Post by prizrak on 2007-05-13
> **picpak said:**
> Has he ever seen the hidden files in his home folder? He can just change the configuration through there. No messing with /etc, no messing up upgrades, just plain simple per-user configuration. Oh, and you can keep the configuration between different distros too (I did that with Arch and Ubuntu). Way better than what he's trying to do here.

I will agree with him on the clipboard though. I shouldn't have to keep track of two clipboards. I shouldn't have to leave a program open just to safely copy text and paste it into another one. The clipboard is such a total "just-do-it-and-forget-about-it" thing, it's confusing to be fully aware of it each time you copy and paste something.
I'm pretty sure it changed in Gnome. Only works with GTK apps though, a QT app won't work with it.

---

### Post by 454redhawk on 2007-05-13
> **karellen said:**
>  I believe maybe one of linux's greatest strenghts and also greatest misunderstandings/fear-generator for new users it's the terminal/command line. simply speaking, a very powerful tool. If you are willing to learn how to use it. Or better explained, if you want to learn anything new. everybody can point-and-click


And thats why windows dominates the world of computers. Why would you WANT to make a tool for productivity harder than it has to be?

Linux has ZERO chance unless it learns from the strengths of windows (and there are alot of them)

---

### Post by aysiu on 2007-05-13
> **454redhawk said:**
> And thats why windows dominates the world of computers. No it's not. Read a book.

---

### Post by macogw on 2007-05-13
> **454redhawk said:**
> And thats why windows dominates the world of computers. Why would you WANT to make a tool for productivity harder than it has to be?

Linux has ZERO chance unless it learns from the strengths of windows (and there are alot of them)

HAHAHAHAHAHA

You're joking...right?  The GUI can do whatever you want in either of them.  The terminal beats Windows's command prompt hands-down though.  If I have the option of clicking through 10 menus or typing 2 commands, which am I picking?  Darned right I'm typing 2 commands.

---

### Post by 454redhawk on 2007-05-13
> **aysiu said:**
> No it's not. Read a book.

Come out of your cave and have a look around. Windows rules the world of computers. Its in almost EVERY home and office. 

This is NOT in dispute.

1% of computer users run linux.

8 to 10% a MAC

Take a guess what the rest use

---

### Post by aysiu on 2007-05-13
> **454redhawk said:**
> Come out of your cave and have a look around. Windows rules the world of computers. Its in almost EVERY home and office. 

This is NOT in dispute. You're right. Windows ruling the world of computers is not in dispute. That having anything to do with the terminal is.

---

### Post by 454redhawk on 2007-05-13
> **aysiu said:**
> You're right. Windows ruling the world of computers is not in dispute. That having anything to do with the terminal is.

The bottom line is...

The terminal HAS to be an option not a requirement. Linux will fail as a mainstream OS if this is not the end result. There is FAR too much interaction with the CLI for 99% of the users currently running a non linux OS.

Right or wrong, that is the way it is.

---

### Post by prizrak on 2007-05-14
> **454redhawk said:**
> Come out of your cave and have a look around. Windows rules the world of computers. Its in almost EVERY home and office. 

This is NOT in dispute.

1% of computer users run linux.

8 to 10% a MAC

Take a guess what the rest use

1) Linux has 3-6% of the DESKTOP market share depending on who is estimating as there are not many sales figures.
2) Mac has 6% market share that is a fact.
3) 49% of world's servers run Linux, not Windows. (In fact Windows doesn't even have the other 51% as alot of stuff still sits on UNIX or even NetWare).
4) 90% of supercomputers run Linux.
5) There are other OS's that run outside of the desktop realm and are quite plentiful. 

Bottom line: Windows dominates the world of DESKTOP but hardly close to dominating the computing world. 
> The bottom line is...

The terminal HAS to be an option not a requirement. Linux will fail as a mainstream OS if this is not the end result. There is FAR too much interaction with the CLI for 99% of the users currently running a non linux OS.

Right or wrong, that is the way it is.
1) It's wrong, I don't touch the CLI unless I want to right now. I had to use a bit of CLI when I was setting it up the first time. If I had bought a System 76 I wouldn't HAVE to touch CLI at all. CLI usage depends very heavily on use cases and individual needs, while one user may need CLI 50% of the time another might not touch it even once.
2) Windows has quite a few problems (one of which is actually lack of CLI, though that's mostly for IT people) that require learning something. You pretty much HAVE TO know how to battle viruses, spyware, file system fragmentation and junk cleanup if you want a Windows box to run decent in any way, or you bug someone to fix your comp once in a while. This doesn't seem to deter any of the so-called "average" users from using Windows. 

Bottom line:
Product success has little to do with quality and technical superiority/inferiority, it has ALOT to do with market forces. Basically any product has to meet a minimum quality/usability requirement and everything else is up to market forces. Think VHS vs BetaMax, the latter was a far superior product that had greater picture quality and smaller cassette size. The porn industry chose VHS and that became the standard. I could cite a million examples of an inferior product winning the market because of even a silly little fluke. 

I'll leave you with this though. When Apple had a GUI, color screens, sound, and multitasking, PC had DOS.... We both know how that ended.

---

### Post by Polygon on 2007-05-14
the terminal will never go away, but people dont have to use it. I mean if you just recieved a comp with ubuntu on it from like dell or whatever you wouldent have to use it. But when it comes to support, nothing is easier then copying a command that someone gives you and then opening the terminal, pasting it and hitting enter. a lot easier then "if you use gnome, go to system> prefs>network then click the "properties tab".... or if you use kde then go to whatever whatever knetworkmanager and click the "wireless tab".... etc etc

---

### Post by 454redhawk on 2007-05-14
> **prizrak said:**
> 1)  I don't touch the CLI unless I want to right now. I had to use a bit of CLI when I was setting it up the first time. 

A VAST amount of questions and answers here involve the CLI to accomplish what the user is trying to do. The examples are almost endless. No matter if its a little bit at the start of an install or not. The amount of interaction with the CLI is staggering to the new / non tech/geek user (read that most users). They dont want to do it and they should not have to either.

I am simply saying that its a problem if linux is to be taken seriously as a mainstream OS.

---

### Post by prizrak on 2007-05-14
> **454redhawk said:**
> A VAST amount of questions and answers here involve the CLI to accomplish what the user is trying to do. The examples are almost endless. No matter if its a little bit at the start of an install or not. The amount of interaction with the CLI is staggering to the new / non tech/geek user (read that most users). They dont want to do it and they should not have to either.

I am simply saying that its a problem if linux is to be taken seriously as a mainstream OS.

Thanks for only pasting a part of what I said. 
1) This is a support forum and in many cases the system might be dead to the point of not being able to do anything in GUI. Windows and OS X get to that point as well and just as easily/hard. The only difference is that in Windows your only cure is to reinstall (by the way the recovery console that is used to fix a borked Windows install is also CLI). 
2) Just because you are given CLI directions doesn't mean it's impossible to do it in GUI. For instance if you are told to ```
sudo apt-get install epiphany-browser
``` doesn't mean you can't open Adept/Synaptic and do it in GUI. The problem however is that the CLI way will work in Ubuntu/Kubuntu/Edubuntu/Xubuntu without a hitch. If you make a GUI tutorial it needs to have screenshots and be remade for every DE. 
3) Probably 80-90% of problems posted here that require tweaking are hardware related. Basically it stems from the fact that alot of us install Ubuntu onto something that was designed for Windows. With Dell rolling out the preinstall those issues will be taken care of. 

There is no need to use a CLI in Ubuntu for everyday "average" user tasks. It's all very individual there is a good number of people out there that wouldn't have to touch CLI ever if Ubuntu was set up for them by someone else (you know like Windows/OS X is). Now I'm not saying that Linux is gonna be 90% of the desktop market soon or ever really. However it can grab a decent enough 15-30% of users. That would be more than enough to:
a) Provide a real choice to people, since let's face it while OS X is pretty good it comes with a heavy price.
b) Get ISV's and OEM's to pay attention to Linux and actually keep it in mind when designing something.

---

### Post by tuatha1337 on 2007-05-15
Speaking as a completely new Linux user, I can safely say that it has not been an "easy" transition from the familiarity of Windows. In fact, I know absolutely nothing about the fundamentals of command line beyond copying and pasting other people's commands. I would dearly like to learn, but finding the a comprehensive and understandable resource from which to learn is proving difficult. 

Getting the "standard" media files to play is confusing, especially when deciding whether to get a potentially illegal codec from the universe repository, which in itself is an adventure to learn about, or to get a mp3 to ogg converter which will degrade the quality of the file. Then learning that it is actually best *not* to download programs from the internet and keep them in a central location, and rather to use the Synaptic package manager for program needs. This lack of central location is only a problem when trying to figure out the workings of the system or to locate a specific program for trouble shooting or alterations. 

This isn't to say that I'm not happy that I learned that mp3 is a proprietary software with all manners of legal issues to deal with, or that ogg vorbis is a "better" format in that it provides higher quality sound with less disc space. Among all the other experiences with Ubuntu that I've had. 

Also, the support is phenomenal. I have never before seen so many people willing to help me through seemingly simple problems. Windows and Mac can't stand up to the kind of technical support and knowledge brought by this community. You guys actually want to help me, are not payed for it, and are not required to respond to any number of rules and regulations regarding the political correctness of the information you give out. 

The problem with desktop Linux is that it's so hard to learn how to use it when the market is dominated by Windows. Most users don't *truly* know how to use their own Windows, even with Windows' "easy-to-use" GUI. They *could* do this for Linux, but since Linux is not the dominant operating system, people will judge Linux against Windows or Macintosh and find faults when something is different, and thus more difficult for them due to the learning curve. It is exactly the same for someone transferring from Windows to Macintosh, or vice versa. The major difference is the configuration of the system and the availability of the Terminal, which need only be used when the average user needs "tech support", for which they need only ask the community. 

I do believe that Linux *can* be learned by the average user, but the time and effort required to  overcome the learning curve is too much for many. I am loath to admit this, but Linux was somewhat forced on my because Windows refused to recognize it's own activation code anymore and I hadn't the money nor patience for a new Windows OS. Still, I'm happy with it, even if it doesn't have drivers for my X-Fi sound card. 

Linux has the hurdle set by the popularity of Windows and Macintosh to leap over before it ever gets on its way to *complete* home usability.

---

### Post by 3rdalbum on 2007-05-15
I've heard this "ordinary users will use Windows simply because it doesn't need a command line" argument so many times. I'm thinking of adding it to my list of "Ridiculous reasons why Linux isn't ready for the desktop" on my blog.

Think back to the 1980s and early 1990s. There were three operating systems in use on desktops: Mac OS Classic, DOS and Windows 3.1/95.

Of these, Mac OS Classic was the only completely-GUI operating system, without a command-line. The other two were totally command-line, or were GUI but required users to learn commands in order to setup the system and programs.

Of these, Mac OS Classic had the smallest install base. Yes, more people ran DOS on desktops than ran Mac.

So don't give us that twaddle about "People will always choose Windows because it doesn't have a command line". It's a good idea to reduce the dependence on the CLI, as it's not an intuitive interface, but quit with the FUD already.

---

### Post by brim4brim on 2007-05-15
I installed Ubuntu on my fathers old work machine (he's retired).  I told him there was a Sudoku game on it and he wanted to print one off but he said he wanted to try on his own first.

So he clicked Applications because he wanted to start an application, then games because it was a game and then sudoku.  I can't think of anything more intuitive.

Its certainly more intuitive than Start, programs, whereever the hell it might have ended up, generally company name, game, exe file.

Ubuntu's way is more intuitive and cleaner as it lacks uninstall etc.. in the menu system too.

> **454redhawk said:**
> A VAST amount of questions and answers here involve the CLI to accomplish what the user is trying to do. The examples are almost endless. No matter if its a little bit at the start of an install or not. The amount of interaction with the CLI is staggering to the new / non tech/geek user (read that most users). They dont want to do it and they should not have to either.

I am simply saying that its a problem if linux is to be taken seriously as a mainstream OS.

CLI is easier than telling someone where to navigate with a window.  It is faster and easier to use CLI for support on a forum.  If the user really wants, they can pay for support and I'm sure that they can get them to talk them through doing it through a User Interface.

---

### Post by GSF1200S on 2007-05-20
> **yoasif said:**
> how is downloading a .deb file different from a .dmg?
after you download a .deb file, you might have to download a host of other dependencies -- this is a linux specific issue, obviously, but to the end user, i think mac os has a nicer scheme. 

not all software is in the repositories, just like how all software for mac os isn't necessarily listed on apple's web page. still, mac os makes it easy to back up applications, and install new ones. 

how easy is it to install the gimp .2 nowadays, if you aren't doing it from source? compare to running an old copy of a Mac app -- much simpler, and generally very feasible. even windows is generally better at this than linux is.

i guess my opinion is that the repository/package manager system is a nice workaround for the kludge of application install on linux, but it misses features that mac os x and windows have, even with the absence of this "nicety". the fact that windows and mac os get along fine without package managers really speaks more to the problem  of package management in linux -- although linux thankfully does it better than windows -- the registry sucks.

Not to be a jerk, but what would you propose we do instead? Do away with the repos and install every thing by .deb/.rpm packages? The only disadvantage to Linux is that all the files are scattered, but even source installs can be uninstalled if you use -checkinstall. The repos are the perfect solution to an open source system. I can BROWSE for applications, versus having to find out if a certain application exists via the net. Its almost the ultimate file system. 

MacOSX and windows dont need package managers because you BUY OR FIND applications for them on the net or in a store. Linux does because apps arent in stores, theyre on the net and not widely spoken of. 

Windows has more issues than Linux: not only does it have the god awful registry (I AGREE with you here), but unless youre fairly technical oriented, not much can be done with the files you have access to via program files. Virtually every aspect can be modified with Linux's plain text approach, as well as MacOSX's approach (im not overly familar here). 

If Linux were more popular, im sure binaries would be very capable of installing things the same way everyones used to on windows or macosx. 

How hard is stuff to install really? I mean, its not that hard. And if a person took a half hour once a day for a little while to study the unix filesystem structure, it would make sense just as much as a central approach. Its like "I wanna change firefox." Some people would think "Find firefox folder for config" (MacOSX, Windows), while others would think "Find config folder and then Firefox's config." (Linux)  6 eggs, half a dozen.. its all based on what one is used too.. And im relatively new to linux, so im not really inclined to blindly defend it.

---

### Post by tehkain on 2007-05-20
> **GSF1200S said:**
> Lots of words

I agree on most things. Has anyone ever compiled something for windows? No? So why do they expect it to be easy on linux. If you can not get an EXE or MSI on windows you wont install the app. If you can't get a deb or a repo on ubuntu then you can't install the app. The mentality is the same... but the vast number of linux apps, big and small, that are source only seem to make these people think that its 'hard to install anything'. 


So is installing things on linux harder then windows? No it is not. If you can not get it in Deb form or from the repo then it is no different from windows. You(a hypothetical person) do not complain about compiling on windows or OSX but you complain here. Its stupid.

---

### Post by mech7 on 2007-05-20
> **tehkain said:**
> You(a hypothetical person) do not complain about compiling on windows or OSX but you complain here. Its stupid.

That is because on windows there is never a need to compile a program when you want to install it, unless you are a programmer perhaps. In linux there is often a need to compile it because many times when a program is new there is no .deb for it.

Also uninstalling is allot harder, things that you don't install from the repository don't end up in add / remove programs. Now that is confusing!

---

### Post by jariku on 2007-05-20
> **mech7 said:**
> That is because on windows there is never a need to compile a program when you want to install it, unless you are a programmer perhaps. In linux there is often a need to compile it because many times when a program is new there is no .deb for it.

Also uninstalling is allot harder, things that you don't install from the repository don't end up in add / remove programs. Now that is confusing!

These problems go away if you use checkinstall to create a .deb instead of using make install after you've compiled the source code.

---

### Post by prizrak on 2007-05-20
> **mech7 said:**
> That is because on windows there is never a need to compile a program when you want to install it, unless you are a programmer perhaps. In linux there is often a need to compile it because many times when a program is new there is no .deb for it.

Also uninstalling is allot harder, things that you don't install from the repository don't end up in add / remove programs. Now that is confusing!

Often? I've been on and off Linux for about 6 years and fulltime on Ubuntu for 2+ years. I've had to compile one or two programs. If you use a .deb or checkinstall you can uninstall using Synaptic (not sure if Add/Remove would show them). It's still graphical and even has a search function.

---

### Post by aysiu on 2007-05-20
I've *never* had to compile a program in Linux.

---

### Post by GSF1200S on 2007-05-20
> **aysiu said:**
> I've *never* had to compile a program in Linux.

Holy crap! Are you serious?! Ive been using Linux for like 3 months and ive had to compile a number of things.

Its cool; it satisfies my geeky side. You dont know what youre missing ;)

---

### Post by aysiu on 2007-05-20
I'm totally serious. I've been using Linux for two months. Never had to compile a program.

All my hardware has been recognized (I did have to edit a config file, though--/etc/X11/xorg.conf--to get my screen resolution optimal), but I've never had to compile software. The repositories more than suit my computing needs.

---

### Post by mech7 on 2007-05-20
yeah i suppose when you use the puter for just browsing the web and emaling and such there is no need to compile but if you want to go a little further then that you are bound to get stuck.

---

### Post by GSF1200S on 2007-05-20
> **aysiu said:**
> I'm totally serious. I've been using Linux for two months. Never had to compile a program.

All my hardware has been recognized (I did have to edit a config file, though--/etc/X11/xorg.conf--to get my screen resolution optimal), but I've never had to compile software. The repositories more than suit my computing needs.

A testament to how far Ubuntu has come... 

I guess this kind of on subject- is it ever really a bad thing if Linux isnt the dominant OS? Its been my experience that once something gets 'big' it gets corrupted both physically and philosophically, and that would suck for Linux. Hell, id be happy if Linux just took a large enough share to receive more corporate support SHOULD WE WANT OR NEED IT... Everyone seems concerned with it burying windows- do we want Linux to become windows?

Are there any provisions in the licensing of Linux to prevent a company from "copyrighting" Linux to the point of where open source isnt possible, rather controlled by some corporation? I would guess not since Novell hasnt done anything of the sort.

---

### Post by jiminycricket on 2007-05-20
Forking will always be possible in open source and free software: for example, XFree86 changed its licensing terms in 2002, and contributors forked the last version with the (acceptable) MIT license to what we now know as Xorg.  In particular, the GPL covers patents, so that a distribution could not be too big and suddenly be bereft of the community.

I guess XFree86 did copyright assignment, as do the FSF and some other projects.  Others have virtually no chance of changing license (especially if they move the GPL "any later version") because the copyright is held by thousands of disparate people.

There were many initiatives in the 90s (GNOME and Harmony) to prevent exactly the sort of situation you describe, because then QT, which the leading DE KDE used, wasn't free software.

---

### Post by prizrak on 2007-05-20
> **aysiu said:**
> I'm totally serious. I've been using Linux for two months. Never had to compile a program.

All my hardware has been recognized (I did have to edit a config file, though--/etc/X11/xorg.conf--to get my screen resolution optimal), but I've never had to compile software. The repositories more than suit my computing needs.

Don't you mean two years? I'm pretty sure you were on the forum before I joined ;)
>  	yeah i suppose when you use the puter for just browsing the web and emaling and such there is no need to compile but if you want to go a little further then that you are bound to get stuck.
I do a fair bit of programming (Java, Perl, C++) and haven't had to compile anything other than what I wrote :)

---

### Post by GSF1200S on 2007-05-20
> **prizrak said:**
> Don't you mean two years? I'm pretty sure you were on the forum before I joined ;)

I do a fair bit of programming (Java, Perl, C++) and haven't had to compile anything other than what I wrote :)

Haha, yeah, I kind of assumed he meant 2 years... He knows way to much to have only been using Linux 2 months. :)

---

### Post by tehkain on 2007-05-20
> **mech7 said:**
> That is because on windows there is never a need to compile a program when you want to install it, unless you are a programmer perhaps. In linux there is often a need to compile it because many times when a program is new there is no .deb for it.
If the app is not open and is not available as an installer you have to compile. In windows did you deal with 95% open sources software? No you did not. I had to install many apps on windows that were source only. So I've compiled a bit on windows.

> **mech7 said:**
> Also uninstalling is allot harder, things that you don't install from the repository don't end up in add / remove programs. Now that is confusing! No they are in synaptic. Add/Remove is for specific programs. Most things in the repos do not show up in ADD/Remove(as they should).

> **GSF1200S said:**
> Haha, yeah, I kind of assumed he meant 2 years... He knows way to much to have only been using Linux 2 months. :)

Yea I paused for a second when I read that. I was like "Didnt I see you post back in 2005/6?"

---

### Post by aysiu on 2007-05-20
Whoops--that was a mistype. It's been two years.

---

### Post by mech7 on 2007-05-20
> **tehkain said:**
> = No they are in synaptic. Add/Remove is for specific programs. Most things in the repos do not show up in ADD/Remove(as they should).


Like i said it is confusing especially when you push Add / Remove programs in the front of the menu and hide Synaptic in the back.

---

