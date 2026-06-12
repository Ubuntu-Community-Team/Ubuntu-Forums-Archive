---
title: "Ubuntu One not showing emblems"
date: 2010-05-12
forum: Ubuntu One (CLOSED)
---

### Post by Amzer zo on 2010-05-12
I tagged a couple of folders under my home directory (Ubuntu 10.04) but I don't see any emblems anymore (they were showing initially first time I tagged them) on these folders despite the files being correctly sent to the cloud.  Only the "Ubuntu One" folder has the "ubuntuone-unsynchronized" emblem showing.

I am also trying to tag another folder (still in /home/user) and the right-click shows the "Synchronize on Ubuntu One" entry but nothing happens when trying to activate it.

How can I make sure the emblems are present and reflect correctly the sync'ing status?

---

### Post by nikkkko on 2010-05-13
Same for me. None of the directories I have asked to be sychronised show any icon changes.  

Also, in the Ubuntu One preferences window I get the message that synchronisation is in progress, but no activity on the bar and no sign that anything is actually happening.

In short, Ubuntu One suffers from chronic lack of feedback.

---

### Post by joshuahoover on 2010-05-13
> **Amzer zo said:**
> I tagged a couple of folders under my home directory (Ubuntu 10.04) but I don't see any emblems anymore (they were showing initially first time I tagged them) on these folders despite the files being correctly sent to the cloud.  Only the "Ubuntu One" folder has the "ubuntuone-unsynchronized" emblem showing.

Do you mean none of the files or folders inside the folder your syncing are showing the Ubuntu One emblems? Or do you mean the folder you selected to sync with Ubuntu One isn't showing the emblem? The folder you select to sync won't show an emblem. We'll need to fix/update this, but all the folders and files inside the folder should display the emblems.

> I am also trying to tag another folder (still in /home/user) and the right-click shows the "Synchronize on Ubuntu One" entry but nothing happens when trying to activate it.

How can I make sure the emblems are present and reflect correctly the sync'ing status?

When you say, "nothing happens when trying to activate it", do you mean the files in that folder don't get the Ubuntu One emblems on them and the right-click menu doesn't change to "Stop synchronizing on Ubuntu One" when you right-click on it again? This should work. Please make sure you have the latest updates and then run the following from a terminal session: u1sdtool -d; u1sdtool --start; u1sdtool -c;

Thanks,

Joshua

---

### Post by Amzer zo on 2010-05-14
> **joshuahoover said:**
> Do you mean none of the files or folders inside the folder your syncing are showing the Ubuntu One emblems? Or do you mean the folder you selected to sync with Ubuntu One isn't showing the emblem? The folder you select to sync won't show an emblem. We'll need to fix/update this, but all the folders and files inside the folder should display the emblems.

No only the folder is not showing the emblem, the files underneath do have the expected emblem.

> **joshuahoover said:**
> When you say, "nothing happens when trying to activate it", do you mean the files in that folder don't get the Ubuntu One emblems on them and the right-click menu doesn't change to "Stop synchronizing on Ubuntu One" when you right-click on it again? This should work. Please make sure you have the latest updates and then run the following from a terminal session: u1sdtool -d; u1sdtool --start; u1sdtool -c;

Correct the right click does not make it toggle to "Stop synchronizing on Ubuntu One".

After running the commands in a terminal, it makes the menu entry appear as "Stop synchronizing on Ubuntu One" (as one would expect) but it's grey'ed out (maybe because it's in the process of sync'ing the folder?)

---

### Post by duanedesign on 2010-05-14
If I ever want to monitor the progress of my Ubuntu One sync I will open a Terminal (Applications > Accessories > Terminal) and run the command.

```
tail -fn 50 ~/.cache/ubuntuone/log/syncdaemon.log
```

This will give you a pretty good idea of what is going on as information is written to the syncdaemon.log

Some other commands I use:
Monitor meta or content information. Get the number of items. Run again later to see if number has gone down.

```
u1sdtool --waiting-meta | wc
```
or
```
u1sdtool --waiting-content | wc
```

--waiting-meta and --waiting-content should progress like this:

```
duanedesign@duanedesign-laptop:~$ u1sdtool --waiting-meta | wc
     27     105    4130
duanedesign@duanedesign-laptop:~$ u1sdtool --waiting-meta | wc
     26      98    3874
duanedesign@duanedesign-laptop:~$ u1sdtool --waiting-meta | wc
     23      86    3391
duanedesign@duanedesign-laptop:~$ u1sdtool --waiting-meta | wc
      4      10     354
duanedesign@duanedesign-laptop:~$ u1sdtool --waiting-meta | wc
      1       3     129
duanedesign@duanedesign-laptop:~$ u1sdtool --waiting-meta | wc
      0       0       0
duanedesign@duanedesign-laptop:~$ 

```
-
-

---

