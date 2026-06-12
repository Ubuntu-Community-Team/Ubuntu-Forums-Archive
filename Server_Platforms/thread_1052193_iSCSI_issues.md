---
title: "iSCSI issues"
date: 2009-01-27
forum: Server Platforms
---

### Post by RMSe17 on 2009-01-27
Hi, I am using Ubuntu 8.10 32bit with desktop packages added on top for GUI.
I am trying to use an iSCSI drive.  I did the discovery part and saw the iSCSI target...

then, when I do the restart command 
```

 sudo /etc/init.d/open-iscsi restart
 * Disconnecting iSCSI targets                                           [ OK ] 
 * Stopping iSCSI initiator service                                      [ OK ] 
 * Starting iSCSI initiator service iscsid                               [ OK ] 
 * Setting up iSCSI targets                                                     
Login session [iface: default, target: iqn.2006-01.com.openfiler:tsn.exodus, portal: 192.168.1.40,3260]
                                                                         [ OK ]

```

which looks good to me.  But when I do the status command I get errors!

```

 sudo /etc/init.d/open-iscsi status
Current active iSCSI sessions:
iscsiadm: Could not get host for sid 1.
iscsiadm: could not get host_no for session 6.
iscsiadm: could not find session info for session1
iscsiadm: Can not get list of active sessions (6)

```

What does this mean?  What do I do now?
Thanks!

---

### Post by electrogeist on 2009-01-27
Related to this?
[http://ubuntuforums.org/showthread.php?t=957696](http://ubuntuforums.org/showthread.php?t=957696)

---

### Post by RMSe17 on 2009-01-28
Yea, I had posted in that thread a month ago, but didn't get an answer there...

---

### Post by RMSe17 on 2009-01-28
I managed to compile open-iscsi-2.0-870.2 after getting my kernel source (had to run ```
uname -r
``` to find out which kernel I had).

Now the status give me proper results.

---

