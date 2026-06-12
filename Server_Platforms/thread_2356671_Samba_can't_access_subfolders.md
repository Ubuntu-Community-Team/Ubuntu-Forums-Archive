---
title: "Samba: can't access subfolders"
date: 2017-03-25
forum: Server Platforms
---

### Post by uncleo2 on 2017-03-25
My Samba server was working fine until yesterday. Now I can't access subfolders in the share from Kodi or smbclient. Windows Explorer works now, but I don't know how I fixed it.

The error message from Kodi is "Invalid Argument". Apparently, this is a pretty generic error message.

From smbclient, I can connect. I can [FONT=courier new]ls[/FONT] the top directory in the share, and can [FONT=courier new]cd[/FONT] into subdirectories as far down the tree as I want since I know their names already, but the [FONT=courier new]ls[/FONT] command doesn't work in any of these subdirectories. The error message is ```
[COLOR=#000000][FONT=monospace]NT_[/FONT][/COLOR][FONT=monospace][COLOR=#000000]STATUS_NOT_FOUND listing \junk\*[/COLOR][/FONT]
```, where junk is the name of the suddir in this example.

The output from testparm for the share is

```

[FONT=monospace][COLOR=#000000][video][/COLOR]
        comment = video
        path = /home/scott/video
        guest ok = Yes
        locking = No
        strict locking = No
[/FONT]
```

The directory permissions look correct
```

[FONT=monospace][COLOR=#000000]drwxr-xr-x  6 scott scott      24576 Mar 24 14:37 [/COLOR][COLOR=#5454FF]**.**[/COLOR][COLOR=#000000]/[/COLOR]
drwxr-xr-x 98 scott scott       4096 Mar 25 08:54 [COLOR=#5454FF]**..**[/COLOR][COLOR=#000000]/[/COLOR]
drwxr-xr-x 61 scott scott       4096 Mar 24 12:49 [COLOR=#5454FF]**AtoE**[/COLOR][COLOR=#000000]/[/COLOR]
-rw-r--r--  1 scott scott 1668731824 Mar 24 02:47 [COLOR=#ff54ff]**movie1**[/COLOR].mkv
-rw-r--r--  1 scott scott 1695138223 Mar 24 02:47 [COLOR=#FF54FF]**movie2.mk**[/COLOR]v
-rw-r--r--  1 scott scott         57 Sep  9  2016 .directory
drwxr-xr-x 74 scott scott      12288 Mar 24 03:55 [COLOR=#5454FF]**FtoN**[/COLOR][COLOR=#000000]/[/COLOR]
drwxrwxr-x  3 scott scott       4096 Mar 24 14:38 [COLOR=#5454FF]**junk**[/COLOR][COLOR=#000000]/[/COLOR]
drwxr-xr-x 87 scott scott       4096 Mar 24 11:44 [COLOR=#5454FF]**OtoZ**[/COLOR][COLOR=#000000]/[/COLOR]
[/FONT]
```[FONT=monospace]

[FONT=arial]Kodi can play these two movies from the top directory, but can't go into subfolders. I tried changing the ownership and group of the directories, and moving the share to various locations, but nothing worked.

Can anyone tell me what is wrong?[/FONT][/FONT]

---

### Post by wildmanne39 on 2017-03-25
*Thread moved to **Server Platforms**.*

---

### Post by uncleo2 on 2017-03-25
SOLVED

Turning up the debug level showed that the problem is [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1675698](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1675698) this bug in Samba filed yesterday.

Adding [FONT=courier new]follow symlinks = yes[/FONT] to each share section in smb.conf resolved the issue.

---

### Post by RobGoss on 2017-03-26
Thanks for sharing your solution with the forum members

---

