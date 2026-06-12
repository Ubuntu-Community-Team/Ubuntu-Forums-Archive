---
title: "when nfs client writes to folder incron start toooo many tasks"
date: 2018-09-01
forum: Server Platforms
---

### Post by oddstan on 2018-09-01
hi,


i have an nfs share which is monitored with incron to start a script for further backup.
though a incron task is "/nfs_share IN_CLOSE_WRITE /script.sh $#", it results in running the script hundreds times till my machine hangs up.

script passes file name changed, does rsync with further uploading to remote storage with rclone.

export for nfs is:
/nfs_share ip(rw,no_subtree_check,sync)


can someone give a hint how to solve that problem? i guess it is "sync" option in nfs.export writes/closes files on nfs share multiple times, that causes incron get many triggers.
another guess may be that nfs has 8 by default threads.


i guess IN_NO_LOOP for incron task is not a solution, since too many changes will be skipped.


/nfs_share may constantly change thus blocking files in share cannot be done, so the idea was if file was closed after it was written rsync starts with --inplace option for duplicating to local folder that subsequently runs command for uploading file that was changed.



thanks.

---

