---
title: "Security Question RE: Unhide"
date: 2014-05-17
forum: Security
---

### Post by cmac2 on 2014-05-17
Hello, I am farily new to linux and ubuntu.  I have been trying to follow the guides on how to set up your os and taking the appropriate security measures.  A few days ago I was running through commands.  Tonight I was reading about the unhide command and tried it out.  I had a large number of hidden PID's.  

Is this usual?  I am currently running a live DVD of UbuntuGnome.  
Here are the results.  Thanks for the help.  

 ```
 	 	 	 	   ubuntu-gnome@ubuntu-gnome:~$ unhide-posix proc  
 Unhide-legacy 20121229  
 Copyright © 2012 Yago Jesus & Patrick Gouin  
 License GPLv3+ : GNU GPL version 3 or later  
 [http://www.unhide-forensics.info](http://www.unhide-forensics.info) 
 

 NOTE : This is legacy version of unhide, it is intended  
        for systems using Linux < 2.6 or other UNIX systems  
 

 
[*]Searching for Hidden processes through /proc scanning  
 

 Found HIDDEN PID: 1053  
 Command: rsyslogd  
 

 Found HIDDEN PID: 1054  
 Command: rsyslogd  
 

 Found HIDDEN PID: 1055  
 Command: rsyslogd  
 

 Found HIDDEN PID: 1567  
 Command: /usr/sbin/ModemManager  
 

 Found HIDDEN PID: 1794  
 Command: gdm  
 

 Found HIDDEN PID: 1795  
 Command: /usr/sbin/ModemManager  
 

 Found HIDDEN PID: 1804  
 Command: NetworkManager  
 

 Found HIDDEN PID: 1805  
 Command: gdm  
 

 Found HIDDEN PID: 1915  
 Command: NetworkManager  
 

 Found HIDDEN PID: 1916  
 Command: NetworkManager  
 

 Found HIDDEN PID: 1919  
 Command: /usr/lib/gdm/gdm-simple-slave  
 

 Found HIDDEN PID: 1920  
 Command: /usr/lib/gdm/gdm-simple-slave  
 

 Found HIDDEN PID: 1994  
 Command: /usr/lib/policykit-1/polkitd  
 

 Found HIDDEN PID: 1995  
 Command: /usr/lib/policykit-1/polkitd  
   
 Found HIDDEN PID: 1998  
 Command: /usr/lib/accountsservice/accounts-daemon  
 

 Found HIDDEN PID: 1999  
 Command: /usr/lib/accountsservice/accounts-daemon  
 

 Found HIDDEN PID: 2000  
 Command: /usr/bin/X  
 

 Found HIDDEN PID: 2016  
 Command: gdm-session-worker [pam/gdm-autologin]  
 

 Found HIDDEN PID: 2018  
 Command: gdm-session-worker [pam/gdm-autologin]  
 

 Found HIDDEN PID: 2264  
 Command: /usr/lib/at-spi2-core/at-spi-bus-launcher  
 

 Found HIDDEN PID: 2266  
 Command: /usr/lib/at-spi2-core/at-spi-bus-launcher  
 

 Found HIDDEN PID: 2268  
 Command: /usr/lib/at-spi2-core/at-spi-bus-launcher  
 

 Found HIDDEN PID: 2271  
 Command: /usr/bin/ibus-daemon  
 

 Found HIDDEN PID: 2274  
 Command: /usr/lib/gvfs/gvfsd  
 

 Found HIDDEN PID: 2276  
 Command: /usr/bin/ibus-daemon  
 

 Found HIDDEN PID: 2280  
 Command: /usr/lib/ibus/ibus-dconf  
 

 Found HIDDEN PID: 2281  
 Command: /usr/lib/ibus/ibus-dconf  
 

 Found HIDDEN PID: 2288  
 Command: /usr/lib/ibus/ibus-dconf  
 

 Found HIDDEN PID: 2291  
 Command: /usr/lib/gvfs/gvfsd-fuse  
 

 Found HIDDEN PID: 2292  
 Command: /usr/lib/gvfs/gvfsd-fuse  
 

 Found HIDDEN PID: 2293  
 Command: /usr/lib/gvfs/gvfsd-fuse  
 

 Found HIDDEN PID: 2294  
 Command: /usr/lib/gvfs/gvfsd-fuse  
 

 Found HIDDEN PID: 2297  
 Command: /usr/lib/ibus/ibus-x11  
 

 Found HIDDEN PID: 2298  
 Command: /usr/lib/ibus/ibus-x11  
 

 Found HIDDEN PID: 2299  
 Command: /usr/lib/at-spi2-core/at-spi2-registryd  
 

 Found HIDDEN PID: 2302  
 Command: /usr/lib/gnome-settings-daemon/gnome-settings-daemon  
 

 Found HIDDEN PID: 2303  
 Command: /usr/lib/ibus/ibus-ui-gtk3  
 

 Found HIDDEN PID: 2304  
 Command: /usr/lib/ibus/ibus-ui-gtk3  
 

 Found HIDDEN PID: 2305  
 Command: /usr/lib/gnome-settings-daemon/gnome-settings-daemon  
 

 Found HIDDEN PID: 2306  
 Command: /usr/lib/ibus/ibus-ui-gtk3  
 

 Found HIDDEN PID: 2308  
 Command: gnome-session  
 

 Found HIDDEN PID: 2309  
 Command: gnome-session  
 

 Found HIDDEN PID: 2310  
 Command: gnome-session  
 

 Found HIDDEN PID: 2318  
 Command: /usr/lib/upower/upowerd  
 

 Found HIDDEN PID: 2319  
 Command: /usr/lib/upower/upowerd  
 

 Found HIDDEN PID: 2345  
 Command: /usr/lib/gnome-settings-daemon/gnome-settings-daemon  
 

 Found HIDDEN PID: 2349  
 Command: /usr/bin/gnome-keyring-daemon  
 

 Found HIDDEN PID: 2350  
 Command: /usr/bin/gnome-keyring-daemon  
 

 Found HIDDEN PID: 2351  
 Command: /usr/bin/gnome-keyring-daemon  
 

 Found HIDDEN PID: 2352  
 Command: /usr/bin/gnome-keyring-daemon  
 

 Found HIDDEN PID: 2360  
 Command: /usr/lib/rtkit/rtkit-daemon  
 

 Found HIDDEN PID: 2361  
 Command: /usr/lib/rtkit/rtkit-daemon  
 

 Found HIDDEN PID: 2362  
 Command: /usr/bin/pulseaudio  
 

 Found HIDDEN PID: 2363  
 Command: /usr/bin/pulseaudio  
 

 Found HIDDEN PID: 2364  
 Command: /usr/bin/pulseaudio  
 

 Found HIDDEN PID: 2370  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2371  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2372  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2373  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2374  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2375  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2386  
 Command: /usr/lib/dconf/dconf-service  
 

 Found HIDDEN PID: 2387  
 Command: /usr/lib/dconf/dconf-service  
 

 Found HIDDEN PID: 2390  
 Command: /usr/lib/gnome-settings-daemon/gsd-printer  
 

 Found HIDDEN PID: 2394  
 Command: /usr/lib/colord/colord  
 

 Found HIDDEN PID: 2399  
 Command: /usr/lib/colord/colord  
   
 Found HIDDEN PID: 2403  
 Command: /usr/lib/ibus/ibus-engine-simple  
 

 Found HIDDEN PID: 2404  
 Command: /usr/lib/ibus/ibus-engine-simple  
 

 Found HIDDEN PID: 2501  
 Command: /usr/bin/gnome-shell  
 

 Found HIDDEN PID: 2541  
 Command: /usr/lib/gnome-shell/gnome-shell-calendar-server  
 

 Found HIDDEN PID: 2542  
 Command: /usr/lib/gnome-shell/gnome-shell-calendar-server  
 

 Found HIDDEN PID: 2543  
 Command: /usr/lib/gnome-shell/gnome-shell-calendar-server  
 

 Found HIDDEN PID: 2550  
 Command: /usr/lib/evolution/evolution-source-registry  
 

 Found HIDDEN PID: 2552  
 Command: /usr/lib/telepathy/mission-control-5  
 

 Found HIDDEN PID: 2553  
 Command: /usr/lib/gvfs/gvfs-udisks2-volume-monitor  
 

 Found HIDDEN PID: 2554  
 Command: /usr/lib/telepathy/mission-control-5  
 

 Found HIDDEN PID: 2560  
 Command: /usr/lib/udisks2/udisksd  
 

 Found HIDDEN PID: 2562  
 Command: /usr/lib/udisks2/udisksd  
 

 Found HIDDEN PID: 2563  
 Command: /usr/lib/udisks2/udisksd  
 

 Found HIDDEN PID: 2564  
 Command: /usr/lib/evolution/evolution-source-registry  
 

 Found HIDDEN PID: 2565  
 Command: /usr/lib/udisks2/udisksd  
 

 Found HIDDEN PID: 2566  
 Command: /usr/lib/gvfs/gvfs-udisks2-volume-monitor  
 

 Found HIDDEN PID: 2571  
 Command: /usr/lib/gvfs/gvfs-mtp-volume-monitor  
 

 Found HIDDEN PID: 2575  
 Command: /usr/lib/gvfs/gvfs-gphoto2-volume-monitor  
 

 Found HIDDEN PID: 2578  
 Command: /usr/lib/gvfs/gvfs-goa-volume-monitor  
 

 Found HIDDEN PID: 2586  
 Command: /usr/lib/gnome-online-accounts/goa-daemon  
 

 Found HIDDEN PID: 2587  
 Command: /usr/lib/gnome-online-accounts/goa-daemon  
 

 Found HIDDEN PID: 2588  
 Command: /usr/lib/gnome-online-accounts/goa-daemon  
 

 Found HIDDEN PID: 2593  
 Command: /usr/lib/gvfs/gvfs-afc-volume-monitor  
 

 Found HIDDEN PID: 2595  
 Command: /usr/lib/gvfs/gvfs-afc-volume-monitor  
 

 Found HIDDEN PID: 2617  
 Command: /usr/bin/gnome-keyring-daemon  
 

 Found HIDDEN PID: 2618  
 Command: nm-applet  
 

 Found HIDDEN PID: 2619  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2620  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2621  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2622  
 Command: nm-applet  
 

 Found HIDDEN PID: 2625  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2626  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2627  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2628  
 Command: /usr/lib/tracker/tracker-store  
 

 Found HIDDEN PID: 2629  
 Command: /usr/lib/tracker/tracker-miner-fs  
 

 Found HIDDEN PID: 2630  
 Command: /usr/lib/tracker/tracker-miner-fs  
 

 Found HIDDEN PID: 2631  
 Command: /usr/lib/tracker/tracker-miner-fs  
 

 Found HIDDEN PID: 2634  
 Command: /usr/lib/gnome-shell/gnome-shell-calendar-server  
 

 Found HIDDEN PID: 2642  
 Command: /usr/lib/evolution/evolution-calendar-factory  
 

 Found HIDDEN PID: 2657  
 Command: /usr/lib/evolution/evolution-calendar-factory  
 

 Found HIDDEN PID: 2658  
 Command: /usr/lib/evolution/evolution-calendar-factory  
 

 Found HIDDEN PID: 2659  
 Command: /usr/lib/evolution/evolution-calendar-factory  
 

 Found HIDDEN PID: 2665  
 Command: /usr/lib/gvfs/gvfsd-metadata  
 

 Found HIDDEN PID: 2706  
 Command: zeitgeist-datahub  
 

 Found HIDDEN PID: 2707  
 Command: zeitgeist-datahub  
 

 Found HIDDEN PID: 2710  
 Command: /usr/bin/zeitgeist-daemon  
 

 Found HIDDEN PID: 2718  
 Command: zeitgeist-datahub  
 

 Found HIDDEN PID: 2719  
 Command: zeitgeist-datahub  
 

 Found HIDDEN PID: 2720  
 Command: zeitgeist-datahub  
 

 Found HIDDEN PID: 2725  
 Command: zeitgeist-datahub  
 

 Found HIDDEN PID: 2750  
 Command: /usr/lib/gvfs/gvfsd-burn  
 

 Found HIDDEN PID: 2762  
 Command: /usr/lib/x86_64-linux-gnu/zeitgeist-fts  
   
 Found HIDDEN PID: 2766  
 Command: /usr/lib/x86_64-linux-gnu/zeitgeist-fts  
 

 Found HIDDEN PID: 2875  
 Command: /usr/lib/evolution/3.10/evolution-alarm-notify  
 

 Found HIDDEN PID: 2876  
 Command: /usr/lib/evolution/3.10/evolution-alarm-notify  
 

 Found HIDDEN PID: 2877  
 Command: /usr/lib/evolution/3.10/evolution-alarm-notify  
 

 Found HIDDEN PID: 2878  
 Command: /usr/lib/evolution/3.10/evolution-alarm-notify  
 

 Found HIDDEN PID: 2893  
 Command: update-notifier  
 

 Found HIDDEN PID: 2894  
 Command: update-notifier  
 

 Found HIDDEN PID: 2895  
 Command: update-notifier  
 

 Found HIDDEN PID: 3001  
 Command: gnome-terminal  
 

 Found HIDDEN PID: 3004  
 Command: gnome-terminal  
 

 Found HIDDEN PID: 3008  
 Command: gnome-terminal  
 

 Found HIDDEN PID: 3027  
 Command: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor  
 

 Found HIDDEN PID: 3029  
 Command: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor  
 

 Found HIDDEN PID: 3030  
 Command: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor  
 

 Found HIDDEN PID: 3405  
 Command: python  
 

 Found HIDDEN PID: 3406  
 Command: python  
 

 Found HIDDEN PID: 3422  
 Command: python  
 

 Found HIDDEN PID: 3423  
 Command: python  
 

 Found HIDDEN PID: 3424  
 Command: python  
 

 Found HIDDEN PID: 3425  
 Command: python  
 

 Found HIDDEN PID: 3426  
 Command: python  
 

 Found HIDDEN PID: 3433  
 Command: python
```

---

### Post by Lars Noodén on 2014-05-17
They're not really hidden, it looks like mostly false positives because they're just processes run by other users.  You can also see them with [ps](http://manpages.ubuntu.com/manpages/trusty/en/man1/ps.1posix.html) or [top](http://manpages.ubuntu.com/manpages/trusty/en/man1/top.1.html)

```

sudo ps -ef | less

```

Some processes need the highest privilege to run, others are given just enough privileges to do their job (least privilege) by using a dedicated account (privilege separation).  

To get an idea what a process is for, you can look it up in [man](http://manpages.ubuntu.com/manpages/trusty/en/man1/man.1posix.html) if it is a regular part of the system.

```

man rsyslogd

```

---

### Post by cmac2 on 2014-05-17
Thank you for the help.  I was mainly concerned with open ports.  While researching open ports and programs to scan them I came accross unhide.  These were the results.  Lots of new information to learn.

---

### Post by cmac2 on 2014-05-17
> **Lars Noodén said:**
> They're not really hidden, it looks like mostly false positives because they're just processes run by other users.  You can also see them with [ps]("http://manpages.ubuntu.com/manpages/trusty/en/man1/ps.1posix.html") or [top]("http://manpages.ubuntu.com/manpages/trusty/en/man1/top.1.html")

```

sudo ps -ef | less

```


I didnt catch this earlier.  I am the only user and it was a live DVD that I was going to do a fresh install with.  Earlier I found some open ports on my router.  There were two ports open and using the Upnp feature to torrent stuff. I was able to shut that down.  But wanted to make sure I didnt have any more issues. 

Thanks for your time.

---

### Post by cmac2 on 2014-05-17
Ive been googling a lot of the different programs.  Couldnt really figure out the freedesktop.org and how it factors in  

This is the output from the command you gave me.

Are all of these normal?  



```
UID        PID  PPID  C STIME TTY          TIME CMD 
root         1     0  0 21:16 ?        00:00:01 /sbin/init 
root         2     0  0 21:16 ?        00:00:00 [kthreadd] 
root         3     2  0 21:16 ?        00:00:00 [ksoftirqd/0] 
root         5     2  0 21:16 ?        00:00:00 [kworker/0:0H] 
root         7     2  0 21:16 ?        00:00:01 [rcu_sched] 
root         8     2  0 21:16 ?        00:00:00 [rcuos/0] 
root         9     2  0 21:16 ?        00:00:00 [rcuos/1] 
root        10     2  0 21:16 ?        00:00:00 [rcuos/2] 
root        11     2  0 21:16 ?        00:00:00 [rcuos/3] 
root        12     2  0 21:16 ?        00:00:00 [rcu_bh] 
root        13     2  0 21:16 ?        00:00:00 [rcuob/0] 
root        14     2  0 21:16 ?        00:00:00 [rcuob/1] 
root        15     2  0 21:16 ?        00:00:00 [rcuob/2] 
root        16     2  0 21:16 ?        00:00:00 [rcuob/3] 
root        17     2  0 21:16 ?        00:00:03 [migration/0] 
root        18     2  0 21:16 ?        00:00:00 [watchdog/0] 
root        19     2  0 21:16 ?        00:00:00 [watchdog/1] 
root        20     2  0 21:16 ?        00:00:03 [migration/1] 
root        21     2  0 21:16 ?        00:00:00 [ksoftirqd/1] 
root        23     2  0 21:16 ?        00:00:00 [kworker/1:0H] 
root        24     2  0 21:16 ?        00:00:00 [watchdog/2] 
root        25     2  0 21:16 ?        00:00:00 [migration/2] 
: 
root        26     2  0 21:16 ?        00:00:00 [ksoftirqd/2] 
root        27     2  0 21:16 ?        00:00:00 [kworker/2:0] 
root        28     2  0 21:16 ?        00:00:00 [kworker/2:0H] 
root        29     2  0 21:16 ?        00:00:00 [watchdog/3] 
root        30     2  0 21:16 ?        00:00:00 [migration/3] 
root        31     2  0 21:16 ?        00:00:00 [ksoftirqd/3] 
root        32     2  0 21:16 ?        00:00:00 [kworker/3:0] 
root        33     2  0 21:16 ?        00:00:00 [kworker/3:0H] 
root        34     2  0 21:16 ?        00:00:00 [khelper] 
root        35     2  0 21:16 ?        00:00:00 [kdevtmpfs] 
root        36     2  0 21:16 ?        00:00:00 [netns] 
root        37     2  0 21:16 ?        00:00:00 [writeback] 
root        38     2  0 21:16 ?        00:00:00 [kintegrityd] 
root        39     2  0 21:16 ?        00:00:00 [bioset] 
root        40     2  0 21:16 ?        00:00:00 [kworker/u9:0] 
root        41     2  0 21:16 ?        00:00:00 [kblockd] 
root        42     2  0 21:16 ?        00:00:00 [ata_sff] 
root        43     2  0 21:16 ?        00:00:00 [khubd] 
root        44     2  0 21:16 ?        00:00:00 [md] 
root        45     2  0 21:16 ?        00:00:00 [devfreq_wq] 
root        46     2  0 21:16 ?        00:00:00 [kworker/0:1] 
root        47     2  0 21:16 ?        00:00:00 [kworker/1:1] 
root        48     2  0 21:16 ?        00:00:00 [kworker/3:1] 
: root        49     2  0 21:16 ?        00:00:05 [kworker/2:1] 
root        51     2  0 21:16 ?        00:00:00 [khungtaskd] 
root        52     2  0 21:16 ?        00:00:00 [kswapd0] 
root        53     2  0 21:16 ?        00:00:00 [ksmd] 
root        54     2  0 21:16 ?        00:00:00 [khugepaged] 
root        55     2  0 21:16 ?        00:00:00 [fsnotify_mark] 
root        56     2  0 21:16 ?        00:00:00 [ecryptfs-kthrea] 
root        57     2  0 21:16 ?        00:00:00 [crypto] 
root        69     2  0 21:16 ?        00:00:00 [kthrotld] 
root        71     2  0 21:16 ?        00:00:00 [kworker/1:2] 
root        90     2  0 21:16 ?        00:00:00 [deferwq] 
root        91     2  0 21:16 ?        00:00:00 [charger_manager] 
root       155     2  0 21:16 ?        00:00:00 [kworker/u8:2] 
root       163     2  0 21:16 ?        00:00:00 [scsi_eh_0] 
root       164     2  0 21:16 ?        00:00:00 [scsi_eh_1] 
root       165     2  0 21:16 ?        00:00:00 [kworker/u8:3] 
root       166     2  0 21:16 ?        00:00:00 [ttm_swap] 
root       261     2  0 21:17 ?        00:00:01 [loop0] 
root       634     2  0 21:17 ?        00:00:00 [kauditd] 
root       948     1  0 21:18 ?        00:00:00 upstart-udev-bridge --daemon 
root       971     1  0 21:18 ?        00:00:01 /lib/systemd/systemd-udevd --daemon 
root       996     1  0 21:18 ?        00:00:00 upstart-file-bridge --daemon 
: 
message+  1000     1  0 21:18 ?        00:00:00 dbus-daemon --system --fork 
root      1018     1  0 21:18 ?        00:00:00 /usr/sbin/bluetoothd 
root      1025     1  0 21:18 ?        00:00:00 /lib/systemd/systemd-logind 
syslog    1056     1  0 21:18 ?        00:00:00 rsyslogd 
avahi     1065     1  0 21:18 ?        00:00:00 avahi-daemon: running [ubuntu-gnome.local] 
avahi     1067  1065  0 21:18 ?        00:00:00 avahi-daemon: chroot helper 
root      1097     2  0 21:18 ?        00:00:00 [krfcommd] 
root      1115     2  0 21:18 ?        00:00:00 [kmemstick] 
root      1131     2  0 21:18 ?        00:00:00 [edac-poller] 
root      1136     2  0 21:18 ?        00:00:00 [kmpathd] 
root      1138     2  0 21:18 ?        00:00:00 [kmpath_handlerd] 
root      1170     2  0 21:18 ?        00:00:00 [kpsmoused] 
root      1198     2  0 21:18 ?        00:00:00 [kworker/0:2] 
root      1208     1  0 21:18 ?        00:00:00 upstart-socket-bridge --daemon 
root      1275     1  0 21:18 ?        00:00:00 /usr/sbin/ModemManager 
root      1346     2  0 21:18 ?        00:00:00 [hd-audio0] 
root      1354     2  0 21:18 ?        00:00:00 [hd-audio1] 
root      1415     1  0 21:18 tty4     00:00:00 /bin/login -f              
root      1419     1  0 21:18 tty5     00:00:00 /bin/login -f              
root      1428     1  0 21:18 tty2     00:00:00 /bin/login -f              
root      1429     1  0 21:18 tty3     00:00:00 /bin/login -f              
root      1432     1  0 21:18 tty6     00:00:00 /bin/login -f              
: 
root      1429     1  0 21:18 tty3     00:00:00 /bin/login -f              
root      1432     1  0 21:18 tty6     00:00:00 /bin/login -f              
root      1463     1  0 21:18 ?        00:00:00 cron 
root      1468     1  0 21:18 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket 
root      1472     1  0 21:18 ?        00:00:00 gdm 
root      1491     1  0 21:18 ?        00:00:00 /usr/sbin/cups-browsed 
root      1530     1  0 21:18 ?        00:00:00 /usr/sbin/cupsd -f 
kernoops  1681     1  0 21:19 ?        00:00:00 /usr/sbin/kerneloops 
root      1760     1  0 21:19 tty1     00:00:00 /bin/login -f              
root      1801  1472  0 21:19 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Displays/_0 
root      1804     1  0 21:19 ?        00:00:00 NetworkManager 
ubuntu-+  1843  1432  0 21:19 tty6     00:00:00 -bash 
ubuntu-+  1903  1415  0 21:19 tty4     00:00:00 -bash 
ubuntu-+  1904  1429  0 21:19 tty3     00:00:00 -bash 
ubuntu-+  1905  1760  0 21:19 tty1     00:00:00 -bash 
ubuntu-+  1910  1428  0 21:19 tty2     00:00:00 -bash 
ubuntu-+  1911  1419  0 21:19 tty5     00:00:00 -bash 
root      1924     1  0 21:19 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug 
root      1930  1801  4 21:19 tty7     00:00:24 /usr/bin/X :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-WGJMkm/database -seat seat0 -nolisten tc: 

o-debug 
root      1930  1801  4 21:19 tty7     00:00:24 /usr/bin/X :0 -background none - 
verbose -auth /var/run/gdm/auth-for-gdm-WGJMkm/database -seat seat0 -nolisten tc 
p vt7 
root      1947     1  0 21:19 ?        00:00:00 /usr/lib/accountsservice/account 
s-daemon 
root      2012  1804  0 21:19 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/N 
etworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhc 
lient-eth0.pid -lf /var/lib/NetworkManager/dhclient-350c77d6-5df1-4479-baeb-bf5c 
d218a0f8-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0 
nobody    2015  1804  0 21:19 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d 
root      2153  1801  0 21:19 ?        00:00:00 gdm-session-worker [pam/gdm-autologin] 
ubuntu-+  2267  2153  0 21:19 ?        00:00:00 init --user 
ubuntu-+  2351  2267  0 21:19 ?        00:00:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-BAE3s9Ugju 
ubuntu-+  2356  2267  0 21:19 ?        00:00:00 ssh-agent 
ubuntu-+  2361  2267  0 21:19 ?        00:00:00 upstart-event-bridge 
ubuntu-+  2376  2267  0 21:19 ?        00:00:00 upstart-file-bridge --daemon --u: 
ser 
ubuntu-+  2378  2267  0 21:19 ?        00:00:00 upstart-dbus-bridge --daemon --session --user --bus-name session 
ubuntu-+  2380  2267  0 21:19 ?        00:00:00 upstart-dbus-bridge --daemon --system --user --bus-name system 
ubuntu-+  2382  2267  0 21:19 ?        00:00:04 /usr/bin/ibus-daemon --daemonize --xim 
ubuntu-+  2396  2267  0 21:19 ?        00:00:02 /usr/lib/gnome-settings-daemon/gnome-settings-daemon 
ubuntu-+  2399  2267  0 21:19 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately 
ubuntu-+  2400  2267  0 21:19 ?        00:00:00 gnome-session --session=gnome 
ubuntu-+  2405  2399  0 21:19 ?        00:00:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3 
ubuntu-+  2411  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfsd 
ubuntu-+  2416  2382  0 21:20 ?        00:00:00 /usr/lib/ibus/ibus-dconf 
ubuntu-+  2417  2382  0 21:20 ?        00:00:01 /usr/lib/ibus/ibus-ui-gtk3 
ubuntu-+  2421  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/999/gvfs -f -o big_writes 
ubuntu-+  2423  2267  0 21:20 ?        00:00:00 /usr/lib/ibus/ibus-x11 --kill-daemon 
ubuntu-+  2436  2267  0 21:20 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session 
: gistryd --use-gnome-session 
root      2450     1  0 21:20 ?        00:00:00 /usr/lib/upower/upowerd 
ubuntu-+  2484  2267  0 21:20 ?        00:00:00 /usr/bin/gnome-keyring-daemon --start --components=gpg 
ubuntu-+  2487  2267  0 21:20 ?        00:00:00 /usr/bin/gnome-keyring-daemon --start --components=ssh 
ubuntu-+  2499  2267  0 21:20 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog 
rtkit     2501     1  0 21:20 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon 
ubuntu-+  2510  2400  6 21:20 ?        00:00:33 /usr/bin/gnome-shell 
colord    2529     1  0 21:20 ?        00:00:00 /usr/lib/colord/colord 
ubuntu-+  2531  2267  0 21:20 ?        00:00:00 /usr/lib/dconf/dconf-service 
ubuntu-+  2532  2396  0 21:20 ?        00:00:00 syndaemon -i 1.0 -t -K -R 
ubuntu-+  2536  2267  0 21:20 ?        00:00:00 /usr/lib/gnome-settings-daemon/gsd-printer 
ubuntu-+  2551  2382  0 21:20 ?        00:00:01 /usr/lib/ibus/ibus-engine-simple 
ubuntu-+  2684  2267  0 21:20 ?        00:00:00 /usr/lib/gnome-shell/gnome-shell-calendar-server 
ubuntu-+  2691  2267  0 21:20 ?        00:00:00 /usr/lib/evolution/evolution-source-registry 
ubuntu-+  2694  2267  0 21:20 ?        00:00:00 /usr/lib/telepathy/mission-control-5 
ubuntu-+  2696  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor 
root      2702     1  0 21:20 ?        00:00:00 /usr/lib/udisks2/udisksd --no-debug 
ubuntu-+  2704  2267  0 21:20 ?        00:00:00 /usr/lib/gnome-online-accounts/goa-daemon 
ubuntu-+  2715  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor 
ubuntu-+  2719  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor 
ubuntu-+  2723  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfs-goa-volume-monitor 
ubuntu-+  2738  2267  0 21:20 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor 
ubuntu-+  2751  2400  0 21:20 ?        00:00:00 nm-applet 
ubuntu-+  2754  2400  0 21:20 ?        00:00:02 /usr/lib/tracker/tracker-store 
ubuntu-+  2758  2400  0 21:20 ?        00:00:00 /usr/lib/tracker/tracker-miner-fs 
ubuntu-+  2780  2267  0 21:21 ?        00:00:00 /usr/lib/evolution/evolution-calendar-factory 
ubuntu-+  2786  2267  0 21:21 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2 
ubuntu-+  2832  2267  0 21:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata 
ubuntu-+  2849  2400  0 21:21 ?        00:00:00 zeitgeist-datahub 
ubuntu-+  2854  2267  0 21:21 ?        00:00:00 /usr/bin/zeitgeist-daemon 
ubuntu-+  2862  2267  0 21:21 ?        00:00:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts 
ubuntu-+  2883  2267  0 21:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0 
ubuntu-+  2902  2862  0 21:21 ?        00:00:00 /bin/cat 
ubuntu-+  2911  2400  0 21:21 ?        00:00:00 /usr/lib/evolution/3.10/evolution-alarm-notify 
ubuntu-+  3035  2510 17 21:21 ?        00:01:18 /usr/lib/firefox/firefox 
ubuntu-+  3038  2400  0 21:21 ?        00:00:00 update-notifier 
ubuntu-+  3122  2400  0 21:22 ?        00:00:00 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor 
root      3171     2  0 21:27 ?        00:00:00 [kworker/0:0] 
ubuntu-+  3189  2267  1 21:28 ?        00:00:00 /usr/bin/seahorse --no-window 
ubuntu-+  3275  2510  2 21:28 ?        00:00:00 gnome-terminal 
ubuntu-+  3289  3275  0 21:28 ?        00:00:00 gnome-pty-helper 
ubuntu-+  3290  3275  0 21:28 pts/0    00:00:00 bash 
```
:

---

### Post by cmac2 on 2014-05-19
Here are some of the other scans and commands I have run.   

```
ubuntu-gnome@ubuntu-gnome:~$ sudo chkrootkit
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
Checking `echo'...                                          not infected
Checking `egrep'...                                         not infected
Checking `env'...                                           not infected
Checking `find'...                                          not infected
Checking `fingerd'...                                       not found
Checking `gpm'...                                           not found
Checking `grep'...                                          not infected
Checking `hdparm'...                                        not infected
Checking `su'...                                            not infected
Checking `ifconfig'...                                      not infected
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not found
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not found
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... nothing found
Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
-268    /usr/share
-1    /usr/bin
-1    /usr/sbin
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient[23706])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user root deleted or never logged from lastlog!
user ubuntu-gnome deleted or never logged from lastlog!
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         4077 tty7   /usr/bin/X :0 -background none -verbose -auth  /var/run/gdm/auth-for-gdm-vBu9xd/database -seat seat0 -nolisten tcp vt7
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected
ubuntu-gnome@ubuntu-gnome:~$
```

---

### Post by cmac2 on 2014-05-19
chkrootkit found one positive so I did some more scans.  I did a lot of reading and know false positives are possible.  

Output from Rkhunter.  

```
ubuntu-gnome@ubuntu-gnome:~$ sudo rkhunter -c --enable all --disable none --rwo
Warning: Checking for prerequisites               [ Warning ]
         No output from the 'lsattr' command - all file immutable-bit checks will be skipped.
Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
Warning: The following processes are using deleted files:
         Process: /usr/sbin/cups-browsed    PID: 1513    File: /etc/passwd
         Process: /usr/bin/gnome-shell    PID: 4436    File: /home/ubuntu-gnome/.local/share/gvfs-metadata/root
         Process: /usr/lib/evolution/evolution-calendar-factory    PID:  4608    File: /home/ubuntu-gnome/.local/share/gvfs-metadata/home
         Process: /usr/lib/firefox/firefox    PID: 5553    File: /var/tmp/etilqs_03HNannjk3Xudpg
         Process: /usr/bin/gnome-terminal    PID: 5955    File: /tmp/#375691
Warning: Process '/sbin/dhclient' (PID 4867) is listening on the network.
Warning: Suspicious file types found in /dev:
         /dev/.udev/rules.d/root.rules: ASCII text
Warning: Hidden directory found: '/dev/.udev: directory '
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' 
ubuntu-gnome@ubuntu-gnome:~$
```

---

### Post by cmac2 on 2014-05-19
Can someone please explain the code tags?  I dont want to create any extra work for the moderators.  


RE: Unhide

Someone on another forum explained that I was using the wrong command.  I tried to add unhide and use the correct command and this is what I got.


```
ubuntu-gnome@ubuntu-gnome:~$ sudo apt-get install unhide
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following NEW packages will be installed:
  unhide
0 upgraded, 1 newly installed, 0 to remove and 122 not upgraded.
Need to get 1,460 kB of archives.
After this operation, 3,540 kB of additional disk space will be used.
(Had to delete the http in order to post) archive.ubuntu.com/ubuntu/ trusty/universe unhide amd64 20121229-1 [1,460 kB]
Fetched 1,460 kB in 2s (494 kB/s)   
Selecting previously unselected package unhide.
(Reading database ... 153216 files and directories currently installed.)
Preparing to unpack .../unhide_20121229-1_amd64.deb ...
Unpacking unhide (20121229-1) ...
Processing triggers for rkhunter (1.4.0-3) ...
[ Rootkit Hunter version 1.4.0 ]
File updated: searched for 169 files, found 138
Processing triggers for man-db (2.6.7.1-1) ...
Setting up unhide (20121229-1) ...
Processing triggers for rkhunter (1.4.0-3) ...
[ Rootkit Hunter version 1.4.0 ]
File updated: searched for 169 files, found 138
ubuntu-gnome@ubuntu-gnome:~$ sudo unhide-linux26 proc
sudo: unhide-linux26: command not found
ubuntu-gnome@ubuntu-gnome:~$ sudo unhide-linux26 brute
sudo: unhide-linux26: command not found
ubuntu-gnome@ubuntu-gnome:~$ unhide-linux26 proc
unhide-linux26: command not found
ubuntu-gnome@ubuntu-gnome:~$
```

I also tried to install gufw and had some different results.  Here is the output from the terminal.  

```
SCREEN (screen)' failed
/usr/share/gufw/gufw/view/gufw.py:73: Warning: invalid (NULL) pointer instance
  self.builder.add_from_file('/usr/share/gufw/ui/gufw.ui')
/usr/share/gufw/gufw/view/gufw.py:73: Warning: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
  self.builder.add_from_file('/usr/share/gufw/ui/gufw.ui')
(gufw.py:6233): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
 
(gufw.py:6233): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed
 
(gufw.py:6233): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed
/usr/bin/gufw-pkexec: line 15:  6233 Segmentation fault      (core dumped) python ${LOCATIONS[${i}]} $1
```
 
 
I also checked my router.  It said I had 97 active internet connections.   The IEP address was correct but it had 97 different entries from the  same address.                                     

 
         [URL="http://www.linuxforums.org/forum/editpost.php?p=950663&do=editpost"][IMG]http://www.linuxforums.org/forum/clear.gif[/IMG] 
The previous command ps -ef | less showed multiple terminals open.  I dont think any of these were my terminal.  I think I only had one open...two max. 

[/URL]ubuntu-+  1843  1432  0 21:19 tty6     00:00:00 -bash 
ubuntu-+  1903  1415  0 21:19 tty4     00:00:00 -bash 
ubuntu-+  1904  1429  0 21:19 tty3     00:00:00 -bash 
ubuntu-+  1905  1760  0 21:19 tty1     00:00:00 -bash 
ubuntu-+  1910  1428  0 21:19 tty2     00:00:00 -bash 
ubuntu-+  1911  1419  0 21:19 tty5     00:00:00 -bash 

[URL="http://www.linuxforums.org/forum/editpost.php?p=950663&do=editpost"]
[/URL]

---

### Post by cmac2 on 2014-05-19
So I was doing some more reading and came upon this post. 

[http://ubuntuforums.org/showthread.php?t=2223045](http://ubuntuforums.org/showthread.php?t=2223045)

I am experiencing several of the same things.  I actually had the same trouble with my name.  I registered as cmac and was given the name cmac2.  Not one but two.  Really weird!

Does anyone have any suggestions on how to research this further?  I want to get to the bottom of this and move on.  

Thank you for your time.

---

### Post by Lars Noodén on 2014-05-19
> **cmac2 said:**
> Can someone please explain the code tags?  I dont want to create any extra work for the moderators.  

The tags are [****code] and [/code].  The stuff in between them will get formatted in a fixed width typeface.  

The warning with init  might be a false positive,

[https://www.google.com/search?client=ubuntu&channel=fs&q=chkrootkit+false+positive+init](https://www.google.com/search?client=ubuntu&channel=fs&q=chkrootkit+false+positive+init)
[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/45456](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/45456)

check also using rkhunter and see if the results overlap.

---

### Post by cmac2 on 2014-05-19
3/4 of the way down on post 8 a hyperlink was created to another forum I had open on my webbrowser.  I didnt create this link.  As I was typing it was being created.  

Is this indicative of someone or a program altering what I type?  

I apologize for the strange posts and questions.  I have never encountered anything like this.

---

### Post by cmac2 on 2014-05-19
Lars, thank you for the help.  I did a check with rkhunter.  

The results are posted above your post along with some other strange stuff.  Any suggestions?

---

### Post by coffeecat on 2014-05-19
> **cmac2 said:**
> Can someone please explain the code tags?  I dont want to create any extra work for the moderators. 

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Instead of typing out [noparse]```

```[/noparse] around your terminal output, you can highlight it - use the advanced editor - and then use the toolbar icon that looks like #. I've added code tags where appropriate to some of your earlier posts. 

> **cmac2 said:**
> I actually had the same trouble with my name.  I registered as cmac and was given the name cmac2.  Not one but two.  Really weird!

No weirdness.

[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

> Please note, that the system may append a number to your forum account username. For example, if you chose “johdoe” as your Ubuntu One account name, and there is already a “johdoe” account in the forum database, your forum account will be named “johdoe2”, or "johdoe3" if there is already a johdoe2, and so on.

---

### Post by cmac2 on 2014-05-19
Thanks coffeecat.  I am checking everything and being paranoid due to the other stuff i am trying to figure out.  Thanks for putting in the code tags.

---

### Post by Lars Noodén on 2014-05-19
> **cmac2 said:**
> 3/4 of the way down on post 8 a hyperlink was created to another forum I had open on my webbrowser.  I didnt create this link.  As I was typing it was being created.  

Did you accidentally drag / drop an image from the other tab?

About the forum login name, there are some problems with the logins for some people since they went over to single signon.  The [resolution center](http://ubuntuforums.org/forumdisplay.php?f=123) would be the place to pursue that.

---

### Post by cmac2 on 2014-05-19
It was a copy and paste job.  For the bash items listed below.  I believe that I copied them from the same thread we are currently on.  

So I didnt drag and drop.

---

### Post by cmac2 on 2014-05-19
So I was reading another thread about similar problems.  There was a  post about checking your root password.  I ran the command and this is  the output.  

```
ubuntu-gnome@ubuntu-gnome:~$ stat -c%y /etc/passwd
2014-05-19 06:17:54.686625555 +0000
ubuntu-gnome@ubuntu-gnome:~$ 

```

---

### Post by coffeecat on 2014-05-19
> **cmac2 said:**
> It was a copy and paste job.  For the bash items listed below.  I believe that I copied them from the same thread we are currently on.  

So I didnt drag and drop.

With the copy and pasting, you may have had a URL in your cache and unwittingly pasted it. The forum software automatically adds url tags to http and https URL's. Looking at the source of your post #8, it looks as though you may have accidentally copied a fragment of a post in Linux Forums and then pasted it here. Were you browsing Linuxforums when you posted post #8?

Another thing to consider. Vbulletin defaults to WYSIWYG mode for the editor which makes using BBCode more difficult. It's easy to misplace and accidentally copy BBCode when in WYSIWYG mode and Linuxforums uses vbulletin as well. You can change to source mode in the editor with the toolbar icon that looks something like A/A - and you can change your default editor in Settings -> General Settings -> Message Editor Interface. I have mine set to Standard Editor.

> **cmac2 said:**
> So I was reading another thread about similar problems.  There was a  post about checking your root password.  I ran the command and this is  the output.  

```
ubuntu-gnome@ubuntu-gnome:~$ stat -c%y /etc/passwd
2014-05-19 06:17:54.686625555 +0000
ubuntu-gnome@ubuntu-gnome:~$ 

```

About the root account and password - you need to read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In short - you don't need to enable your root password.

---

### Post by cmac2 on 2014-05-19
Coffeecat, thanks for taking the time and thatks for the help.

I did have the linuxforum open in another tab.  I may have copied and pasted from their.  I thought it was from here...but I asked a similar question on that forum.  So I could have cut and pasted from their site.  Thanks for the tips about changing the default editor.  

I am running a live dvd of Ubuntu.  I havent enabled the root account.  I just started up the dvd.  

Everything that needs root access gets done with sudo.  

Is there as way it gets modified each time you start up the dvd?  Would that show the same results as the command above?

Any reason why it would show so many shells open?

---

### Post by cmac2 on 2014-05-19
Any explination of the rkhunter results?

Any thought on the hidden directory and the hidden file?  

Thanks  


   ubuntu-gnome@ubuntu-gnome:~$ sudo rkhunter -c --enable all --disable none --rwo 
Warning: Checking for prerequisites 
              [ Warning ]          No output from the 'lsattr' command - all file immutable-bit checks will be skipped.
 Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text 
Warning: The following processes are using deleted files:          Process: /usr/sbin/cups-browsed    PID: 1513    File: /etc/passwd          Process: /usr/bin/gnome-shell    PID: 4436    File: /home/ubuntu-gnome/.local/share/gvfs-metadata/root          Process: /usr/lib/evolution/evolution-calendar-factory    PID:  4608    File: /home/ubuntu-gnome/.local/share/gvfs-metadata/home          Process: /usr/lib/firefox/firefox    PID: 5553    File: /var/tmp/etilqs_03HNannjk3Xudpg          Process: /usr/bin/gnome-terminal    PID: 5955    File: /tmp/#375691
 Warning: Process '/sbin/dhclient' (PID 4867) is listening on the network. 
Warning: Suspicious file types found in /dev:          /dev/.udev/rules.d/root.rules: ASCII text 
Warning: Hidden directory found: '/dev/.udev: directory ' Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'  ubuntu-gnome@ubuntu-gnome:~$

---

### Post by cmac2 on 2014-05-19
My text has been changed a few times....or actually not changed.  

Coffeecat, can you please quote the post before this one?  It had some results from rkhunter posted in it.

Thank you for taking the time to help me out.
 
I just checked my router.  It has/had 127 active internet connections a few seconds ago when I checked.

---

### Post by cmac2 on 2014-05-19
So I used the command sudo kill 4436 and I was left with a black screen with the terminal open and the web pages open.  I dont have any of the Gnome gui.  Just a black screen.

Any suggestions?  It's a live dvd so all I have to do is reboot...but wanted to get this posted first.  I forgot to add that the PID came from the Rkhunter scan.  It was one of the warnings.  


[QUOTE=cmac2;13027657]

     PID: 4436    File: /home/ubuntu-gnome/.local/share/gvfs-metadata/root          Process: /usr/lib/evolution/evolution-calendar-factory

---

### Post by jon43 on 2014-05-19
I'm a little confused....

It sounds like you're booting off a live DVD, but are randomly terminating background processes and wondering why things then fail?

First, it'd be pretty hard to infect a live DVD, since there should be no cross-session storage taking place. Second, of course things are starting to fail if you're not infected with malware and you're randomly terminating system processes. They are obviously running for a reason...

---

### Post by coffeecat on 2014-05-20
Thread closed. The OP was advised to start a new thread which can be found here:

[http://ubuntuforums.org/showthread.php?t=2225092](http://ubuntuforums.org/showthread.php?t=2225092)

---

