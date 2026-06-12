---
title: "How to adjust volume with keyboard?"
date: 2008-11-22
forum: The Cafe
---

### Post by days_of_ruin on 2008-11-22
Its just a normal keyboard.Is there some program that allows you to make
any key perform any action you want?

---

### Post by p_quarles on 2008-11-22
I use Fluxbox and amixer. I imagine there are keybinding applications independent of window managers, but I also know that Compiz has pretty flexible keyboard programming.

---

### Post by days_of_ruin on 2008-11-22
> **p_quarles said:**
> I use Fluxbox and amixer. I imagine there are keybinding applications independent of window managers, but I also know that Compiz has pretty flexible keyboard programming.

How do I use them?

---

### Post by Afkpuz on 2008-11-22
If you're looking to set a keyboard shortcut for volume up/down, that's easy.  Goto System>Preferences>Keyboard Shortcuts.  There, you can set several system wide key bindings.

---

### Post by days_of_ruin on 2008-11-22
> **Afkpuz said:**
> If you're looking to set a keyboard shortcut for volume up/down, that's easy.  Goto System>Preferences>Keyboard Shortcuts.  There, you can set several system wide key bindings.

THX I should have noticed that:D

---

### Post by p_quarles on 2008-11-22
> **days_of_ruin said:**
> How do I use them?
If you're using Fluxbox, it's simple: you just need to add lines to your .fluxbox/keys file:
```
174 :ExecCommand amixer sset Master 5%-
```
On my multimedia keyboard, the key with the X keycode 174 is the volume down key. Your keyboard may be different. Following is the syntax that causes the Fluxbox window manager to run the amixer command that reduces the Master volume control by 5%.

---

### Post by hessiess on 2008-11-22
XBindKeys

---

