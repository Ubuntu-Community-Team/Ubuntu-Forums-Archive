---
title: "smartmon tools questions"
date: 2008-09-08
forum: Server Platforms
---

### Post by trmentry on 2008-09-08
I have 2 mdadm arrays.  I keep having a drive say it goes bad, and the array freak and rebuild.  I zero out the drive and re-add it and it's fine.  

So I'm wanting to SMART monitor these drives.  

I installed smartmontools

```

 apt-get install smartmontools

```

I then edited /etc/default/smartmontools to make it start smartd on start up.

My /etc/smartd.conf has the following:

```

DEVICESCAN -m root -M exec /usr/share/smartmontools/smartd-runner

```

I then tried to start the daemon and it fails.  
This is what is in the /var/log/daemon.log.

```


Sep  8 07:27:28 hoth smartd[8115]:   For example: '/dev/sdq -a -d sat'
Sep  8 07:27:28 hoth smartd[8115]: Device: /dev/sdr, opened
Sep  8 07:27:28 hoth smartd[8115]: Device /dev/sdr: ATA disk detected behind SAT layer
Sep  8 07:27:28 hoth smartd[8115]:   Try adding '-d sat' to the device line in the smartd.conf file.
Sep  8 07:27:28 hoth smartd[8115]:   For example: '/dev/sdr -a -d sat'
Sep  8 07:27:28 hoth smartd[8115]: Device: /dev/sds, opened
Sep  8 07:27:28 hoth smartd[8115]: Device /dev/sds: ATA disk detected behind SAT layer
Sep  8 07:27:28 hoth smartd[8115]:   Try adding '-d sat' to the device line in the smartd.conf file.
Sep  8 07:27:28 hoth smartd[8115]:   For example: '/dev/sds -a -d sat'
Sep  8 07:27:28 hoth smartd[8115]: Unable to monitor any SMART enabled devices. Try debug (-d) option. Exiting...

```


I'm a bit confused... do I put the '-d sat' on the line in smartd.conf?   Why is it wanting a debug option?  I can do a smartcrl -a /dev/sd$x with no issues, so not sure why the daemon won't start.

Any pointers are greatly appreciated.

Thanks



(Running Hardy 8.04.1 server 64 bit)

---

### Post by inphektion on 2008-09-08
the -d isn't for debug.  Its to specify the device type.  its trying to guess the type and tries ata and scsi and I guess those aren't working so its telling you to specify and try sat.

since smartctl appears to work for you then I assume one of the avail options will work from the .conf page.

check here for more details [http://man-wiki.net/index.php/5:smartd.conf](http://man-wiki.net/index.php/5:smartd.conf)

Edit:
oh so to directly answer your question, yes try this in your smartd.conf
```
DEVICESCAN -d sat -m root -M exec /usr/share/smartmontools/smartd-runner
```

---

