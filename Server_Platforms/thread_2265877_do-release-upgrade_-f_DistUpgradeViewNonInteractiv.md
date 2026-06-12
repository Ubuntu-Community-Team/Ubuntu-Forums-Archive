---
title: "do-release-upgrade -f DistUpgradeViewNonInteractive is broken"
date: 2015-02-18
forum: Server Platforms
---

### Post by hackeron on 2015-02-18
I seem to be affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/1382707](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/1382707)

When I run:
  
```
do-release-upgrade -f DistUpgradeViewNonInteractive
```

I expect to upgrade from Trusty to Utopic. Unfortunately, this command freezes and if I check /var/log/dist-upgrade/apt-term.log, I see:

```
Configuration file '/etc/sysctl.conf'^M
 ==> Modified (by you or by a script) since installation.^M
 ==> Package distributor has shipped an updated version.^M
   What would you like to do about it ? Your options are:^M
    Y or I : install the package maintainer's version^M
    N or O : keep your currently-installed version^M
      D : show the differences between the versions^M
      Z : start a shell to examine the situation^M
 The default action is to keep your current version.^M
*** sysctl.conf (Y/I/N/O/D/Z) [default=N] ?
```

This should not happen as I am specifying -f DistUpgradeViewNonInteractive.

Any solution/workaround for this?


EDIT: When I run ps aux, I see these relevant processes:

```

root     24531  0.0  0.2  18676  3872 pts/5    Ss+  14:36   0:00 /usr/bin/dpkg --force-overwrite --force-overwrite --status-fd 70 --configure libcgmanager0:amd64 libjson-c2:amd64 libnih1:amd64 libnih-dbus1:amd64 libudev1:amd64 initramfs-tools-bin:amd64 busybox-initramfs...
root      9120  4.2  3.7 237260 68500 pts/4    Ss+  14:25   1:45 /usr/bin/python3 /tmp/ubuntu-release-upgrader-hezptcnw/utopic --mode=server --frontend=DistUpgradeViewNonInteractive
root      7934  0.8  5.5 237256 100588 pts/3   S+   13:38   0:42 /usr/bin/python3 /tmp/ubuntu-release-upgrader-hezptcnw/utopic --mode=server --frontend=DistUpgradeViewNonInteractive

```

It seems I need a way for do-release-upgrade to pass something like -o Dpkg::Options::="--force-confdef" to apt-get and dpkg -- but question is how?

---

### Post by hackeron on 2015-02-18
It seems this works as a workaround. Create a file: /etc/apt/apt.conf.d/local with:

```
DPkg::options { "--force-confdef"; "--force-confnew"; }
```

Run do-release-upgrade -f DistUpgradeViewNonInteractive

Then remove that file.

Messy, but seems to work!!

---

