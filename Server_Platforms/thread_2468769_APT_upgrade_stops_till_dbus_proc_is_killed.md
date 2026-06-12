---
title: "APT upgrade stops till dbus proc is killed"
date: 2021-11-10
forum: Server Platforms
---

### Post by nts-workspace on 2021-11-10
Hi all
It looks like, sometimes if systemd is updated with apt, the Upgrade process stucks till the Process "dbus" is killed.
```

10.11 09:08:22 root|host1:~$ cat /var/log/dpkg.log.1
----------------- %< -----------------
2021-11-09 21:01:19 configure systemd:amd64 237-3ubuntu10.52 <none>
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status unpacked systemd:amd64 237-3ubuntu10.52
2021-11-09 21:01:19 status half-configured systemd:amd64 237-3ubuntu10.52 <<<<<< stucks
2021-11-09 21:08:50 status installed systemd:amd64 237-3ubuntu10.52 <<<<<<<<<<< after killing dbus process, the upgrade runs again
2021-11-09 21:08:50 startup archives unpack
2021-11-09 21:08:50 upgrade systemd-sysv:amd64 237-3ubuntu10.48 237-3ubuntu10.52
2021-11-09 21:08:50 status half-configured systemd-sysv:amd64 237-3ubuntu10.48
2021-11-09 21:08:50 status unpacked systemd-sysv:amd64 237-3ubuntu10.48
2021-11-09 21:08:50 status half-installed systemd-sysv:amd64 237-3ubuntu10.48


```

dbus Version
```

10.11 09:12:16 root|host1:~$ dpkg -l | grep dbus
ii  dbus                                   1.12.2-1ubuntu1.2                               amd64        simple interprocess messaging system (daemon and utilities)
ii  libdbus-1-3:amd64                      1.12.2-1ubuntu1.2                               amd64        simple interprocess messaging system (library)
ii  libdbus-glib-1-2:amd64                 0.110-2                                         amd64        deprecated library for D-Bus IPC
ii  python-dbus                            1.2.6-1                                         amd64        simple interprocess messaging system (Python interface)
ii  python3-dbus                           1.2.6-1                                         amd64        simple interprocess messaging system (Python 3 interface)

```

Systemd Version:
```

10.11 09:12:20 root|host1:~$ dpkg -l | grep systemd
ii  libnss-systemd:amd64                   237-3ubuntu10.52                                amd64        nss module providing dynamic user and group name resolution
ii  libpam-systemd:amd64                   237-3ubuntu10.52                                amd64        system and service manager - PAM module
ii  libsystemd0:amd64                      237-3ubuntu10.52                                amd64        systemd utility library
ii  networkd-dispatcher                    1.7-0ubuntu3.3                                  all          Dispatcher service for systemd-networkd connection status changes
ii  python3-systemd                        234-1build1                                     amd64        Python 3 bindings for systemd
ii  systemd                                237-3ubuntu10.52                                amd64        system and service manager
ii  systemd-sysv                           237-3ubuntu10.52                                amd64        system and service manager - SysV links

```

System:
```

10.11 09:13:13 root|host1:~$ uname -a
Linux rpki1 4.15.0-147-generic #151-Ubuntu SMP Fri Jun 18 19:21:19 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

10.11 09:13:41 root|host1:~$ cat /etc/os-release 
NAME="Ubuntu"
VERSION="18.04.6 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.6 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

```

Does anybody have some hints about this behaviour?
If you need more printouts, please let me know!

Thank you very much!
BR A

---

