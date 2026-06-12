---
title: "Printer shares dont appear on startup.."
date: 2010-02-22
forum: Server Platforms
---

### Post by fisch79 on 2010-02-22
I notice that after rebooting my ubuntu 9.10 server my printer shares disappear across the network... They seem to reappear once I physically log in as root or another user AT the server.... 

It seems as if a service is not starting unless a user logs in at server. Any one have any suggestions??

-- other than that it was quite simple getting samba/cups setup and working to share the printers to other workstations....

Thanks...

---

### Post by fisch79 on 2010-02-23
ok... I think I found the problem... seems like its Samba... it's not starting up after I reboot the system.

I would hate to login remotely and restart the service  everytime!

Any else seeing this??

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

You can check if samba is set to autostart during boot by checking if the 'S20samba' file is present in the /etc/rc*.d directories.

If the file is not present, you can do:
```
$ sudo update-rc.d samba defaults
```
This will enable the service to startup during boot in runlevels 2,3,4,5.

The 'S20samba' is a symbolic (soft) link to the '/etc/init.d/samba' file. Having a symbolic link to this file in the rc3.d directory will start samba automatically in run level 3. Likewise, rc0.d to rc6.d corresponds to run levels 0 through 6. Any file present inside the directories are executed when the system enters that particular run level.

Also see if this helps: [http://ubuntuforums.org/showthread.php?t=250673](http://ubuntuforums.org/showthread.php?t=250673)

---

