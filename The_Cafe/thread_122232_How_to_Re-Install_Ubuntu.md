---
title: "How to Re-Install Ubuntu?"
date: 2006-01-27
forum: The Cafe
---

### Post by cryingzombie on 2006-01-27
Hey all, I need your help.
I`ve installed ubuntu 5.04 few months ago and it run great (office work). But now Im facing a problem which my ubuntu system seems like corrupted. So I`d like to know here if there is any way to **re-install **this ubuntu system **without format the partition & losing the data**.

Hope yall who experienced on this can help. Thank You.

---

### Post by aysiu on 2006-01-27
[QUOTE=cryingzombie]I`d like to know here if there is any way to **re-install **this ubuntu system **without format the partition & losing the data**.[/QUOTE] It's called having a separate /home partition. Do you have one?

---

### Post by Titus A Duxass on 2006-01-27
The first thing to do is to make a back up of your system now and make a separate back of /home.

/home has all your personal files on it.

You may have to re-install ubuntu, but this time when you get to the partitioning part make: 1) a swap area of the appropriate size, 2) a / partition of  5 - 10 gb depending on how much space you have on the HDD. 3) a /home partition from all the remaining space.

After the installation you can fill /home with the data from your home back up.

If you do this technique you can uninstall and install linux (not just ubuntu) as often as you like, just do not touch the /home partition.

---

### Post by cryingzombie on 2006-01-27
Thanks aysiu.
I think nope. That was the first time I install this ubuntu so I just put filesystem & swap partition.

---

### Post by cryingzombie on 2006-01-27
Thanx Titus,
So you meant re-installing ubuntu is the same way we install the fresh new system? just put back to the new /home with the old /home (folder) which has backed up?

How about my mail in evolution? how do I backup them? and 1 more thing I don`t know how to edit .txt or .conf file from root console without GUI. I only know to use terminal & gedit when using GUI. Can you help me with that ?

---

### Post by Titus A Duxass on 2006-01-27
1st point - yes make a fresh install and add the / and /home partition.

2nd point - I know nothing about evolution so we'll have to hope someone else can help you there.

3rd point - to edit text or any files at the command line type: pico /path to file/file.name i.e to edit a text file in my home directory I do: 

             pico /home/titus/example.txt

To save it do Ctrl+x and then answer the questions.

Before you do anything to any files in the console make a backup of the file first with: cp /path to file/file.name /path to file/filename.old, then you can always reverse your changes.

---

### Post by byen on 2006-01-27
[QUOTE=cryingzombie]How about my mail in evolution? how do I backup them?[/QUOTE]
I know there may be other ways to do this but when I upgraded from Hoary to Breezy I just copied the .evolution folder hidden in /home folder and after re-install pasted it back into my /home. And for safety i also exported my address book and saved a copy of it as well.
Goodluck.

Notes: 
1.By doing this you will have all your mail
2.My address book did not have my old contact list (even after pasting the folder) so I used the one that I backed up (via export) to get back my contact list in evolution.
3.I did have to set my mail account again to send and receive email.

Edit: I know this may seem redundant to some but this is what I did and it worked. If there is a simpler way....I'd be glad to learn too :-)

---

### Post by ctt1wbw on 2006-01-27
If you have an 80 gig drive, what size would you recommend your /home partition being?  Say about half, is that enough room for all the programs?

---

### Post by Titus A Duxass on 2006-01-27
For an 80 gb drive (I have the same size) I have 10 gb for / and the rest for /home.  The / size is a little excessive but I would not go under 5 gb.

---

### Post by craiglarry on 2006-01-27
Is this not important? I don't know for sure because I'm so stupid I can't even get Ubuntu to work at all. Yet, you should know, there is really no such thing as reinstall in Ubuntu. It just installs another system and leaves the other one there. You dig it? I have a hd full of bad installs.

---

### Post by curuxz on 2006-01-27
Most applications store a .hidden directory (click view hidden files and you will see what i mean). This means a backup of a the home directory is normaly enough to keep everything else running without setting up again (provided the package is installed). The way I do it is backup my home folders hidden directories then reinstall all my apps, then overwrite the hidden folders and hey presto everythings working again.

---

### Post by Titus A Duxass on 2006-01-27
If you want to reinstall you must format the partitions that ubuntu was installed on in the first place otherwise you get a new installation.

---

