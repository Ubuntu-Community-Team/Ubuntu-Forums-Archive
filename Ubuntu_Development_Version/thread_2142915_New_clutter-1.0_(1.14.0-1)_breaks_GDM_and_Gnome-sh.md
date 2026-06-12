---
title: "New clutter-1.0 (1.14.0-1) breaks GDM and Gnome-shell (3.6.3)"
date: 2013-05-07
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-05-07
Just to remind you, that if you have a Saucy (or Raring) setup with gnome-shell from official repos (version 3.6.3),
do not install new clutter-1.0 (1.14.0-1).
It will break both gdm and gnome-shell. Gdm will freeze and you are not able to login. X will also freeze, so startx will not help there.
However, you can still login from tty1 (Ctrl + Alt + F1).
You can sort this issue by downgrading clutter packages to the previous version (1.12.2).

---

### Post by kuvanito on 2013-05-07
yeap
it just happened to me,dang it!

---

### Post by Cheesemill on 2013-05-07
Does anyone know if this affects gnome-shell 3.8 as well?

I was about to update my system but I'll hold off for a while until there's any more news.

---

### Post by Harry33 on 2013-05-07
> **Cheesemill said:**
> Does anyone know if this affects gnome-shell 3.8 as well?

I was about to update my system but I'll hold off for a while until there's any more news.

It does not affect Gnome3.8 branch.
In fact, the Gnome3 PPA (raring branch) already has the clutter-1.0 (1.14.0-1).
So users using the Gnome3 PPA are not affected.

This might not even be a bug. New clutter may only need the newer gnome-shell, gdm and mutter.

---

### Post by dino99 on 2013-05-07
even gdm have been dropped with GS 3.8.1

---

### Post by Harry33 on 2013-05-08
> **dino99 said:**
> even gdm have been dropped with GS 3.8.1

What exactly are you saying here?
I have GS 3.8.1 and I use solely gdm (3.8.1.1).
Do you mean the dependencies of gnome-shell?
In order to get Unity work, the gnome-shell now depends on libgdm (and not gdm), after the old gdm package was split into packages gdm and libgdm.

---

### Post by VinDSL on 2013-05-08
Glad I read this thread...

I noticed a brace of clutter upgrades in Synaptic, this morning.

I wouldn't have done the upgrade(s) at this point in time, anyway, because Synaptic wanted to remove gnome et cetera.  Better to be safe than sorry!

Instead, I'll check later this afternoon and see if the coast is clear... :)

Thanks!

---

### Post by kuvanito on 2013-05-08
dang it.I need a fix for this asap :)

---

### Post by VinDSL on 2013-05-09
Did you guys ever get this sorted?!?!?

I finally did an upgrade, a few minutes ago, and everything seems to be working fine.

---

### Post by Harry33 on 2013-05-10
> **VinDSL said:**
> Did you guys ever get this sorted?!?!?

I finally did an upgrade, a few minutes ago, and everything seems to be working fine.

No this sissue is definitely not solved ATM.
Workaround is clear: downgrade to the previous version 1.12.2.

VinDSL, you may have Gnome3 enabled and thus you would not be using Gnome 3.6.
This issue does not affect Gnome 3.8.

---

### Post by Chanath on 2013-05-10
Thanks for letting us know about this. I had installed Gnome-shell through Synaptic and it froze. Then, I downloaded the Ubuntu-gnome saucy, but that too froze. Good that I noticed this post. I reinstalled Ubuntu Saucy, added the raring ppa and installed the gnome-shell 3.8.1 and and everything is working well. 3.8 doesn't have enough extensions yet, but its okay.:)

Regards!
Chanath

---

### Post by Harry33 on 2013-05-10
> **Chanath said:**
> Thanks for letting us know about this. I had installed Gnome-shell through Synaptic and it froze. Then, I downloaded the Ubuntu-gnome saucy, but that too froze. Good that I noticed this post. I reinstalled Ubuntu Saucy, added the raring ppa and installed the gnome-shell 3.8.1 and and everything is working well. 3.8 doesn't have enough extensions yet, but its okay.:)

Regards!
Chanath

Yes I think it is better that people switch to Gnome 3.8 (enabling Gnome3 PPA).
Saucy will follow anyway, sooner or later.

---

### Post by VinDSL on 2013-05-10
> **Harry33 said:**
> VinDSL, you may have Gnome3 enabled and thus you would not be using Gnome 3.6.
This issue does not affect Gnome 3.8.
I was concerned about how the multiple, new, clutter upgrades would affect GS 3.9.1

Synaptic wanted to remove gnome & gnome-core, which I had already removed, some time again, which raised some flags, for me.

I replaced gnome & gnome-core with the ubuntu-gnome-desktop package, 2 months ago.  They must have sneaked back in, under the radar.

Before proceeding with the clutter upgrades, I did a quick search, and found this thread, which set off the warning bells, as well as the flags. LoL!  :D

Anyway, now that I'm back on path -- I was thinking about this thread -- and wondered if it had been sorted yet...

---

### Post by VinDSL on 2013-05-10
> **Chanath said:**
> 3.8 doesn't have enough extensions yet, but its okay. :)
I don't run all that many extensions, but the ones I do run are paramount to my happiness/sanity.  

Without the correct mix of extensions, GS is a kludge IMO.  With them, GS >= Unity, IMO.  :)

To make them work...

Sometimes you need to compile the extension from source.  Example: Dash to Dock

Other times, you can simply hack the json file, and include the version of Gnome you're running.  Example:  Icon Hider

It's lonely out here, in the +1 wilderness!  

Sometimes, you just need to take matters in your own hands, you know?  ;)

---

### Post by Chanath on 2013-05-10
I must've been little too quick to say everything was alright. After few hours, gnome-shell started giving problems, mainly getting frozen from time to time. Maybe I should wait till Saucy becomes at least beta.:(

---

### Post by VinDSL on 2013-05-10
> **Chanath said:**
> Maybe I should wait till Saucy becomes at least beta.:(
Really?!?!?

> Ubuntu 13.10 Release Schedule

[LIST]
[*]Alpha 1 &#8211; June 20th
[*]Alpha 2 &#8211; July 18th
[*]Alpha 3 &#8211; August 1st
[*]**[COLOR="#0000CD"]Beta 1- September 5th[/COLOR]**
[*]Final Beta &#8211; September 26th
[*]Release Candidate &#8211; October 10th
[/LIST]


You'll miss all the 'fun'...  :)

---

### Post by Chanath on 2013-05-10
> **VinDSL said:**
> Really?!?!?

You'll miss all the 'fun'...  :)

True, but it gives me a headache waiting for the apps to unfreeze. Of course, I am not letting go of the installation, and would go back from time to time upgrading it.:smile:

---

### Post by Rukiri on 2013-05-11
Clutter 1.14 and 1.14.1 work great under gnome-3.8, use earlier versions of clutter for gnome 3.6

---

### Post by jppr on 2013-05-11
That's common sense, it is a triumph of the Clutter will be updated to the new version but the rest is left to the old version ... What is there really to pay that Gnome to get officially updated to version 3.8 ...<snip>...

---

### Post by Chanath on 2013-05-12
Well, reinstalled Saucy and used Raring Gnome3 ppa and this time it worked very well. I didn't uninstall Unity like the last time. So far so good!:)

---

### Post by sgage on 2013-05-12
> **Harry33 said:**
> Yes I think it is better that people switch to Gnome 3.8 (enabling Gnome3 PPA).
Saucy will follow anyway, sooner or later.

Do you have any idea when 3.8 might enter the main repos? I did a fresh install of yesterday's daily of regular Ubuntu, and added Gnome Shell, and sure enough, it still doesn't work. I applied the gnome3 ppa, and it killed Unity. So I purged the ppa and downgraded libclutter and friends, so now I have both Unity and GS working well.

I wonder what killed Unity, exactly, from the newer Gnome Shell install. Maybe they're still getting it sorted before 3.8 is in the main repos...

---

### Post by pressureman on 2013-05-12
I'm currently running GNOME Shell 3.8 from the GNOME 3 PPA (stable, raring) on my saucy install. It works fine, however I've noticed yet another undesirable change to Nautilus. When copying or moving files, if you hover the mouse over the destination folder, Nautilus automatically opens that folder. This is a real pain, because you lose the overview of the parent folder. Also, if the destination folder contains a lot of images or videos, Nautilus churns away displaying the previews of them. I understand that some people might find this feature useful, but it's yet another instance of the GNOME devs introducing a feature without providing any (obvious) way to opt out.

I also don't like the way that they've made the "systray" (or whatever the politically correct term for it is) even harder to access. If I'm not mistaken, previously it would appear immediately if you moved the mouse to the bottom right corner. Now it seems you have to hover the mouse there for what seems like an eternity, before it appears. For things that are accessed surprisingly frequently, this small delay has a big effect on my workflow.

I use Cinnamon on raring at work, and I'm probably going to switch to it at home too, as I simply find it more productive. Unfortunately though, the Cinnamon debs in the PPA don't work in conjunction with the GNOME 3.8 PPA (something to do with dbus JavaScript bindings).

TBH, my installs are probably starting to deviate so much from stock Ubuntu installs, that I'd probably be better off just running Mint and be done with it. Nemo file manager has some very smart features - including several features that Nautilus saw fit to remove. I've been using Ubuntu as my primary desktop OS since 2008, but lately I have become increasingly disillusioned with it.

---

### Post by Harry33 on 2013-05-13
> **sgage said:**
> Do you have any idea when 3.8 might enter the main repos? I did a fresh install of yesterday's daily of regular Ubuntu, and added Gnome Shell, and sure enough, it still doesn't work. I applied the gnome3 ppa, and it killed Unity. So I purged the ppa and downgraded libclutter and friends, so now I have both Unity and GS working well.

I wonder what killed Unity, exactly, from the newer Gnome Shell install. Maybe they're still getting it sorted before 3.8 is in the main repos...

I don't think anyone knows that ATM.
There are certain regressions compared to 3.6. 3.8 is just not yet ready.
The other problem is that it seems to be incompatible with Ubuntu's Unity. Certain parts of Gnome (like gdm) cannot be used with Unity.

---

### Post by sgage on 2013-05-13
> **Harry33 said:**
> I don't think anyone knows that ATM.
There are certain regressions compared to 3.6. 3.8 is just not yet ready.
The other problem is that it seems to be incompatible with Ubuntu's Unity. Certain parts of Gnome (like gdm) cannot be used with Unity.

That's kind of what I thought. Hard to believe that it's not even 3 weeks since Raring was released!

---

