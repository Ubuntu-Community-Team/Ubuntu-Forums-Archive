---
title: "Heartbeat on DRBD"
date: 2008-04-11
forum: Server Platforms
---

### Post by Scormen on 2008-04-11
Hi all,

Last week I have installed DRBD and HeartBeat on a Ubuntu 7.10 server system, but I'm having problems with the configuration.

I tried it already on more than 5 2-node clusters (in VMware), but I still can't get it at work. I hope someone can see a issue in my config.

I have configurated 2 systems with in each 2 hard disks in software RAID-1.
My partition (in raid) for DRBD is /dev/md4

I installed DRBD like this:

```
apt-get install drbd8-utils drbd8-module-source \
  build-essential module-assistant
module-assistant auto-install drbd8
```

HeartBeat like this:
```
apt-get install heartbeat
```

The server was updated ofcourse :)

[SIZE="2"]**DRBD**[/SIZE]
These are my configuration files of DRBD.

**drbd.conf**
```
global {
minor-count 1;
}

resource mysql {
protocol C;
                
on dbg00 {
device /dev/drbd0; 
disk /dev/md4;  
address 192.168.1.30:7788;
meta-disk internal;
}

on dbg01 {
device /dev/drbd0; 
disk /dev/md4;   .
address 192.168.1.31:7788; 
meta-disk internal;
}

disk {
on-io-error detach;
}

net {
max-buffers 2048;
ko-count 4; 
}

syncer {
rate 10M; 
al-extents 257; 
}

startup {
wfc-timeout 0; 
degr-wfc-timeout 120; # 2 minutes.
}
} 
```

**[SIZE="2"]HeartBeat[/SIZE]**

**ha.cf**
```
logfacility     daemon     
keepalive 1                  
deadtime 10        
warntime 5                  
initdead 120      
udpport 694            
bcast eth2   
auto_failback off    
node    dbg00 
node    dbg01

respawn hacluster /usr/lib/heartbeat/ipfail

use_logd yes
```

**haresources**
```
dbg00 IPaddr::192.168.1.35/26 drbddisk::mysql \
Filesystem::/dev/drbd0::/mnt/mysql::ext3::defaults mysql
```


---------


/mnt/mysql is mounted on /dev/drbd0.

DRBD **is working** but Heartbeat does not.
Does someone have a idea what I'm doing wrong?

Does someone have a working configuration?

Thanks,
Kris

---

### Post by Scormen on 2008-04-15
Hi all,

It is a little bug: [https://bugs.launchpad.net/ubuntu/+source/heartbeat/+bug/174182](https://bugs.launchpad.net/ubuntu/+source/heartbeat/+bug/174182)

The solution is:

> It's working after I changed the first line of "/usr/lib/ocf/resource.d/heartbeat/Filesystem" from "#!/bin/sh" to "#!/bin/bash"
(see the link above to launchpad)

Kris

---

