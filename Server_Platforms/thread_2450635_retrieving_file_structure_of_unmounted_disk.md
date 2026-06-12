---
title: "retrieving file structure of unmounted disk"
date: 2020-09-18
forum: Server Platforms
---

### Post by johnycage on 2020-09-18
I used to mount an internal hard disk on /media/storage/ 
Now the HDD is formatted and recovering the data may or may not be possible. 

But if I could just get the list of all files and directory list that used to reside in /media/storage that would be great. 

Question: Does ubuntu index or cache the list of for filenames,directories information of external drives? Where can I get this information? If there's list that I can retrieve from temp files, or autobackup etc? Where to locate this? 
This is not a data recovery request, I just need to get the file structure of unmounted disk that used to mount on /media/storage

Thank you.

---

### Post by ameinild on 2020-09-18
Maybe you should edit the title to: "Retrieving file structure of unmounted and formatted disk", since this is definitely harder than if it's just unmounted.

In addition to that, I unfortunately have no clue! :(

---

### Post by darkod on 2020-09-18
I am not familiar with any place where the folder structure would be kept except on the disk itself.

But even if the disk is formatted, you could still recover a lot of the data if you haven't used it much after the formatting. That is the important part.

Also, did you simply format the existing partitions or you created new partition table and new partitions?

---

### Post by TheFu on 2020-09-18
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Unix systems do what they are told, in general.
If you want a list of files on a  system, creating one is easy. A few different ways:
```
ls -lR /  > $HOME/ls-lR.txt
find / -type f -size +5b > $HOME/all-files.txt
```

If you want a directory structure, that is also trivial to create:
```
tree -d / > $HOME/all-dirs.txt
find / -type d > $HOME/all-dirs2.txt
```

But these are the admin's task to create and update.  I do stuff like this weekly via cron.

And it is also the role of the admin to create any backups desired.  Backups solve at least 1001 problems on computers. I don't understand why there is such avoidance to do this small task. Not knowing how is where we all begin.  Gaining that knowledge is possible.

---

