---
title: "RHEL in Xenserver"
date: 2009-10-08
forum: Virtualisation
---

### Post by smc18 on 2009-10-08
Hola,

After installing RHEL5.3 on Xenserver 5.5 my redhat vm does not have a gui.

startx gives me

> Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct  8 02:53:14 2009
(EE) Unable to locate/open config file

xf86PciVideoInfo is not set
(==) Using default built-in configuration (45 lines)
(EE) open /dev/fb0: No such file or directory
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining

After looking at the error, I thought it may help if I installed XenServer tools.

I mounted the XenServer tools virtual cd and ran the install.sh under the Linux directory.  Once I ran the script it logged me out before giving any form success or failure.

So I relogin and startx still gives me the same error.  I then rebooted the vm and retried but no luck.

Getting the gui working is no big deal, but I would like to learn how to fix it. :)

Anyone have a similiar setup and/or problem?

(By the way sorry for posting a redhat and xenserver issue here, but you can't beat this community ;) )

---

### Post by smc18 on 2009-10-14
bump

---

