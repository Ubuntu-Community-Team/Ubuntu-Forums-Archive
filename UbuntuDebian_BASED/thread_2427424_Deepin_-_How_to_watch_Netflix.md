---
title: "Deepin - How to watch Netflix?"
date: 2019-09-22
forum: Ubuntu/Debian BASED
---

### Post by javierdl on 2019-09-22
I normally use Mint, and watching streaming video from Netflix or Prime Video is not a problem. I am trying Deepin now, but getting this to work seems to be quite a challenge.
Browsers are telling me that the Widevine CDM is not active/present/installed/etc.
I looked for solutions for Chrome, but the problem is that these solutions assume that this component is already installed. Not for me. Yes I already checked the Chrome://components page and looked for Widevine Content Description Module.
I checked the Addons/Extensions available in the Google Store but there is no such a component available.
I also did a plane search for this module but didn't find it.

So far I have only found it in Firefox ESR.
I checkmarked "Play DRM Controlled Content" in Prefs, and in about:addons / Widevine Content Decryption Module provided by Google Inc, I have it as: Always Activate, then in its prefs for Automatic updates, it was on Default, I changed it to ON.
I closed it and opened it again and still no go.

The only one thing that has worked temporarily (Chrome) was this:

1. Select the Menu icon from the upper right corner of your browser.
2. Select Help.
3. Select About Google Chrome.
4. Chrome will display the current version and automatically install available updates.
5. Select Relaunch to complete the update.
Try Netflix again.
After logging back in, or rebooting, this solution was of no help anymore.

Chromium and Vivaldi were of no help either.

Then what?

If you have a solution using any browser I would love to hear it.

Thanks

---

### Post by howefield on 2019-09-22
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by hk42 on 2019-09-24
Hi
Apart from Firefox I only tried Opera and sure it doesn't work.
As I am short on storage space on this device I plan to remove Opera.

---

### Post by javierdl on 2019-09-24
Someone recommended [ElectronPlayer]("https://github.com/oscartbeaumont/ElectronPlayer"), an Electron Based Web Video Services Player. Supporting Netflix, Youtube, Twitch, Floatplane, Hulu And More. It's working great for Netflix. Too bad it doesn't support Prime Video. I am in Canada, so I cannot see Hulu :(
But yeah, at least I found a solution for Netflix.

JDL

---

### Post by javierdl on 2019-09-24
I got it working in Firefox!
I just removed some files so that Firefox would start anew. This way when I opened it after and went to Netflix, it told me it needed a plugin for the digital rights stuff, so I agreed for it to get it and install it. Once installed I was able to view the videos!
The following command line is for both Chrome and Firefox. I only wanted to do it for Firefox so I removed the command line parts for Chrome.

```
rm -rf ~/.config/google-chrome/ ~/.mozilla/firefox/ ~/.firefox-installed/ ~/.cache/mozilla/firefox ~/.cache/google-chrome/
```

---

### Post by wildmanne39 on 2019-09-24
Thanks for posting the solution, please use thread tools at the top of the forum to mark the thread solved.

---

