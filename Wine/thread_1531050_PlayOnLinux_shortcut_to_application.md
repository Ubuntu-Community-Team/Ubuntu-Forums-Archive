---
title: "PlayOnLinux shortcut to application"
date: 2010-07-14
forum: Wine
---

### Post by Arkish0 on 2010-07-14
i guess i should put this in wine section

anyways .. i installed some windows program using PlayOnLinux. the problem is that now every time that i want to load them i have to open play on linux and then click the program that i want..

is there any way that i can create a launcher for example for Microsoft Word? what would be the command?

besides.. can i create a template for this files.. 

i right click a Doc.xdoc file and it only says open with open office .. how can i get word to be there

i had office before without using PlayOnLinux and all this stuff that i tell you worked ... i decided to use PlayOnLinux to make easier to handle Wine versions but now i don't know how to do this!

thanks in advance =)

---

### Post by Joe-Zeif on 2010-11-24
> **Arkish0 said:**
> i guess i should put this in wine section

anyways .. i installed some windows program using PlayOnLinux. the problem is that now every time that i want to load them i have to open play on linux and then click the program that i want..

is there any way that i can create a launcher for example for Microsoft Word? what would be the command?

besides.. can i create a template for this files.. 

i right click a Doc.xdoc file and it only says open with open office .. how can i get word to be there

i had office before without using PlayOnLinux and all this stuff that i tell you worked ... i decided to use PlayOnLinux to make easier to handle Wine versions but now i don't know how to do this!

thanks in advance =)
Hi,
I have been struggling with the same problems myself and I have just figured them out.

1) For the shortcuts, I haven't figured out how to create shortcuts for an already installed application. However, after you finish installing Office 2007, the installer itself prompts you for shortcuts. I guess (if this is an option), you can reinstall Office 2007 and accept the creation of shortcuts. To make these shortcuts actually work, go to the Plugins menu of PlayOnLinux and run the Wine Import plugin. 

2)The "Open With" part is easier. 
To associate .doc files with MS Word:
- Go to any .doc file and right-click its icon. Choose "Properties", go to the "Open With" tab.
- In the applications menu, click "Add"
- Select "Use Custom Command" and type:
playonlinux --run Microsoft\ Office\ Word\ 2007

Note the backslashes before the spaces.
-After you've added this custom command, a new radio button should appear in the application list. It should be called simply "playonlinux". 
-Select that and you're good to go

The same procedure works for any other type of Office document. You just change the application from Word to whichever one is appropriate.

Hope this helps...

---

### Post by vatsok on 2010-12-13
I think this is what you are looking for.

[http://playonlinux.wikia.com/wiki/Starters_Tutorial](http://playonlinux.wikia.com/wiki/Starters_Tutorial)

---

