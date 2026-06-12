---
title: "Can't delete folder - does not exist?"
date: 2010-11-14
forum: Ubuntu One (CLOSED)
---

### Post by SmileyCactus on 2010-11-14
I accidently selected the wrong folder to sync with ubuntu one. It has now added .u1conflict to all my files (around 8000 of them :mad: ) and now I can't stop the folder syncing. I've followed these instructions 
[https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIStopSyncingAFolderOutsideTheUbuntuOneFolder]("https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIStopSyncingAFolderOutsideTheUbuntuOneFolder")

This just returns an error:
```
FolderDeleteError: DOES_NOT_EXIST (subscribed=, suggested_path=~/Music, generation=, 
node_id=dc8be355-c4dc-4111-9650-b4744aeae2a4, volume_id=1897e926-212b-424e-87ee-a8e87b80cd05, 
path=/home/brent/Music, type=UDF)

```

Is there any way to stop this?!?

---

### Post by max127 on 2010-11-14
Are you joking or serious.

---

### Post by SmileyCactus on 2010-11-14
> **max127 said:**
> Are you joking or serious.

Why would I be joking?

---

### Post by SmileyCactus on 2010-11-17
bump

Anyone?

---

### Post by mitchroberts on 2010-11-17
I fixed this problem last night on my ubuntu one with some help from the support staff at ubuntu one.Your syncing a folder outside ubuntu one and let me guess you have deleted that folder from your computer thats what i did if that is what you did then it's easy to fix.First you need to make the folder or folders again just like you had them so go to your ubuntu one account from firefox now open go to the files tab the name and location should be in there.Now go to the location and recreate the folder then make sure ubuntu one is connected to the internet then from the terminal

> u1sdtool --list-folders 
then you should have something like this
> Folder list:
  id=[COLOR="Red"]b5fa78b0-e27e-4185-8f33-4626cbebe172[/COLOR] subscribed=True path=/home/mitch/Music
now do this
> u1sdtool --quit
and now
> u1sdtool --start
copy the id from the terminal and make it look like this

> u1sdtool --delete-folder=[COLOR="Red"]b5fa78b0-e27e-4185-8f33-4626cbebe172[/COLOR]

the red is my id you will need to replace it with what you id is

---

