---
title: "is gnome-launch-box the best program ever?..."
date: 2007-10-29
forum: The Cafe
---

### Post by ice60 on 2007-10-29
yes, it probably is :) well it's good :| so has everyone been using this for ages? why didn't anyone tell me about it :confused:

gnome-launch-box is a program launcher a little like alt-F2, but on steroids lol

you can launch a program -
***program name <enter>***

you can launch a CLI program and it will run it in a terminal for you e.g. -
***top <enter>***


you can search for files and directories too 8)

here's how to make a keybinding for it -
[http://developer.imendio.com/node/77](http://developer.imendio.com/node/77)

i made the keybinding alt-F3, that's not used for anything else is it?

it's in the repos -
**sudo aptitude install gnome-launch-box**

---

### Post by p_quarles on 2007-10-29
Sounds like KDE's Katapult. I'm a fan of that. Good to know that Gnome has something similar.

---

### Post by Calash on 2007-10-29
Sounds like the new run line in Vista, one of the better improvements to general usability in the OS IMHO.  Glad to see a similar function in Ubuntu, I will check it out tonight.

---

### Post by macogw on 2007-10-29
Is it like QuickSilver on OSX?

---

### Post by rowanparker on 2007-10-29
Doesn't work for moi.
Segmentation Fault or something :(

---

### Post by ice60 on 2007-10-29
yeap, it's like quicksilver and Katapult, i have got vista but i never use it so i'm not sure if it's like the vista program. but, i suppose it's a bit like start++ for vista 
[http://lifehacker.com/software/top/download-of-the-day--start%252B%252B-windows-vista-240173.php](http://lifehacker.com/software/top/download-of-the-day--start%252B%252B-windows-vista-240173.php)

---

### Post by ice60 on 2007-10-29
> **rowanparker said:**
> Doesn't work for moi.
Segmentation Fault or something :(i did a search for it before i posted and noticed others had that problem too, but i thought that was with olders versions of it, or older versions of ubuntu. i tried it on gutsy. there might be some posts about how to fix it if you search the forums.

---

### Post by ticopelp on 2007-10-29
Looks cool -- unfortunately, I can't seem to get it to work with Compiz Fusion enabled. :(

---

### Post by rowanparker on 2007-10-29
> **ice60 said:**
> i did a search for it before i posted and noticed others had that problem too, but i thought that was with olders versions of it, or older versions of ubuntu. i tried it on gutsy. there might be some posts about how to fix it if you search the forums.
Thanks.
I'll have a look around later.
It looked good before it crashed anyway :)

---

### Post by ice60 on 2007-10-30
i'm sorry it doesn't work for all of you :( 

i upgraded my ubuntu from feisty, so maybe i have slightly different system files and that's the difference between it working and Seg. Faulting??

if it makes you feel any better, it is slower than alt-F2, so i'm still using that more.

i'm no expert, so all i can say is you can run it from a terminal (which it sounds like you're already doing) to have a look at any error messages that may be useful.

you can also run it with strace too to watch all the calls it makes.
**strace gnome-launch-box**

---

### Post by bennyp on 2007-11-01
very nice.
Also try gnome do

---

### Post by Ultra Magnus on 2007-11-01
Its an awesome program... but for some reason it has never been able to open firefox - which is kind of annoying

---

### Post by macogw on 2007-11-01
Yep, segfaults here too, even if I compile it.

---

### Post by davidsiegel on 2007-11-10
Check out GNOME Do: [http://launchpad.net/gc](http://launchpad.net/gc)

GNOME Do allows you to quickly search for many objects present in your GNOME desktop environment (applications, Evolution contacts, Firefox bookmarks, files, artists and albums in Rhythmbox, Pidgin buddies) and perform commonly used commands on those objects (Run, Open, Email, Chat, Play, etc.).

Here's a preliminary package: [ATTACH]49739[/ATTACH]

---

### Post by enchance on 2007-11-11
It's a great program. GNOME Do isn't worth it since it's still in production. I don't have any problems whatsoever with it and it runs firefox just fine too.

---

### Post by davidsiegel on 2007-11-11
You're right, GNOME Do isn't worth it since it's still in production. On that note, Linux, Ubuntu, Firefox, Compiz fusion, Pidgin, OpenOffice, etc. aren't worth it either - they're still in production too. Better stick with GNOME Launch Box - no one is working on it anymore, so you don't have to worry about pesky new features or other improvements.

On a non-sarcastic note, GNOME Do will let you manually type URLs to open in your default browser. GNOME Launch Box can only open Firefox bookmarks (I actually submitted a patch to enable this in GNOME Launch Box, but it the developers didn't seem interested so I wrote GNOME Do). Also, GNOME Launch Box only lets you open applications in your GNOME main menu, whereas GNOME Do indexes those applications, AND the hidden ones, AND your preference applications, AND system administration applications, AND lets you enter commands and run them in a shell.

---

### Post by Kalli on 2007-11-12
I think he just meant that it's really not quite ready for the big time yet, there are some basic things to be done. On the other hand I use it and got it running with no bother and it's working great for me so I don't know why anyone shouldn't "bother"...

---

### Post by davidsiegel on 2007-11-12
Packages are now available in a PPA archive:

>  Do packages are currently available through a Launchpad PPA. These packages are from the still-in-development codebase and, like the project, are potentially unstable. Please make sure to provide feedback on packages to the mailing list.

 To use the packages from the PPA, add the following lines to your /etc/apt/sources.list file:

 deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main

 and install GNOME Do with the command: sudo apt-get update && sudo apt-get install gnome-do.

 For Hardy packages, change "gutsy" in the lines above to "hardy".

 PPA downloads are not signed so you have to ignore the error about "The following packages cannot be authenticated."


This will keep you updated on this work in progress ;)

---

