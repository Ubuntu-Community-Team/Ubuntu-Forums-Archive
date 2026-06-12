---
title: "hdparam -S"
date: 2011-09-24
forum: Server Platforms
---

### Post by billiumb on 2011-09-24
I want to put into standby my /home server hard drive when it is idle for 2 hours.

root@zeus:~# hdparm -S 60 /dev/sdb
/dev/sdb:
setting standby to 60 (5 minutes)
root@zeus:~# hdparm -C /dev/sdb
/dev/sdb:
 drive state is:  active/idle

(Short time for testing)
The drive never goes into standby.

However:

root@zeus:~# hdparm -y /dev/sdb
                                            
/dev/sdb:
 issuing standby command
root@zeus:~# hdparm -C /dev/sdb
/dev/sdb:
 drive state is:  standby

works and the drive wakes up as expected on mail collection, so there are no processes keeping it awake.

Any clues as to why the -S command does not work.

I do not have smart running.

Thanks for any thoughts.

---

