---
title: "Merge System76 Driver with upstream kernel and HAL"
date: 2007-12-08
forum: System76 Support
---

### Post by DRM_free on 2007-12-08
Why doesn't System76 merge the patches in the System76 driver (intel hda sound driver, acpi buttons, etc) into kernel.org and HAL? I would have expected everything to work out of the box in Ubuntu Gutsy, but instead I still have to download the System76 drivers and compile a patched alsa. Not to mention the fact that other distros like OpenSuse or Fedora don't work either, and running the System76 driver on those is problematic.

---

### Post by palintheus on 2007-12-08
BIG +1, I have always wondered why System76 didn't push their fixes upstream, seems it would help them out in the long run and help the community.

---

### Post by greg_g on 2007-12-08
I'm a +1 on this also.  I mean, it can only help Sys76 in the end:

"Hey, see those 20 things we fixed so that anyone using GNU/Linux on those laptop models is better off?  Cool right?  Oh, by the way, we sell computers too, want one?"

---

### Post by pavel_987 on 2007-12-08
+1 here

Although I see how it could be problematic. If the patches are applied upstream then people are still going to have to wait for the new version of hal / the kernel to be released. Then wait for it to come to stable ubuntu.

Plus you'd never really get rid of the driver. Because it also delivers hardware specific updates like, in my case, DSDT tables.

Not knowing how things function at System76, I at least hope that they're doing something. Assuming the previous poster is correct, it would be awesome if the snd hda intel was pushed upstream. But I don't know too much about that. It seems the laptop that I bought didn't have any custom coding but more of special configurations.

---

### Post by thomasaaron on 2007-12-10
Actually, we work closely with Canonical on a number of issues and have pushed several fixes upstream.

Many of our fixes are already available to everyone in the Ubuntu community (often via the repositories). We just do the research and apply those fixes to our specific models via the driver. Don't forget, too, that the driver is open source and there for anybody to peek under the hood.

Wnen we do develop a groundbreaking fix, though, it definitely goes upstream.

That said, we also share what we've learned with folks who neither use System76 computers -or- Ubuntu whenever we are able. (Unfortunately we just don't have the bandwidth to master other manufacturer's computers and other OS's, but we do what we can.)

---

### Post by DRM_free on 2007-12-10
> have pushed several fixes upstream
That's great, but why not do this it for all your fixes? Thinning out all the quirks that are in the System76 driver will make it more manageable **for you** too. Seriously, it takes like **2 minutes** to shoot an email to the maintainers.

For example: Send the special key codes for the laptop keys to HAL like these people did:

[Keymap: Acer: Add more Aspire, Extensa and TravelMate laptops]("http://lists.freedesktop.org/archives/hal/2007-November/009941.html")
[[PATCH] Add Acer Aspire 1300 keymap]("http://lists.freedesktop.org/archives/hal/2007-December/010146.html")
[keymap: Acer TravelMate 6292 query]("http://lists.freedesktop.org/archives/hal/2007-December/010285.html")

As for the ALSA driver, just open up a bug report in the [ALSA bugtracker]("https://bugtrack.alsa-project.org") and attach the patch as-is. The ALSA devs will take care of integrating it into the official ALSA tree, and you can then remove it from the Sytem76 driver. One less quirk for you to worry about.
> 
we also share what we've learned with folks who neither use System76 computers
It's not about helping other hardware sellers -- it's about **forward-compatibility** and peace of mind. It's about helping **your own customers** be able to upgrade to a newer Ubuntu that "just works" out of the box.

---

