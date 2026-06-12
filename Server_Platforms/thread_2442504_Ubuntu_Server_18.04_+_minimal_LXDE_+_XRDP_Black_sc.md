---
title: "Ubuntu Server 18.04 + minimal LXDE + XRDP: Black screen"
date: 2020-05-04
forum: Server Platforms
---

### Post by nbun9u on 2020-05-04
I have installed a vanilla Ubuntu Server 18.04.4 and want to install a minimal desktop environment, accessible from Windows through RDP. I ran:

```

apt-get -y install lubuntu-core --no-install-recommends
apt-get -y install xrdp
adduser xrdp ssl-cert

```

All configuration files are left at their defaults.

Now, when I connect to the server using the Windows RDP client, I am greeted by the login dialog. I leave the default Session (Xorg), enter my credentials, and login succeeds. Afterwards, I only see a **completely black screen** instead of the desktop. How can I fix this?

/var/log/xrdp.log:

```

[20200504-12:41:02] [DEBUG] xrdp_00002995_wm_login_mode_event_00000001
[20200504-12:41:02] [INFO ] Loading keymap file /etc/xrdp/km-00000407.ini
[20200504-12:41:02] [WARN ] local keymap file for 0x00000407 found and doesn't match built in keymap, using local keymap file
[20200504-12:41:09] [DEBUG] xrdp_wm_log_msg: connecting to sesman ip 127.0.0.1 port 3350
[20200504-12:41:10] [INFO ] xrdp_wm_log_msg: sesman connect ok
[20200504-12:41:10] [DEBUG] xrdp_wm_log_msg: sending login info to session manager, please wait...
[20200504-12:41:10] [DEBUG] return value from xrdp_mm_connect 0
[20200504-12:41:10] [INFO ] xrdp_wm_log_msg: login successful for display 10
[20200504-12:41:10] [DEBUG] xrdp_wm_log_msg: started connecting
[20200504-12:41:10] [INFO ] lib_mod_log_peer: xrdp_pid=10645 connected to X11rdp_pid=10649 X11rdp_uid=1000 X11rdp_gid=1000 client_ip=::ffff:192.168.1.2 client_port=56377
[20200504-12:41:10] [DEBUG] xrdp_wm_log_msg: connected ok
[20200504-12:41:10] [DEBUG] xrdp_mm_connect_chansrv: chansrv connect successful
[20200504-12:41:10] [DEBUG] Closed socket 26 (AF_INET6 ::ffff:127.0.0.1 port 52522)
[20200504-12:41:10] [INFO ] The following channel is allowed: rdpdr (0)
[20200504-12:41:10] [INFO ] The following channel is allowed: rdpsnd (1)
[20200504-12:41:10] [INFO ] The following channel is allowed: cliprdr (2)
[20200504-12:41:10] [INFO ] The following channel is allowed: drdynvc (3)
[20200504-12:41:10] [DEBUG] The allow channel list now initialized for this session

```

/var/log/xrdp-sesman.log:

```

[20200504-12:41:09] [INFO ] A connection received from ::ffff:127.0.0.1 port 52522
[20200504-12:41:10] [INFO ] ++ created session (access granted): username user, ip ::ffff:192.168.1.2:56377 - socket: 12
[20200504-12:41:10] [INFO ] starting Xorg session...
[20200504-12:41:10] [DEBUG] Closed socket 9 (AF_INET6 :: port 5910)
[20200504-12:41:10] [DEBUG] Closed socket 9 (AF_INET6 :: port 6010)
[20200504-12:41:10] [DEBUG] Closed socket 9 (AF_INET6 :: port 6210)
[20200504-12:41:10] [DEBUG] Closed socket 8 (AF_INET6 ::ffff:127.0.0.1 port 3350)
[20200504-12:41:10] [INFO ] calling auth_start_session from pid 10647
[20200504-12:41:10] [DEBUG] Closed socket 7 (AF_INET6 ::ffff:127.0.0.1 port 3350)
[20200504-12:41:10] [DEBUG] Closed socket 8 (AF_INET6 ::ffff:127.0.0.1 port 3350)
[20200504-12:41:10] [INFO ] /usr/lib/xorg/Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp.%s.log
[20200504-12:41:10] [CORE ] waiting for window manager (pid 10648) to exit

```

Logging in locally (through lightdm) works without problems.

---

### Post by slickymaster on 2020-05-04
*Thread moved to **Server Platforms**.*

---

### Post by nbun9u on 2020-05-04
I was able to fix the issue: It turns out a file named ~/.xsession was missing.

Solution (execute as the user that you want to login as remotely):

```

echo "lxsession -s Lubuntu -e LXDE" > ~/.xsession
sudo systemctl restart xrdp

```

---

