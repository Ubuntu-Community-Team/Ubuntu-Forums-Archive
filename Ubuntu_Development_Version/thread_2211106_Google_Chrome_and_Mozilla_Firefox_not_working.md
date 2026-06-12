---
title: "Google Chrome and Mozilla Firefox not working"
date: 2014-03-14
forum: Ubuntu Development Version
---

### Post by bela83 on 2014-03-14
Hi !

I have this strange problem since a couple of days : Chrome and Firefox can't open. Chromium still can. I think the problem for the two browsers is related since they failed to start at the same time, after an upgrade (can't remember what this was though).

When trying to start at the command line, segmentation fault :
```
k9n6sgm-v:~$ google-chrome-stable 
Erreur de segmentation (core dumped)

k9n6sgm-v:~$ firefox 

(process:10749): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "overlay-scrollbar"
Erreur de segmentation (core dumped)
```

I tried to reinstall, whith no success.

Thanks for any tip !

---

### Post by lonniehenry-gmail on 2014-03-14
I am getting that message [COLOR=#000000][FONT=Ubuntu Mono]g_slice_set_config: assertion 'sys_page_size == 0' failed when I do upgrades in synaptic.  I had problems running chrome and found chromium would work.  I installed chrome dev version and it works. chrome stable and chrome unstable don't.  Using 14.04 Gnome-shell version of ubuntu.[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-03-14
There is a bug report and another thread with links about this at [http://ubuntuforums.org/showthread.php?t=2208264](http://ubuntuforums.org/showthread.php?t=2208264)

I don't think there is a proper solution yet, though there are some workarounds.

---

### Post by bela83 on 2014-03-14
Thank you very much ajgreeny !

It's good to have the link to the bug on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062").

---

