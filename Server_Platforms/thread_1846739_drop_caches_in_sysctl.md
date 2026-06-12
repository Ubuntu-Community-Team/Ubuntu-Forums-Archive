---
title: "drop_caches in sysctl?"
date: 2011-09-19
forum: Server Platforms
---

### Post by mike.emery on 2011-09-19
All the examples I see about setting /proc/sys/vm/drop_caches act like it's an on-demand call (mentioning things like calling sync first). Does this actually make a change to the handling of clean caches that lasts until reboot, or is it a one-time thing? If it's not a one-time thing, can I make it permanent by setting sysctl vm.drop_caches=1?

---

### Post by trimmer on 2012-02-16
The more I look around in ubuntuforums the more I am finding that the community is becoming less and less helpful. This question was posted in September 2010 and has no reply.

From what I've found and read it appears that if you want to permanently disable the cache you would ...

To free ONLY pagecache:
```
sync
cat /proc/sys/vm/drop_caches                       #checks current state
#echo 1 > /proc/sys/vm/drop_caches                 #not recommended
sysctl -w vm.drop_caches=1                         #changes current 
echo "vm.drop_caches = 1" >> /etc/sysctl.conf"     #makes perm
sync
```

To free ONLY dentries and inodes:
```
sync
cat /proc/sys/vm/drop_caches                       #checks current state
#echo 2 > /proc/sys/vm/drop_caches                 #not recommended
sysctl -w vm.drop_caches=2                         #changes current 
echo "vm.drop_caches = 2" >> /etc/sysctl.conf"     #makes perm
sync
```

To free ALL pagecache, dentries and inodes:
```
sync
cat /proc/sys/vm/drop_caches                       #checks current state
#echo 3 > /proc/sys/vm/drop_caches                 #not recommended
sysctl -w vm.drop_caches=3                         #changes current 
echo "vm.drop_caches = 3" >> /etc/sysctl.conf"     #makes perm
sync
```

It used to be that once the 3,2 or 1 value was echoed to the current cache state that you would have to return to the 0 value. I have not found any documentation to that effect since the upgrade to oneiric. I know that the 'sysctl -w vm.drop_caches = 0' command now returns 'error: "Invalid argument" setting key "vm.drop_caches"'

To me this is good because it means that whatever value is passed to vm.drop_caches be it 3,2 or 1 the system will automatically begin to operate its caches normally immediately following the issuance of the sysctl command.


I created two executable scripts to operate on my machine as follows...


/usr/local/sbin/zap
```
swapoff -a
drop
swapon -a
```

/usr/local/sbin/drop
```
sync
sysctl -w vm.drop_caches=3
sync
```

If my machine ever becomes sluggish or unresponsive the first script will always clear up the issue. I do not want the cache off permanently because I use the machine quite frequently and because of the programming I do, I can not always turn off the swap so I created the second 'drop' script because at times, compiling my software gets a little intrusive on using the machine I simply issue the script command to 'drop' the caches and all memory that is available is freed for use and the software compiling in the background is not interrupted due to loss of swap.


Hope this helps.

---

