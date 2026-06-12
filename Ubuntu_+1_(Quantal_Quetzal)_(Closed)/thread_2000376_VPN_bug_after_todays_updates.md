---
title: "VPN bug after todays updates"
date: 2012-06-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sammiev on 2012-06-09
My VPN looses connection after 1 min on 12.10 but works great on 12.04 on the same computer. Just started after today’s updates. Anyone else come across this bug as well?
Sam

---

### Post by pressureman on 2012-06-09
It would be helpful if you described what type of VPN connection, as there are many.

I'm going to assume you mean OpenVPN, because yes, I've noticed the same problem. The connection drops after 40s.

The VPN plugin appears to be exiting unexpectedly:

```

Jun  9 16:53:13 thinkpad NetworkManager[1323]: <info> VPN plugin state changed: stopping (5)
Jun  9 16:53:13 thinkpad NetworkManager[1323]: <info> VPN plugin state changed: stopped (6)
Jun  9 16:53:13 thinkpad NetworkManager[1323]: <info> VPN plugin state change reason: 0
Jun  9 16:53:13 thinkpad avahi-daemon[1310]: Withdrawing workstation service for tun0.

```

---

### Post by sammiev on 2012-06-09
I'm using pptp on WiTopia but with the same results.
Thanks

---

### Post by pressureman on 2012-06-09
So that would appear to imply that Network Manager is at fault, since it's happening with two separate plugins.

---

### Post by sammiev on 2012-06-09
> **pressureman said:**
> So that would appear to imply that Network Manager is at fault, since it's happening with two separate plugins.

I agree and Network Manager was one of the updates I took today.

---

### Post by pressureman on 2012-06-12
I tried running the openvpn plugin in the foreground like so:

```
sudo OPENVPN_DEBUG=1 /usr/lib/NetworkManager/nm-openvpn-service
```

which yielded all the debug during the connection phase, and I could see keepalive pings occurring. The VPN was up - I was able to ping the remote server. But then as the VPN automatically disconnected itself, I saw the following:

```

** Message: Connect timer expired, disconnecting.
** Message: Terminated openvpn daemon with PID 21424.
Tue Jun 12 09:21:14 2012 us=793779 PO_WAIT[2,0] fd=5 rev=0x00000001 rwflags=0x0001 arg=0x7f30c66ce068 
Tue Jun 12 09:21:14 2012 us=793833  event_wait returned 1
Tue Jun 12 09:21:14 2012 us=793862 I/O WAIT status=0x0040
Tue Jun 12 09:21:14 2012 us=793907 PID packet_id_free
Tue Jun 12 09:21:14 2012 us=794028 SSL alert (write): warning: close notify
Tue Jun 12 09:21:14 2012 us=794834 TCP/UDP: Closing socket
Tue Jun 12 09:21:14 2012 us=794889 Closing TUN/TAP interface
Tue Jun 12 09:21:14 2012 us=806547 SIGTERM[hard,] received, process exiting

```

Searching through the networkmanager source, I found the "Connect timer expired, disconnecting" message in libnm-glib/nm-vpn-plugin.c, in the function connect_timer_expired(). This function is called from the following code snippet, in the same file:

```

                /* Add a timer to make sure we do not wait indefinitely for the successful connect. */
                priv->connect_timer = g_timeout_add_seconds_full (G_PRIORITY_DEFAULT,
                                                                  NM_VPN_PLUGIN_CONNECT_TIMER,
                                                                  connect_timer_expired,
                                                                  plugin,
                                                                  connect_timer_removed);

```

This confirms that it should not be limited to just the openvpn plugin (in my case), or even specific VPN plugins, but rather *all* VPN plugins. It would also appear that for whatever reason, network manager either doesn't think the plugin has connected (seems unlikely, since the GUI definitely indicates successful connection), or that it's not killing that timer upon successful connection.

---

### Post by pressureman on 2012-06-12
Looks like this has been acknowledged and fixed upstream - very recently:

[http://cgit.freedesktop.org/NetworkManager/NetworkManager/commit/libnm-glib/nm-vpn-plugin.c?id=11b8574f07ca1df74b84c51195ba76a3218d4c54](http://cgit.freedesktop.org/NetworkManager/NetworkManager/commit/libnm-glib/nm-vpn-plugin.c?id=11b8574f07ca1df74b84c51195ba76a3218d4c54)

The commit message describes the problem exactly.

I've opened an Ubuntu bug at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991) - add yourself to that bug if it affects you, so it can get some attention.

---

### Post by sammiev on 2012-06-12
> **pressureman said:**
> Looks like this has been acknowledged and fixed upstream - very recently:

[http://cgit.freedesktop.org/NetworkManager/NetworkManager/commit/libnm-glib/nm-vpn-plugin.c?id=11b8574f07ca1df74b84c51195ba76a3218d4c54](http://cgit.freedesktop.org/NetworkManager/NetworkManager/commit/libnm-glib/nm-vpn-plugin.c?id=11b8574f07ca1df74b84c51195ba76a3218d4c54)

The commit message describes the problem exactly.

I've opened an Ubuntu bug at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991) - add yourself to that bug if it affects you, so it can get some attention.

Added. :)

---

### Post by sammiev on 2012-07-16
It seems the latest updates from tonight fixed the VPN bug. Thread now marked as solved.

---

