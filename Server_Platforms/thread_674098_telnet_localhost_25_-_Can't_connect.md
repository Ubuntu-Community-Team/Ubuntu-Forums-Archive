---
title: "telnet localhost 25 - Can't connect"
date: 2008-01-21
forum: Server Platforms
---

### Post by dethredic on 2008-01-21
I am trying to set up Postfix With SMTP-AUTH And TLS and it is part of a tutorial I am following.

One of the steps I have to type telnet localhost 25 and connect, but I get :unable to connect to remote host: connection timed out.

How can I fix this?

Tutorial is [here]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p5") BTW.

---

### Post by MJN on 2008-01-21
Do you have a firewall that might be blocking the connection (even to self)? Is Postfix definitely running? (one check is to run **sudo lsof -i :25** which will show you what, if any, process is listening on port 25 - you should see at least smtpd running by postfix)

Mathew

---

### Post by dethredic on 2008-01-21
ok, there are 2 things listening to port 25.

EDIT: No firewall

EDIT: the internet works as well.

---

### Post by MJN on 2008-01-21
No, that's alright - myhostname is just the Postfix directive/setting so you've done the right thing by only changing the value.

What was the lsof output? (two entries is fine - usually master on IPv4 and v6)

Let's also take a look at the output of **ps aux** (you might want to actually run **ps aux > output.txt** and copy/paste the contents of that file otherwise you might find the processes are truncated).

Mathew

---

### Post by dethredic on 2008-01-21
Here are the processes
> 
root@server1:/etc/postfix/ssl# sudo lsof -i :25
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
master  7513 root   11u  IPv4  24200       TCP *:smtp (LISTEN)
master  7513 root   12u  IPv6  24202       TCP *:smtp (LISTEN)
root@server1:/etc/postfix/ssl# 


here is the ps aux
> 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2948  1856 ?        Ss   10:58   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:58   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:58   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   10:58   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:58   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:58   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        SN   10:58   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   10:58   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   10:58   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   10:58   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   10:58   0:00 [khelper]
root        31  0.0  0.0      0     0 ?        S<   10:58   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S<   10:58   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S<   10:58   0:00 [kacpid]
root        34  0.0  0.0      0     0 ?        S<   10:58   0:00 [kacpi_notify]
root       114  0.0  0.0      0     0 ?        S<   10:58   0:00 [kseriod]
root       135  0.0  0.0      0     0 ?        S    10:58   0:00 [pdflush]
root       136  0.0  0.0      0     0 ?        S    10:58   0:00 [pdflush]
root       137  0.0  0.0      0     0 ?        S<   10:58   0:00 [kswapd0]
root       189  0.0  0.0      0     0 ?        S<   10:58   0:00 [aio/0]
root       190  0.0  0.0      0     0 ?        S<   10:58   0:00 [aio/1]
root      2018  0.0  0.0      0     0 ?        S<   10:59   0:00 [ata/0]
root      2019  0.0  0.0      0     0 ?        S<   10:59   0:00 [ata/1]
root      2020  0.0  0.0      0     0 ?        S<   10:59   0:00 [ata_aux]
root      2023  0.0  0.0      0     0 ?        S<   10:59   0:00 [ksuspend_usbd]
root      2024  0.0  0.0      0     0 ?        S<   10:59   0:00 [khubd]
root      2177  0.0  0.0      0     0 ?        S<   10:59   0:00 [scsi_eh_0]
root      2178  0.0  0.0      0     0 ?        S<   10:59   0:00 [scsi_eh_1]
root      2389  0.0  0.0      0     0 ?        S<   10:59   0:00 [kjournald]
root      2544  0.0  0.0   3028  1352 ?        S<s  10:59   0:00 /sbin/udevd --daemon
root      3451  0.0  0.0      0     0 ?        S<   10:59   0:00 [kedac]
root      3468  0.0  0.0      0     0 ?        S<   10:59   0:00 [kpsmoused]
root      4067  0.0  0.0   1696   520 tty4     Ss+  10:59   0:00 /sbin/getty 38400 tty4
root      4068  0.0  0.0   1692   516 tty5     Ss+  10:59   0:00 /sbin/getty 38400 tty5
root      4070  0.0  0.0   1696   520 tty2     Ss+  10:59   0:00 /sbin/getty 38400 tty2
root      4071  0.0  0.0   1696   520 tty3     Ss+  10:59   0:00 /sbin/getty 38400 tty3
root      4072  0.0  0.0   1696   516 tty1     Ss+  10:59   0:00 /sbin/getty 38400 tty1
root      4074  0.0  0.0   1696   520 tty6     Ss+  10:59   0:00 /sbin/getty 38400 tty6
root      4262  0.0  0.0   2436  1324 ?        Ss   10:59   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4312  0.0  0.0      0     0 ?        S<   10:59   0:00 [kondemand/0]
root      4313  0.0  0.0      0     0 ?        S<   10:59   0:00 [kondemand/1]
syslog    4394  0.0  0.0   1916   700 ?        Ss   10:59   0:00 /sbin/syslogd -a /var/lib/named/dev/log -u syslog
root      4449  0.0  0.0   1836   536 ?        S    10:59   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4451  0.0  0.0   2500  1408 ?        Ss   10:59   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4472  0.0  0.0   2908  1160 ?        Ss   10:59   0:00 /usr/bin/dbus-daemon --system
root      4488  0.0  0.0  13588  2056 ?        Ssl  10:59   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4502  0.0  0.0   3280  1292 ?        Ss   10:59   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4515  0.0  0.0   3084   812 ?        Ss   10:59   0:00 /usr/bin/system-tools-backends
root      4516  0.0  0.0   2772  1256 ?        S    10:59   0:00 dbus-daemon --session --print-address --nofork
107       4536  0.0  0.1   5828  4008 ?        Ss   10:59   0:00 /usr/sbin/hald
root      4537  0.0  0.0   3096  1028 ?        S    10:59   0:00 hald-runner
107       4579  0.0  0.0   2164   896 ?        S    10:59   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       4580  0.0  0.0   2164   896 ?        S    10:59   0:00 hald-addon-keyboard: listening on /dev/input/event4
107       4581  0.0  0.0   2160   892 ?        S    10:59   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       4584  0.0  0.0   2160   884 ?        S    10:59   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4609  0.0  0.0   3260  1228 ?        S    10:59   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
bind      4708  0.0  0.3  35108  7148 ?        Ssl  10:59   0:00 /usr/sbin/named -u bind -t /var/lib/named
root      4789  0.0  0.0   5280   968 ?        Ss   10:59   0:00 /usr/sbin/sshd
root      4865  0.0  0.1   5916  2516 ?        Ss   10:59   0:00 /usr/sbin/cupsd
root      4957  0.0  0.0   2824  1360 ?        S    10:59   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     4997  0.0  0.7 126916 16124 ?        Sl   10:59   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4998  0.0  0.0   1680   552 ?        S    10:59   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      5236  0.0  0.1   7500  2128 ?        Ssl  10:59   0:00 /usr/sbin/console-kit-daemon
avahi     5323  0.0  0.0   2732  1368 ?        Ss   10:59   0:00 avahi-daemon: running [server1.local]
avahi     5324  0.0  0.0   2732   456 ?        Ss   10:59   0:00 avahi-daemon: chroot helper
root      5338  0.0  0.0   1996   920 ?        Ss   10:59   0:00 /usr/sbin/dhcdbd --system
root      5360  0.0  0.0   2924  1184 ?        Ss   10:59   0:00 /usr/sbin/hcid -x -s
root      5372  0.0  0.0   2772   984 ?        S    10:59   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5373  0.0  0.0   2844  1216 ?        S    10:59   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5379  0.0  0.0      0     0 ?        S<   10:59   0:00 [krfcommd]
root      5414  0.0  0.0  13100  1600 ?        Ss   10:59   0:00 /usr/sbin/gdm
root      5415  0.0  0.1  13544  2892 ?        S    10:59   0:00 /usr/sbin/gdm
root      5421  0.3  1.2  31624 25664 tty7     Ss+  10:59   1:01 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daemon    5470  0.0  0.0   1964   432 ?        Ss   10:59   0:00 /usr/sbin/atd
root      5484  0.0  0.0   2336   908 ?        Ss   10:59   0:00 /usr/sbin/cron
phil      5615  0.0  0.0  13272  1844 ?        SL   10:59   0:00 /usr/bin/gnome-keyring-daemon -d
phil      5618  0.0  0.3  27688  7336 ?        Ssl  10:59   0:00 x-session-manager
phil      5657  0.0  0.0   4432   544 ?        Ss   10:59   0:00 /usr/bin/ssh-agent x-session-manager
phil      5659  0.0  0.1   6856  4124 ?        S    10:59   0:00 /usr/lib/libgconf2-4/gconfd-2 6
phil      5663  0.0  0.0   2900  1048 ?        Ss   10:59   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
phil      5665  0.0  0.4  38140  9868 ?        Sl   10:59   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
phil      5671  0.0  0.5  17932 10400 ?        S    10:59   0:06 /usr/bin/metacity --replace --sm-client-id default0
phil      5674  0.0  0.8  42372 16944 ?        S    10:59   0:02 gnome-panel --sm-client-id default1
phil      5676  0.0  0.8  62236 17800 ?        S    10:59   0:01 nautilus --no-default-window --sm-client-id default2
phil      5680  0.0  0.2  19464  5068 ?        Ss   10:59   0:00 gnome-volume-manager --sm-client-id default4
phil      5687  0.0  0.1  40972  3140 ?        Ssl  10:59   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
phil      5721  0.0  0.1   8736  3464 ?        S    10:59   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
phil      5728  0.0  0.3  19204  6788 ?        S    10:59   0:00 vino-session --sm-client-id default5
phil      5730  0.0  0.2  13288  5412 ?        S    10:59   0:00 bluetooth-applet
phil      5733  0.0  0.5  34192 11804 ?        S    10:59   0:00 update-notifier
phil      5739  0.0  0.4  26812  9364 ?        Sl   10:59   0:00 /usr/lib/evolution/2.12/evolution-alarm-notify
phil      5740  0.0  0.2  16560  4876 ?        Ss   10:59   0:01 gnome-screensaver
phil      5745  0.0  0.3  27840  7228 ?        SNl  10:59   0:00 trackerd
phil      5747  0.0  0.6  46288 14340 ?        S    10:59   0:00 nm-applet --sm-disable
phil      5749  0.0  0.5  22816 11728 ?        S    10:59   0:00 python /usr/share/system-config-printer/applet.py
phil      5752  0.0  0.3  22164  7684 ?        Ss   11:00   0:00 gnome-power-manager
phil      5767  0.0  0.4  65020  9008 ?        S    11:00   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=19
phil      5781  0.0  0.0   2660   892 ?        S    11:00   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
phil      5832  0.0  0.6  43984 12516 ?        Sl   11:00   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
dhcp      5916  0.0  0.0   2416  1192 ?        S    11:01   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
phil      5979  0.0  0.0   3844  1348 ?        S    11:01   0:00 /bin/sh /usr/bin/firefox
phil      5991  0.0  0.0   3884  1372 ?        S    11:01   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
phil      5996  0.3  2.6 169196 55456 ?        Sl   11:01   1:05 /usr/lib/firefox/firefox-bin
phil      6013  0.0  1.0  92484 22392 ?        Sl   11:01   0:04 gnome-terminal
phil      6016  0.0  0.0   2668   744 ?        S    11:01   0:00 gnome-pty-helper
phil      6017  0.0  0.1   5692  3088 pts/0    Ss   11:01   0:00 bash
root      6037  0.0  0.0   3888  1228 pts/0    S    11:02   0:00 su
root      6038  0.0  0.0   4172  1772 pts/0    S    11:02   0:00 bash
root      7363  0.0  0.0   6528   752 ?        Ss   11:41   0:00 /usr/sbin/saslauthd -a pam -n 5
root      7364  0.0  0.0   6528   492 ?        S    11:41   0:00 /usr/sbin/saslauthd -a pam -n 5
root      7365  0.0  0.0   6528   476 ?        S    11:41   0:00 /usr/sbin/saslauthd -a pam -n 5
root      7366  0.0  0.0   6528   476 ?        S    11:41   0:00 /usr/sbin/saslauthd -a pam -n 5
root      7367  0.0  0.0   6528   476 ?        S    11:41   0:00 /usr/sbin/saslauthd -a pam -n 5
root      7414  0.0  0.0   7456   752 ?        Ss   11:45   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      7415  0.0  0.0   7456   480 ?        S    11:45   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      7416  0.0  0.0   7456   364 ?        S    11:45   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      7417  0.0  0.0   7456   364 ?        S    11:45   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      7418  0.0  0.0   7456   364 ?        S    11:45   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      7513  0.0  0.0   5328  1688 ?        Ss   11:50   0:00 /usr/lib/postfix/master
postfix   7518  0.0  0.0   5368  1636 ?        S    11:50   0:00 qmgr -l -t fifo -u
postfix   7556  0.0  0.0   5336  1608 ?        S    15:10   0:00 pickup -l -t fifo -u -c
root      7596  0.0  0.0   2624  1004 pts/0    R+   16:22   0:00 ps aux


---

### Post by MJN on 2008-01-21
Hmm... all looks fine.

Have you tried restarting Postfix? (**sudo /etc/init.d/postfix restart**)

Anything in the logs? (**tail /var/log/mail.log**)

Mathew

---

### Post by dethredic on 2008-01-21
Nothing that I can see

> 
root@server1:/etc/postfix/ssl# sudo /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
root@server1:/etc/postfix/ssl# telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection timed out
root@server1:/etc/postfix/ssl# tail /var/log/mail.log
Jan 21 11:03:00 server1 postfix/master[6381]: daemon started -- version 2.4.5, configuration /etc/postfix
Jan 21 11:03:16 server1 postfix/master[6381]: terminating on signal 15
Jan 21 11:04:45 server1 postfix/master[6775]: daemon started -- version 2.4.5, configuration /etc/postfix
Jan 21 11:38:44 server1 postfix/master[6775]: terminating on signal 15
Jan 21 11:38:44 server1 postfix/master[7306]: daemon started -- version 2.4.5, configuration /etc/postfix
Jan 21 11:50:22 server1 postfix/master[7306]: terminating on signal 15
Jan 21 11:50:22 server1 postfix/master[7513]: daemon started -- version 2.4.5, configuration /etc/postfix
Jan 21 17:20:14 server1 postfix/master[7513]: terminating on signal 15
Jan 21 17:20:15 server1 postfix/master[7727]: daemon started -- version 2.4.5, configuration /etc/postfix
root@server1:/etc/postfix/ssl# 



---

### Post by MJN on 2008-01-21
I really don't know. Maybe I'm/we're missing something obvious so maybe a fresh pair of eyes are what's needed.

It might be worth posting your config (main.cf) in case anything jumps out.

Edit: Post your master.cf file too.

Mathew

---

### Post by dethredic on 2008-01-21
main.cf

> 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server1.HatchSEADGroup.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server1.HatchSEADGroup.com, localhost.HatchSEADGroup.com, localhost.localdomain.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


master.cf
> 
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_enforce_tls=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache	  unix	-	-	-	-	1	scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}






EDIT:
The telnet localhost 25 does not work on my other computer either. Don't know if this is important or not. I will try forwarding port 25 in my router.

---

### Post by MJN on 2008-01-21
Man, you really have got me now.

I take it you cannot connect from another machine (unlikely I know but I'm willing grab any straw I can).

Is this machine accessible from the Internet? I'm wondering if a remote test might turn anything up (i.e. running packet trace to see if there is any response at the lower level(s))

Mathew

---

### Post by dethredic on 2008-01-21
> I take it you cannot connect from another machine (unlikely I know but I'm willing grab any straw I can).

Not sure what you mean. Both my computer can connect to the internet, but both get the connection timed out when doing telnet localhost 25.

I do know that no one can ping me. My and my friend found that out a while ago, I will try and find the trace we did. (I was on windows at the time)

**UPDATE:**

Ok, we were trying to get UltraVNC to work, but we couldn't but I still think it might be relevant. 

We both had all our firewalls turned off, and were plugged directly into our modems. He could connect to me, but I couldn't connect to him.

I could ping my friend perfectly, with no errors, but when he pinged me he got a bunch of requests timed out.

My friend ran a tracert on me. Here are the results.

> 
C:\Documents and Settings\Dandymcgee>tracert 24.57.211.254

Tracing route to d57-211-254.home.cgocable.net [24.57.211.254]
over a maximum of 30 hops:

1     5 ms     1 ms    <1 ms  192.168.2.1
2     6 ms     1 ms     1 ms  192.168.1.1
3    36 ms    35 ms    35 ms  10.20.10.1
4    34 ms    33 ms    33 ms  P0-1.LCR-01.CNCDNH.verizon-gni.net [130.81.35.230]
5    60 ms    44 ms    43 ms  so-7-0-0-0.PEER-RTR1.NY111.verizon-gni.net [130.81.17.131]
6    47 ms    45 ms    46 ms  130.81.15.138
7    52 ms    51 ms    49 ms  p5-0.core01.bos01.atlas.cogentco.com [66.28.4.117]
8    53 ms    55 ms    55 ms  p13-0.core01.alb02.atlas.cogentco.com [154.54.7.41]
9    69 ms    69 ms    68 ms  p14-0.core01.yyz01.atlas.cogentco.com [66.28.4.218]
10   238 ms   113 ms   209 ms  v3491.mpd01.yyz01.atlas.cogentco.com [154.54.5.78]
11    68 ms    68 ms    68 ms  v3493.mpd01.yyz02.atlas.cogentco.com [154.54.5.86]
12    69 ms    71 ms    68 ms  cogeco-cable-canada.demarc.cogentco.com [38.99.220.154]
13    73 ms    71 ms    72 ms  cgowave-0-114.cgocable.net [24.226.0.114]
14    72 ms    73 ms    74 ms  d226-8-198.home.cgocable.net [24.226.8.198]
15     *        *        *     Request timed out.
16     *        *        *     Request timed out.
17     *        *        *     Request timed out.
18     *        *        *     Request timed out.
19     *        *        *     Request timed out.
20     *        *        *     Request timed out.
21     *        *        *     Request timed out.
22     *        *        *     Request timed out.
23     *        *        *     Request timed out.
24     *        *        *     Request timed out.
25     *        *        *     Request timed out.
26     *        *        *     Request timed out.
27     *        *        *     Request timed out.
28     *        *        *     Request timed out.
29     *        *        *     Request timed out.
30     *        *        *     Request timed out.


Here are the results when I ran a tracert on him

> C:\Documents and Settings\Philip>tracert 72.64.9.67
Tracing route to pool-72-64-9-67.cncdnh.east.verizon.net [72.64.9.67]
over a maximum of 30 hops:

  1     1 ms    <1 ms    <1 ms  192.168.1.1
  2    10 ms     8 ms     8 ms  10.67.176.1
  3     8 ms    15 ms     9 ms  d226-9-129.home.cgocable.net [24.226.9.129]
  4    10 ms     9 ms    11 ms  cgowave-0-105.cgocable.net [24.226.0.105]
  5    45 ms    12 ms     *     g8-11.mpd01.yyz02.atlas.cogentco.com [38.99.220.153]
  6     9 ms     9 ms     9 ms  v3493.mpd01.yyz01.atlas.cogentco.com [154.54.5.85]
  7    25 ms    24 ms    26 ms  t7-4.mpd01.ord01.atlas.cogentco.com [154.54.7.73]
  8    25 ms    25 ms    25 ms  v3489.mpd01.ord03.atlas.cogentco.com [154.54.5.18]
  9    24 ms    23 ms    21 ms  g15-0-0-3493.core01.ord03.atlas.cogentco.com [154.54.3.245]
10    24 ms    23 ms    25 ms  so-0-1-0-0.PEER-RTR1.CHI80.verizon-gni.net [130.81.15.85]
11    26 ms    25 ms    23 ms  so-7-0-0-0.BB-RTR2.CHI01.verizon-gni.net [130.81.16.78]
12    44 ms    43 ms    42 ms  so-6-0-0-0.BB-RTR1.BOS.verizon-gni.net [130.81.19.64]
13    42 ms    44 ms    43 ms  so-0-0-0-0.BB-RTR2.BOS.verizon-gni.net [130.81.19.73]
14    45 ms    44 ms    46 ms  P14-0.LCR-01.CNCDNH.verizon-gni.net [130.81.28.77]
15    46 ms    49 ms    45 ms  P9-0.MNCHNHCO-ERXG01.CNCDNH.verizon-gni.net [130.81.35.231]
16    88 ms    78 ms    79 ms  pool-72-64-9-67.cncdnh.east.verizon.net [72.64.9.67]

Trace complete.


Ohh, this might be the problem. Some guy told us to check to see if my IP blocked any ports. I checked and...

Cogeco (my ISP) blocks: 25/tcp, 135/tcp, 137/tcp, 139/tcp, 445/tcp, 1433/udp.

Now UltraVNC was port 5900, so that didn't help, but could that 25/tcp be the problem in this senario???


That is all the info I had on that saga, and we never found a resolution. Maybe some of this info helps.

---

### Post by MJN on 2008-01-22
Well, if your ISP blocks incoming port 25 (you'd have to check whether it's incoming, outgoing, or both) then you're not going to have much joy running a mail server without a few tricks.

However, you cannot even connect to localhost from your own machine hence your ISP has nothing to do with this particular problem.

You mentioned you have two computers - presumably connected on a LAN? You also stated that neither could do telnet localhost 25 - however the second machine should not be trying to connect to localhost as that is itself - you should be trying telnet <ip of server> 25 (where the IP is the internal, private, address as opposed to your WAN address as there's no point including your router as another possible hurdle).

I'm out of ideas I'm afraid.

Mathew

---

### Post by dethredic on 2008-01-22
Ok, i tried replacing localhost with my internal ip (192.168.1.xxx) on both my computers and both failed.

I can ping localhost.

Do I even need this postfix for a basic file server anyways?

---

### Post by MJN on 2008-01-22
I'm afraid I don't know what the problem is. Someone else will have to step in, although if your ISP blocks incoming port 25 then the outlook is not looking great anyway.
 
> Do I even need this postfix for a basic file server anyways?
 
No, not at all. Postfix is a mail server and hence used only for sending/receiving mail.
 
Mathew

---

### Post by dethredic on 2008-01-22
Thanks a lot for your effort.

I guess I will just skip the mail part of it then.


EDIT: I can't even telnet localhost 21 or telnet localhost 23  :S

---

### Post by crouton on 2008-01-22
It vaguely sounds like 'localhost' isn't 127.0.0.1.  So try 'telnet 127.0.0.1 25' if you still have Postfix running, or 'telnet 127.0.0.1 22' if you have SSHD running.

---

### Post by MJN on 2008-01-22
I initially thought that but post #7 shows the mapping was done correctly to 127.0.0.1. And, firewalls notwithstanding, a connection from a LAN machine should have worked given an IP address was used.

I'm completely stumped... not that that necessarily means anything!

Mathew

---

### Post by dethredic on 2008-01-22
It is ok, I don't need postfix anyways.

I have tried 127.0.0.1 instead of local host, but that did nothing.

---

### Post by koenn on 2008-01-22
OK, so you can live without postfix, but in light of 
> **MJN said:**
> I initially thought that but post #7 shows the mapping was done correctly to 127.0.0.1. ... 
I'm completely stumped... 
I was wondering ...
one can very well have 127.0.0.1 mapped to localhost (in /etc/hosts), but that doesn't necessarily mean thear actually is a loopback ("local host") interface configured. 

dethredic, could you run the following, just to check : 
```
grep "lo" /etc/network/interfaces
ifconfig lo
```

---

### Post by dethredic on 2008-01-22
> **koenn said:**
> OK, so you can live without postfix, but in light of 

I was wondering ...
one can very well have 127.0.0.1 mapped to localhost (in /etc/hosts), but that doesn't necessarily mean thear actually is a loopback ("local host") interface configured. 

dethredic, could you run the following, just to check : 
```
grep "lo" /etc/network/interfaces
ifconfig lo
```

here you go

> 
root@server1:/home/phil# grep "lo" /etc/network/interfaces
# # The loopback network interface
# auto lo
# iface lo inet loopback
root@server1:/home/phil# ifconfig lo
lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@server1:/home/phil# 



---

### Post by koenn on 2008-01-22
yep, your loopback interface is commented out (i.e. disabled) in "interfaces" and thus doesn't show an IP address in ifconfig.

if you change the loopback part of /etc/network/interfaces  (remove the # ) to
```
auto lo
iface lo inet loopback
```
and do
```
ifconfig lo up
```
or
```
ifup lo
```
(or reboot if all else fails) then you should be able to get
```
n@knix:~$ ifconfig lo
lo        Link encap:Local Loopback
          **inet addr:127.0.0.1**  Mask:255.0.0.0
```
and you should be able to telnet services listening on localhost / 127.0.0.1
-- unless there is a very good reason that this server needs to have loopback disabled (can't think of any), I think it's better to have lo on.

---

### Post by dethredic on 2008-01-22
Wow, man you are a genius!!! 

That just made my apache work!!!!!

Thanks a lot.

EDIT: postfix will probably now work, but I don't need it so ya..

---

### Post by MJN on 2008-01-22
Genius indeed - excellent!

Any thoughts how this might have happened? (and why?)

Dethredic, do check your Postfix if only so we can sleep soundly!!

Koenn, do you know why this would stop a remote client connecting?

Mathew

---

### Post by dethredic on 2008-01-22
well, postfix still does not work, but now I get a connection refused.

---

### Post by koenn on 2008-01-22
> **MJN said:**
> Genius indeed - excellent!

Linux' Law : "given enough eyeballs, all bugs are shallow" - it was actually  your comments that made me think of checking the lo interface. 

> **MJN said:**
> 
Any thoughts how this might have happened? (and why?)

None. I suppose someone actually has had to put these #'s there ...

> **MJN said:**
> 
Koenn, do you know why this would stop a remote client connecting?

Not really. I don't know if lo does anything else than being 'localhost' but my first guess would be those are separate probblems.

---

### Post by dethredic on 2008-01-22
well, the instructions accually told me to remove the ##, I just didn't cause it said make your /etc/network/interfaces look like this:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1


I just must have missed those cause I was too worried about the lower part.

How can I fix the connection refused?

---

### Post by koenn on 2008-01-22
> **dethredic said:**
> 
How can I fix the connection refused?
Could be (yet another) network problem, or a postfix config problem. 
It's past my bed time and i don't know anything about postfix, so I'm out.

---

### Post by dethredic on 2008-01-22
I will go through the postfix instructions, as there could be a chance that something didn't configure properly because I didn't have the proper setup before.

---

### Post by dissdigg on 2008-04-11
Thanks so much for this - I had the same problem.  

New server 7.10 install, I'm not sure what howto for what, but for some reason I had the same "auto lo..." line commented out in /etc/network/interfaces.

I had my firewall completely disabled, could connect to any listening port from another system (over ethernet), but could not connect to any of the listening ports on the system itself!  Even when trying to connect to the IPs listening on the ethernet interfaces I was having this problem.

Uncommenting and ifup'ing lo fixed everything.  Thanks!!

---

