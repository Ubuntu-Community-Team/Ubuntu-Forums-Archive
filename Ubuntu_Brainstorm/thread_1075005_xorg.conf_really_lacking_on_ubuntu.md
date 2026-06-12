---
title: "xorg.conf really lacking on ubuntu"
date: 2009-02-19
forum: Ubuntu Brainstorm
---

### Post by NinjaWork on 2009-02-19
I am using a Dell and my xorg.conf was totally generic. I had to copy one from the Slack USB distro (Slax) for all things like Intel drivers, etc.

---

### Post by smartboyathome on 2009-02-20
The new Xorg tries to guess as much as possible. It has been like this since 8.04, and they said they aren't going to change it. It is a pain, I know, but it was their decision.

---

### Post by NinjaWork on 2009-02-20
thanks for your reply.

I had my computer very blurry for a few months and I loved Slax since it was so clear.

Finally I figured out I needed to copy the xorg.conf from Slax.

I do love using Ubuntu, but this font and resolution stuff is a major problem...especially doing things like coding all day on the desktop.

---

### Post by glotz on 2009-02-20
Font rendering, eh? Fire up gconf-editor and point it to /desktop/gnome/font_rendering and try different combos for antialiasing and hinting.

---

### Post by lithorus on 2009-02-20
> **NinjaWork said:**
> thanks for your reply.

I had my computer very blurry for a few months and I loved Slax since it was so clear.

Finally I figured out I needed to copy the xorg.conf from Slax.

I do love using Ubuntu, but this font and resolution stuff is a major problem...especially doing things like coding all day on the desktop.

It's probably down to the DPI setting which you can also set in the Fonts settings.

---

### Post by markbuntu on 2009-03-09
This is not really a Ubuntu issue, it is an Xorg decision. We are lucky there is any xorg.conf at all as Xorg has already deprecated it in favor of automatic detection and moving configuration options to the drivers. Do not expect to see an xorg.conf in future versions.

---

