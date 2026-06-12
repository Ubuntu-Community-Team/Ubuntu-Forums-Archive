---
title: "In what direction would you like to see Linux grow?"
date: 2005-05-02
forum: The Cafe
---

### Post by darthsabbath on 2005-05-02
Hi, all,

I've been doing some thinking recently about what Linux (or GNU/Linux, if you prefer) needs (at least in my humble opinion) to make it accessible for Joe User, the guy who just wants to play his games, check his email, and what have you.  Just wanted to get some discussion going in this direction, or even just some thoughts as to what other people would like to see out of our beloved OS (when CUPS works over my network at least ;-)).

I think it's *ALMOST* there.  Certainly far better than Windows in regards to security, and a lot more fun. ;-) 

However, as I do Dell technical support (yeah, I'm uber-1337 :-P )for a living, I just cannot see the average Windows user successfully making a go at Linux.  This certainly is not due to any problems on the part of Linux, but rather, some behavior that I have seen in my time doing tech support.

1. Users like to make changes.
2. Users never remember what changes they make... or in their words "I didn't do anything!"
3. Users do not read dialog boxes, instead they blindly click "Yes," "Ok," or "Next."
4. Users want quick fixes.

This got me to thinking.  One of the greatest assets to Windows is System Restore.  In some cases, it's junk.  But when Joe User blindly makes changes to his system, and wants it fixed NOW!, it's a beautiful thing.  And, with the numerous config options and files for Linux, I could see something similar being useful.  Basically a script that stores backup copies of all your configuration files for certain dates, that could restore an entire backup of your configuration, or even just individual files.  

Maybe something exists already, but if not, once I get a little more knowledgeable about programming and Linux in general, I may look into coding something like this.  

And no, by the way, I don't want to see Linux "just like Windows."  But there are some things in Windows that are done right that Linux fails upon, and this is one of them.  

Any other thoughts on what you'd like to see?
Phil

---

### Post by Stormy Eyes on 2005-05-02
If all Joe User does is screw up the config files in his $HOME, then all you have to do is make the guy logout, back up everything whose file name does *not* start with ".", and then do "rm -rf .*" in the guy's home directory. Then have him log in again to a clean slate. Config files in /etc are a different story of course.

Personally, I wouldn't mind seeing more game developers do what BioWare and Id did with *Neverwinter Nights* and *Doom 3*: release a Linux client that the player can use if he's purchased the Windows version for the game data. I'm hoping NCsoft will do this with *Guild Wars*.

---

### Post by primeirocrime on 2005-05-02
I would like linux to grow on the mobile/handheld/pda market. It's the future anyway. 

Multimedia distribs. 
[agnula, dynebolic]

Open source hardware.

---

### Post by ssam on 2005-05-02
linux has got very good networking and routing systems, but they can be a pain to configure.

if there more good gui config tools, so you could 
press a button and turn on a web sever
click a share with button in the network preferences and share your adsl line to a wireless network
menu editing
right click on a folder and set it to share
easy to set up using a remote x server
why does anyone need to see an ip address when we have zeroconf?
power management prefs that let you make different profiles for being at my desk, in the garden, on a train, in a wireless cafe etc. each with choises of cpu speed, hard drive sleep time, system loging (to reduce hard drive writing), services, screen brighness, screen saver, wireless cards.  

the gui config tools need to be catogorised in a sane way for a user, not because of what the underlying unix system is. connection sharing and fire walls have little do with each other.

it is probably true that you can do cooler things with linux than windows. but too much of it is inaccessable.

---

### Post by darthsabbath on 2005-05-02
I agree on the GUI tools.  I'd love to see something for CUPS and SAMBA, for easily configuring those tools, beyond the basic GUI utilities provided with GNOME.  

I can understand the need for the config files for X-less servers, but on a desktop system like Ubuntu, a GUI interface is very much needed IMO.

Then again, maybe I just haven't found the right tool... if anyone knows of a good GUI (beyond localhost:631) for CUPS (and SAMBA too), let me know. ;-)

I'm excited about the possibilities of Autopackage as well.  I like the idea of wizards because it doesn't present the user with too much information at once.  If I were new to Linux, and I was told to use Synaptic to install new software, I'd feel a little overwhemled.  A wizard based apt tool would be able to step a new user through choosing and installing software.  This seems to be what [PC-BSD](http://www.pcbsd.org) is going for with their new package manager.  I like the looks of PC-BSD so far.  Never used BSD, but it looks really slick.

Phil

---

### Post by Stormy Eyes on 2005-05-02
[QUOTE=darthsabbath]Then again, maybe I just haven't found the right tool... if anyone knows of a good GUI (beyond localhost:631) for CUPS (and SAMBA too), let me know. ;-)[/QUOTE]

KDE has a sweet config tool for CUPS, but I've only started using SAMBA recently because I got burned using NFS on Gentoo, and I set up SAMBA with a config file. :)

---

### Post by TravisNewman on 2005-05-02
Faster, more stable, more secure-- improve on its strengths
Easier, in general-- improve on its major weakness

---

### Post by poofyhairguy on 2005-05-02
[QUOTE=darthsabbath]
This got me to thinking.  One of the greatest assets to Windows is System Restore.  In some cases, it's junk.  But when Joe User blindly makes changes to his system, and wants it fixed NOW!, it's a beautiful thing.  And, with the numerous config options and files for Linux, I could see something similar being useful.  Basically a script that stores backup copies of all your configuration files for certain dates, that could restore an entire backup of your configuration, or even just individual files.  [/QUOTE]

Good idea.

---

### Post by wondering_jew on 2005-05-03
I want to see something along the lines of autopackage get more support. I love synaptic because it checks all the dependencies and downloads everything i need for that program to work. For programs not in the repositories I usually have to configure look at all the error messages, figure out what I'm missing, install them configure again look at the error messages download more stuff and so on. This can be quite a task for someone as new to linux as myself and I almost miss the easier windows exe install files that installs a working program with a couple of clicks. Luckily most of what I need can be found within the repositories and everything else works so well that I don't miss windows at all... if only installing programs was not so much work.

---

### Post by KiwiNZ on 2005-05-03
The direction I would like to see Linux grow is the direction the users want it to grow. And not impose on the users what developers dictate they want and need then lock it down so self expression of the user is almost impossible . That direction was taken by another OS maker we all know .

Linux must stay free and not necessarily as in beer. I have no issue paying for it, if it gives me what I want and doesnt dictate to me how I want it .

---

### Post by Spoofhound on 2005-05-05
Improved support for mobility/laptop use. Make it stand out in terms of VoIP, internet telephony,etc. - put as softswitch in the desktop of every user who wants one. The old style telcos are starting to fight back in the converged multi-media space, new players are starting to offer interesting bundled offerings. Get linux to ride the convergence wave and build industry support from these players

---

### Post by 23meg on 2005-05-05
I'd like to see low latency kernels developed for realtime operations with multimedia software; looks like the 2.6.12 kernel will deliver the goods in this department.

---

### Post by weekend warrior on 2005-05-05
I'd like to see improved documentation. You can easily see the praise that ubuntuguide.org gets. For Joe User good, concise but relatively simple documentation is what's most needed. You have to ask yourself why Joe User is messing up his system, not think of a slipshod workaround after the fact. 

This is why things like system restore is not where I'd like to see linux go. M$ put this in precisely because it's far too easy to screw up their OS. This is where nix systems have a supreme advantage. This is where continued effort should go, making sure Joe User doesn't destroy his system in the first place. Preventative medicine is always less painful than a quacky cure. 

Offer good docs in the style of ubuntuguide and fewer Joe Users will need tech support.

---

### Post by weekend warrior on 2005-05-05
and of course offer a great supportive, creative community like this one!  :grin:

---

