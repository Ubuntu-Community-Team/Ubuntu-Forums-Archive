---
title: "apache directory on mounted ntfs/vfat?"
date: 2006-08-14
forum: Server Platforms
---

### Post by cshake on 2006-08-14
I'm trying to set up a webserver with apache2 that is serving the same root directory as the apache2 running in my winXP boot.

I have the root dir in a vfat partition so I can edit the files from both systems, and I would like to share other directories that I have on a ntfs disk. I used to have this working a few years ago in gentoo, but now I can't seem to get the permissions right. In my fstab I have the umask for the partition as 003 to allow read access for the www-data user, but it still doesn't want to authorize. I have all the Alias and Directory sections in apache2.conf right, I just get a 403 error for the directory.
The permissions string is dr-xr-xr-- for the dir, so I don't understand it.

Does anyone have experience with this issue?

[edit]Forgot that I needed the x bit set for directory browsing... now it works with umask=002[/edit]

---

