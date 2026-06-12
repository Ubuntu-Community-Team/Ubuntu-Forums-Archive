---
title: "apt Errorr &quot;Invalid 'Date' entry in Release file&quot; when using Local Repo"
date: 2017-01-15
forum: The Cafe
---

### Post by tk83 on 2017-01-15
Just for info: If you're using your own local repository it looks like the latest version of apt has decided that the 'Date' field in the InRelease file must be in UTC, and not any other timezone (even if the offset is specified). The error you might start getting is similar to:
```
W: Invalid 'Date' entry in Release file /var/lib/apt/lists/_srv_packages_local-xenial_._InRelease
```

Ensure the date is in UTC in your generated (or manually created InRelease), e,g:
Date: Sun, 15 Jan 2017 04:59:43 +0000

(I use a Bash script to manually generate the Release file for my repo, I changed the relevant line to: echo -e "Date: `LANG=C date --utc -R`" >> Release)

---

### Post by QIII on 2017-01-15
Moved to the Cafe.

Not a support request.

---

