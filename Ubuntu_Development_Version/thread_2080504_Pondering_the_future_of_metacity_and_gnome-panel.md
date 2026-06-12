---
title: "Pondering the future of metacity and gnome-panel"
date: 2012-11-04
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2012-11-04
After reading [Stinger's thread]("http://ubuntuforums.org/showthread.php?t=2080263") I posted a note here:

[http://ubuntuforums.org/showpost.php?p=12336188&postcount=91](http://ubuntuforums.org/showpost.php?p=12336188&postcount=91)

But in hindsight I decided that conversation more properly belongs here :)

Just read on the [ubuntu-desktop mailing list]("https://lists.ubuntu.com/archives/ubuntu-desktop/2012-October/004018.html"):

> Seb, I blame the remix idea on you. ;) Anyway, if the GNOME remix
becomes an official flavor, I was hoping to then ask for permission to
include the GNOME3 PPA due to our unique overlap with the flagship
Ubuntu release. It's still a bit of a handicap as I don't think we
could gain that trust if we included things that regressed Unity.

If we don't fork ubuntu-control-center and ubuntu-settings-daemon off
from gnome-control-center, then I don't believe it will be possible to
ship GNOME Shell 3.7/3.8 next cycle. The last two cycles we've shipped
the latest GNOME Shell but with bugs due to incomplete g-c-c/g-s-d
support in Ubuntu (for 12.04 it was [http://pad.lv/965921](http://pad.lv/965921) with keyboard
shortcuts not able to be configured from System Settings and for 12.10
it was 1045914 with a missing keyboard layout status menu). [B]It's a
reasonable guess that for 3.8, the GNOME developers will move
aggressively to kill fallback mode[/B] and make optimizations and GNOME
Shell will depend on those newer optimizations.

A big reason for the GNOME remix is to show that you can contribute to
GNOME from Ubuntu. I worry about what happens when most users are
using a different distro than most developers. Shipping an outdated
GNOME means that we have a much less compelling story to tell these
developers.

So once the UDS dust settles I'll ask Jeremy if that means metacity and gnome-panel will be dropped altogether.

Edit: I found this after a bit of googling:

[http://worldofgnome.org/gnome-3-8-fallback-mode-the-first-feature-under-discussion/](http://worldofgnome.org/gnome-3-8-fallback-mode-the-first-feature-under-discussion/)

In one of the later comments Jeremy says:

> 

He means **if you don't have working 3D, then Totem won't work**.

Now that we have llvmpipe, it doesn't seem like GNOME needs a "fallback mode" for when GNOME Shell won't work. **[COLOR="Red"]I think gnome-panel should be allowed to continue as GNOME Classic instead of as GNOME Fallback.[/COLOR]** In other words, getting rid of some of the patches that made it look like GNOME Shell even though most of its users would prefer it look like a polished GNOME 2 desktop.

It sounds like there is also a need for developers to continue updating the code to keep it on par with the latest GTK3 and GNOME 3 code. This is the project the Mate developers should have taken on.


I definitely agree with that sentiment.

I personally hope that plain old metacity survives because I find "classic (no effects)" to run just as efficiently as Lubuntu on lower-end hardware, but it's not a huge deal.

And I've come to really like the new gnome-panel, it "just works" :)

---

### Post by ibjsb4 on 2012-11-04
But running 12o4, so its got at least 5 year life span with me.

In future releases, if its done away with; we will just have to build it in  :)

---

### Post by kansasnoob on 2012-11-04
> **ibjsb4 said:**
> But running 12o4, so its got at least 5 year life span with me.

In future releases, if its done away with; we will just have to build it in  :)

In deed, that's why I wrote this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I just wish I could still properly edit it :(

---

### Post by ibjsb4 on 2012-11-04
> **kansasnoob said:**
> In deed, that's why I wrote this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I just wish I could still properly edit it :(

I thought you already turned that thread into a Wiki.

---

### Post by kansasnoob on 2012-11-04
> **ibjsb4 said:**
> I thought you already turned that thread into a Wiki.

Someone else did that ............ I can't wiki :(

The new forum rules make it much harder to share tweaks and such.

---

### Post by kansasnoob on 2012-11-04
In fact, how hard is that to find in a google search?

How do you find the wiki for Ubuntu Precise Classic (no effects)?

Regardless **that goes far off-topic from the intent of this thread** .............. maybe we could ask that a discussion be allowed here:

[http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48)

But I suspect that would be a futile effort :(

---

### Post by ibjsb4 on 2012-11-04
> **kansasnoob said:**
> The new forum rules make it much harder to share tweaks and such.

I am not aware of these rules.

Your thread has not been closed; it can still be edited.  Unless the changes are just to massive and a fresh start is better.

---

### Post by kansasnoob on 2012-11-04
> **ibjsb4 said:**
> I am not aware of these rules.

Your thread has not been closed; it can still be edited.  Unless the changes are just to massive and a fresh start is better.

You're wrong! Posts can no longer be edited after one week!

I'd have to ask a forum mod to edit it for me.

---

### Post by kansasnoob on 2012-11-04
I'm going to ask one of the mods to remove all of these off-topic posts. This has nothing to do with 12.04, only 13.04 and onward :)

---

### Post by ibjsb4 on 2012-11-04
> **kansasnoob said:**
> You're wrong! Posts can no longer be edited after one week!

**[SIZE=3]OK![/SIZE]**[SIZE=3][SIZE=2]  :)  Must be one of those new rules your talking about.[/SIZE][/SIZE]

Ill leave you with this thought.  If you come up with any brainy ideas how two old guys can change the world back to Classic, Im in.  PM me  :)

---

### Post by ronacc on 2012-11-04
make that 3 old guys:P

---

### Post by cariboo on 2012-11-04
Closed by request.

---

