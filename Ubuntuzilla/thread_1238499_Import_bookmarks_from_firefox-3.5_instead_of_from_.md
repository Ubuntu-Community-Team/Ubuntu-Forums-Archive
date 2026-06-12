---
title: "Import bookmarks from firefox-3.5 instead of from firefox"
date: 2009-08-12
forum: Ubuntuzilla
---

### Post by jis on 2009-08-12
I used firefox-3.5 installed from a repository before installing firefox by ubuntuzilla. The script took bookmarks from firefox, but I want them from firefox-3.5.

---

### Post by nanotube on 2009-08-12
Hi
not sure where firefox-3.5 from the repos stores its profile, probably somewhere like ~/.mozilla/firefox-3.5/someletters.default ?

find where that profile is, inside there will be a "bookmarkbackups" folder with some dated files.

so, open firefox, open bookmarks -> organize bookmarks -> import and backup -> restore -> choose file, browse to that directory, and choose the latest file.

hope that helps. :)

---

### Post by jis on 2009-08-12
It works, thanks.

---

### Post by nanotube on 2009-08-12
excellent :)

---

