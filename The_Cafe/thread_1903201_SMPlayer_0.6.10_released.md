---
title: "SMPlayer 0.6.10 released"
date: 2012-01-01
forum: The Cafe
---

### Post by rvm4000 on 2012-01-01
**Version 0.6.10.**

**Most important changes since 0.6.9:**
[list]

[*] New vdpau configuration dialog, which allow to select the vdpau codecs to use.

[*] Port for eCS, OS/2 (by Silvan Scherrer).

[*] New menu to select the closed caption channel (requires mplayer >= r32607).

[*] Possibility to select the seeking method (absolute or relative).

[*] Possibility to sort the items of the playlist.[/list]

This version doesn't have many new features, but I prefer to release it now as new features planned for the future will (probably) require a more recent version of Qt.

To install it:
```

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer

```

Packages for older versions of ubuntu are also available:
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

---

### Post by sisco311 on 2012-01-01
Not a support question. Moved to **The Community Cafe**.

---

### Post by inobe on 2012-01-01
thank you.

---

### Post by andrew.46 on 2012-01-03
Excellent news RVM, I am rushing to download this new version :)

---

### Post by doorknob60 on 2012-01-03
Cool, this is my preferred media player, it's very good. I used to use VLC but mplayer has much better VDPAU support, so I use this now, no complaints with it. I even occasionally use it in Windows (though I rarely need Windows). Latest version is already in the Arch repos too :)

---

### Post by rvm4000 on 2012-01-31
SMPlayer 0.7.0 released

[list]

[*] New favorite menu, where you can add your favorite videos, music, streams, youtube videos... It's also possible to add submenus.
[*] Support for youtube. Now you can open urls like [http://www.youtube.com/watch?v=](http://www.youtube.com/watch?v=)..... using the Open -> URL dialog or dragging a link from a browser to the smplayer window.
[*] Support for mplayer2 ([http://www.mplayer2.org](http://www.mplayer2.org)). It's a fork of mplayer with interesting features like precise seeking, ordered chapters in mkv videos and better pause handling (e.g. seek works while the video is paused).
[*] New translation: croatian.[/list]

---

