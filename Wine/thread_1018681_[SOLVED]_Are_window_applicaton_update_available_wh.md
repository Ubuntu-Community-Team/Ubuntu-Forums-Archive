---
title: "[SOLVED] Are window applicaton update available when using wine?"
date: 2008-12-22
forum: Wine
---

### Post by kkruecke on 2008-12-22
If I install an Windows application, like Outlook 2003 or Word 2007, are Windows updates to these applications going to be available, like there periodically are on Windows, when there are bug or security fixes?

---

### Post by DieB on 2008-12-22
as far as i assume: no they won't

---

### Post by namdung on 2008-12-22
> **kkruecke said:**
> If I install an Windows application, like Outlook 2003 or Word 2007, are Windows updates to these applications going to be available, like there periodically are on Windows, when there are bug or security fixes?


Why would u use MS Office when OO3 does everything better? Anyways Outlook doesn't install in WINE.

---

### Post by kkruecke on 2008-12-22
Open Office doesn't have an email client.
While Outlook 2003 did install in Wine
       #wine /media/cdrom0/setup.exe
it doesn't run.

---

### Post by almigi on 2008-12-22
Mabye I'm wrong, but here's my understanding... For awhile, the updater for MicroSoft Office did work fine under Wine as far as applying patches, security upgrades, etc...

However, MicroSoft then updated the updater so that it would check the registry of the machine it was on to figure out if it was really Windows or Wine, and as such, it would intentionally not update if you were running it under Wine.

However, I guess enough people made a stink over this to MicroSoft (after all, if I'm paying for the software I should be able to run it anywhere it works), and this being a possible anti-trust issue, I think MicroSoft rescinded that "modification" and the updater, should, in theory, work now.

- Al

---

