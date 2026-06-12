---
title: "How to synchronize other folders ?"
date: 2009-10-31
forum: Ubuntu One (CLOSED)
---

### Post by desperado666 on 2009-10-31
HI

I wonder how to keep documents, my music, and videos folder synchronized with Ubuntu One ? 

Anyone got an idea ?

---

### Post by Irishpolyglot on 2009-11-01
I want to know this too; I can't move everything I want into the default folder. There should be an option (according to some tutorials I've seen online) of right clicking any folder and "Share on Ubuntuone" being in the menu. It's not.
How can we enable this? It's a pity it doesn't come enabled as default (at least on my system). I've set up an account and it's working fine in the default folder.

---

### Post by King of Heart 4711 on 2009-11-01
Make a symbolic link possibly.

---

### Post by damnick on 2009-11-01
> **King of Heart 4711 said:**
> Make a symbolic link possibly.

No symbolic links will not work.
Only hard links will work.
I have read that the ubuntuone team will add this feature in the future.

---

### Post by desperado666 on 2009-11-01
future future future...i want it now :D

---

### Post by paxmark1 on 2009-11-05
Possible work around.  No, not really.  The name needs  \ slashes at the command line due to the space in Ubuntu one.  Reminds me of windows.  I did the total purge of Ubuntu one. 

I have two folders in ~/home   say ~/mud and ~/dog

I add new folders  named mud and dog to Ubuntu one.  (mkdir dog)

And then I use the unison-gtk to perform synchronizations  between ~/dog and ~/Ubuntu\ one/dog    and also    between     ~/mud  and ~/Ubunutu\ one/mud

Didn't work well for me.  

Then the daemon will awaken and synchronize up with the cloud.  


Not elegant but workable for another backup for 2 gb of data.  


I am not abandoning my Chicago b/up site that I have bash rsync -ssh scripts for  (unless you can tell me of a good one in Canada)/

Side question, in what country does the Amazon cloud that Ubuntu pays for actually exist and is there platinum clad guarantees that they will not release the data to anyone under any circumstances?

---

### Post by sombrancelha on 2009-11-07
Can you provide me with a howto for unison-gtk?

Thanks!

EDIT: found out how to use it

---

### Post by josteinaj on 2009-11-07
To synchronize my Photos, Music, Documents etc. folders, I simply moved them into the Ubuntu One folder and made symlinks to them from my home folder. I do this on all my computers. So;

~/Photos -> ~/Ubuntu One/Photos
~/Documents -> ~/Ubuntu One/Documents
~/Music -> ~/Ubuntu One/Music
~/Video -> ~/Ubuntu One/Video

It's not an ideal solution, but it seems to work as it should.

---

### Post by paxmark1 on 2009-11-08
for what it is worth   Unison hints and info
[http://en.wikipedia.org/wiki/Unison_(file_synchronizer](http://en.wikipedia.org/wiki/Unison_(file_synchronizer))

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

     (Note, there is another Unison with more google hits than the child of rsync)

man unison

[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html)

and 

[http://www.linuxjournal.com/article/7712](http://www.linuxjournal.com/article/7712)

---

### Post by joshuahoover on 2009-11-09
> **josteinaj said:**
> To synchronize my Photos, Music, Documents etc. folders, I simply moved them into the Ubuntu One folder and made symlinks to them from my home folder. I do this on all my computers. So;

~/Photos -> ~/Ubuntu One/Photos
~/Documents -> ~/Ubuntu One/Documents
~/Music -> ~/Ubuntu One/Music
~/Video -> ~/Ubuntu One/Video

It's not an ideal solution, but it seems to work as it should.

This is probably the best you can do right now. We hope to provide the ability to define which folders you want to sync and/or support symlinks properly in the Lucid release cycle. 

Thank you,

Joshua

---

### Post by oliv66 on 2009-11-10
there is an easy way with a nautilus script ready to use.

so, you have to install nautilus script + download ubuntu one script avaibable.

Olivier

---

### Post by desperado666 on 2009-11-14
Link ?

---

### Post by oliv66 on 2009-11-14
the link I have is in French (I guess not useful for you) but please find below the script very easy to write with any editor

name it ubuntu_one for instance

```
#!/bin/bash

cp -r $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ~/Ubuntu\ One/

```

You must put your script (do not forget to make it executable via chmod a+x ubuntu_one in  

```
~/.gnome2/nautilus-scripts
```. 

please find a site in English about nautilus script.
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

installing nautilus script is very easy via Synaptic.

Then you can choose to send any file to Ubuntu One via a right click.

Hope it helps,

---

### Post by DouglasAdams on 2010-02-24
i am new to Ubuntu & Linux so please don't shoot me
but
i was looking at the mount command and found this:

The bind mounts.
Since Linux 2.4.0 it is possible to remount  part  of  the  file
hierarchy somewhere else. The call is
                     mount --bind olddir newdir
                             (and the recursive rbind)
or fstab entry:
                     /olddir  /newdir  none  bind

could this command, probably in fstat, not be used to equate the one file system to anything, even /home
if i'm wrong i would really appreciate knowing what's wrong with my understanding of this command.

---

### Post by kyleabaker on 2010-02-25
> **joshuahoover said:**
> This is probably the best you can do right now. We hope to provide the ability to define which folders you want to sync and/or support symlinks properly in the Lucid release cycle. 

Thank you,

Joshua
[Looks like]("http://popey.com/blog/2010/02/20/u1-music-store-store-music-in-u1/") this new feature *may* also be used for purchased music from the Ubuntu One Music Store.

If that's true, then there is a good chance that we'll have this feature. Dropbox is nearing v0.8.x which will also have this feature so the timing would be great! ...as long as the implementation is solid.

---

### Post by Maximus_ARNP on 2010-05-09
> **paxmark1 said:**
> Possible work around.  No, not really.

And then I use the unison-gtk to perform synchronizations  between ~/dog and ~/Ubuntu\ one/dog    and also    between     ~/mud  and ~/Ubunutu\ one/mud

Didn't work well for me.  



Here is a work-around that worked for me:

I used **Unison** and **Gnome-schedule** to sync a folder in the home directory with the one outside home directory. The folder in the home directory is synced with a laptop via Ubuntu One. This will require two copy of the same folder. But, space is not a problem for me. Gnome-schedule (Cron) is syncing file every 1 minute. Syncing works well bi-directionally from any one folder to other folders.

Helpful links:
[Unison configuration related:]("http://ubuntuforums.org/showthread.php?t=869219")


[Gnome-schedule configuration related]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html")

Enjoy.

---

### Post by ghosTM55 on 2010-05-11
> **joshuahoover said:**
> This is probably the best you can do right now. We hope to provide the ability to define which folders you want to sync and/or support symlinks properly in the Lucid release cycle. 

Thank you,

Joshua

Really looking forward to it :)

---

### Post by DouglasAdams on 2010-05-11
> **ghostm55 said:**
> really looking forward to it :)
lol

---

