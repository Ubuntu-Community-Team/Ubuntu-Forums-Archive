---
title: "lxc: artful host + artful guest = no ip on guest?"
date: 2017-09-01
forum: Ubuntu Development Version
---

### Post by dankegel on 2017-09-01
Reported at
[https://lists.linuxcontainers.org/pipermail/lxc-users/2017-September/013646.html](https://lists.linuxcontainers.org/pipermail/lxc-users/2017-September/013646.html)
but repeated here just in case:

On an up to date 17.10 alpha on amd64, lxd works:

```
$ sudo apt install lxd lxd-client
$ sudo lxc init
$ lxc launch ubuntu-daily:17.10 lxd-1710
$ lxc list
+----------+---------+-----------------------+------+------------+-----------+
|   NAME   |  STATE  |         IPV4          | IPV6 |    TYPE    | SNAPSHOTS |
+----------+---------+-----------------------+------+------------+-----------+
| lxd-1710 | RUNNING | 10.201.190.247 (eth0) |      | PERSISTENT | 0         |
+----------+---------+-----------------------+------+------------+-----------+
```

while lxc-create/lxc-start/lxc-ls create containers without IP
addresses (for both ubuntu and download templates):

```
$ sudo apt install lxc
$ sudo lxc-create -n demo-1710 -t ubuntu -- -r artful
$ sudo lxc-start -n demo-1710
$ sleep 5
$ sudo lxc-ls -f
NAME                  STATE   AUTOSTART GROUPS IPV4 IPV6
demo-1710             RUNNING 0         -      -    -
```
```
$ sudo lxc-create -n demo2-1710 -t download -- --dist ubuntu --release
artful --arch amd64
$ sleep 5
```
```
$ sudo lxc-ls -f
NAME                  STATE   AUTOSTART GROUPS IPV4 IPV6
demo-1710             RUNNING 0         -      -    -
demo2-1710            RUNNING 0         -      -    -

```
The problem appears to be in the guest:
```
$ sudo lxc-create -n demo-1704 -t ubuntu -- -r zesty
$ sudo lxc-start -n demo-1704
$ sleep 5
$ sudo lxc-ls -f
NAME                  STATE   AUTOSTART GROUPS IPV4      IPV6
demo-1704             RUNNING 0         -      10.0.3.16 -
demo-1710             RUNNING 0         -      -         -
demo2-1710            RUNNING 0         -      -         -

```
...

The lxc-users mailing list post has more detail.

---

### Post by amano on 2017-09-03
This seems to be the wrong place to report that problem. You should file a bug on lauchpad, otherwise no Ubuntu developer will have a look.

---

