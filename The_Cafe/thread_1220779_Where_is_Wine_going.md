---
title: "Where is Wine going?"
date: 2009-07-23
forum: The Cafe
---

### Post by keiichidono on 2009-07-23
Wine seems more like a back-end to me, and it's also lacking features that PlayOnLinux has that should probably be implemented upstream. Do you guys think Wine should focus on providing a back end with a simple optional GUI (like MPlayer) and allow development for more advanced front ends (Like SMPlayer is to MPlayer) or should they just include the PayOnLinux code and make them apart of their coding team?

---

### Post by Bucky Ball on 2009-07-23
> **CalvinB said:**
>  PayOnLinux

That is a great typo! :)

---

### Post by keiichidono on 2009-07-23
I was gonna fix it but it's funnier that way. :D

---

### Post by Bucky Ball on 2009-07-23
> should they just include the PayOnLinux code

haha. Sorry, I'm getting a bit off topic. As you were. :)

---

### Post by binbash on 2009-07-23
We do not need a front-end.That is why most of us using Linux

---

### Post by SunnyRabbiera on 2009-07-23
Personally I think Wine is fine on its own, Wine dos not have auto installer stuff but its still pretty easy for me.

---

### Post by Starlight on 2009-07-23
I think that Wine should go in the direction where no front-end is even needed, so that a person can simply install and run Windows programs in exactly the same way as they do it on Windows. :)

---

### Post by Sealbhach on 2009-07-23
> **Starlight said:**
> I think that Wine should go in the direction where no front-end is even needed, so that a person can simply install and run Windows programs in exactly the same way as they do it on Windows. :)

I use PlayonLinux and I like it but I think you're right, it would be better if Wine were seamless and you could just click on an .exe and you're done.

.

---

### Post by SunnyRabbiera on 2009-07-23
> **Starlight said:**
> I think that Wine should go in the direction where no front-end is even needed, so that a person can simply install and run Windows programs in exactly the same way as they do it on Windows. :)

But the legal BS we will get from microsoft is why Wine is the way it is.
I never had an issue with wine personally, most applications I installed in it worked like a charm.

---

### Post by insane_alien on 2009-07-23
> **Sealbhach said:**
> I use PlayonLinux and I like it but I think you're right, it would be better if Wine were seamless and you could just click on an .exe and you're done.

.

this can actually be done, you just have to set .exe's to open with wine. not that difficult tbh. just right click on a .exe then go to properties and then the 'open with' tab.

---

### Post by Mornedhel on 2009-07-23
It isn't very far from seamless, though. Assuming your application works without tweaks, you only need to run the installer once through wine on the command line, and you get the menu entries in your Applications menu.

I think it's fine as it is now.

---

### Post by SunnyRabbiera on 2009-07-23
> **Mornedhel said:**
> It isn't very far from seamless, though. Assuming your application works without tweaks, you only need to run the installer once through wine on the command line, and you get the menu entries in your Applications menu.

I think it's fine as it is now.

Never needed the commandline here, works fine without it

---

### Post by Starlight on 2009-07-23
For me it's almost seamless. :) I download an installation file of some program, open Nautilus, and go to the directory where I downloaded it. Then, I double click on it, and Wine is automatically used to run the installer. After I finish the installation, the icon for the installed program appears in Applications->Wine. However, when I try to run the program using the icon, it doesn't work, because it's trying to run it from my home directory instead of the directory where the program is installed. For that, I need to open Nautilus, then open the program's directory, and double click on the .exe file.

---

### Post by Sand &amp; Mercury on 2009-07-23
Agreed fully with those who said that it's best without the need for a frontend. Integration is what they should go for and it does seem to be the way they're headed anyway. So no complaints from me, they're doing a spiffing job.

---

### Post by Mornedhel on 2009-07-23
> **SunnyRabbiera said:**
> Never needed the commandline here, works fine without it

For some reason on my system application/x-msdos-executable files are opened with the Archive Manager. If I took the trouble of associating them to Wine (three clicks since it's a choice available in Open With) it would probably work as you said.

Anyway, I'd rather the Wine developers focused on 100% compatibility rather than some frontend, which can be taken care of by another project.

---

### Post by Starlight on 2009-07-23
I've also had another idea. It often happens that a program won't work on Wine perfectly unless you make some tweaks in the settings specifically for that program. So it would be cool if there was a database on the internet with instructions what to do to make a program run well, kind of like AppDB, except that this database wouldn't be read by people, but by Wine itself. Whenever you install a program in Wine, it will check the database and present a dialog box like this:


This program can work better if these tweaks are applied to it:

(list of stuff)

Do you want to have these tweaks automatically applied every time you run this program?

[ Yes ] [ No ]

---

### Post by Sealbhach on 2009-07-23
> **Starlight said:**
> I've also had another idea. It often happens that a program won't work on Wine perfectly unless you make some tweaks in the settings specifically for that program. So it would be cool if there was a database on the internet with instructions what to do to make a program run well, kind of like AppDB, except that this database wouldn't be read by people, but by Wine itself. 


I think that's kind of how PlayonLinux and Cedega and Winedoors work, they use install scripts to do all the tweaking for you. But making the process invisible would be good.

.

---

### Post by khelben1979 on 2009-07-23
Wasting time with a powerful GUI feels less important than working on the Wine code.

---

### Post by SunnyRabbiera on 2009-07-23
> **Mornedhel said:**
> For some reason on my system application/x-msdos-executable files are opened with the Archive Manager. If I took the trouble of associating them to Wine (three clicks since it's a choice available in Open With) it would probably work as you said.

Anyway, I'd rather the Wine developers focused on 100% compatibility rather than some frontend, which can be taken care of by another project.

Yeh but wine cannot really become a 100% microsoft clone, so making it 100% windows compatible is out of the question.
I personally will settle for 60 to 80%, right now Wine seems to be around the 60% compatible range.

---

### Post by keiichidono on 2009-07-23
> **Starlight said:**
> I've also had another idea. It often happens that a program won't work on Wine perfectly unless you make some tweaks in the settings specifically for that program. So it would be cool if there was a database on the internet with instructions what to do to make a program run well, kind of like AppDB, except that this database wouldn't be read by people, but by Wine itself. Whenever you install a program in Wine, it will check the database and present a dialog box like this:


This program can work better if these tweaks are applied to it:

(list of stuff)

Do you want to have these tweaks automatically applied every time you run this program?

[ Yes ] [ No ]

That's a great idea! If you feel you can expound on these thoughts then I'll want to get you to become and editor for my blog. :D

---

### Post by MikeTheC on 2009-07-23
I like the notion of Wine being more of a "back-end" type project, considering that technologically, being a back end kind of its role, anyhow.

Linux needs to find legitimacy in the hearts and minds of the general public. That is the only way it will best Microsoft.

---

### Post by Starlight on 2009-07-23
> **CalvinB said:**
> That's a great idea! If you feel you can expound on these thoughts then I'll want to get you to become and editor for my blog. :D

I'm glad you like my idea :D But I'm not sure if there's anything more to say about it, since the idea is rather simple... and I'm not even sure how easy it would be for the Wine guys to actually do this. But you can write about this idea in your blog, maybe someone from the Wine team will see it :D

---

### Post by keiichidono on 2009-07-23
> **Starlight said:**
> I'm glad you like my idea :D But I'm not sure if there's anything more to say about it, since the idea is rather simple... and I'm not even sure how easy it would be for the Wine guys to actually do this. But you can write about this idea in your blog, maybe someone from the Wine team will see it :D

I might be able to code some of the idea, though it may be out of my scope. But even if that's all you've got it'd be cool if you could post it as a contributor on my blog. :D

---

### Post by keiichidono on 2009-07-24
I think the question has changed from where is Wine going, to how can we get Wine to improve? Who here knows how we can contact the developers with this idea? If no one does anything besides bemoan about how much this would be great nothing will get done!

---

### Post by oedipuss on 2009-07-24
I think wine isn't meant to be seamless. Even the default debug information is often too valuable to ignore, if only to inform you that a dll is missing or simply that the program has terminated, or even to google an error. Right clicking and selecting "Open with wine" will often appear do nothing and the user won't be certain if the program has failed or if it's just starting up slowly. 

I think a user would be better off learning some basic console wine usage, such as WINEPREFIX for having multiple "bottles" as in crossover, and create launchers or use a GUI after he/she 's sure the program he's trying to run works properly. It's easier than it seems. 


Of course that's just an opinion, I'm by no means an expert on the matter :P

---

