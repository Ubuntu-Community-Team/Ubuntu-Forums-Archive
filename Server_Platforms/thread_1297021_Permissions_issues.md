---
title: "Permissions issues"
date: 2009-10-21
forum: Server Platforms
---

### Post by J V on 2009-10-21
While attempting to move the default site on my development purpose home PC to have permissions to edit the files, somehow apache assigned all the files root as owner.

Now I know that if I change the owner of the files (An incredibly daunting task in its own) apache will just switch them back again...

Anyone know of some setting defining who owns the site? (sites-available)

---

### Post by abaden on 2009-10-21
If Apache is run by www-data, it shouldn't have any permission to change file permissions - are you sure that you didn't accidentally change the permissions while copying the files? Try changing the permissions  / owner on one file back and see if they stay that way.


Alex

---

### Post by J V on 2009-10-21
Oh I think I've found it, I must have copied over with sudo...

Thanks all the same

---

### Post by abaden on 2009-10-21
Happens to all of us... more than we'd like to admit I'm sure. Glad you worked it out!


Alex

---

