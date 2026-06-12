---
title: "mount options for reiserfs"
date: 2008-07-01
forum: Server Platforms
---

### Post by LRT on 2008-07-01
what mount options can i use for reiserfs aside from the one described in its man page. i have a cifs mount where i use uid,gid,file_mode,dir_mode mount options. i want to be able to use these for the reiserfs mount. i'll be more specific...

when a user creates a file on this partition it should create a file with permissions 660, and a directory should be 770. owner should be user who created the file or user who last modified it. group owner should be the 'editors' group.

is this possible with a reiserfs mount??

---

### Post by amenszer on 2008-07-02
Are you using this setup in conjunction with samba? i.e. are you sharing out the Reiserfs partition with samba, and is that how users are accessing it? Or are users accessing the partition locally on the machine?

---

