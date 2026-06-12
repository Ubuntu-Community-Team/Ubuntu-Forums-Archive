---
title: "Shut off LCD on laptop server"
date: 2010-07-20
forum: Server Platforms
---

### Post by drovsen on 2010-07-20
Hi,

I've just installed Ubuntu Server 10.04 on an old laptop. I would like the screen to automatically shut off after, say, a minute of inactivity. 

- After some time, the monitor blanks but the backlight does not power down. 

- I do not have a gui installed, and do not want to install one since this is a server. Most of the solutions I've found involve running X or KDE.

- It's an old laptop and the lid switch is broken, so closing the lid won't work.

I appreciate any help!

---

### Post by arrrghhh on 2010-07-20
This looks like a solution, in the Arch forums.  I'll let you decide how far to take it...

[https://bbs.archlinux.org/viewtopic.php?id=66169](https://bbs.archlinux.org/viewtopic.php?id=66169)

---

### Post by volkswagner on 2010-07-20
Some laptops have a hard coded function key (my ThinkPad has FN+F7) to switch to the vga output.  This may be a quick solution without fussing with too many settings.  You may need acpi support for it to work.

---

### Post by drovsen on 2010-07-21
Thanks for the suggestions.

@Arrrghhh: setterm succeeded in blanking the monitor but not powering down the backlight. I couldn't figure this out.

@Volkswagner:  The fn key for toggling crt/lcd does not do anything.

My temporary solution for now was to install vbetool and run

```
sudo vbetool dpms off
```

This powers off the backlight the way I want. Unfortunately in order to turn it back on I need to either type blindly, or ssh into the machine from another computer. This is somewhat problematic.

Is it possible to bind a shell script to a fn key combination on a laptop? That would solve the problem!

---

### Post by arrrghhh on 2010-07-22
> **drovsen said:**
> Is it possible to bind a shell script to a fn key combination on a laptop? That would solve the problem!

Maybe not to a function key... but you can create an alias that's just a couple of letters... Perhaps that would work?

---

### Post by juancarlospaco on 2010-07-22
**xset dpms force off**

---

### Post by arrrghhh on 2010-07-22
> **juancarlospaco said:**
> **xset dpms force off**

Doesn't that require X?  The whole point is that he doesn't have X.org installed...

---

