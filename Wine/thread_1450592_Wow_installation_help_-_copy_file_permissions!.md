---
title: "Wow installation help - copy file permissions!"
date: 2010-04-09
forum: Wine
---

### Post by piecesofadream on 2010-04-09
Hello! :)

I've only these last few days converted to linux so bare with me, I'm still getting used to it :)
Basically, my new copy of WOW came today, just the original, no expansions. I was hoping for the versions with the CD's, but I got the 2 DVD version instead. Now, according to the ubuntu tutorial, I need to copy and paste the files from the disk into a new folder, but each time I try to do this I get permission errors and I don't know how to get past this...

I know it sounds silly, but could someone help me ? :)

---

### Post by viralmeme on 2010-04-09
[QUOTE=piecesofadream;9097548]I need to copy and paste the files from the disk into a new folder, but each time I try to do this I get permission errors and I don't know how to get past this.../QUOTE]

Fireup the console and type .. (without the dollar sign)

$mkdir /home/user/wow

$cp -r /path/to/DVD/* /home/user/wow

---

### Post by piecesofadream on 2010-04-09
Did the top bit fine, folder created.

Could you possibly explain the second one to me in a little more detail please! :) Like I said, I'm REALLY new to this! :)

---

### Post by piecesofadream on 2010-04-09
On a second note, did it but permission is still denied... :(

---

### Post by viralmeme on 2010-04-15
> **piecesofadream said:**
> On a second note, did it but permission is still denied... :(

$sudo -i

$mkdir /home/user/wow

$cp -r /path/to/DVD/* /home/user/wow

/path/to/DVD/ is where your DVD is mounted

/home/user/wow is where you want to copy the files to

$copy -r from-this-directory to-this-directory

The r means and all sub-directories

---

