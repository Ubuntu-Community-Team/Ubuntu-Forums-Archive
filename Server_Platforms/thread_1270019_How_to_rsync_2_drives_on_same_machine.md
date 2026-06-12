---
title: "How to rsync 2 drives on same machine"
date: 2009-09-19
forum: Server Platforms
---

### Post by android6011 on 2009-09-19
I want to create a cron job that rsyncs 2 drives every 3 hours in the same machine. I only used a very simple gui before for rsync but now with ubuntu server things are trickier.

the rsync options I want are:

-delete files on target that are not on source,
-keep permissions

any suggestions would be great. thanks

---

### Post by ugm6hr on 2009-09-19
What format are the 2 drives (e.g. ext3)?

The following assumes ext3, since it won't work with vfat (and uncertain re: ntfs).

In general, the -a option will cover your requirements, with the addition of --delete.

```
rsync -a --delete /source_folder/ /destination_folder/
```

---

### Post by android6011 on 2009-09-19
> **ugm6hr said:**
> What format are the 2 drives (e.g. ext3)?

The following assumes ext3, since it won't work with vfat (and uncertain re: ntfs).

In general, the -a option will cover your requirements, with the addition of --delete.

```
rsync -a --delete /source_folder/ /destination_folder/
```

They are XFS

---

### Post by ugm6hr on 2009-09-19
I have never used XFS, but as far as I know it preserves ownership, permissions etc just fine with rsync.

So the above command should be fine.

You can see what it all does with:
```
man rsync
```

Perhaps someone with XFS experience might be able to confirm.

---

