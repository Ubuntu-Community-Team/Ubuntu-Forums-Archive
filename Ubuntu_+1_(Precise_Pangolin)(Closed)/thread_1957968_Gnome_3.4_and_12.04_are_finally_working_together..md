---
title: "Gnome 3.4 and 12.04 are finally working together."
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Mathor on 2012-04-13
Though i have tested Gnome 3.4 before with my old install of 12.04 beta2 (with lots of bugs), much of the 3.2 extensions would also not work, and the desktop was almost unusable for Ubuntu upon the release of Gnome 3.4. With a clean install of a daily image of Ubuntu 12.04 today and gnome-shell (3.4 is in repos now!) I must say I am VERY impressed with how Ubuntu and Gnome work together.  Anyone else tested out the new GS in Precise?

---

### Post by fillmont on 2012-04-13
> **Mathor said:**
> Though i have tested Gnome 3.4 before with my old install of 12.04 beta2 (with lots of bugs), much of the 3.2 extensions would also not work, and the desktop was almost unusable for Ubuntu upon the release of Gnome 3.4. With a clean install of a daily image of Ubuntu 12.04 today and gnome-shell (3.4 is in repos now!) I must say I am VERY impressed with how Ubuntu and Gnome work together.  Anyone else tested out the new GS in Precise?

Have been working with it the last few weeks. The change from even 2 weeks ago is pretty stunning. It is nearly rock solid for me now.

The only issue I have is playing full screen movies. It was actually originally a Xubuntu machine, and when I play video files in Xubuntu (with VLC or Gnome player) it plays fine.

But in Gnome Shell, using VLC and Gnome player, full screen playback is choppy. 

Other than that though, I've really enjoyed using Shell.

---

### Post by sgage on 2012-04-13
> **Mathor said:**
> Though i have tested Gnome 3.4 before with my old install of 12.04 beta2 (with lots of bugs), much of the 3.2 extensions would also not work, and the desktop was almost unusable for Ubuntu upon the release of Gnome 3.4. With a clean install of a daily image of Ubuntu 12.04 today and gnome-shell (3.4 is in repos now!) I must say I am VERY impressed with how Ubuntu and Gnome work together.  Anyone else tested out the new GS in Precise?

I've been using it pretty much exclusively all along. Coming along very nicely, except this bug still hasn't been addressed:

[http://ubuntuforums.org/showthread.php?t=1947969&highlight=desktop+glitch]("http://ubuntuforums.org/showthread.php?t=1947969&highlight=desktop+glitch")

Not sure if it's a GS bug or a Nautilus bug. In any case the Extensions website is catching up with 3.4.0, and things are coming together for sure.

---

### Post by Quackers on 2012-04-13
I've been using GS in an updated 11-10 install since the beginning. By and large it's been fine for me.
I have experienced the desktop glitch but not for a while now.
Everything is good except for the GS crash/restart after using synaptic - but this is only minor, as there is no other effect.
My beta1 install also uses GS and has been the same.
All in all this cycle's been pretty much a trouble-free run for me. :-)

---

### Post by sgage on 2012-04-13
> **Quackers said:**
> I've been using GS in an updated 11-10 install since the beginning. By and large it's been fine for me.
I have experienced the desktop glitch but not for a while now.
Everything is good except for the GS crash/restart after using synaptic - but this is only minor, as there is no other effect.
My beta1 install also uses GS and has been the same.
All in all this cycle's been pretty much a trouble-free run for me. :-)

I still have the desktop glitch with a fresh install of today's daily. It's some interaction between GS and nautilus.

Try this in Tweak Tool: under Desktop, toggle "have file manager handle the desktop" off and then back on. Same glitch. If you toggle it off and leave it off, no shell reset glitch (but no icons on the desktop).

---

### Post by Quackers on 2012-04-13
I do have the file manager handling the desktop, which is why I have not had the glitch for a while, I suspect.
TBH it is rare that I need to use the alt+F2 r option. In fact, I can't remember the last time :-)

---

### Post by sgage on 2012-04-13
> **Quackers said:**
> I do have the file manager handling the desktop, which is why I have not had the glitch for a while, I suspect.
TBH it is rare that I need to use the alt+F2 r option. In fact, I can't remember the last time :-)

You do or do not have the file manager handling the desktop. The glitch only occurs for me and several others if it IS, and the problem goes away if it ISN'T.

It's not a huge deal - just a minor annoyance. I reset the shell once in a while if I've manually added an extension or .desktop file. Probably use it more now in the develeopment phase than I ever would in day-to-day.

Interestingly, once in a while something (be it Synaptic or whatever) causes GS to crash and reset, and when that happens, the desktop glitch does not appear.

---

### Post by jbicha on 2012-04-13
The desktop glitch bug is mutter bug [673566]("https://bugzilla.gnome.org/show_bug.cgi?id=673566") and will be fixed as part of mutter 3.4.1 next week.

---

### Post by Quackers on 2012-04-13
Sorry sgage for my absence.
Yes I have the file manager handling the desktop and no I haven't had that glitch for some time now. Occasionally if I have left it running overnight (as usual) the glitch will appear. That's the only time now.

Thanks jbicha, it seems 3.4.1 is the answer to all our problems :-) (few though they are).

---

### Post by sgage on 2012-04-13
> **jbicha said:**
> The desktop glitch bug is mutter bug [673566]("https://bugzilla.gnome.org/show_bug.cgi?id=673566") and will be fixed as part of mutter 3.4.1 next week.

Ah, good to hear it! Thanks for the word...

---

### Post by xajeiw9I on 2012-04-13
I have been testing daily builds with Live USB. I have an ASUS A43E (i5 2410m) and an HP dm1-3250br (E-350). The E-350 system has a history of problems with a lot of GNU/Linux distros, Ubuntu 11.10 worked but not as good as I wish. 12.04 started to look good in it, but I was having a lot of crashes when starting Update Manager or Ubuntu Software center. I runned it as my only OS in it for a while during alpha and it was the same.

Today I have not seen crashes yet. On the i5 system the only complaint I have is that some menus felt glitchy, those boxes that open with options when you click on them. They sometimes won't stay open when I click. And the scroll bars that disappear sometimes don't appear and I have to keep passing the mouse over the edge to make it appear. 

I am not sure if these problems have been addressed, but I always try to post bugs when I crash and it says that they were already notified about them. The other problems I related are esthetical and I am not sure which packet is to blame. Are these possibly happening because I am running Live?

---

### Post by suprman2020 on 2012-04-13
12.04 and Gnome Shell have been working great with one exception. There seems to be missing text on the top panel. Funny thing is that it only happens after my laptop has been sleeping. Besides that, the improvement from 11.10 has been great.

---

