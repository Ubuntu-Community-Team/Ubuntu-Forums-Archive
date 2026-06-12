---
title: "JACK server socket err"
date: 2012-01-07
forum: Ubuntu Studio
---

### Post by Robert Finley on 2012-01-07
Hardware= HP DL360 G4 / soundblaster card (don't laugh)
OS= Ubuntu 11.04 

I am trying to get Ubuntu set up for some audio production.  I have installed ubuntustudio through synaptic and added the lowlatency kernel, and edited my limits.conf to look like this: [http://pastebin.com/pZ5WxZ7U](http://pastebin.com/pZ5WxZ7U)

When I click on Applications/Sound & Video/Audio Production/QjackCtl the JACK Audio Connection Kit opens and any sound that was going on stops (Audacious was playing a song but seemed to just pause) and the Message window says:
[COLOR=#999999]
16:09:06.733 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]16:09:06.877 Statistics reset.[/COLOR]
 [COLOR=#cccc99]16:09:06.910 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]16:09:06.925 ALSA connection graph change.[/COLOR]

When I close JACK, Audacious picks right back up.  Can someone please tell what I need to do to get it functioning correctly?

---

### Post by jejeman on 2012-01-07
This is how you should set realtime support
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support)

---

### Post by Robert Finley on 2012-01-10
> **jejeman said:**
> This is how you should set realtime support
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support)


That is a really good jumping-off place to begin reading. Thank you.

---

