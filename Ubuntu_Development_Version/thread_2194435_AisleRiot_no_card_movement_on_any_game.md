---
title: "AisleRiot: no card movement on any game"
date: 2013-12-18
forum: Ubuntu Development Version
---

### Post by VMC on 2013-12-18
[Bug report]("https://bugs.launchpad.net/ubuntu/+source/aisleriot/+bug/1260795")

Maybe someone that has installed Aisleriot can confirm the following. On any game, when you click on a card. The card itself will not move. Only the card it can go to will become darken.

Its hard to describe unless you just play a game, any game.

Make sure *'Control > Click to Move*' is off

Edit: This issue is on any Ubuntu 14.04 distro. AisleRiot version 3.10.1

---

### Post by grahammechanical on 2013-12-18
With Control>Click to Move unticked - Left click and hold on the card to be moved. When the pointer is moved the card disappears. Move the pointer over the target card and the target card goes grey. Release the left click button and the card being moved re-appears sitting on the target card.

That is how it works for me. A bug or a design feature? How would we know? Double clicking a card to move on to the stack of cards sitting on an Ace, still works as it should.

Regards.

---

### Post by mc4man on 2013-12-18
The game itself works fine here in either mode. If in the past you saw the card while moving then possibly the new behavior is from gtk-3.10
(objects aren't  shown when moving/dragging , only cursor/hand, whatever.

---

### Post by VMC on 2013-12-18
For me that's a design flaw. Seeing the card move is what happened in the past. I don't see how the current "blind" move is a design feature.
Hopefully someone will confirm my bug report,  to at least see a developers response.

---

### Post by mc4man on 2013-12-18
> **VMC said:**
> For me that's a design flaw. Seeing the card move is what happened in the past. I don't see how the current "blind" move is a design feature.
Hopefully someone will confirm my bug report,  to at least see a developers response.

You should see the same now in nautilus, DnD no longer shows the icon of file during the drag. This started with gtk-3.10
(I think it's actually better in nautilus not to show the icon for various reasons.

Will confirm your bug though possibly this is an intended change in gtk (never really pursed checking...

---

### Post by VMC on 2013-12-18
I don't think its **AisleRiot** causing this. I purged ver 3.10 and installed ver 3.8. Same results. Then I tried Saucy 13.10 distro, using both versions. The cards move. Something with Trusty 14.04 that prevents seeing the cards moving. 

So did gtk-3.10 first start with Trusty? If not , then something else is the problem.

Edit: According to [this Gnome link]("https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00052.html") , 13.10 was released in September. Past Trusty release. So that must be the problem. I don't think the maintainers of AisleRiot had any knowledge of this.

---

### Post by PJs Ronin on 2013-12-18
I agree with VMC.   This 'new' attribute detracts from what I'm trying to do in the game.

Added a 'me too' to your bug.

---

### Post by VMC on 2013-12-18
Thanks mc4man and PJ for the support and useful info.

---

### Post by mc4man on 2013-12-18
put up a report here, see what shakes out
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1262427](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1262427)

(see the same with nemo which uses gtk3, not with pcmanfm which is gtk2

---

### Post by cariboo on 2013-12-18
I added my me too, to both bug reports.

---

### Post by cecilpierce on 2013-12-19
I don't like the new mod either, have two Manjaro's installed here and one has sound and one don't ??? Weird...:(

---

### Post by mc4man on 2013-12-19
take this as you may
[https://bugzilla.gnome.org/show_bug.cgi?id=720750](https://bugzilla.gnome.org/show_bug.cgi?id=720750)

---

### Post by VMC on 2013-12-19
> **mc4man said:**
> take this as you may
[https://bugzilla.gnome.org/show_bug.cgi?id=720750](https://bugzilla.gnome.org/show_bug.cgi?id=720750)
Thanks for the info, but how do I make the cards [COLOR=#333333]window native?[/COLOR]

---

### Post by mc4man on 2013-12-19
For the moment until 14.04 gets the workarounded package one could install from here directly (download & install, no need to add ppa
[https://launchpad.net/~gnome3-team/+archive/gnome3-staging/+packages](https://launchpad.net/~gnome3-team/+archive/gnome3-staging/+packages)

---

### Post by VMC on 2013-12-19
Thanks for the update. Got it!

---

