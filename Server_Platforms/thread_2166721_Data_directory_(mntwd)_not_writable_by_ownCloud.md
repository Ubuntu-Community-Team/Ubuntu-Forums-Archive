---
title: "Data directory (/mnt/wd) not writable by ownCloud"
date: 2013-08-10
forum: Server Platforms
---

### Post by donniezazen on 2013-08-10
Hello,

I am trying out a setup explained [here]("http://blog.bittorrent.com/2013/05/23/how-i-created-my-own-personal-cloud-using-bittorrent-sync-owncloud-and-raspberry-pi/").

I want to use ownCloud to make my external hard drive accessible over web.

I mount external hard drive using fstab.
```

# WD Mount
UUID=xxxxxxxxxxxxxxxxxxxxx	/mnt/wd		ext4	defaults,noatime,nofail		0	2
```

I have added myself to www-data and changed /mnt/wd to 770
```

sudo usermod -a -G www-data $USER
sudo chmod -R 770 /mnt/wd
```

I use this external drive for backup, torrenting, subsonic, plex, media center, etc.. Transmission daemon requires folder is owned by debian-transmission group and has a permission of 775. Plex recommends 755 for folder and 644 for files. I do 1:1 mirror back of my laptop and would like to preserve file permissions.

How should I solve this problem?

Thanks.

---

### Post by sandyd on 2013-08-11
> **donniezazen said:**
> Hello,

I am trying out a setup explained [here]("http://blog.bittorrent.com/2013/05/23/how-i-created-my-own-personal-cloud-using-bittorrent-sync-owncloud-and-raspberry-pi/").

I want to use ownCloud to make my external hard drive accessible over web.

I mount external hard drive using fstab.
```

# WD Mount
UUID=xxxxxxxxxxxxxxxxxxxxx	/mnt/wd		ext4	defaults,noatime,nofail		0	2
```

I have added myself to www-data and changed /mnt/wd to 770
```

sudo usermod -a -G www-data $USER
sudo chmod -R 770 /mnt/wd
```

I use this external drive for backup, torrenting, subsonic, plex, media center, etc.. Transmission daemon requires folder is owned by debian-transmission group and has a permission of 775. Plex recommends 755 for folder and 644 for files. I do 1:1 mirror back of my laptop and would like to preserve file permissions.

How should I solve this problem?

Thanks.
The www-data user still doesn't have access to the folder - the folder is owned by debian-transmission.

The only users who have permission to access the folder are debian-transmission, because you have set the permissions to 770, which mainly means that only the owner (debian-transmission), and the group (debian transmission?) would be able to write to it, as the first digit represents the owner's permissions, the second digit represents the group's permissions, and the last digit represents the group permissions


Few things you can do -
 - Add permissions for all other users so any user can access the folder 
```

chmod -R 777 /mnt/wd
```
- Create a new group, add the users (is debian-transmission a group or user?) to the group, and do a 
```
chown -R debian-transmission:groupnamehere /mnt/wd
```
- Change the user/group that transmission/plex runs in - you can basically create a new group, and add the plex/transmission users to the group
and do a
```

chown -R www-data:newgroupname /mnt/wd
chmod 2770 /mnt/wd
```

---

