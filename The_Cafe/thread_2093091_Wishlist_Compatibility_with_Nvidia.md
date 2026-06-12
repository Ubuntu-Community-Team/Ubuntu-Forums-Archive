---
title: "Wishlist: Compatibility with Nvidia"
date: 2012-12-09
forum: The Cafe
---

### Post by JetSirus on 2012-12-09
GTS 360M
GTX 580

Neither of these cards (and perhaps others) can even boot the OS and instead leave you sitting at a screen filled with corrupted graphics.  This issue has been around since 10.10 I think.  You can use nomodeset to at least get into the OS and install the Nvidia drivers.  

Might be something someone with more knowledge than me would want to fix, as this issue can't be a small one.  Seems like a simple flag or some such could be set to default to nomodeset when certain cards are detected.

It's an odd issue as ever single PC I own has a different yet, still incompatible video card.

---

### Post by mörgæs on 2012-12-11
This thread might offer some help:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by haqking on 2012-12-11
I use the GTX 580 and it works fine with propietary driver in Slackware, Ubuntu, Mint and Fedora. I have never had any major issues with it, I use it with 2 screens at 1920x1080.  It may not work initial upon install but its easy enough to fix

---

### Post by JetSirus on 2012-12-13
You misunderstand.  I can get the system to work fine, by using nomodeset.  Then when I get into the OS I can install both the OS and the graphics drivers.  The issue is that it's a simple issue to fix that can cause a lot of confusion for new users.

---

### Post by haqking on 2012-12-13
> **JetSirus said:**
> You misunderstand.  I can get the system to work fine, by using nomodeset.  Then when I get into the OS I can install both the OS and the graphics drivers.  The issue is that it's a simple issue to fix that can cause a lot of confusion for new users.

So you arent asking for support ?

If you want a discussion ask the mod to put it in the cafe.

---

### Post by mörgæs on 2012-12-13
All new ideas are welcome. Please take a look at
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

If it's already there, you can vote for it, or post the idea if not.

Moved to the cafe.

---

### Post by grahammechanical on 2012-12-13
The problem is not down to Ubuntu but to Nvidia not being open (as is their right) to the technical details of the hardware so that the X.Org foundation can develop the X-server to be more compatible with Nvidia hardware.

It seems to me that a lot of people are doing the best that they can under difficult circumstances.

Regards.

---

### Post by JetSirus on 2012-12-16
> **grahammechanical said:**
> The problem is not down to Ubuntu but to Nvidia not being open (as is their right) to the technical details of the hardware so that the X.Org foundation can develop the X-server to be more compatible with Nvidia hardware.

It seems to me that a lot of people are doing the best that they can under difficult circumstances.

Regards.

Aha, but the issue is that Ubuntu and most all of its variants can boot these cards fine without closed source drivers.  But for reasons I don't understand it does not work correctly.  When you try to load Ubuntu on a system with these certain video cards I assume it tries to load some proprietary driver that always fails.  The solution is to simply use whatever the default drivers are that load when nomodeset is flagged.  Then the end user can use the OS as intended, and will have the option to install any closed source drivers they wish.

---

