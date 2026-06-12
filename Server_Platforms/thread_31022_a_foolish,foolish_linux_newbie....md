---
title: "a foolish,foolish linux newbie..."
date: 2005-05-01
forum: Server Platforms
---

### Post by soulboyluis on 2005-05-01
hey there..I've just installed ubuntu, and I've comepletely forgotten the un + pw...I can log in as admin, buth wion't let me into the gui bootup...pls forgive me, I've just had a addled weekend, andI've got a rotten headcold. How can I finsd out the un /pw? knoppix? get around in recovery mode? I need a linux refresher, used to know some commands for dir nvaigation...thanks in adavnce... ](*,)

---

### Post by sethmahoney on 2005-05-01
I don't know how you can find out that info, but if you reinstall linux you should be able to enter a new username/pw.

Actually...

If you can login as admin, you should be able to find out the username by typing

cd /home
ls

And then looking at the list of directories that will pop up.  One of them should be the same as your username (hopefully you can remember which one!).

Also, if you do reinstall linux, and if you originally installed it with /home on its own partition, so long as you don't reformat the /home partition you can keep all your old data, but its slightly tricky.

---

### Post by jdong on 2005-05-01
If you know the root password, log in at a command line, and do **ls /home**. That should give away the username ;)

Once you know that, type **passwd username**, and that'll allow you to set a new password.


If you can't get a root login, refer to this: [http://ubuntuforums.org/showthread.php?t=3609&highlight=forgot+password](http://ubuntuforums.org/showthread.php?t=3609&highlight=forgot+password)

---

### Post by soulboyluis on 2005-05-01
:) Many thanks folks, now using online with the newly installed OS, lots to figure out now...Like I forgot how  to change dir..duh! ta again for the attention..if anyone knows of any good ubuntu dox to download, that would speed up things..the GUI is open, and I've got to start administering...(funny how the more along the IT ladder you go, instead of shuffling papers and putting them away, you shuffle more and more electrons)

---

### Post by s0c0 on 2005-05-01
In the future just google: linux root password recover with knoppix.  I had to recover my ubuntu root passwd a month ago and it was simple.  Once your knoppix boots up the process takes just a few short mins.

---

