---
title: "Starting processes with /etc/rc*.d/procname scripts"
date: 2010-03-31
forum: Server Platforms
---

### Post by stuartsiegler on 2010-03-31
I apologize for this Newby-esq question:

How do you start processes with the /etc/rc*.d/procname scripts on boot?

I have init scripts (ie, /etc/init.d/openvpn and vmware,etc ) that are pointed to by my rc.* dirs (ie, /etc/rc0.d/K08vmware,/etc/rc2.d/K08vmware
/etc/rc2.d/S90vmware,/etc/rc3.d/K08vmware,
/etc/rc3.d/S90vmware,/etc/rc5.d/K08vmware,
/etc/rc5.d/S90vmware,/etc/rc6.d/K08vmware...)

but they do no seem to get invoked on reboot.

These etc/rc*.d files are of course created by update-rc.d 
(automatically, it seems, during the package installs), but who is supposed to call them?

Do I need to include a pointer to one of these (with the appropriate "start" parameter) somewhere?

After trying rc.local, and crontab, and (I looked at all the rc*conf files),
as a workaround, I have a things_that_dont_start.sh script on my desktop that has in it
```
/etc/init.d/mysql start
/etc/init.d/vmware start
/etc/init.d/openvpn start
/etc/init.d/ssh start
```

that I launch my hand. Yuck.

Thanks!

Stuart

---

### Post by geoffmcc on 2010-03-31
To start my counter strike server on boot i found a startup script on the net. I placed in /etc/init.d and called it cstrike.

i then 
```
sudo chmod +x cstrike 
```

and then 

```
sudo update-rc.d cstrike defaults
```

and when i restart my server cstrike is auto started every time
and because all my counter strike server files are chown to cstrike when the server starts it starts counterstrike server using the user cstrike and not root


This should work for you with your script. In your case it would be 
```
sudo update-rc.d openvpn defaults
``` and  ```
sudo update-rc.d vmware defaults
```

---

### Post by stuartsiegler on 2010-04-02
As I said, I have the scripts in /etc/init.d (created, by the installers)
and, it appears that the installer *have executed* update-rc.d procname defaults, because the symlynks are already in the /etc/rc*.d/ files (created by the installers invokation of update-rc.d)

Nonetheless, re-running it generates:

> sudo update-rc.d vmware defaults
update-rc.d: warning: vmware start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 3 5)
update-rc.d: warning: vmware stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
 System start/stop links for /etc/init.d/vmware already exist.

The issue is that they do not seem to get invoked at startup.

Thanks,

Stuart

---

