---
title: "live-desktop, install-alternative, your thoughts on the CD name change for Ubuntu?"
date: 2006-05-27
forum: The Cafe
---

### Post by RAV TUX on 2006-05-27
live-desktop, install-alternate, your thoughts on the CD name change for Ubuntu?
(my apologies, typo)



[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2006-May/000140.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2006-May/000140.html)

"Following various discussions among the Ubuntu release team, the
Canonical business department, et al, the next round of daily CD image
builds will be renamed.

Instead of "dapper-live-*", there will be "dapper-desktop-*", reflecting
the rename to "desktop CD" that we started at the Dapper Beta release to
indicate that the live CD is now also installable.

Instead of "dapper-install-*", there will be "dapper-alternate-*", the
"alternate install CD"; this avoids confusion along the lines of "which
CD do I use to install a new system?", and indicates that the desktop CD
should be used for most installation scenarios while still allowing
people to find the alternate install CD for special cases (OEM,
automation, LVM, RAID, etc.).

If you have scripts to download CD images using rsync or similar, please
make sure that they can cope with this change of name. In particular,
avoid using rsync's --delete option so that you aren't faced with having
to download everything from scratch.

Cheers,

-- 
Colin Watson  "

---

### Post by mostwanted on 2006-05-27
I don't think the Live CD installer is ready yet so I this renaming is not so fortunate as it leads to believe that the new Desktop CD is somehow the most stable way to install (considering the other CD is called "alternate").

---

### Post by SeanTater on 2006-05-27
Even if it's not perfect -- it's already acceptable (to me), so by June 6th, it should be quite stable, IMO.. But I would imagine that for many people, the "desktop" cd will still be the best choice, even if it's 2% less stable..

---

### Post by Jucato on 2006-05-27
[quote=mostwanted]I don't think the Live CD installer is ready yet so I this renaming is not so fortunate as it leads to believe that the new Desktop CD is somehow the most stable way to install (considering the other CD is called "alternate").[/quote]

Is the Desktop CD Installer still not ready in the Release Candidate that was announced the other day? Bummer...

---

### Post by K.Mandla on 2006-05-27
It's a subtle change, and one I can get used to over time. Personally I think the Live CD name is more accurate that way. Alternate is ... ?

---

### Post by AlexandreP on 2006-05-29
[QUOTE=K.Mandla]Personally I think the Live CD name is more accurate that way. Alternate is ... ?[/QUOTE]
Agree.  I think *desktop* reflects more what the liveCD has become by now.  I don't like the *alternate* name, it's like if it only good if the *desktop* CD does not work on your computer.  This is not true, *alternate* offers some other possibilities not available using *desktop*.

On the other hand, this name change is done to prevent questions about which CD is the right one for installing Ubuntu.  People will try first the liveCD, which is what the name change is about.  I have no better idea on how to call the *alternate*... :-?

---

### Post by gingermark on 2006-05-29
[QUOTE=AlexandreP]I have no better idea on how to call the *alternate*... :-?[/QUOTE]
I'd call it the "traditional" install CD. Or maybe "convetional". Either way, I agree that "alternative" isn't a terribly useful name for it.

---

### Post by RAV TUX on 2006-05-29
[quote=gingermark]I'd call it the "traditional" install CD. Or maybe "convetional". Either way, I agree that "alternative" isn't a terribly useful name for it.[/quote] 
It's actually "alternate" NOT "alternative",...again my apologies for the typo in the thread title.








.

---

### Post by prizrak on 2006-05-30
I personally think it's confusing. The name LiveCD has been around for a while, at the same time my non tech friends have no clue what a Live CD is so maybe a more descriptive name would be better for the non-techie crowd.
Although I think a mouse over tip explaining what a LiveCD is would be better.

---

### Post by Iandefor on 2006-05-30
I like the new Live installer system. It worked perfectly for me during install- but, apparently, debconf is all funky when you install it that way. Can't install Java or Flash properly until you fix it.

---

### Post by gingermark on 2006-05-30
[QUOTE=Iandefor]I like the new Live installer system. It worked perfectly for me during install- but, apparently, debconf is all funky when you install it that way. Can't install Java or Flash properly until you fix it.[/QUOTE]
I installed that way, but haven't gotten around to installing those yet. I don't suppose there is a thread you could link to explaining the fix? Surprisingly searching for "funky debconf" didn't bring much up :)

---

### Post by Iandefor on 2006-05-30
[quote=gingermark]I installed that way, but haven't gotten around to installing those yet. I don't suppose there is a thread you could link to explaining the fix? Surprisingly searching for "funky debconf" didn't bring much up :)[/quote] Arnieboy posted a fix somewhere. I reposted it here:

[http://www.ubuntuforums.org/showpost.php?p=1067050&postcount=13]("http://www.ubuntuforums.org/showpost.php?p=1067050&postcount=13")[I][COLOR=Black]
[/COLOR][/I]

---

