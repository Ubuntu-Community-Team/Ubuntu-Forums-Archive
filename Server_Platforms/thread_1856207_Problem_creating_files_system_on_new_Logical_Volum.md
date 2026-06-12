---
title: "Problem creating files system on new Logical Volume"
date: 2011-10-07
forum: Server Platforms
---

### Post by sobgtp on 2011-10-07
Ubuntu server 10.04 

I have LVM setup on my servers main drive. The drive is 1TB and I setup the intial partitionas as 1.2GB swap and 30GB Root , I am now trying to create a new logical volume. I have created the logical volume however when I attempt to create the file system I am given an error. 

Command I using to create the filesystem:
```

sudo mkfs -t ext4 -q /dev/mediaserver/movies
```

Error message returned: 
```
/dev/mediaserver/movies is apparently in use by the system; will not make a filesystem here!
```

---

### Post by sobgtp on 2011-10-07
I found the solution to my problem, I am not sure how the drive was in use since it did not have a file system but the following command seemed to release the drive from the system and I was able to create the file system 

```
  sudo partprobe 
```

---

