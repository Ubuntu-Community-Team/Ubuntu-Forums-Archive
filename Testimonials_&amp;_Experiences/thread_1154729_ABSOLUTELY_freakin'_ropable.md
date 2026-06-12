---
title: "ABSOLUTELY freakin' ropable"
date: 2009-05-10
forum: Testimonials &amp; Experiences
---

### Post by 3rdalbum on 2009-05-10
I've been an Ubuntu user since 2005 and I run it single-boot on all my machines.

I recently upgraded to Jaunty, which went really well. It killed suspend support on my desktop, but then I understand that reverse-engineered drivers (and the proprietary Nvidia driver) can be unpredictable in how they bring the machine back from suspend. That doesn't bother me.

What *does* bother me is that support for my MP3 player has been broken again! This is a *run of the mill* Sony Walkman MP3 player; in Gutsy and Intrepid you plugged it in and it appeared on the desktop as a USB mass storage device. You drag music or videos to it, and that's all there is to it. In fact, one of the two main selling points of the Walkman is that it is drag and drop, and that you don't need any external software to use it!

In Hardy, somebody got a little too clever and decided that this MP3 player should be supported with MTP rather than UMS; and no way of switching it back. Unfortunately MTP actually wouldn't mount the device anyway, so users had to manually mount. The problem affected a number of other MP3 players. This was pretty bad and was not fixed until Intrepid. The fix for Intrepid was to use UMS for those devices again, which worked fine.

Now, in Jaunty, the player is automatically handled by MTP again! ONCE AGAIN the MTP code is broken; the device appears on the desktop this time, but when you open it there are no files. You can load music on with Rhythmbox via its MTP plugin, but you can't access any non-music files stored on it. You can't load videos or photos.

When I realised that this was happening, I looked in gconf-editor to see if I could tell Gnome to handle the device as UMS again. Nada - there's no gconf key for that. The workaround is to edit a configuration file for Gvfs, which doesn't seem to work for everyone, and incredibly the bug report on Launchpad claims that the bug is "fixed"!

The bug affects a large range of MP3 players that Linux users have traditionally bought, for instance certain Sansa models! These are players that require ABSOLUTELY NO reverse-engineering as they can use the standard mass storage driver.

My questions are:
1. Who on earth is making these changes to the system, when everything was working before, and when the person obviously doesn't own a non-Apple MP3 player?!
2. Why doesn't Gnome provide a gconf key so the user can choose whether to treat devices as UMS or as MTP?
3. Why is MTP being treated as the preferred protocol for media transfer? It's a Microsoft protocol!
4. I just donated $50 to Gnome. How can I get a refund so I can donate it to KDE, which never introduced the problem? (just kidding, I don't want to take back my donation).

I love my Walkman, and I love Linux, but the fact that somebody keeps stuffing up my player for seemingly no reason at all, really makes me want to throw a cricket ball through my window. After breaking support for Walkmans last year, you would have thought that everyone would have learnt not to stuff around with MTP for players that don't require it.

I also feel bad because I recommended Walkmans to Linux users during the Gutsy days, and then again during the Intrepid days.

**Anyone who develops a proper fix for the Walkmans and all other affected MP3 players, and gets it pushed out to Jaunty users, gets $100 AUD put into their Paypal account now, and another $100 AUD in a year's time if Walkmans still work properly with Ubuntu 9.10 and 10.04.**

---

