---
title: "Need help understanding Security and ACL"
date: 2021-12-17
forum: Security
---

### Post by welefort on 2021-12-17
I have a media server that runs plex.  one option i have set is to delete files after watching.  Some shows it doesn't work on,  some it does.   I "think" I've got the issue narrowed down to a permissions issue and ACL(access control lists)


example:
```
drwxrwxrwx+   4  xxx xxx 4.0K Jun 26 12:03 'War of the Worlds (2019)'
drwxrwxrwx    2 xxx xxx4.0K Dec 14 21:54 'Watchmen (2019)'
drwxrwxrwx    2 xxx xxx4.0K Dec 14 21:54 'Weeds (2005)'
drwxrwxrwx    2 xxx xxxt 4.0K Dec 14 21:54 'Welcome to Earth (2021)'
drwxrwxrwx+   5 xxx xxx 4.0K Mar 23  2020  Westworld
drwxrwxrwx+   2 xxx xxx4.0K Nov  8 21:50 'What We Do in the Shadows'
drwxrwxrwx    2 xxx xxx 4.0K Dec 14 21:48 'Whistleblower, The (2021)412949'
drwxrwxrwx    2 xxx xxx 4.0K Dec 14 21:54 'White Collar (2009)'
drwxrwxrwx+   3 xxx xxx  4.0K Aug 22  2019 'Why Women Kill'



```

Everything with the +  will correctly delete,  everything without it,  wont.

My plex media server runs under the "plex" username.   The files are under my user account (xxx)  which is the admin account for this machine.   The files are put there by Sonarr,  which is running under docker with the GID and UID of 1000


This drive is local to the machine,  but it was at one point in a NAS.  When I moved it to this machine I chmod xxx -R to the entire thing.  Its mounted ext4  defaults.  

I can't seem to find out why some folders have that +  and some dont.

---

### Post by TheFu on 2021-12-19
The + means there are ACLs applied.  You can disable them either by using setfacl or disabling ACLs in the mount options for the file system (i.e. in the fstab).
There is no need for ACLs to allow plex, jellyfin or any other media server sufficient access to add or delete media files.  Normal Unix file and directory permissions are sufficient.  The learn how, search these forums for "chown chmod setgid working together". That should return a few posts with specific examples for allowing 3+ userids to work together in the same directories, modify, add, delete files and have any new subdirectories contain the same permissions by default.

It is all about placing the different userids into the same Unix group and setting the group setgid flag on all directories. Then normal group permissions on the directories and files are all that is needed. No ACLs necessary.

---

