---
title: "Yet Another Wireless issue (PanP5)"
date: 2011-05-27
forum: System76 Support
---

### Post by HotShotDJ on 2011-05-27
I'm having trouble with dropped connections with both my PanP5 (Intel 5300 wireless card) and my friend's Star1 (I don't know the wireless card).  The PanP5 is currently running OpenSuSE 11.4 with Gnome 3 while the Starling is running Ubuntu 10.10 with fully updated Gnome 2.  I know that System76 doesn't support distributions other than Ubuntu, but since it was happening for me with Natty on the PanP5 as well (although not as severe) I suspect my issue isn't distro-specific.

On the PanP5, the problem is so severe, that I simply can't use my laptop wireless in my house.  The only thing that gets the wireless back to working is switching the hardware off and then back on (via Fn+F11).  Then the wireless will work for awhile, but eventually dies.

I suspect a hardware issue... either the wifi card or the router. I'm going to pack up my PanP5 and visit some local Wifi hotspots to see if I can rule out the router as being the issue (Belkin N+).  If I have trouble elsewhere, I'll need instructions for replacing the card (perhaps with a Intel 6000 series?).

UPDATE:  Here I sit at Borders.  Same trouble here.  I need to switch off and then back on the wireless card before I can get a connection.  Eventually it dies just like at home.  So far, I've done the switch off/on thing twice to keep connected.  Grrrrrrr.......

UPDATE2: No problems at Starbucks, even though a very weak signal.  I'm now home and have set my router to a & g only.  No longer having connection issues (so far).  I'm stumped.  Driver? Gnome 3's implementation of nm-gnome?  I did read that there are some issues with the driver (which is where I got the idea to disable N mode).  Any thoughts from System76 would be greatly appreciated.

UPDATE3: Ok, definitely the driver. When I update the driver using the compat-wireless + updated iwlwifi-5000-ucode from intel, the problem goes away... BUT, I break bluetooth.  I suspect a kernel upgrade will take care of the issue, but could cause other problems.  *sigh*

---

### Post by HotShotDJ on 2011-05-28
After much searching of bug reports, listserv's, forums, etc., the best I can come up with is that the 5000 series of Intel's wifi cards has had driver issues across several Linux distributions for quite some time, despite Intel's best efforts.  It seems to work just fine when I disable "N" but gets terribly flaky with "N" enabled.  Ok... such is life.

Before I mark this "thread" as "Solved," I just have one question: Can the Wifi card in the PanP5 be upgraded to an Intel 6000 series card?  If so, will upgrading break Bluetooth?  Recommendations from System79 tech support would be greatly appreciated.

(Oh, a recommendation to return to Ubuntu will be considered after Canonical abandons Unity)

UPDATE:  Switching from OpenSuSE 11.4 to OpenSuSE Tumbleweed fixed things up for me.  I'm still interested in upgrading the Wifi card, since this is something I shouldn't have had to do... but something I CAN live with.

UPDATE2: NEVERMIND.  All is well. No need to upgrade the Wifi card. Getting good results with updated Kernel.  Must have just been a hiccup in the OpenSuSE development cycle.  Sorry for the spam thread.  Move along, nothing to see here. :)

---

