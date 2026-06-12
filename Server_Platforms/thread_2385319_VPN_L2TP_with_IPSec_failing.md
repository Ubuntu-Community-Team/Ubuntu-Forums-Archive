---
title: "VPN L2TP with IPSec failing"
date: 2018-02-19
forum: Server Platforms
---

### Post by martin022 on 2018-02-19
Hello, I need l2tp vpn working so I followed guide to get l2tp working with ipsec, installed required packages (intltool libtool network-manager-dev libnm-util-dev libnm-glib-dev libnm-glib-vpn-dev libnm-gtk-dev libnm-dev libnma-dev ppp-dev libdbus-glib-1-dev libsecret-1-dev libgtk-3-dev libglib2.0-dev xl2tpd strongswan) + network-manager-l2tp from ppa, but it just could not load bliss plugin.. before blis it was another one, and another.. Every time, charon dies. I'v searched this like million times.

Does somebody know solution for this? 


every package is latest version from ppa's (strongswan 5.3.5-1ubuntu3.4, etc..) on KDE.

here is journalctl output:
```

Feb 19 08:02:08 xxx wpa_supplicant[1414]: wlp2s0: WPA: Group rekeying completed with macaddr [GTK=CCMP]
Feb 19 08:02:10 xxx NetworkManager[1110]: <info>  [1519023730.4066] audit: op="connection-activate" uuid="uuid" name="l2tpvpn" pid=1912 uid=1000 result="success"
Feb 19 08:02:10 xxx NetworkManager[1110]: <info>  [1519023730.4307] vpn-connection[0xc76790,3cd543f2-3f51-4a7d-927e-ff7e3cfb528f,"l2tpvpn",0]: Started the VPN service, PID 6382
Feb 19 08:02:10 xxx NetworkManager[1110]: <info>  [1519023730.4565] vpn-connection[0xc76790,3cd543f2-3f51-4a7d-927e-ff7e3cfb528f,"l2tpvpn",0]: Saw the service appear; activating connection
Feb 19 08:02:10 xxx NetworkManager[1110]: nm-l2tp[6382] <info>  ipsec enable flag: yes
Feb 19 08:02:10 xxx NetworkManager[1110]: ** Message: Check port 1701
Feb 19 08:02:10 xxx NetworkManager[1110]: ** Message: Can't bind to port 1701
Feb 19 08:02:10 xxx NetworkManager[1110]: nm-l2tp[6382] <warn>  L2TP port 1701 is busy, using ephemeral.
Feb 19 08:02:10 xxx NetworkManager[1110]: nm-l2tp[6382] <info>  starting ipsec
Feb 19 08:02:10 xxx NetworkManager[1110]: Stopping strongSwan IPsec failed: starter is not running
Feb 19 08:02:12 xxx NetworkManager[1110]: Starting strongSwan 5.6.1 IPsec [starter]...
Feb 19 08:02:12 xxx NetworkManager[1110]: Loading config setup
Feb 19 08:02:12 xxx NetworkManager[1110]: Loading conn 'uuid'
Feb 19 08:02:12 xxx ipsec_starter[6396]: Starting strongSwan 5.6.1 IPsec [starter]...
Feb 19 08:02:12 xxx ipsec_starter[6396]: Loading config setup
Feb 19 08:02:12 xxx ipsec_starter[6396]: Loading conn 'uuid'
Feb 19 08:02:12 xxx NetworkManager[1110]: found netkey IPsec stack
Feb 19 08:02:12 xxx ipsec_starter[6396]: found netkey IPsec stack
Feb 19 08:02:12 xxx ipsec_starter[6418]: Attempting to start charon...
Feb 19 08:02:12 xxx charon[6419]: 00[DMN] Starting IKE charon daemon (strongSwan 5.6.1, Linux 4.13.0-32-generic, x86_64)
Feb 19 08:02:12 xxx charon[6419]: 00[LIB] plugin 'bliss' failed to load: /usr/lib/ipsec/plugins/libstrongswan-bliss.so: undefined symbol: mgf1_bitspender_create
Feb 19 08:02:12 xxx kernel: charon[6419]: segfault at 2 ip 00007fbe07262746 sp 00007fffe971b0c8 error 4 in libc-2.23.so[7fbe071d7000+1c0000]
Feb 19 08:02:12 xxx ipsec_starter[6418]: child 6419 (charon) has been killed by sig 11
Feb 19 08:02:12 xxx ipsec_starter[6418]:  
Feb 19 08:02:12 xxx ipsec_starter[6418]: charon has died -- restart scheduled (5sec)
Feb 19 08:02:12 xxx ipsec_starter[6418]: charon refused to be started
Feb 19 08:02:17 xxx ipsec_starter[6418]: Attempting to start charon...
Feb 19 08:02:17 xxx charon[6446]: 00[DMN] Starting IKE charon daemon (strongSwan 5.6.1, Linux 4.13.0-32-generic, x86_64)
Feb 19 08:02:17 xxx charon[6446]: 00[LIB] plugin 'bliss' failed to load: /usr/lib/ipsec/plugins/libstrongswan-bliss.so: undefined symbol: mgf1_bitspender_create
Feb 19 08:02:17 xxx kernel: charon[6446]: segfault at 2 ip 00007fae9292a746 sp 00007fff761a7e28 error 4 in libc-2.23.so[7fae9289f000+1c0000]
Feb 19 08:02:17 xxx ipsec_starter[6418]: child 6446 (charon) has been killed by sig 11
Feb 19 08:02:17 xxx ipsec_starter[6418]:  
Feb 19 08:02:17 xxx ipsec_starter[6418]: charon has died -- restart scheduled (5sec)
Feb 19 08:02:17 xxx ipsec_starter[6418]: charon refused to be started
Feb 19 08:02:22 xxx NetworkManager[1110]: nm-l2tp[6382] <warn>  IPsec service is not ready.
Feb 19 08:02:22 xxx NetworkManager[1110]: Stopping strongSwan IPsec...
Feb 19 08:02:22 xxx ipsec_starter[6418]: ipsec starter stopped
Feb 19 08:02:22 xxx NetworkManager[1110]: nm-l2tp[6382] <warn>  Could not establish IPsec tunnel.
Feb 19 08:02:22 xxx NetworkManager[1110]: (nm-l2tp-service:6382): GLib-GIO-CRITICAL **: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
Feb 19 08:02:22 xxx NetworkManager[1110]: <info>  [1519023742.6971] vpn-connection[0xc76790,3cd543f2-3f51-4a7d-927e-ff7e3cfb528f,"l2tpvpn",0]: VPN service disappeared
Feb 19 08:02:22 xxx NetworkManager[1110]: <warn>  [1519023742.7002] vpn-connection[0xc76790,3cd543f2-3f51-4a7d-927e-ff7e3cfb528f,"l2tpvpn",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'

```

---

### Post by wildmanne39 on 2018-02-19
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by dkosovic on 2018-03-12
Most of the dependencies you installed are for building the network-manager-l2tp source code, but are harmless for running.

You only need the following strongswan packages :

[LIST]
[*]strongswan 
[*]strongswan-charon 
[*]strongswan-libcharon 
[*]strongswan-starter 
[*]strongswan-starter 
[*]libstrongswan 
[*]libstrongswan-standard-plugins 
[/LIST]
The libstrongswan-extra-plugins package which has the bliss plug-in isn't required.

If you are still having issues with strongswan, you could install libreswan instead :

```
sudo apt install libreswan
```

Also be sure to look at the "Issue with not stopping system xl2tpd service" and "Issue with VPN servers only proposing IPsec IKEv1 weak legacy algorithms" sections of the README.md file :

[LIST]
[*][https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service](https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service) 
[/LIST]

---

### Post by beyhansen on 2018-10-20
Thank you. I changed strongswan to libreswan and it's working now.

---

