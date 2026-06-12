---
title: "Ubuntu server cgroup issue"
date: 2013-09-13
forum: Server Platforms
---

### Post by Bin_Wu on 2013-09-13
Ubuntu 12.04.3 server with all the latest official packages, have cgroup-bin 0.37-1ubuntu installed.

I am currently testing the resource management in Ubuntu by using cgroups, but found a problem. If anyone got any clue, please help. Here is the details:

after I stopped the cgconfig service, 
```

sudo service cgconfig stop

```

all the related process will be terminated, but the /sys/fs/cgroup and all the subfolders and files are still mounted. that is the problem which preventing me to start the service again. I have to either wait a while, 10 - 40 mins, it's pretty random, or mannually call /usr/sbin/cgclear to unmount the file system. BUT the cgclear now refuse to work sometimes, it says invalid argument. but 'man cgclear' simply tells us there is no argument is required.

I am stucking on this annoying problem now, your help will be appreciated.

---

