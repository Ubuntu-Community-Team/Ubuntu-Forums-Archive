---
title: "my VPN connection drops when my computer is inactive"
date: 2017-10-04
forum: Server Platforms
---

### Post by necb on 2017-10-04
I have an VPN that I connect to through OpenVPN.  I noticed that when I step away from my computer for a while and come back that I cannot connect to the internet.  Even a simple command such as "ping google.com" does nothing.  I can only connect when I disconnect from my VPN and reconnect.  Any tips to prevent this from happening?  Thanks.

---

### Post by wildmanne39 on 2017-10-04
*Thread moved to **Server Platforms for a better fit**.*

---

### Post by necb on 2017-10-04
Also my log is full of this...

> Oct  4 23:17:05 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:20:45 htpc nm-openvpn[2006]: message repeated 44 times: [ RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution]
Oct  4 23:20:50 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:27:40 htpc nm-openvpn[2006]: message repeated 82 times: [ RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution]
Oct  4 23:27:45 htpc systemd-timesyncd[618]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Oct  4 23:27:45 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:27:50 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:27:55 htpc systemd-timesyncd[618]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Oct  4 23:27:55 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:28:00 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:28:05 htpc systemd-timesyncd[618]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Oct  4 23:28:05 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:28:15 htpc nm-openvpn[2006]: message repeated 2 times: [ RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution]
Oct  4 23:28:15 htpc systemd-timesyncd[618]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
Oct  4 23:28:20 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:29:10 htpc nm-openvpn[2006]: message repeated 10 times: [ RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution]
Oct  4 23:29:11 htpc systemd[1]: snapd.refresh.timer: Adding 4h 41min 31.526592s random time.
Oct  4 23:29:15 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:43:36 htpc nm-openvpn[2006]: message repeated 172 times: [ RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution]
Oct  4 23:43:41 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution
Oct  4 23:47:06 htpc nm-openvpn[2006]: message repeated 41 times: [ RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution]
Oct  4 23:47:08 htpc wpa_supplicant[1027]: wlx681ca201d2b8: WPA: Group rekeying completed with 28:c6:8e:87:b0:39 [GTK=CCMP]
Oct  4 23:47:11 htpc nm-openvpn[2006]: RESOLVE: Cannot resolve host address: nyc-a01.ipvanish.com: Temporary failure in name resolution


So probably a DNS issue?

---

### Post by tina-brown11 on 2017-10-05
Not sure which VPN you are using, but it sounds like it is your kill-switch kicking in.  Essentially, if your wifi or internet connection is unstable, your VPN would kill your connection for you so that you are not accidentally leaking personal details about yourself.  Not sure which provider you use, but with mine for example (express vpn) you can disable the network lock but I am not sure how smart that would be since a network lock is very important for ensuring that you don't share private internet info you didn't intend to.

---

