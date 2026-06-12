---
title: "apt-get or aptitude for server GUI ?"
date: 2009-02-06
forum: Server Platforms
---

### Post by darksideforge on 2009-02-06
I'm slightly confused about how to install either the kde or gnome desktop on my server from the command line.

From the user $ would I be better off typing
```
$sudo apt-get install kubuntu-desktop
```

or

```
$sudo aptitude
```



Last questions:
I'm assuming that once I do whichever command is recommended above, a graphical desktop environ isn't just going to pop up. How do I get to it? Once I Restart, will it show after the restart or are there other commands required to access the desktop in GUI?

---

### Post by kerry_s on 2009-02-06
that command will install the **whole** kubuntu setup, are you sure that's what you want?

you can just grab the minimum:
example:
sudo apt-get install xorg kdm kde-base

or go even lighter, just use a low resource window manager.
example:
sudo apt-get install xorg gdm fluxbox


the commands "apt-get" and "aptitude" doesn't matter they both do the same thing, it's just a matter of preference. i prefer apt-get it's never done me wrong, i have had aptitude bone my install in the past, so it's 1 of the first things i uninstall.

---

### Post by darksideforge on 2009-02-06
Thanks Kerry!

All I want graphically speaking is just what you see on your desktop: access to whatever applications are installed (browser, text editor, etc), a shortcut to different places (documents, pictures, etc), and Preferences. So you're right...I don't want the entire package.

Once I use the sudo apt-get install, do I restart for the GUI to show up or what? In other words, what command do I use in CLI to get there?

---

### Post by darksideforge on 2009-02-06
Kerry, can you explain what is involved here:

```
sudo apt-get install xorg kdm kde-base
```

I was just browsing through aptitude, just looking at the different programs, and it looks like kde-core is what I want.

---

### Post by volkswagner on 2009-02-06
> **darksideforge said:**
> Thanks Kerry!

All I want graphically speaking is just what you see on your desktop: access to whatever applications are installed (browser, text editor, etc), a shortcut to different places (documents, pictures, etc), and Preferences. So you're right...I don't want the entire package.

Once I use the sudo apt-get install, do I restart for the GUI to show up or what? In other words, what command do I use in CLI to get there?

Although this [document]("https://help.ubuntu.com/community/Installation/LowMemorySystems") does not break things down to the "core" it is useful for your task.

My own observation between aptitude vs apt-get is how each handles dependencies and recommended packages.

Again these are just my observations; with aptitude it seems both recommended and dependent libraries are installed without warning or information.

With apt-get you get a list of dependent packages that will be installed and a second list of recommended libraries which you would need to install manually if so desired.

Another thing I noticed if you have a package installed already and you try  to apt-get install it, you will be notified you already have the latest version.  With aptitude, it just says no packages installed, it acts as though it has just "failed" (no informative output).

See for yourself:
```
sudo apt-get install nautilus
[sudo] password for eric:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]nautilus is already the newest version.[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```

eric@Vista:~$ sudo aptitude install nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
[COLOR="Red"]No packages will be installed, upgraded, or removed[/COLOR].
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done 
```

Please correct me if my observations are far off.  ;)

---

### Post by hyper_ch on 2009-02-06
why do you want a gui on a server?

---

### Post by kerry_s on 2009-02-06
> **darksideforge said:**
> Kerry, can you explain what is involved here:

```
sudo apt-get install xorg kdm kde-base
```

I was just browsing through aptitude, just looking at the different programs, and it looks like kde-core is what I want.

kde-core is good to.

xorg <- you need this, this is X itself
kdm <- this is the login manager, when you reboot it will go straight to the gui. if you don't want that, you can manually log in and type> **startx**

---

### Post by kerry_s on 2009-02-06
> **hyper_ch said:**
> why do you want a gui on a server?

does it really matter? everyone has there own preference, it may not just be a server, double duty these days has become standard, some work faster in a gui, some don't like doing it remotely, some just prefer the visual aspect. so what if it uses extra resources, in the end all that matters is it does what you want.

---

### Post by hyper_ch on 2009-02-06
> **kerry_s said:**
> does it really matter?
It does when a person is not informed ;)

---

### Post by kerry_s on 2009-02-06
> **hyper_ch said:**
> It does when a person is not informed ;)

"informed"? are you talking security?
as far as i know, you can have a gui and still be secure.

my belief is, if your going to have a server, your responsible for it.

---

### Post by hyper_ch on 2009-02-06
> **kerry_s said:**
> "informed"? are you talking security?
as far as i know, you can have a gui and still be secure.

my belief is, if your going to have a server, your responsible for it.
So much for being informed... you just jump to the conclusion of security impacts only while there is a plethora more things... see why informed choice is necessary?

---

### Post by punx45 on 2009-02-06
i aptitude for search or show, and apt-get to install upgrade and remove.  just 'cuz.

---

### Post by kerry_s on 2009-02-06
> **hyper_ch said:**
> So much for being informed... you just jump to the conclusion of security impacts only while there is a plethora more things... see why informed choice is necessary?

no, your just being cryptic and ain't informing jack****. it doesn't matter why he wants a gui, it's not your problem. :evil:

---

### Post by darksideforge on 2009-02-06
> **hyper_ch said:**
> It does when a person is not informed ;)

Actually, you're both right LoL! Not only was I uninformed, but to be perfectly honest I'm still a noob at CLI. I'm learning by leaps and bounds, but nowhere NEAR competent enough to do the things I want to do with my server experiments.  More on all of this in a few.

---

### Post by inphektion on 2009-02-06
use aptitude for everything, install search show purge, etc.
it handles dependencies perfectly and is one command (with sub cmds) for all the apt-* commands.

---

### Post by darksideforge on 2009-02-06
In hindsight, I realize I should've probably included more information in my original question. However, as I'm a newbie where servers are concerned (although I've been a desktop Ubuntu user for almost 5 months now), and since this isn't the "Absolute Beginner" section of the forum, I didn't want to clog up the board with a useless question/explanation.

In general, here's the scoop: I recently took a job doing some odd jobs for a professional programmer. Programmer he is, SysOp he's not (okay, that is SO totally not fair...the guy's actually a genius, he just doesn't have time for mundane things like backups when he should be programming). In short, one of my primary responsibilities is to ensure routine backups are performed for both on-site as well as off-site security. I'm also in charge of downloading and installing security updates (or checking for them) daily.

I have some NT4.0 experience and a touch of W2K and W2K3S experience (although I haven't done anything with any of it since around 2003 or 4. So, at work we have two servers: one is Windows 2003 Server and the other is Red Hat Enterprise.  The Windows handle primary file storage and the backup/storage program while the Red Hat handles mail and webserver duties.

There are approximately 10 backup clients in the system, most of which are stand alone desktops running XP and/or Ubuntu Desktop 8.10 in either single or dual boot situations. None of the workstations are Thin Clients, although I'm not certain why in most cases. WinXP is primarily being used for, believe it or not, strictly for MSWord and MSExcel. All actual programming is done via Ubuntu Desktop or two custom micro-systems running the DO 178 B compliant LynxOS...managed by a light Ubuntu Server. Currently Lynx is not connected to the rest of the network (for compliance purposes). There are also three laptops, two of which are running XP and one of which is running (*&^#$.  Yeah...that's the "V" word...at least until I con the boss into letting me destroy the Vsh*ta.

However, in general, that's the network configuration I've been handed. I've never had any experience with RHE nor UbuntuServer, so this is all a learning process. RHE came with a kde GUI and I like the way it looks...no fluff and all business. Unfortunately, 90% of my time at work is on the W2K3 Server.

My ultimate goal, and the boss has given the go-ahead for this, is to figure out a proper Ubuntu Server setup that will manage everything, to include the Windows-based backup program (unless I can find something equivalent or better), and then completely get rid of ALL Microsoft software in the office. The boss says that if I can figure out how to do this, he'll spring for a new Xeon to go into the rack and give me two new +TB drives in it and I can have it solely for the Ubuntu Server and have time to bring it up to speed and transfer data to it, and implement it. Once I do that, I can take the existing Windows Xeon in the rack and use it for other stuff...it's got a 300Gb and 150Gb iSCSI in it. (All backups are via an IBM Ultrium LTO, by the way.)

I ended up using sudo aptitude to go through and pick what I wanted. I ended up downloading about 125 extra files. The GUI I got out of kde-core just wasn't enough...no browser (although it had browser support), no good graphic file server/file management system, and not a whole lot else for me to work with.  All of my original problems are now solved, although I'm probably a little top-heavy at this point.

My next ordeal will be to find a graphical "C" programming program that I can play around in...any suggestions?

:popcorn:

---

### Post by kerry_s on 2009-02-07
dang dog, you got a lot ahead of you. good luck.

yeah the kde-base is a little more than the kde-core.
by the way "konqueror" the kde filemanager is also a web browser. ;)
light reading if you want to:
[http://www.kde.org/](http://www.kde.org/)

no ideas on a c program program, sorry.

---

### Post by hyper_ch on 2009-02-07
> **kerry_s said:**
> it doesn't matter why he wants a gui, it's not your problem. :evil:
it matters and well, it is not my problem but my responsability ;)

And as he says, in the end he wants a proper server setup he doesn't want to have a gui on there ;)

Btw, on a server rather use apt-get instead of aptitude. Apt-get will only install the required dependencies, aptitude will also install the recommended packages. On a server you do want to have installed as little as possible.

And if I correctly understand, the main issue is how to create backups from those XP machines?

---

### Post by darksideforge on 2009-02-07
> it matters and well, it is not my problem but my responsability ;)

Actually, it is NOT your responsibility.
> 
And as he says, in the end he wants a proper server setup he doesn't want to have a gui on there.

That's ***not*** what I said; what I said was that I wanted a proper server setup, and many (and let's *GASP* all remember that the *_most_* popular server environment in the world uses a GUI to get things done. In addition, many other server systems use GUI and in this, Ubuntu appears to be in the vast minority. _Your_ definition of a "proper" server setup is just that: your *_opinion_*.  I appreciate hearing your opinions, but we should probably remember to separate *your opinion* from _fact_.


> And if I correctly understand, the main issue is how to create backups from those XP machines?

No, the main issue is how to control ten different workstations (not light terminals), running a combined total of 5 different OS's, from one single server. The server will be a combined file server, backup machine, music server, and webserver...as well as controlling Ethernet and two wireless routers (g/n).

---

### Post by hyper_ch on 2009-02-07
> **darksideforge said:**
> Actually, it is NOT your responsibility.
Actually, it is my responsibitily ;) If you try to do something out of wrong understanding then it should be anyone's responsibility to point this out. Nobody knows everything and helping others should be everyone's responsibility.

> **darksideforge said:**
> That's ***not*** what I said; what I said was that I wanted a proper server setup, and many (and let's *GASP* all remember that the *_most_* popular server environment in the world uses a GUI to get things done.
You said:
> **darksideforge said:**
> My ultimate goal, and the boss has given the go-ahead for this, is to figure out a proper Ubuntu Server setup that will manage everything, to include the Windows-based backup program (unless I can find something equivalent or better), and then completely get rid of ALL Microsoft software in the office.
There is no mentioning of a gui and a proper server setup does not use a gui... 99.999% of linux server do not run a gui. And then, what's the most poplular server environment? It's not windows ;) it's those linux servers. And because windows uses a gui, it doesn't make it better. Remember, MSIE is deeply integrated into Windows, so if you find a small weakness in MSIE then you own the whole server ;)

> **darksideforge said:**
> In addition, many other server systems use GUI and in this, Ubuntu appears to be in the vast minority.
As said in the other thread, most linux distros I know will not install a gui by default. Even less those distros that have a "server" edition. RHEL Server isn't a server, when you install it you will see it installs more like a desktop than a server.

> **darksideforge said:**
> _Your_ definition of a "proper" server setup is just that: your *_opinion_*.  I appreciate hearing your opinions, but we should probably remember to separate *your opinion* from _fact_.
Then please give me stats on linux servers running a gui? Look at all those servers you can rent, those running linux have no gui...

> **darksideforge said:**
> No, the main issue is how to control ten different workstations (not light terminals), running a combined total of 5 different OS's, from one single server. The server will be a combined file server, backup machine, music server, and webserver...as well as controlling Ethernet and two wireless routers (g/n).
No clue about controlling windows desktops from a linux server (automatically) but controlling linux desktops is very simple by terminal.

---

### Post by darksideforge on 2009-02-07
> **hyper_ch said:**
> Actually, it is my responsibitily ;) If you try to do something out of wrong understanding then it should be anyone's responsibility to point this out. Nobody knows everything and helping others should be everyone's responsibility.


You said:

There is no mentioning of a gui and a proper server setup does not use a gui... 99.999% of linux server do not run a gui. And then, what's the most poplular server environment? It's not windows ;) it's those linux servers. And because windows uses a gui, it doesn't make it better. Remember, MSIE is deeply integrated into Windows, so if you find a small weakness in MSIE then you own the whole server ;)


As said in the other thread, most linux distros I know will not install a gui by default. Even less those distros that have a "server" edition. RHEL Server isn't a server, when you install it you will see it installs more like a desktop than a server.


Then please give me stats on linux servers running a gui? Look at all those servers you can rent, those running linux have no gui...


No clue about controlling windows desktops from a linux server (automatically) but controlling linux desktops is very simple by terminal.

If you're going to get on your soapbox, would you at least please answer some of my questions instead of repeatedly giving me your **OPINIONS** on things? The only solid answer you just gave me in that long diatribe was at the very end, which was that you don't have a clue how to control Windows desktops from a Linux server. Wonderful. Great. Thanks. Oh, and thanks for mentioning the word "terminal" in the last sentence.

Let me be clear, in case I've misstated something along the way: I'm not the only person in this office. The server ***_IS GOING TO HAVE A GUI_***..._forever_. If Ubuntu Server isn't up to this task I'll simply look somewhere else. Our Edition of **Red Hat Enterprise Linux Server** _auto-installed_ a GUI desktop environment when we installed it from DVD. At first I thought it was a kde desktop environment but after last night and today, I realize that it's actually Gnome with a very low graphics setting...similar to what the graphics were like in Windows 3.11 years ago.

---

### Post by hyper_ch on 2009-02-07
How does "i'm not the only person in this office" correlate to "the server is going to have a gui forever"? One thing has nothing to do with the other one. And well, I just did a RHEL install and although it's named "server" it's rather a desktop. Furthermore it's not "auto-isntalled" but "auto-selected" and last even the RHEL manuals advice against using a gui on a server *surprise, surprise* although they suggest to run x clients is ok.

---

### Post by darksideforge on 2009-02-07
> **hyper_ch said:**
> How does "i'm not the only person in this office" correlate to "the server is going to have a gui forever"? One thing has nothing to do with the other one. And well, I just did a RHEL install and although it's named "server" it's rather a desktop. Furthermore it's not "auto-isntalled" but "auto-selected" and last even the RHEL manuals advice against using a gui on a server *surprise, surprise* although they suggest to run x clients is ok.

As far as RHEL being "more a desktop than a server" I can't answer you. I just don't have the knowledge that you do on the subject. I can only tell you what the box and disk say they are, and what the Applications menu looks like. It does what is needed, but it isn't Ubuntu. I want Ubuntu that will do what RHEL is currently doing alongside Windows 2003 Server Edition. If Ubuntu Server won't do that, then I'll have to go somewhere else...sadly. Do you have any idea if Ubuntu Server will do what I want? Of so, tell me so and I'll leave you alone...I'll install a GUI, not tell you that I'm installing a GUI, and figure it out on my own or through Private Messages here on the community board (i think I might've posted enough to have PM priveledges...if not I'll just harass the admin folks until they give it/them to me).

I'm interested in the x clients...xorg etc. Not that I have any experience with them of course, but i've seen some posts suggesting them and their GUI.  Let me know what you think about them if you have time.

I'm in a situation where I don't have the time needed to learn all of the CLI commands and processes needed to do all of the tasks I'm required to do on a daily basis. I've got to have a GUI for now (although I practice my CLI skills every day) and I'd like that GUI to be an Ubuntu GUI because I like the desktop so much.

---

### Post by dcstar on 2009-02-07
> **darksideforge said:**
> 
........
I'm in a situation where I don't have the time needed to learn all of the CLI commands and processes needed to do all of the tasks I'm required to do on a daily basis. I've got to have a GUI for now (although I practice my CLI skills every day) and I'd like that GUI to be an Ubuntu GUI because I like the desktop so much.

Then install the **ubuntu-desktop** meta-package and you will have one (along with all the desktop apps etc).

---

### Post by darksideforge on 2009-02-07
> **dcstar said:**
> Then install the **ubuntu-desktop** meta-package and you will have one (along with all the desktop apps etc).

Already done and have given up on the Ubuntu Server. Not enough support in the community boards without catching a load of crap for asking questions. I'll either make it work with the desktop or uninstall it and install the RedHat and learn it instead.

---

### Post by hyper_ch on 2009-02-08
> **darksideforge said:**
> I'm in a situation where I don't have the time needed to learn all of the CLI commands and processes needed to do all of the tasks I'm required to do on a daily basis.
Let's welcome another hacked zombie box :)

> **darksideforge said:**
> Already done and have given up on the Ubuntu Server. Not enough support in the community boards without catching a load of crap for asking questions.
Oh noes.... you mean you're entitled to receive support here and not being questioned about why you want do something in a specific way that is generally viewed as a bad idea? Oh noes... what happened to the world.

---

### Post by kerry_s on 2009-02-08
> **darksideforge said:**
> Already done and have given up on the Ubuntu Server. Not enough support in the community boards without catching a load of crap for asking questions. I'll either make it work with the desktop or uninstall it and install the RedHat and learn it instead.

sorry about that, kinda knew it was going to happen.
don't give up on the board, there are good people here, not everyone is stuck in the past and unable to change there ways, some of us understand it's a gui world, knowing the command line is great, but there are many ways to get things done.

a few tips:
ask 1 question at a time, try to be clear.
start a new thread for each question, so the thread doesn't drag on.
if you don't get a answer, try refreshing the question, put it a different way.
try not to get mad, ignore any counter questions thats off topic or does not help.

i'm am sorry i can't be of more help, right now i'm working 10 to 15 hour days, so i'm just to tired to deal.

---

### Post by hyper_ch on 2009-02-08
> **kerry_s said:**
> don't give up on the board, there are good people here, not everyone is stuck in the past and unable to change there ways, some of us understand it's a gui world

stuck in the past? Is that why M$ introduced the new POWER SHELL on its servers? hmmm...

---

### Post by kerry_s on 2009-02-08
> **hyper_ch said:**
> stuck in the past? Is that why M$ introduced the new POWER SHELL on its servers? hmmm...

who cares, doesn't help the OP.

---

### Post by hyper_ch on 2009-02-08
> **kerry_s said:**
> who cares
Obviously you do ;)

> **kerry_s said:**
> doesn't help the OP.
same goes for you

---

### Post by kerry_s on 2009-02-08
hey darksideforge, give this a read:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

it go's over some of the applications that might help you.

---

### Post by windependence on 2009-02-08
I'll suggest looking at Bacula or Amanda for backup.

You can use almost any Linux distro as a domain controller, dns server, dhcp server, file server, print server, or a number of other things done with Windoze boxen.

If you *must* have a GUI crutch, at least use a web interface like Webmin, eBox, or one of the many others available. They don't take near the resources from the box, nor do they introduce the security risks that a full blown GUI does. Contrary to n00b beliefs, the world does NOT run on a GUI, nor is the CLI outdated or old fashioned. If you wanted to get a job as a Linux admin, they would laugh you out of the office if you couldn't admin a box without a gui. None of us know all the commands, but the more you use the basic ones, the more you will remember, and before you know it, that light bulb will go off and you will wonder how you ever did it any other way.

You mentioned a graphical C programming environment. Do you mean a graphical IDE, or do you mean to write graphical programs? Just to let you know, because you seem a bit green at this stuff, C and C++ do not lend themselves well to WYSIWYG programming. Some IDE's like Borland's C Builder come close, but still, you have to learn to code, and THAT is far worse than the CLI. You may want to learn Linux scripting first, to get your feet wet. It isn't graphic, but it WILL be useful for you, and you will learn at the same time. BASH scripting would probably be best to start.

If you have any other questions, just ask, but I ain't gonna be easy on you with the GUI stuff. You'll thank me later. ;)

-Tim

---

### Post by darksideforge on 2009-02-08
For now I've given up on the Ubuntu Server idea...at least for learning the basics. I'm using RedHat to learn as well as Ubuntu Desktop 8.10. I'm going to print out some lists of CLI commands and try to memorize them and what they do, then hit the console on my desktop and practice moving around in the directories and performing minor functions like apt-get install's and remove's...and just go from there.  Some members have sent me links via PM for places to go study and I'll be doing that as well. The code stuff is entirely different from the network admin stuff...the C is what I'm studying now, but C++ will come later...it's all code to get different pieces of precision equipment to talk to one another. There'll be some Java in there too I'm sure.  Thanks for the great advice and post.

---

### Post by windependence on 2009-02-09
No problem. You're welcome.

As for learning, you don't have to memorize everything, just remember to use the man pages, even if they are sometimes cryptic. At least they will give you the options you can use.

Also, most commands have a help switch available by typing the command with --help behind it. That gives you a quick list of options you can use and also the syntax of the command.

If you are really interested in using the command line and learning C, I would suggest using something like FreeBSD, which is a true Unix. You can write code and compile right on the OS. If you need help in that area, just let me know.

-Tim

---

