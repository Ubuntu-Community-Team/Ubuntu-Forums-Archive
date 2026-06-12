---
title: "Lost permission to a certain folder"
date: 2015-01-08
forum: Security
---

### Post by pingaan on 2015-01-08
Hi,

Without logging into Windows 7, I've lost permission in my folder "c:\Users\pingaan" which from Ubuntu would be "/mnt/windows7/Users/pingaan".
I don't know what to do! I really need to access this at all times...

I've tried various of values with chmod but no luck.. And if it would be some issues from within Windows 7, where do I go from here?

Regards.

---

### Post by Al1000 on 2015-01-08
Hi pingaan,

What's the output of:

```
ls -l /mnt/windows7/Users/pingaan
```

?

---

### Post by bab1 on 2015-01-08
> **pingaan said:**
> Hi,

Without logging into Windows 7, I've lost permission in my folder "c:\Users\pingaan" which from Ubuntu would be "/mnt/windows7/Users/pingaan".
I don't know what to do! I really need to access this at all times...

I've tried various of values with chmod but no luck.. And if it would be some issues from within Windows 7, where do I go from here?

Regards.
Windows partitions are mostly NTFS and as such have no provision for Linux chmod.  In fact chmod is not what you want anyway.  You need to set the ownership and the permissions of the partitions.  You can ONLY set the ownership and permissions at mount time.

Is this share mounted via fstab? Did try remounting the share?

---

### Post by pingaan on 2015-01-09
```

 $ sudo ls -l /mnt/windows7/Users/pingaan/
 total 2661
drwx------ 1 root root       0 feb  1  2013 AppData
lrwxrwxrwx 2 root root     156 feb  1  2013 Application Data -> /mnt/windows7/Users/pingaan/AppData/Roaming
drwx------ 1 root root       0 okt  5 09:19 Contacts
lrwxrwxrwx 1 root root     260 feb  1  2013 Cookies -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Cookies
drwx------ 1 root root    4096 dec  6 12:06 Desktop
drwx------ 1 root root    4096 dec  6 12:06 Documents
drwx------ 1 root root    8192 okt  5 09:19 Downloads
drwx------ 1 root root   12288 jan  2 14:52 Dropbox
drwx------ 1 root root    4096 okt  5 09:19 Favorites
drwx------ 1 root root    4096 okt  5 09:19 Links
lrwxrwxrwx 2 root root     148 feb  1  2013 Local Settings -> /mnt/windows7/Users/pingaan/AppData/Local
drwx------ 1 root root       0 okt  5 09:19 Music
lrwxrwxrwx 2 root root     132 feb  1  2013 My Documents -> /mnt/windows7/Users/pingaan/Documents
lrwxrwxrwx 1 root root     300 feb  1  2013 NetHood -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Network Shortcuts
-rwx------ 1 root root 1310720 dec 29 13:37 NTUSER.DAT
 -rwx------ 2 root root   65536 feb  1  2013 NTUSER.DAT{016888bd-6c6f-11de-8d1d-001e0bcde3ec}.TM.blf
 -rwx------ 2 root root  524288 feb  1  2013 NTUSER.DAT{016888bd-6c6f-11de-8d1d-001e0bcde3ec}.TMContainer00000000000000000001.regtrans-ms
-rwx------ 2 root root  524288 feb  1  2013 NTUSER.DAT{016888bd-6c6f-11de-8d1d-001e0bcde3ec}.TMContainer00000000000000000002.regtrans-ms
 -rwx------ 2 root root  262144 dec 29 13:37 ntuser.dat.LOG1
 -rwx------ 2 root root       0 feb  1  2013 ntuser.dat.LOG2
-rwx------ 1 root root      20 feb  1  2013 ntuser.ini
drwx------ 1 root root       0 okt  5 09:19 Pictures
lrwxrwxrwx 2 root root     300 feb  1  2013 PrintHood -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Printer Shortcuts
lrwxrwxrwx 1 root root     256 feb  1  2013 Recent -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Recent
drwx------ 1 root root       0 okt  5 09:19 Saved Games
drwx------ 1 root root       0 okt  5 09:19 Searches
lrwxrwxrwx 1 root root     256 feb  1  2013 SendTo -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/SendTo
lrwxrwxrwx 2 root root     272 feb  1  2013 Start Menu -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Start Menu
lrwxrwxrwx 2 root root     268 feb  1  2013 Templates -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Templates
drwx------ 1 root root       0 dec 29 12:39 Videos
drwx------ 1 root root       0 feb  7  2013 VirtualBox VMs
 
```

 bab1: OK, good to know about the NTFS mounts and chmod. Did try to remount but it's busy; unable to umount it...
I did recently add my drives to fstab but I am able to access the whole disk, read/write. It's just that folder where permissions fail.
fstab line: 
```

UUID=3C14BEAA14BE6694 /mnt/windows7 ntfs-3g permissions,auto 0 0

```

---

### Post by bab1 on 2015-01-09
> **pingaan said:**
> ```

 $ sudo ls -l /mnt/windows7/Users/pingaan/
 total 2661
drwx------ 1 root root       0 feb  1  2013 AppData
lrwxrwxrwx 2 root root     156 feb  1  2013 Application Data -> /mnt/windows7/Users/pingaan/AppData/Roaming
drwx------ 1 root root       0 okt  5 09:19 Contacts
lrwxrwxrwx 1 root root     260 feb  1  2013 Cookies -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Cookies
drwx------ 1 root root    4096 dec  6 12:06 Desktop
drwx------ 1 root root    4096 dec  6 12:06 Documents
drwx------ 1 root root    8192 okt  5 09:19 Downloads
drwx------ 1 root root   12288 jan  2 14:52 Dropbox
drwx------ 1 root root    4096 okt  5 09:19 Favorites
drwx------ 1 root root    4096 okt  5 09:19 Links
lrwxrwxrwx 2 root root     148 feb  1  2013 Local Settings -> /mnt/windows7/Users/pingaan/AppData/Local
drwx------ 1 root root       0 okt  5 09:19 Music
lrwxrwxrwx 2 root root     132 feb  1  2013 My Documents -> /mnt/windows7/Users/pingaan/Documents
lrwxrwxrwx 1 root root     300 feb  1  2013 NetHood -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Network Shortcuts
-rwx------ 1 root root 1310720 dec 29 13:37 NTUSER.DAT
 -rwx------ 2 root root   65536 feb  1  2013 NTUSER.DAT{016888bd-6c6f-11de-8d1d-001e0bcde3ec}.TM.blf
 -rwx------ 2 root root  524288 feb  1  2013 NTUSER.DAT{016888bd-6c6f-11de-8d1d-001e0bcde3ec}.TMContainer00000000000000000001.regtrans-ms
-rwx------ 2 root root  524288 feb  1  2013 NTUSER.DAT{016888bd-6c6f-11de-8d1d-001e0bcde3ec}.TMContainer00000000000000000002.regtrans-ms
 -rwx------ 2 root root  262144 dec 29 13:37 ntuser.dat.LOG1
 -rwx------ 2 root root       0 feb  1  2013 ntuser.dat.LOG2
-rwx------ 1 root root      20 feb  1  2013 ntuser.ini
drwx------ 1 root root       0 okt  5 09:19 Pictures
lrwxrwxrwx 2 root root     300 feb  1  2013 PrintHood -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Printer Shortcuts
lrwxrwxrwx 1 root root     256 feb  1  2013 Recent -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Recent
drwx------ 1 root root       0 okt  5 09:19 Saved Games
drwx------ 1 root root       0 okt  5 09:19 Searches
lrwxrwxrwx 1 root root     256 feb  1  2013 SendTo -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/SendTo
lrwxrwxrwx 2 root root     272 feb  1  2013 Start Menu -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Start Menu
lrwxrwxrwx 2 root root     268 feb  1  2013 Templates -> /mnt/windows7/Users/pingaan/AppData/Roaming/Microsoft/Windows/Templates
drwx------ 1 root root       0 dec 29 12:39 Videos
drwx------ 1 root root       0 feb  7  2013 VirtualBox VMs
 
```

 bab1: OK, good to know about the NTFS mounts and chmod. Did try to remount but it's busy; unable to umount it...
I did recently add my drives to fstab but I am able to access the whole disk, read/write. It's just that folder where permissions fail.
fstab line: 
```

UUID=3C14BEAA14BE6694 /mnt/windows7 ntfs-3g permissions,auto 0 0

```

As you can clearly see the directories will only allow root to access (root:root and 700).  You can read all about mount.ntfs (man mount.ntfs) but the most important part is this```
OPTIONS
       Below is a summary of the options that ntfs-3g accepts.

       uid=value and gid=value
              Set the owner and the group of files and directories. The values are numerical.  The defaults are the uid  and  gid
              of the current process.

       umask=value
              Set  the   bitmask  of  the  file  and directory permissions that are not present. The value is given in octal. The
              default value is 0 which means full access to everybody.

       fmask=value
              Set the  bitmask of the file permissions that are not present.  The value is given in octal. The default value is 0
              which means full access to everybody.

       dmask=value
              Set  the  bitmask of the directory permissions that are not present. The value is given in octal. The default value
              is 0 which means full access to everybody.


```

If you are the only user on the machine then use *uid=1000* and *gid=1000* for ownership and *umask=002* for permissions.  Here is an example you can follow: [http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab]("http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab")

---

### Post by pingaan on 2015-01-10
I Always found building my own fstab hard.. Thanks for the Quick response! <3
Should the new fstab line look like this:
```

UUID=3C14BEAA14BE6694 /mnt/windows7 ntfs-3g uid=1000,gid=1000,umask=002,auto 0 0

```

Cheers.

---

### Post by bab1 on 2015-01-10
> **pingaan said:**
> I Always found building my own fstab hard.. Thanks for the Quick response! <3
Should the new fstab line look like this:
```

UUID=3C14BEAA14BE6694 /mnt/windows7 ntfs-3g uid=1000,gid=1000,umask=002,auto 0 0

```

Cheers.

Yes I would use that line in fstab.  Post back here that the ownership and permissions are correct.  If not we will make the adjustments and remount it again.

---

### Post by pingaan on 2015-01-13
Worked like a charm! Thanks alot, BAB!

---

### Post by pingaan on 2015-01-14
OK, Another issue! =P
I can access it via Samba, just like Before, only diffrence is that I can't write files to the drive. What do I need to add to fstab to be able to do this?

Cheers.

Edit: umask=000 did the trick... Thanks again! :)

---

