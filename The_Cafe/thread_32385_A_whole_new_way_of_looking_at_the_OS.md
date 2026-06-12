---
title: "A whole new way of looking at the OS"
date: 2005-05-07
forum: The Cafe
---

### Post by Psquared on 2005-05-07
While doing some research on rox-filer I came across this site.

Here is the most important thing it says to me:

> Traditionally, Unix users have always based their activities around the file system. Just about everything that's anything appears as a file: regular files, hardware devices, and even processes on many systems (for example, inside the /proc filesystem on Linux).

However, recent desktop efforts (such as KDE and GNOME) seem to be following the Windows approach of trying to hide the filesystem and get users to do things via a Start-menu or similar. Modern desktop users, on Windows or Unix, often have no idea where their programs are installed, or even where their data files are saved. This leads to a feeling of not being in control, and a poor understanding of how the system works.

The ROX Desktop, however, is based around the file system. Its core component is ROX-Filer, a powerful graphical file manager which, in addition to being a popular filer in its own right, provides a couple of extra features which allow it to solve the above problems...


[http://rox.sourceforge.net/phpwiki/index.php/WhatIsRox?PHPSESSID=911a9ae3793b06c08f1efe40e834857e](http://rox.sourceforge.net/phpwiki/index.php/WhatIsRox?PHPSESSID=911a9ae3793b06c08f1efe40e834857e)

I have to agree somewhat with the conclusion that Linux GUIs are Windows wannabes. I also like the idea of a DE based upon the Unix filesystem rather than dynamically linked libraries and shared files which pervade Windows and seem to be infiltrating Linux. I may be wrong about this, but it does seem that way when every program has lists of dependencies.

I'd be interested in other thoughts on this.

---

### Post by markw on 2005-05-07
I think users don't always want to see where all the system files are; they just want to get stuff done. Personally I like to use more classic Window Managers, and just work from the command line. It enables me to get more advantage out of linux. If I want an easy desktop witha startmenu, I can just use Windows.

Mark

P.S. I think I will try ROX out...

---

### Post by Lovechild on 2005-05-07
doesn't sound like it would be very usable, a design feature of GNOME I'm personally very fond of..

---

### Post by N'Jal on 2005-05-07
Personally i always wanted to know where Linux install software. in windows its normally C:\Program Files\whatever

But in Linux i really don't know. I have installed Neverwinter Night's Acrobat Reader 7 and Realplayer 10 all to /usr/local/whatever but i dunno if i should have.

If there was a difined place to install software instead of throwing it everywhere i would find it easier, but hey i'm a kinda n00b, been saying that almost 2 years now

---

### Post by Psquared on 2005-05-07
[QUOTE=markw]I think users don't always want to see where all the system files are; they just want to get stuff done. Personally I like to use more classic Window Managers, and just work from the command line. It enables me to get more advantage out of linux. If I want an easy desktop witha startmenu, I can just use Windows.

Mark

_P.S. I think I will try ROX out..._[/QUOTE]

I'm thinking about it too. I'm not quite sure how the install works. The site describes something called "zero install" which I assume means you run the apps remotely. This has been tried before and doesn't work -- or at least few people have adopted it or demand it. The old "apps on tap" model.

What I want is to install it as a true DE that I can select on login. Its going to take some more investigation I think.

If you get it to work (or if I do) let's agree to post the procedure and the steps to set it up as well as the results.

---

### Post by poofyhairguy on 2005-05-07
I disagree with this....

> However, recent desktop efforts (such as KDE and GNOME) seem to be following the Windows approach of trying to hide the filesystem and get users to do things via a Start-menu or similar. Modern desktop users, on Windows or Unix, often have no idea where their programs are installed, or even where their data files are saved. This leads to a feeling of not being in control, and a poor understanding of how the system works. 

Screw that. That is one person's opinion. I can feel in "control" real easily again (by opening the terminal). But I don't want to have to deal with it everyday. Thats why KDE and Gnome exist- not to burden the power users!!!!

I don't care to know where my programs are installed or where my data is. I care that my programs RUN and that my data can be found. Apt-get + Gnome + Beagle make being a power user not matter, and I kinda like that even as a power user. 

I don't need to know how to bootstrap a kernel or compile an app. or "get around" on the CLI to enjoy Linux that is a good thing. Only people who get paid to hack on Linux should know these things.

Give the rest of us those wonderfully large GUIs....

---

### Post by Psquared on 2005-05-08
Well, its a moot point for the time being. Compiling it requires GTK+2.2 or higher. That is not available on Ubuntu Hoary and I can't figure out if its available for Breezy or not. I've posted a message in the backports forum requesting it if its available, but I have not hear from Jdong yet.

I could try and compile GTK myself, but I'm not comfortable doing that yet.

Funny thing is, GTK+2.2 is available in Fedora and Mandrake. I may install FC3 just to try the Rox-filer-sessions out.

---

### Post by crane on 2005-05-08
Again, another reference to windows. BAH
You want to know how or where your programs are installed, then Google, read, or ask questions. If you don't want to know where they go then don't.
I have heard this before, "in windows, I know where my apps are going or are installed " 
No one knew where they were installed the first time they started working with windows, But they learned.

GUI interfaces are good, so is terminals. I also don't think Gnome, KDE or any other gui is trying to look like windows. I mean come on. How else can on deign a desktop, Icons and menus. I happen to like the way linux handles it's file system. Very easy to follow and makes sense.

---

### Post by salsafyren on 2005-05-08
Of course Gnome and KDE are Windows-like. Windows copied MAC and Linux DEs copy Windows and MAC hence the similarity.

People want to use apps not worry about the Desktop Environment which should just get out of the way or help the user if he needs help. Micromanagement of files is a thing of the past. Stay in your own world while the rest of us moves on.

---

### Post by Stormy Eyes on 2005-05-08
[QUOTE=Psquared]Well, its a moot point for the time being. Compiling it requires GTK+2.2 or higher.[/QUOTE]

If you're using GNOME 2.10, and you probably are if you're using Hoary, then you have the required GTK+ version. You probably have GTK+ 2.4 or even 2.6.

---

### Post by Gentist on 2005-05-08
I'm currently running ROX-Filer together with IceWM as a low-resource demanding, userfriendly setup. I have to say that while ROX-Filer is great when it comes to handling icons and backgrounds for a "Windows user", the actual file manager is crap. It's clumsy, has a few odd behaviours that you can't really work around, etc. The only time I use it myself is when I need to change something within ROX-Filer (like when I need to change the background). Basically, what it misses is proper shortcuts (for example, the default shortcut to delete a file is Ctrl+X). Some of this can be changed, but it's way too confusing for a normal Windows user, and way too clumsy for a power user.

I'm hunting for a file manager that isn't bloated and isn't too confusing for a Windows user (looks and acts similar to Windows Explorer). Preferably it should be able to handle desktop/pinboard icons. The closest I've come is ROX-Filer, though I'm sure there has to be something better out there. If anyone knows of something better, please let me know. :)

---

### Post by Psquared on 2005-05-08
[QUOTE=Stormy Eyes]If you're using GNOME 2.10, and you probably are if you're using Hoary, then you have the required GTK+ version. You probably have GTK+ 2.4 or even 2.6.[/QUOTE]

Yeah, I found that out. When compiling I got a message that gtk was not the right version, but when i installed libgtk-dev it worked.

However, rox is choking on the icons. I'm working on it, but so far no go.

---

### Post by Psquared on 2005-05-08
[QUOTE=Gentist]I'm currently running ROX-Filer together with IceWM as a low-resource demanding, userfriendly setup. I have to say that while ROX-Filer is great when it comes to handling icons and backgrounds for a "Windows user", the actual file manager is crap. It's clumsy, has a few odd behaviours that you can't really work around, etc. The only time I use it myself is when I need to change something within ROX-Filer (like when I need to change the background). Basically, what it misses is proper shortcuts (for example, the default shortcut to delete a file is Ctrl+X). Some of this can be changed, but it's way too confusing for a normal Windows user, and way too clumsy for a power user.

I'm hunting for a file manager that isn't bloated and isn't too confusing for a Windows user (looks and acts similar to Windows Explorer). Preferably it should be able to handle desktop/pinboard icons. The closest I've come is ROX-Filer, though I'm sure there has to be something better out there. If anyone knows of something better, please let me know. :)[/QUOTE]

I agree the rox-filer manager by itself is only average. Actually, I like xffm4 (and nautilus when it is setup properly) as a file manager much better. The only advantage to rox is thumbnails - when it works.

What I am interested in the full blown desktop environment which requires quite a few more packages.

---

### Post by nuopus on 2005-05-11
[QUOTE=poofyhairguy]I disagree with this....
 
 
 
Screw that. That is one person's opinion. I can feel in "control" real easily again (by opening the terminal). But I don't want to have to deal with it everyday. Thats why KDE and Gnome exist- not to burden the power users!!!!
 
I don't care to know where my programs are installed or where my data is. I care that my programs RUN and that my data can be found. Apt-get + Gnome + Beagle make being a power user not matter, and I kinda like that even as a power user. 
 
I don't need to know how to bootstrap a kernel or compile an app. or "get around" on the CLI to enjoy Linux that is a good thing. Only people who get paid to hack on Linux should know these things.
 
Give the rest of us those wonderfully large GUIs....[/QUOTE]
 
I tend to disagree. Many of us grew up on the console, and having to point and click is a lot more difficult than typing the command. The GUI is a nuisance to me... I will bet money I can do anything as far as management quickly and more efficiently (to me) than you can with any GUI.
 
It is all relative to past experience and depends on your preference.
 
BTW ... I don't get paid to hack on linux ... I use the CLI for everything and that is why I love it. If Linux ever went pure GUI like crapindows I would probably dump it.

---

### Post by davidgypsy on 2005-05-12
I just want to get my work done... all the silly politics don't interest me.

---

### Post by markw on 2005-05-14
I want to get work done, and the console is the way I can get my work done most efficiently. However GUIs are nice for speeding the process up a little (I.E. Some file management). However the only good way to configure things is with config files. I like to control my system and make it a tool, not have it control me.

I got it to work on Arch (gasp!). What I did was install ROX, and then add "rox --pinboard=MyPinboard &" to my ".xinitrc". ROX is not a window manager, but more of a desktop environment. Right now I am using it with openbox 3 (all xml configs; very nice) and pypanel, and works out very well. I enjoy the way it uses applications as single directories. Its not the best file manager, but its unique, does the job and fast. Those three things are enough for me. I might try to get it to work in Ubuntu soon, and report back with a howto or something. I really like what a I see so far about it, and am looking more into it (as well as packaging some apps into its format).

---

### Post by markw on 2005-05-14
P.S. A screenshot: [http://www.markwatson.us/share/screenshotopenboxrox.jpg](http://www.markwatson.us/share/screenshotopenboxrox.jpg)

---

### Post by bored2k on 2005-05-14
[QUOTE=markw]P.S. A screenshot: [http://www.markwatson.us/share/screenshotopenboxrox.jpg](http://www.markwatson.us/share/screenshotopenboxrox.jpg)[/QUOTE]
 How fast is openbox running compared to xfce, iceWM, etc ? I'm a KDE lover, but I love speed. If one of them is worth trying using the gnome-panel I'd be up for the challenge (need that panel because of my brother -- quick way for him to click reboot rather than power off the HARD way).

---

### Post by greenwom on 2005-05-14
I find it funny when an average and even an advanced  Windows user thinks he knows where his apps are installing.  A great portion of Windows users don't know or understand the windows registry.  

Ask a windows "super" user why he can't get all the crappy spyware of his machine.

---

### Post by bored2k on 2005-05-14
[QUOTE=greenwom]I find it funny when an average and even an advanced  Windows user thinks he knows where his apps are installing.  A great portion of Windows users don't know or understand the windows registry.  

Ask a windows "super" user why he can't get all the crappy spyware of his machine.[/QUOTE]
 I totally agree. I totally agree. Oh yes, I agree. I enjoy watching those "veterans" brag about their knowledge in front of people with "less knowledge but more conscience". I like to ask them the simple "what can you do in a computer?". 9 out of 10 answer "everything" or "whatever everyone can do". That's a sign of ignorance right there. I usually follow with a --while acting like the most ignorant african tribe member without technology ever- "what do you call everything?" >everything dude. "I don't know man explain :-|" >chat, fix computers "fix how ? at this point, theyre shaking already >uh.... "well ok what else ?" >I used to be a good hacker ---they all "were" lol .. "really ? wow amazing, what program you used ?" >..... 

I don't know why people keep tryingto be something they aren't. I don't know how to program, thus you'll never see me having a conversation with anyone on this subject. I just dont get it..

---

### Post by Gentist on 2005-05-15
[QUOTE=Psquared]I agree the rox-filer manager by itself is only average. Actually, I like xffm4 (and nautilus when it is setup properly) as a file manager much better. The only advantage to rox is thumbnails - when it works.

What I am interested in the full blown desktop environment which requires quite a few more packages.[/QUOTE]

The problem as I see it is that there's all these Window Managers and a few fullblown desktop environments (KDE, GNOME, XPde, etc), but there are few proper standalone File Managers.

What I would like to see is either a standalone File Manager which is Windows-user friendly (IE fairly similar to Explorer, layout-wise), or one developed for IceWM (which is an excellent low-resource, user friendly, WM) which is optional. I never really understood why the components in a desktop environment had to be so tightly integrated. If you want to install Nautils, for example, it is not only bloated, it's got one hell of a dependency list (IIRC).

If IceWM were to get a low-reseource filemanager and desktop icons (pinboard), it would make a great software package for old computers.

---

### Post by Stormy Eyes on 2005-05-15
[QUOTE=bored2k]How fast is openbox running compared to xfce, iceWM, etc ? I'm a KDE lover, but I love speed. If one of them is worth trying using the gnome-panel I'd be up for the challenge (need that panel because of my brother -- quick way for him to click reboot rather than power off the HARD way).[/QUOTE]

I'd say that Openbox is definitely lighter and faster than XFCE, and at least equal to IceWM. Also, you can use Openbox as a replacement for KDE's window mangler if you like.

---

### Post by raven on 2005-05-29
[QUOTE=greenwom]I find it funny when an average and even an advanced  Windows user thinks he knows where his apps are installing.  A great portion of Windows users don't know or understand the windows registry.  

Ask a windows "super" user why he can't get all the crappy spyware of his machine.[/QUOTE]


IMHO, I am almost an advanced user on MSXP, while n00b on Linux
and I don't need to delete any spywares 
cause I don't let them getting installed (4 years MSXP no problem
not even once)
and hope to be a moderate user on Linux
all in the user handling the OS
you can break a finger with a hammer, you can poke your eye with a drill
if you do not know how to use the tool
ask the proffessional
goes for all OS's
with all do respect

---

### Post by aysiu on 2005-05-29
This may sound like a silly question, but why do you want to know where your programs are stored? I'd say there might be two reasons:

1. You've somehow lost or want to create yet another shortcut to the program.
2. You wish to uninstall the program.

In both Windows and Linux, you don't uninstall the program by knowing where it is. You use add/remove program, Synaptic, or some other helper application. Some Mac advocates say Mac's program file system makes more sense, and you can drag a program from Applications to the trash, but I doubt most everyday users would do so, thinking they'd likely damage something.

As for creating shortcuts... well, I've generally found most programs to be in usr/bin. And it's not often that I need to create a new shortcut, so I can take the time to a "find" for the file name.

Finally, if the Windows user is paying attention (which is not necessarily a safe assumption), she may actually know where her programs are being installed, as most Windows installer programs specify the directory of install (c:\Program Files\name of program\). Of course, most people just click *yes* and *next* without reading stuff...

Also, what does it mean for a program to be located somewhere? Sure, the executable launcher of the program may be in Applications, Program Files, or usr/bin, but in Mac, Windows, and Linux, there are always libraries and other associated files that stored somewhere else.

The question of knowing what goes on behind the scenes should be a practical question, for most users: "Why do I need to know that?" Sure, you can know everything for the sake of bragging rights, curiousity, or whatnot. Still, most computer users use computers to accomplish a task. They do not want to know the inner workings of things.

---

