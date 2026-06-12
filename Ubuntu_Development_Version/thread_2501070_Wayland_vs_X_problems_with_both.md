---
title: "Wayland vs X: problems with both"
date: 2024-09-21
forum: Ubuntu Development Version
---

### Post by mcellius on 2024-09-21
I'm trying the Oracular beta, upgraded from 24.04.  I am using Nvidia graphics. Everything feels very slow, especially to open.

On Wayland I can't even open Nautilus.  I get a circular icon to indicate something is trying to run, then it just goes away.  And overall, almost everything opens very slowly, including the Gnome terminal.

On X I can open Nautilus, after it thinks about it, but although I have chosen dark mode, the first time it opens Nautilus is all in light mode.  If I close it and reopen it, it comes up in dark mode.  However, lots of other windows open with the title bar light: Soliaire, Firefox, GParted, Software & Updates, gufw, and many others.

Most of these things seem like Gnome problems, which definitely doesn't seem at all ready.

---

### Post by mcellius on 2024-09-21
Wayland still won't let me open Nautilus. I was able to fix X by choosing the Nvidia driver 535. I guess I'll stick to X.

---

### Post by jbinpg on 2024-09-21
My video is an Nvidia 1660 ti. After upgrade to 24.10, I noticed it had chosen to load the 535 driver. I could only get anything to open on the desktop in the X session. Almost nothing in Wayland would open. Eventually, even the X session started being wonky. Then I switched to the 550 open driver and now Wayland works slowly but everything opens fine. Probably has something to do with loading a proper gl environment?

---

### Post by vhaarr+launchpad on 2024-09-23
In wayland on a machine with Intel Arc GPU, the whole desktop often seizes up completely, for example if I open two evince windows with PDFs and fullscreen them on different monitors.

In X11 on an nvidia 3080 GPU, nautilus crashes all the time, like every time I use it. Every day it crashes. Or, locks up so I have to kill the process.

And obviously wayland on nvidia-560 is a complete trainwreck.

I've used linux and gnome daily since - if I remember correctly - 1999/2000. They only focus on redesigning apps and removing features like for example the ability to email a PDF from the evince menu.

Nautilus changes so much each release it's complete insanity. Moving the copy/move progress stuff around for no reason.

I'm close to giving up on Gnome entirely. After 25 years or so.

---

### Post by mcellius on 2024-09-28
Now the Nvidia 550 is working great on Wayland: everything works and it is very stable.  Whatever they fixed, it's working.  I need to reboot and see how X is doing.

Of course, it's still a beta - so as of Thursday the Extension Manager is no longer working.  On three different computers, it opens a blank window with nothing in it so it can't be used.  I'm hoping in a few days they'll provide a fix for it, too.

Edit: Well, that was quick!  I mentioned that the Gnome Extension Manager wasn't working, and an hour later a fix was issued and it's working again!  Great!

---

