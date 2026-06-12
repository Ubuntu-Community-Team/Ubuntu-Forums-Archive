---
title: "swapoff / swapon not running in a script"
date: 2011-05-24
forum: Server Platforms
---

### Post by hkphooey on 2011-05-24
Hi all,

Not quite sure where to post this, so please bear with me ... I have a server running in a datacentre. Its running apache and every now and then apache fills up the memory, and the disk starts to swap out. There must be some kind of php / apache memory leak, which I can't locate, but anyway, in the meantime, I wrote a script which alleviates the problem - this is the short version:

```
#!/bin/bash
sync
echo 1 > /proc/sys/vm/drop_caches
sleep 5
swapoff -a && swapon -a

```

This works beautifully when run as root from the command line: free memory increases and swap is cleared. However, when its run as root using crontab, the first bit works - echo 1 > /proc/sys/vm/drop_caches clears all the page cache memory - but the second doesn't, swap memory is still non-zero. 

So, any ideas why the script works OK when I'm logged in as root, but doesn't work OK when I run it via the root's crontab?

---

### Post by prshah on 2011-05-25
> **hkphooey said:**
> 
swapoff -a && swapon -a


Try using the full path```
/sbin/swapoff -a && sleep 1 && /sbin/swapon -a
```

You have to use full absolute pathnames in crontab commands because when cron runs a script, it does not perform initial login activity (which is where the path(s) are set). Default paths are only /usr/sbin:/usr/bin.

However, you should be aware that if swap is in active use and there is no place for active process to be moved from swap to main memory, then it is likely that swapoff will fail.

---

### Post by hkphooey on 2011-05-25
Bingo! It was the paths. And I now realise it isn't the first time I've been caught out by this 'full paths in cron' gotcha ... 

Thanks for the explanation. Maybe it will stick in my head this time!

---

