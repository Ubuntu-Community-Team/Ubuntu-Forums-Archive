---
title: "Live Session testing - what applications are we expected to test?"
date: 2023-09-22
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2023-09-22
In the Live Session testcases it says something like:

> Use and execute the default applications found for the desktop enviroment being run
    All applications should function without error 

There's an awful lot of applications in an ISO file (unless it's a minimal install, such as xubuntu). Is one expected to test all of them? Or, what do most testers actually end up doing?

---

### Post by guiverc on 2023-09-23
What I do varies on how much time I have. It may be one of the following

- I boot the *live* ISO and use the session normally instead of an installed system. I may stream video in a window, use browser normally, use text editors, using either files from the local drive OR more commonly from network shares (meaning I need to add packages to enable NFS) etc.  (*in my own case; I usually QA on a different box to my primary system, so I've got that system if required for some reason*).

- what I was told the LIVE test should consist of, was opening every app in the menu, ensure it opens, looks correct, then close & do the next app. ie. there is minimal usage of the app; the primary task of LIVE was to ensure the apps open/close & look correct. If you have time you explore a few a little more eg. if its a spreadsheet (*libreoffice calc*) I may create a few rows of values, some text/numbers, a totals line (*adding/averaging values*) etc.  As Lubuntu included gcc, I've often created a simple C program (in `featherpad` or the text editor), used `gcc` to compile it, made a change (inc. fix typo!) in `vim` & saved it, recompile, run, then even return to `featherpad` & expect an error/warning message telling me to file contents have changed! (ie. due to `vim` edit/save)   As far as I recall `mousepad` does that too (*I think it told me that ~8 times yesterday on this box*)

- On some days I decide to open all apps, but rather than do all apps in the one LIVE session, I record 3 tests & do it on 3 boxes, and accomplish all apps being opened over those 3 tests. This provides testing for 3 boots & sessions on 3 different boxes, even if I only opened the Accessories during the first QA-test, and SystemTools in the last for example

- I often decide some days to concentrate on specific apps, OR consider myself I specific type of user, and try and behave as I believe that user would (ie. not my normal behavior). What you can do here will depend on how creative you are, and this can be a little "*fun*" (*you can often discover features in the software we regularly use that we didn't know existed*)

- If I've limited time, it will NOT be all apps (*and I note this in the summary section on the iso.qa website*), and I open only RANDOM apps...  I try and pick different apps to last time, or apps I don't regularly test, 1 or 2 from each type etc.  The more testing we can do, the better it is, but even partial tests are more beneficial than doing none because you lack time for complete testing.


For Lubuntu, I wrote [https://discourse.lubuntu.me/t/what-is-a-lubuntu-live-session-test/1672](https://discourse.lubuntu.me/t/what-is-a-lubuntu-live-session-test/1672) a few years ago. Do note I've not re-read that thread for this answer, so it's likely to be the same or similar detail.

---

### Post by Irihapeti on 2023-09-23
Thanks. That's helpful.

Most of my testing gets done in VMs, since I have RAM to spare but no spare box. I assume that the same principle applies there: better to do that than nothing at all.

---

### Post by guiverc on 2023-09-23
> **Irihapeti said:**
> 
Most of my testing gets done in VMs, since I have RAM to spare but no spare box. I assume that the same principle applies there

Yep. I'd expect a VM will pick almost all (esp. user level) software flaws equally, except for those really low-level kernel specific things, such as booting quirks with firmware, video issues with specific cards etc (*VMs often smooth these rough edges*), and most of those require the same (*or very close*) hardware to re-create.

Thank you for helping make Ubuntu better.

---

