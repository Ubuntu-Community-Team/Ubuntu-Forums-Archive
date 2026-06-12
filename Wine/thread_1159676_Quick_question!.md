---
title: "Quick question!"
date: 2009-05-14
forum: Wine
---

### Post by Vostrocity on 2009-05-14
**Forget this, solved**





Sorry this is another nooby question. I installed some non-working apps in WINE, so I decided to start over. I removed WINE, and then realized that it doesn't remove the Windows apps. I was going to delete the .wine folder but I can't find it. Should I reinstall WINE and then delete the apps?

---

### Post by RedSingularity on 2009-05-14
.wine folder is hidden......it in the home folder just press ctl+h

---

### Post by Vostrocity on 2009-05-14
Thanks for the quick response. I did do that, but it's not there. I did a Tracker search too and I can't find it.

---

### Post by Vostrocity on 2009-05-14
Oh wait nvm! I tried removing by command line. Maybe that worked and I wasn't aware of it. Right now, the apps are still listed in the menu. I hope a reboot fixes it.

---

### Post by Vostrocity on 2009-05-14
Ok did a reboot and they're still there. I also reinstalled WINE, but the apps aren't in the .wine folder nor are they listed in the Uninstall Wine Software box. :(

---

### Post by Vostrocity on 2009-05-14
Oops forgot about this.
> Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

Ran the code but they're still there. Another reboot.
Sorry for so many posts, I need WINE urgently.

---

### Post by Vostrocity on 2009-05-14
Ok the terminal commands didn't do anything. But I went to all the folders manually and deleted the files, and now they're gone.

Sorry people for my barbaric posting. :D I needed WINE really badly to get to a Windows only software we use at school.

---

