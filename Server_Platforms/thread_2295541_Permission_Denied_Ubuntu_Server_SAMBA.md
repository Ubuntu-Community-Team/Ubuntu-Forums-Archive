---
title: "Permission Denied Ubuntu Server SAMBA"
date: 2015-09-19
forum: Server Platforms
---

### Post by nathanhawthorne12 on 2015-09-19
Evening folks

I have Ubuntu Server running PLEX, SAMBA and SSH.  I have setup 2 folders Backup & Movies.  When i create a folder on either its fine, but when i try to copy over a file or create a new file i get permission denied.

smb.conf
```

#======================= Share Definitions =======================

[Movies]
        path = /srv/Samba/Movies
        writable = yes
        guest ok = yes
        guest only = yes
        create mode = 0777
        directory mode = 0777


[Backup]
        path = /srv/Samba/Backup
        writable = yes
        guest ok = yes
        guest only = yes
        create mode = 0777
        directory mode = 0777


```

Folder permission
```


drwxrwxrwx 2 nobody nogroup 4096 Sep 19 18:04 Backup
drwxrwxrwx 2 nobody nogroup 4096 Sep 19 18:07 Movies


```

Fstab on my Opensuse for auto mounting server name blanked out on purpose :)

```


//****/Movies /mnt/Movies cifs defaults,guest 0 0
//****/Backup /mnt/Backup cifs defaults,guest 0 0



```


Any help would be appreciated

---

### Post by alxhoff-d on 2015-09-22
I had a similar problem a while ago and if i remember correctly I had issues with the default file permissions. 

This thread and the one it references really helped me.

[http://unix.stackexchange.com/questions/1314/how-to-set-default-file-permissions-for-all-folders-files-in-a-directory](http://unix.stackexchange.com/questions/1314/how-to-set-default-file-permissions-for-all-folders-files-in-a-directory)

I also move onto webmin for managing my samba shares and found they usually worked a lot better when managing permissions.

Hope this helps

---

