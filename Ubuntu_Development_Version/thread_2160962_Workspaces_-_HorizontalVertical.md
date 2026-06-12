---
title: "Workspaces - Horizontal/Vertical"
date: 2013-07-08
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2013-07-08
My Unity DE is 98% fabulous and I have 4 horizontal workspaces that I can mouse wheel scroll through to my hearts delight.   Unfortunately, I need to run a VirtualBox VM running Win 7 Pro (I assign it to one of the workspaces) and for some reason that currently alludes me, the bottom half of the Windows bottom panel is missing. There are some other issues, but never no mind.   So I tried bringing in the Gnome DE and praise the Great Pumkin the VB Windows VM works a treat; Win bottom panel all correct and accounted for.   Unfortunately, in GS the workspaces are vertical, not horizontal, amd imo that makes switching a nightmare.

I've tried CCSM to set the #workspaces to 4h x 1v but the setting doesn't seem to 'stick'.   If I go back into CCSM after making these changes the number of workspaces has reset to 1 horizontal, and vertical and number of desktops are both blank.   I'm at a loss to figure out what to do next and would appreciate any advice.

For reference, here's my current specs courtesy of a VinDSL script:```
~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~Current Date/Time: Tue Jul  9 10:22:45 WST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-2-generic
Unity Release: unity 7.0.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 650/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 319.32

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes 
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: xserver-xorg-core
  Installed: 2:1.14.1-0ubuntu0.8

Gnome Release: 
GNOME Shell 3.8.3
```

Edit:   Hmmm... I just checked Gnome-Tweak-Tool and I have Dynamic Workspaces switched 'off' and with the number set to 4... there is nowhere to set the orientation of those workspaces.   Very confusing.

---

### Post by mc4man on 2013-07-08
> **PJs Ronin said:**
> 

I've tried CCSM to set the #workspaces to 4h x 1v but the setting doesn't seem to 'stick'.   If I go back into CCSM after making these changes the number of workspaces has reset to 1 horizontal, and vertical and number of desktops are both blank.   I'm at a loss to figure out what to do next and would appreciate any advice.



Edit:   Hmmm... I just checked Gnome-Tweak-Tool and I have Dynamic Workspaces switched 'off' and with the number set to 4... there is nowhere to set the orientation of those workspaces.   Very confusing.
As far as a ubuntu/unity session "Dynamic Workspaces" in the tweak tool is meaningless, just for Gs.

ccsm seems to often misreport the number of Ws's, doesn't matter what ccsm says, what do you actually have?
While I use rotate (4h/1v), switched to wall & set 1h/4v. While ccsm shows as in screen it's still 1h/4v. That it isn't just 1x1 can be confirmed in screen by the presence of the expo icon which would disappear if only on 1 Ws. (obviously opening expo would also show 1h/4v

So do you actually have 1h/4v after setting to that?

---

### Post by PJs Ronin on 2013-07-09
@mc4man.   Thank you for your response.   Whilst some of your comments are flying over my head I will answer the best I can and hope I'm not telling you how to suck eggs.

> **mc4man said:**
> ... ccsm seems to often misreport the number of Ws's, doesn't matter what ccsm says, what do  you actually have?
I currently have 4 workspaces (see image) that all work.   The representation in the attached graphic is a Gnome Extension called "Workspacebar" that at least shows me the workspaces and allows me to click to the desired one.   I can also ctrl-alt up/down arrow to select any of the workspaces.   I cannot seem to get the mouse scroll wheel to scroll through the workspaces as I can with Unity.
[ATTACH=CONFIG]244545[/ATTACH]

> **mc4man said:**
> ... While I use rotate (4h/1v), switched to wall & set 1h/4v. While ccsm shows as in screen it's still 1h/4v. That it isn't just 1x1 can be confirmed in screen by the presence of the expo icon which would disappear if only on 1 Ws. (obviously opening expo would also show 1h/4v Yeah, this is over my head.   I guess you're referring to CCSM and the only thing I can find in there refers to Desktops.   I have tried to set this to every combination of horizontal/vertical I can imagine but when I re-open CCSM the setting has reverted to this:
[ATTACH=CONFIG]244546[/ATTACH]

---

### Post by mc4man on 2013-07-09
So you want to run gnome-shell but adjust your ws's in compiz?

---

### Post by PJs Ronin on 2013-07-09
> **mc4man said:**
> So you want to run gnome-shell but adjust your ws's in compiz?

I want to run GS and have 4 horizontal workspaces and hopefully scroll those workspaces with the mouse wheel activated from anywhere on the desktop (as is currently possible with Unity).   My inexperience precludes me from commenting on compiz being the best (only?) way of doing this.   I've tried gnome-tweak-tool, compiz and googled options for editing dconf/gconf, all with no result.

---

### Post by cariboo on 2013-07-09
> **PJs Ronin said:**
> I want to run GS and have 4 horizontal workspaces and hopefully scroll those workspaces with the mouse wheel activated from anywhere on the desktop (as is currently possible with Unity).   My inexperience precludes me from commenting on compiz being the best (only?) way of doing this.   I've tried gnome-tweak-tool, compiz and googled options for editing dconf/gconf, all with no result.

Compiz doesn't run when using gnome-shell so using ccsm to try and adjust the desktops will fail every. GS uses mutter as compositor.

---

### Post by PJs Ronin on 2013-07-09
ty cariboo907.

It would seem my cause is lost as mutter is not very configurable.

---

### Post by markbl on 2013-07-10
> **PJs Ronin said:**
> Unfortunately, in GS the workspaces are vertical, not horizontal, amd imo that makes switching a nightmare.
I don't understand how anybody could prefer the "classic" n by n workspace switcher model used by Unity versus the dynamic linear model used by GS? Who wants to think about up/down versus left/right? Just step through all workspaces quickly with ctrl+alt+up/down. Much simpler that you don't have to remember and negotiate the silly corner turns.

---

### Post by Cheesemill on 2013-07-10
I use the Desktop Scroller shell extension to handle switching workspaces, a mouse up/down on either edge of the screen will switch workspaces.

I actually prefer this to having to scroll from the desktop as I can switch workspaces even if the desktop isn't visible (scrolling from the desktop still works however).

[https://extensions.gnome.org/extension/561/desktop-scroller-all-sides-for-gnome-36/](https://extensions.gnome.org/extension/561/desktop-scroller-all-sides-for-gnome-36/)

---

### Post by PJs Ronin on 2013-07-10
> **markbl said:**
> I don't understand how anybody could prefer the "classic" n by n workspace switcher model used by Unity versus the dynamic linear model used by GS? Who wants to think about up/down versus left/right? Just step through all workspaces quickly with ctrl+alt+up/down. Much simpler that you don't have to remember and negotiate the silly corner turns.

It's not an issue of thinking about "up/down versus left/right", it's an issue about how I get to the workspace that's currently demanding my attention.   Under Unity I can position the mouse pointer anywhere in free space, roll the mouse wheel and voila, I am there.   Under GS I have to position the mouse pointer over a specify, and very small, part of the screen and then mouse scroll to bring up the desired workspace.   I live by the mouse, not by keyboard combinations.

> **Cheesemill said:**
> I use the Desktop Scroller shell extension to handle switching workspaces, a mouse up/down on either edge of the screen will switch workspaces.

I actually prefer this to having to scroll from the desktop as I can switch workspaces even if the desktop isn't visible (scrolling from the desktop still works however).

[https://extensions.gnome.org/extension/561/desktop-scroller-all-sides-for-gnome-36/](https://extensions.gnome.org/extension/561/desktop-scroller-all-sides-for-gnome-36/)

Ty, I shall have a look.

And this is the thing that really confuses me (from the Gnome3 Staging PPA thread):> **Cavsfan said:**
> I am trying to be a will participant but, I am not into adding extra PPA's that you already know are going to break.
But, I have had Raring running fairly flawlessly **not using unity but, classic gnome**.
**Have Compiz, Emerald, CCSM, the cube and Cairo Dock all working great. The cube rotates in 3D and I managed to put colors on the top and bottom.**
I had to use Application Switcher in CCSM to get ALT+TAB to work in gnome.
I got VinDSL's conky installed and updated to match my system (and added 13.04 to my signature). :D ...

The bolding is mine, but from that (and many other posts on this forum) I 'assumed' that Compiz was a mechanism for adjusting GS.

---

### Post by markbl on 2013-07-10
> **PJs Ronin said:**
> Under Unity I can position the mouse pointer anywhere in free space, roll the mouse wheel and voila, I am there.  Under GS I have to position the mouse pointer over a specify, and very small, part of the screen and then mouse scroll to bring up the desired workspace.  I live by the mouse, not by keyboard combinations.
That's not standard in Unity. You must have enabled that functionality via a special Compiz setting. The same functionality can be had in GS in an analogous way by enabling the Desktop Scroller extension, so your argument is moot.

---

### Post by PJs Ronin on 2013-07-10
> **markbl said:**
> That's not standard in Unity. You must have enabled that functionality via a special Compiz setting. The same functionality can be had in GS in an analogous way by enabling the Desktop Scroller extension, so your argument is moot.
I was not making an argument for or against anything, simply requesting assistance.   Your post was made before I had a chance to install the Desktop Scroller (I'm two hours west of you).   I have now installed Desktop Scroller and whilst it is somewhat limited versus the Unity/Compiz settings, it has broadened the mouse response area markedly and I'm happy to live with that.

Thanks for all the assistance, I shall mark this thread solved. 

(although I am still confused as to why there are so many posts about GS/Compiz usage.  Such is life and Linux.)

---

### Post by grahammechanical on 2013-07-10
You have installed the Gnome 3 DE complete with Gnome 3 shell. Which is completely different from what some people call classic Gnome - gnome-session-fallback. It is clear that gnome-session-fallback works on top of Compiz but Gnome 3 DE does not use Compiz.

Regards.

---

### Post by PJs Ronin on 2013-07-10
> **grahammechanical said:**
> You have installed the Gnome 3 DE complete with Gnome 3 shell. Which is completely different from what some people call classic Gnome - gnome-session-fallback. It is clear that gnome-session-fallback works on top of Compiz but Gnome 3 DE does not use Compiz.

Regards.

Thank you for that :)
I wish there was a roadmap linking all these permutations together.   Nonetheless, I now have some new experimenting to do... woot :)

---

