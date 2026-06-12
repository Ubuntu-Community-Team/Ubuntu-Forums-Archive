---
title: "Get rid of all those anoying .ini ,and .db Windows left in your files in 3 steps"
date: 2009-04-30
forum: The Cafe
---

### Post by swoll1980 on 2009-04-30
Choose the directory you want to clean out.
```
cd /path_to _folder_you_want_to_clean
```

```
find . -name *.ini -type f -print0 | xargs -0 /bin/rm
```
finds and deletes all the .ini
```
 find . -name *.db -type f -print0 | xargs -0 /bin/rm
```
finds and deletes all the .db

---

### Post by Dark Aspect on 2009-04-30
Cool, XP via Virtualbox dumps crap in my home folder when I mount it as a network drive. This works well to get ride of these files.

---

### Post by swoll1980 on 2009-04-30
> **Dark Aspect said:**
> Cool, XP via Virtualbox dumps crap in my home folder when I mount it as a network drive. This works well to get ride of these files.

You can also use
 ```
find . -name *.jpg -type f -print0 | xargs -0 /bin/rm
```

To pull the album art out of your music folders. Make sure you change to you music directory first.
```
 cd /path_to_your_music_folder
```
Make sure your in the right folder
 ```
ls
```
Then go ahead and execute the command
**WARNING!!!** *If your in the wrong directory you could delete all your photos*

---

### Post by swoll1980 on 2009-04-30
I was was just thinking; If you have wine installed I wouldn't do it from your ~/ ,but rather pick specific folders you want to rid of .ini because the wine programs might need the .ini I'm not sure

---

### Post by ajgreeny on 2009-04-30
And beware that f-spot keeps the photo info in a .db file in ~/.gnome2/f-spot/photos.db.  Get rid of that and you will need to re-import all your photos again, along with all their tags.

---

### Post by Namtabmai on 2009-04-30
> **ajgreeny said:**
> f-spot

And Thunderbird, Firefox, Exaile.... that first command probably isn't the safest thing to run blindly.

---

### Post by swoll1980 on 2009-04-30
Yeah we should defiantly pick the directory we want to clean out, and not use ~/ I had know Idea Linux used all these Windowss files. Now I just have to ask why. The command does save a lot of time though. I cleaned out 100s and 100s of junk files in a few seconds.

---

