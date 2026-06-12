---
title: "Why I switched from Lubuntu to Xubuntu after 7 years"
date: 2020-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-11-03
Since 2013, I've used Lubuntu, from 12.04 to 18.04, but 20.04 was just bad, I got a headache using 20.04. The design of LXQt was just bad.

The panel was bad. The |1|2|3|4| style workspace switcher was bad, and the fact that you cannot left click and drag apps through workspaces with your mouse like you could do in 18.04 was what made me dislike it, you have to right click the application and click to move it through to another workspace, terrible.

Lack of complete dark mode. The dark themes available on 20.04 didn't make the distro fully dark as it once did in 18.04. My favorite dark theme, [Windows 10 Dark]("https://github.com/B00merang-Project/Windows-10-Dark/"), doesn't work on 20.04, it didn't make the desktop environment fully dark, it was a mix of dark and light, which made my eyes squint.

I used Lubuntu 20.04 the whole day to get used to the distro, but eventually I made the decision to switch to Xubuntu 20.04 the next day, and I can say, I have less headaches with Xfce than LXQt, the workspace switcher acted like it was in LXDE, my favorite dark theme works on Xfce.

My conclusion is that LXDE is superior than LXQt and Xfce, but Xfce is better than LXQt.

---

### Post by mastablasta on 2020-11-03
LxQT is still under heavy development. when it is done it should be a lot better. it's a mix of KDE and LXDE. and dark theme on Kubuntu works rather well.

for example this LXQT seem to work ok: [https://github.com/gabretana/lxqt-arc-dark-theme](https://github.com/gabretana/lxqt-arc-dark-theme)

---

### Post by ardouronerous on 2020-11-03
> **mastablasta said:**
> LxQT is still under heavy development. when it is done it should be a lot better. it's a mix of KDE and LXDE. and dark theme on Kubuntu works rather well.

for example this LXQT seem to work ok: [https://github.com/gabretana/lxqt-arc-dark-theme](https://github.com/gabretana/lxqt-arc-dark-theme)

Well, based off my experience a few days ago on LXQt, I found it to be quite more difficult to customize, one thing that I liked about LXDE and now XFCE is that customizing the entire system's look is a lot easier than LXQt.

Also, if LXQt is still under heavy development, why did they use it on a LTS release? LTS, in my opinion, is about stability and LXQt in it's current form isn't ready for an LTS release.

Maybe in the next LTS release, I'll return to Lubuntu, to see if LXQt has improved.

---

### Post by bill-chatfield on 2020-11-03
Someone needs to fork the old LXDE-based Lubuntu and continue developing it so we can still have the more efficient, better looking and easier to use desktop that we had before LXQt. The whole decision to switch to LXQt was a developer preference. It has nothing to do with what the users wanted. The Raspberry PI interface also uses LXDE. It is not dead.

---

### Post by ardouronerous on 2020-11-03
> **bill-chatfield said:**
> Someone needs to fork the old LXDE-based Lubuntu and continue developing it so we can still have the more efficient, better looking and easier to use desktop that we had before LXQt. The whole decision to switch to LXQt was a developer preference. It has nothing to do with what the users wanted. The Raspberry PI interface also uses LXDE. It is not dead.

Based off what I've read, correct me if I'm wrong, but LXDE is now unsupported and not being developed, which is sad. I remember someone suggesting that you could install LXDE in Lubuntu 20.04 over LXQt, but one of the developers said that installing LXDE over LXQt in 20.04 would be dangerous since it's unsupported.

So, if LXDE is unsupported by it's development team, what does that mean for the other distros using it, like Raspbian, LXLE or Peppermint OS? It looks like they might have to switch to XFCE or as you said, create their own fork of LXDE.

This reminds me of the situation Microsoft was having over Windows 8's Metro style UI, everyone switched back to Windows 7.

---

### Post by guiverc on 2020-11-03
> **ardouronerous said:**
> 
Also, if LXQt is still under heavy development, why did they use it on a LTS release? LTS, in my opinion, is about stability and LXQt in it's current form isn't ready for an LTS release.

Maybe in the next LTS release, I'll return to Lubuntu, to see if LXQt has improved.

LXDE relies on GTK2 which is almost dead upstream (ie. most of it is unpatched and unmaintained; only the functions used by GIMP are still maintained).  XFCE, LXDE & GIMP were some of the last large projects still using it, XFCE hasn't used any GTK2 since Xubuntu 19.04, and GIMP has almost completed it's port to GTK3, GTK2 will be completely unmaintained when that's completed.

Lubuntu announced the move to LXQt years ago (eg. [https://lubuntu.me/lubuntu-1504-vivid-vervet-is-here/](https://lubuntu.me/lubuntu-1504-vivid-vervet-is-here/)) on 23-April-2015 mentions
> 
"General bug fix release as we prepare for LXQt"

Pcman (creator of `pcmanfm` that doubles as file-manager and handles the desktop) blogged about the porting of `pcmanfm` from GTK2 to GTK3 long ago and the performance hit, then subsequent re-port to Qt5 (`pcmanfm-qt`) which was much lighter fitting with the "Light" intention of then LXDE.

The LXDE team then joined with the RazorQt team creating a new project we know now as LXQt.

Lubuntu 20.04 LTS was the 4th release of Lubuntu with LXQt, not the first.

Active development mainly signifies an active project, GNOME, KDE, MATE & XFCE .. are both in active development.  That hasn't been the case for LXDE for a long time (though some translation & other cosmetic work is still performed, primarily thanks to Pixel). If you compare the LXDE contributors with LXQt ones, you'll find many of the same people, but you'll also quickly see where they spend most of their resources.

Qt4 was dropped from libraries in 2019, when will GTK2 be dropped (along with any packages that rely on it)...

(FYI:  The raspberry pi foundation have said they'll keep PIXEL running even if main GNU/Linux projects drop GTK2 for their Raspberry Pi OS as GTK2 runs well on 1GB pi devices (armv7) used in education environments.  Some people in the Arch world have indiciated they'll port it to GTK3, but that may not complete until after GTK2 has been dropped by much  of the GNU/Linux world - but we'll have to wait & see what happens).


If you mainly used GTK3 apps, it actually makes sense to me to move from LXDE to XFCE, as those GTK3 apps can use some of the same libraries as your desktop does. That to me is the largest hurdle with the LXDE to LXQt change, and for Lubuntu it couldn't be helped.

My favorite picture viewer is still `gpicview`, and I'll probably continue to use it until GTK2 is dropped from my systems and I have no choice but change.. Likewise I use a number of GTK3 programs from my GNOME2 days.  This box has enough ram so I can afford GTK3 & Qt5 libraries in memory, but not all boxes may have that.

> **ardouronerous said:**
> 
I found it to be quite more difficult to customize, one thing that I  liked about LXDE and now XFCE is that customizing the entire system's  look is a lot easier than LXQt.


I modelled my LXQt desktop to be a clone of an earlier XFCE desktop I love. Yes adding quick launchers was a little tricky ([https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html)).  Mostly it's just different, as it wasn't all based on prior LXDE but with some ideas from the RazorQt desktop were used.

You switched, so be it.  Myself my system has both `xubuntu-desktop` & `lubuntu-desktop` installed, so I can select which I want to use when I login.

We have great choice with our chosen operating system, to me the switch from LXDE/LXQt to XFCE doesn't matter much. Both are Ubuntu flavors (*hey I have both installed on this box, and they're not alone either*)

---

### Post by ardouronerous on 2020-11-04
> **guiverc said:**
> 13997672[/URL]]LXDE relies on GTK2 which is almost dead upstream (ie. most of it is unpatched and unmaintained; only the functions used by GIMP are still maintained). XFCE, LXDE & GIMP were some of the last large projects still using it, XFCE hasn't used any GTK2 since Xubuntu 19.04, and GIMP has almost completed it's port to GTK3, GTK2 will be completely unmaintained when that's completed.


Lubuntu announced the move to LXQt years ago (eg. [https://lubuntu.me/lubuntu-1504-vivid-vervet-is-here/](https://lubuntu.me/lubuntu-1504-vivid-vervet-is-here/)) on 23-April-2015 mentions




Pcman (creator of `pcmanfm` that doubles as file-manager and handles the desktop) blogged about the porting of `pcmanfm` from GTK2 to GTK3 long ago and the performance hit, then subsequent re-port to Qt5 (`pcmanfm-qt`) which was much lighter fitting with the "Light" intention of then LXDE.


The LXDE team then joined with the RazorQt team creating a new project we know now as LXQt.


Lubuntu 20.04 LTS was the 4th release of Lubuntu with LXQt, not the first.


Active development mainly signifies an active project, GNOME, KDE, MATE & XFCE .. are both in active development. That hasn't been the case for LXDE for a long time (though some translation & other cosmetic work is still performed, primarily thanks to Pixel). If you compare the LXDE contributors with LXQt ones, you'll find many of the same people, but you'll also quickly see where they spend most of their resources.


Qt4 was dropped from libraries in 2019, when will GTK2 be dropped (along with any packages that rely on it)...


(FYI: The raspberry pi foundation have said they'll keep PIXEL running even if main GNU/Linux projects drop GTK2 for their Raspberry Pi OS as GTK2 runs well on 1GB pi devices (armv7) used in education environments. Some people in the Arch world have indiciated they'll port it to GTK3, but that may not complete until after GTK2 has been dropped by much  of the GNU/Linux world - but we'll have to wait & see what happens).




If you mainly used GTK3 apps, it actually makes sense to me to move from LXDE to XFCE, as those GTK3 apps can use some of the same libraries as your desktop does. That to me is the largest hurdle with the LXDE to LXQt change, and for Lubuntu it couldn't be helped.


My favorite picture viewer is still `gpicview`, and I'll probably continue to use it until GTK2 is dropped from my systems and I have no choice but change.. Likewise I use a number of GTK3 programs from my GNOME2 days. This box has enough ram so I can afford GTK3 & Qt5 libraries in memory, but not all boxes may have that.






I modelled my LXQt desktop to be a clone of an earlier XFCE desktop I love. Yes adding quick launchers was a little tricky ([https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html)). Mostly it's just different, as it wasn't all based on prior LXDE but with some ideas from the RazorQt desktop were used.


You switched, so be it. Myself my system has both `xubuntu-desktop` & `lubuntu-desktop` installed, so I can select which I want to use when I login.


We have great choice with our chosen operating system, to me the switch from LXDE/LXQt to XFCE doesn't matter much. Both are Ubuntu flavors (hey I have both installed on this box, and they're not alone either)


Seeing that you're a developer on Lubuntu, I hope my opinion on LXQt didn't insult you. I just needed to vent out.


On the day I decided to install Lubuntu 20.04, when I booted and logged into my system, which by the way, I love the login screen, I noticed a lot of the functionalities that made me love LXDE was changed in LXQt, like the Workspace switcher and the not so nice LXQt themes.


I knew the Lubuntu has changed from LXDE to LXQt, but what I didn't expect was the totally functionality difference between the two. I like continuity, that's why when Windows 8 was released, it was met with dislike from it's users due to it's changes. For now, XFCE is similar to LXDE and that's why I prefer it over LXQt.


Once again, I hope I didn't insult you, being that you're a developer in Lubuntu.

---

### Post by guiverc on 2020-11-04
> **ardouronerous said:**
> Seeing that you're a developer on Lubuntu, I hope my opinion on LXQt didn't insult you. ..

..  I noticed a lot of the functionalities that made me love LXDE was changed in LXQt, like the Workspace switcher and the not so nice LXQt themes.


No you didn't offend me, I read your post as your opinions and facts/reasoning. That's how I tried to reply, with facts & my opinions.  I'm also not a *developer*,  yes I am a Lubuntu team member, but I still didn't see anything I could be offended about.

I don't worry much about themes, I'd personally love it if Lubuntu included more themes by default, but including them means we have to support them for the life of the release, most other themes come from different sources (*more places to watch for changes*), all of which involves more work for the small team. It's not difficult to add themes so I don't think it matters that we don't include them.

I recall hearing Richard Brown, a prior OpenSUSE lead, reporting that many open-source projects are *do-ocracies*, ie. those who do the work decide. This also means as Lubuntu is downstream of the LXQt desktop, those upstream *devs* who work on that desktop, will make decisions that will impact us, and thus our users. To me that's just fact. We do the best with what time/resources we have.

---

### Post by DuckHook on 2020-11-04
> **ardouronerous said:**
> Seeing that you're a developer on Lubuntu, I hope my opinion on LXQt didn't insult you. I just needed to vent out.
guiverc is a thoroughly decent sort, so I suspect that no offence was taken.

I too found that the transition from LXDE to LXQt had some rough edges, but then, I also ran into difficulties with the vanilla Ubuntu upgrade from Bionic to Focal. It was, oddly, the first time in a long while that a network upgrade did not go smoothly for me. However, it sort of brought home the fact that problematic upgrades/new&#8209;looks&#8209;&&#8209;feels are not restricted to Lubuntu alone. LTS to LTS upgrades often bring hiccups. It's just that Ubuntu's devs have done such a good job recently that smooth upgrades have become the new normal and we've forgotten how much rockier things used to be.

---

### Post by mastablasta on 2020-11-05
> **guiverc said:**
> 
My favorite picture viewer is still `gpicview`, and I'll probably continue to use it until GTK2 is dropped from my systems and I have no choice but change.. 


nomacs - easy to use, fast, light. became default on my Kubuntu install. the KDE one is too heavy.

[QUOTE=ardouronerous]
[COLOR=#000000]Also, if LXQt is still under heavy development, why did they use it on a LTS release? LTS, in my opinion, is about stability and LXQt in it's current form isn't ready for an LTS release.[/COLOR][/QUOTE]

stable means the app versions are kept at the same version. bug fixes & patches might be ported back to that version, while development continues in new version of the app.

stable does not mean that for example you will get less crashes on your hardware with LTS. LTS also extends the support for these libraries.

anyway LXQt is at version 0.16.something i believe, which indicates that it is not done yet. KDE is at 5.20.smth, Gnome is also at version 3.smth ... More mature desktops might give a better experience. just maybe not on older machines.


anyway i hope they succeed with LXQt. many of the Qt based apps are actually really good.

---

### Post by ardouronerous on 2020-11-05
> **guiverc said:**
> No you didn't offend me, I read your post as your opinions and facts/reasoning. That's how I tried to reply, with facts & my opinions.  I'm also not a *developer*,  yes I am a Lubuntu team member, but I still didn't see anything I could be offended about.

I don't worry much about themes, I'd personally love it if Lubuntu included more themes by default, but including them means we have to support them for the life of the release, most other themes come from different sources (*more places to watch for changes*), all of which involves more work for the small team. It's not difficult to add themes so I don't think it matters that we don't include them.

I recall hearing Richard Brown, a prior OpenSUSE lead, reporting that many open-source projects are *do-ocracies*, ie. those who do the work decide. This also means as Lubuntu is downstream of the LXQt desktop, those upstream *devs* who work on that desktop, will make decisions that will impact us, and thus our users. To me that's just fact. We do the best with what time/resources we have.

Thank you.

> **DuckHook said:**
> guiverc is a thoroughly decent sort, so I suspect that no offence was taken.

I too found that the transition from LXDE to LXQt had some rough edges,  but then, I also ran into difficulties with the vanilla Ubuntu upgrade  from Bionic to Focal. It was, oddly, the first time in a long while that  a network upgrade did not go smoothly for me. However, it sort of  brought home the fact that problematic upgrades/new&#8209;looks&#8209;&&#8209;feels  are not restricted to Lubuntu alone. LTS to LTS upgrades often bring  hiccups. It's just that Ubuntu's devs have done such a good job recently  that smooth upgrades have become the new normal and we've forgotten how  much rockier things used to be.

Yes, I understand that, for example, my printer is always the one that has hiccups every time I upgrade to a new LTS release, and sometimes my scanner doesn't work.

> **mastablasta said:**
> nomacs - easy to use, fast, light. became default on my Kubuntu install. the KDE one is too heavy.



stable means the app versions are kept at the same version. bug fixes  & patches might be ported back to that version, while development  continues in new version of the app.

stable does not mean that for example you will get less crashes on your  hardware with LTS. LTS also extends the support for these libraries.

anyway LXQt is at version 0.16.something i believe, which indicates that  it is not done yet. KDE is at 5.20.smth, Gnome is also at version  3.smth ... More mature desktops might give a better experience. just  maybe not on older machines.


anyway i hope they succeed with LXQt. many of the Qt based apps are actually really good.

I also want to see LXQt succeed, that is why, in the next LTS release, I'll give Lubuntu another shot.

Another reason for my switching is because I'm maintaining the computers of my father and my sister, so I think LXQt wouldn't be their cup of tea, so I'm also looking for a distro that they might like, and I think they'll like Xubuntu.

---

### Post by mastablasta on 2020-11-05
XFCE as desktop is very easy to manage. i had no troubles or obstacles setting it up as i liked.

---

