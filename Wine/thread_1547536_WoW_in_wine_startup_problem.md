---
title: "WoW in wine startup problem"
date: 2010-08-06
forum: Wine
---

### Post by KnightGrinder on 2010-08-06
Every time I try to play WoW this happens
[IMG]http://i36.tinypic.com/2i09gt4.png[/IMG]

I have ubuntu 10.04 and wine 1.2 that has all default settings and windows version set to XP.
Please help

---

### Post by asdfoo on 2010-08-06
> **KnightGrinder said:**
> Every time I try to play WoW this happens
[IMG]http://i36.tinypic.com/2i09gt4.png[/IMG]

I have ubuntu 10.04 and wine 1.2 that has all default settings and windows version set to XP.
Please help

Looks like a problem with your video drivers.

Which video card do you have?  If it's ATI, you should try updating to catalyst 10.7.  If nvidia then there are 256.xx drivers available.

---

### Post by KnightGrinder on 2010-08-06
> **asdfoo said:**
> Looks like a problem with your video drivers.

Which video card do you have?  If it's ATI, you should try updating to catalyst 10.7.  If nvidia then there are 256.xx drivers available.

How do i upadate to catalysy 10.7?

---

### Post by cwwilson721 on 2010-08-06
In addition to the above:

[LIST]
[*]What version of wine?
[*]Do you have Compiz enabled?
[*]Are you using opengl (Either '-opengl' appended at end of command, or in the WTF file)?
[/LIST]

---

### Post by KnightGrinder on 2010-08-06
1. wine 1.2
2. what is Compiz?
3. I'm using directx

---

### Post by asdfoo on 2010-08-07
> **KnightGrinder said:**
> How do i upadate to catalysy 10.7?

Not related to this subforum.

---

### Post by cwwilson721 on 2010-08-07
> **KnightGrinder said:**
> 1. wine 1.2
2. what is Compiz?
3. I'm using directxYour main issues are #2 and #3
Compiz is the 'wow, gee-whiz' effects on your desktop, like expanding windows, wobbly windows, rotating cube desktops, etc. Compiz should be disabled by:

[LIST]
[*]Installing compiz-fusion-icon then running it (It installs to  Applications > System Tools)
[*]rt click on the icon in the tray after it starts, and select the "Metacity" windows decoration
[*]Reload the desktop manager (also by rt clicking the icon)
[/LIST]
After compiz is disabled, you need to run WoW with the 'opengl' option (I just append this to the end of the command to launch WoW, which I copied to the panel by rt clicking on it in the Wine menu, and selecting "Add to panel", then rt-click for Properties) or you could add the appropriate "opengl" line in WTF, which is explained NUMEROUS times in this forum.

Not sure if it will help, but wine 1.3 is available. 'sudo apt-get install wine1.3'

---

### Post by KnightGrinder on 2010-08-07
It's working now, it was a driver issue.
Thank you for the help.

---

