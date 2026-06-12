---
title: "ubuntu server first reboot bpfilter error"
date: 2019-06-05
forum: Server Platforms
---

### Post by christopher-santos18 on 2019-06-05
hi im new here how are you ?

i install for the first time the last version of ubuntu server 19.04 and when i restart for the first time he said started bpfilter and is stuck there can some one help me please ?

thanks

---

### Post by TheFu on 2019-06-05
I didn't think bpfilter was ready for use at this point.  It wasn't last fall, so I 'd avoid it.

Most "servers" should use only LTS releases.  19.04 is NOT LTS.

---

### Post by christopher-santos18 on 2019-06-05
Ok what can I do I reeinstal 18.4 and I don't apt-get install upgrade ?

Thanks

---

### Post by christopher-santos18 on 2019-06-06
Ok I have install the 18.04 lts I reboot and it worked now can you help with something else please I have install Plex media server but he installed on root/bar/lib/plexmedia server that's ok but when I try to access by sftp I can access by sftp user:ip then passowrd but I need to put my mídia on sftp root@ip then /var/lib/Plex mediaserver/library and it's not authorized I do what I go to vi /etc/ssh/sshd_config and I put PermitRootLogin yes and I saved the root passowrd it's ok with sudo passwd root and when I go to sftp root@ip the password still don't work can you help me with that please ???


Thanks very much

---

### Post by TheFu on 2019-06-06
Good on using 18.04.  That has support until 2023.  
To maintain it, keep it patched, there are 3 things you need to do, weekly.
```

sudo apt update
sudo apt dist-upgrade
sudo apt autoremove  # run when the output suggests this
sudo apt autoclean  # run to remove old .deb packages which aren't being used anymore
```
run versioned backups weekly, if not daily. Sorry, there isn't a trivial backup command for everyone.
and
Test the restore of those backups before you need them.  Lots of people here have been doing backups for years, only to find they cannot restore. Until you test the restore, you don't really know that you have a backup.
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) has more details.  Update: certs renewed.
None of those commands above will move an 18.04 system to any other release.  They will move an 18.04.1 to 18.04.2 to 18.04.3 (when available).

The Plex question needs a different thread, but you shouldn't use root and should never allow remote root just for plex.

---

### Post by christopher-santos18 on 2019-06-06
Thank you very much, and for Plex I find a way without using root, can you help with one more thing please how can I access do meu server from exterior from another internet ?? Can I use vpn ?? Thanks very much for the help

---

### Post by TheFu on 2019-06-06
If the original question is answered, please use the Thread Tools button and mark it SOLVED to help the community.

Any other questions need a new thread so that volunteers who might know something about the topic might respond.

---

