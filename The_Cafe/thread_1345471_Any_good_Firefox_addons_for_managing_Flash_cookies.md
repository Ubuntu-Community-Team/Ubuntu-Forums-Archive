---
title: "Any good Firefox addons for managing Flash cookies"
date: 2009-12-04
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-04
What is a good Firefox extension to manage Flash cookies?

I use Firefox in private browsing mode so that all of my web activity is saved to the RAM instead of the hard drive and would like my Flash cookies to work in this way as well. But Flash cookies are a separate matter (they save in the .macromedia folder in your /home directory) and don't follow that protocol.

I don't mind having them enabled. But I would prefer for them to be saved to my RAM with the rest of my web information where it's erased every time you power down your computer. Instead on the hard drive where even if you write over the section of the hard drive where they were originally stored theirs still the possibility of data remembrance.

Would disabling them completely make some Flash applications not function properly, or are they purely for convenience?

---

### Post by FuturePilot on 2009-12-04
I don't know if it's possible to have them stored in RAM. Maybe you could do it with a RAM disk or something. I haven't tried completely disabling them. The worst that I think would happen is that the settings will be forgotten when you leave the page. This is probably the next best thing. [https://addons.mozilla.org/en-US/firefox/addon/6623]("https://addons.mozilla.org/en-US/firefox/addon/6623")

---

### Post by BenAshton24 on 2009-12-04
How about BetterPrivacy...

[https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)

---

### Post by blueshiftoverwatch on 2009-12-05
Thanks.

---

### Post by josephpmh on 2009-12-05
I like flashblock.  It blocks any flash from loading unless you want it.

---

### Post by blueshiftoverwatch on 2009-12-05
Aparently if I just set the permissions of my .macromedia folder access files only and set the dom.storage.enabled in about:config to false, I've not only rendered Better Privacy obsolete. I've one upped it, as now flash objects and DOM information won't even be saved to my computer in the first place, let alone need to be periodically cleared out when I closer the browser.

Edit: what is this "ping tracking disabled" option in Better Privacy. Is it the "broser.sends.pings" option in the about:config menu?
> **josephpmh said:**
> I like flashblock.  It blocks any flash from loading unless you want it.
I use NoScript, which basically does the same thing. Some of my friends use Ad Block Plus, but web ads don't really bother me.

---

