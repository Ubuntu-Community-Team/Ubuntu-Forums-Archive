---
title: "Gmail Backup"
date: 2008-03-11
forum: Server Platforms
---

### Post by Penguin Power on 2008-03-11
Hey, does anyone know if it would be possible to backup files from my shared hosting on Gmail? I don't have any other remote backup facilities available, and I don't know if I really trust the hosting company to not spill coffee on the server my site is hosted on with all my files on it :(

I suppose any local scheme that could wget the entire /www/ directory every 24hrs and back it up locally would also be sufficient... Does anyone know of such an automated system? Gmail backup would be very cool, no worries, no fuss. Just to know it's there if something goes wrong. :popcorn:

---

### Post by LeoSolaris on 2008-03-12
check out gmailfs in the repos. It may not be in the Official repos, but if nothing else google it and see if you can locate the right repo.

The site listed on the package in synaptic is: [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)

---

### Post by ctyc on 2008-03-13
is rsync available to you?

---

