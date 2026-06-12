---
title: "Apache2"
date: 2008-01-09
forum: Server Platforms
---

### Post by tmlingam on 2008-01-09
hi
am new to ubuntu, and i tried to install apache2, i was successfull and apache2 was working fine. but in due process of installing other packages somehow the apache got corrupted and now its not working.

when i try to restart

sudo /etc/init.d/apache2 restart

* Restarting web server apache2                                                httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs                              [fail]                                                                                    

i don't know what the problem is.

when i try to check the port

sudo lsof -i:80

COMMAND  PID     USER   FD   TYPE DEVICE SIZE NODE NAME
nginx   5059     root    6u  IPv4  16605       TCP *:www (LISTEN)
nginx   5060 www-data    6u  IPv4  16605       TCP *:www (LISTEN)

someone help me plss..

---

### Post by MJN on 2008-01-09
You've already got a web server, nginx, listening on port 80. Only one process can bind to any one port hence why Apache is bombing is out because nginx got there first.
 
You need to either move nginx onto a different port (if it's still needed) or, most likely a better solution, remove nginx entirely leaving port 80 available for Apache.
 
Mathew

---

### Post by _chimp on 2008-01-09
So as not to start another thread about the same problem -

sudo /etc/init.d/apache2 start

 * Starting web server apache2                                                                               (98 )Address already in use: make_sock: could not bind to address 127.0.0.5:80
no listening sockets available, shutting down
Unable to open logs

sudo lsof -i :80

NOTHING :(

So if nothing is listening on that port, why is it not starting.  Or am I missing something?

---

### Post by MJN on 2008-01-09
Does **sudo fuser 80/tcp** show anything?

Mathew

---

### Post by k_grdn on 2008-01-09
Hi,

Try sudo netstat -pant|grep 80.

Have you configured apache to bind to 127.0.0.5?

What address is in your vhosts file?

egrep '[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+' /etc/apache2/*/*

Some program must be listening on port 80?

Regards,

k_grdn

---

### Post by _chimp on 2008-01-10
The hosts are set up to listen on 127.0.0.5:80
As there were a whole load of errors about server name and named hosts, however they have been sorted (Well I think they have been sorted ;))

sudo fuser 80/tcp
NOTHING
sudo netstat -pant | grep 80
NOTHING

Everything I have tried says that there is nothing listening on 80.  So there must be something that I am missing.

---

### Post by MJN on 2008-01-10
Do you get anything when you connect to [http://127.0.0.5](http://127.0.0.5) in a web browser?
 
Post the output of **ps -aux** 
 
Mathew

---

### Post by _chimp on 2008-01-10
On [http://127.0.0.5](http://127.0.0.5) I get the "Cant connect to server..." message

ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2948  1852 ?        Ss   Jan09   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Jan09   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   Jan09   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Jan09   0:00 [watchdog/0]
root        15  0.0  0.0      0     0 ?        S<   Jan09   0:00 [events/0]
root        19  0.0  0.0      0     0 ?        S<   Jan09   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kblockd/0]
root        45  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kacpid]
root        46  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kacpi_notify]
root       174  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kseriod]
root       210  0.0  0.0      0     0 ?        S    Jan09   0:00 [pdflush]
root       211  0.0  0.0      0     0 ?        S    Jan09   0:00 [pdflush]
root       212  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kswapd0]
root       263  0.0  0.0      0     0 ?        S<   Jan09   0:00 [aio/0]
root      2238  0.0  0.0      0     0 ?        S<   Jan09   0:00 [ksuspend_usbd]
root      2239  0.0  0.0      0     0 ?        S<   Jan09   0:00 [khubd]
root      2285  0.0  0.0      0     0 ?        S<   Jan09   0:03 [ata/0]
root      2293  0.0  0.0      0     0 ?        S<   Jan09   0:00 [ata_aux]
root      2297  0.0  0.0      0     0 ?        S<   Jan09   0:00 [khpsbpkt]
root      2400  0.0  0.0      0     0 ?        S<   Jan09   0:00 [knodemgrd_0]
root      2401  0.0  0.0      0     0 ?        S<   Jan09   0:19 [scsi_eh_0]
root      2402  0.0  0.0      0     0 ?        S<   Jan09   0:00 [scsi_eh_1]
root      2436  0.0  0.0      0     0 ?        S<   Jan09   0:00 [scsi_eh_2]
root      2437  0.0  0.0      0     0 ?        S<   Jan09   0:00 [scsi_eh_3]
root      2723  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kjournald]
root      2934  0.0  0.0   3048  1396 ?        S<s  Jan09   0:00 /sbin/udevd --d
root      4033  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kpsmoused]
root      4859  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kjournald]
root      5097  0.0  0.0   1692   516 tty4     Ss+  Jan09   0:00 /sbin/getty 384
root      5098  0.0  0.0   1696   520 tty5     Ss+  Jan09   0:00 /sbin/getty 384
root      5100  0.0  0.0   1696   520 tty2     Ss+  Jan09   0:00 /sbin/getty 384
root      5102  0.0  0.0   1696   520 tty3     Ss+  Jan09   0:00 /sbin/getty 384
root      5104  0.0  0.0   1696   520 tty1     Ss+  Jan09   0:00 /sbin/getty 384
root      5105  0.0  0.0   1696   516 tty6     Ss+  Jan09   0:00 /sbin/getty 384
root      5318  0.0  0.0   2436  1328 ?        Ss   Jan09   0:00 /usr/sbin/acpid
root      5386  0.0  0.0      0     0 ?        S<   Jan09   0:00 [kondemand/0]
syslog    5461  0.0  0.0   1912   732 ?        Ss   Jan09   0:00 /sbin/syslogd -
root      5521  0.0  0.0   1840   536 ?        S    Jan09   0:00 /bin/dd bs 1 if
klog      5523  0.0  0.0   2484  1396 ?        Ss   Jan09   0:00 /sbin/klogd -P
103       5544  0.0  0.0   3160  1420 ?        Ss   Jan09   0:00 /usr/bin/dbus-d
root      5560  0.0  0.0  21784  2196 ?        Ssl  Jan09   0:00 /usr/sbin/Netwo
root      5574  0.0  0.0   3280  1296 ?        Ss   Jan09   0:00 /usr/sbin/Netwo
root      5587  0.0  0.0   3084   836 ?        Ss   Jan09   0:00 /usr/bin/system
root      5588  0.0  0.0   2772  1312 ?        S    Jan09   0:00 dbus-daemon --s
107       5607  0.0  0.1   6108  4292 ?        Ss   Jan09   0:00 /usr/sbin/hald
root      5608  0.0  0.0   3096  1108 ?        S    Jan09   0:00 hald-runner
root      5678  0.0  0.0   3156  1108 ?        S    Jan09   0:00 /usr/lib/hal/ha
107       5679  0.0  0.0   2164   884 ?        S    Jan09   0:00 hald-addon-acpi
107       5763  0.0  0.0   3264  1228 ?        S    Jan09   0:00 hald-addon-stor
postgres  5792  0.0  0.1  38376  4576 ?        S    Jan09   0:00 /usr/lib/postgr
postgres  5906  0.0  0.0  38376  1284 ?        Ss   Jan09   0:00 postgres: write
postgres  5907  0.0  0.0   9824  1028 ?        Ss   Jan09   0:00 postgres: stats
root      6135  0.0  0.0   6428  1348 ?        Ss   Jan09   0:00 /usr/sbin/nmbd
root      6153  0.0  0.0   9900  2236 ?        Ss   Jan09   0:00 /usr/sbin/smbd
root      6192  0.0  0.0   7848  2460 ?        Ssl  Jan09   0:00 /usr/sbin/conso
root      6270  0.0  0.0   9900   920 ?        S    Jan09   0:00 /usr/sbin/smbd
avahi     6284  0.0  0.0   2844  1460 ?        Ss   Jan09   0:00 avahi-daemon: r
avahi     6286  0.0  0.0   2732   456 ?        Ss   Jan09   0:00 avahi-daemon: c
root      6315  0.0  0.0   1992   968 ?        Ss   Jan09   0:00 /usr/sbin/dhcdb
root      6335  0.0  0.0   2928  1184 ?        Ss   Jan09   0:00 /usr/sbin/hcid
root      6351  0.0  0.0   2772   984 ?        S    Jan09   0:00 /usr/lib/blueto
root      6352  0.0  0.0   2844  1216 ?        S    Jan09   0:00 /usr/lib/blueto
root      6361  0.0  0.0      0     0 ?        S<   Jan09   0:00 [krfcommd]
root      6395  0.0  0.0  13348  1772 ?        Ss   Jan09   0:00 /usr/sbin/gdm
ntp       6444  0.0  0.0   4128  1244 ?        Ss   Jan09   0:00 /usr/sbin/ntpd
daemon    6479  0.0  0.0   1960   428 ?        Ss   Jan09   0:00 /usr/sbin/atd
root      6493  0.0  0.0   2332   912 ?        Ss   Jan09   0:00 /usr/sbin/cron
sy        6726  0.0  0.0   2904  1132 ?        Ss   Jan09   0:00 dbus-daemon --f
sy        6793  0.0  0.1   8876  3576 ?        S    Jan09   0:00 /usr/lib/gnome-
root      7626  0.0  0.0  22360  2752 ?        Ssl  Jan09   0:00 /usr/sbin/cupsd
root     10525  0.0  0.0  13860  3052 ?        S    09:18   0:00 /usr/sbin/gdm
root     10653  0.0  0.0      0     0 ?        S<   09:18   0:00 [migration/1]
root     10654  0.0  0.0      0     0 ?        SN   09:18   0:00 [ksoftirqd/1]
root     10655  0.0  0.0      0     0 ?        S<   09:18   0:00 [watchdog/1]
root     10656  0.0  0.0      0     0 ?        S<   09:18   0:00 [kondemand/1]
root     10657  0.0  0.0      0     0 ?        S<   09:18   0:00 [ata/1]
root     10658  0.0  0.0      0     0 ?        S<   09:18   0:00 [aio/1]
root     10659  0.0  0.0      0     0 ?        S<   09:18   0:00 [kblockd/1]
root     10660  0.0  0.0      0     0 ?        S<   09:18   0:00 [events/1]
root     10661  0.0  0.0      0     0 ?        S<   09:18   0:00 [migration/2]
root     10662  0.0  0.0      0     0 ?        SN   09:18   0:00 [ksoftirqd/2]
root     10663  0.0  0.0      0     0 ?        S<   09:18   0:00 [watchdog/2]
root     10664  0.0  0.0      0     0 ?        S<   09:18   0:00 [kondemand/2]
root     10665  0.0  0.0      0     0 ?        S<   09:18   0:00 [ata/2]
root     10666  0.0  0.0      0     0 ?        S<   09:18   0:00 [aio/2]
root     10667  0.0  0.0      0     0 ?        S<   09:18   0:00 [kblockd/2]
root     10668  0.0  0.0      0     0 ?        S<   09:18   0:00 [events/2]
root     10669  0.0  0.0      0     0 ?        S<   09:18   0:00 [migration/3]
root     10670  0.0  0.0      0     0 ?        SN   09:18   0:00 [ksoftirqd/3]
root     10671  0.0  0.0      0     0 ?        S<   09:18   0:00 [watchdog/3]
root     10672  0.0  0.0      0     0 ?        S<   09:18   0:00 [kondemand/3]
root     10673  0.0  0.0      0     0 ?        S<   09:18   0:00 [ata/3]
root     10674  0.0  0.0      0     0 ?        S<   09:18   0:00 [aio/3]
root     10675  0.0  0.0      0     0 ?        S<   09:18   0:00 [kblockd/3]
root     10676  0.0  0.0      0     0 ?        S<   09:18   0:00 [events/3]
sy       10702  3.0  0.6  64804 20928 ?        Sl   11:42   0:00 gnome-terminal
sy       10705  0.0  0.0   2668   740 ?        S    11:42   0:00 gnome-pty-helpe
sy       10706  1.6  0.0   5768  3040 pts/0    Ss   11:42   0:00 bash
sy       10723  0.0  0.0   2624  1008 pts/0    R+   11:42   0:00 ps -aux
root     11267  2.0  1.8  64264 56736 tty7     RLs+ 09:18   3:00 /usr/bin/X :0 -
root     11363  0.0  0.0      0     0 ?        S<   09:18   0:00 [scsi_eh_7]
root     11364  0.0  0.0      0     0 ?        S<   09:18   0:00 [usb-storage]
root     11396  0.0  0.0      0     0 ?        S<   09:18   0:00 [rt61pci]
107      11448  0.0  0.0   2160   896 ?        S    09:18   0:00 hald-addon-keyb
107      11496  0.0  0.0   2164   896 ?        S    09:18   0:00 hald-addon-keyb
root     11504  0.0  0.0      0     0 ?        S<   09:18   0:00 [scsi_eh_8]
root     11505  0.0  0.0      0     0 ?        S<   09:18   0:00 [usb-storage]
107      11585  0.0  0.0   2160   892 ?        S    09:18   0:00 hald-addon-keyb
107      11598  0.0  0.0   2164   896 ?        S    09:18   0:00 hald-addon-keyb
dhcp     11714  0.0  0.0   2420  1168 ?        S    09:18   0:00 /sbin/dhclient
107      11875  0.0  0.0   3264  1184 ?        S    09:18   0:00 hald-addon-stor
107      11877  0.0  0.0   3264  1184 ?        S    09:18   0:00 hald-addon-stor
107      11879  0.0  0.0   3264  1184 ?        S    09:18   0:00 hald-addon-stor
107      11881  0.0  0.0   3264  1184 ?        S    09:18   0:00 hald-addon-stor
107      11883  0.0  0.0   3260  1180 ?        S    09:18   0:00 hald-addon-stor
sy       11886  0.0  0.0  13424  1952 ?        SL   09:18   0:00 /usr/bin/gnome-
sy       11889  0.0  0.2  28260  7684 ?        Ssl  09:18   0:00 x-session-manag
sy       11924  0.0  0.0   4436   544 ?        Ss   09:18   0:00 /usr/bin/ssh-ag
sy       11926  0.0  0.1   7196  4324 ?        S    09:18   0:00 /usr/lib/libgco
sy       11930  0.0  0.0   2908  1140 ?        Ss   09:18   0:00 dbus-daemon --f
sy       11932  0.0  0.3  38740 10192 ?        Sl   09:18   0:00 /usr/lib/gnome-
sy       11938  0.0  0.0   1756   540 ?        S    09:18   0:00 /bin/sh /usr/bi
sy       11940  0.0  0.6  44152 21744 ?        S    09:18   0:05 gnome-panel --s
sy       11942  0.0  0.8  81328 25532 ?        S    09:18   0:01 nautilus --no-d
sy       11947  0.0  0.1  19800  5212 ?        Ss   09:18   0:00 gnome-volume-ma
sy       11951  0.0  0.1   8880  3556 ?        S    09:18   0:00 /usr/lib/gnome-
sy       11956  0.0  0.1  41148  3276 ?        Ssl  09:18   0:00 /usr/lib/bonobo
sy       12003  0.0  0.0  16776  2880 ?        Ss   09:18   0:03 gnome-screensav
sy       12046  0.0  0.3  25500 12296 ?        S    09:18   0:03 /usr/bin/gtk-wi
sy       12047  0.1  0.8  63420 26132 ?        SL   09:18   0:16 /usr/bin/compiz
sy       12052  0.0  0.2  19692  7084 ?        S    09:18   0:00 vino-session --
sy       12053  0.0  0.1  13716  5688 ?        S    09:18   0:00 bluetooth-apple
sy       12056  0.0  0.4  30200 13232 ?        S    09:18   0:00 update-notifier
sy       12059  0.0  0.3  68288 10288 ?        Sl   09:18   0:00 /usr/lib/evolut
sy       12062  1.0  0.6  39812 19700 ?        SNl  09:18   1:34 trackerd
sy       12064  0.0  0.3  23000 11836 ?        S    09:18   0:00 python /usr/sha
sy       12065  0.0  0.4  30800 12648 ?        S    09:18   0:00 nm-applet --sm-
sy       12071  0.0  0.3  58592 10000 ?        S    09:18   0:00 /usr/lib/gnome-
sy       12076  0.0  0.2  22628  8000 ?        Ss   09:18   0:00 gnome-power-man
sy       12085  0.0  0.3  36800  9736 ?        Sl   09:18   0:00 /usr/lib/evolut
sy       12090  0.0  0.0   2660   892 ?        S    09:18   0:00 /usr/lib/nautil
sy       12108  0.0  0.2  67424  6816 ?        Sl   09:18   0:00 /usr/lib/evolut
sy       12134  0.0  0.3  28036 12344 ?        S    09:18   0:00 /usr/lib/fast-u
sy       12136  0.0  0.9  62360 30132 ?        Sl   09:18   0:00 /usr/bin/python
sy       12138  0.0  0.4  37672 13612 ?        Sl   09:18   0:00 /usr/lib/gnome-
sy       12151  0.0  0.0   1752   524 ?        S    09:19   0:00 /bin/sh /usr/bi
sy       12163  0.0  0.0   1752   528 ?        S    09:19   0:00 /bin/sh /usr/li
sy       12167  2.0  5.0 284476 157776 ?       Sl   09:19   2:59 /usr/lib/firefo
sy       12180  0.4  3.1 240160 98848 ?        Sl   09:19   0:38 java_vm 
sy       12440  0.0  0.3  24332 11156 ?        S    09:25   0:00 /usr/lib/notifi

Any ideas?  As iv been hitting my head on a wall for a while...

---

### Post by MJN on 2008-01-10
If you redirect the output to a file (**ps aux > processes.txt**) and post the contents of that it won't be truncated. (Note: I wrongly put the '-' in my first command)
 
I can't see anything that immediately jumps out, but the python processes could hold some clue.
 
Having said that, we're pretty much ruled out port 80 already being bound to.
 
Has Apache ever worked? What's the background the position you're now?
 
Mathew

---

### Post by _chimp on 2008-01-10
Apache used to work...when it was 2.0 compiled from source.
The ubuntu version has never worked and seeing as it is different from the default distribution from apache most of the configuration information has to be modified to get it to work with ubuntu.  
I managed to get rid of all of the warnings about hosts and everything else, but I have never got the actual server to work :(

---

### Post by MJN on 2008-01-10
Are you saying that you used to use a self-compiled release of Apache 2.0, but now you're using the repository package v2.2?
 
Which config are you using? The default from the repository or your config from your self-compiled release? If the latter then I'm afraid you're on your own as who knows what mismatches might now exist...
 
Mathew

---

