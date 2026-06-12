---
title: "Vbox, rdesktop, and hotkeys"
date: 2014-01-11
forum: Virtualisation
---

### Post by JKyleOKC on 2014-01-11
I've got a perplexing problem and havn't been able to find any discussion of it by searching, both here and via Google. Hopefully I'm not the only person to have encountered it...

I use vrdp and rdesktop, daily, to access my email VM from any station on my LAN. I also use it often to access other VMs, and except for this one problem it seems to fill all my needs.

One application I must handle every 90 days requires intensive use of Microsoft Word and Microsoft Publisher, which run in a dedicated VM under WinXP. I've automated large parts of this task (publication of a 40-page magazine for a non-profit organization) using macros, with hotkeys to launch them. This works perfectly when I'm at the host station of that VM, but I like to use a different station that has a larger monitor and thus is easier on my aging eyes and 20/80 vision. And on that other station, while the mouse and keyboard work properly, the hotkeys for the two Office applications don't work at all.

I've investigated both the -k and -K options to rdesktop, and they have no effect on the problem. Using -K does switch window-manager hotkeys from the remote guest to the local host -- and those hotkeys DO work remotely as expected if I omit the -K option from rdesktop. However no other hotkeys seem to make it through the remote connection. It appears that the CTRL and ALT keystrokes are being trapped out, rather than forwarded to the remote.

Is this a problem that can be solved, and if so, how? My WM is XFCE, and I'm running Xubuntu 12.04.4 with all updates applied. I'm not averse to doing some deep digging if necessary, but at this point I don't even know where to start looking...

---

### Post by JKyleOKC on 2014-01-15
Bump, anyone? There **has** to be a solution, even if it requires rebuilding a few things!

---

