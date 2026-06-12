---
title: "Bug confirmation request: Chromium-browser &quot;Incognito Mode&quot; - Segfault"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-30
Hi everyone. This consistently causes a segfault here, as of today's updates:

- Install chromium-browser if you don't already have it.
- Close all Chromium-Browser instanced (if any is opened)
- Add chromium-browser (drag it) to the Unity Launcher.
- Right click the launcher icon. Select "Open a new window in Incognito Mode"
- Crash.

chromium-browse[24584]: segfault at 108 ip 00007ff8ce0469d5 sp 00007fffe2e90340 error 4 in chromium-browser[7ff8cd9f9000+3ca8000]

Left-clicking the launcher icon opens a Chromium-Browser instance normally.

If you confirm this, please +1 and add any details to [_**[COLOR=Red]Bug #969487[/COLOR]**_]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/969487") 

Thanks,
Effenberg

---

### Post by cariboo on 2012-03-30
It works OK here, I'm using it now to post this.

---

### Post by kaldor on 2012-03-30
Everything working as expected on my end.

---

### Post by Abandon on 2012-03-30
No problem here. Try deleting (or renaming) your .config/chromium map.

---

### Post by ubuntu27 on 2012-03-30
> **effenberg0x0 said:**
> Hi everyone. This consistently causes a segfault here, as of today's updates:

- Install chromium-browser if you don't already have it.
- Close all Chromium-Browser instanced (if any is opened)
- Add chromium-browser (drag it) to the Unity Launcher.
- Right click the launcher icon. Select "Open a new window in Incognito Mode"
- Crash.

chromium-browse[24584]: segfault at 108 ip 00007ff8ce0469d5 sp 00007fffe2e90340 error 4 in chromium-browser[7ff8cd9f9000+3ca8000]

Left-clicking the launcher icon opens a Chromium-Browser instance normally.

If you confirm this, please +1 and add any details to [_**[COLOR=Red]Bug #969487[/COLOR]**_]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/969487") 

Thanks,
Effenberg

I can confirm this. If I open Chromium with "Open a new Secret Window" [That's how it says in Japanese], it crashes.


Terminal output:

(exe:8003): Gtk-WARNING **: module_path &#12395;&#12399;&#12486;&#12540;&#12510;&#12539;&#12456;&#12531;&#12472;&#12531;&#12364;&#12354;&#12426;&#12414;&#12379;&#12435;: "pixmap",

(exe:8003): Gtk-WARNING **: module_path &#12395;&#12399;&#12486;&#12540;&#12510;&#12539;&#12456;&#12531;&#12472;&#12531;&#12364;&#12354;&#12426;&#12414;&#12379;&#12435;: "pixmap",
Segmentation fault (&#12467;&#12450;&#12480;&#12531;&#12503;)


My rough Translation:

(exe:8003): Gtk-WARNING **: There is no Theme Engine in module_path: "pixmap",

(exe:8003): Gtk-WARNING **: There is no Theme Engine in module_path: "pixmap",
Segmentation fault (Core Dump)



@effenberg0x0: The link to the launchpad bug report is not working. It says, "Lost something? This page does not exist, or you may not have permission to see it. "


Perhaps the bug report is marked as private.

---

### Post by effenberg0x0 on 2012-03-30
> **ubuntu27 said:**
> I can confirm this. If I open Chromium with "Open a new Secret Window" [That's how it says in Japanese], it crashes.


Terminal output:

(exe:8003): Gtk-WARNING **: module_path &#12395;&#12399;&#12486;&#12540;&#12510;&#12539;&#12456;&#12531;&#12472;&#12531;&#12364;&#12354;&#12426;&#12414;&#12379;&#12435;: "pixmap",

(exe:8003): Gtk-WARNING **: module_path &#12395;&#12399;&#12486;&#12540;&#12510;&#12539;&#12456;&#12531;&#12472;&#12531;&#12364;&#12354;&#12426;&#12414;&#12379;&#12435;: "pixmap",
Segmentation fault (&#12467;&#12450;&#12480;&#12531;&#12503;)


My rough Translation:

(exe:8003): Gtk-WARNING **: There is no Theme Engine in module_path: "pixmap",

(exe:8003): Gtk-WARNING **: There is no Theme Engine in module_path: "pixmap",
Segmentation fault (Core Dump)



@effenberg0x0: The link to the launchpad bug report is not working. It says, "Lost something? This page does not exist, or you may not have permission to see it. "


Perhaps the bug report is marked as private.

Ubuntu27, yes, I see now that Launchpad or triaging made it private/security :\
I have checked two more PCs. Same problem (on Fresh Install plus full update/upgrade).

Regards,
Effenberg

---

### Post by larrypg on 2012-03-30
mine did the more or less the same with the crash messege of chromium-browser has crashed with SIGSEGV in get addrinfo()

---

### Post by effenberg0x0 on 2012-03-30
I have removed the "private" tag, so others can +1 on it.

Thanks,
Effenberg

---

### Post by ubuntu27 on 2012-03-30
> **effenberg0x0 said:**
> I have removed the "private" tag, so others can +1 on it.

Thanks,
Effenberg

All right. I added myself. :)


On a almost unrelated topic, can someone confirm [this bug report]("http://ubuntuforums.org/showthread.php?t=1949620")?

---

### Post by brainwash on 2012-04-01
This issue has been already reported here:
[http://code.google.com/p/chromium/issues/detail?id=113950](http://code.google.com/p/chromium/issues/detail?id=113950)

Scroll down to **comment #13** to read more about what is causing the segfault.

Chromium 17.0.963.83 Ubuntu 12.04

---

