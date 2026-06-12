---
title: "Stopped LVM2 metadata daemon - Sits here for several minutes upon reboot"
date: 2017-02-02
forum: Server Platforms
---

### Post by LHammonds on 2017-02-02
I installed a fresh server from scratch using the 16.04.1 LTS ISO image and noticed the 1st time I issued the reboot command (via PuTTY), the server didn't come back...which usually happens in about 10 seconds.

I jumped directly on the console and noticed that it was in the shutdown process but seemed to hang up after the following lines:

```

[ OK ] Stopped File System Check on /dev/disk/by-uuid/asdf-asdf-asdf-asdfsfadfs.
[ OK ] Removed slice system-systemd\x2dfsck.slice.
[ OK ] Stopped target Local File Systems (Pre).
       Stopping Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or process polling...
[ OK ] Stopped Remount Root and Kernel File Systems.
[ OK ] Stopped Create Static Device Nodes in /dev.
[ OK ] Stopped monitoring of LVM2 mirrors, snapshots etc. using dmeventd or process polling.
       Stopping LVM2 metadata daemon.......
[ OK ] Stopped LVM2 metadata daemon.
```

After exactly 10 minutes, it throws out some red text and immediately reboots before I can read what it said.

When booting up, it seems to take a tad bit longer than what it should when it says the following (pauses here for about 10 seconds):

```

Begin: Mounting /usr file system ...
```

The same scenario happens if I issue the shutdown command "shutdown -P now" or the reboot command.

I thought I did something wrong when I was going through the LVM creation process so I wiped out the server and created a new one from scratch.  The exact same thing happened.

I have thoroughly documented the steps I take when [installing a server here]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220") and have setup 3 servers that were initially setup using the 16.04 ISO image before the 1st point release.

This is a VMware environment so the hardware is not likely the issue.  I have setup a couple dozen servers on this platform since Ubuntu 10.04.  But just to be sure, I did specify a different host and storage LUN the 2nd time round.

I did notice that open-vm-tools was installed automatically as part of the initial setup.  Not sure if that has anything to do with it though but it is something new in the install process.

More info:

```
root@srv-ubuntu:/# lvscan
  ACTIVE            '/dev/LVG/root' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/swap' [1.86 GiB] inherit
  ACTIVE            '/dev/LVG/home' [188.00 MiB] inherit
  ACTIVE            '/dev/LVG/tmp' [476.00 MiB] inherit
  ACTIVE            '/dev/LVG/usr' [4.00 GiB] inherit
  ACTIVE            '/dev/LVG/var' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/srv' [188.00 MiB] inherit
  ACTIVE            '/dev/LVG/opt' [4.00 GiB] inherit
  ACTIVE            '/dev/LVG/bak' [5.00 GiB] inherit

```

```

root@srv-ubuntu:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
udev                  225M     0  225M   0% /dev
tmpfs                  49M  2.7M   47M   6% /run
/dev/mapper/LVG-root  2.0G  654M  1.2G  36% /
/dev/mapper/LVG-usr   3.0G  691M  2.1G  25% /usr
tmpfs                 245M     0  245M   0% /dev/shm
tmpfs                 5.0M     0  5.0M   0% /run/lock
tmpfs                 245M     0  245M   0% /sys/fs/cgroup
/dev/sda1             461M  105M  334M  24% /boot
/dev/mapper/LVG-home  179M  1.6M  164M   1% /home
/dev/mapper/LVG-tmp   453M  2.3M  423M   1% /tmp
/dev/mapper/LVG-var   2.0G  293M  1.6G  16% /var
/dev/mapper/LVG-opt   3.0G  3.2M  2.8G   1% /opt
/dev/mapper/LVG-bak   3.9G  3.1M  3.7G   1% /bak
/dev/mapper/LVG-srv   179M  1.6M  164M   1% /srv
tmpfs                  49M     0   49M   0% /run/user/1000
```

```
root@srv-ubuntu:/# free
              total        used        free      shared  buff/cache   available
Mem:         500120       42672      314648        2776      142800      423764
Swap:       1949692           0     1949692
```

```
root@srv-ubuntu:/# uname -a
Linux srv-ubuntu 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

```
root@srv-ubuntu:/# ls -l /boot/vm*
-rw------- 1 root root 7047504 Jul 12  2016 /boot/vmlinuz-4.4.0-31-generic
-rw------- 1 root root 7070992 Jan 18 09:59 /boot/vmlinuz-4.4.0-62-generic
```

LHammonds

---

### Post by gouriga on 2017-02-05
Hi,

I had a same problem, but it seems that the problem isn't with the LVM2 but with the Untenanted Upgrades Services' script. It seems there is a bug in it which was described here:
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1661611](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1661611)

Workaround based on this information:
Please edit the line 120 of /usr/share/unattended-upgrades/unattended-upgrade-shutdown.
- if apt_pkg.config.find_b("Unattended-Upgrade::InstallOnShutdown", False):
+ if apt_pkg.config.find_b("Unattended-Upgrade::InstallOnShutdown", false):

Gouriga

---

### Post by baberb on 2017-02-06
Yeah I had this happen to me, too.  I'm also on vmware, but I use separate vmdks instead of partitions or LVM...Staring at that last line while waiting for a reboot, I'm like I don't even use LVM

Changing F to f on line 120 fixes the issue, which would happen whether virtual or bare-metal

More info here: [http://askubuntu.com/questions/878630/apt-unattended-upgrades-stalls-shutdown](http://askubuntu.com/questions/878630/apt-unattended-upgrades-stalls-shutdown)

---

### Post by LHammonds on 2017-02-07
Thanks for finding the tempfix for this.  I thought it was a bug but had no idea where or what was causing it.

I made the change of "False" to "false" and it does allow the reboot to happen immediately rather than wait for a 10 minute timeout.  But now I see this error message upon reboot during shutdown...not sure if it is an issue though:

```
[FAILED] Failed to start Unattended Upgrades Shutdown. See 'systemctl status unattended-upgrades.service' for details.
```

I noticed a flash of red during the reboot and used my iPhone to take a video of it to capture the output.

When I run the status command like it suggests, this is the output:

```

â unattended-upgrades.service - Unattended Upgrades Shutdown
   Loaded: loaded (/lib/systemd/system/unattended-upgrades.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:unattended-upgrade(8)
```

---

### Post by kainino on 2017-05-04
For anyone who ends up here via Google as I did:

The fix above (False -> false) is **NOT a fix or real workaround**. It simply changes the script from valid Python to invalid Python, causing it not to execute. A better workaround is to *uninstall* unattended-upgrades for the time being. Or, see below.

The Ubuntu team has just fixed this, see this bug:
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1654600](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1654600)
It seems it will be fixed as soon as the unattended-upgrades package reaches 0.90ubuntu0.5 (currently it is 0.90ubuntu0.3 in xenial-updates).

Please see here to help the team test out the fixed version, if you're willing:
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1654600/comments/42](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1654600/comments/42)

EDIT: btw, new version works for me!

---

### Post by LHammonds on 2017-05-05
Well, it was already said it is not a "true" fix but the dozen servers I have are no longer stalling out upon bootup and the timely reveal of this tempfix was much appreciated.  When 0.5 is pushed down the pipe, I'll go back and undo the changes I made since the tempfix will likely cause the same problem to occur again once the source is fixed.

LHammonds

---

