---
title: "LTSP System Wide Network Proxy"
date: 2010-02-17
forum: Server Platforms
---

### Post by jag3773 on 2010-02-17
Hello,

I have a new 9.10 LTSP server installed and it is working very well.  I am trying to set a system wide proxy for the chroot but I'm not sure where the config file is for this nor could I find any information on how to set this via the command line.  Clearly, on the server's root I can navigate to System>Preferences>Network Proxy and then specify "Apply System-Wide..." but that does not take effect for the chroot environment that is presented to the clients.

Furthermore, I can navigate to the settings in gconf-editor, but I'm still unsure how to apply the changes to the chroot.

Any ideas?

Thanks

---

### Post by jag3773 on 2010-02-17
For anyone else interested in doing the same thing I'll post the solution I found.  If anyone knows of another way to do this I would still be interested.  Based on the LTSP Manual, I found that this works:

[LIST]
[*]Make sure gconf-editor is installed on your server.
[*]Create $CHROOT/usr/share/ldm/rc.d/X02-proxysettings.  This file should contain the gconf settings, like so:
[/LIST]

```
#
# The following is a script to set up network proxy on LTSP through LDM
ssh -S ${LDM_SOCKET} ${LDM_SERVER} "/usr/bin/gconftool-2 --type string --set  /system/proxy/mode 'manual'"
ssh -S ${LDM_SOCKET} ${LDM_SERVER} "/usr/bin/gconftool-2 --type string --set  /system/http_proxy/host '172.X.X.X'"
ssh -S ${LDM_SOCKET} ${LDM_SERVER} "/usr/bin/gconftool-2 --type int --set  /system/http_proxy/port 8080"
ssh -S ${LDM_SOCKET} ${LDM_SERVER} "/usr/bin/gconftool-2 --type boolean --set  /system/http_proxy/use_http_proxy true"
ssh -S ${LDM_SOCKET} ${LDM_SERVER} "/usr/bin/gconftool-2 --type boolean --set  /system/http_proxy/use_same_proxy true"
```

Essentially, this script runs every time a user logs in with the chroot environment and sets the proxy.

---

