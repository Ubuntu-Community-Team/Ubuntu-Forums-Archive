---
title: "Curious how you install certain software on non-popular distros.."
date: 2008-05-25
forum: The Cafe
---

### Post by Exershio on 2008-05-25
For example, ATI FGLRX drivers are not open source (as far as I know). To install them, you need to generate a package with the .run file, but it only supports a certain number of distros.

How do you install a piece of software like that on a less popular distro, or even something like Gentoo, where you need to install it from source?

---

### Post by LaRoza on 2008-05-26
> **Exershio said:**
> For example, ATI FGLRX drivers are not open source (as far as I know). To install them, you need to generate a package with the .run file, but it only supports a certain number of distros.

How do you install a piece of software like that on a less popular distro, or even something like Gentoo, where you need to install it from source?

Just because Gentoo typically installs from source, it doesn't mean it always has to. Likewise, just because Ubuntu uses .deb packages most of the time, it doesn't mean you can't install from source.

---

### Post by MaindotC on 2008-05-26
I've not worked w/ Gentoo or Slax but can't you just install a packinag system on them?  I mean if you don't have one, you'd have to get it from some type of physical media (you can't yum yum), but couldn't you do that?

I didn't know the .run command was only on certain distros.  What package is the .run?

---

### Post by Exershio on 2008-05-26
what I meant is with ATI's drivers, you do "sh blahblah.run --buildpkg Ubuntu/8.04" or something like that, but --buildpkg only supports a certain amount of distros. How would you install something like that on a distro not listed via --listpkg ?

---

### Post by MaindotC on 2008-05-26
Yeah, I know how .run files are installed.  What do you do --buildpkg for?  I just do the sh or double-click it in nautilus.

---

### Post by FuturePilot on 2008-05-26
AFAIK .run files can be executed on any distro. I don't think you absolutely *have* to make a deb out of ATI's driver. I would think you could just run it. But I've never installed that driver before so I could be wrong. But Nvidia also releases their drivers in a .run format and you can just simply execute them.

---

