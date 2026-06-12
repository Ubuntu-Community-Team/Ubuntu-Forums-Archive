---
title: "Somehow &quot;Trojan Agent&quot; Keeps Getting In Through Firefox..."
date: 2016-04-28
forum: Security
---

### Post by BlacklightHalo on 2016-04-28
Hello,

I'm having a recurring problem where, despite the use of a firewall and not visiting with my computer any sites that I would normally associate with viruses or other security risks, somehow every time I perform a security scan of my home directory with ClamTK, I come back with between 4 to 7 risks-found, one or two of which is always a "Trojan Agent" file. ClamTK says the source is Firefox. I tried ditching the outdated/no longer supported Adobe Flash Plugin, thinking it might be the "weak-link," but the problem persists.

What can be done about this?

Thank you for reading, and in advance for any information you might be able to provide.

---

### Post by Habitual on 2016-04-28
Did you enable PUA scanning?
It's not enabled by default.

---

### Post by BlacklightHalo on 2016-04-29
I don't believe so. I just looked it up and found the definition on Wikipedia. Is that something I enable in Firefox?

*Sorry, my mistake. Found it in ClamTK and yes it's already enabled. Is that a problem? Seems like it would be a good thing.

---

### Post by Habitual on 2016-04-29
No, not in Firefox.
PUA stands for Potentially Unwanted Applications
and it an option in clam-tk.

default  is unchecked.

---

### Post by BlacklightHalo on 2016-04-29
Yeah I got that now, thanks. It has been checked since before I started detecting these Trojan-Agent files.

---

### Post by sgian on 2016-04-30
The problem with ClamAV, which you are using through the ClamTK GUI, is the number of false positives, especially with PUA checked.  First thing you should do in my opinion is make sure that ClamTK is not scanning for the PUA option just because it has so many false positives on things that are needed.  For example, when I first was using ClamTK, I messed up my ability to print by deleting or quarantining PUA's that I couldn't identify.  Turned out they weren't PUA's afterall.  Oops.

Next time you get any kind of positive on ClamTK, upload the supposedly "infected" file to [https://www.virustotal.com/](https://www.virustotal.com/) which is a free file scanner, before doing anything else.

---

