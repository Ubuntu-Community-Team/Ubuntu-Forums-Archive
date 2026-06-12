---
title: "Using gnome-power-manager with XFCE?"
date: 2012-11-17
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2012-11-17
I was attempting to get a little additional speed/memory on a low-end machine, so I installed the Xubuntu desktop packages on my CR-48.

Everything works great (after tweeking)... except one thing:  The XFCE power manager would not suspend the system when the lid is closed.

I read that there could be problems when you have both gnome-power-manager and XFCE's power manager running at the same time.  Since I don't want to remove gnome-power-manager (because I still want to be able to boot the Unity desktop and test too), I thought it would be best to just use the gnome power management with the XFCE desktop - so I removed the XFCE power management.

So far, no problems, except:  The Gnome power management icon doesn't show up in the indicator applet on the top panel (like my gnome sound and bluetooth icons do).

I've looked through dconf, gconf, and at the settings in gnome-control-center... but don't see anywhere to enable this.  Most of the documents online seem as if they're written for gnome2, as there aren't even really gnome-power-management and gnome-power-preferences binaries anymore (which makes me wonder if the gnome guys decided the art of unix programming was wrong and threw everything into one blob like with d/gconf).

Does anyone have any idea of where I could look to enable the gnome power icon under XFCE?

Thanks!

---

### Post by cariboo on 2012-11-17
I have the same problem on my Compaq netbook, it won't go into suspend when closing the lid, but will if it is manually selected from the user menu.

Have you created a bug report?

---

### Post by 3vi1 on 2012-11-17
> **cariboo907 said:**
> I have the same problem on my Compaq netbook, it won't go into suspend when closing the lid, but will if it is manually selected from the user menu.

Have you created a bug report?

No, I had guessed that the suspend issue was a known side effect of having the two power managers installed, based on some other posts I had found.  But, if I don't end up getting it to work without the XFCE power manager, it looks like that's my next probable step.

Do you have a ticket for your compaq that I can reference as being potentially the same issue?  Like yours, mine would suspend from the menu fine - just not via the settings/lid.

---

### Post by cariboo on 2012-11-17
> **3vi1 said:**
> No, I had guessed that the suspend issue was a known side effect of having the two power managers installed, based on some other posts I had found.  But, if I don't end up getting it to work without the XFCE power manager, it looks like that's my next probable step.

Do you have a ticket for your compaq that I can reference as being potentially the same issue?  Like yours, mine would suspend from the menu fine - just not via the settings/lid.

I just recently installed Xubuntu, and I'm still customizing/finding my way around, if you don't create a bug report, I will in the next day or two.

---

