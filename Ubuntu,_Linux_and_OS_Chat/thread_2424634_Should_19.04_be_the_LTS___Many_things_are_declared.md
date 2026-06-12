---
title: "Should 19.04 be the LTS?   Many things are declared &quot;won't be fixed&quot; on 18.04"
date: 2019-08-12
forum: Ubuntu, Linux and OS Chat
---

### Post by BFG on 2019-08-12
I usually only run LTS versions, but I've hit quite a few speed-bumps on 18.04 and have been quite surprised that many prominent software packages are deploying fixes to 19.04 only, and not adding fixes to 18.04.
*Full disclosure: All my data is on a NAS and so I'm resistant to sandboxes. So this is mostly apt related. * 

I imagine it's a kernel issue, but it still poses quite a problem.  I find myself using debs and adding 3rd party repos more with 18.04 than with any other release.

Bluetooth, gnome apps like gimp, flatpak - all have a number of workarounds to get working in 18.04.

E.g.
GIMP version in the 18.04 repo is 2.8., with several things broken.  When I finally had no workaround for cage transform tool error, I dug deep and found that I couldn't rely on the canonical repo.
Fixes are in latest version and Gimp approach to get 2.10 is either use flatpak or compile (though it is in snap - if you only save files locally).

flatpak is a somewhat ironic example, being an alternative to apt I'd imagine they want to give apt users the best opportunity to experience flatpak, but there's only a very old v1.0.8 in the 18.04 repo, and only when you visit [https://flatpak.org/setup/Ubuntu/](https://flatpak.org/setup/Ubuntu/) do you find that adding a 3rd party repo gives the latest 1.4.2.  But you'd never actually ever get to know about this unless you went deeper into flatpak docs, which probably only happens when something has already gone wrong ;)

Flatpak are maintaining in 18.10 onwards only: [https://flatpak.org/setup/Ubuntu/](https://flatpak.org/setup/Ubuntu/)  

E.g. Bluetooth / Bluez is broken in 18.04, with no apparent appetite to backport the fix. Add repo to workaround
[https://askubuntu.com/questions/1036195/bluetooth-doesnt-work-after-resuming-from-sleep-ubuntu-18-04-lts](https://askubuntu.com/questions/1036195/bluetooth-doesnt-work-after-resuming-from-sleep-ubuntu-18-04-lts)


I haven't kept a list, but I'd say I've stumbled across at least 8-10 apt packages recently which are not being fixed in 18.04, only later versions. 

Which sort of breaks the LTS concept for me.  Thoughts?

---

### Post by cruzer001 on 2019-08-12
You seem to have hit on hard times.  Gimp is the only flatpak I have and zero snaps.  I do experience random window crashes, but I'm pretty sure I built that in.  Bluetooth required blueman for it to work on mine, just maybe they will get it right in 20.04, the next LTS.  

You could open up the developer repositories, bet those apt updates are there.

---

### Post by cruzer001 on 2019-08-12
Well I take that back.  Pre-release has only 48 updates, nothing about apt.

---

### Post by QIII on 2019-08-12
Unless the changes are deemed to be security updates, there is no guarantee software changes will appear in the main repo after an OS release.  Possible, but unlikely.

You can count on the Canonical main repo to contain packages for software versions available at the time of the OS release or security updates.  That's a long-standing policy.

---

### Post by irv on 2019-08-12
This might not be the way to do this, but I installed 19.04 on all my computers except my sound system, and plan to install 20.04 when it comes out. I just keep a list of programs I use and do a quick install on all of them. To go from one release to another (clean install) it takes me about 30 minutes. I keep all my data in the cloud and external drive for backups. This works great for me. I wish 19.04 was an LTS but, as I said in am going to 20.04 anyway.

---

### Post by ajgreeny on 2019-08-12
There may be some PPA repos for your packages for which you want , or need, the latest versions.  For example I use PPAs for Libreoffice-6.2.5 and Gimp-2-10-12, both of which I find stable and very much worthwhile using.

I have no snaps at all and currently an appimage for Musescore-3.2.3 which is a great deal newer and better than the standard repository version, though I have just noticed that there is a PPA for Musescore as well with that same 3.2.3 version which I'm about to try.

---

### Post by mastablasta on 2019-08-13
snap "replaces" apt, flatpack is from Redhat.

the version stay the same. while new version might fix your problem they are not just fix version but also feature upgrades which may break someone else version. stable means that packages are kept on same versions and only security fixes are applied. this is also what is meant under support.

if you need newer version you can introduce instability to the OS by adding a PPA or use a snap which sandboxes the application and thus preserves the stability of the OS while providing you with new app version.

---

