---
title: "Firefox not loadng bookmarks"
date: 2009-08-09
forum: Ubuntuzilla
---

### Post by mick222 on 2009-08-09
My bookmarks have disappeared in firefox 3.5 ,installed using ubuntuzilla,after i installed bbciplayer.I have no back or forward buttons and no history is recorded.When i open in terminal everything is ok any help would be appreciated

---

### Post by khelben1979 on 2009-08-09
I suggest you make a backup of your bookmarks next time. See attached file.

Reinstall Firefox.

---

### Post by mick222 on 2009-08-09
when i start firefox as root i have my bookmarks .It's not just bookmarks it gives a warning that another application is using the bookmarks folder and i also can't download or move back and forth between pages.

---

### Post by nanotube on 2009-08-09
Hi
if things work as root but not as user, that's an indication that the ownership of some files in your profile is messed up. try this tip from the ubuntuzilla faq:

[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.2C_Seamonkey.5D_Some_stuff_only_works_when_I_run_as_root.21](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.2C_Seamonkey.5D_Some_stuff_only_works_when_I_run_as_root.21)

---

### Post by nanotube on 2009-08-09
> **khelben1979 said:**
> I suggest you make a backup of your bookmarks next time. See attached file.

Reinstall Firefox.

ubuntuzilla automatically makes a profile backup. so if it comes to that, he's covered. :)

---

### Post by mick222 on 2009-08-09
thx nanotube that seemed to work .I think i used sudo intead of gksudo to run from terminal.

---

### Post by nanotube on 2009-08-09
> **mick222 said:**
> thx nanotube that seemed to work .I think i used sudo intead of gksudo to run from terminal.

glad it worked. :)

---

### Post by bugritall on 2009-09-05
The same thing has just happened to me. I returned to Ubuntu after playing a session of Rome:TW in Windoze, only to discover that Firefox's Bookmarks panel was completely empty. Everything had been fine in Windoze so I returned there to verify the fact and all was, indeed, well over there. (I had better explain that my two Firefoxes both use the same store.)

Back in Ubuntu, when I had a look at* ~/.mozilla/firefox/profiles.ini* and tried to save it, I was advised that the file couldn't be saved because there wasn't enough disc space. Huh? 

When I checked, however, Ubuntu was correct and there was only 8k available. I had recently been doing a bit of downloading and I had unwittingly stuffed 14GB in to the Deleted items folder and used up very nearly every last byte of Ubuntu's disc space. Anyway, after I emptied Trash and restarted Firefox, there were my bookmarks!

**So, if your Firefox bookmarks disappear, try emptying Trash.**

---

