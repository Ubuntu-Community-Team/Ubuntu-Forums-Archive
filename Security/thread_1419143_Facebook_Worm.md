---
title: "Facebook Worm"
date: 2010-03-01
forum: Security
---

### Post by sthrnpagan on 2010-03-01
I was watching the news today and I heard about a worm that comes from the ads on facebook. One of the biggest reasons I went with Linux is because I was told it is much more secure than Windows and that I would not need an anti-virus program. I am assuming this is true. Am I wrong? Is there a possibility that this worm could infect my computer?

---

### Post by FuturePilot on 2010-03-01
No, you are correct. It's unlikely that you could get infected with something like that. But regardless of OS, it's always best to watch what you click on and don't run unknown or untrusted code.

---

### Post by sthrnpagan on 2010-03-01
> **FuturePilot said:**
> No, you are correct. It's unlikely that you could get infected with something like that. But regardless of OS, it's always best to watch what you click on and don't run unknown or untrusted code.


Thank you for reassuring me. I got a little frightened there for a minute

---

### Post by TurnOfTide on 2010-03-01
No, a facebook worm doesn't install itself on your computer, it uses XSS to inject itself inside your profile somewhere (perhaps a comment on a pic or something like that, so it might not be on the main profile page). When others see it, it injects similiary. The point of this is to usually do a redirect to a spam website. Doesn't matter wether you run linux or windows on this. Some people like noscript or yescript + firefox. I do not use those, I never have and I think they are just silly, having to constantly check where JS is executing is just anal retentive.

---

### Post by OpSecShellshock on 2010-03-01
On Windows systems, JavaScript executed within a browser session is one of the most reliable and least immediately visible ways to propagate malicious code. The scripts can be made to execute in a browser running on Linux, but in the most standard configurations it won't do much beyond running. Most of them are written specifically for Windows. NoScript is your friend, as it blocks everything first and then lets you allow exactly what you want. It's tedious, but worth it in my opinion.

---

### Post by TurnOfTide on 2010-03-01
It isn't the javascript that brings in malicous code, it was microsoft's poor decision to allow active x - pure machine code, to run in IE. The js just redirects to a page exploiting a given vulnerability. I actually lost a windows box just from visiting a website back in like 2005/2004, when IE was a real crap hole in terms of security. Now, it is better these days, but still that is pretty bad!

As for worms on social networking websites, these are actually somewhat common and kind of fun. You could find some sources of them too since they obviously open source if you think about it ;) A friend of mine found an XSS on gaiaonline.com and attempted to write a worm on there but the devs found his debug code and patched it quicker then he could spread it.

---

