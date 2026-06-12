---
title: "VirtualBox components failing on upgrade to Karmic"
date: 2009-11-08
forum: Virtualisation
---

### Post by patman0623 on 2009-11-08
After upgrading my host machine from Jaunty to Karmic, VirtualBox had a version upgrade. However, the guest machine (WinXP) is no longer able to connect to the internet, and the sound is fuzzy: the sound was never funny on XP for me before, though I've run Fedora and had the same problems.

Anybody know what might be happening? I've checked to make sure I have the network adapters enabled for the guest machine.

---

### Post by noelvh on 2009-11-08
I would uninstall VB and reinstall form the VB's web site. You will have to manualy update the version going foreword but its worth it. Then make sure you have your gust addons installed. Also there should be 2 types of sound cards to use in VB so try and change them. I think I use sound blaster.

Noel

---

### Post by patman0623 on 2009-11-08
> **noelvh said:**
> I would uninstall VB and reinstall form the VB's web site. You will have to manualy update the version going foreword but its worth it. Then make sure you have your gust addons installed. Also there should be 2 types of sound cards to use in VB so try and change them. I think I use sound blaster.

NoelDoes an uninstall mean I would lose my virtual hard drive an installs?

---

### Post by noelvh on 2009-11-08
Nope. But you should back it up any ways.

Noel

---

### Post by patman0623 on 2009-11-08
Sadly, after an install of the new VirtualBox version, none of this seems to be working. I'm using the same audio adapter as before (alsa), and the internet is reporting "disconnected" (though it clearly is not, as you can see I am writing this post on said host machine).

This is very frustrating.
[B]
Additional note[/B]: after booting up, it's not connecting properly, but some how the RSS reader for BBC News on Firefox properly downloaded the latest news, which means *something* is getting through, but very little.

---

### Post by patman0623 on 2009-11-08
Could this (somehow) have something to do with me just enabling pipelining on Firefox on the host machine? The ping works on the guest, and after running a diagnostic, it's consistently reporting "connection reset"

---

