---
title: "Unauthenticated downloads safe?"
date: 2009-10-25
forum: Security
---

### Post by Camilia on 2009-10-25
When I download wine I get the message that the downloads are unauthenticated. Thus uncertain if it is safe to download the programs.

What is your opinion?

---

### Post by Agent ME on 2009-10-25
We can't tell you if something you downloaded is safe if we don't know what it is or where you got it from. But I can tell you what that specific error message is caused by.

The first time you click a desktop shortcut that window will appear (unless the shortcut was properly marked as executable, which Wine doesn't do for better or worse).

---

### Post by The Cog on 2009-10-25
The official wine web site is probably safe, but the safest place to get wine is from the repositories. This command will install it:
> sudo aptitude install wine

---

### Post by Camilia on 2009-10-25
I downloaded the programs only from synaptic package manager or the update manager.  The warnings that the program is not authenticated worried me.  I probably won't bother with upgrades for it since I don't need them.

---

### Post by gnuisancev3 on 2009-10-25
> **Camilia said:**
> I downloaded the programs only from synaptic package manager or the update manager.  The warnings that the program is not authenticated worried me.  I probably won't bother with upgrades for it since I don't need them.
This simply means that you have a repository listed in /etc/apt/sources.list in which you never installed a key for.

Maybe you can post the contents of this file here so we can deduct where your install of wine might be coming from?   

Chances are, if you're using official Ubuntu repos or something official by WINE, then it is PROBABLY safe.  If this is a repo you added from some random website, who knows.

---

### Post by Camilia on 2009-10-26
> **gnuisancev3 said:**
> This simply means that you have a repository listed in /etc/apt/sources.list in which you never installed a key for.

Maybe you can post the contents of this file here so we can deduct where your install of wine might be coming from?  

In the software sources, third-party software. I see [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main.  Is this what you are talking about?

How do I find this file /etc/apt/sources?

---

