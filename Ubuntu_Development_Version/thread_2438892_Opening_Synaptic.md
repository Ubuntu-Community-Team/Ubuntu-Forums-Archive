---
title: "Opening Synaptic"
date: 2020-03-19
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2020-03-19
I was unable to open synaptic from the icon after updates yesterday . Using sudo -H synaptic works fine, but the password entree box won't open. I have seen the same on wayland , but there is no wayland session on U Budgie. Is this happening on Ubuntu?

---

### Post by uRock on 2020-03-19
Howdy! I am not seeing that in Xubuntu. I just ran updates a few minutes before testing Synaptic via the menu.

---

### Post by Claus7 on 2020-03-19
Hello,

in ubuntu flashback is working fine too.

Regards!

---

### Post by dino99 on 2020-03-20
See the latest different tweaks of libc changelog

it needs more work to fully support libcryt1 integration

---

### Post by kurt18947 on 2020-03-21
> **Frogs Hair said:**
> I was unable to open synaptic from the icon after updates yesterday . Using sudo -H synaptic works fine, but the password entree box won't open. I have seen the same on wayland , but there is no wayland session on U Budgie. Is this happening on Ubuntu?

My understanding - and I could be wrong on this - is that Synaptic doesn't work under Wayland. Synaptic requires elevated privileges and Wayland doesn't permit that - or something. Synaptic will install and function as expected in an X session in my 20.04 install.

---

### Post by mc4man on 2020-03-21
> **kurt18947 said:**
> My understanding - and I could be wrong on this - is that Synaptic doesn't work under Wayland. Synaptic requires elevated privileges and Wayland doesn't permit that - or something. Synaptic will install and function as expected in an X session in my 20.04 install.
Been fixed to run under wayland foe a while now..
> synaptic (0.84.6ubuntu2) eoan; urgency=medium

  * cherry-pick:
    "Allow running synaptic under wayland again. Wayland supports
    this now since Gnome/Mutter 3.34"

 -- Michael Vogt <michael.vogt@ubuntu.com>  Sun, 13 Oct 2019 08:57:20 +0200



---

### Post by Frogs Hair on 2020-03-21
As I wrote U Budgie has no wayland session. I have reported this on Budgie discourse.

Edit: Fix pending and will be released in a few days.

---

