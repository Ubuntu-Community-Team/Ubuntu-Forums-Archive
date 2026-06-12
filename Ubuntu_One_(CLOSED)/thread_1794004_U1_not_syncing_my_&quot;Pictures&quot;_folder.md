---
title: "U1 not syncing my &quot;Pictures&quot; folder"
date: 2011-06-30
forum: Ubuntu One (CLOSED)
---

### Post by Kruger2147 on 2011-06-30
I switched my U1 account yesterday, which caused some issues, AUTH_FAILURE and ROOT_MISMATCH, I managed to fix them, I still have 1 issue though. my Pictures folder won't sync. It keeps telling me that I cant sync it because one or more folders are already synced. But that can't be since this is a new U1 account and I've never synced with it before. So I thought I would make a temp folder and move all my my pictures over, then move them back 1 by 1 to try and figure out where the problem was. Now my Pictures folder is empty and it still wont let me sync it because "one or more folders that are already synchronised"

I've tried removing my computer from my Synced Machines list. I've gone to the U1 website and removed all my synced files, then added my comp again and resynced everything. Still cant sync my Pictures folder. 

What do I do? how do I fix this?

---

### Post by duanedesign on 2011-07-06
Could you please run the following command in a Terminal:

```
u1sdtool --list-folders

```
This will list all the folders you are syncing with Ubuntu One. Is your Pictures folder listed? Is the value subscribed=True?

thank you,
duanedesign

---

