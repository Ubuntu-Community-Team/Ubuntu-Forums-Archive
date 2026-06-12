---
title: "ubuntuone-syncd running wild"
date: 2012-09-14
forum: Ubuntu One (CLOSED)
---

### Post by skrempl on 2012-09-14
I just did an software update and restarted my computer. After login the machin was extremely slow and i recognized many (>200) processes ubuntuone-syncd eating all the cpu time. 

Killing the processes did not help since the restarted every time. 

[I]pids=`ps -u $USER | grep syncd | sed s/^/' '/g | awk 'BEGIN {FS="[ \t]*"}{ printf  $2 " "} END {}'` 
kill -9 $pids
[/I]
Some trial and error lead to the result that killing nautilus stops the restarting of the syncd. 

[I]4 S stefan    2636  2218  0  80   0 - 98034 poll_s 13:42 ?        00:00:00 gnome-session --session=ubuntu
0 S stefan    2740  2636  0  80   0 - 223879 poll_s 13:42 ?       00:00:00 nautilus -n
[/I]
[I]>kill -9 2740 
[/I]
After again killing all syncd processes the problem is gone until the next login.
The interesting fact now is that i do not have configured or installed ubuntuone at all. 
Installing ubuntuone results in errors (IPC Error) while trying to configure it.
Uninstalling ubuntuone does not change anything.

Since the nautilus process was started by gnome i looked in the .xsession-errors an found hundereds of entries:

[I].xsession-errors:** (nautilus:2740): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
.xsession-errors:** (nautilus:2740): WARNING **: Error calling get_folders: Method "get_folders" with signature "" on interface "com.ubuntuone.SyncDaemo
[/I]
Any ideas ?

---

