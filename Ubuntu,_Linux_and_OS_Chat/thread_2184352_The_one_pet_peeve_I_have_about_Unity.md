---
title: "The one pet peeve I have about Unity"
date: 2013-10-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Vannyi on 2013-10-28
So, I've installed Ubuntu 12.04 and while I disagree with the inflexibility of the Unity bar, it is something that I can get used to on the side.

What I really miss however is the fact that when you have a browser maximized, it doesn't sit flush with the top of the screen.  The top of the screen has the clock and a few other apps.

What this means is that now if I want to close a browser tab, I've got to line up the mouse arrow on both the X and the Y axis whereas before, I'd just push the mouse arrow to the top of the screen and then go left or right to close the tab. 

This may not seem like a big deal, but for someone with shaky hands, it does make a difference.  I guess there is no way to at least get the bar to be flush with the top of the screen?

---

### Post by ajgreeny on 2013-10-28
So what you want is a panel at the bottom of the screen, not the top?

If so have a look at Xubuntu or Lubuntu.

You could also stick with your current Ubuntu (to give you all the applications you now have) and add the xfce4 or lxde desktop packages, then choose one or other of those when you get to the login screen.

---

### Post by buzzingrobot on 2013-10-28
The top panel is fixed on Unity.  Xubuntu has a top panel as installed, but it's easily moved to the bottom of the screen.  Lubuntu, with LXDE, puts the panel on the bottom by default.

Kubuntu, with KDE, of course, comes with the panel on the bottom by default.

The Mate desktop is essentially the Gnome 2 interface you may be used to if you just upgraded to 12.04.  By default, it has panels on top and bottom, but is easily configured to use only a bottom panel.  Look at mate-desktop,org for more info and how to install.

The Linux Mint distribution is based on Ubuntu and used the same software repositories, so applications available for Ubuntu are available for Mint.  It comes in 4 interface styles, each with a panel on the bottom.  Mint has a reputation as a solid and very usable distribution: linuxmint.com.

---

### Post by craig10x on 2013-10-28
I don't know if you realize it, but because the unity top panel is a global menu, space is actually being saved at the top...the reason is that what would normally be on the top section of the browser is incorporated into the actual panel bar...so no extra space is really taken at all!

---

### Post by buzzingrobot on 2013-10-28
> **craig10x said:**
> I don't know if you realize it, but because the unity top panel is a global menu, space is actually being saved at the top...the reason is that what would normally be on the top section of the browser is incorporated into the actual panel bar...so no extra space is really taken at all!


The OP's concern is about usability with an unsteady hand, not screen space.

---

### Post by cariboo on 2013-10-29
If you press F11, you get the browser in full screen without being bothered with any top panel, or anything else on the desktop. :-)

---

### Post by malspa on 2013-10-29
> **cariboo907 said:**
> If you press F11, you get the browser in full screen without being bothered with any top panel, or anything else on the desktop. :-)

This does not work for me. Unity in 12.04. F11 toggles the volume on and off on my notebook. But I don't share the OP's one pet peeve.

---

### Post by vasa1 on 2013-10-29
> **malspa said:**
> This does not work for me. Unity in 12.04. F11 toggles the volume on and off on my notebook. But I don't share the OP's one pet peeve.
Maybe you need to use Fn+F11?

---

### Post by malspa on 2013-10-29
> **vasa1 said:**
> Maybe you need to use Fn+F11?

Oh, yeah. Duh.

---

### Post by vasa1 on 2013-10-29
> **malspa said:**
> Yeah, that does it. So does pressing F11 alone, as cariboo907 wrote, work on other computers the same as Fn+F11 here?

On my Dell 1545 laptop, all but one of the function keys have dual roles. Depending on what I set in the BIOS, I can use the function key alone or with "Fn" and access one or the other purpose. So I've used the setting in BIOS that lets me use the function key in isolation for the "conventional" function purpose and use Fn+Fx for the "multimedia" aspect.

---

### Post by malspa on 2013-10-29
yeah, dumb question on my part

---

### Post by deadflowr on 2013-10-29
You can always use keyboard shortcuts to open close and move between tabs, and or windows.
Not the most optimal solution, but it's something.

---

### Post by Vannyi on 2013-10-29
> **cariboo907 said:**
> If you press F11, you get the browser in full screen without being bothered with any top panel, or anything else on the desktop. :-)

The F11 option was nice, to bad you don't get the tabs at top of the screen...that would have been optimal. :)

---

### Post by VietCanada on 2013-10-30
Wow! How many posters have to complain about this bar before somebody fixes it? How hard can that be? Maybe Canonical should run a crowdfunding compaign to hire a programmer to fix it. I see a record compaign for funding in Ubuntu's future if they did that.

---

### Post by craig10x on 2013-10-30
Fix what? The top panel works the way it is supposed to...the original poster was just asking how to do something out of the ordinary...

---

### Post by buzzingrobot on 2013-10-30
F11 seems to be a Firefox-specific command.  

Here, on Unity 13.10, the tabs are initially displayed after F11 maximizes the window, but then the window moves up momentarily and obscures them.  Tapping F11 will redisplay the tab row, but will also display Unity's top panel.

Control-tab will cycle through the current tabs even if they are obscured.  Other options are listed here: [http://www.shortcutworld.com/en/win/Firefox.html](http://www.shortcutworld.com/en/win/Firefox.html).

What the OP really needs, however, is a Unity panel that hides when a window is maximized. Canonical should not make design decisions based on a handful of forum posts, but it would be reasonable to consider it an accessibility need. (The Gnome Shell panel does not hide, either, and I suspect Unity is inheriting that behavior.)

The OP might boot a live Xubuntu image and see if the panel there behaves differently or if it can be configured.

---

### Post by malspa on 2013-10-30
> **buzzingrobot said:**
> What the OP really needs, however, is a Unity panel that hides when a window is maximized. Canonical should not make design decisions based on a handful of forum posts, but it would be reasonable to consider it an accessibility need. (The Gnome Shell panel does not hide, either, and I suspect Unity is inheriting that behavior.)

The OP might boot a live Xubuntu image and see if the panel there behaves differently or if it can be configured.

I was thinking along the same lines. I don't have a problem with Unity's top panel, but if I did, I might go with Xubuntu instead (or simply install Xfce) because xfce4-panel can be moved anywhere you want it. Actually, in distros where I use Xfce, I currently have the panel over on the left side of the screen, like where Unity's launcher sits, which works out nicely for a wide-screen monitor.

---

### Post by buzzingrobot on 2013-10-30
Just noticed that if you push the cursor against the top of the screen after F11 maximizes it, the tabs become visible and the panel does *not*.

---

### Post by coffeecat on 2013-10-30
> **Vannyi said:**
> The F11 option was nice, to bad you don't get the tabs at top of the screen...that would have been optimal. :)

> **buzzingrobot said:**
> Just noticed that if you push the cursor against the top of the screen after F11 maximizes it, the tabs become visible and the panel does *not*.

I can confirm buzzingrobot's observation with Unity in 13.10. @Vannyi, does that work for you in 12.04?

---

### Post by malspa on 2013-10-30
> **buzzingrobot said:**
> Just noticed that if you push the cursor against the top of the screen after F11 maximizes it, the tabs become visible and the panel does *not*.

Doesn't work for me here in 12.04.

---

### Post by Vannyi on 2013-10-30
> **coffeecat said:**
> I can confirm buzzingrobot's observation with Unity in 13.10. @Vannyi, does that work for you in 12.04?

Yes, F11 does work for me in Chrome while on 12.04...I just don't get the tabs, but when I was looking in the Google Forums, this was something that other users have been requesting as well.

---

### Post by coffeecat on 2013-10-30
Just to add to the last two posts. I've now tried firefox in 12.04. I can make the tabs visible in Firefox after using F11 in both 12.04 and 13.10, but the tabs don't appear in Chromium in 13.10. It seems to be browser specific then.

---

### Post by malspa on 2013-10-30
> **coffeecat said:**
> It seems to be browser specific then.

Ah.

---

### Post by Vannyi on 2013-10-30
> **coffeecat said:**
> Just to add to the last two posts. I've now tried firefox in 12.04. I can make the tabs visible in Firefox after using F11 in both 12.04 and 13.10, but the tabs don't appear in Chromium in 13.10. It seems to be browser specific then.

You are right, tabs do appear in Firefox, but not in Chrome.

---

