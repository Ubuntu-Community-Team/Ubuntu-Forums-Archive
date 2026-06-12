---
title: "Mount Sub-dir with different permissions"
date: 2014-11-21
forum: Server Platforms
---

### Post by Jonny87 on 2014-11-21
I need to mount a sub-dir of an already mounted dir to a new location with different permissions, but I cant work out how to set up fstab to do so.

I have;
```
/media/Library           jonny:jonny
/media/Library/Dir1    jonny:jonny
```

I want to have Dir1 remounted with different permissions so I will have something like the following;
```
/media/Library           jonny:jonny
/media/Library/Dir1    jonny:jonny

/media/Dir1             www-data:www-data
```

Is this possible?

---

### Post by volkswagner on 2014-11-21
Perhaps it would be best to explain why you want to do this and why you prefer to use mount as the mechanism to accomplish your goal.

---

### Post by Jonny87 on 2014-11-21
The entire /media/Library is shared to my local network via samba. But the Dir I want to remount /media/Library/Dir1, I want to have accessible to ownCloud.

ownCloud requires that the dir permissions are www-data:www-data but if I change Dir one to that I cant access it from samba.

As for using mount, I just thought it would be the best method. If anyone else has a better way of accomplishing this, I'm open to hear it.

---

### Post by Jonny87 on 2014-11-22
K heres an idea I've had;
What if I add my user "jonny" to the group of www-data,
Mount /media/Library with www-data:www-data ownership,
Then as i'm now a member of www-data I try and share it via samba.

Any one have any ideas on this?

---

### Post by volkswagner on 2014-11-23
Using file permissions and groups would be a good method.
What version of SAMBA are you using?
If you add users to group www-data, you'll just need to be sure folders & files are writeable by the group.

You can also force samba to use the group and owner when users create files.

You can run some tests one directory deep by manually setting owner:group. If all works as expectd
you modify the following commands to change permissions for files and directories.

```
# To recursively set permissions only on directories!
sudo find /path/to/base/dir -type d -print0 | xargs -0 chmod 775 


# To recursively set permissions only on files!
sudo find /path/to/base/dir -type f -print0 | xargs -0 chmod 664 
```

You can also modify the above for "chgrp www-data"

---

