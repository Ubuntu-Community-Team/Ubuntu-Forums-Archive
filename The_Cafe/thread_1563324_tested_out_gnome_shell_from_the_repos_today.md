---
title: "tested out gnome shell from the repos today"
date: 2010-08-28
forum: The Cafe
---

### Post by Dustin2128 on 2010-08-28
I was sick of people whining about GNOME 3 and its accompanying shell  being delayed yet again, forgetting it was an open source project where  you can download all the latest builds, and was wondering how its  progressed since about this time last year; the first time I tried it.  The sidebar thing is quite nice; very kde-like and well designed. The  shell screen is quite an excellent pager as well; so much easier to  change the amount of desktops you have and keep track of open windows,  not to mention the recent documents group. All in all, its quite  excellent. Now there are still a few problems:
1. the applications thing was nice, but they really should be grouped, this isn't windows.
2. disabled desktop effects like wobbly windows. (I'm an eye-candy addict)
3. yakuake and tilda both used the minimize animation instead of sliding up/down.
4. no window list on the top bar- made it difficult to swap between windows on the same desktop.
5. stability, crashed a half hour after I started it up.
6. mutilated window decoration.
but other than that, its a pretty solid beta release; quite a bit more polished than last time.

---

### Post by Legendary_Bibo on 2010-08-28
I really do like it (I'm using Zeitgeist/Activity Journal in place of it for now), but like you said it disables Compiz which for me is bad.

Does it only pop up when you click on something or press a KB shortcut?

---

### Post by Jesus_Valdez on 2010-08-29
Gnome-Shell is awesome.

---

### Post by Dustin2128 on 2010-08-29
> **Legendary_Bibo said:**
> 
Does it only pop up when you click on something or press a KB shortcut?
yeah, you hit the activities thing in the top left corner. I'm guessing you can assign a key though. I like it besides the special fx disabling and am going to make it the default on my 2 old 512M machines.

---

### Post by MasterNetra on 2010-08-29
> **Dustin2128 said:**
> I was sick of people whining about GNOME 3 and its accompanying shell  being delayed yet again, forgetting it was an open source project where  you can download all the latest builds, and was wondering how its  progressed since about this time last year; the first time I tried it.  The sidebar thing is quite nice; very kde-like and well designed. The  shell screen is quite an excellent pager as well; so much easier to  change the amount of desktops you have and keep track of open windows,  not to mention the recent documents group. All in all, its quite  excellent. Now there are still a few problems:
1. the applications thing was nice, but they really should be grouped, this isn't windows.
2. disabled desktop effects like wobbly windows. (I'm an eye-candy addict)
3. yakuake and tilda both used the minimize animation instead of sliding up/down.
4. no window list on the top bar- made it difficult to swap between windows on the same desktop.
5. stability, crashed a half hour after I started it up.
6. mutilated window decoration.
but other than that, its a pretty solid beta release; quite a bit more polished than last time.

I'd rather have it delayed and released when ready, then released not ready and/or stable. but thats just my preference.
And I do like that fact that at least gnome is trying not to clone the Windows GUI and doing its own thing.

---

### Post by Legendary_Bibo on 2010-08-29
> **MasterNetra said:**
> I'd rather have it delayed and released when ready, then released not ready and/or stable. but thats just my preference.
And I do like that fact that at least gnome is trying not to clone the Windows GUI and doing its own thing.

Yeah and it's actually a good idea. I'll use it when it's ready. Are they including the global menu? I hope when they do they include it only when it's fully functioning. Although I'm curious as to how they're going to deal with the task switcher thing, I know there a panel applet that just brings up a list of your applications open that you can use.

---

### Post by wildman4god on 2010-08-29
I believe it disables compiz because it uses clutter, which is like plasma for kde, I.E. it is an opengl accelerated toolkit that sits on top of gtk and provides it's own compositing making compiz unnecessary.

---

### Post by Legendary_Bibo on 2010-08-29
> **wildman4god said:**
> I believe it disables compiz because it uses clutter, which is like plasma for kde, I.E. it is an opengl accelerated toolkit that sits on top of gtk and provides it's own compositing making compiz unnecessary.

Then it better have wobbly windows as well as everything from compiz.

---

### Post by Mr. Picklesworth on 2010-08-29
> **Dustin2128 said:**
> I was sick of people whining about GNOME 3 and its accompanying shell  being delayed yet again, forgetting it was an open source project where  you can download all the latest builds, and was wondering how its  progressed since about this time last year; the first time I tried it.  The sidebar thing is quite nice; very kde-like and well designed. The  shell screen is quite an excellent pager as well; so much easier to  change the amount of desktops you have and keep track of open windows,  not to mention the recent documents group. All in all, its quite  excellent. Now there are still a few problems:
1. the applications thing was nice, but they really should be grouped, this isn't windows.
2. disabled desktop effects like wobbly windows. (I'm an eye-candy addict)
3. yakuake and tilda both used the minimize animation instead of sliding up/down.
4. no window list on the top bar- made it difficult to swap between windows on the same desktop.
5. stability, crashed a half hour after I started it up.
6. mutilated window decoration.
but other than that, its a pretty solid beta release; quite a bit more polished than last time.

Judging by the screenshot, what you're looking at there is *horrifically* out of date.
Try [http://live.gnome.org/GnomeShell#Building](http://live.gnome.org/GnomeShell#Building)
It takes a while, but it's quite easy :)

On your problem #2, there's really nothing &#8220;disabled&#8221; per-se. Gnome Shell is a *window manager* / desktop shell; a change from the previous design where the window manager and the rest of the shell were all detached, theoretically modular components. So, *now*, if you get Compiz to replace Gnome Shell you will lose the launcher, panel, etc along with it because those were also part of Gnome Shell. (And at this point in time, Compiz doesn't provide any of those itself).
While it does sound restrictive, this more interconnected design is *not* unusual. See: most other operating systems (including mobile devices) and a lot of window managers right here that run as X sessions. (You can't &#8220;run Compiz on Fluxbox&#8221;).

Unfortunately, #1 still isn't fixed and there appears to be zero interest in doing so. They have changed it, though, and search works slightly better.

---

### Post by Zorgoth on 2010-08-29
> **Legendary_Bibo said:**
> Then it better have wobbly windows as well as everything from compiz.

It won't...  GNOME devs are convinced that people don't care about those features, or in fact compiz at all.  I personally am just not going to use GNOME shell's WM or panel.  Maybe eventually I'll switch to a DE that doesn't try to lock me into one WM, but GNOME has a lot of great features that I'd miss.

---

### Post by cariboo on 2010-08-29
The compiz dev has posted here in the forums that he will be creating add-ons for clutter instead of continually updating compiz, so maybe by the time Gnome 3/gnome-shell is released in the spring of 2011, there may be effects available.

---

### Post by Khakilang on 2010-08-29
I am not an eye candy fan. But I would like to see how far it can go in term of user friendly and productivity. It can be pretty awesome. May have a go at it one of this days.

---

### Post by Dustin2128 on 2010-08-29
hm... even with search, not grouping items in the menu is, in my opinion, just stupid. Maybe I should contribute some code to fix that. Also: I'm about to download and build the latest, I didn't know the version in the repositories was so dated. Updating my review accordingly.

---

### Post by Dragonbite on 2010-08-29
> **MasterNetra said:**
> I'd rather have it delayed and released when ready, then released not ready and/or stable. but thats just my preference.
And I do like that fact that at least gnome is trying not to clone the Windows GUI and doing its own thing.

Aww.. what's the fun in THAT?!  You don't want to have anything for people to complain about? You mean you want them to WORK at finding things to complain about? 
:popcorn:

I like Gnome-shell, but have not been able to get it on my Ubuntu installation (Fedora and openSUSE only, and they were slightly unstable).

---

### Post by Naiki Muliaina on 2010-08-29
Does it change Gnome much? Although I only use LTS release of Ubuntu so wont have to worry about this for a long time, I work with a large number of 40+ computer illiterate people that wont learn new 'stuff'. Half the reason I moved them onto Ubuntu in the first place was because they don't think before clicking. The old windows 98 PC's were utterly knackered in a very short time. Same as the win 2000 machines. 

I am not keen on teaching these non learners a new desktop environment when the time comes. :)

---

### Post by Merk42 on 2010-08-29
As Mr. Picklesworth said, that's a VERY old version of GNOME Shell.
Check out my pictures in the [GNOME Shell thread](http://ubuntuforums.org/showthread.php?t=1476241) for more recent samples.

---

### Post by SmSpillaz on 2010-09-01
Few small bits:

1) It's my view that integrating the window manager and the panel isn't a necessary move to make if you want to use some window manager features within the panel or if you want the panel to be part of a composited scene. The former is made possible by the ICCCM and later EWMH which specifies how panels and window managers should communicate. The latter is made possible by RGBA-GLX windows (see plasma-desktop for a good example of this).

2) It's likely that I won't be writing a clutter backend for compiz - simply because I do not have the time and I feel that there are far better things for me to do in order to advance compiz rather than writing yet another rendering backend for it.

3) If you want a modern desktop environment, I suggest you try KDE 4.5 - I have been using it for a while now and I really can't imagine going back to GNOME (unless I am doing some GNOME related development).

---

### Post by bash on 2010-09-01
> **Dustin2128 said:**
> hm... even with search, not grouping items in the menu is, in my opinion, just stupid. Maybe I should contribute some code to fix that. Also: I'm about to download and build the latest, I didn't know the version in the repositories was so dated. Updating my review accordingly.

Application grouping is a planned feature in the latest Shell design mockups presented at GUADEC.

You can find a short video showing of the new design here:

[http://www.vimeo.com/13797705](http://www.vimeo.com/13797705)

---

### Post by Zorgoth on 2010-09-01
> **SmSpillaz said:**
> Few small bits:
3) If you want a modern desktop environment, I suggest you try KDE 4.5 - I have been using it for a while now and I really can't imagine going back to GNOME (unless I am doing some GNOME related development).

Does this mean you have compiz 0.9 working properly in KDE?  I get all manner of crashes trying to do that, particularly with ccsm.  I couldn't get it to even talk to GNOME (basically I can't turn on any settings whatsoever so I get an uncomposited desktop with no window management features).

---

### Post by BrokenKingpin on 2010-09-01
I have tried it and I just do not like it. It's trying to do something similar to the Ubuntu netbook remix interface, or the MeeGo interface, and I just don't want that for my desktop (or notebook/netbook for that matter).

I hope they will continue to support the old panel system when Gnome 3 is released.

---

### Post by CraigPaleo on 2010-09-02
> **BrokenKingpin said:**
> I have tried it and I just do not like it. It's trying to do something similar to the Ubuntu netbook remix interface, or the MeeGo interface, and I just don't want that for my desktop (or notebook/netbook for that matter).

I hope they will continue to support the old panel system when Gnome 3 is released.

In the thread Merk42 provided, you'll find > **TRUTH: The GNOME 2.x panel and Metacity (the window manager) will still be available.**
Downstream distributions such as Fedora, openSUSE and Ubuntu will have the option to include them in their distribution. You will be able to install them just as now you can install sawfish, compiz, etc inside your GNOME session. (There are no plans to support GNOME panel applets in GNOME Shell, TBA. This mailing list post has some information.)  

Which originally came from: [http://live.gnome.org/GNOME3Myths](http://live.gnome.org/GNOME3Myths)

---

### Post by murderslastcrow on 2010-09-02
Yeah, I'm looking forward to seeing if they integrate any new features into the classic layout. Because really, that would mean you basically get an updated Gnome 2 with prettier and more functional stuff.

---

### Post by BrokenKingpin on 2010-09-10
> **CraigPaleo said:**
> In the thread Merk42 provided, you'll find  

Which originally came from: [http://live.gnome.org/GNOME3Myths](http://live.gnome.org/GNOME3Myths)
Yes, I read this, but it doesn't say they will continue to support and develop the panels and applets, they just stay they will still be an option. If they are not I have to say I will probably switch to XFCE.

---

