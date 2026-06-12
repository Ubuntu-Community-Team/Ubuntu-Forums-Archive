---
title: "Xubuntu - Composition By Default In 11.04"
date: 2011-04-08
forum: The Cafe
---

### Post by Lucradia on 2011-04-08
When I installed Xubuntu 11.04 today on my netbook I noticed many things wrong with it right off the bat. Some are good things, some are bad.

**The Bad:**
```
* The bottom panel now auto-hides, is transparent, and is centered like a dock, and is now dock-like in comparison to before.
* XFWM4's composition is on by default on my Asus EeePC 1015PE Netbook.
* More usage of the indicator applet system like GNOME 2.
* gmusicbrowser (GNOME App?) we have too many gnome apps in Xubuntu already (Including Pidgin, yep, requires gconf2.)
```

**The Good:**
```
* The top panel now has workspace switching, and the window buttons thing.
* The applications menu is icon'd by default.
* The xubuntu logo now fades out to reveal the GDM screen rather than to have it suddenly flash to show it.
```

**The Bugs:**
```
* Turning off XFWM4's composition may cause the XFCE4 Panel to disappear, and won't come back unless you run it, and an OpenGL app takes full screen (IE: Screensaver)
* If you try to run xfce4-panel and you can't get it back, terminal will say it's running, but you can't see it somehow.
* Using the sudo version of xfce4-panel will cause the Applications menu to not be able to use the "Log Out..." as no session manager is provided for sudo's environment.
* If XFCE4-Panel is removed accidentally due to no composition, it won't come back into view even if you turn composition back on.
** It will not return even if you set it to start-up apps.
** It will not return even if you save session and it's running.
```

Xubuntu people should help get Ayttm to be better, so Xubuntu can include it instead of Pidgin. Ayttm does not need gconf/2. (Pidgin only needs it for proxy information.)

Firefox 4 still needs ubufox and the gnome-support package for some strange reason (even though there's a stand-alone package that does what gnome-support does, without needing gnome.)

Something other than GDM should be used (SLiM?) LXDE has its own upcoming DM, and GDM is bulky.

---

### Post by XubuRoxMySox on 2011-04-09
I should know better than to experiment with a Beta release, especially since I only have one 'puter and need it for school!

But, I'm an impulsive kid who sometimes takes foolish risks, lol. Like installing Xubuntu 11.04 Beta 1 yesterday.

I *like* the disappearing panel! But adding a *new* panel isn't possible on my 'puter yet for some reason. I wanted to have a "docky-looking" panel on the bottom that disappears 'til you mouse over it, and the task bar on a disappearing panel on top. But I can't add the second panel, and the task bar goes into the bottom panel, changing it's size.

Not a show stopper, and it's Beta anyway. I like the full transparency of the panel (who needs a dock when you have awesome looking panels in the new Xfce!) and the other goodies. And I really like the new choice of truly lightweight apps now, more Xfce-apps by default instead of Gnome all over the place. Xubuntu is slimmed down, lean and mean! 

I promised myself I'd stick to the LTS versions only. Dunno what came over me! But so far, even with the li'l bugs above, the newest Xubuntu is wonderful!

Still a Xubuntu fanboy,
Robin

---

### Post by Lucradia on 2011-04-09
> **dixiedancer said:**
> I should know better than to experiment with a Beta release, especially since I only have one 'puter and need it for school!

But, I'm an impulsive kid who sometimes takes foolish risks, lol. Like installing Xubuntu 11.04 Beta 1 yesterday.

I *like* the disappearing panel! But adding a *new* panel isn't possible on my 'puter yet for some reason. I wanted to have a "docky-looking" panel on the bottom that disappears 'til you mouse over it, and the task bar on a disappearing panel on top. But I can't add the second panel, and the task bar goes into the bottom panel, changing it's size.

Not a show stopper, and it's Beta anyway. I like the full transparency of the panel (who needs a dock when you have awesome looking panels in the new Xfce!) and the other goodies. And I really like the new choice of truly lightweight apps now, more Xfce-apps by default instead of Gnome all over the place. Xubuntu is slimmed down, lean and mean! 

I promised myself I'd stick to the LTS versions only. Dunno what came over me! But so far, even with the li'l bugs above, the newest Xubuntu is wonderful!

Still a Xubuntu fanboy,
Robin

I agree on this, and in fact, I was one person who helped get the Xubuntu-meta people to package Parole into Xubuntu instead of totem when Parole 0.2 was released. As 0.2 Parole was the first stable version, and is developed on the XFCE environment. But I like the single panel default environment of XFCE the most. The transparency, however, is good because XFCE 4.8 helped fix all that.

---

### Post by gsmanners on 2011-04-09
Yeah, I noticed that comp is on by default. No big deal. Just turn it off if you don't like it. The panels are never close to the way I like them by default. No big deal. Just change them. As for gdm, I think that's getting replaced by lightdm at some point. Maybe not in 11.04 but almost certainly by 11.10.

---

### Post by Lucradia on 2011-04-09
> **gsmanners said:**
> Yeah, I noticed that comp is on by default. No big deal. Just turn it off if you don't like it. The panels are never close to the way I like them by default. No big deal. Just change them. As for gdm, I think that's getting replaced by lightdm at some point. Maybe not in 11.04 but almost certainly by 11.10.

Regardless, I'm going to do LTS on my netbook. I rarely use my netbook.

---

