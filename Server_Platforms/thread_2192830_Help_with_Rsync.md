---
title: "Help with Rsync"
date: 2013-12-09
forum: Server Platforms
---

### Post by badgerbailey2 on 2013-12-09
Hello,

I currently use a seedbox for downloading of torrents, I also have a home media server which I use for all of my TV's to connect to, every night, I have set up a cron job using rsync to bring in the content from the seedbox to the home server, using the following command rsync -avhzS --progress (my ftp account location). The problem is that I then use another script for organizing the files when they get to my server and the other script renames and moves them, when this happens rsync believes that they haven't been downloaded and downloads them again, is there some command in rsync that will keep a log of downloaded files so that even if they have been moved then it won't try to download them again?

Any thoughts on this are much appreciated,

Thanks and regards

---

### Post by papibe on 2013-12-09
Hi badgerbailey2.

If the source and destination are in the same partition, you can use hardlinks to leave the source file as they are, and create links with new names to them.

For example:
```
$ tree
.
&#9500;&#9472;&#9472; dir1
&#9474;   &#9492;&#9472;&#9472; file.txt
&#9492;&#9472;&#9472; dir2

2 directories, 1 file

$ ln dir1/file.txt dir2/new_name.txt
$ tree
.
&#9500;&#9472;&#9472; dir1
&#9474;   &#9492;&#9472;&#9472; file.txt
&#9492;&#9472;&#9472; dir2
    &#9492;&#9472;&#9472; new_name.txt

2 directories, 2 files

$ diff dir1/file.txt dir2/new_name.txt 
$

```
Hope it helps. Let us know how it goes.
Regards.

---

