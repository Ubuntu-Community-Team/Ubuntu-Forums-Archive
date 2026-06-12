---
title: "Linux distributors unite on desktop standard"
date: 2006-04-22
forum: The Cafe
---

### Post by YourSurrogateGod on 2006-04-22
> NEW YORK - In a move to make the freely distributed Linux operating system a stronger alternative to Microsoft Corp.'s Windows, a group of major Linux distributors announced Friday they have united on a standard set of components for desktop versions of Linux.

-snip-

"One of the big things that's difficult is consistency, and that's Window's biggest strength," said Jim Zemlin, executive director of the Free Standards Group. (MSNBC.com is a Microsoft - NBC joint venture.)

If you buy a Windows program, you know it will run on a Windows computer, and Linux needs to work the same way, Zemlin said. 

-snip-

[http://www.msnbc.msn.com/id/12424790/](http://www.msnbc.msn.com/id/12424790/)

'bout damn time.

---

### Post by aysiu on 2006-04-22
Yeah, I read about that yesterday, and I wasn't sure exactly what that means. Does it mean a binary compiled for Ubuntu would work on Fedora as well...?

---

### Post by viciouslime on 2006-04-22
WOW, that's great news! Maybe linux will finally get a hold in the desktop market too, afterall that's got to be the biggest problem for linux users at the moment, installation of software.

I can see it now, no more This product requires Windows 9x/ME/2000/XP but instead this product requires LSB 3.1 or greater....yay!:-D :-D :-D

---

### Post by YourSurrogateGod on 2006-04-22
[QUOTE=aysiu]Yeah, I read about that yesterday, and I wasn't sure exactly what that means. Does it mean a binary compiled for Ubuntu would work on Fedora as well...?[/QUOTE]
Now that you mention it, that's a good point... I don't know.

---

### Post by mostwanted on 2006-04-22
[QUOTE=aysiu]Yeah, I read about that yesterday, and I wasn't sure exactly what that means. Does it mean a binary compiled for Ubuntu would work on Fedora as well...?[/QUOTE]

They should already? The differences are in file tree layout and so on, otherwise x86 is x86 and ppc is ppc no matter the distro.

---

### Post by YourSurrogateGod on 2006-04-22
[QUOTE=viciouslime]WOW, that's great news! Maybe linux will finally get a hold in the desktop market too, afterall that's got to be the biggest problem for linux users at the moment, installation of software.

I can see it now, no more This product requires Windows 9x/ME/2000/XP but instead this product requires LSB 3.1 or greater....yay!:-D :-D :-D[/QUOTE]
I think that's a tad overambitious.

More realistically, it'll mean that more people will write programs for Linux operating systems. Now you won't have to be an expert in order to make that program run well across different distros.

Also, this action that is being undertaken by the different distros is to be expected as Linux the OS evolves, I welcome it.

---

### Post by helpme on 2006-04-22
[QUOTE=aysiu]Yeah, I read about that yesterday, and I wasn't sure exactly what that means. Does it mean a binary compiled for Ubuntu would work on Fedora as well...?[/QUOTE]
Yes and no.
If I understand it correctly, what this means is that now developers, software companies can build software for the LSB3.1 and that this software will then run on any distribution that is LSB3.1 compliant.
So for example, someone who develops a tax software now just has to make sure it runs on LSB3.1 compliant distros and can be sure that his software will ran on all compliant distros.

---

### Post by BoyOfDestiny on 2006-04-22
[QUOTE=YourSurrogateGod]I think that's a tad overambitious.

More realistically, it'll mean that more people will write programs for Linux operating systems. Now you won't have to be an expert in order to make that program run well across different distros.

Also, this action that is being undertaken by the different distros is to be expected as Linux the OS evolves, I welcome it.[/QUOTE]

Hmm, I just hope it's not excessive. I'd like if they standardized where things are, like for /etc, /usr/lib/, and the like. Not that I'd ever switch from Ubuntu, but it's nice when things are in the same place.

As for compatibility, nothing beats source. Besides 1 app that requires assembly, I've been able to compile software for ubuntu 32 or 64. Handy for when it's not in the repo...

Some binaries I've tried that people built on Fedora worked on my Ubuntu boxes... I'd imagine they wouldn't run if I didn't already have the dependency's...

How far does the LSB go, since I think the kernel changes sometimes break things in user space...

---

### Post by Mathias-K on 2006-04-22
I think this is a matter of huge importance. I'm looking forward to the day i can buy a computer game from a Linux friendly publisher such as ID Software and just run the damn thing out of the box.

---

### Post by harisund on 2006-04-22
People, here's my 2 cents on what a "standard base" should mean. 

First, yes, package installation. I go to a website, it says "For Windows use name.exe, for Debian and Debian based systems, use name.deb, for Red Hat and Red Hat based systems use name.rpm, for so and so, use name.soso and if you want to configure from source use name.tar.gz, but make sure you have libwhatever.so, libwhocares.so, libannoying.so" 

If you want to know what I am talking about, go here [http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/) And the worst part is there are no instructions on installing it on debian based systems. 

This is a strict no no. Just like in Windows, it should say "For Linux use this: name.lexe" or any common extension, so people can be taught .exe for Windows, .dmg for Mac, and .something for Linux. 

Then, I download it, double  click on that file, and it installs. No terminal, no unmet dependancies, no package warnings, nothing. Just like in Windows. Plain, simple double click. 

Don't get me wrong, the repository thing is awesome too. But seriously, does anybody even know half the softwares in the repository? I have all sorts of repos in my sources.list, and when I open Synaptic it simply freezes for a while before it makes its entire list and shows me. There must be something done about this. 

Next, after I install a program, it should turn up in the start menu. Or whatever is the equivalent. Gnome's menu. KDE's menu. Whatever. The user should know what to click to start the program. I am used to going to Start Menu ->Programs and finding what I just installed. Can I do that on Linux? Always? 

Another issue: choices. Yes, Linux / Open Source is all about choices, and you can have tons of them. But seriously, I don't need Bash, Ash, tcsh, zsh and cash ( :) now that would be nice ) on my system. Similarly, standardize on OSS or Alsa, or ask the user "Use OSS or Alsa (If you don't know what that just meant, just use the default"), standarize on Firefox. Don't give the user a menu saying Browser: and then offer Konqueror, Epiphany, w3m, lynx, Firefox, something_you_built, something_I_built. Who cares? I jsut want a browser that works. Simple.

A center control panel. KDE does a good job on this. Whatever configuration and tweaking I want to do in Windows, Control Panel is my one stop shop. Gnome has a control panel, but I don't want to go through individual menus for that. 

Outside of the LSB, hardware and vendor support. This can only come with time, and I am sure once a LSB is established, vendors will see the need to provide drivers and what not. 

The terminal. Yes, even though users shouldn't be exposed to the terminal unless absolutely necessary, you can't deny, the terminal is the heart of any Linux. Absolutely anything can be done through this baby. Have it somewhere prominent. On the desktop create a "My Computer", "My Recycle bin" and "my terminal" icon. A user reads on a wiki "execute sudo iwconfig wlan0..." and they are lost right there. 

External support. In Windows, I can call for remote desktop support. Similarly, I should be able to call for, I believe an SSH support. Windows has an awesome feature called "Call for Remote Assistance." Of course, we don't have paid people to do the job, but I am sure thre are people who would volunteer to do such a thing at some times. Just like an IRC channel. My mom doesn't need an SSH server on all the time, but if something gets broken she should be able to call me for a troubleshoot, and a SSH server should termporarily get started, log me in, and stopped after I log out. People like it when they know they have somebody to support.

Concept of sudo. User's shouldn't be allowed to install programs, and when they download a .lexe file and run it, it should ask for root permission. Or even better get installed for that user alone, and not affect general user space. Most home user's don't have multiple accounts, and disk space shouldn't be a problem. 

Mounting CDs. Why on earth should I mount a CD with the -exec option to be able to execute binaries? What sort of a clown came up with that idea? First, you ask me to use exec. Then again, you ask me to use sudo. Isn't this getting sort of paranoid? 

Audio, Video, Codecs, DVD. Please get something done people. After an install, show a message "You just installed a free OS and you get only free stuff. You want proprietary stuff?" and then either "Here is what you do... " or "Get lost. You want free stuff, you get only free stuff." Automatix, Easy Ubuntu, Easy Fedora whatever. Show the user it needs to be done and get it done. 

Flame wars. Stop having them. I am getting tired of 1337 users debating on Kde/Gnome, Vi/Emacs, sendmail/fetchmail, linux kernel/bsd kernel. They scare regular users. And most importantly, Linux users should stop trashing Windows. Calling Windows as "WinDoze" or "WinBlows" simply shows arrogance on Linux user's part. I understand Linux is way more powerful, easier, safer and what not. I know, I use LInux too. But that doesn't mean Windows and its user gets the trash talk. 


Maybe there are more, but these are certainly some stuff that would help in moving towards a standard Linux base.

---

### Post by aysiu on 2006-04-22
[QUOTE=mostwanted]They should already? The differences are in file tree layout and so on, otherwise x86 is x86 and ppc is ppc no matter the distro.[/QUOTE] I don't know all the technical details, but if they already have binary compatibility, what is Poofyhairyguy talking about in [this thread?](http://www.ubuntuforums.org/showthread.php?t=54227) [quote=Poofyhairyguy]I see you don't get it. Let me say it in a certain way:

Linux Distros (as a group) are not compatible with binary compatibility.

We don't not want what you want because we are mean, stupid, or uncaring. We (as in the people that understand how the Gnu operating system works) know that its an impossible dream. Its because of the way Linux is. Its because of the way distros are made. Its because of how different each Linux is. Its because its too hard.

I talk to people like you all the time that can't grok it. Here is your problem: you hear about all the distros (using a version of the Linux kernel) and you hear "many types of one operating system." That is not the case. Each one is their own OS. Some versions of Linux are closer to BSD than all the other versions of Linux (Gentoo). Some are closer to Windows (xandros) than to other Linuxs. The diversity within the distro community is great.

Nothing can bring it together. There is no unifying force...or a common thread (they all use different kernels even many times). There is nothing like that.

Ubuntu is its own OS. Mandriva is its own OS. SuSe is its own OS. It might be confusing since all have very similar apps and a similar feel, but they are all essentially different. They only way something will work on all of them is the most primative of all software packages (the tar file) because by compiling it on your system you are making it compatible with the OS you have. Thats how even BSDs can install Linux tar files.

What you want is the Windows model in Linux. We don't not want it because Windows does it or something- its just that Linux lacks major qualities of Windows. On Windows EVERYONE uses the same kernel. EVERYONE has IE (in some form). EVERYONE has _____ .dlls in the system folder by default. Same thing applies for OSX. This does not apply to Linux. That is why the ways both OSes install apps won't work in Linux.

Ubuntu is a seperate OS based on the seperate Debian OS. Ubuntu software (aka what is comparible to OSX software or Windows software) is only installed through synaptic. If we get big, developers will make Ubuntu packages. Our deb is the equivelent of the exe. There will NEVER be a Linux exe that will work as good as that deb.

If what I am telling you disappoints you, then get in there and change it. Find a new way. Develop something new. Autopackage is not the answer. Its a kludge. There is only a few installers that truely work across all Linuxs (XFCE , Nvidia's) and all of those compile the app or module needed on the users computer. If you are not a developer, either deal with it (I have) or buy Windows or buy a Mac. There isn't another option.

Binary compatiblity won't come. Magic does not exist in the real world.[/quote]

---

### Post by zerhacke on 2006-04-22
[QUOTE=helpme]Yes and no.
If I understand it correctly, what this means is that now developers, software companies can build software for the LSB3.1 and that this software will then run on any distribution that is LSB3.1 compliant.[/QUOTE]
Call me ignorant.  I do not know what LSB3.1 is.  Is it more rehashing of the POSIX standard?  What is the difference between POSIX and LSB3.1?

---

### Post by helpme on 2006-04-22
[QUOTE=zerhacke]Call me ignorant.  I do not know what LSB3.1 is.  Is it more rehashing of the POSIX standard?  What is the difference between POSIX and LSB3.1?[/QUOTE]
I'm not really an expert, but I think POSIX focuses on the api level, whereas the LSB clearly works towards binary compatability. If I'm way off base here, someone correct me please.

> What is the LSB Project?

The goal of the LSB is to develop and promote a set of binary standards that will increase compatibility among Linux systems (and other similar systems), and enable software applications to run on any conforming system. In addition, the LSB will help coordinate efforts to recruit software vendors to port and write products for such systems. 
[linuxbase]("http://www.linuxbase.org/modules.php?name=FAQ&myfaq=yes&id_cat=1&categories=General+Info#17")

@aysiu:
No, we don't have binary compatability as this means a lot more than merely the architecture of the processor. For example you still have to make sure the libraries needed are available and installed.
That said, reading the thread you are referring, I get the impression poofyhairyguys point has been refuted more than enough there already. No need to bring it up again, he simply was wrong.

---

### Post by mostwanted on 2006-04-22
[QUOTE=aysiu]I don't know all the technical details, but if they already have binary compatibility, what is Poofyhairyguy talking about in [this thread?](http://www.ubuntuforums.org/showthread.php?t=54227)[/QUOTE]

I think he's talking about the patches different vendors put on some apps, the use of different ABIs between compilers and the fact that Linux is not bound to just one processor architecture. All these things make sure that binary compatibility is not viable on Linux, but it is *doable* to some degree.

On Ubuntu, using RPMs is possible, using Debian packages (from the Debian repositories) is possible, using the standard precompiled binary for Firefox is possible, but there's bound to be some problems involved with some apps.

---

### Post by prizrak on 2006-04-22
From the article it would seem that LSB is nothing but a specification for what libraries would have to be installed in the distro and where to find them. It is possible that it would make the filesystem layout the same across certified distros. Yes it does mean binary compatibility across distros, I have been able to install .rpm's just fine with alien if I had all the libraries available on my system. 
To the point of installing applications for just one user, it is possible but hardly prudent/necessary. It isn't difficult to put your password in once to make the software install and then it is available for all users that you may ever create on your system. Making software install for individual users would mean different versions for corporate and home users that would have different installers. Asking for the password is also a very good way to indicate to the user that he/she is doing something to the system that is beyond normal usage. 
I do think that a more common GUI system might benefit wide adoption, I know that no one will ever stand for that of course :)
LSB seems like a good idea though, and I hope that more distros go that way. What I wonder though is will it specify which kernel to use for the system and how to deal with upgrades. I do believe that all libraries and kernels are backwards compatible though.

---

### Post by Kimm on 2006-04-22
> 
@aysiu:
No, we don't have binary compatability as this means a lot more than merely the architecture of the processor. For example **you still have to make sure the libraries needed are available and installed.**
That said, reading the thread you are referring, I get the impression poofyhairyguys point has been refuted more than enough there already. No need to bring it up again, he simply was wrong.


That has nothing to do with Binary compatability, after all, if you have a library missing in windows the app that needs it will not run, but the binary is still compatable with windows.
Strictly speaking, a Linux binary will allways be a Linux binary, no mather what system you put it on, the library is just a requirement that the program needs to run, if the app would have every dependency staticly linked to it, it would run on every (non outdated) version of Linux, as long as the architecture is right.

---

### Post by helpme on 2006-04-22
[QUOTE=Kimm]That has nothing to do with Binary compatability, after all, if you have a library missing in windows the app that needs it will not run, but the binary is still compatable with windows.
[/QUOTE]
That's why I mentioned availability.
If a library or the version that is needed by the program you want to install is not available for your distro, have fun getting the program to run.

---

### Post by aysiu on 2006-04-22
So ... not being that knowledgeable about binary compatibility, libraries, and whatnot...

can someone please explain to me the practical ramifications of this "desktop standard"?

---

### Post by catlett on 2006-04-22
I don't have anything to add because I do not know anything about the subject, but here is the link to the Free Stangards Group. [http://www.freestandards.org/](http://www.freestandards.org/) They have a link to there whitepaper which is interesting.I'll get out of your way now. Thanks for the original post and link. It's my intellectual stimulus for the evening.

---

### Post by prizrak on 2006-04-22
[QUOTE=aysiu]So ... not being that knowledgeable about binary compatibility, libraries, and whatnot...

can someone please explain to me the practical ramifications of this "desktop standard"?[/QUOTE]
I'll take a stab at it. 
Withouht LSB
Say you are using Ubuntu Breezy and you have ubuntulib2.4. And lets say that I run Fedora Core 5 that uses fedoralib2.6 for the same thing. Now the libraries maybe completely identical save for the name. So lets say you are trying to install [Keepass Password Manager]("http://keepass.berlios.de/")(good program btw I recommend it) and that program requires fedoralib2.6 to function. If you install it on Ubuntu it will not find the needed library and not work. 
With LSB
Same scenario, only now both you and me will have a library called userlib2.5 and Keepass that is created to work on LSB will now need userlib2.5 enabling it to work on both Fedora and Ubuntu transparently. 
So in other words instead of the dowload section of websites saying something like
Mandriva Linux 10.2 package
Debian package
Fedora Core 5 package 
It will say:
LSB 3.1 or later compatible.

---

### Post by ade234uk on 2006-04-23
If we get a bit of unifomity then 3rd parties may show some interest. I would really love the day to be able to go out and buy a game that runs on Linux and know that it will just run on whatever distro I choose to run it from.

Obviously what we must not lose is this community friendly spirit. There will be :evil: :twisted: people out there that will only look at the money and not care for Linux roots.

---

### Post by GeneralZod on 2006-04-23
[QUOTE=ade234uk]If we get a bit of unifomity then 3rd parties may show some interest. I would really love the day to be able to go out and buy a game that runs on Linux and know that it will just run on whatever distro I choose to run it from.
[/QUOTE]

I've tried the same (untouched) install of UT04 across Mandrake 10, 10.1, Gentoo, Kubuntu 5.04 and Kubuntu 5.10 and it has always Just Worked immediately as soon as the nvidia drivers were installed.  The only exception was 5.10, when I had to install libstdc++5.0 first.

I think we've been at the stage for quite a while now where *games* manufacturers can issue a version that installs across all distros, but none of them are taking advantage of it.

---

### Post by prizrak on 2006-04-23
[QUOTE=GeneralZod]I've tried the same (untouched) install of UT04 across Mandrake 10, 10.1, Gentoo, Kubuntu 5.04 and Kubuntu 5.10 and it has always Just Worked immediately as soon as the nvidia drivers were installed.  The only exception was 5.10, when I had to install libstdc++5.0 first.

I think we've been at the stage for quite a while now where *games* manufacturers can issue a version that installs across all distros, but none of them are taking advantage of it.[/QUOTE]
They just don't bother as they don't want to spend all the resources testing it for all different distro's. With LSB it's a bit easier as they just get any LSB compliant distro, test it on that and they are done. Having said that though, considering that the Linux share on the home desktop market is miniscule it's hardly worth the effort for the game developers to create a Linux port not enough money will be made from that. 
On the organizational side of things however the software writers might be more interested as LSB would make it easier for organizations to switch to Linux only infrastructure since they won't have to worry about some programs they need working on Red Hat and others working on Mandriva.

---

### Post by TrailerTrash on 2006-04-23
[QUOTE=harisund]

 Easy Fedora
[/QUOTE]


Easy Fedora? Where? How? :-k Never seen that one.

---

### Post by harisund on 2006-04-23
Well, I don't know whether EasyFedora exists, but I believe there is some such project to get everything installed in Fedora after the default installation. Do you know what it's called?

---

### Post by MetalMusicAddict on 2006-04-23
[QUOTE=harisund]A center control panel. KDE does a good job on this. Whatever configuration and tweaking I want to do in Windows, Control Panel is my one stop shop. Gnome has a control panel, but I don't want to go through individual menus for that.[/QUOTE]
I would LOVE to get rid of Ubuntu's "Preferences" drop-down which is just gnome-control-center. Id rather launch it. Maybe with "Administration" added in a seperate pane. In Dapper if you use the menu editor to hide 'em it removes 'em from gnome-control-center also. I dont like a ton of drop-downs. Thats just me. :)

---

### Post by poofyhairguy on 2006-04-26
[QUOTE=aysiu]I don't know all the technical details, but if they already have binary compatibility, what is Poofyhairyguy talking about in [this thread?](http://www.ubuntuforums.org/showthread.php?t=54227)[/QUOTE]

Please don't go quoting that all over the place. Some of it might have been correct at the time (as the recent slowdown in the develoment in Autopackage almost proves) but the overall assertion is wrong.

The klik people are proving that binary compatibility between distros is not magic or a pipe dream- its just hard work.

Of course, there are still many problems. Here is Mr. Hearn's most recent opinion on the matter:

[http://plan99.net/autopackage/Linux_Problems](http://plan99.net/autopackage/Linux_Problems)

---

### Post by poofyhairguy on 2006-04-26
[QUOTE=aysiu]So ... not being that knowledgeable about binary compatibility, libraries, and whatnot...

can someone please explain to me the practical ramifications of this "desktop standard"?[/QUOTE]

Its not a desktop standard. It really has nothing to do with the desktop. It does not favor KDE or Gnome and doesn't put forth any desktop guidelines.

Its a Linux distro standard- its focused on low level stuff like libraries. Its just meant to make development for Linux distros that much easier.

---

### Post by aysiu on 2006-04-26
[QUOTE=poofyhairguy]
Its a Linux distro standard- its focused on low level stuff like libraries. Its just meant to make development for Linux distros that much easier.[/QUOTE] So to end users, will there be any noticeable effect?

---

### Post by poofyhairguy on 2006-04-26
[QUOTE=prizrak]
So in other words instead of the dowload section of websites saying something like
Mandriva Linux 10.2 package
Debian package
Fedora Core 5 package 
It will say:
LSB 3.1 or later compatible.[/QUOTE]

Thats not at all what the LSB is about. It puts forth no common package format or some magic binary bridge.

To use your example, what it helps is those who have to make the binaries for each major Linux. Their job is easier as it ensures that a LSB compatible distro already has this or that library.

There is only one project that is trying to make a magic Linux binary- the Autopackage project. But its development has stalled recently it seems- Mr. Hearn has said he is tired of cleaning up other people's messes.

The klik project probably has the best cross platform magic going (I would say its ahead of Autopackage based on experiance) but it suffers from the same centralization that lovers of a unified Linux binary package complain about with repositories.

Recently it seems like unifying the look and feel of package managers is seen as a more possible goal that having unified packages. Mark has put a good bit of money into the Smart Package Manager and I expect support for it to be in Edgy:

[http://labix.org/smart](http://labix.org/smart)

Yet it does not want to be the magic bridge:> 

Notice that this project is not a magical bridge between every distribution in the planet. Instead, this is a software offering better package management for these distributions, even when working with their own packages. 

I still think that the most likely way for a unified Linux desktop package to exist is if one distro "wins" in the desktop market. Lets say Ubuntu get 80% of the Linux desktop marketshare. Suddenly its debs are Linux's new exes and all the only distros will have to support debs in order to compete. Who knows if one distro will ever get that far.

Another idea I have been having recently is if a commercial entity would make a magic bridge. For example- if Mr. Carmony would just give up on Linspire/Freespire and instead focused on making Click and Run work for all the major distros (thereby becoming THE entry point for closed source commercial applications on the linux desktop) then he could make a lot of money. But that does not seem likely. The truth is that after following Autopackage development it seems that the only way a bridge will be made is if someone is paid to do it. Each Linux is so different its not fun to bolt them together....

---

### Post by poofyhairguy on 2006-04-26
[QUOTE=aysiu]So to end users, will there be any noticeable effect?[/QUOTE]

Just maybe more programs ported or made for Linux because development costs just got a little cheaper (maybe).

The end user will see no difference otherwise.

---

### Post by prizrak on 2006-04-26
> Thats not at all what the LSB is about. It puts forth no common package format or some magic binary bridge.

To use your example, what it helps is those who have to make the binaries for each major Linux. Their job is easier as it ensures that a LSB compatible distro already has this or that library.
I didn't really imply a magical package, although the .bins work pretty well so far. The only issue is making them executable through CLI (not easy double click most "regular "users seem to want) but I'm sure a program could be easily written to do just that. 
I'm not really sure on that, but I thought that LSB will also created a unified directory structure. If that is true I don't see how different packaging makes any kind of a difference. Alien can handle .rpm's and I'm sure .rpm distros either already have or can get something to handle .dpkg's. I was more or less under the impression that as long as the libraries are there it makes very little difference what packaging system is used. 
Of course I could be wrong.

---

### Post by helpme on 2006-04-27
[QUOTE=poofyhairguy]Thats not at all what the LSB is about. It puts forth no common package format or some magic binary bridge.
[/QUOTE]
That's not true. It actually puts forth a common package format, namely rpm, or rather a subset of rpm that has to be supported by all LSB compliant distros.

Also, what is a binary bridge supposed to be?

---

### Post by poofyhairguy on 2006-04-27
[QUOTE=helpme]That's not true. It actually puts forth a common package format, namely rpm, or rather a subset of rpm that has to be supported by all LSB compliant distros.[/QUOTE]

Oh yeah. I forgot. Red Hat and all.

> 
Also, what is a binary bridge supposed to be?

And exe for Linux distros.

---

### Post by helpme on 2006-04-27
[QUOTE=poofyhairguy]Oh yeah. I forgot. Red Hat and all.
[/QUOTE]
?

[QUOTE=poofyhairguy]
And exe for Linux distros.
[/QUOTE]
Sorry, I'm still on my first coffee today, so I'm probably a little slow, but this also doesn't compute. But afaik LSB compliant packages (packages, not exe files) will work on any LSB compliant distro, so what's your point here?

---

### Post by Mathias-K on 2006-04-27
[QUOTE=helpme]Sorry, I'm still on my first coffee today, so I'm probably a little slow, but this also doesn't compute. But afaik LSB compliant packages (packages, not exe files) will work on any LSB compliant distro, so what's your point here?[/QUOTE]

I think by saying "linux exe" he means that a common package format could be shipped with for example games and then you could be as certain that it would work with any distro as you are with the exe file and Windows.

---

### Post by helpme on 2006-04-27
[QUOTE=Mathias-K]I think by saying "linux exe" he means that a common package format could be shipped with for example games and then you could be as certain that it would work with any distro as you are with the exe file and Windows.[/QUOTE]
But that's exactly what the LSB makes possible.

---

### Post by dmacdonald111 on 2006-04-27
So I was reading this post thinking how to explain windows and linux and I have come up with;

"Linux is a suggestion, Windows is a demand"

The whole reason that Windows is where it is, is based purely on standards which you may think is great, but if there are a group of people or businesses which are going to say 'this is way linux is going to be' you can kiss open-source goodbye because no company will work with another and not want some form of compensation. Unless I have got it wrong, forgive me and stuff.

I always thought that linux was a base standard anyway. As in you get a cd and told 'this is the base linux for debian/fedora, build your linux from here' and then people are happy to go off and do their own thing.

Imagine having  a standard laid out and people have the choice - if they choose to work along the 'standard' road, they can benefit from more compatible software/hardware/drivers, or they are welcome to go it alone (as I'm sure there will always be people willing to do).

Linux. It's an idea...

---

### Post by poofyhairguy on 2006-04-27
[QUOTE=helpme]But that's exactly what the LSB makes possible.[/QUOTE]

It does little to standardize the desktop, which Mr. Hearn (Autopackage guy) has been screaming about for over a year. Without such a standard, a GUI exe for Linux is still no closer to existing.

---

### Post by helpme on 2006-04-27
[QUOTE=poofyhairguy]It does little to standardize the desktop, which Mr. Hearn (Autopackage guy) has been screaming about for over a year. Without such a standard, a GUI exe for Linux is still no closer to existing.[/QUOTE]
You should proably read up on this stuff before commenting. The big news with the latest realease of the LSB is that for the first time also defines a standard for the desktop.
This means that desktop applications that are build against this standard will run on any standard compliant distribution, whether you believe it or not.

---

### Post by poofyhairguy on 2006-04-27
> 
This means that desktop applications that are build against this standard will run on any standard compliant distribution, whether you believe it or not.

And MS originally said that Vista would be released two years ago- this is something I will have to see to believe.

---

### Post by prizrak on 2006-04-27
[QUOTE=dmacdonald111]So I was reading this post thinking how to explain windows and linux and I have come up with;

"Linux is a suggestion, Windows is a demand"

The whole reason that Windows is where it is, is based purely on standards which you may think is great, but if there are a group of people or businesses which are going to say 'this is way linux is going to be' you can kiss open-source goodbye because no company will work with another and not want some form of compensation. Unless I have got it wrong, forgive me and stuff.

I always thought that linux was a base standard anyway. As in you get a cd and told 'this is the base linux for debian/fedora, build your linux from here' and then people are happy to go off and do their own thing.

Imagine having  a standard laid out and people have the choice - if they choose to work along the 'standard' road, they can benefit from more compatible software/hardware/drivers, or they are welcome to go it alone (as I'm sure there will always be people willing to do).

Linux. It's an idea...[/QUOTE]
Linux was built on standards, POSIX, FTP, W3C. Linux relies on open standards to achieve it's objectives. This is going to just be another standard for Linux based OS's to use. No one is forcing it on anyone. It simply means that instead of having 20 packages for 20 different distros it will have 1 package for 20 different distros and will be guaranteed to work with all of them. Distributions will still be able to use their GUI of choice, and will have other things differentiating them but all of the certified ones will still have the same libraries so they will be compatible on the lower level.

---

### Post by helpme on 2006-04-27
[QUOTE=poofyhairguy]And MS originally said that Vista would be released two years ago- this is something I will have to see to believe.[/QUOTE]
Sigh, it's the whole freaking purpose of the freaking standard, you're ignorance doesn't change that.

And the LSB exists for some time already, the new thing is that it now also covers the desktop, so if you want to see for yourself, happy playing around with the current LSB. :rolleyes:

---

### Post by poofyhairguy on 2006-04-27
[QUOTE=helpme]Sigh, it's the whole freaking purpose of the freaking standard, you're ignorance doesn't change that.:[/QUOTE]

I thought the purpose was to make Linux more appealing for third party developers. Either way Freedesktop proves that Linux and standards can work together.

> 
And the LSB exists for some time already, the new thing is that it now also covers the desktop, so if you want to see for yourself, happy playing around with the current LSB. :rolleyes:

You miss understand me. Its not a big deal, as there is no good point for me to make.

---

### Post by kencoe on 2006-05-24
[QUOTE=poofyhairguy]Thats not at all what the LSB is about. It puts forth no common package format or some magic binary bridge.

To use your example, what it helps is those who have to make the binaries for each major Linux. Their job is easier as it ensures that a LSB compatible distro already has this or that library.[/QUOTE]

I would point out that one of LSB stated goals is a set standard of compatible libraries accross the distributions to aid in matching dependencies. If you couple this with the FHS standard being worked on, then this is exactly what it means. This app will work on that distro, or this admin script will not halt because the file is not in this location on Fedora or SUSE.

The point of all of these efforts is to keep Linux from fragmenting between the distros. The entire purpose of that is for ease of installation and administration across multiple distro's platforms.

I would consider this an admirable goal. I would also call this the step many companies have been waiting for before more serious consideration about whether to switch to Linux as their primary platform.

---

### Post by neighborlee on 2006-06-02
[QUOTE=kencoe]I would point out that one of LSB stated goals is a set standard of compatible libraries accross the distributions to aid in matching dependencies. If you couple this with the FHS standard being worked on, then this is exactly what it means. This app will work on that distro, or this admin script will not halt because the file is not in this location on Fedora or SUSE.

The point of all of these efforts is to keep Linux from fragmenting between the distros. The entire purpose of that is for ease of installation and administration across multiple distro's platforms.

I would consider this an admirable goal. I would also call this the step many companies have been waiting for before more serious consideration about whether to switch to Linux as their primary platform.[/QUOTE]


I sometimes feel people are worried that 'xp land' is overtaking their precious linux OS when we need just 'that'...we need the consistency found in that land while having our own customized niche ;-)  I really admire the LSB for standing up for whats obviously going to be the ONLY thing taking linux to adoption-land, because no matter how KEWL linux might be on other levels you aren't getting it any other way, or at least in numbers that is going to propel us in directionsa that really matter to most people.  Do we really need apt and rpm and smart and autoblahadinfinitum and yum ? lOL...good lord its us vs them and in the end 'they' get hurt.  What is so hard about everyone agreeing to use just one distro and one package manager and make THAT the best it can be..did it hurt windows ? ( say what you will about windows..but at the end of the day beyond some obvious 'issues', it just works. I concede it doesn't have 'synaptic, but sometimes what you want isn't 'there', and things occasionally fail to install due to DEP HELL ;-)..I've never seen this in windows in most of my yearS of using it ( and why I LOVE pbi system of pcbsd)  v, but of course other issues exist which can be just as madening ( had to reboot other day when dvdburn went south, and rebooted to non -useable mup.sys file and had to reinstall windows). go fig---

Why has linux not adopted the    clearly superior 'pbi' system of pcbsd I wonder ( libs needed by app Zyz, go into their own appdir causing no  problems, and keeping /usr/lib pristine ), while still being able to use KLIK for whatever else ?

I am so utterly surprised ( albeit happy to see it ) to think that the FIRST distro to adopt full LSB desktop complaince will be Xandros 4, as its not even completely free ( mainly slower burning as I recall ) albeit a very nice setup.

It will be nice when linux unites for the 'village' mentality in lieu of any other.

Does anyone know when ubuntu is going to come online to be lsb compliant , as until then I dont see the logic in using it since to me the 'village' mentality is broken.

cheers
nl

---

### Post by Virogenesis on 2006-06-02
[QUOTE=harisund]People, here's my 2 cents on what a "standard base" should mean. 

First, yes, package installation. I go to a website, it says "For Windows use name.exe, for Debian and Debian based systems, use name.deb, for Red Hat and Red Hat based systems use name.rpm, for so and so, use name.soso and if you want to configure from source use name.tar.gz, but make sure you have libwhatever.so, libwhocares.so, libannoying.so" 

If you want to know what I am talking about, go here [http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/) And the worst part is there are no instructions on installing it on debian based systems. 

This is a strict no no. Just like in Windows, it should say "For Linux use this: name.lexe" or any common extension, so people can be taught .exe for Windows, .dmg for Mac, and .something for Linux. 

Then, I download it, double  click on that file, and it installs. No terminal, no unmet dependancies, no package warnings, nothing. Just like in Windows. Plain, simple double click. 

Don't get me wrong, the repository thing is awesome too. But seriously, does anybody even know half the softwares in the repository? I have all sorts of repos in my sources.list, and when I open Synaptic it simply freezes for a while before it makes its entire list and shows me. There must be something done about this. 
[/QUOTE]
Things break inside windows because of that.

[B]Are you sure you want to remove that file removing it might prevent other applications from working?
[/B]

Fantastic upon boot up, windows is missing this dll....you can not boot anymore.

[QUOTE=harisund]
Next, after I install a program, it should turn up in the start menu. Or whatever is the equivalent. Gnome's menu. KDE's menu. Whatever. The user should know what to click to start the program. I am used to going to Start Menu ->Programs and finding what I just installed. Can I do that on Linux? Always? 
[/QUOTE]
I install a program within windows and my start menu gets filled up....

[QUOTE=harisund]
Another issue: choices. Yes, Linux / Open Source is all about choices, and you can have tons of them. But seriously, I don't need Bash, Ash, tcsh, zsh and cash ( :) now that would be nice ) on my system. Similarly, standardize on OSS or Alsa, or ask the user "Use OSS or Alsa (If you don't know what that just meant, just use the default"), standarize on Firefox. Don't give the user a menu saying Browser: and then offer Konqueror, Epiphany, w3m, lynx, Firefox, something_you_built, something_I_built. Who cares? I jsut want a browser that works. Simple.
[/QUOTE] 
So you want IE and Firefox only?
Fantastic tell me what to do.....I like choice I like to choose between italian food, french, american, indian, chinese...etc


[QUOTE=harisund]
A center control panel. KDE does a good job on this. Whatever configuration and tweaking I want to do in Windows, Control Panel is my one stop shop. Gnome has a control panel, but I don't want to go through individual menus for that. [/QUOTE]  True.... 

Outside of the LSB, hardware and vendor support. This can only come with time, and I am sure once a LSB is established, vendors will see the need to provide drivers and what not. 

The terminal. Yes, even though users shouldn't be exposed to the terminal unless absolutely necessary, you can't deny, the terminal is the heart of any Linux. Absolutely anything can be done through this baby. Have it somewhere prominent. On the desktop create a "My Computer", "My Recycle bin" and "my terminal" icon. A user reads on a wiki "execute sudo iwconfig wlan0..." and they are lost right there. 

[QUOTE=harisund]
External support. In Windows, I can call for remote desktop support. Similarly, I should be able to call for, I believe an SSH support. Windows has an awesome feature called "Call for Remote Assistance." Of course, we don't have paid people to do the job, but I am sure thre are people who would volunteer to do such a thing at some times. Just like an IRC channel. My mom doesn't need an SSH server on all the time, but if something gets broken she should be able to call me for a troubleshoot, and a SSH server should termporarily get started, log me in, and stopped after I log out. People like it when they know they have somebody to support.
[/QUOTE] 
That exists, pay for support...if you buy a licease for redhat enterprise and a driver doesn't exist they will write one.... 
Try that for support.
Windows didn't come with desktop icons on.

[QUOTE=harisund]
Concept of sudo. User's shouldn't be allowed to install programs, and when they download a .lexe file and run it, it should ask for root permission. Or even better get installed for that user alone, and not affect general user space. Most home user's don't have multiple accounts, and disk space shouldn't be a problem. [/QUOTE] But lsb is designed around servers aswell which do have multiple users.

[QUOTE=harisund]
Mounting CDs. Why on earth should I mount a CD with the -exec option to be able to execute binaries? What sort of a clown came up with that idea? First, you ask me to use exec. Then again, you ask me to use sudo. Isn't this getting sort of paranoid? [/QUOTE] 
A smart clown who understands security, a clown that should be employed by microsoft to sort out their Os.
[QUOTE=harisund]
Audio, Video, Codecs, DVD. Please get something done people. After an install, show a message "You just installed a free OS and you get only free stuff. You want proprietary stuff?" and then either "Here is what you do... " or "Get lost. You want free stuff, you get only free stuff." Automatix, Easy Ubuntu, Easy Fedora whatever. Show the user it needs to be done and get it done. [/QUOTE]  Why? I see no point in this, let them whine all they want its not our fault we shouldn't try to fix someone elses mess. Let them understand about closed codecs and why they can be considered harmful.

[QUOTE=harisund]
Flame wars. Stop having them. I am getting tired of 1337 users debating on Kde/Gnome, Vi/Emacs, sendmail/fetchmail, linux kernel/bsd kernel. They scare regular users. And most importantly, Linux users should stop trashing Windows. Calling Windows as "WinDoze" or "WinBlows" simply shows arrogance on Linux user's part. I understand Linux is way more powerful, easier, safer and what not. I know, I use LInux too. But that doesn't mean Windows and its user gets the trash talk. [/QUOTE]
Linux users should stop trashing windows and its users why?
Windows users trash Linux without trying the damn thing look at all the crap microsoft spreads about linux being a hobbist Os.
I call windows, windoze, winblows... why because its my fun, I enjoy it I enjoy laughing at people who defrag, who have to clean their registry, run third party software due to bad security.

[QUOTE=harisund]
Maybe there are more, but these are certainly some stuff that would help in moving towards a standard Linux base.[/QUOTE]


These aren't standards, these are faults any have nothing to do with standards and things you have choose to dislike.
Distros should be able to stand out from others if they wish to.

---

### Post by neighborlee on 2006-06-02
[QUOTE=Virogenesis]Things break inside windows because of that.

[B]Are you sure you want to remove that file removing it might prevent other applications from working?
[/B]

Fantastic upon boot up, windows is missing this dll....you can not boot anymore.

[/quote]

to be taken seriously you can't spread FUD ;-)...It may be true 'sometimes', but in my several year of windows use ( I've used linux for about half that time period ) I've never had this happen to me, and I've done the 'yes to all' remove stuff before...its alot more rare but I"ve done it..now IF linux used the PBI system that pcbsd uses, we could all have a nice clean efficient system, but until then dep issues can occur . MacosX uses appdir's so is that a system to learn something from too ?

cheers
nl

---

### Post by Virogenesis on 2006-06-02
[QUOTE=neighborlee]to be taken seriously you can't spread FUD ;-)...It may be true 'sometimes', but in my several year of windows use ( I've used linux for about half that time period ) I've never had this happen to me, and I've done the 'yes to all' remove stuff before...its alot more rare but I"ve done it..now IF linux used the PBI system that pcbsd uses, we could all have a nice clean efficient system, but until then dep issues can occur . MacosX uses appdir's so is that a system to learn something from too ?

cheers
nl[/QUOTE]
Explain how its FUD, you don't do yes to all because of what reason because you are unsure you will break your system.  
I have been unsure of programs using dll and because of that reason I will not say yes to all when removing programs why? 
Once bitten, Twice shy...
So I do not know how xp handles removing applications as I am scared I'll break somethng and not be able to repair it.
Can you blame me?

---

### Post by neighborlee on 2006-06-10
[QUOTE=Virogenesis]Explain how its FUD, you don't do yes to all because of what reason because you are unsure you will break your system.  
I have been unsure of programs using dll and because of that reason I will not say yes to all when removing programs why? 
Once bitten, Twice shy...
So I do not know how xp handles removing applications as I am scared I'll break somethng and not be able to repair it.
Can you blame me?[/QUOTE]

No heh I dont blame you, Im just saying its never happened to me since I've used Windows, and so to incite that as a definitive concern is spreading fud when its clearly not something that happens to everyone or even just a few..

cheers
nl

---

### Post by RAV TUX on 2006-06-10
[quote=aysiu]Yeah, I read about that yesterday, and I wasn't sure exactly what that means. Does it mean a binary compiled for Ubuntu would work on Fedora as well...?[/quote]

I may be mistaken but isn't this already being implemented with Yoper ?

[http://www.yoper.com/](http://www.yoper.com/)

---

### Post by Filthpig on 2006-06-14
$0.02

I really don't know why some of you folks are actually using Linux. You want to go out and buy a game and know it works on whatever distro you're using? You have repositories of thousands of titles of software there for free at a single keystroke and you want to be able to walk into a store and know the ware you're about to buy will work? 

You complain that the most versatile and customisable OSes ever made (that is, the Linux and BSD derivatives) don't do what you want and complain you have too many choices to make?

Some of you guys complain like you've been given a free car and whine you never had to buy gas on the bicycle.

---

### Post by Virogenesis on 2006-06-14
[QUOTE=Filthpig]$0.02

I really don't know why some of you folks are actually using Linux. You want to go out and buy a game and know it works on whatever distro you're using? You have repositories of thousands of titles of software there for free at a single keystroke and you want to be able to walk into a store and know the ware you're about to buy will work? 

You complain that the most versatile and customisable OSes ever made (that is, the Linux and BSD derivatives) don't do what you want and complain you have too many choices to make?

Some of you guys complain like you've been given a free car and whine you never had to buy gas on the bicycle.[/QUOTE]
Complaining and understanding the need for standards is two different things.
Sure I would like to see linux share a common standard why?
Because standards help progress can you imagine a world where no human spoke the same language.
The whole internet is based around standards.... FTP, HTTP...etc these are successful as they have been embraced.
Standards will bring things like webcams, drivers... special mouse drivers...etc 
Standards help why do you think the LSB was created?

---

### Post by vinodis on 2006-06-15
if no binary works good cross-distribution , then , how does the Google Earth's , NetBeans's and Oracle's installation/Setup Programs working across RedHat/Debian etc?
I mean the .bin files.

---

### Post by aysiu on 2006-06-15
Firefox's binary also works across distros.

---

### Post by turbojugend_gr on 2006-11-24
Note. I am not that wise on such matters, but I have two statements to make, and of course a question alongside. All mostly regarding post #10 and others like it.

1. I have to disagree with the view that Linux, should be turned into a free windoz. Most users do not choose Linux cause they don't have to pay. They choose is because it is about freedom, and the capability to make things the easy way. I can't stand listening to people saying Linux it's too damn hard, in windows I just do "this". It's all about sth growing on you. If Linux was the standard, then windoz would seem Hacker only to users, imagine a user that is used in installing via synaptic (also imagine the amount of packages synaptic would have given Linux was 90% of the market), just search, check, install! Who would find, googling, downloading, locating the *.exe. starting it, deciding where to put the damn thing, and then searching an ever growing menu to locate the entry. It seems pretty obvious to me, it's all about the monopoly. Just take a look at OS X, you install .dmgs via drag 'n' drop, yet users think that's stupid, cause they were Masters back in windoz, and now they have to ask to find out it's not all windoz-like in their new OS. What a stupid OS is that, it doesn't look like windoz, it's for experts, that is how I find they are thinking.

2. Is it truly that hard to create a Linux-wide isntaller? my view: DEFINATELY not, take a look at Planeshift installer, Firefox, Real Player, nvdia drivers, songbird... Well Planeshift let's say, it has a double click installer, the regular next,next,next,some alterations maybe,next,finish. It does the trick amazingly well, and guess what it's for all Distros, DEs, 32/64 bits (and it asks you real time what you use), it can perform a system wide install plus plus plus. So I guess it's not hard to make a windows installer, it is hard to make a windows programmer to sit down and learn how linux works, so he can create an installer. That's why despite PLaneshift despite not being commercial software, having less cash,etc, has a better installer than many other big companies, which many describe creating a Linux installer too damn hard. So i guess that Apps that have Linux devs, and not windoz retrained cause Linux is growing, don't find it hard to create a top notch installer. Same goes for realplayer too, though with its installer slightly more troubles seem to appear. Long story short, it's the companies decision, if you get to pay for 4-5 nice Linux devs, then a very nice distro-free installer will appear, or at least 4-5 packages (rpms,debs,portage emerge scripts etc) that cover the vast majority of users. The current winers seem like thinking "why on earth isn't Linux the same as windows, so I can run the same installer on it?" they don't say so, not even to themselves, but it's implied when they are seeking the fault on Linux rather on companies, and M$ monopoly. Mac's are far easier to support and less variated than windows, not just linux (since even the hardware difference is limited to practically nothing), it has a slightly better desktop user percentage (2-4 % than Linux I read), and still it receives about 4-8% better coverage than the endlessly BABEL of Linux (many distros, more architectures, and even more hardware differences), so I guess the platform has very little to do about it, the market share is about the only real factor.

3. Here the question now. If and I say IF, thing is not as it should be, and it's Linux's fault it doesn't get the support windoz do, **Would you sacrifice choice over better commercial software support?**

For me, not. Cause if we did, then we would all be great with a windoz copy. M$ never did anything to prevent users doing that, on the contrary it made it real easy, being an economist myself I can understand it, it's not like they only make money from windows sales, it's all about having a Monopoly in the market, then you can force both Costs and Standards in the Market, and is just that M$ is doing. Making money is a lot easier this way, you may loose great peaks, cause you loose sale boosts (since users can copy it) but on the long term you also loose bottoms, you have your bucks safe, and that's a Managers paradise, you know how much you make (and being the monopoly in the software market- that's enormously big profits) so you can feed other projects, like msn, windows mobiles, xboxes, windows ce, 50$ pc's , overpriced peripherals and so on, trust me you make more money this way, and you are sure of it. Fighting over the market is just a derby, it always is, so you are not left with enough capital to expand your self if you let your self being dragged in one from a challenger company.

"But what are you saying lad, Linux is growing", yup it is, and in fact it is said that by 2008 it would become a 10 billion $ market, that's too big, since most of it is under Public Licenses, and therefore free. So all that money is about the newcomers to Linux, those companies that will ship their products Linux ready, commercial stuff. To cover that money it means that almost all stuff will be ported to Linux too, or else commercial success won't be guaranteed. How come? Ubuntu has a share, but in general most distros became easier to use, most users became better users (computing, especially in Europe is about 8-10 years old-so before trying linux, users had to feel good with their knowledge state, so time had to do with it), so Linux got from a server thing, to a Desktop thing. Now to this add that Linux-MacOS are now even more alike (since there's no PPC processor, Macs are now pretty much PCs), so a company will decide easier to expand to Linux, since that would cover the Mac market too, still many mods needed, but nothing compared to having a different architecture. S if you was Managing a company, wouldn't you decide such a move? That would increase your sales/share by about 20%, since, especially in the beginning of this (Now that would be) Linux/OSX boom, it would be appreciated as a nice thing to support "us too. I tell you m8s, it's no wonder Gates is often described as the most clever man on the Planet, that's close. He perfectly took advantage of the PC boom, he made enough profits to buy a planet, he gave charity enough to make sure he is to be remembered as a fairly nice guy, instead of a ruthless millionaire, he tried hard to extend the acme period of his company and when he made sure that wasn't possible, left his position (as far as I know, not his shares) to avoid all the coming decay.

Linux is not to grow, by choices over a stanza, it is to grow if it has a nice Marketing Plan, ubuntu is giving that, it's trying to show the world it is even more Free to use it, than to pay for it. It's working big time, and it should since it is the truth after all. Of course, a standard is always welcome since it would reduce Human Resource Educating costs, for a company willing to cover Linux as well, and as such is to be welcomed and contributed as much as possible. But it is not by itself what will take us from minority, to an equal importance case. It's making it **Cool, Fun, Easy** (see one of 'em), **beautiful and powerful** that will. So keep supporting one an other, keep answering threads, keep creating how-to's, keep posting bug reports, generally keep making Linux and especially Ubuntu matching all the bold words and why not keep using ubuntu, as it seem to be the "faster ship" around to a big market share. If a user feels whatever of the bold ones is most important to him for Ubuntu, he will stick, he will bring others too... so we will accelerate sth that seems inevitable, Linux becoming a serious market % and being treated as such. Keep in mind, that it's not only how many we are, it is also how much we use the damn thing (pc/web/etc), Linux users tend to greatly overcome others on that, and having a beautiful, fun and smart/powerful  desktop will further boost that . Who said impatience is always a bad thing to feel? ;)

I hope I 'll get at least one to read this. I had fun writing it, I got the chance to share my thought on this subject with others. Whoever manages to stay awake while reading this, plz post your views/thoughts, you 'll win a clothes peg... ;).

Best Regards, TJ.

---

### Post by ShadowVlican on 2006-11-24
i haven't read the thread, but i'm all for teamwork instead of the current situation where we have tons of branching and programs that do basically the same thing but made by different people

linux needs to UNITE and STANDARDIZE EVERYTHING or else it CANNOT compete with Microsoft for the Desktop market!!!

---

### Post by chaosgeisterchen on 2006-11-24
@**turbojugend_gr**

Thanks for your posting, I read it and have my very own way of interpreting it. It shows that you want an unified installer for Linux if I understood you correctly? But you want to keep the choice free for the people?

Well, I often tend to think that we badly need unification to get further forward concerning market share. But this would extremely decrease competition and therefore the urge for innovation within the business itself. So we stay on the safe side improving Linux in all aspects by combining all our ideas  and sharing knowledge. I love to watch the incredible increase of usability on the free desktop and we are just at the beginning of a era in which free software will become far more important, the problems concerning Windows Vista will be the next step towards that, provided by Microsoft itself.

I chose Linux merely because I wanted to know how it works like. And it works great, I often miss it while using Windows here. (Please do not discuss the usage of Windows I have to admit - my notebook will just not run decent with Ubuntu)

We can advance even without unification. Or just because we have no unification? Anyway, we're constantly improving. And we're improving at a higher rate than Microsoft has ever done.

---

### Post by turbojugend_gr on 2006-11-24
@chaosgeisterchen: Well actually I am not urging for a unified installer, I am just saying that if a corp wants to port it's apps to Linux, there are many,many choices, and there fore it's actually not that difficult. There are .bins out there now, and Linux is just string to grow, therefore I strongly believe, that unifying things is not the thing to greatly boost Linux usage, making tempting to use on the other hand will get bigger % of the market and therefore the companies will make more money porting things to Linux, thus choosing to do so. Long story short: Linux is growing, if we help this in any way (the easiest one being providing support and nice stuff one an other) will just give things a boost. I don't believe that an effort to a unified platform will hold things back, but neither I believe it definitely means boosting 'em.

---

### Post by dvarsam on 2006-11-24
Sounds like a big Flamewar started here!

Even though it is late (in my country), let me give a basic summary from all I read (I will edit this much better tomorrow responding to the most interesting posts on an individual basis):

_Reality_:

> All Linux Distributions need a unified installer!

AND

All Linux Users need a unified installer!

Now if LSB can create some standards accepted by all Linux OS makers, it will be very good!

Let me explain:

1. LSB will create 2 versions/types of "package databases" that _Must_ be installed on _Every_ Linux OS's _by Default_.

2. These "package databases" _Must_ be accepted by all makers of different Linux Distributions - Example:

a. Linux Ubuntu,
b. Linus Suse,
c. Linux Red Hat,
d. Linux Solaris
e. Linux Mandrake
f. ...etc etc
g. ...and Whoever else wants to join

_Conclusion_:
The above 2 versions/types of "package databases" are a requirement for what is going to be adopted, meaning ".exe" packages (or whatever you want to call them)!

Now, all Linux Distributions that accept _both_ of these 2 versions/types "package databases" will automatically be called "LSB compliant".

So, all software/games that ship into stores will state:

1. Hardware Requirements: ...blah ... blah...

2. Software Requirements: Linux Distribution must be LSB v2.0 or later compliant

To answer your big question:

> Why create 2 versions/types of "package databases"?

Because there are 2 versions/types of Linux Distros:

1. Long Version (e.g. Ubuntu, Suse, Mandriva, Fedora, etc etc)

2. Short/Stripped Version (e.g. Puppy Linux or Damn Small Linux - both of which require 50MB or 64MB HardDrive/Memory to install)

_Note_:
The "Short/Stripped Version package database" could also be implemented in other cases/devices, such as Linux Cellular/Mobile Phones, PDAs, or whatever else... (...something _similar_ to **Windows CE**)


_Warning_:
IF this "LSB compliant" standard is NOT accepted across all the Linux Distro producers, we will end up in cases where the ".exe" file can NOT be installed because some of the default/required "database packages" were not installed by that Linux Distro maker.
Of course, such a Distro would be considered as "non LSB compliant"!!!

_Conclusion_:
Distributions that decide NOT to adopt the NEW "LSB standard" will be left alone in the DARK!

Now, the "LSB standard" must _try_ to accept all Linux Distro producer's wants & non-wants.

_Example_:

1. Ubuntu Distro rejects the package named "build-essentials", to be included in the "long version package database" for their Linux Distro.
2. Suse Distro accepts the package named ""build-essentials", to be included in the "long version package database" for their Linux Distro.
3. Fedora Distro accepts...
4. Mandriva Distro rejects...
5. Whatever Distro accepts...

IF 90% of all Distro makers "accept" the package "build-essentials" to be added by default to the "long version package database", LSB will add the above package to the UNIVERSALLY ACCEPTED "long version package database" ADOPTED by all Linux Distro makers that decide to be "LSB compliant".

In the end, the "long version package database" will be big enough & including ALL the packages accepted by most Linux Distro producers!

Of course the same above procedure must be followed for choosing what packages will be added by default to the "short/stripped version package database"!
And of course, the companies voting for which packages to be added by default to the "short/stripped version package database", are the ones producing Short/Stripped Linux OS's - like Puppy Linux & Damn Small Linux or even Distro makers that are willing to make/produce Short/Stripped version of Linux OS.
Also, companies using Short/Stripped Linux versions for PDAs or Cellular/Mobile phones can also join this "LSB package decision team".


Security & Stability of course must play a big role towards the decision to whether a package will be added or not in the "LSB long/short version package database"!

Now, the program/game file, will have to be posted in 2 formats:

1. source code format (for those that want to compile on an individual basis)

2. ".exe" format (for all "long version Linux OS's")

3. ".exe" format (for all "short/stripped version Linux OS's)

And on the stores selling programs/games, it must be denoted whether the program/game ".exe" file, can be installed on both "long version Linux OS" & "short/stripped version Linux OS" or in which of the 2...

IF a Linux Distro maker does NOT want to be "LSB Compliant", let him decide whether he wants to convert the package to ".rpm" or ".deb" or ".tar.gz" or 
whatever - that's his problem...!!!

At least, in this manner, the linux world will be progressing!

You can't ask from a company that is aiming towards profit, to provide a program/package in ALL the following formats:

1. ".rpm"
2. ".deb"
3. ".tar.gz"
4. source code
5. ".tgz"
6. ".tbz"
7. ".src" (portage)
8. etc etc...

> Lets be reasonable!!!

Come on!!!

[QUOTE=turbojugend_gr]@chaosgeisterchen:
Well actually I am not urging for a unified installer, I am just saying that if a corp wants to port it's apps to Linux, there are many,many choices, and therefore it's actually not that difficult.[/quote]

Really?

Then, can you try to convince a company looking for maximum profit to provide the drivers for their products in all the above mentioned package forms!!!
I bet that they will tell you to "scr*w yourself".

[quote=turbojugend_gr]
There are .bins out there now, and Linux is just string to grow, therefore I strongly believe, that unifying things is not the thing to greatly boost Linux usage,...[/quote]

Really?
And you prefer this CHAOS instead?

[quote=turbojugend_gr]
...making tempting to use on the other hand will get bigger % of the market and therefore the companies will make more money porting things to Linux, thus choosing to do so.
Long story short: Linux is growing, if we help this in any way (the easiest one being providing support and nice stuff one an other) will just give things a boost. I don't believe that an effort to a unified platform will hold things back, but neither I believe it definitely means boosting 'em.[/QUOTE]

How do you make it "tempting" for someone to adopt Linux, when he has to learn 8 different install methods in order to be able to judge which Linux Distro suits him better?

Personally, I don't want to mess with ".rpm" packages, when I have learned how to cope with ".deb" files.
And I am sure that every other user out there is feeling the same for their own preferred Linux Distro!
They do not want to mess with ".deb" files, because they are comfortable with some other different package format!

> 
The **true differentiation** between the Linux Distros out there, should involve **the programs** selected to be installed by default!

**AND NOT the installation method**

Example:

1. Suse     prefers: Desktop: KDE,   Office: KOffice, Architecture: i386,  Install: Graphical
2. Ubuntu   prefers: Desktop: Gnome, Office: OOOrg,   Architecture: i386,  Install: Text Mode
3. Fedora   prefers: Desktop: Xfce,  Office: Gnome,   Architecture: sparc, Install: Graphical
3. Mandriva prefers: ... etc etc
4. ... etc ... etc

Thanks.

P.S.> Another Unification between Linux Distros should take place in terms of **Filesystem** being used - lets all use Ext3... please!!!

---

### Post by vincentvee on 2006-11-24
i think what it means is that all distro's should ship with a standard set of packages, nothing to do with differences in compiling

> **YourSurrogateGod said:**
> Now that you mention it, that's a good point... I don't know.

---

### Post by turbojugend_gr on 2006-11-24
**@dvarsam: **Well since you are a fellow greek too, let me this time use some greeklish: re si dvarsam tha mas koirodevoun edw oti oi ellines then mporoun na pou afto pou theloun se ligotero apo 100 grammes. Kai oi dio to xesame to thema! ;)

Now back to the topic. I 'll quote you where it's due.


[I]Quote:
Originally Posted by turbojugend_gr
@chaosgeisterchen:
Well actually I am not urging for a unified installer, I am just saying that if a corp wants to port it's apps to Linux, there are many,many choices, and therefore it's actually not that difficult.
Really?

Then, can you try to convince a company looking for maximum profit to provide the drivers for their products in all the above mentioned package forms!!!
I bet that they will tell you to "scr*w yourself".
[/I]
---> Well actually, that's not that accurate, if a tarball is provided then it takes a small effort to make an rpm, if it's an rpm instead then it takes seconds to "alien" it. So it's not that hard if you decide to provide one to match the others. It is not ideal too, in that I would agree. THat's where the .bins come to the table. If planeshift devs can create one, then it's not that hard after all. As or the "scr*w you" part, a company will say that if you are 7% of the market share, if you are 18% thought let's say, they will respond "We will try our best" and they trully will, money makes the world go round my friend!

[I]
Quote:
Originally Posted by turbojugend_gr
There are .bins out there now, and Linux is just string to grow, therefore I strongly believe, that unifying things is not the thing to greatly boost Linux usage,...
Really?
And you prefer this CHAOS instead?[/I]

---> Well I don't. I said so actually. But I don't find either this Chaos is always to blame, it makes Linux all about choice, and this makes Linux tempting to many users. It could still be tempting though if there were less installing routes. I second that, but I believe that it should be done cautiously, so that Linux won't loose this element (freedom of choice), again it is not neccesary to only have these ways, but it is necessary that you don't take away a Gentooeer his portage tree, it's what makes him happy! That's why things need caution, I am no expert on this subject so here I stop.

*How do you make it "tempting" for someone to adopt Linux, when he has to learn 8 different install methods in order to be able to judge which Linux Distro suits him better?*

---> I can't imagine a user getting to understand how all systems on earth work, then get to choose his. If users thought that way windoz would have 5% of the market, maybe not that but definatelly not numbers like 85%. Therefpre I haven't learned everything about all distros, then chose ubuntu, a Suse book fell into my hands, tried SuSE, liked it, then I read about ubuntu being popular, and wanted to try, that was it, I sticked with it, I liked it, I do like Gentoo's approach a little more, but still I don't get to try it. I am very happy with ubuntu, and thus I don't get in the trouble just cause I believe with Gentoo I MIGHT be better, see it's not that definate, users are human and as such we don't think in an absolute way. Again I would agree that less options would do good, but having lees options is a complicate matter. Gentoo is not an option for me right now cause I feel nice with the safety ubuntu community gives me, the safety using the most popular distro gives me. See again I decide in a not absolute/definate way...;)

*Suse prefers KDE Desktop, KOffice, Architecture i386, Install: Graphical*

---> SuSE does (KDE, KOffice, i386), Novell does not (Gnome, OpenOffice, 64bits also important to them-btw when will we get 64bit ubuntu like SUSE's, having 32bit apps running neatly, no chmods?). If all the parts that are involved can't have the same opinion, how do you expect all Distros to do so? And I haven't involved the users in that. SuSE doesn't have a default as far as I can see with my own eyes, you HAVE to choose either GNOME or KDE, no default, so users use both, who is gonna tell me what should I use?  A lazy windows dev, that is bored of learning all that Linux crap his company ask him to, definately not! That's why I pointed out that companies that feel the Linux market is important to them, have great installers, while other companies believing Linux isn't big enough, make awful iunstallers, and troublesome products. Compare nvidia to ATi, you 'll se what I mean.

*Ubuntu prefers Gnome Desktop, OpenOfficeOrg, Architecture i386, Install: **Text Mode*** WRONG! Ubuntu was the first Major Distro giving LiveCD so much attention, a user can install through it, after testing his hardware is detected. When did you downloaded an UBUNTU last time? here I quote the official site's view on the use of graphical installer (Live CD): "The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 192MB of RAM to install from this CD." while for the text based installer : "The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:blah blah (not so important go check if you find it is)"

I understand ubuntu didn't have a graphical installer till Dapper, but when it introduced one, it was the best choice, since you can ask step by step installation questions while you are installing (or simply check your email). So it's not that accurate. Generally my point is, ALL linux distros would like a graphical isntaller, even Gentoo is now using one. It's just a matter of time since they get that. So it's a point that only suits your need to show the so Called CHAOS. Sorry I can't see any other point in including the graphical/text installation there along with the differences. There's noone a graphical installation would hurt. Those not having ram, should be given an alternative, but the main choice if it was possible it would be Graphical for everyone.(all the other reason an ubuntu user would need the alternate cd, are there due to temporary limitations, too).

On the whole, you don't seem to get my spirit, so I will try to sum it. I has been stated that unifying things is extra critical to Linux to expand. That's wrong, it's only a minor thing and should be treated cautiously too. It could become a boomerang case, a company would find it less costly to port its products to Linux now, but Linux might loose users on the Long Term, if this "unification" alters its nature, freedom that would be.

Linux is SET to expand, you can't change that, it's the way the Market (econimically, not the software market specifically) works. Linux is better than windows, MacOS is too, you can hold a better product back for a fair amount of time, but if it persists market pressure (Linux is immune to that, since it is OSS) then the time will come that the Consumer will seek for his best. And this time is approaching. PC users, are somewhat like the hobby-photographer in the late 1800s. When only Kodaks were easy to use, Kodaks where monopoly, while there where (maybe) better cameras (Linux), they where difficult to use, and only professionals used 'em (Hackers, geeks, whatever a Linux user was called till 1998-when the main De's appeared). The time passed and Kodak couldn't proceed further with easyness, challenger companies filled the "easyness" gap, while keeping the superiority of their products (what most distro's are targetting now, ease of use, while projects like Beryl still blow off their opponents-call me Aero). Users are getting to know better what a PC is. Internet spread lets 'em know there's an OS called Linux out there, and it's for free, why not try it, wow that's better!

Finally to support my sayings, there no better example than Ubuntu. Ubuntu is not a Mandrake like Distro. By that I mean it's not targetting Blindly at the ease of Use. No, you still have to read a how-to to play mp3s ad so on. Why in order to remain free, inorder to get the user involved in the community, and ubuntu is said to have the best community, so it's a good marketing for the Distro. The results? most ubuntu users are not migrating from other Distro's, they are migrating from Windoz. Users like to use a more powerful system, now that they had a fair amount of time to understand using a computer is more than learning how to use the MSPaint, their browser, winamp etc, they can evaluate thing too, and evaluating things will lead a user in choosing ubuntu/linux for his PC, or maybe buy a MAC. Ubuntu is not by luck the most popular distro. They made key choices:

1. Small download size --> "We target for the spontaneous, a users chats with a friend using ubuntu, or "stumbles" upon a site talking about it. He likes the idea, he needs less than 2 hours to get it on his system, we take advantage of his enthusiasm, we don't let that fade away making him to wait  for about 12 hours before he can test it. Ship it free takes advantage of this too, he reads about ubuntu, request a ship it free, no cash, no harm, why not?"

2. Small download size, means the user, has to install software using the internet after installing --> "The better for us, he will get to use the forums asking 'bout apps-he will like the feeling of being part of such a great community, he 'll get to see the easyness of installing through synaptic (btw we need to stop giving people commands, let them use add/remove programms or synaptic, it's encouraging to see so many apps categorized, one click away). He will get to appreciate the vast amount of choices available, humans like choice.

3. If a user needs to dl stuff after installing then he will needa broadband connection --> "The power user, is our main interest. The spender, the one that has developped a curious mind using the internet, he will be the one likely to get interested about ubuntu, after all it's a short term setback (if any), broadband connections is becoming more and more affordable, after all Linux power is in it constanlty changing, if a user can't follow that, he won't appreciate it after all. Also having a nice connection is needed to join the community, which is the a key factor for a user to stick with us. Last but not least, a broadband connection would keep the user insterested, since we lack games (no wonder most games in linux are multiplayer targetted, like Quake,Doom,Neverwinter Nights or PLaneshift, Nexuiz) for now, after all multiplayer games are the future of gaming (plus the companies don't face the copying issue-so they may port to linux too)"

**What I am trying to proove? -->** It's tempting users that will force the companies to support Linux, not tempting companies to create stuff for Linux that will tempt users. The latter won't necceserelly happen. MacOS is very easy to support, yet it's not, why? It's a minority. I tell you Lads money makes the world go round! Having many users meens the companies will be forced to port to Linux if they wish to hold a big market share. Therefore I believe that LSB it's not such an important matter, it won't make companies port to Linux, those that believe Linux support is making 'em money do so without any LSB, while those that don't believe it will make 'em profits, whine about Linux being difficult to support (again take a look at the nvidia/ati case, or HP's attitude to that). It won't hurt either (if it's done in a way that it doesn't alter the nature of linux->choice), it could slightly boost things under that term.

I tried to built a strong base around my points, I hope I did. I really appreciate this conversation, and I am happy to take part in it. I am looking forward to som comments ;).

P.S.:@ dvarsam: I find your view fair, but you need to evaluate things commercially not like a developer would do. It's the companies that make the decisions, not their workers. ;)

---

### Post by jclmusic on 2007-01-11
isn't this what autopackage does?

---

