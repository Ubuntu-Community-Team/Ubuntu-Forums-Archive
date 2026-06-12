---
title: "Totem gets unresponsive windows often"
date: 2012-12-02
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-12-02
At least so here & on a live session.
Seem mainly by using the playlist though can happen at any time.
(may try an new install later as this one is a bit aged.

At least here removing the pulseaudio plugin improves but doesn't 100% solve
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342)
( the app menu is not currently available in an ubuntu session unless totem is started with an env of UBUNTU_MENUPROXY=0

---

### Post by VinDSL on 2012-12-02
I cannot duplicate your "unresponsive windows" problem, but...

I opened Totem, made a playlist, and danced on them back n' forth for 2-3 minutes -- nothing, no probs, responded just fine.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-dec-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-dec-2012-3.png")[/INDENT]


If you'll notice, I also have Banshee steaming audio, at the same time.  Neither player hiccuped once.

I left them both running, while I prepared this post, and danced on the Totem playlist even more, for good measure.

Only thing I'm seeing are a few odd warnings in CLI...

```
totvindsl@Zuul:~$ totem

<SNIPPED $#@! fontconfig warning>

(totem:23127): Clutter-Gst-WARNING **: Failed to convert non-scaled coordinates for video-sink

(totem:23127): Cogl-WARNING **: Over 50 separate fragment shaders have been generated which is very unusual, **[COLOR="Red"]so something is probably wrong![/COLOR]**

(totem:23127): Cogl-WARNING **: Over 50 separate programs have been generated which is very unusual, **[COLOR="Red"]so something is probably wrong![/COLOR]**

```

Sooo, "something is probably wrong!"  LoL!  :D

But, everything is remaining responsive, here. Sorry!

Okay, I'm going to turn off one of these players now, before I go mad!  :guitar:

---

### Post by Edward D. on 2012-12-04
Yeah, totem has been hanging very frequently in my Raring installation.  For maybe a few weeks now, even.  I haven't filed a bug yet, but came looking now to see if anyone else had problems.  So thanks.

(edit: I'm sleepy and read right past your bug link.  I'm subscribed to it now.)

---

### Post by VinDSL on 2012-12-04
Hrm...

Well, I tried Totem again, tonight, and it won't play jack!

Dead as a toenail.  LoL! :D

I'll add a "me too" to your bug report...

---

### Post by kansasnoob on 2012-12-04
Totem now depends on OpenGL and so far it's a total fail.

I wouldn't be surprised to see Ubuntu choose to change default video players.

Off-topic, but what do you think Ubuntu will do with Nautilus?

---

### Post by dino99 on 2012-12-04
i'm getting that error logged after opening a gnome-classic session on RR i386:

** (nautilus:3297): WARNING **: /usr/lib/nautilus/extensions-3.0/libtotem-properties-page.so: undefined symbol: bacon_video_widget_get_type

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1086300](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1086300)

---

### Post by VinDSL on 2012-12-04
OMG!!!

I'll tell you what...

Ever since Totem failed, last night, this machine is running like grunt!

Everything is unresponsive -- all windows -- no kidding!

Network-manager, Banshee, Chromium, Compiz plugins -- everything...

WoW!  Just WoW!  LoL!  :D

---

### Post by dino99 on 2012-12-04
you seems testing over the limit that agp card :( its a miracle to still get it on board  :P

---

### Post by VinDSL on 2012-12-04
> **kansasnoob said:**
> Off-topic, but what do you think Ubuntu will do with Nautilus?
I've been forcing myself to use Nautilus, since we're supposed to be testing.

I'm actually starting to like it, but...

I cannot get past their removal of the "extra pane" feature. Tabs are not a suitable replacement, IMO.

All the other stuff, I can live without.

They can dress it up all they want, but the missing pane gives Nautilus a missing tooth, black-eye, bloody nose, or whatever.

If I was Canonical, I'd reinstate the pane, and call it a day...

---

### Post by VinDSL on 2012-12-04
> **dino99 said:**
> you seems testing over the limit that agp card :( its a miracle to still get it on board  :P
Truth!

I'm searching for a new mobo, right now.

I got a [Seasonic Gold-certified 750W PSU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817151087") (Quad 6P/8P PCI-E connectors), at the Egg, on "Black Friday", blah, blah, blah.  So, I'm starting to collect parts for my new monster.

But, it's more than that!  It's like everything is freezing up, and unresponsive.

Totem must have flagged something, somewhere.  It's dragging my whole machine down, waiting to do something.  It's not just a video problem.

I've looked for zombies, but I can't detect anything.

This is truly a weird one!  ;)

---

### Post by VinDSL on 2012-12-06
**[COLOR="Sienna"]UPDATE[/COLOR]**

Thought I should leave an update...

The unresponsiveness on this machine had nothing to do with Totem.

Turned out to be a bad border router between Phoenix and LA. Heh!

---

