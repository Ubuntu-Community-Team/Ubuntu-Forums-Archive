---
title: "Samba and Raid Drives - Ubuntu 18.04 TLS"
date: 2018-07-19
forum: Server Platforms
---

### Post by milesdecolwell on 2018-07-19
I have just installed Ubuntu 18.04 TLS on an old box. The OS is on a standard drive and I have also mounted a RAID 5 setup.
I want to the raid drive available as a Samba share but seem to be having permission issues.

I have Samba working and a public directory on the non-RAiD drive working.
The Raid dir seem to be exactly the same, see below.

However when trying to access it
[ATTACH=CONFIG]280453[/ATTACH]

I get a permission error;

Samba Config;

[ATTACH=CONFIG]280454[/ATTACH]

Working public share
[ATTACH=CONFIG]280455[/ATTACH]

RAID Drive
[ATTACH=CONFIG]280456[/ATTACH]

The Raid drive Samba share Storage shows up as a windows share, it's just not accessible.

Any ideas?

thanks in advance

---

### Post by slickymaster on 2018-07-19
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2018-07-20
I suggest you create mountpoint for samba shares, something like /sambashares. Then you can create directory storage inside and mount the raid5 array at /sambashares/storage. Using system folders like /media is not a good idea.
For a user to be able to access it it has to have permissions along the path to the folder I believe. In your case I think guest user nobody has no permissions on /media. Try something else for the location and let us know.

And don't use file create mask as 777, that will always create executable files. Files rarely need to be executable. Don't give more permissions than ypu need to...

---

### Post by Morbius1 on 2018-07-20
You cannot have a "force user = nobody" in your share definition because the path to the share is:
> /media/gryphon/bunch-of-numbers/stroage
gryphon is a user name and Linux limit's only that user to traverse the /media/gryphon folder to get to what is past it. This is by design.

Change the mount point to something one level up ( /media/bunch-of-numbers/storage ) or under /srv or /sambashares as darkod suggested.

OR: change the force user to:
```
force user = gryphon
```

---

