---
title: "UniDockyNapse 11.10"
date: 2012-02-18
forum: The Cafe
---

### Post by neu5eeCh on 2012-02-18
Terrible name, but just an FYI. One of my _least_ favorite **"**'features**'"** (monolithic air quotes) of Unity is its ""Launcher"". Just noticed [this derivative]("http://sourceforge.net/projects/unidockynapse/") released yesterday, apparently. Looks like it's 32bit. I've been yearning and yearning for a way to remove the launcher. This derivative gives me that. Don't know anything more about it, but I'm going to install it on a spare partition and try it out.

---

### Post by Version Dependency on 2012-02-18
Nothing you can't already do in Ubuntu.  You want the old Gnome 2 style top panel/bottom dock look but want the global menu and window decorations on the panel?  Install Gnome Classic and add some Gnome [applets]("http://www.webupd8.org/2012/02/window-applets-finally-available-for.html") (Indicator Appmenu I think is the global menu; and Window Buttons adds the window decorations to the panel).  To add the applets, hit SUPER-ALT-RIGHTCLICK on the panel.  Also, do the same for the bottom panel to delete it.  Add Cairo Dock or AWN or whatever dock you choose.  Add Synapse or whatever launcher you want...or use one of the menu applets on the dock you choose.  Or add a menu button to the top panel.

Takes less than 5 minutes.

---

### Post by neu5eeCh on 2012-02-18
> **Version Dependency said:**
> Nothing you can't already do in Ubuntu.  You want the old Gnome 2 style top panel/bottom dock look but want the global menu and window decorations on the panel?  Install Gnome Classic and add some Gnome [applets]("http://www.webupd8.org/2012/02/window-applets-finally-available-for.html") (Indicator Appmenu I think is the global menu; and Window Buttons adds the window decorations to the panel).  To add the applets, hit SUPER-ALT-RIGHTCLICK on the panel.  Also, do the same for the bottom panel to delete it.  Add Cairo Dock or AWN or whatever dock you choose.  Add Synapse or whatever launcher you want...or use one of the menu applets on the dock you choose.  Or add a menu button to the top panel.

Takes less than 5 minutes.

That's flatly wrong; installing Gnome Classic has nothing to do with it. Show me how to remove the launcher in Unity, **then** you can write that this is "Nothing you can't already do in Ubuntu". That's not a challenge. I would sincerely like to know. Also, [AWN & Unity conflict]("http://ubuntuforums.org/showthread.php?t=1897966"), which is probably why docky was chosen.

---

### Post by Version Dependency on 2012-02-18
> **VTPoet said:**
> That's flatly wrong; installing Gnome Classic has  nothing to do with it. Show me how to remove the launcher in Unity, **then**  you can write that this is "Nothing you can't already do in Ubuntu".  That's not a challenge. I would sincerely like to know. Also, [AWN & Unity conflict]("http://ubuntuforums.org/showthread.php?t=1897966"), which is probably why docky was chosen.

You seemed confused.  I didn't say this UniDockySynapse thingy used  Gnome Classic.  I simply stated that there is nothing that it does that  can't be achieved already in Gnome Classic.  After all, if you remove the launcher and the dash and lenses...all you have left is a basic gnome panel anyway...minus the global menu which is easily added.

---

### Post by neu5eeCh on 2012-02-18
I'm not confused. It's completely different. Gnome Classic uses Mutter, not Compiz. Using _Unity_ without the Launcher gives you all the benefits of Compiz on a Gnome Base without a Launcher. It gives you something more like the old Ubuntu  _with_ Compiz.

---

### Post by Version Dependency on 2012-02-18
> **VTPoet said:**
> I'm not confused. It's completely different. Gnome Classic uses Mutter, not Compiz.

It seems you are confused.  Gnome Classic comes in two varieties, one with no effects (Mutter) and one with effects (Compiz).  You get both when you install it.

---

### Post by neu5eeCh on 2012-02-18
It seems you are confused too. No effects comes with Metacity, not Mutter. You are right that effects comes with Compiz, however, Gnome Classic does not come pre-installed in 11.10 - and that leads to problems. To [quote glennric]("http://ubuntuforums.org/showthread.php?t=1860615&page=2"):

"To put it simply for you, the gnome classic session is not working as it  should be.  The Ubuntu devs have focused on the switch to the  Unity/Gnome desktop and have for the most part ignored issues with the  classic desktop.  The end result is that the classic session is buggy  and poorly setup, while at the same time the unity session is buggy and  poorly setup because it is not ready yet.  Leaving Ubuntu a real mess.   If this happened for one of the projects that I develop for I would be  rather embarrassed."

The beauty of unidockynapse, if it works as advertized, is that you can bypass this whole mess. Using Gnome Classic just isn't a comparable option.

---

### Post by neu5eeCh on 2012-02-19
Downloaded and tried installing it, but I either had a bad burn or the distro is buggy. It worked in live mode, once, and I liked it; but I won't be using it. I'm back to Cinnamon.

---

### Post by Version Dependency on 2012-02-19
> **VTPoet said:**
> Downloaded and tried installing it, but I either had a bad burn or the distro is buggy. It worked in live mode, once, and I liked it; but I won't be using it. I'm back to Cinnamon.

I downloaded it and gave it go to see if it worked.  I was able to install it but it was a bit buggy.  Docky, in particular, didn't play well.  It was incredibly slow...so slow I installed Cairo Dock and AWN to see if they performed a little better.  They did.  But the interesting thing is that, in Cairo Dock, I noticed an icon for an open app (even though no apps were open on my desktop).  The app -- unity-2d-panel.   

To create this "Unity panel with compiz with a dock" session in Ubuntu, login to Unity 2D...set the unity-2d-launcher (unity-2d-shell in 12.04) to no longer be executable.  Go to startup programs and add "compiz --replace".  Install Docky and Synapse if you wish (add them to startup programs).  Log out and log back in.  Voila.  I tested this in 12.04 and it worked great.

---

### Post by neu5eeCh on 2012-02-19
I didn't have the problem with docky running slowly, but then I never got past the Live CD. The installer crashed (booted out/unmounted the CD) every time I tried to run it. It was evidently confused as to which drives it should be un-mounting. So you're running compiz in Unity 2D? I'll try that. I'm running out of partitions to experiment with.

---

