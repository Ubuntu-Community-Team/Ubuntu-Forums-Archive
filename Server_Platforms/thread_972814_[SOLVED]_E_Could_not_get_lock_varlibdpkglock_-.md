---
title: "[SOLVED] E: Could not get lock /var/lib/dpkg/lock -"
date: 2008-11-06
forum: Server Platforms
---

### Post by Fertech on 2008-11-06
im trying to install mailman but i get this error. does anyone knows what this means.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

---

### Post by MJN on 2008-11-06
Do you have any other package managers open? Only one can manipulate the package databases and other related files at any one time.
 
Check the process list (**ps aux**) for any mention of apt, synaptic, ... - and kill them.
 
Mathew

---

### Post by Fertech on 2008-11-06
well i install  mailman, and thats when everything went wrong. i try to config the postfix.

---

### Post by MJN on 2008-11-06
Did you do what I suggested?

(Post the **ps aux** output if you're not sure)

Mathew

---

### Post by Fertech on 2008-11-06
yea but i there so much information i'm confuse

---

### Post by Fertech on 2008-11-06
do you think this can be it, avahi     4985  0.0  0.0   2760  1412 ?        Ss   10:47   0:00 avahi-daemon: running [fertech-desktop.local]

---

### Post by MJN on 2008-11-06
Unlikely. Post the **ps aux** output then we can help.

Mathew

---

### Post by Fertech on 2008-11-06
fertech@fertech-desktop:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2952  1820 ?        Ss   10:47   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:47   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:47   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   10:47   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:47   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:47   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   10:47   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   10:47   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   10:47   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   10:47   0:00 [kacpi_notify]
root       112  0.0  0.0      0     0 ?        S<   10:47   0:00 [kseriod]
root       146  0.0  0.0      0     0 ?        S    10:47   0:00 [pdflush]
root       147  0.0  0.0      0     0 ?        S    10:47   0:00 [pdflush]
root       148  0.0  0.0      0     0 ?        S<   10:47   0:00 [kswapd0]
root       189  0.0  0.0      0     0 ?        S<   10:47   0:00 [aio/0]
root      1418  0.0  0.0      0     0 ?        S<   10:47   0:00 [ksuspend_usbd]
root      1422  0.0  0.0      0     0 ?        S<   10:47   0:00 [khubd]
root      1485  0.0  0.0      0     0 ?        S<   10:47   0:01 [ata/0]
root      1490  0.0  0.0      0     0 ?        S<   10:47   0:00 [ata_aux]
root      1571  0.0  0.0      0     0 ?        S<   10:47   0:01 [scsi_eh_0]
root      1573  0.0  0.0      0     0 ?        S<   10:47   0:00 [scsi_eh_1]
root      2427  0.0  0.0      0     0 ?        S<   10:47   0:00 [kjournald]
root      2697  0.0  0.0   2428   976 ?        S<s  10:47   0:00 /sbin/udevd --d
root      2962  0.0  0.0      0     0 ?        S<   10:47   0:00 [kpsmoused]
root      4531  0.0  0.0   1716   504 tty4     Ss+  10:47   0:00 /sbin/getty 384
root      4532  0.0  0.0   1716   512 tty5     Ss+  10:47   0:00 /sbin/getty 384
root      4536  0.0  0.0   1716   512 tty2     Ss+  10:47   0:00 /sbin/getty 384
root      4537  0.0  0.0   1716   508 tty3     Ss+  10:47   0:00 /sbin/getty 384
root      4539  0.0  0.0   1716   508 tty6     Ss+  10:47   0:00 /sbin/getty 384
root      4714  0.0  0.0   2456  1356 ?        Ss   10:47   0:00 /usr/sbin/acpid
root      4742  0.0  0.0      0     0 ?        S<   10:47   0:00 [kondemand/0]
syslog    4829  0.0  0.0   1936   648 ?        Ss   10:47   0:00 /sbin/syslogd -
root      4888  0.0  0.0   1872   540 ?        S    10:47   0:00 /bin/dd bs 1 if
klog      4890  0.0  0.0   3256  2060 ?        Ss   10:47   0:00 /sbin/klogd -P
108       4914  0.0  0.0   2828  1316 ?        Ss   10:47   0:00 /usr/bin/dbus-d
root      4932  0.0  0.1  12892  2096 ?        Ssl  10:47   0:00 /usr/sbin/Netwo
root      4948  0.0  0.0   3536  1308 ?        Ss   10:47   0:00 /usr/sbin/Netwo
root      4963  0.0  0.0   4112  1104 ?        Ss   10:47   0:00 /usr/bin/system
avahi     4985  0.0  0.0   2860  1456 ?        Ss   10:47   0:00 avahi-daemon: r
avahi     4986  0.0  0.0   2760   464 ?        Ss   10:47   0:00 avahi-daemon: c
clamav    5251  0.1  2.8  69016 58912 ?        Ss   10:47   0:16 /usr/sbin/clamd
clamav    5353  0.0  0.0   3008  1232 ?        Ss   10:47   0:00 /usr/bin/freshc
clamav    5584  0.1  5.5 133076 114552 ?       Ssl  10:47   0:12 /usr/sbin/clama
clamsmtp  5596  0.0  0.0   2044   420 ?        Ss   10:47   0:00 /usr/sbin/clams
root      5620  0.0  0.1   5920  2296 ?        Ss   10:47   0:00 /usr/sbin/cupsd
root      5637  0.0  0.0      0     0 ?        S<   10:47   0:00 [loop0]
root      5646  0.0  0.0      0     0 ?        S<   10:47   0:00 [kjournald]
havp      5650  0.0  2.8  62504 59068 ?        Rs   10:47   0:05 /usr/sbin/havp
havp      5651  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5652  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5656  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5657  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5658  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5660  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5661  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5663  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5665  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5666  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5668  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5670  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5671  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5672  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
havp      5674  0.0  2.7  62564 57856 ?        S    10:47   0:00 /usr/sbin/havp
havp      5675  0.0  2.7  62564 57768 ?        S    10:47   0:00 /usr/sbin/havp
icecast   5680  0.1  0.0   3352   960 ?        Sl   10:47   0:08 /usr/bin/icecas
root      5761  0.0  0.0   5396  1732 ?        Ss   10:47   0:00 /usr/lib/postfi
root      5895  0.0  0.0   2020   900 ?        Ss   10:47   0:00 /usr/sbin/dhcdb
111       5916  0.0  0.1   6160  4012 ?        Ss   10:47   0:00 /usr/sbin/hald
root      5919  0.0  0.1   7884  2384 ?        Ssl  10:47   0:00 /usr/sbin/conso
root      5981  0.0  0.0   3352  1152 ?        S    10:47   0:00 hald-runner
111       6001  0.0  0.0   2204   904 ?        S    10:47   0:00 hald-addon-acpi
root      6014  0.0  0.0   3416  1148 ?        S    10:47   0:00 hald-addon-inpu
root      6030  0.0  0.0   3420  1136 ?        S    10:47   0:02 hald-addon-stor
root      6071  0.0  0.0   3172  1264 ?        Ss   10:47   0:00 /usr/sbin/hcid
root      6080  0.0  0.0      0     0 ?        S<   10:47   0:00 [btaddconn]
root      6081  0.0  0.0      0     0 ?        S<   10:47   0:00 [btdelconn]
root      6095  0.0  0.0   3084  1284 ?        S    10:47   0:00 /usr/lib/blueto
root      6096  0.0  0.0   3020  1088 ?        S    10:47   0:00 /usr/lib/blueto
root      6099  0.0  0.0      0     0 ?        S<   10:47   0:00 [krfcommd]
root      6125  0.0  0.0  14048  1592 ?        Ss   10:47   0:00 /usr/sbin/gdm
root      6135  0.0  0.1  14504  2972 ?        S    10:47   0:00 /usr/sbin/gdm
root      6149  0.1  0.3  12096  7052 tty7     Ss+  10:47   0:10 /usr/bin/X :0 -
daemon    6168  0.0  0.0   1984   420 ?        Ss   10:47   0:00 /usr/sbin/atd
root      6184  0.0  0.0   2104   896 ?        Ss   10:47   0:00 /usr/sbin/cron
dhcp      6283  0.0  0.0   2440  1180 ?        S    10:47   0:00 /sbin/dhclient
root      6360  0.0  0.0   1716   512 tty1     Ss+  10:47   0:00 /sbin/getty 384
postfix   6475  0.0  0.0   5444  1680 ?        S    10:47   0:00 qmgr -l -t fifo
fertech   6489  0.0  0.2   7264  4348 ?        S    10:48   0:02 /usr/lib/libgco
fertech   6491  0.0  0.0  14340  2044 ?        S    10:48   0:00 /usr/bin/gnome-
fertech   6493  0.0  0.3  28856  7536 ?        Ssl  10:48   0:00 x-session-manag
fertech   6560  0.0  0.0   1772   492 ?        S    10:48   0:00 /bin/sh /usr/sh
fertech   6565 32.2  7.1 174796 147508 ?       R    10:48  43:40 Xgl :1 -accel x
fertech   6576  0.0  0.3  23056  6832 ?        Ss   10:48   0:00 /usr/bin/seahor
fertech   6580  0.0  0.0   2828  1236 ?        Ss   10:48   0:00 dbus-daemon --f
fertech   6581  0.0  0.4  39976 10292 ?        Sl   10:48   0:02 gnome-settings-
fertech   6585  0.0  0.2  28472  5712 ?        Sl   10:48   0:03 /usr/bin/pulsea
fertech   6592  0.0  0.1   5776  2264 ?        S    10:48   0:00 /usr/lib/pulsea
fertech   6607  0.0  0.1  40108  3244 ?        Ssl  10:48   0:00 /usr/lib/bonobo
fertech   6608  0.1  0.2  15740  5688 ?        Ss   10:48   0:10 gnome-screensav
fertech   6611  0.0  0.0   1772   532 ?        S    10:48   0:00 /bin/sh /usr/bi
fertech   6614  0.0  0.3  17776  6756 ?        S    10:48   0:01 /usr/lib/vino/v
fertech   6615  0.1  1.0  38616 22784 ?        S    10:48   0:13 gnome-panel --s
fertech   6616  0.1  1.3  72180 29000 ?        S    10:48   0:15 nautilus --no-d
fertech   6629  0.3  0.5  19740 12388 ?        S    10:48   0:27 /usr/bin/compiz
fertech   6631  0.0  0.1   5372  2096 ?        S    10:48   0:00 /usr/lib/gvfs/g
fertech   6634  0.0  0.2  14592  5740 ?        S    10:48   0:00 bluetooth-apple
fertech   6638  0.0  0.6  26416 14116 ?        S    10:48   0:00 update-notifier
fertech   6643  0.0  0.0  29048  1900 ?        Ssl  10:48   0:00 /usr/lib/gvfs//
fertech   6648  0.0  0.0   4772  1740 ?        S    10:48   0:00 /usr/bin/obex-d
fertech   6650  0.0  0.4  62324 10216 ?        Sl   10:48   0:00 /usr/lib/evolut
fertech   6654  0.0  0.2  15208  5520 ?        S    10:48   0:00 tracker-applet
fertech   6656  0.0  0.5  30740 10380 ?        SNl  10:48   0:00 trackerd
fertech   6660  0.0  0.5  25192 11836 ?        S    10:48   0:05 nm-applet --sm-
fertech   6661  0.0  0.5  24260 12176 ?        S    10:48   0:00 python /usr/sha
fertech   6663  0.0  0.2  20664  4692 ?        Ss   10:48   0:00 /usr/lib/gnome-
fertech   6664  0.0  0.3  23448  7736 ?        Ss   10:48   0:00 gnome-power-man
fertech   6671  0.0  0.1   5372  2132 ?        S    10:48   0:00 /usr/lib/gvfs/g
fertech   6674  0.0  0.1  22032  2604 ?        S    10:48   0:00 /usr/lib/gvfs/g
fertech   6686  0.0  0.4  38932  9768 ?        Sl   10:48   0:00 /usr/lib/evolut
fertech   6693  0.0  0.3  67964  6580 ?        Sl   10:48   0:00 /usr/lib/evolut
fertech   6696  0.0  0.5  41212 11868 ?        S    10:48   0:00 /usr/lib/gnome-
fertech   6698  0.0  0.4  23320 10196 ?        S    10:48   0:00 /usr/lib/gnome-
fertech   6701  0.0  0.7  44760 15128 ?        Sl   10:48   0:00 /usr/lib/gnome-
fertech   6705  0.0  0.6  26104 13224 ?        S    10:48   0:00 /usr/lib/fast-u
fertech   6723  0.0  0.0   1772   484 ?        Ss   10:48   0:00 /bin/sh -c /usr
fertech   6724  0.0  0.0   1772   504 ?        S    10:48   0:00 /bin/sh /usr/bi
fertech   6726  0.0  0.5  20684 11688 ?        S    10:48   0:03 /usr/bin/gtk-wi
fertech   6739 10.3  5.3 234148 110448 ?       Sl   10:48  13:57 /usr/lib/firefo
fertech   6777  0.0  0.6  23552 12960 ?        S    10:49   0:00 /usr/lib/notifi
fertech   7082  0.0  0.6  24820 13904 ?        S    11:45   0:00 gksu /usr/sbin/
root      7083  0.3  1.9  50836 39772 ?        Ss   11:45   0:17 /usr/sbin/synap
root      7090  0.0  0.0   2912   848 ?        S    11:47   0:00 gnome-pty-helpe
fertech   7180  0.0  1.1  69820 24012 ?        S    11:55   0:01 /usr/lib/kde4/b
fertech   7188  0.0  1.5 161912 33132 ?        S    11:57   0:01 /usr/lib/kde4/b
fertech   7199  0.0  0.9  32064 18764 ?        S    11:59   0:01 gedit file:///v
postfix   7274  0.0  0.0   5404  1640 ?        S    12:27   0:00 pickup -l -t fi
fertech   7435  0.6  1.7 163732 36192 ?        S    12:59   0:01 /usr/lib/kde4/b
fertech   7442  0.0  0.2  28172  4564 ?        Ss   13:00   0:00 kdeinit4: kdein
fertech   7443  0.0  0.4  28872  9260 ?        S    13:00   0:00 klauncher
fertech   7445  0.1  0.4  50236  9404 ?        S    13:00   0:00 kded4
fertech   7449  0.0  0.3  44852  8192 ?        S    13:00   0:00 /usr/lib/kde4/b
fertech   7458  6.2  1.1  83412 22904 ?        Rl   13:03   0:00 gnome-terminal
fertech   7460  0.0  0.0   2912   852 ?        S    13:03   0:00 gnome-pty-helpe
fertech   7461  3.5  0.1   6128  3544 pts/0    Rs   13:03   0:00 bash
fertech   7478  0.0  0.0   2644  1004 pts/0    R+   13:03   0:00 ps aux
fertech@fertech-desktop:~$

---

### Post by MJN on 2008-11-06
You've certainly got Synaptic running - is that what you're using to (attempt to) install mailman?

If not, kill it with **sudo killall synaptic**

It would be really helpful if you can provide as much information as possible when asking for help - in this case the exact steps you were doing prior to the problem occurring (e.g. whether you were installing using synaptic, apt-get, etc).

Incidentally, you'd be better off widening your terminal window and re-running **ps aux** - then copy-and-paste the output without the truncated lines.

Mathew

---

### Post by Fertech on 2008-11-06
yes thats what im using, so now what do i do

---

### Post by MJN on 2008-11-06
Try closing Synaptic down, then installing mailman from the command line with **sudo apt-get install mailman**

Mathew

---

### Post by Fertech on 2008-11-06
how do i copy-and-paste the output without the truncated lines

---

### Post by MJN on 2008-11-06
By doing what I said - '...widening the terminal window and then re-running **ps aux**...'

Have you tried installing mailman from the command line?

Mathew

---

### Post by Fertech on 2008-11-06
fertech@fertech-desktop:~$ sudo apt-get install mailman
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pwgen
Suggested packages:
  listadmin lynx
The following NEW packages will be installed:
  mailman pwgen
0 upgraded, 2 newly installed, 0 to remove and 128 not upgraded.
Need to get 8631kB of archives.
After this operation, 40.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main pwgen 2.06-1 [19.5kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main mailman 1:2.1.9-9ubuntu1 [8612kB]
Fetched 8631kB in 16s (531kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package pwgen.
(Reading database ... 204410 files and directories currently installed.)
Unpacking pwgen (from .../archives/pwgen_2.06-1_i386.deb) ...
Selecting previously deselected package mailman.
Unpacking mailman (from .../mailman_1%3a2.1.9-9ubuntu1_i386.deb) ...
Setting up pwgen (2.06-1) ...
Setting up mailman (1:2.1.9-9ubuntu1) ...
Looking for enabled languages (this may take some time) ... done.
Installing site language en ............................................ done.
Configuring mailman for domain fertech-desktop ...
Upgrading from version 0x0 to 0x20109f0
getting rid of old source files
 * Site list for mailman (usually named mailman) missing.
 * Please create it; until then, mailman will refuse to start.

fertech@fertech-desktop:~$

---

### Post by MJN on 2008-11-06
Excellent - you're sorted.

---

### Post by Fertech on 2008-11-06
fertech@fertech-desktop:~$ sudo apt-get install mailman
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mailman is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
fertech@fertech-desktop:~$

---

### Post by MJN on 2008-11-06
You installed it two posts up!

Hint:

```
mailman is already the newest version.
```

Mathew

---

### Post by Fertech on 2008-11-06
now that i install mailman, my website is down. [http://fertech.ath.cx](http://fertech.ath.cx)
did mailman config my apache.

---

### Post by MJN on 2008-11-06
I've never used mailman but, no, I wouldn't have thought so.

Looking at your process list (albeit truncated) it would appear you don't even have Apache running. Start it with **sudo /etc/init.d/apache2 start**

Mathew

---

### Post by Fertech on 2008-11-06
ok its up now thank you for taking the time to help me. im going to try to config the mailman now if i need help. i will just post it on here.

---

### Post by MJN on 2008-11-06
You're welcome.

You'd be better off starting a new thread with any mailman queries - it'll be off-topic for this thread title and risks not getting any replies.

Mathew

---

### Post by abnaxus on 2010-10-30
hey guys...i'm having the same problem. tried the solutions posted here but no luck. actionparsnip tried to help me, but all his solutions ended up no were. 

please check this link for more details: [https://answers.launchpad.net/ubuntu/+question/131742](https://answers.launchpad.net/ubuntu/+question/131742)

thanks...in advance!

:(

---

### Post by abnaxus on 2010-11-02
> **abnaxus said:**
> hey guys...i'm having the same problem. tried the solutions posted here but no luck. actionparsnip tried to help me, but all his solutions ended up no were. 

please check this link for more details: [https://answers.launchpad.net/ubuntu/+question/131742](https://answers.launchpad.net/ubuntu/+question/131742)

thanks...in advance!

:(
anyone?! :-/

---

