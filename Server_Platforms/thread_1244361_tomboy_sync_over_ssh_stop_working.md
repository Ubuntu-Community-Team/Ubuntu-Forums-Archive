---
title: "tomboy sync over ssh stop working"
date: 2009-08-19
forum: Server Platforms
---

### Post by kangyu29 on 2009-08-19
First I am not sure if this is the right place to ask, if not, please forgive me, and tell me where should I post it and I will do that.

I always sync my notes to a school server over ssh. I have had this working for a long time until recently.

the error is something like
"Error connecting to the synchronization service. Please try again."

I had this a couple days back, and fixed it by deleting a file under ~/.tomboy/sync-sshfs/lock

but this time I don't see any "lock" file.

the log file show something like this. 

```

8/19/2009 11:06:33 AM [DEBUG]: SyncThread using SyncServiceAddin: SSH (sshfs FUSE)
8/19/2009 11:06:33 AM [DEBUG]: Mounting sync path with this command: /usr/bin/sshfs -p 22 user@xxx.xxx.xxx:/home/user/tomboy /home/user/.tomboy/sync-sshfs
8/19/2009 11:06:37 AM [DEBUG]: Error calling /usr/bin/sshfs
8/19/2009 11:06:37 AM [DEBUG]: Exception while creating SyncServer: An error ocurred while connecting to the specified server:

fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

  at Tomboy.Sync.FuseSyncServiceAddin.MountFuse (Boolean useStoredValues) [0x00000] 
  at Tomboy.Sync.FuseSyncServiceAddin.CreateSyncServer () [0x00000] 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] 
```

---

