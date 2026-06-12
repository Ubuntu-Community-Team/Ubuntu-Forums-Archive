---
title: "ubuntu 20.04 systemd-logind.service crashing"
date: 2020-05-12
forum: Server Platforms
---

### Post by sbuxhofer on 2020-05-12
on a vanilla ubuntu 20.04 lxc container install on proxmox 6.0 the systemd-logind.service is crashing. Upon login, console or ssh it takes a while before prompt shows; in the background the systemd-logind service is crashing several times. It seems masking the service is the only workaround. Changing the container to unprivileged did not resolve it either. The trashing of the service seems to have started after 1st ssh login.

LXC config:

```
arch: amd64cores: 2
hostname: testsystem
memory: 2048
net0: name=eth0,bridge=vmbr0,hwaddr=F6:E6:99:99:DF:19,ip=dhcp,ip6=auto,type=veth
net1: name=eth1,bridge=vmbr0,hwaddr=DE:F0:A1:BC:72:46,ip6=auto,tag=20,type=veth
ostype: ubuntu
rootfs: pve-disk:vm-3001-disk-0,size=16G
swap: 0
unprivileged: 1
```

Syslog:
```
May 12 04:47:14 testsystem dbus-daemon[100]: [system] Activating via systemd: service name='org.freedesktop.login1' unit='dbus-org.freedesktop.login1.service' requested by ':1.8' (uid=0 pid=404 comm="sshd: sbuxhofer [priv] " label="unconfined")
May 12 04:47:14 testsystem systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
May 12 04:47:14 testsystem systemd[1]: Starting Login Service...
May 12 04:47:14 testsystem systemd[406]: systemd-logind.service: Failed to set up special execution directory in /var/lib: Oper
ation not permitted
May 12 04:47:14 testsystem systemd[406]: systemd-logind.service: Failed at step STATE_DIRECTORY spawning /lib/systemd/systemd-l
ogind: Operation not permitted
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Main process exited, code=exited, status=238/STATE_DIRECTORY
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Failed with result 'exit-code'.
May 12 04:47:14 testsystem systemd[1]: Failed to start Login Service.
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Scheduled restart job, restart counter is at 1.
May 12 04:47:14 testsystem systemd[1]: Stopped Login Service.
May 12 04:47:14 testsystem systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
May 12 04:47:14 testsystem systemd[1]: Starting Login Service...
May 12 04:47:14 testsystem systemd[409]: systemd-logind.service: Failed to set up special execution directory in /var/lib: Oper
ation not permitted
May 12 04:47:14 testsystem systemd[409]: systemd-logind.service: Failed at step STATE_DIRECTORY spawning /lib/systemd/systemd-l
ogind: Operation not permitted
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Main process exited, code=exited, status=238/STATE_DIRECTORY
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Failed with result 'exit-code'.
May 12 04:47:14 testsystem systemd[1]: Failed to start Login Service.
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Scheduled restart job, restart counter is at 2.
May 12 04:47:14 testsystem systemd[1]: Stopped Login Service.
May 12 04:47:14 testsystem systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
May 12 04:47:14 testsystem systemd[1]: Starting Login Service...
May 12 04:47:14 testsystem systemd[412]: systemd-logind.service: Failed to set up special execution directory in /var/lib: Oper
ation not permitted
May 12 04:47:14 testsystem systemd[412]: systemd-logind.service: Failed at step STATE_DIRECTORY spawning /lib/systemd/systemd-l
ogind: Operation not permitted
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Main process exited, code=exited, status=238/STATE_DIRECTORY
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Failed with result 'exit-code'.
May 12 04:47:14 testsystem systemd[1]: Failed to start Login Service.
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Scheduled restart job, restart counter is at 3.
May 12 04:47:14 testsystem systemd[1]: Stopped Login Service.
May 12 04:47:14 testsystem systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
May 12 04:47:14 testsystem systemd[1]: Starting Login Service...
May 12 04:47:14 testsystem systemd[415]: systemd-logind.service: Failed to set up special execution directory in /var/lib: Oper
ation not permitted
May 12 04:47:14 testsystem systemd[415]: systemd-logind.service: Failed at step STATE_DIRECTORY spawning /lib/systemd/systemd-l
ogind: Operation not permitted
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Main process exited, code=exited, status=238/STATE_DIRECTORY
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Failed with result 'exit-code'.
May 12 04:47:14 testsystem systemd[1]: Failed to start Login Service.
May 12 04:47:14 testsystem systemd[1]: systemd-logind.service: Scheduled restart job, restart counter is at 4.
May 12 04:47:14 testsystem systemd[1]: Stopped Login Service.
May 12 04:47:14 testsystem systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
May 12 04:47:14 testsystem systemd[1]: Starting Login Service...
May 12 04:47:14 testsystem systemd[418]: systemd-logind.service: Failed to set up special execution directory in /var/lib: Oper
ation not permitted
May 12 04:47:14 testsystem systemd[418]: systemd-logind.service: Failed at step STATE_DIRECTORY spawning /lib/systemd/systemd-l
ogind: Operation not permitted
```

---

### Post by LHammonds on 2020-05-12
```
systemd-logind.service: Failed to set up special execution directory in /var/lib: Operation not permitted
```

Makes me think there is a permission or space problem.

Easy to make sure we are not looking at a space issue by doing this:

```
df -h
```

Once you do that, then we can start looking at the permissions around /var/lib and /var/systemd

LHammonds

---

### Post by sbuxhofer on 2020-05-12
The system has sufficient space, its a 16G lxc container:

```
df -kh
Filesystem                              Size  Used Avail Use% Mounted on
/dev/mapper/vg--disk-vm--3001--disk--0   16G  853M   14G   6% /
none                                    492K     0  492K   0% /dev
udev                                     48G     0   48G   0% /dev/tty
tmpfs                                    48G     0   48G   0% /dev/shm
tmpfs                                   9.5G  100K  9.5G   1% /run
tmpfs                                   5.0M     0  5.0M   0% /run/lock
tmpfs                                    48G     0   48G   0% /sys/fs/cgroup
```

looking at permissions, though I do not see a "/var/systemd directory.

```
ll /var/lib/total 108
drwxr-xr-x 27 root    root    4096 Apr 25 13:53 ./
drwxr-xr-x 11 root    root    4096 May 12 05:08 ../
drwxr-xr-x  4 root    root    4096 Apr 25 13:53 AccountsService/
drwxr-xr-x  5 root    root    4096 May 12 01:09 apt/
drwxr-xr-x  2 root    root    4096 May 11 07:23 command-not-found/
drwxr-xr-x  2 root    root    4096 May 11 07:15 dbus/
drwxr-xr-x  2 root    root    4096 Apr 10 17:21 dhcp/
drwxr-xr-x  7 root    root    4096 May 11 08:46 dpkg/
drwxr-xr-x  2 root    root    4096 May 12 00:00 logrotate/
drwxr-xr-x  2 root    root    4096 Apr 25 13:53 man-db/
drwxr-xr-x  2 root    root    4096 Apr 15 11:09 misc/
drwxr-xr-x  2 root    root    4096 Apr 25 13:53 pam/
drwxr-xr-x  2 root    root    4096 Apr  1 09:49 plymouth/
drwxr-xr-x  3 root    root    4096 Apr 25 13:52 polkit-1/
drwxr-xr-x  2 postfix postfix 4096 May 11 07:13 postfix/
drwx------  2 nobody  nogroup 4096 Apr 25 13:53 private/
drwxr-xr-x  2 root    root    4096 Apr 25 13:52 python/
drwxr-xr-x  3 root    root    4096 Apr 25 13:52 sudo/
drwxr-xr-x  7 nobody  nogroup 4096 May 11 07:13 systemd/
drwxr-xr-x  2 root    root    4096 Mar 30 20:49 ubuntu-advantage/
drwxr-xr-x  2 root    root    4096 May 11 10:16 ubuntu-release-upgrader/
drwxr-xr-x  3 root    root    4096 Apr 25 13:53 ucf/
drwxr-xr-x  2 root    root    4096 May 11 10:16 update-manager/
drwxr-xr-x  2 root    root    4096 Apr 17 22:06 update-notifier/
drwxr-xr-x  2 root    root    4096 Apr 25 13:53 usbutils/
drwxr-xr-x  3 root    root    4096 Apr 25 13:52 vim/
drwxr-xr-x  2 root    root    4096 Feb 28 20:13 xkb/
```

---

