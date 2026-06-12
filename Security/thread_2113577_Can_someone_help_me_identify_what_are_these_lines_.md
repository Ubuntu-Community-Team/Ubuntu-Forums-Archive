---
title: "Can someone help me identify what are these lines in boot.log"
date: 2013-02-07
forum: Security
---

### Post by lobo_tuerto on 2013-02-07
Hi guys, I just noticed that when my Ubuntu 12.10 is booting up, there are some lines that don't have any info on it (They just say * Starting ... [OK]).

This didn't happen in 12.04 that I can recall...

Here is my boot.log, any ideas about what's going on?


```

fsck de util-linux 2.20.1
fsck de util-linux 2.20.1
/dev/mapper/ubuntu-root: clean, 598763/14573568 files, 32992393/58269696 blocks
/dev/sda1: clean, 278/124496 files, 118119/248832 blocks
 * Starting bluetooth daemon                                             [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting Mount network filesystems                                    [ OK ]
 * Starting Failsafe Boot Delay                                          [ OK ]
 * Stopping Mount network filesystems                                    [ OK ]
 * Starting configure network device                                     [ OK ]
 * Stopping Failsafe Boot Delay                                          [ OK ]
 * Starting System V initialisation compatibility                        [ OK ]
 * Starting configure network device security                            [ OK ]
 * Stopping modem connection manager                                     [ OK ]
 * Starting Bridge socket events into upstart                            [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting network connection manager                                   [ OK ]
 * Starting Uncomplicated firewall                                       [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting AppArmor profiles                                            [ OK ] 
 * Stopping System V initialisation compatibility                        [ OK ]
 * Starting System V runlevel compatibility                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting restore sound card(s') mixer state(s)                        [ OK ]
 * Starting                                                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting save kernel messages                                         [ OK ]
 * Starting                                                              [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting anac(h)ronistic cron                                         [ OK ]
 * Starting ACPI daemon                                                  [ OK ]
 * Starting regular background program processing daemon                 [ OK ]
 * Starting crash report submission daemon                               [ OK ]
 * Starting deferred execution scheduler                                 [ OK ]
 * Stopping anac(h)ronistic cron                                         [ OK ]
 * Starting automatic crash report generation                            [ OK ]
 * Starting CPU interrupts balancing daemon                              [ OK ]
 * Stopping Read required files in advance                               [ OK ]
 * Stopping restore sound card(s') mixer state(s)                        [ OK ]
 * Starting configure virtual network devices                            [ OK ]
 * Stopping save kernel messages                                         [ OK ]
 * Starting CUPS printing spooler/server                                 [ OK ]
 * Stopping cold plug devices                                            [ OK ]
 * Starting load fallback graphics devices                               [ OK ]
 * Stopping log initial device creation                                  [ OK ]
 * Starting save udev log and update rules                               [ OK ]
 * Stopping save udev log and update rules                               [ OK ]
 * Starting load fallback graphics devices                               [fail]
 * Starting                                                              [ OK ]
 * Starting set console font                                             [ OK ]
 * Starting                                                              [ OK ]
 * Stopping                                                              [ OK ]
 * Starting LightDM Display Manager                                      [ OK ]
 * Stopping set console font                                             [ OK ]
 * Starting Userspace bootsplash                                         [ OK ]
 * Starting                                                              [ OK ]
 * Stopping                                                              [ OK ]

```

---

### Post by CharlesA on 2013-02-07
You should be fine.

Mine looks similar:

```
fsck from util-linux 2.20.1
/dev/sda1: clean, 275891/29491200 files, 8222609/117939712 blocks
 * Starting configure network device security                                                                            [ OK ]
 * Starting configure network device security                                                                            [ OK ]
 * Stopping Userspace bootsplash                                                                                         [ OK ]
 * Starting Mount network filesystems                                                                                    [ OK ]
 * Starting Failsafe Boot Delay                                                                                          [ OK ]
 * Stopping Mount network filesystems                                                                                    [ OK ]
 * Starting Bridge socket events into upstart                                                                            [ OK ]
 * Starting SMB/CIFS File Server                                                                                         [ OK ]
 * Stopping Read required files in advance (for other mountpoints)                                                       [ OK ]
 * Stopping Mount filesystems on boot                                                                                    [ OK ]
 * Stopping cold plug devices                                                                                            [ OK ]
 * Stopping log initial device creation                                                                                  [ OK ]
 * Starting configure network device security                                                                            [ OK ]
 * Starting save udev log and update rules                                                                               [ OK ]
 * Starting configure virtual network devices                                                                            [ OK ]
 * Stopping save udev log and update rules                                                                               [ OK ]
 * Stopping configure virtual network devices                                                                            [ OK ]
 * Starting configure network device                                                                                     [ OK ]
 * Stopping OpenSSH server                                                                                               [ OK ]
 * Starting OpenSSH server                                                                                               [ OK ]
 * Starting NetBIOS name server                                                                                          [ OK ]
 * Starting Mount network filesystems                                                                                    [ OK ]
 * Stopping Mount network filesystems                                                                                    [ OK ]
 * Stopping Failsafe Boot Delay                                                                                          [ OK ]
 * Starting System V initialisation compatibility                                                                        [ OK ]
 * Starting set sysctls from /etc/sysctl.conf                                                                            [ OK ]
 * Starting configure network device                                                                                     [ OK ]
 * Stopping set sysctls from /etc/sysctl.conf                                                                            [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                                                                            [ OK ]
 * Setting sensors limits                                                                                                [ OK ]
 * Stopping System V initialisation compatibility                                                                        [ OK ]
 * Starting System V runlevel compatibility                                                                              [ OK ]
 * Starting save kernel messages                                                                                         [ OK ]
 * Starting ACPI daemon                                                                                                  [ OK ]
 * Starting regular background program processing daemon                                                                 [ OK ]
 * Starting deferred execution scheduler                                                                                 [ OK ]
 * Starting automatic crash report generation                                                                            [ OK ]
 * Starting CPU interrupts balancing daemon                                                                              [ OK ]
 * Stopping save kernel messages                                                                                         [ OK ]
 * Starting disk temperature monitoring daemon hddtemp:                                                                  [ OK ]
 * Starting crash report submission daemon                                                                               [ OK ]
Starting hptsvr daemon.
 * Starting Postfix Mail Transport Agent postfix                                                                         [ OK ]
 * Starting VirtualBox kernel modules                                                                                    [ OK ]
 *  done.
 * Starting vnStat daemon vnstatd                                                                                        [ OK ]
 * Starting NTP server ntpd                                                                                              [ OK ]
Starting UPS power management: apcupsd.
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.2 for ServerName
 * Starting web server apache2                                                                                           [ OK ]
Starting CrashPlan Engine ... Using standard startup
OK
Starting uptime daemon:  * Starting configure network device security                                                    [ OK ]
 * Starting configure network device                                                                                     [ OK ]
uptimed.
Waiting for VM "Sol" to power on...
VM "Sol" started successfully!
Waiting for VM "Precise" to power on...
VM "Precise" started successfully!
Waiting for VM "Server2K8" to power on...
VM "Server2K8" started successfully!
No Saved VMs to Start!
 * Stopping System V runlevel compatibility                                                                              [ OK ]

```

---

### Post by lobo_tuerto on 2013-02-07
But it's not the same, in yours everyline have a name for what it is starting. In mine there are several that don't have a name for _what_ they are starting.

Is it really ok?

---

### Post by lobo_tuerto on 2013-02-08
Check, for example, the last two lines of the log I posted.

---

### Post by lobo_tuerto on 2013-02-11
Could anyone post here her Ubuntu 12.10 /var/log/boot.log, please? If it's a new install, the better.

Mine is from a fresh install.

---

### Post by Stonecold1995 on 2013-02-13
It's the exact same for me, although it doesn't seem to be causing any problems.
```
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... Scanning for Btrfs filesystems
done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/mapper/sdb5_crypt: clean, 474697/1941504 files, 4861228/7753216 blocks
/dev/sdb1: clean, 278/124496 files, 118391/248832 blocks
mount: according to mtab, tmpfs is already mounted on /dev/shm

mountall: mount /dev/shm [593] terminated with status 1
fsck from util-linux 2.20.1
/dev/mapper/sda1_crypt: clean, 116597/45793280 files, 159464938/183142656 blocks
Sandbox disabled, edit /etc/default/sandbox to enable it

 * Loading IPsec SA/SP database:                                                                                                                                                                                                         [ OK ] 
 * Starting bluetooth daemon                                                                                                                                                                                                             [ OK ]
 * Starting mDNS/DNS-SD daemon                                                                                                                                                                                                           [ OK ]
 * Starting AppArmor profiles                                                                                                                                                                                                            [ OK ] 
 * Starting network connection manager                                                                                                                                                                                                   [ OK ]
 * Setting sensors limits                                                                                                                                                                                                                [ OK ]                                
Sandbox disabled, edit /etc/default/sandbox to enable it                                                                                                                                                                                                                       
 * Loading cpufreq kernel modules...                                                                                                                                                                                                     [ OK ]                                
 * Stopping System V initialisation compatibility                                                                                                                                                                                        [ OK ]                                
 * Starting System V runlevel compatibility                                                                                                                                                                                              [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting Bumblebee supporting nVidia Optimus cards                                                                                                                                                                                    [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting K Display Manager                                                                                                                                                                                                            [ OK ]                                
 * Starting save kernel messages                                                                                                                                                                                                         [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting anac(h)ronistic cron                                                                                                                                                                                                         [ OK ]                                
 * Starting ACPI daemon                                                                                                                                                                                                                  [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting                                                                                                                                                                                                                              [ OK ]                                
 * Starting regular background program processing daemon                                                                                                                                                                                 [ OK ]                                
 * Starting deferred execution scheduler                                                                                                                                                                                                 [ OK ]                                
 * Starting automatic crash report generation                                                                                                                                                                                            [ OK ]                                
 * Starting CPU interrupts balancing daemon                                                                                                                                                                                              [ OK ]                                
 * Stopping                                                                                                                                                                                                                              [ OK ]                                
 * Starting LightDM Display Manager                                                                                                                                                                                                      [ OK ]                                
 * Stopping save kernel messages                                                                                                                                                                                                         [ OK ]                                
 * Stopping LightDM Display Manager                                                                                                                                                                                                      [ OK ]                                
 * Starting Initializes zram swaping
```

---

