---
title: "insserv: warning: script 'lampp' missing LSB tags and overrides"
date: 2016-06-07
forum: Server Platforms
---

### Post by sreez on 2016-06-07
Iam using **ubuntu 16.04 server** while adding lampp service to automatic startup on the boot **sudo**** update-****rc****.d ****lampp**** defaults. ** Its shows the error 
insserv: warning: script 'lampp' missing LSB tags and overrides
insserv: There is a loop between service monit and lampp if stopped
insserv: loop involving service lampp at depth 2
insserv: loop involving service monit at depth 1
insserv: Stopping lampp depends on monit and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header

plz help to fix it. thanks in advance.

---

### Post by raja.genupula on 2016-06-08
The origin thread not coming , so check this out
[http://crunchbang.org/forums/viewtopic.php?id=22017](http://crunchbang.org/forums/viewtopic.php?id=22017)

---

### Post by inchidi on 2017-03-03
> **sreez said:**
> Iam using **ubuntu 16.04 server** while adding lampp service to automatic startup on the boot **sudo**** update-****rc****.d ****lampp**** defaults. ** Its shows the error  insserv: warning: script 'lampp' missing LSB tags and overrides insserv: There is a loop between service monit and lampp if stopped insserv: loop involving service lampp at depth 2 insserv: loop involving service monit at depth 1 insserv: Stopping lampp depends on monit and therefore on system facility `$all' which can not be true! insserv: exiting now without changing boot order! update-rc.d: error: insserv rejected the script header  plz help to fix it. thanks in advance.  have same issue and fix this with edit lampp script  ```
#!/bin/bash
### BEGIN INIT INFO
# Provides: lampp
# Required-Start:    $local_fs $syslog $remote_fs dbus
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start lampp
### END INIT INFO
/opt/lampp/lampp start 
```

---

