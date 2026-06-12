---
title: "xl commands doesn't work in openvpn scripts"
date: 2020-05-05
forum: Server Platforms
---

### Post by ernestofileev on 2020-05-05
Hello,

[COLOR=#242729][FONT=Arial]I have script with xl command (Xen 4.9) which run by OpenVPN (Ubuntu server 19.04).

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]In my openvpn config:
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]script-security 2 [/FONT][/COLOR]
[COLOR=#242729][FONT=Consolas]up /etc/xen/scripts/vpn.sh[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]In my script commans like this:[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]TEST=`xl domid test`[/FONT][/COLOR]
```

[COLOR=#242729][FONT=Arial]So. If I run this script in root console everything is good, but OpenVPN (systemd, run by root) excute this scripts with errors:
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]xencall: error: Could not obtain handle on privileged command interface: Operation not permitted
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]libxl: error: libxl.c:102:libxl_ctx_alloc: cannot open libxc handle: Operation not permitted [/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]cannot init xl context[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]OpenVPN run by root (systemd):
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]root@MS /etc/openvpn # ps -Af|grep openvpn
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]root      3257     1  0 02:08 ?        00:00:01 /usr/sbin/openvpn --daemon ovpn-b2b --status /run/openvpn/b2b.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/b2b.conf --> writepid /run/openvpn/b2b.pid[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]If I run OpenVPN with similar config in root console, script is run without error. What is problem?[/FONT][/COLOR]

---

### Post by TheFu on 2020-05-05
19.04 support ended months ago. Please move to a supported release.

Without seeing the content of all scripts and configs, doubt i can help.  Aso need to see the network settings, routes, before and after the VPN is running.  Both the working and non-working setups.  My openvpn scripts are nothing like what is posted above.

---

