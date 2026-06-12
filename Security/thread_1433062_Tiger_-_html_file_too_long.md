---
title: "Tiger - html file too long"
date: 2010-03-18
forum: Security
---

### Post by RasterBurn on 2010-03-18
hello, i am not sure if this is common on the 64bit version of ubuntu or not, but it seems when i run the command "tiger -H" it does its job and creats a nice output in html, i copy its output to a directory on my hdd and use chown to set it to my user account ownership (so that i can look it over as a normal user, is it common for the html file to contain 24199 lines of text? everything between lines 315 and 24157 are all when it checks the ntpd configuration and shows everything as dangling symlinks, is this normal? I know there are things to be ignored and thinks to take extra care into looking at, i am just wondering if this is normal or not cause it just doesnt seem like it would be normal (after all why would you put a symlink on the OS and not connect it to anything?) so anyways, these "dangling" symlinks that i seem to have a few hundred - thousand of, can they just be deleted? or would that be bad??? or is there some way to fix them? one instance of the dangling symlinks is:

```

***WARN*** [[fsys013w]]("file:///home/michael/security_reports/security.report.michael-desktop.100318-12:08.html#fsys013w")cannot access           /home/michael/.googleearth/instance-running-lock is a dangling           symlink. 
```
which links to the file "/proc/29446" which doesnt exist on the computer, been to the directory as well as did a whereis within the directory looking for that file.

there are only 6 of these symlinks in hidden subdirectories of my home folder, the rest are in varous subdirectories of /use/share once this major symlink delema is solved then the html file will be of a reasonable size, right now it is sitting at 1.5MB

also after the symlinks is dealt with i will move onto a different area of the scan to fix :)

---

### Post by RasterBurn on 2010-03-21
bump

---

### Post by unspawn on 2010-03-22
> **RasterBurn said:**
> everything between lines 315 and 24157 (..) shows everything as dangling symlinks, is this normal?
Not really.


> **RasterBurn said:**
> these "dangling" symlinks that i seem to have a few hundred - thousand of, can they just be deleted? or would that be bad??? or is there some way to fix them? one instance of the dangling symlinks is: ```
[fsys013w] cannot access /home/michael/.googleearth/instance-running-lock is a dangling symlink. 
```
The example you gave is not that interesting as it's just a link in some users ~/. I wouldn't delete any symbolic links outside of /home unless I knew what they were about. Having a few hundred sounds like either some file operation gone really bad (as in 'cp -rl') or a bug in tiger/scripts/find_files (check the Tiger bug tracker?)...


In etc/tigerrc the "Tiger_FSScan_SymLinks" option is used for checking symbolic links. In the worst case scenario you could turn it off until you find a fix. If you don't want to do that then Tiger_FSScan_SymLinks=Y basically means running tiger/scripts/find_files which shows a clue in the TODO about -prune paths. Maybe that's usable to (temporarily) exclude /usr/share until you find a fix?

---

### Post by RasterBurn on 2010-03-22
just having a look through the report right now, the dangling symlinks so far i have seem seem to be mainly /usr/share/gnome/help/ and then it goes to /usr/share/omf/ and then a some symlinks in various other directories, I have gone to various symlinks listed and have found that they are actually broken, so of course that seems to be alot of wasted space (being each symlink is ~10bytes each and take into consideration the size of the list), i would estimate about 95% of the symlinks relate in some way to a language pack i dont have installed or dont use due to the fact i dont understand the language like for instance           "/usr/share/gnome/help/config-desktop/it/config-desktop.xml" which links to "/usr/share/gnome/help-langpack/config-desktop/it/config-desktop.xml" which if i am not mistaken i require the Italian language pack to be installed for gnome and i dont understand Italian why the symlink is there in the first place has me puzzled and I guessing that language pack symlinks are safe to delete.

---

### Post by RasterBurn on 2010-03-25
bump

---

