---
title: "Rsync help: directory information not updated."
date: 2009-05-18
forum: Server Platforms
---

### Post by japtar10101 on 2009-05-18
Note that I had rsync running perfectly until i moved my files.

My files were all over the place, so to make it more organized, I moved all of my rsync backup directories to ~/rsync/, and updated /etc/rsyncd.conf accordingly.  Now my host computers can't seem to recognize the new locations of the backup files.  How can I fix this?

For reference, here's the updated /etc/rsyncd.conf file:
```
motd file = /etc/rsyncd.motd
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
lock file = /var/run/rsync.lock
max connections = 3

[testing]
comment = testing...
path = /home/taro/rsync/testing
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes

[School]
comment = notes synchronization
path = /home/taro/rsync/School
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes

[Work]
comment = work documents synchronization
path = /home/taro/rsync/Work
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes

[Health]
comment = issurance notes synchronization
path = /home/taro/rsync/Health
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes

[Programming]
comment = programming synchronization
path = /home/taro/rsync/Programming
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes

[Game]
comment = game synchronization
path = /home/taro/rsync/Game
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes

[Music]
comment = music synchronization
path = /home/taro/rsync/Music
read only = yes
auth users = omiyat
uid = nobody
gid = nobody
list = yes
```

---

### Post by windependence on 2009-05-18
What error messages are you seeing in the logs? What user is your rsync script running under and what are your directory permissions on your data directories?

-Tim

---

### Post by japtar10101 on 2009-05-19
> **windependence said:**
> What error messages are you seeing in the logs? What user is your rsync script running under and what are your directory permissions on your data directories?

-Tim

Sorry, I should have been more clear.  The error specifically says:
```
rsync --verbose  --progress --stats --compress --rsh=/usr/bin/ssh --recursive --times --perms myserver.com:testing .
receiving incremental file list
rsync: link_stat "/home/taro/testing" failed: No such file or directory (2)

Number of files: 0
Number of files transferred: 0
Total file size: 0 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 1
Total bytes sent: 8
Total bytes received: 10

sent 8 bytes  received 10 bytes  2.40 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1506) [receiver=3.0.5]
```

This is true.  I moved the /home/taro/testing directory to /home/taro/rsync/testing.  I would like to keep my current directory settings, since it's much more organized, but have the rsync recognize the update I've made.

Also, rsync is (probably) running under root, but the directory permissions goes to me.

---

### Post by japtar10101 on 2009-05-19
> **japtar10101 said:**
> ```
rsync --verbose  --progress --stats --compress --rsh=/usr/bin/ssh --recursive --times --perms myserver.com:testing .
```...Or I could add "rsync" to that path: "myserver.com:rsync/testing".
...And it works.
*facepalm*
I don't know why that didn't cross my mind before....Anyway, call this fixed.

---

### Post by koenn on 2009-05-19
```
 myserver.com:testing .
```
this is where you went wrong.
written like this, the path refers to an actual directory, relative to the home directory you logon with at the remote system hence /home/taro/testing.

This syntax completely ignores the rsync.conf.

To refer to a 'rsync' share defined in rsync.conf , you write 
```
myserver.com::testing
``` note the double "::"
In this case, 'testing' refers to the path defined under [testing] in rsync.conf. It requires rsync to be running in daemon mode on the target server, but that might be enabled by default.

---

### Post by japtar10101 on 2009-05-19
> **koenn said:**
> ```
 myserver.com:testing .
```
this is where you went wrong.
written like this, the path refers to an actual directory, relative to the home directory you logon with at the remote system hence /home/taro/testing.

This syntax completely ignores the rsync.conf.

To refer to a 'rsync' share defined in rsync.conf , you write 
```
myserver.com::testing
``` note the double "::"
In this case, 'testing' refers to the path defined under [testing] in rsync.conf. It requires rsync to be running in daemon mode on the target server, but that might be enabled by default.

Thanks.  That clears everything up!

---

