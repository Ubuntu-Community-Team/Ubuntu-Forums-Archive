---
title: "Firefox compiled with GStreamer support"
date: 2013-09-01
forum: The Cafe
---

### Post by Helkaluin on 2013-09-01
I thought I might share this with you: I've set up a PPA with Firefox (stable) builds with GStreamer support enabled.

What this means is that you can use the HTML5 video tags with all sorts of formats, including H.264.  This means if you turn on [HTML5 support in YouTube]("https://www.youtube.com/html5"), you'll be able to watch every video (except the ones with monetisation) without needing Flash.

Right now I'm only building for Raring because that's my platform now.  If people on Precise want it I'll find a way to do that.  I'll probably continue maintaining this on the latest Ubuntu release until the Ubuntu repositories ship a Firefox with GStreamer enabled by default.

Here it is: [https://launchpad.net/~helkaluin/+archive/firefox-gstreamer](https://launchpad.net/~helkaluin/+archive/firefox-gstreamer)

---

### Post by monkeybrain20122 on 2013-09-02
> **Helkaluin said:**
> I thought I might share this with you: I've set up a PPA with Firefox (stable) builds with GStreamer support enabled.

What this means is that you can use the HTML5 video tags with all sorts of formats, including H.264.  This means if you turn on [HTML5 support in YouTube]("https://www.youtube.com/html5"), you'll be able to watch every video (except the ones with monetisation) without needing Flash.



So only for Youtube? I never need flash for Youtube

[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

---

### Post by Helkaluin on 2013-09-02
> **monkeybrain20122 said:**
> So only for Youtube? I never need flash for Youtube

[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

The ViewTube script (along with all other 3rd-party userscripts like it) break every now and then when YouTube (and other video hosting sites) decides to changes its video embedding method.

Firefox compiled with GStreamer support enables Firefox to handle h.264 HTML5 videos out of the box without fear of 3rd-party scripts getting abandoned/not updated.  Whenever there's HTML5 video using WebM/Theora/H.264, this build of Firefox will support it: no need to ask the 3rd-party userscript authors to manually add support (and maintain the script) for another site.

Plus, the ViewTube userscript doesn't work with HTTPS-Everywhere.

---

### Post by pqwoerituytrueiwoq on 2013-09-02
Will the video run via my GPU (smplayer/vlc) or CPU (adobe flash)?
also when will you be switching to saucy (13.10)?

---

### Post by monkeybrain20122 on 2013-09-02
> **Helkaluin said:**
> The ViewTube script (along with all other 3rd-party userscripts like it) break every now and then when YouTube (and other video hosting sites) decides to changes its video embedding method.

True, but usually it gets updated very quickly.

> Firefox compiled with GStreamer support enables Firefox to handle h.264 HTML5 videos out of the box without fear of 3rd-party scripts getting abandoned/not updated.  Whenever there's HTML5 video using WebM/Theora/H.264, this build of Firefox will support it: no need to ask the 3rd-party userscript authors to manually add support (and maintain the script) for another site.


For which other websites does it work other than Youtube? the script(s) works for many sites and it seems that only Youtube breaks every now and then because of changes. The others don't change that often.

> Plus, the ViewTube userscript doesn't work with HTTPS-Everywhere.


It does, but you have to manually unblock it or use something like [https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/)


Advantage of script is that if use mplayer/mplayer2 as backend I get hardware decoding. Can't get that with html5 or flash.

---

### Post by Helkaluin on 2013-09-04
> **pqwoerituytrueiwoq said:**
> Will the video run via my GPU (smplayer/vlc) or CPU (adobe flash)? also when will you be switching to saucy (13.10)?  It uses the built-in GStreamer support to decode your videos.  As I remember GStreamer could utilise VA-API (and thus VDPAU indirectly) for hardware accelerated decoding.  As for Saucy, I'll switch after two to three weeks after it's released.

---

### Post by Helkaluin on 2013-09-04
> **monkeybrain20122 said:**
> True, but usually it gets updated very quickly. The point of this is that Firefox can support all H.264 HTML5 videos natively without relying on 3rd-party scripts.  > For which other websites does it work other than Youtube? the script(s) works for many sites and it seems that only Youtube breaks every now and then because of changes. The others don't change that often. It works for whatever websites that implement HTML5 videos.  > It does, but you have to manually unblock it or use something like [https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/) So it's the mixed content block that they implemented recently?  Thanks!  Editing about:config now.  > Advantage of script is that if use mplayer/mplayer2 as backend I get hardware decoding. Can't get that with html5 or flash. Technically, if Firefox is now using GStreamer for HTML5 videos, then it should be able to leverage VA-API (and thus VDPAU indirectly) for hardware acceleration: [https://gitorious.org/vaapi/gstreamer-vaapi/source/0a4582de6fa43f9f7fbfedf595e8c390f045f43f:](https://gitorious.org/vaapi/gstreamer-vaapi/source/0a4582de6fa43f9f7fbfedf595e8c390f045f43f:) [https://wiki.archlinux.org/index.php/VA-API#GStreamer](https://wiki.archlinux.org/index.php/VA-API#GStreamer)  I don't know if Ubuntu ships with a GStreamer compiled with VA-API acceleration support, though.

---

