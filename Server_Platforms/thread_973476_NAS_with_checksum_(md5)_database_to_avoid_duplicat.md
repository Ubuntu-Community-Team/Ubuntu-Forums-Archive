---
title: "NAS with checksum (md5) database to avoid duplicates"
date: 2008-11-06
forum: Server Platforms
---

### Post by jfwiedmayer on 2008-11-06
I'm looking for some help putting together a headless NAS from an old pc and am looking for some suggestions
 
Really what I would like to implement is a cron job to do a md5 for each file and save the file name and location to a database so that when new files are received by the NAS it runs a md5 and checks against the database to avoid backing up dupe files.   I am thinking this can be done with a storage folder an incoming folder and cron/md5.   Has anyone done something similar or have a much simpler solution?

---

### Post by jfwiedmayer on 2008-11-26
bump!

---

### Post by dantrevino on 2008-11-26
inotify-tools maybe?  i've not used them, but its a place to start looking.

---

