---
title: "Ubuntu One support in Nautilus"
date: 2010-05-26
forum: Ubuntu One (CLOSED)
---

### Post by SteveOll on 2010-05-26
I remember using an earlier version of Ubuntu One (might have been 9.04 or 9.10) where you got a icon in the notification area on the task bar and you could open up your cloud storage location through nautilus and the whole thing seemed to work quite well.

In 10.04 is there a way of installing the earlier version of Ubuntu One as the whole affair with using the web browser to select individual files to sync/upload seems very tedious and the connection doesn't seem to work properly i.e. sync'd files are not there but the folders are up there correctly. Something doesn't 'Just Work' here.

---

### Post by kyleabaker on 2010-07-12
Are you unable to find the "Ubuntu One" folder on your computer? I may have misunderstood you, but just in case, try this:
[http://ubuntuforums.org/showthread.php?t=1528286](http://ubuntuforums.org/showthread.php?t=1528286)

---

### Post by duanedesign on 2010-07-12
> **SteveOll said:**
> I remember using an earlier version of Ubuntu One (might have been 9.04 or 9.10) where you got a icon in the notification area on the task bar and you could open up your cloud storage location through nautilus and the whole thing seemed to work quite well.

In 10.04 is there a way of installing the earlier version of Ubuntu One as the whole affair with using the web browser to select individual files to sync/upload seems very tedious and the connection doesn't seem to work properly i.e. sync'd files are not there but the folders are up there correctly. Something doesn't 'Just Work' here.

The Ubuntu One Applet was replaced by the Ubuntu One Preferences Panel. This panel can be found under Me Menu --> Ubuntu One or System --> Preferences --> Ubuntu One.

To sync files/folders you can either place them in the ~/Ubuntu One folder or you can now sync any folder in your Home directory by r-click --> 'Sync with Ubuntu One'

Are all your files synced yet? If not could you run the following command in a Terminal (Applications > Accessories > Terminal) and post the results.

```
u1sdtool -s
```

The following commands will show you how many items are waiting to be synced.

```
u1sdtool --waiting-metadata | wc -l
```
and
```
u1sdtool --waiting-content | wc -l
```

---

