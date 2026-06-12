---
title: "Apt-get and Synaptic needs improvement"
date: 2007-11-08
forum: The Cafe
---

### Post by daynah on 2007-11-08
Today, my SPSS (windows only) decided not to let me use it. You know, when a big project is due. Thanks, proprietary software. So, with less than a week to do this project, I submit a ticket to my school's wonderful support team (cough) telling them that they'd better fix it for me, and then.. I go about trying to fix it myself.

My solution is to try to learn R or PSPP or something. One of these many linux statistical program equivalents. I wasn't doing this to begin with because I'm having enough problems with this class than to have to translate everything.

But now I have problems with apt-get.

I install r-base with apt-get and try to run it, and it isn't a command. Knowing that "R" is the name of the program, I run that, and it tells me that "litter" isn't installed .Litter? What? I'm trying to run R!

**So, first rule of package-ness I'd like to propose: When I install a package, and I want to run it, the name of the package I install should be what I use to run the program I installed.**

I find out that I need a front end for this program. Okay. I try not to wonder why, if this program apparently doesn't come with its own front end, that I never was able to get to the terminal section, but I go about installing RKWard anyway. Fabulous program, but I'm far too math stupid to use it.

So I go into synaptic and try to install something else. Something for stupid people. I understand synaptic not advertising, "This program is for stupid people, yeah YOU! Right THERE! The one who always worries if it's deb or tar.gz that's the hard one! Yeah this program's for YOU!" I get that. But (here's the second rule of package-ness) **when I install a program from synaptic, a GUI, it should tell me if the program has or does not have a gui!**

Lastly, I installed R, RKWard, and PSPP and none of them got added to my menu. Granted, two of those had no gui, but this leads me into the **third rule of package-ness: Any package installed should add itself somewhere into the menu so that I can find it.**

Yeah.

---

### Post by tehet on 2007-11-08
[QUOTE=daynah;3730884]So, first rule of package-ness I'd like to propose: When I install a package, and I want to run it, the name of the package I install should be what I use to run the program I installed.[quote]
Look at Imagemagick for instance and you'll see why this wont work.

I disagree with your other two points as well.

---

### Post by Anessen on 2007-11-08
Sounds like you'd be more at home with add/remove.

---

### Post by ltk5 on 2007-11-08
If the package doesnt appear in menu it ussually helps if you restart X again;
Then they appear - at least this works for me :)

---

### Post by kerry_s on 2007-11-08
that's start with your first oops "r-base" is a meta-package not a program, a quick look in synaptic tells you that. pic #1

so if you use the correct name of a actual application, it would have worked.

the menu, to me it's always been if'y, i have no problem doing my own. that does need to be fixed by the programmer who actually made the program, it has nothing to do with apt-get or synaptic.

---

### Post by daynah on 2007-11-09
Thanks, Kerry_S. Yeah, at that point I was just typing it through terminal. It took me a bit until I was like... what the heck is going on here and started googling and what not. It just blew my mind that when I typed "R" it told me about litter instead of just saying it wasn't a command. Like, whoa.

Speaking of, I need to go back and uninstall everything from the day-o-madness. My project is doing alright! Yay!

---

### Post by osxcapades on 2007-11-09
I haven't had too many problems with apt-get, personally. In Synaptic or apt-get, you can usually find descriptions of each package. If your having problems running the program, check its documentation.

The only problem with Synaptic is that it's too slow when it refreshes its list of software. You usually don't need it anyway.

---

### Post by FranMichaels on 2007-11-09
When dealing with command line, your best bet is to use "man" :)

As for simplifying, we need more of a mix of GUI and CLI, either with front-ends or just nice little features, like in nautilus. If you press ctrl+s, you could enter *.ogg, and it will select all the oggs in the folder.

Some sort of best of both worlds, the CLI can be so swift and efficient, while GUI's usually just require clicking around. 

:KS

---

### Post by daynah on 2007-11-09
:/ Thanks guys. But just because there's something to read to say why it is the way it is, which isn't the best way, *doesn't mean that it can't be improved to be more intuitive.*

And I know basic "navigate my computer" commands, thanks, though. :)

---

### Post by FranMichaels on 2007-11-09
I had stumbled upon this article yesterday, and your post reminded me of it.
The trick is finding the "best way". 

[http://labs.mozilla.com/2007/07/the-graphical-keyboard-user-interface/](http://labs.mozilla.com/2007/07/the-graphical-keyboard-user-interface/)

I did not mean to come off as just saying, read the manual and get used to it. 
For now, with certain applications, that's the only option.

ALL software could use improvements I say :)

---

### Post by Jussi Kukkonen on 2007-11-09
> **daynah said:**
> **third rule of package-ness: Any package installed should add itself somewhere into the menu so that I can find it.**

Ubuntu would then have over 1400 menu items by default. I don't think you'd find anything.

---

### Post by Polygon on 2007-11-09
the thing about it not getting added to the menu is not apt-get or synaptics fault, it is the fault of the maintainers of the packages that didnt include a .dekstop file to go wherever the menu items are stored.

and also,the package name not being the name of the program, another package maintainer fault, not the actual program/apt/synaptic

and third off, i think the description in the program is enough to tell if its a cli or gui program

but here is what ive found useful if i dont know how to run a program. go to the package you just installed > properties, and go to installed files, and there should be something in /usr/bin/SOMENAMEHERE

somenamehere is usually the command you need to enter

---

