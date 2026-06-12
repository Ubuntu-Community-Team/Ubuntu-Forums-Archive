---
title: "syslog-ng setup"
date: 2018-07-17
forum: Server Platforms
---

### Post by bamatx on 2018-07-17
Howdy forums, 

Ubuntu Server Release 16.04

I am trying to migrate from syslog-ng 3.1.2 on RHEL 5.4 to 3.5.6-21 on Ubuntu 16.04.  I've restored the directory structure to /var/log/syslog-ng to maintain history.  I am going to a default config file for the new version and adding the following:

```
# Remote logging
source s_remote {
        tcp(ip(0.0.0.0) port(514));
        udp(ip(0.0.0.0) port(514));
};

destination d_separatedbyhosts {
        file("/var/log/syslog-ng/$HOST/messages.log" owner("root") group("root") perm(0640) dir_perm(0750) create_dirs(yes));
};

log { source(s_remote); destination(d_separatedbyhosts); };
```

I can see the server listening on port 514 both TCP and UDP but nothing seems to be hitting the device logs.  

These are the errors in the syslog.log:

```
Jul 17 17:41:28 itgl-syslog01 syslog-ng[2360]: Error opening file for writing; filename='/dev/vc/10', error='No such file or directory (2)'
Jul 17 17:41:28 itgl-syslog01 syslog-ng[2360]: internal() messages are looping back, preventing loop by suppressing all internal messages until the current message is processed; trigger-msg='Error opening file for writing; filename=\'/dev/vc/10\', error=\'No such file or directory (2)\'', first-suppressed-msg='Error opening file for writing; filename=\'/dev/vc/10\', error=\'No such file or directory (2)\''
Jul 17 17:50:05 itgl-syslog01 syslog-ng[2360]: Log statistics; processed='destination(error)=12', processed='destination(user)=0', processed='destination(uucp)=0', processed='center(received)=16', processed='destination(daemon)=0', processed='destination(syslog)=16', processed='destination(lpr)=0', processed='destination(console)=0', processed='destination(debug)=0', processed='center(queued)=78', processed='destination(kern)=6', processed='src.none()=0', stamp='src.none()=0', processed='source(src)=16', processed='destination(newsnotice)=0', processed='destination(newserr)=0', processed='destination(xconsole)=21', processed='global(payload_reallocs)=3', processed='global(sdata_updates)=0', processed='source(s_remote)=0', processed='destination(mail)=0', processed='destination(newscrit)=0', processed='destination(auth)=1', processed='destination(cron)=0', processed='src.internal(src#1)=16', stamp='src.internal(src#1)=1531867288', processed='global(msg_clones)=0', processed='destination(console_all)=21', processed='destination(d_separatedbyhosts)=1'
```

I can confirm there is no /dev/vc/10 device, and I am not sure where I should be pointing that section of the default config file.  I tried /dev/vcs and /dev/vcsa6 unsuccessfully.  

Any help in solving this is much appreciated.  Do let me know if anything else is need from me.

Attached is my full syslog-ng.conf file.

Thanks!
Brad

---

### Post by bamatx on 2018-07-18
It was logging after all.  The problem was it wasn't resolving hostnames, but writing into folders with ip addresses as the folder name.  Those existed on the old server and were restored to the new from backup so I didn't think to look in them as they had been there all along.

---

