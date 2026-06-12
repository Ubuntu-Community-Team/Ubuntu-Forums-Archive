---
title: "Samba issue after getting rid of ebox"
date: 2009-05-31
forum: Server Platforms
---

### Post by sport9155 on 2009-05-31
I installed ebox-samba to see if it made admin tasks easier, it didn't so I decied to remove it and go back to the old faithfull; using VI and doing my own entries.
Stupid me though in thinking I was cleaning up and deleted the contents of the /etc/samba/ dir.  Now I figured I could just reinstall the samba package and voila the conf files would be back as defalt..No go though.
So how can I get samba back to a working default install?
 
thanks in advance.

---

### Post by Vegan on 2009-05-31
I use SAMBA for a crude file server behind a WRT54G and I use one share for the web server and the other for my MP3 files.

If you want a crude share its not hard to implement, if you want to do more I suggest a book as SAMBA is rather complicated to use in advanced environments.

---

### Post by Iowan on 2009-05-31
Which version are you running?  Someone can *probably* post the files you need to re-populate /etc/samba without re-installing.

---

### Post by sport9155 on 2009-06-01
I don't have the exact rev of the package, at hand, but its the one shipping with Ubuntu 9.04.
I can respond later today with the exact rev number.  that being said, I'm taking it that the default config files can not be regenerated just by readding the pkg?  so, if I was to remove a pkg using "purge" the dir and files that were created by the pkg are not removed?

---

### Post by Iowan on 2009-06-01
9.04 is the version I was looking for. I failed to specify "Ubuntu version" - as opposed to "Samba version". Re-installing the package *should* put the config files back - or I could post the three files from my laptop. Your choice! :D

---

### Post by sport9155 on 2009-06-01
Tried cleanning everything up one more time, and reinstalling and all is back to rights now.  Thanks for the help.
 
Derek

---

