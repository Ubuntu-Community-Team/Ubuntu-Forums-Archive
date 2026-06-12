---
title: "Broken USB Audio playback in Chromium/Firefox"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tim1 on 2012-02-08
One of the last updates broke audio playback in web browsers.

I have chosen my USB audio device in the sound settings but only Totem, Banshee etc. use it, Firefox and Chromium play sound through my Notebook speakers which sound horrible of course.

I tried to downgrade the last pulseaudio update but this didn't fix it.

Bug report here: [https://bugs.launchpad.net/bugs/928790](https://bugs.launchpad.net/bugs/928790)

Suggestions?

---

### Post by cariboo on 2012-02-08
From the ubuntu-devel mailing list:

> On Wed, Feb 08, 2012 at 07:16:51PM EST, Luke Yelavich wrote:
> Hey folks,
> Just a heads up that I am in the process of getting ALSA 1.0.25 into precise. I am checking as thoroughly as I can to make sure I don't break anything, but if you find your audio is broken in the coming days, please let me know, particularly ARM folks.
In light of being reminded about our need for testing, I have put alsa-utils v1.0.25 into the Ubuntu Audio Dev PPA for precise, [https://launchpad.net/~ubuntu-audio-dev/+archive](https://launchpad.net/~ubuntu-audio-dev/+archive). Alsa-lib is already in precise since I jumped the gun a bit, so any issues you find can be filed in launchpad against alsa-lib. Please test alsa-utils, and file a bug in launchpad with your issue, noting the version of alsa-utils in the description.

Thanks

Luke

---

### Post by portis on 2012-02-08
I found a workaround from ubuntu-devel mailing list:

create /etc/asound.conf:

pcm.pulse {
     type pulse
}

ctl.pulse {
     type pulse
}

pcm.!default {
     type pulse
}

ctl.!default {
     type pulse
}

Then restart the browser.

Thanks Palo and Pete.

---

