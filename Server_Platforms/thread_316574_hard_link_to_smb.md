---
title: "hard link to smb"
date: 2006-12-11
forum: Server Platforms
---

### Post by dpan on 2006-12-11
I want to make a hard link to a smb dir on my windows system...

the dir would be smb://192.168.5.103/frog the dir i want the link in is /home/me/freee/box (box is the link)

I have been trying to do this all day and can't seem to figure it out..

---

### Post by jpkotta on 2006-12-11
I don't think you mean "hard link" in the Unix sense.  I don't think that's possible.  ```
man ln
```

You can set up a network share to be *mounted* at a directory automatically.

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

