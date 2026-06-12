---
title: "failed to bring up enp0s8 connection in vm machine"
date: 2017-06-10
forum: Virtualisation
---

### Post by LastDino on 2017-06-10
I got an error saying this, not entirely sure where to look for exactly
```
root@pc1:/home/owl# /etc/init.d/networking restart
[....] Restarting networking (via systemctl): networking.serviceJob for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.
 failed!


```

when I looked at "journalctl -xe" I saw 

```
-- Unit networking.service has finished shutting down.
Jun 11 01:35:07 pc1 systemd[1]: Starting Raise network interfaces...
-- Subject: Unit networking.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has begun starting up.
Jun 11 01:35:07 pc1 ifup[1750]: RTNETLINK answers: File exists
Jun 11 01:35:07 pc1 ifup[1750]: Failed to bring up enp0s8.
Jun 11 01:35:07 pc1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jun 11 01:35:07 pc1 systemd[1]: Failed to start Raise network interfaces.
-- Subject: Unit networking.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has failed.
-- 
-- The result is failed.
Jun 11 01:35:07 pc1 systemd[1]: networking.service: Unit entered failed state.
Jun 11 01:35:07 pc1 systemd[1]: networking.service: Failed with result 'exit-code'.


```

Any ideas?

This is on VM machine, issuing commands through open ssh from host terminal

On VM Ubuntu 16.04 server is installed and host is Ubuntu 16.04 based eOs

---

### Post by KillerKelvUK on 2017-06-10
Hey, might be related to your SSH challenges maybe ;-)

If your guest is a server variant it would be useful to know how you've configured for your network interface(s)...have you made any modifications to /etc/network/interfaces?  Posting its output here would help?

---

### Post by LastDino on 2017-06-11
Yes, indeed. 

Here is output
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet dhcp

auto enp0s8
iface enp0s8 inet static
        address 192.168.1.1
        netmask 255.255.255.0
up route add -net 192,168.0.0/16 gw 192.168.1.254 dev enp0s8


```

---

### Post by KillerKelvUK on 2017-06-11
Looks like you have a typo in your route addition using a comma instead of a period "...192(comma)168.0.0/16"

---

### Post by LastDino on 2017-06-11
Sorry, that typo got there when posting the post somehow. Error still stays
 
Error
```
root@pc1:/home/owl# /etc/init.d/networking restart
[....] Restarting networking (via systemctl): networking.serviceJob for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.
 failed!

```


journal -xe output
```

root@pc1:/home/owl# journalctl -xe
-- Unit networking.service has begun starting up.
Jun 11 17:09:07 pc1 ifup[3531]: RTNETLINK answers: File exists
Jun 11 17:09:07 pc1 ifup[3531]: Failed to bring up enp0s8.
Jun 11 17:09:07 pc1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jun 11 17:09:07 pc1 systemd[1]: Failed to start Raise network interfaces.
-- Subject: Unit networking.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has failed.
-- 
-- The result is failed.
Jun 11 17:09:07 pc1 systemd[1]: networking.service: Unit entered failed state.
Jun 11 17:09:07 pc1 systemd[1]: networking.service: Failed with result 'exit-code'.
Jun 11 17:09:38 pc1 systemd[1]: Stopped Raise network interfaces.
-- Subject: Unit networking.service has finished shutting down
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has finished shutting down.
Jun 11 17:09:38 pc1 systemd[1]: Starting Raise network interfaces...
-- Subject: Unit networking.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has begun starting up.
Jun 11 17:09:38 pc1 ifup[3612]: RTNETLINK answers: File exists
Jun 11 17:09:38 pc1 ifup[3612]: Failed to bring up enp0s8.
Jun 11 17:09:38 pc1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jun 11 17:09:38 pc1 systemd[1]: Failed to start Raise network interfaces.
-- Subject: Unit networking.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has failed.
-- 
-- The result is failed.
Jun 11 17:09:38 pc1 systemd[1]: networking.service: Unit entered failed state.
Jun 11 17:09:38 pc1 systemd[1]: networking.service: Failed with result 'exit-code'
```

---

### Post by LastDino on 2017-06-11
Solved. Did the entire process again, not sure what was the problem but I think must be me, followed the same steps but with good results.

---

