---
title: "Empathy Talk !"
date: 2010-05-08
forum: The Cafe
---

### Post by alket on 2010-05-08
I was happy with pidgin, but pidgin unblocked all my deleted and blocked contacts, so from Lucid Lynx I'm using Empathy because it doesn't unblock and is more integrated, here is my issue:

1. It doesn't have File Sharing with MSN contacts.
2. It doesn't open new conversations in bottom panel (Windows List) but in that green envelope and for that reason sometimes i don't notice it.

3. It doesn't have Display Pictures in Chat Windows, I know that this is not important but it looks so oldish.

4. When i write longer text (specially in IRC rooms) it resizes it self and when i write even longer it start something "shaking-like".

5. It doesn't have plugins (there were great ones with pidgin).

6. It doesn't have text modification so I cant resize text so It's hard to read.


If you have any solutions of those problems above, please reply.

---

### Post by Mr. Picklesworth on 2010-05-08
The answer to #4 is that Empathy doesn't have a plugin interface per se, but it has a very different architecture from Pidgin. Empathy is actually a very very tiny application that plugs in to a system of services called Telepathy. All your different IM accounts work through separate processes that provide services through Telepathy, then there's a switchboard sort of thing called Mission Control that sets status and all that stuff.

It's theoretically possible to use any buddy list / chat application you want (where Empathy is one such choice, and currently the only one I know of) and since they all plug in to Telepathy you can do so very very easily.

The other cool thing here is that other applications can plug in to that service to achieve wonderful things. Those wonderful things haven't really landed in a shipping desktop yet, but for example some day you'll be able to pull open Nibbles from the Games menu and, from there, get a list of friends in your buddy list and play with them.
(Don't worry, by that date, [bug #1]("https://bugs.edge.launchpad.net/ubuntu/+bug/1") will also be solved).

It's a distinctly different direction; in most IM clients, everything happens from the client. In Telepathy and Empathy, everything is separate. The latter is a more robust approach, but does take a long time to happen.


For #3, that's really a design thing (and I like it, though I'm a bit weird). However, you can change the theme it uses for chat messages. Head to Edit&#8250;Preferences&#8250;Themes from the buddy list, and change the Chat Theme to Ubuntu. That theme shows each message as a colourful bubble with the sender's display picture.


As for the rest&#8230; well, you've described some known bugs / wishlist items :)

You can subscribe to them to keep up on their status. Hopefully they'll be fixed soon. Note that a lot of these are in Launchpad and filed upstream. You can find the upstream report at the top, or under &#8220;Remote bug watches&#8221; on the right column:

#1: This is a telepathy-butterfly thing. Nearly there. (I suspect this thing will be awesome in a few months; webcam support looked pretty encouraging for a while, too). [Freedesktop.org bug #22507]("http://bugs.freedesktop.org/show_bug.cgi?id=22507")

#2: The Ubuntu people want this fixed, but the Empathy people just don't agree with it for some reason. [Launchpad bug #206547]("https://bugs.edge.launchpad.net/ubuntu/+source/empathy/+bug/206547")

#4: The text size problem haunts me, too. You can work around it by hitting Shift+Enter to force a new line, and from then on your text box will wrap properly with the current window size. It's reported in [Launchpad bug #433651]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/433651")

#6: The chat font should really inherit from your desktop-wide application font set in Appearance Preferences, but, alas, it doesn't do that. [Launchpad bug #504711]("https://bugs.edge.launchpad.net/empathy/+bug/504771")

---

### Post by TheNessus on 2010-05-08
you can remove the indicator's chat package, and thus have Empathy work in the Notification Area applet instead of the Indicator applet (no envelope, but an icon, like Pidgin uses). but this also removes the microblogging and evolution stuff in your indicator app. (bloat anyway, I say)

---

