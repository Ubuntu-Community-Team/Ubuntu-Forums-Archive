---
title: "Can't Alt+Tab in Ubuntu Gnome Classic"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ubuntu27 on 2012-04-06
Do any of you experience this?

I can't use window switcher (Alt+Tab) in Ubuntu Gnome Classic with effects.
It simply does not respond to anything.

---

### Post by Darxus on 2012-04-06
> **ubuntu27 said:**
> Do any of you experience this?

I can't use window switcher (Alt+Tab) in Ubuntu Gnome Classic with effects.
It simply does not respond to anything.

Yup, I just loaded up gnome classic for the first time in this ubuntu precise install, and noticed alt-tab isn't working.  Found this post first looking to see if others were seeing the same thing.

---

### Post by mc4man on 2012-04-06
The reason it doesn't work is likely because it's not enabled by default in the "Default' profile.

While in Classic(compiz) open ccsm & enable
You may get better results with the static app switcher ('better' being better than crap

---

### Post by ubuntu27 on 2012-04-06
> **mc4man said:**
> The reason it doesn't work is likely because it's not enabled by default in the "Default' profile.


Is it a "feature" or a bug?

---

### Post by mc4man on 2012-04-06
More like 'Classic' is low on the totem-pole, don't think much effort is expended in testing how it works ootb

---

### Post by ubuntu27 on 2012-04-06
Found a bug report: [SIZE="3"][COLOR="Red"][Bug#971051]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/971051")[/COLOR][/SIZE]

Please subscribe. :guitar:

---

### Post by Darxus on 2012-04-06
Opened a bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/975701](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/975701)

Not certain compiz is the thing to report it against.

---

### Post by mc4man on 2012-04-06
Have you guys tried enabling it & using?, does work here (the static one

---

### Post by ubuntu27 on 2012-04-07
> **mc4man said:**
> Have you guys tried enabling it & using?, does work here (the static one

CCSM keeps crashing on me, so I can't test that.

But, this is definitely a bug or a regression, seen that we always had this ability. IMHO if this is "fixed" by enabling it in CCSM, then it should be enabled by default.


[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/971051](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/971051)

---

### Post by mc4man on 2012-04-07
If ccsm is crashing then you may not be able to use anyway (yourself

Seems reasonable that 'staticswitcher' be enabled in Classic(effects) by default, maybe they will

You could try enabling thru gconf-editor, if so do it _while in the Classic (effects) session_

You'd go /apps/compiz-1/general/screen0/options  & double click on the active_plugins  key. That will open an edit box, add there. (staticswitcher), screen after adding

---

