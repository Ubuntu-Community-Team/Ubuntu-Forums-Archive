---
title: "Ubuntu 20.04 Focal LXD Container not getting network interface immediately"
date: 2020-04-26
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2020-04-26
Decided to try to start testing a focal container. Creation was no problem. But here is an issue. It has no network for a good while after starting the container. I'm not finding much.

```
grep networkd /var/log/syslog
```

```
Apr 26 23:43:50 focalltsp systemd-networkd[296]: eth0: IPv6 successfully enabledApr 26 23:43:50 focalltsp systemd-networkd[296]: eth0: Gained IPv6LL
Apr 26 23:43:50 focalltsp systemd-networkd[296]: Enumeration completed
Apr 26 23:43:50 focalltsp systemd-networkd-wait-online[297]: managing: eth0
Apr 26 23:43:50 focalltsp systemd[1]: Starting Dispatcher daemon for systemd-networkd...
Apr 26 23:43:50 focalltsp systemd[1]: Started Dispatcher daemon for systemd-networkd.
Apr 26 23:46:30 focalltsp systemd[1]: Stopping Dispatcher daemon for systemd-networkd...
Apr 26 23:49:37 focalltsp systemd-networkd[215]: eth0: IPv6 successfully enabled
Apr 26 23:49:37 focalltsp systemd-networkd[215]: eth0: Gained IPv6LL
Apr 26 23:49:37 focalltsp systemd-networkd[215]: Enumeration completed
Apr 26 23:49:37 focalltsp systemd-networkd[215]: eth0: DHCPv4 address 192.168.1.169/24 via 192.168.1.1
Apr 26 23:49:37 focalltsp systemd-networkd-wait-online[216]: managing: eth0
Apr 26 23:49:37 focalltsp systemd[1]: Starting Dispatcher daemon for systemd-networkd...
Apr 26 23:49:38 focalltsp systemd[1]: Started Dispatcher daemon for systemd-networkd.
```

Just under 6 minutes before it got an ip via dhcp. Same problem if I set a static ip.

```
journalctl -xe | grep networkd
```

```
-- Subject: A start job for unit networkd-dispatcher.service has finished successfully-- A start job for unit networkd-dispatcher.service has finished successfully.
Apr 26 23:42:08 focalltsp systemd[1]: Stopping Dispatcher daemon for systemd-networkd...
-- Subject: A stop job for unit networkd-dispatcher.service has begun execution
-- A stop job for unit networkd-dispatcher.service has begun execution.
Apr 26 23:42:08 focalltsp systemd[1]: networkd-dispatcher.service: Succeeded.
-- The unit networkd-dispatcher.service has successfully entered the 'dead' state.
Apr 26 23:42:08 focalltsp systemd[1]: Stopped Dispatcher daemon for systemd-networkd.
-- Subject: A stop job for unit networkd-dispatcher.service has finished
-- A stop job for unit networkd-dispatcher.service has finished.
-- Subject: A stop job for unit network-online.target has finished
-- A stop job for unit network-online.target has finished.
-- Subject: A stop job for unit network.target has finished
-- A stop job for unit network.target has finished.
Apr 26 23:42:08 focalltsp systemd[1]: systemd-networkd-wait-online.service: Succeeded.
-- The unit systemd-networkd-wait-online.service has successfully entered the 'dead' state.
-- Subject: A stop job for unit systemd-networkd-wait-online.service has finished
-- A stop job for unit systemd-networkd-wait-online.service has finished.
-- Subject: A stop job for unit systemd-networkd.service has begun execution
-- A stop job for unit systemd-networkd.service has begun execution.
Apr 26 23:42:08 focalltsp systemd[1]: systemd-networkd.service: Succeeded.
-- The unit systemd-networkd.service has successfully entered the 'dead' state.
-- Subject: A stop job for unit systemd-networkd.service has finished
-- A stop job for unit systemd-networkd.service has finished.
-- Subject: A stop job for unit network-pre.target has finished
-- A stop job for unit network-pre.target has finished.
Apr 26 23:42:08 focalltsp systemd[1]: Stopped Initial cloud-init job (pre-networking).
Apr 26 23:43:48 focalltsp systemd[1]: Starting Initial cloud-init job (pre-networking)...
Apr 26 23:43:49 focalltsp systemd[1]: Finished Initial cloud-init job (pre-networking).
-- Subject: A start job for unit network-pre.target has finished successfully
-- A start job for unit network-pre.target has finished successfully.
-- Subject: A start job for unit systemd-networkd.service has begun execution
-- A start job for unit systemd-networkd.service has begun execution.
Apr 26 23:43:49 focalltsp systemd-networkd[296]: eth0: IPv6 successfully enabled
Apr 26 23:43:49 focalltsp systemd-networkd[296]: eth0: Gained IPv6LL
Apr 26 23:43:49 focalltsp systemd-networkd[296]: Enumeration completed
-- Subject: A start job for unit systemd-networkd.service has finished successfully
-- A start job for unit systemd-networkd.service has finished successfully.
-- Subject: A start job for unit systemd-networkd-wait-online.service has begun execution
-- A start job for unit systemd-networkd-wait-online.service has begun execution.
Apr 26 23:43:49 focalltsp systemd-networkd-wait-online[297]: managing: eth0
-- Subject: A start job for unit systemd-networkd-wait-online.service has finished successfully
-- A start job for unit systemd-networkd-wait-online.service has finished successfully.
-- Subject: A start job for unit network.target has finished successfully
-- A start job for unit network.target has finished successfully.
-- Subject: A start job for unit network-online.target has finished successfully
-- A start job for unit network-online.target has finished successfully.
Apr 26 23:43:50 focalltsp systemd[1]: Starting Dispatcher daemon for systemd-networkd...
-- Subject: A start job for unit networkd-dispatcher.service has begun execution
-- A start job for unit networkd-dispatcher.service has begun execution.
Apr 26 23:43:50 focalltsp networkd-dispatcher[335]: No valid path found for iwconfig
Apr 26 23:43:50 focalltsp networkd-dispatcher[335]: No valid path found for iw
Apr 26 23:43:50 focalltsp systemd[1]: Started Dispatcher daemon for systemd-networkd.
-- Subject: A start job for unit networkd-dispatcher.service has finished successfully
-- A start job for unit networkd-dispatcher.service has finished successfully.
Apr 26 23:46:30 focalltsp systemd[1]: Stopping Dispatcher daemon for systemd-networkd...
-- Subject: A stop job for unit networkd-dispatcher.service has begun execution
-- A stop job for unit networkd-dispatcher.service has begun execution.
Apr 26 23:46:30 focalltsp systemd[1]: networkd-dispatcher.service: Succeeded.
-- The unit networkd-dispatcher.service has successfully entered the 'dead' state.
Apr 26 23:46:30 focalltsp systemd[1]: Stopped Dispatcher daemon for systemd-networkd.
-- Subject: A stop job for unit networkd-dispatcher.service has finished
-- A stop job for unit networkd-dispatcher.service has finished.
-- Subject: A stop job for unit network-online.target has finished
-- A stop job for unit network-online.target has finished.
-- Subject: A stop job for unit network.target has finished
-- A stop job for unit network.target has finished.
Apr 26 23:46:30 focalltsp systemd[1]: systemd-networkd-wait-online.service: Succeeded.
-- The unit systemd-networkd-wait-online.service has successfully entered the 'dead' state.
-- Subject: A stop job for unit systemd-networkd-wait-online.service has finished
-- A stop job for unit systemd-networkd-wait-online.service has finished.
-- Subject: A stop job for unit systemd-networkd.service has begun execution
-- A stop job for unit systemd-networkd.service has begun execution.
Apr 26 23:46:30 focalltsp systemd[1]: systemd-networkd.service: Succeeded.
-- The unit systemd-networkd.service has successfully entered the 'dead' state.
-- Subject: A stop job for unit systemd-networkd.service has finished
-- A stop job for unit systemd-networkd.service has finished.
-- Subject: A stop job for unit network-pre.target has finished
-- A stop job for unit network-pre.target has finished.
Apr 26 23:46:30 focalltsp systemd[1]: Stopped Initial cloud-init job (pre-networking).
Apr 26 23:49:34 focalltsp systemd[1]: Starting Initial cloud-init job (pre-networking)...
Apr 26 23:49:34 focalltsp systemd[1]: Finished Initial cloud-init job (pre-networking).
-- Subject: A start job for unit network-pre.target has finished successfully
-- A start job for unit network-pre.target has finished successfully.
-- Subject: A start job for unit systemd-networkd.service has begun execution
-- A start job for unit systemd-networkd.service has begun execution.
Apr 26 23:49:34 focalltsp systemd-networkd[215]: eth0: IPv6 successfully enabled
Apr 26 23:49:34 focalltsp systemd-networkd[215]: eth0: Gained IPv6LL
Apr 26 23:49:34 focalltsp systemd-networkd[215]: Enumeration completed
-- Subject: A start job for unit systemd-networkd.service has finished successfully
-- A start job for unit systemd-networkd.service has finished successfully.
-- Subject: A start job for unit systemd-networkd-wait-online.service has begun execution
-- A start job for unit systemd-networkd-wait-online.service has begun execution.
-- Subject: A start job for unit network.target has finished successfully
-- A start job for unit network.target has finished successfully.
Apr 26 23:49:35 focalltsp systemd-networkd[215]: eth0: DHCPv4 address 192.168.1.169/24 via 192.168.1.1
Apr 26 23:49:37 focalltsp systemd-networkd-wait-online[216]: managing: eth0
-- Subject: A start job for unit systemd-networkd-wait-online.service has finished successfully
-- A start job for unit systemd-networkd-wait-online.service has finished successfully.
-- Subject: A start job for unit network-online.target has finished successfully
-- A start job for unit network-online.target has finished successfully.
Apr 26 23:49:37 focalltsp systemd[1]: Starting Dispatcher daemon for systemd-networkd...
-- Subject: A start job for unit networkd-dispatcher.service has begun execution
-- A start job for unit networkd-dispatcher.service has begun execution.
Apr 26 23:49:38 focalltsp networkd-dispatcher[251]: No valid path found for iwconfig
Apr 26 23:49:38 focalltsp networkd-dispatcher[251]: No valid path found for iw
Apr 26 23:49:38 focalltsp systemd[1]: Started Dispatcher daemon for systemd-networkd.
-- Subject: A start job for unit networkd-dispatcher.service has finished successfully
-- A start job for unit networkd-dispatcher.service has finished successfully.
```

---

### Post by Tadaen_Sylvermane on 2020-04-26
Marking as solved. With nothing showing out of place I simply dumped the container and rebuilt. Seems fine so far.

---

