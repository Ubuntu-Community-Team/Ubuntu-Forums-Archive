---
title: "nautilus rename issue after scrolling a dir"
date: 2014-01-08
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-01-08
Seen here on long term install & on a new install of today.
When opening a nautilus window where a large number of files aren't visible, after scrolling window to bottom,  all the **newly exposed files**  will have an issue when r. click > rename is used.

What happens here is the name disappears & the rename label is invisible. For purposes of testing it seems 50% of files not seen when window is opened will cause (though much less than 50% in practice, only very short scrolls here don't cause.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961)

---

### Post by kansasnoob on 2014-01-08
Thanks for reporting this. I noticed it while testing 3.10 packages from the gnome 3 PPA but then I got side-tracked and forgot about it :oops:

I me-tooed, subscribed, and added a note.

---

### Post by Mateusz Stachowski on 2014-01-08
I thought that it's happening because of changes that I made to the Ambiance theme to make it look more consistent. Anyway I also me-tooed that bug report.

BTW this inconsistencies in Ambiance theme I have opened a bug report some time ago but nobody seems to care.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1212712](https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1212712)

[http://discourse.ubuntu.com/t/inconsistencies-in-windows-with-ambiance-theme/757/16](http://discourse.ubuntu.com/t/inconsistencies-in-windows-with-ambiance-theme/757/16)

---

### Post by Mateusz Stachowski on 2014-01-08
This bug is also present in Nemo. That's a second bug that affects both Nautilus and Nemo. 

Previous was and still is about memory leak in list view mode.

[http://ubuntuforums.org/showthread.php?t=2196975](http://ubuntuforums.org/showthread.php?t=2196975)    (decent mem leak in nautilus > list view)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1264539](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1264539)   (List view: scrolling a directory with thumbnails leaks memory)

---

### Post by craig10x on 2014-01-08
Yeah...i am getting that also...so i added "this affects me also" to the bug report...

---

### Post by mc4man on 2014-01-08
> **Mateusz Stachowski said:**
> I thought that it's happening because of changes that I made to the Ambiance theme to make it look more consistent. Anyway I also me-tooed that bug report.

BTW this inconsistencies in Ambiance theme I have opened a bug report some time ago but nobody seems to care.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1212712](https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1212712)

[http://discourse.ubuntu.com/t/inconsistencies-in-windows-with-ambiance-theme/757/16](http://discourse.ubuntu.com/t/inconsistencies-in-windows-with-ambiance-theme/757/16)

There is going to be new unico &unity-themes packages to fix DnD in nautilus, gedit, ect.  (what you are dragging is unseen
That may affect your changes to ambiance depending on what you've done, if so I've found only the unico change is really needed here

As far as your Lp bug on gtk2 menus I've had an open bug there for for almost 2 years, figure at this point it's not going to be fixed. 
( have been fixing for myself for about the same time
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/961679](https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/961679)

---

### Post by Mateusz Stachowski on 2014-01-11
This bug is now fixed for Nautilus.

> [COLOR=#333333][FONT=Ubuntu Mono]This bug was fixed in the package nautilus - 1:3.8.2-0ubuntu5
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]
nautilus (1:3.8.2-0ubuntu5) trusty; urgency=medium
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]  * debian/patches/git_rename_display.patch:
    - correctly display the rename box even when scrolling (lp: [#1266961]("https://bugs.launchpad.net/bugs/1266961"))
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono] -- Sebastien Bacher <seb128@ubuntu.com> Fri, 10 Jan 2014 17:46:06 +0100[/FONT][/COLOR]

Obviously this didn't solve the problem for Nemo.

---

### Post by Mateusz Stachowski on 2014-01-11
Mint developers fixed this issue for Nemo in latest commit to git repo.

> Fix bad positioning of rename window in some views (gtk 3.10)

[https://bugzilla.gnome.org/show_bug.cgi?id=705464](https://bugzilla.gnome.org/show_bug.cgi?id=705464)
 
master

mtwebster authored 9 days ago

[https://github.com/linuxmint/nemo/commit/d5377cfd53034b6ab5588376322126f48782ec59](https://github.com/linuxmint/nemo/commit/d5377cfd53034b6ab5588376322126f48782ec59)

---

