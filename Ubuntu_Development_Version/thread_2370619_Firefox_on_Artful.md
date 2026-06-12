---
title: "Firefox on Artful"
date: 2017-09-05
forum: Ubuntu Development Version
---

### Post by amano on 2017-09-05
I wonder, when Firefox and Thunderbird will be updated to the current (or future?) versions....


Out of personal interest (bit off topic, I know):

Did someone try those experimental Wayland+CSD flatpaks?: [https://firefox-flatpak.mojefedora.cz/](https://firefox-flatpak.mojefedora.cz/)

For me those will NOT install, I can fetch and install the GNOME 2.24 core files and it seems that it can fetch Firefox as well. But then it will error out without any useful error (something like "further input is necessary").

I tried it on Zesty, I tried it on Artful and I tried the recommended Flatpak PPA provided in the How-To above. Always the same error :(

---

### Post by Frogs Hair on 2017-09-05
I'm running 56 from the next PPA, but there will be a new process for add-ons in the very near future. Even with 56 some add-ons are already marked legacy and won't work. This may have something to do with the delay.

[https://support.mozilla.org/en-US/kb/firefox-add-technology-modernizing?as=u&utm_source=inproduct](https://support.mozilla.org/en-US/kb/firefox-add-technology-modernizing?as=u&utm_source=inproduct)

---

### Post by amano on 2017-09-05
Yeah, but that is a "normal" Firefox without Wayland support and client side decorations.

In theory it should work, I was just wondering if some other "Ubuntero" got this working and I was just stupid...


I love Firefox and I think the whole idea behind it brought me to Linux. About 12 or 13 years ago - still on Windows!! - I was compiling nightly builds on the mozillazine forums. And tinkered with the XUL files to make them use the german translations from the last official version :)  Sooo many years since then.

---

### Post by vasa1 on 2017-09-05
> **amano said:**
> ...
I love Firefox and I think the whole idea behind it brought me to Linux. About 12 or 13 years ago - still on Windows!! - I was compiling nightly builds on the mozillazine forums. And tinkered with the XUL files to make them use the german translations from the last official version :)  Sooo many years since then.
Then you may like to run Firefox Nightly instead of waiting for Canonical builds. I'm sure Mozilla would like some telemetry data from someone using Fx57 on Wayland: [https://download.mozilla.org/?product=firefox-nightly-latest-ssl&os=linux64&lang=en-US](https://download.mozilla.org/?product=firefox-nightly-latest-ssl&os=linux64&lang=en-US)

I installed it in my home folder and get updates (directly) twice in 24h. I haven't turned on any of the privacy measures so they can get an idea of my usage in terms of browser settings, etc.

---

### Post by acheronuk on 2017-09-06
> **amano said:**
> I wonder, when Firefox and Thunderbird will be updated to the current (or future?) versions....

There is a discussion on the ubuntu-devel mailing list about why it is not getting updated (build failures on some architectures, so uploads stuck in -proposed pocket), and what can be done about it.

[https://lists.ubuntu.com/archives/ubuntu-devel/2017-September/thread.html](https://lists.ubuntu.com/archives/ubuntu-devel/2017-September/thread.html)

Thread "Old Firefox versions discourage real-world testing of Ubuntu development versions"

---

