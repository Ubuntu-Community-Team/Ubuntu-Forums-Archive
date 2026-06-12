---
title: "disappointed by Ubuntu 18"
date: 2019-12-21
forum: Ubuntu, Linux and OS Chat
---

### Post by axd1967 on 2019-12-21
I have been using default Ubuntu 16 (with Unity) for over a year, was quite happy and decided to buy a XPS-13 laptop with 18 preinstalled.

For a few weeks now I have been using Ubuntu 18 (+Gnome), and am extremely  disappointed by the regressions I stumble across.

for example, 

- In Nautilus, when I toggle the sidebar (F9), this affects all Nautilus instances
- when I save files, I ALWAYS have to navigate to a folder where I save the previous file in the same application
- I can no longer create a shortcut (ctrl-M) in Nautilus
- in Evince, the menu items are not highlighted (F10).  this happens in all applications, it's a window manager issue I guess. Switching to another theme is no solution. and why do I have to separately install the Tweaks app???
- the Image Viewer does not react to spacebar, I have to use arrow right.
-  I enabled Pointer Location (ctrl) - this worked for a few minutes, then some other settings broke this forever.
- Snap is a disaster, good for the most basic use only. I am stopping to use Snap to install applications because almost all of them are outdated and partly broken.
- in Tweaks I was able to add 'xclock' as a login app (just for testing, mind you), and now can't do that any more (I can remove it only)??? some update changed this possibilty. but now I can add "logout" and "reboot" (among others) instead... 

(And what is Amazon doing in my applications?? Is Amazon financing Ubuntu? but that is a digression.)

I would expect 18 to be an improvement over 16, but it is NOT. And when I read that upgrading has risks (ok, I can understand that), I have started wondering what value Ubuntu can still offer to me.

Ubuntu (18), this is a shame. 

I don't think much can be done about this - what I am tempted to call - mess. It feels as if Ubuntu is in fact a message to start looking elsewhere.

I truely hope this is a temporary situation, but seeing that Ubuntu 18 exists for a while now, it looks like my problems will never be solved in 18.

-alex

---

### Post by axd1967 on 2019-12-21
- In Nautilus , icon mode, I cannot extend the selection via keyboard (SHIFT+cursor).
- when I delete a file in icon mode, the focus disappears and I have to select another file. I would have expected focus to shift to the next file instead. in list mode this still works fine.
- this extension mode DOES work when using the mouse.
- in icon mode, there is a strange behaviour when navigating the icons by using the keyboard. for example enable icon mode, enter a subdirectory, leave it (ALT up), then hit arrow right to select the next directory: nothing happens, the next arrow right selects the  the first item in the current directory instead. obviously a bug.

all this gives the impression that Ubuntu developers have forgotten the art of the keyboard, otherwise they would have corrected this long ago.

---

### Post by CatKiller on 2019-12-21
Unity was created because Canonical had hoped to have a unified environment for phones, tablets, netbooks, and the desktop. That all fell through and maintaining Unity just for the desktop was unsustainable, so they went back to Gnome; Gnome 2 had been Ubuntu's default environment before Unity.

Gnome 3 makes questionable choices, and the devs are allergic to users being able to configure things. Gnome 3 has been made considerably better as a result of Ubuntu putting in effort, but the products of that are in releases later than 18.04.

You can still use Unity in 18.04, but it's now maintained by the community rather than Canonical. Or one of the many other desktop environments.

---

### Post by Frogs Hair on 2019-12-21
It is possible to install Unity on 18.04 , but the changes in Gnome applications and features are changes made by Gnome Developers and they are on going. See the flavors link in my signature for other Desktop options.

---

### Post by cpt-ankitsharma on 2019-12-21
> **axd1967 said:**
> 

(And what is Amazon doing in my applications?? Is Amazon financing Ubuntu? but that is a digression.)


I don't understand why so many people make such big deal out of this. It takes one command to get rid of Amazon if you don't like it there. 

Little bit of funding goes a long way in open source world. Now, I am not saying that linux distros should be full of bloatware and adware. But just one app ? How bad that can be ?

---

### Post by TheFu on 2019-12-21
And just for clarity, nobody here works for Canonical.  Everyone here is a community volunteer.  Canonical developers seldom, if ever, come here.

In Linux distributions, the vast majority of programs used are created with defaults setup by the developers on another team, not Canonical. Gnome is one of those projects.  [https://www.gnome.org/](https://www.gnome.org/)   You can join the team: [https://www.gnome.org/get-involved/](https://www.gnome.org/get-involved/)

Canonical tried to make Gnome3 useable and for many people, it is and they LOVE it. That is an extremely personal thing.  We all have different tastes.  Seems they missed what you would have liked, what CatKiller and what I would like.  That's fine.  Can't please everyone.

Fortunately, the GUI isn't the OS with any Unix OS. It is just a layer that can be swapped as you like.  You can choose from 20+ different GUIs if you don't like the one that arrived.  There are many people who complained that Canonical didn't use the Gnome3 DE like all the other major distros do for years.  Now that the default DE for Ubuntu is Gnome3, other people are complaining.

If you want to complain, that's fine.

If you actually want suggestions to solve any specific issue, it is best to create a thread for each and clearly say - Ubuntu 18.04, Gnome3 DE, Fully patched as of DD-MM-YY date, then describe what you want from which specific program.  Many times, it is just a different way to accomplish what you desire, but not always.

If you choose a different DE trying to solve the most issues, let the thread know.  Every DE has different behavior, so trying a few is worth your time if you are picky.  To save a little time, perhaps youtube videos of the different Ubuntu flavors would let you quickly see how each behaves.  

I recall when MS-Win7 was new, the ZDNet team went to a mall in Australia and was showing off KDE, but told them it was Win7 [https://www.youtube.com/watch?v=CPIgEFIv5MI](https://www.youtube.com/watch?v=CPIgEFIv5MI)  Normal people don't know the difference and looking for 2 minutes isn't sufficient to really understand how an OS or even a DE will work for you.  It takes a little time.

---

### Post by CatKiller on 2019-12-21
> **TheFu said:**
> Canonical tried to make Gnome3 useable and for many people, it is and they LOVE it. That is an extremely personal thing.  We all have different tastes.  Seems they missed what you would have liked, what CatKiller and what I would like.  That's fine.  Can't please everyone.

For the record, Gnome could have whatever defaults they thought were best, and you'd hear barely a grumble from me. They want to make the volume control go in 6% increments? Fine. They want to make Minesweeper black-and-white while people are getting displays that can do 1,073,741,824 colours? OK.

What rubs me up the wrong way is that they remove basic options and configurability. They had a means to configure the increment on the volume control, but they took it out. They had a Minesweeper theme that had colours, but they took it out. You used to be able to have icons on the desktop, but they took it out. To recover all sorts of basic functionality you have to install random extensions that no one's going to discover, and that could be doing all kinds of sketchy things for all the user knows. That and client-side-decorations, that turn every application into a GeoCities page and destroy any prospect of having a unified themed desktop, are why I don't think Gnome should be used by anyone, but especially by people that are exploring Linux for the first time.

---

### Post by axd1967 on 2019-12-27
The issue here is that Ubuntu 18 is a major regression. I still can't understand why - for example - an application such as Nautilus now won't dsplay the date column when searching for files.

Kinetic scrolling is probably an example of where Ubuntu wants to head: notebooks.

And I wonder - what would happen if I disabled the "Touchpad" toggle? would I stlll be able to re-enabled it? Because I tried the keyboard, I see no way how to reach that control via the keyboard only. 

Sorry to be so grumpy, but every day I discover new bad issues in UBuntu 18. I wonder why I forled out 1500$ for a Dell XPS-13 with this OS installed...

(edit added: in Nautilus one cannot even drag&drop ICONS between two windows?)

---

### Post by CatKiller on 2019-12-27
> **axd1967 said:**
> I wonder why I forled out 1500$ for a Dell XPS-13 with this OS installed...

Your complaints haven't been about the OS, they've been about the desktop environment. Use a different one. There are many to choose from. KDE and Cinnamon have both been great on my XPS13.

---

### Post by vidtek on 2019-12-28
Axd-  I tend to agree with you about Gnome-I was never able to get on with it from Gnome 1.  I have used KDE ever since weaning myself off of Windows in the late 1990's and early 2000's.

KDE can be frustrating purely because of the bewildering array of configuration options.  KDE were the first with multiple desktops, then they changed it around and made multiple desktops in multiple activities.  Some zealots in KDE in their wisdom decided to cripple Dolphin by removing root options, it still is far and away the best file manager in Linux.  Reluctantly after 2 years they conceded defeat and re-enabled it.

All these developers give freely of their expertise and time, for which we should be eternally grateful.   Sometimes they make erroneous decisions, don't we all?  They are only human and we all make mistakes. 

I suggest you give Kubuntu a try, after a few weeks with the plasma desktop you will wonder how you ever managed without it.

Best regards, Tony.

---

### Post by bunny9000 on 2019-12-28
I don't know how good you (the OP) is good with computers, but it's pretty easy to backup your files, use an app like unetbootin and install something else. There are literally hundreds of versions of Linux. Ubuntu isn't the Windows of Linux, you don't have to use it. Ubuntu is packaged with alternatives such as kde, mate, xfce. Canonical will keep going the path they think is best. I expect monetization of the OS is a desire and a future goal especially if Windows ever goes OSS. I personally don't like the default DE, but to be popular you (canonical) has to please most people and has to have a hook to get new users interested in using their operating system and I think for gnome and unit it's been a case if you can't beat them, join them and imitate them.

Linux is a modular system. You can install dolphin or any other file manager and use it instead of nautilus. Better yet, if you don't want to re-install a different flavor of gnu/inux you can install kde or xfce, etc to your existing install and switch to any one of them when you login. So one day  you can be using kde with dolphin or the next day you could be using mate with caja.

---

### Post by axd1967 on 2019-12-29
So, to reiterate the issue: UBuntu 18.04 is a regression with respect to 16; I don't really care whether it's the DE or the OS, the result is disappointment. 

I know how to run backups with rsync, to give an example, and am an avid user of Bash (and am turning away from Snap, another failure in my eyes). But I have always been used to see improvement with every new version of an OS, not regression; this is the first time I encounter such an oddity. I realise the switch from Unity to Gnome must not have been taken lightly, nevertheless it is a regression. With all respect, I believe Gnome might have its followers, but Unity has given me a lot of pleasure I miss in Gnome.

I'll have a look at KUbuntu, thanks for the suggestion. I've long heard good things about KDE and was always fond of Qt, now is probably the moment to switch.

---

