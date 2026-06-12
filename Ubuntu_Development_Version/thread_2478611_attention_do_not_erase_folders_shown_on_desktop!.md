---
title: "attention: do not erase folders shown on desktop!"
date: 2022-08-30
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-08-30
Hello,

with today's updates I saw all folders under my user appearing on desktop. I though that they were just shortcuts and I erased them all but home. After some time I noticed that they no longer existed under nautilus or even on the panel of flashback under Places. If they appear, leave them there!

Regards!

---

### Post by TheFu on 2022-08-30
Directories have always been "real" under all versions of Ubuntu.  Some users may make them symbolic links to other locations, but that certainly isn't the default.  I routinely delete all the directories created by the new user skel, since I don't use them.  ~/Downloads/ comes back - I think that is from the browser.  For 20+ yrs, I put downloads into /tmp/, but snap packages don't allow that.

---

### Post by Claus7 on 2022-08-31
Hello,

I do not know why this happened in the first place. As I mentioned I deleted them which was a mistake. In order to bring them back I created them anew under the home folder of nautilus and edited the file: ~/.config/user-dirs.dirs by placing back the names of the folders missing. I logged out and back in and everything was back to normal with folders having the corresponding icon-labels, apart form the files that were placed in these folders that were deleted.

Now on my flashback desktop I can see only the home folder and trash.

Regards!

---

### Post by Claus7 on 2022-08-31
Hello,

and in order to change the size of desktop icons I opened dconf editor and changed them from there: /org/gnome/gnome-flashback/desktop/icons/icon-size 

Regards!

---

