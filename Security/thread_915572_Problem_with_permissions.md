---
title: "Problem with permissions"
date: 2008-09-10
forum: Security
---

### Post by zuidema on 2008-09-10
I thought I had a problem with my portable drive as when trying to view permissions the message read (the permissions could not be determined)

This also happened when viewing any drive located within my computer icon located on my desktop

On further examination I also have the problem with my home directory located on my desktop.

I have no idea what is going on and need help. Thanks in advance

---

### Post by cariboo on 2008-09-10
You may get this result if the drives are not formatted as ext3. Linux permissions don't work on ntfs/vfat drives. About the only thing is to set the mount points as world readable eg:

```
sudo chmod -R 777 /media/portable drive
```

Where portable drive is your drive

Jim

---

