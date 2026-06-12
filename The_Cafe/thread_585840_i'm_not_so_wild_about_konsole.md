---
title: "i'm not so wild about konsole"
date: 2007-10-21
forum: The Cafe
---

### Post by fuscia on 2007-10-21
i installed kubuntu gutsy and i'm loving it (was thinking about sidux). there are a couple of things i could do without (amarok, kaffeine, kontact, adept), but there's a lot i really like (konqueror, k3b, kmplayer, kstreamripper, kdegames, etc.). lately, i've noticed things i don't like about konsole. one thing that irritates me is the restricted number of fonts it uses (what's up with that?), so i've been using urxvt (which i love) instead. i was able to add it to my panel with all my little arguments (no scrollbar, tinted just the right shade and whichever damn font i want). trouble is, i haven't figured out how to add it to the right-click menu with all my special instru...hey, wait a minute! if i add it to the regular menu, i can add it that way. we'll see..

anyway, fire away on konsole. maybe i'm missing it's finer qualities.

---

### Post by -grubby on 2007-10-21
I thought they were all more or less pretty much the same....I guess not

---

### Post by fuscia on 2007-10-21
> **nathangrubb said:**
> I thought they were all more or less pretty much the same....I guess not

i'll bet you think all aspirin's alike.

---

### Post by Dark Aspect on 2007-10-21
> **fuscia said:**
> i'll bet you think all aspirin's alike.
I for one do think all aspirin's alike.........

lol

---

### Post by picpak on 2007-10-21
What bugs me most about konsole is that I can only choose between light transparency and dark transparency. No refinement at all.

---

### Post by fuscia on 2007-10-21
> **picpak said:**
> What bugs me most about konsole is that I can only choose between light transparency and dark transparency. No refinement at all.

you can actually alter those in 'configure konsole' and save them as different schemes. seems a bit too many steps for something that should be simple. xfce4-terminal handles that the best, in my experience.

---

### Post by igknighted on 2007-10-21
> **picpak said:**
> What bugs me most about konsole is that I can only choose between light transparency and dark transparency. No refinement at all.

You sure can adjust the transparency, look at the screenie attached

---

### Post by RAV TUX on 2007-10-21
Konsole works fine for me but I haven't experimented much beyond Konsole, what are all the options?

---

### Post by p_quarles on 2007-10-21
> **picpak said:**
> What bugs me most about konsole is that I can only choose between light transparency and dark transparency. No refinement at all.
Nonsense. You can choose both the opacity level and the color to which it shades. Relevant screenshot attached.

The fonts *are* limited, though. Doesn't bother me at all, since I like my terminal to look like a terminal, but it's a fair complaint.

[EDIT]: Igknighted simul-posted the exact same point, and the same screen.

Response to fuscia: Look closely at the screenshot(s), and I'll believe you'll notice both a slider and a palette.[/EDIT]

---

### Post by fuscia on 2007-10-21
it's still a lot more trouble than it should be. what's wrong with having a slider and a palette? this schema crap is the worst thing about konsole, for me. maybe the kde development team should turn dolphin into a terminal emulator.

---

### Post by Ireclan on 2007-10-21
I, like nathangrubb, thought they were all pretty much alike. The only reason I avoid Konsole is that it has this annoying bug where, if you try to set two different backgrounds- one for normal users and one for root- it makes it to where whenever you invoke Konsole, it always wants your root password. This is on PC-BSD, though. Not sure if Linux Konsole has the bug.

---

### Post by fuscia on 2007-10-21
> **RAV TUX said:**
> Konsole works fine for me but I haven't experimented much beyond Konsole, what are all the options?

gnome terminal, xfce-terminal, rxvt, rxvt-unicode, eterm (if you want whacky), a-term and a bunch of others. mrxvt, if you need tabs...etc.

---

### Post by RAV TUX on 2007-10-21
> **fuscia said:**
> gnome terminal, xfce-terminal, rxvt, rxvt-unicode, eterm (if you want whacky), a-term and a bunch of others. mrxvt, if you need tabs...etc.

[Enterminus]("http://www0.get-e.org/Resources/Applications/System/Enterminus/") looks cool perhaps I will try this.

---

### Post by picpak on 2007-10-22
> **igknighted said:**
> You sure can adjust the transparency, look at the screenie attached

Ok, so I can't move my eyes to the right. :rolleyes:

I still don't like the whole thing about schemes though.

---

### Post by fuscia on 2007-10-22
> **picpak said:**
> Ok, so I can't move my eyes to the right. :rolleyes:

I still don't like the whole thing about schemes though.

i agree. i'm done with it. i've got urxvt in my kde right-click menu, all's right with the world.

---

### Post by whit on 2007-10-25
> **fuscia said:**
> rxvtI'm a long-time rxvt user. I put a button in the Panel something like: rxvt -rv -sr -g 150x50 (or whatever geometry, and perhaps specify a font). 

It works fine on many Linuxes, including KDE on Gentoo. But KDE on Kubuntu has a mismatch in terminal codes that ends up not present all text highlighting and special characters correctly, messing up some of the screens. What's the most direct route to rectifying that?

What I like about rxvt is it's light-weight, thus fast. And I don't want tabs. I'd rather just have a few independent terminal sessions over a few desktops.

---

### Post by whit on 2007-10-25
> **fuscia said:**
> urxvtWhat package is urxvt in?

---

### Post by fuscia on 2007-10-25
> **whit said:**
> What package is urxvt in?

*sudo apt-get install rxvt-unicode*

*urxvt* to run it. [http://linux.die.net/man/1/urxvt](http://linux.die.net/man/1/urxvt)

---

