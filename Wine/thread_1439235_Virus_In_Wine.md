---
title: "Virus In Wine?"
date: 2010-03-25
forum: Wine
---

### Post by TicTac52 on 2010-03-25
I've heard that it's nearly impossible, if not completely, to have a virus attack Ubuntu. But can a virus run under Wine and jack up your system?

---

### Post by kenweill on 2010-03-25
> **TicTac52 said:**
> I've heard that it's nearly impossible, if not completely, to have a virus attack Ubuntu. But can a virus run under Wine and jack up your system?

Nope

---

### Post by dino99 on 2010-03-26
> **TicTac52 said:**
> I've heard that it's nearly impossible, if not completely, to have a virus attack Ubuntu. But can a virus run under Wine and jack up your system?

of course, that's why you might care about rights. Install clamav and the related packages too. Wine is like Windows and antivirus & firewall are needed.

---

### Post by asdfoo on 2010-03-26
> **kenweill said:**
> Nope

They can and do.

Wine does not provide any security against attacks from viruses, malware or trojans.  Infact, with each release of Wine they become more compatible with Wine.

From a default Wine setup, anything which you run in Wine has access to any files which your userid does on Ubuntu, so your documents, network, internet, part of the display.

---

### Post by hikaricore on 2010-03-27
The likelihood of there being a major issue is minimal.
Actual system level viruses are a rare beast these days and they will probably fail under wine.
Malware could cause issues with your current wine config and possibly (but doubtful) your user account.
When I have doubts about a software title I use wine prefixes and if the program doesn't behave as expected I just remove the prefix afterwords.

---

