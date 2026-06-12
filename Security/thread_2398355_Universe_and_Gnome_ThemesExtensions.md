---
title: "Universe and Gnome Themes/Extensions"
date: 2018-08-10
forum: Security
---

### Post by mborl on 2018-08-10
How safe are themes (those found in Universe repo) and packages such as gnome-tweaks and gnome-shell-extensions? I want to keep the data on my computer safe! Have there ever been reports of malware/spyware being found in the Universe repo?

---

### Post by DuckHook on 2018-08-14
Sorry it's taken so long to reply, mborl.

It is not possible to give absolute assurances in life. There are known instances of redirection attacks on Linux distros, which for the sake of diplomacy, I won't name here. In other words, nothing stops bad actors from using unpatched or zero-day exploits to carry out their dirty work. It's an unavoidable part of participating in the big, bad—but also glorious, amazing—info sphere that we live in.

Your question is not as simple as it sounds. For an answer that is at least partially informed, we need to get into the Ubuntu ecosystem a bit. Unlike commercial software, the Linux sphere is almost entirely open source. This means that for code to make it into the repos, it has to be open to easy scrutiny, at least by those who can read code. This requirement has the corollary benefit of making it very difficult, *but not impossible*, for rogue code to sneak into the repos. The Universe repo consists of code that is free but not maintained. This means that it won't be updated as the system gets updates: it is frozen in time at the moment that the devs released the finalized version of the OS to the world. However, everything within it is still subject to the community of eyeballs that make up the Linux ecosystem.

You will have to assess whether that community is sufficiently savvy to put your fears to rest. I am not aware of any malware that has made it past the Ubuntu devs in Universe, but I am aware of malware being found in one or two snap store packages earlier this year and, of course, if you install PPAs willy-nilly, then you are juggling live hand grenades and entirely the author of your own misery.

---

### Post by mborl on 2018-08-17
Thanks DuckHook! I appreciate your input. Using Linux is certainly different from Windows and OSX. I'm still getting a feel for the interesting connection between the community and the software

---

