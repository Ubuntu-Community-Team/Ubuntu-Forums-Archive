---
title: "Firefox back space"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by crookiecookie on 2012-04-04
after updating to precise the back button in fire fox is non existent and the dropdown url history in search bar dont open

Aswell as the links on search page no mouse hover icon

if any one can help

---

### Post by lovinglinux on 2012-04-05
Export your bookmarks using the bookmark manager (CTRL+SHIFT+O). Click "Import and Backup >> Export Bookmarks as HTML". Then close Firefox, open ~/.mozilla/firefox folder, locate your profile folder and open it. Locate the file places.sqlite. Rename it to something else. Restart Firefox. Open the bookmark manager. Click "Import and Backup >> Import Bookmarks from HTML".

Let me know if that solves the problem or not.

---

### Post by crookiecookie on 2012-04-05
That did not work
I had no bookmarks to export so it wouldnt save
and it wouldnt let me book mark a page

But have no fear i have solved this issue

What i did was unistall fire fox and ubufox
then went to home directory and clicked option on top bar of window
to view hidden files i then deleted .mozzila folder

Reinstalled firefox and voila its back to normall

---

### Post by lovinglinux on 2012-04-05
> **crookiecookie said:**
> That did not work
I had no bookmarks to export so it wouldnt save
and it wouldnt let me book mark a page

But have no fear i have solved this issue

What i did was unistall fire fox and ubufox
then went to home directory and clicked option on top bar of window
to view hidden files i then deleted .mozzila folder

Reinstalled firefox and voila its back to normall

I usually don't like to suggest deleting the profile, but if you don' t have any important data, then it is usually the easier solution to solve many problems. As I expected, it was a corrupted profile file, just missed the actual culprit. :-)

---

