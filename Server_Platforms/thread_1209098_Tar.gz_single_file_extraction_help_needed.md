---
title: "Tar.gz single file extraction help needed"
date: 2009-07-09
forum: Server Platforms
---

### Post by archangel2021 on 2009-07-09
Hi, first post ever here  ( first time needed, since i've googled about everything else and found it here somewhere )

I'm sure it's been asked a dozen times, but I just can't get it to work.

I'm trying to extract a single file out of a tar.gz file and not to even save my life i can't get it to work. Tried a series of recommendations from others posts but nothing works.

this is where i'm at.

I've tried 

tar x /wordpress/wp-settings.php -zvft ./wordpress-2.8.1.tar.gz -C /extract2/      

which in my mind means that i want to extract the file called wp-settings.php from the folder wordpress which resides tarballed inside wordpress-2.8.1.tar.gz and in top of that have it be extract to a folder in the same level called extract2

so basically we have this:

ill paste an ls -l

root [~/public_html/ipc]# ls -lh
total 2.9M
drwxr-xr-x  10 crystaq3 crystaq3 4.0K Jul  9 20:29 ./
drwxr-xr-x  33 crystaq3 crystaq3 4.0K Jul  9 19:59 ../
drwxr-xr-x   2 crystaq3 crystaq3 4.0K Jul  9 20:29 extract2/
-rw-r--r--   1 crystaq3 crystaq3 2.0M Jul  9 19:56 wordpress-2.8.1.tar.gz
root [~/public_html/ipc]# 

when i run my command i get this:

tar x /wordpress/wp-settings.php -zvft ./wordpress-2.8.1.tar.gz -C /extract2/    
tar: t: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /wordpress/wp-settings.php: Not found in archive
tar: ./wordpress-2.8.1.tar.gz: Not found in archive
tar: Error exit delayed from previous errors


i tried flipping the source tar and folders around but it doesn't change the error..

so i must be missing something more " core " 


Any helps appreciated. Thanks!

( sorry if its a long post, tried to make it as precise as possible -and short- )

---

### Post by sdlynx on 2009-07-09
through the file browser you can open and read the archive and extract the particular file you want.  Hooray for the GUI! lol

---

### Post by archangel2021 on 2009-07-12
> **sdlynx said:**
> through the file browser you can open and read the archive and extract the particular file you want.  Hooray for the GUI! lol


..... hmmm. Thanks?

I'm trying to do this over ssh because the server i am on... is remote, and I don't have a gui to it.

anybody else ?

---

### Post by ~sHyLoCk~ on 2009-07-12
Try using "tar -x" and not "tar x"

---

### Post by sdlynx on 2009-07-12
> **archangel2021 said:**
> ..... hmmm. Thanks?

I'm trying to do this over ssh because the server i am on... is remote, and I don't have a gui to it.

anybody else ?

oh haha sorry...

---

### Post by jerome1232 on 2009-07-12
Pretty sure you just do this, my Linux machine is going through a release update process so I can't create a test archive to test it.

```
tar xzfv archiveName fileNameToBeExtracted -C destination
```

---

