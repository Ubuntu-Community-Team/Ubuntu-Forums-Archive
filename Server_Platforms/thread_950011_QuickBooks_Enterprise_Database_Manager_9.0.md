---
title: "QuickBooks Enterprise Database Manager 9.0"
date: 2008-10-16
forum: Server Platforms
---

### Post by eurohim on 2008-10-16
Does anyone know of a good resource or walk through for setting up v9.0 of the software? I can find 7 and 8, but not 9.

One problem I foresee is that the Linux Database server won't search through subdirectories, and that just won't do because the client I want to use this for in a Linux environment is an Accounting firm and they have them all over the place, so I found a solution and I'd like to share it because I have no desire to manually keep qbmonitord.conf updated with the hundreds of separate locations required. 

Set up a cron job to run the following:

```
find /shared/data -name "*.QBW" -exec dirname {} \; | uniq > /opt/qb/util/qbmonitord.conf
```

Just replace /shared/data with the path to the top level of the file system you want to scour. What this does is use find to find all *.QBW files in a file structure that you create and then uses dirname to pull out all of the paths, then it replaces the file gbmonitord.conf with the new paths and only paths where QBW files exist thus making the path list as short as possible. The uniq just makes it so you don't have duplicate directories.

Then, just restart the proper services.

---

