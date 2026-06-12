---
title: "Ntop Not Starting At Boot"
date: 2008-04-26
forum: Security
---

### Post by wormser on 2008-04-26
I have ntop installed and it works fine, but I have to manually start it after each boot.  My boot log shows ntop in the start up process.  Any ideas?

```
 sudo ntop -u ntop -d
Sat Apr 26 20:42:08 2008  NOTE: Interface merge enabled by default
Sat Apr 26 20:42:08 2008  Initializing gdbm databases
Sat Apr 26 20:42:08 2008  ntop v.3.2 SourceForge .tgz
Sat Apr 26 20:42:08 2008  Configured on May 21 2007 17:35:23, built on May 21 2007 17:35:55.
Sat Apr 26 20:42:08 2008  Copyright 1998-2005 by Luca Deri <deri@ntop.org>
Sat Apr 26 20:42:08 2008  Get the freshest ntop from http://www.ntop.org/
Sat Apr 26 20:42:08 2008  NOTE: ntop is running from 'ntop'
Sat Apr 26 20:42:08 2008  NOTE: (but see warning on man page for the --instance parameter)
Sat Apr 26 20:42:08 2008  NOTE: ntop libraries are in '/usr/lib'
Sat Apr 26 20:42:08 2008  Initializing ntop
Sat Apr 26 20:42:08 2008  Checking eth0 for additional devices
Sat Apr 26 20:42:08 2008  Resetting traffic statistics for device eth0
Sat Apr 26 20:42:08 2008  DLT: Device 0 [eth0] is 1, mtu 1514, header 14
Sat Apr 26 20:42:08 2008  Initializing gdbm databases
Sat Apr 26 20:42:08 2008  VENDOR: Loading MAC address table.
Sat Apr 26 20:42:08 2008  VENDOR: Checking for MAC address table file
Sat Apr 26 20:42:08 2008  VENDOR: File '/etc/ntop/specialMAC.txt' does not need to be reloaded
Sat Apr 26 20:42:08 2008  VENDOR: ntop continues ok
Sat Apr 26 20:42:08 2008  VENDOR: Checking for MAC address table file
Sat Apr 26 20:42:08 2008  VENDOR: File '/etc/ntop/oui.txt' does not need to be reloaded
Sat Apr 26 20:42:08 2008  VENDOR: ntop continues ok
Sat Apr 26 20:42:08 2008  Fingeprint: Loading signature file.
Sat Apr 26 20:42:08 2008  Fingeprint: ...loaded 1697 records
Sat Apr 26 20:42:08 2008  INIT: Parent process is exiting (this is normal)
poindexter@xanadu:~$ Sat Apr 26 20:42:08 2008  **[COLOR=Red]INIT: Bye bye: I'm becoming a daemon...[/COLOR]**
```

---

### Post by Oldsoldier2003 on 2008-04-27
Just a stab in the dark Wormser, but check your init scripts...

> To have ntop start at boot and constantly watch traffic, add the following to /etc/init.d/rc.local or a similar script that is started at boot:

ntop -P /var/lib/ntop -u ntop -d 

[http://www.builderau.com.au/program/linux/soa/Monitor-network-traffic-with-ntop/0,339028299,339281712,00.htm](http://www.builderau.com.au/program/linux/soa/Monitor-network-traffic-with-ntop/0,339028299,339281712,00.htm)

---

### Post by wormser on 2008-04-27
> **Oldsoldier2003 said:**
> Just a stab in the dark Wormser, but check your init scripts...

[http://www.builderau.com.au/program/linux/soa/Monitor-network-traffic-with-ntop/0,339028299,339281712,00.htm](http://www.builderau.com.au/program/linux/soa/Monitor-network-traffic-with-ntop/0,339028299,339281712,00.htm)

Thanks for the link.  I believe this is related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/ntop/+bug/138682").  It looks like there is a work around.

---

### Post by bazzieb on 2008-06-06
Can i paste this ntop -P /var/lib/ntop -u ntop -d anywhere in that file?

---

