---
title: "Using Nautilus Actions + shell script for syncing of any file / folder"
date: 2010-03-19
forum: Ubuntu One (CLOSED)
---

### Post by aeriph on 2010-03-19
I'm sure it is possible to use a shell script via Nautilus Actions to have a right click -> "sync on Ubuntu One" function.

I've tried to do this but haven't got it working properly.

The shell script is:
```

#!/bin/bash
mv $1 ~/Ubuntu\ One/$1
ln -s --target-directory=$2 ~/Ubuntu\ One/$1
```

where $1 is the name of the file (%f in nautilus actions) and $2 is the path to the file (%d in nautilus actions).

This works fine for files and folders in the home directory (~) but when used on files elsewhere, e.g. ~/folder/, it seems to create a symlink in the home folder (i.e. ~/link) and do nothing else.

Sorry if this has been covered before, I couldn't find anything similar in search.

Thanks a lot

---

### Post by zekopeko on 2010-03-21
I don't think U1 follows symlinks.I could be wrong.

You will be glad to know that in Lucid U1 allows you to sync any folder.

---

### Post by joshuahoover on 2010-03-22
> **zekopeko said:**
> I don't think U1 follows symlinks.I could be wrong.

You will be glad to know that in Lucid U1 allows you to sync any folder.

This is correct. If you install the latest version of Lucid, you will now be able to right-click on a folder in Nautilus and select "Synchronize on Ubuntu One". And, no, this is not currently documented anywhere but we'll be fixing that very shortly. :)

Thanks!

Joshua

---

### Post by Vrekk on 2010-03-22
> **joshuahoover said:**
> This is correct. If you install the latest version of Lucid, you will now be able to right-click on a folder in Nautilus and select "Synchronize on Ubuntu One". And, no, this is not currently documented anywhere but we'll be fixing that very shortly. :)

Thanks!

Joshua

When you do this, how do you make that folder show up on the other clients? When I do that, the file shows up online but not on my other computers.

---

### Post by iansyngin on 2010-03-23
> **joshuahoover said:**
> This is correct. If you install the latest version of Lucid, you will now be able to right-click on a folder in Nautilus and select "Synchronize on Ubuntu One". And, no, this is not currently documented anywhere but we'll be fixing that very shortly. :)

Thanks!

Joshua

Im using Jaunty Jackalope and if i right click on a folder within Nautilus, i have the option the synchronize with Ubuntu One. I haven't actually tested if this works but the option is there all the same.

Ian

---

### Post by juancarlospaco on 2010-03-23
NVM Lucid can do that with built-in Nautilus

---

### Post by joshuahoover on 2010-03-23
> **Vrekk said:**
> When you do this, how do you make that folder show up on the other clients? When I do that, the file shows up online but not on my other computers.

Are your other clients Lucid as well? If you have Karmic clients using the Ubuntu One packages in main, then these clients won't see the folders outside of ~/Ubuntu One. To get that capability on Karmic you'd need to install our beta PPA: [https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)

If all your clients are Lucid and/or the beta PPA, you may need to disconnect/connect the Ubuntu One client to force a sync.

Thank you,

Joshua

---

### Post by duanedesign on 2010-03-23
> **zekopeko said:**
> I don't think U1 follows symlinks.I could be wrong.


You are correct.
However it does work the other way around. Put the folder in /Ubuntu\ One and the symlink where the folder was.

---

### Post by claudio87 on 2010-05-02
> **joshuahoover said:**
> This is correct. If you install the latest version of Lucid, you will now be able to right-click on a folder in Nautilus and select "Synchronize on Ubuntu One". And, no, this is not currently documented anywhere but we'll be fixing that very shortly. :)

Thanks!

Joshua

And it works flawlessly :)) good work!
But it works only in folders in the home directory.
I have a different partition where I store music and photos...right clicking on a folder in /media/data does not show the "Sync with UbuntuONE" menu entry.
Is it normal?

Thanks.

---

### Post by joshuahoover on 2010-05-03
> **claudio87 said:**
> And it works flawlessly :)) good work!
But it works only in folders in the home directory.
I have a different partition where I store music and photos...right clicking on a folder in /media/data does not show the "Sync with UbuntuONE" menu entry.
Is it normal?

Thanks.

Yes, right now it's limited to your home folder. I'm not sure we're looking to expand beyond this but if we do, we'll be sure to announce it in a blog post: [http://voices.canonical.com/ubuntuone/](http://voices.canonical.com/ubuntuone/)

Thank you,

Joshua

---

