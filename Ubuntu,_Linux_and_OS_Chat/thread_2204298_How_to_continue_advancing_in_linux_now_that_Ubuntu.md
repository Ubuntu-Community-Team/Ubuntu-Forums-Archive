---
title: "How to continue advancing in linux now that Ubuntu has become so user friendly"
date: 2014-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Christodoulou_Marios on 2014-02-07
I have not really found good advice on this issue (human advice not resources). So let me try to articulate my question in hope to create a discussion:

I turned to linux at 2006 after using it first at the university (openSUSE and some scientific debian based distros). I then went for ubuntu, my first installation was Hardy (8.04) which was awsome! Ever since (2008) I have stayed with ubuntu and installed it to about 20 other machines, for friends, family and for me. In my humble opinion Ubuntu has excelled in becoming super user friendly in very few years and has now a beautiful and modern GUI (the older Gnome was a classic too).

However, although I consider my self an experienced user and I always have some terminal open because I love tweaking stuff, getting feedback and troubleshooting, I feel that I hit a plateau in my lurning curve of linux. I now have familiarity with a variety of commands and manipulations, from constantly trying to push the functionality of my Ubuntu, however I am totally dependent on blogs, forums and documentation for even relatively simple stuff. I understand enough to change the commands proposed and figure out where things go bad. I generally get things to work, but I almost never manage to simply open the terminal and do something other than browsing and file manipulations, i simply do not remember the commands since they are structuressly scattered  in my mind. I have lately noticed that I install programs that are simply a GUI for a command and I always find that I understand better what is happening when I am at the terminal (you see all the errors for example so you can guess wher things go wrong instantly instead of searching for error logs or where that or this option is in the graphical menus).

In other words, I don't really feel I know any linux, I just learned how to be a very good user of Ubuntu. I want to take it to the next level but I am not sure what that level is. I am not an IT professional (i do a phd in mathematical physics) or want to be one, so courses on how to become a linux administrator is maybe not what I need. I KNOW that this is a very vague question, I am not really looking for do this and that advice and that is why I do not mention any specific software, **I would simply like to hear from other people what they did when they arrived at this point**, **to round up the knowledge gathered from years of terminal usage to troubleshoot and personalise Ubuntu** **to their needs**.

---

### Post by oldos2er on 2014-02-07
I do 95% of my package management in a terminal, mainly because once I learned about apt-get, apt-cache, dpkg, etc., I could do things faster and/or more efficiently in a terminal than a GUI program.

I came to a point similar to the one you're at now about a year ago. I decided to install a window manager (i3) alongside KDE, and after a week or so I found myself using i3 exclusively, because it's quite fast and efficient (there are plenty other good wm's available; I chose i3 mostly because it can be configured with plain text files rather than some other wm's which are configured with a programming language e.g. Haskell or lua. I'm no programmer). 

 Next step for me was to install Ubuntu Server (no default DE or Xorg) and configure it to use i3, which I've done. 

This is the road I took trying to broaden my Linux horizons, yours may vary.

---

### Post by buzzingrobot on 2014-02-07
There's a difference between learning how to manipulate software, whether that's a word processing app or an app that facilitates adding and removing packages, and understanding how the software and the operating system it depends on actually work. Using a terminal or using a GUI tool, in the end, amounts to the same thing because both rely on the capabilities provided by the OS.  The difference is only in the interface that collects information from the user.

It looks like your next step is a foray into understanding how Linux works.  If you do not relish wading through texts on system design and programming (can't blame you) I'd suggest taking an historical approach.  Go back 30-40 years to the beginnings of Unix. Many of its founders were also effective writers.  Find what they've written about how Unix came to be, and why they made the choices they made.

---

### Post by whatthefunk on 2014-02-07
Use a more difficult OS like Arch or Gentoo.

Build your own Linux system using Linux From Scratch.

Choose a simple task and try to write a shell command that completes that task.  (The last one I wrote, now outdated, automatically detected whether my second monitor was receiving a feed and changed the Nvidia twinview settings accordingly.)

Stop using GUIs.

Study.

Find a project.  (Setting up a home server, crating your own theme, etc.)

Install 14.04 alpha.  Be warned that this could result in an unstable system, but it should give you several more problems to solve.

Try helping people on the forums.

---

### Post by Christodoulou_Marios on 2014-02-07
It is nice to see all the activity. Actually i got some pretty good advice already. I will let others speak their mind and make a list at the end of all the advice offered. 

Oldos2er, learning how to manage packages without a GUI like the Software manager is solid good advice I think and I understand why, but can you explain a bit how switching to a window manager like i3 (I checked it out it looks very cool but a bit too geeky for me) and installing Ubuntu Server helped you to advance in linux skills? 

Buzzingrobot, I agree that getting some historical perspective into linux is the fastest way to understand better the diverse habitat of linux, distros, packages etc although I had personally done this some years ago and still do. It is indeed what got me hooked on linux (also ideologically i guess) and convinced me that the pain is worth it.  

Whatthefunk, i think you completely understood my question and I will probably try to do some of the things you mention. I think trying a harder distro would help me to learn how to do better maintenance, diagnostics and system monitoring which is one of my goals in order to be in control of my system. Going for alpha version or setting up linux from scratch is kind of an overkill for me but could be good advice for others. As for a project, setting up a "personal network" is actually one of the things I want to do but not sure were to start from (i would like to set up a NAS, have my different computers talk to each other easily, access stuff from work, abroad, synchronise, backup etc). Also, I had thought too about starting to solve other people problems in the forums on subjects that I would like to become good at (as the ones mentioned above for example).

Other ideas?

---

### Post by tgalati4 on 2014-02-07
There are hundreds of ebooks and printed books about linux.  Find one and go through it.  You will quickly see what works and what doesn't and what has changed.  Linux is based on frameworks.  Pick a framework and study it.  For instance CUPS is for printing.  Have you tried printing something from 3000 miles away?  You can with [CUPS]("cups.org").  Get into the [framework]("http://cups.org/documentation.php").  Study it.  Pull it apart.  You will apreciate the power of just this one framework.  When you are done, pick another framework.

That should take a few years.

---

### Post by Bucky Ball on 2014-02-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldos2er on 2014-02-08
> **Christodoulou_Marios said:**
> Oldos2er, learning how to manage packages without a GUI like the Software manager is solid good advice I think and I understand why, but can you explain a bit how switching to a window manager like i3 (I checked it out it looks very cool but a bit too geeky for me) and installing Ubuntu Server helped you to advance in linux skills? 

In a nutshell, it's what whatthefunk suggested: Stop using GUIs. I wanted to learn how to install a minimal GUI (a window manager) from scratch, since Server is console-only by default.

---

