---
title: "FVWM-Crystal anyone?"
date: 2007-06-04
forum: The Cafe
---

### Post by urukrama on 2007-06-04
How do you configure fvwm-crystal?

Looking at screenshots from the wm in action, I got tempted to try it out. Installed everything nicely, and started testing it out. It all looks nice, but I have absolutely no idea how to configure the beast. I can, off course, use the settings in the menus, but practically all the screenshots I've seen look nothing like the settings in the menus.

I've dowloaded a theme I liked, but then couldn't figure out what to do with it. Whatever I change in my config file seems to have no effect in the looks, no matter how many times I restart fvwm-crystal.

Man, this is a hard window manager! The fvwm-crystal website doesn't offer any documentation, and there isn't even a howto on these forums.

So -- are there any fvwm-crystalites around here that could help the newcomers getting started?

---

### Post by urukrama on 2007-06-05
Hmm. No one?

---

### Post by starcraft.man on 2007-06-05
Sorry, I'm just a plain GNOME/Beryl user :).

Ummm, I hope I'm not wrong but I think Aysiu mentioned using fvwm for a while, maybe you could give him a nice little PM.... I don't think that many people are using it here though, google or their forums are probably a better bet.

---

### Post by ThomasAdam on 2007-06-07
> **urukrama said:**
> So -- are there any fvwm-crystalites around here that could help the newcomers getting started?

Take the theme that you want (from /usr/share/fvwm-crystal/ typically) and mirror it in ~/.fvwm-crystal -- then you can edit everything therein to your heart's content.

If you're more specific about what it is you want, I am sure I can tailor my answer to suit.

-- Thomas Adam

---

### Post by graabein on 2007-06-07
Screenshots would help to get the thread started...

---

### Post by ThomasAdam on 2007-06-07
> **graabein said:**
> Screenshots would help to get the thread started...

Not really -- it's difficult to describe functionality that way,

-- Thomas Adam

---

### Post by urukrama on 2007-06-11
Thanks, Thomas Adam, that worked fine. The difficulty with fvwm-crystal, though, is that those config files are a bit hard to grasp at times :-). I've extensively configured IceWM, Openbox, Fluxbox and Blackbox before, but this is quite something else. I'm sure I'll have a few more questions...

Is it possible to get a 'normal' alt-tab dialog in fvwm-crystal, one like Metacity or the new Openbox?

---

### Post by ThomasAdam on 2007-06-11
> **urukrama said:**
> Is it possible to get a 'normal' alt-tab dialog in fvwm-crystal, 
one like Metacity or the new Openbox?

No.

-- Thomas Adam

---

### Post by urukrama on 2007-06-11
Is there a good place to download fvwm themes?

---

### Post by ThomasAdam on 2007-06-13
> **urukrama said:**
> Is there a good place to download fvwm themes?

[http://fvwm-themes.sf.net](http://fvwm-themes.sf.net)
[http://fvwm.lair.be](http://fvwm.lair.be)
[http://edulinux.homeunix.org/fvwm/fvwmchanfaq.html](http://edulinux.homeunix.org/fvwm/fvwmchanfaq.html)

-- Thomas Adam

---

### Post by Brian96 on 2007-06-24
A couple more questions:

1. How do you configure panels (particularly those in an existing recipe)? I really like FVWM-Crystal's "Clean" recipe, but I'd like to add a clock to it.

2. How do you configure the pager (change the number of desktops shown, again preferrably within a recipe)?

3. How do you edit menus?

I'd like to be able to do these things through a GUI, if possible.

--Thanks

---

### Post by ThomasAdam on 2007-06-25
> **Brian96 said:**
> 1. How do you configure panels (particularly those in an existing recipe)? I really like FVWM-Crystal's "Clean" recipe, but I'd like to add a clock to it.

Look at the theme, and add another FvwmButtons definition, swallowing FvwmScript-Clock.

> **Brian96 said:**
> 
2. How do you configure the pager (change the number of desktops shown, again preferrably within a recipe)?

Set the DesktopSize (see the FVWM manpage.)

> **Brian96 said:**
> 
3. How do you edit menus?


You'd need to be more specific here.

> **Brian96 said:**
> 
I'd like to be able to do these things through a GUI, if possible.

[http://edulinux.homeunix.org/fvwm/user_enumerate.html](http://edulinux.homeunix.org/fvwm/user_enumerate.html)

-- Thomas Adam

---

### Post by Brian96 on 2007-06-25
> **ThomasAdam said:**
> Look at the theme, and add another FvwmButtons definition, swallowing FvwmScript-Clock.



Set the DesktopSize (see the FVWM manpage.)



You'd need to be more specific here.



[http://edulinux.homeunix.org/fvwm/user_enumerate.html](http://edulinux.homeunix.org/fvwm/user_enumerate.html)

-- Thomas Adam

Thanks! I'll look into these.

By "edit menus" I mean change the location of applications within the menus. I accomplished this by changing them in gnome.

Thanks again.

---

### Post by the music man on 2007-07-10
I also have some questions about fvwm. How do i make something run at the startup of fvwm-crystal (*after *logging in with gdm)? I read someting in the fvwm manpage but i don't understand it.

---

### Post by BLTicklemonster on 2007-12-09
I want to add firefox and thunar to my menu in fvwm crystal. How do I do that?

---

### Post by chris4585 on 2008-01-07
If you installed the programs all you should have to do is restart fvwm-crystal and look for the programs in the menu's good luck

---

