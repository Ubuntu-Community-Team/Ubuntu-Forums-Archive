---
title: "Many problems after installation"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by emt_1 on 2012-03-09
Hi,having terrible time finding way to report bug.IRC won't log, in no mention of it anywhere.My first install of Alpha 1 had it ,but got fixed in updates,now back in beta 1.Can't right click at all anywhere,panel and dash disapear and desktop freezes.Can't keep doing these hard restarts.Any help appreciated.AMD64 12.04 beta1.Happens in windows on desktop,panel.dash,terminal,

---

### Post by cariboo on 2012-03-09
Moved to a thread of it's own, as there are too many different things that won't work reported, including the desktop itself.

---

### Post by grahammechanical on 2012-03-09
I am using a fresh install of Beta 1 and it has something called Apport installed. This little utility is very good at detecting things going wrong even before they become noticeable. It usually invites me to submit a bug report. Often it will tell me that the bug has already been reported but that I can add more information if I want to. Then it will open Launchpad in the browser for me.

Are you using Unity? Have you installed a different user interface? Have you removed stuff? This is the kind of thing that causes Compiz or Unity  to crash. In fact are you using the Compiz Configuration Settings Manager to activate certain effects? Some of those effects will most definitely cause the desktop to crash.

Try logging in as Ubuntu 2D and removing the Compiz effects that have been activated.

sometimes logging out and back in sets things up again.

Regards.

---

