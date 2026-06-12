---
title: "Clock to 24hs format; cannot change in Gnome classic"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by spsf on 2012-03-25
Topic says it all...
Anyone else with same problem? Or solution?
TIA

---

### Post by dino99 on 2012-03-25
i'm on gnome-classic too and can change it as i like :)

right-click on time, select "adjust time & date" then select either the checkbox "24h" or "pm"

---

### Post by spsf on 2012-03-25
> **dino99 said:**
> i'm on gnome-classic too and can change it as i like :)

right-click on time, select "adjust time & date" then select either the checkbox "24h" or "pm"

I think you are not using the standard "Indicator Applet Complete"... Can you confirm this?
It works only if I add to panel the "old" clock 
Thanks

---

### Post by dino99 on 2012-03-25
> **spsf said:**
> I think you are not using the standard "Indicator Applet Complete"... Can you confirm this?
It works only if I add to panel the "old" clock 
Thanks

hm, the package is installed, but it might be the old applet in the toolbar; i've not payed much attention to this setting as it give me what i like.

---

### Post by spsf on 2012-03-25
> **dino99 said:**
> i'm on gnome-classic too and can change it as i like :)

right-click on time, select "adjust time & date" then select either the checkbox "24h" or "pm"

Just another note, for me if I use "adjust time & date", it wont work; I have to go this way:

"right-click on time, select preferences, then 24 hour format"

Anyway, I filled a bug report...

---

### Post by dino99 on 2012-03-25
is it a fresh install ? because mine does not have "24h" into preferences (explaining that im using the old applet i suppose)

let us know about the report number please.

---

### Post by spsf on 2012-03-25
> **dino99 said:**
> is it a fresh install ? because mine does not have "24h" into preferences (explaining that im using the old applet i suppose)
Its 3 day old install, from daily live, preferences are from the old clock applet, in general tab, i got these options 12 or 24 hs format.
In the "new" applet (Indicator Applet Complete) I have to Left click on it to go into its options

---

### Post by tista on 2012-03-25
Guys,

I suppose he talked about "Clock Applet" on stock gnome-panel's applets...

If so, 

1. Kick "gconf-editor".
2. Follow "/ -> apps -> panel3-applets -> clock".
3. Set "format" value to "24-hour" from "12-hour".

Regards,
Tista.

---

### Post by jbicha on 2012-03-25
Yes, this is a bug. In GNOME Classic or GNOME Shell, only GNOME's "Date and Time" panel is shown; in Unity, "Time & Date" is shown which controls the clock indicator. Here's some workarounds:


[LIST=1]
[*]XDG_CURRENT_DESKTOP=Unity gnome-control-center indicator-datetime
[*]Or use dconf-editor (install dconf-tools) and edit the options in com.canonical.indicator.datetime
[*]Or just run Unity long enough to change the clock settings.
[/LIST]

---

