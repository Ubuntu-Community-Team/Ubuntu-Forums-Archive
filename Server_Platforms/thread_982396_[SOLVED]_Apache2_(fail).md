---
title: "[SOLVED] Apache2 (fail)"
date: 2008-11-14
forum: Server Platforms
---

### Post by quikone8 on 2008-11-14
Hi I am trying to run Apache 2 along side a Citadel Server, when I try to start Apache by; sudo /etc/init.d/apache2 start I get the following;

*starting web server apache2
apache2:  Could not reliably determine the server's fully qualified name, using 127.0.1.1 for ServerName
(98) Address already in use:  make_sock: could not bind to address 0.0.0.0:80 no listening sockets available, shutting down
Unable to open logs 

                                                               [[COLOR="Red"]fail[COLOR="Black"]][/COLOR][/COLOR]

Should read 98 address already in use

---

### Post by CrucifiedEgo on 2008-11-14
are you sure apache isn't already running?  Looks like something's listening on port 80 already.   try ps aux | grep apache and see if anything is running.  if so, try to stop it with /etc/init.d/apache2 stop

---

### Post by Philio on 2008-11-14
If Apache is running the init script detects it...

> # /etc/init.d/apache2 start
 * Starting web server apache2                                                  httpd (pid 4290) already running
                                                                         [ OK ]

It seams more likely that something else is running on port 80 other than Apache, check your configs.

To show what is listening on which ports use: netstat -nlp

---

### Post by quikone8 on 2008-11-14
> **CrucifiedEgo said:**
> are you sure apache isn't already running?  Looks like something's listening on port 80 already.   try ps aux | grep apache and see if anything is running.  if so, try to stop it with /etc/init.d/apache2 stop

Looks as if it was running; followed your suggestion to stop the service;

*Stopping web server apache2
apache2: Could not reliabluy determine the server's fully qualified name, using 127.0.1.1 for ServerName
httpd (no pid file) not running

[OK]

---

### Post by quikone8 on 2008-11-14
> **Philio said:**
> If Apache is running the init script detects it...



It seams more likely that something else is running on port 80 other than Apache, check your configs.

To show what is listening on which ports use: netstat -nlp

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:2020            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:5222            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:504             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
udp        0      0 192.168.1.252:137       0.0.0.0:*                           -               
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -               
udp        0      0 192.168.1.252:138       0.0.0.0:*                           -               
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:41149           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     13243    -                   /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     13938    -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     14320    6003/gconfd-2       /tmp/orbit-ron/linc-1773-0-134e9d6aa93a1
unix  2      [ ACC ]     STREAM     LISTENING     14330    6005/gnome-keyring- /tmp/orbit-ron/linc-1771-0-61321e0ab3a72
unix  2      [ ACC ]     STREAM     LISTENING     14520    6005/gnome-keyring- /tmp/keyring-5oa8Qn/socket
unix  2      [ ACC ]     STREAM     LISTENING     14522    6005/gnome-keyring- /tmp/keyring-5oa8Qn/ssh
unix  2      [ ACC ]     STREAM     LISTENING     14524    6005/gnome-keyring- /tmp/keyring-5oa8Qn/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     14697    6066/seahorse-agent /tmp/orbit-ron/linc-1776-0-5149fc92c6a62
unix  2      [ ACC ]     STREAM     LISTENING     14728    6006/x-session-mana /tmp/seahorse-Tj55TP/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     14766    6006/x-session-mana /tmp/orbit-ron/linc-1776-0-4bbf4697907
unix  2      [ ACC ]     STREAM     LISTENING     14770    6006/x-session-mana /tmp/.ICE-unix/6006
unix  2      [ ACC ]     STREAM     LISTENING     14826    6071/gnome-settings /tmp/orbit-ron/linc-17b7-0-f90f9eb1d504
unix  2      [ ACC ]     STREAM     LISTENING     14954    -                   /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     12832    -                   /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     14958    -                   /tmp/pulse-ron/native
unix  2      [ ACC ]     STREAM     LISTENING     14984    6080/gconf-helper   /tmp/orbit-ron/linc-17c0-0-7b85a9a8a5a0a
unix  2      [ ACC ]     STREAM     LISTENING     15138    6093/gnome-screensa /tmp/orbit-ron/linc-17c8-0-65c831a73972c
unix  2      [ ACC ]     STREAM     LISTENING     15303    -                   /tmp/orbit-ron/linc-17cf-0-74c4a5d55d062
unix  2      [ ACC ]     STREAM     LISTENING     15366    6097/nautilus       /tmp/orbit-ron/linc-17d1-0-74c4a5d56c5d2
unix  2      [ ACC ]     STREAM     LISTENING     15577    6166/bluetooth-appl /tmp/orbit-ron/linc-1816-0-28d859c1c037e
unix  2      [ ACC ]     STREAM     LISTENING     16030    6106/bonobo-activat /tmp/orbit-ron/linc-17da-0-129ff5e81e331
unix  2      [ ACC ]     STREAM     LISTENING     16045    6169/update-notifie /tmp/orbit-ron/linc-1819-0-74c4a5d622ab4
unix  2      [ ACC ]     STREAM     LISTENING     16050    6186/gnome-power-ma /tmp/orbit-ron/linc-1821-0-74c4a5d623ce2
unix  2      [ ACC ]     STREAM     LISTENING     16076    6187/gnome-volume-m /tmp/orbit-ron/linc-1825-0-62c7f77c33a83
unix  2      [ ACC ]     STREAM     LISTENING     16085    6094/metacity       /tmp/orbit-ron/linc-17ce-0-769838703611c
unix  2      [ ACC ]     STREAM     LISTENING     16135    6173/evolution-alar /tmp/orbit-ron/linc-181d-0-62c7f77c95687
unix  2      [ ACC ]     STREAM     LISTENING     16201    6195/trashapplet    /tmp/orbit-ron/linc-1833-0-50b293712faf0
unix  2      [ ACC ]     STREAM     LISTENING     16267    6182/nm-applet      /tmp/orbit-ron/linc-1826-0-303a070c5c613
unix  2      [ ACC ]     STREAM     LISTENING     16576    6222/mixer_applet2  /tmp/orbit-ron/linc-184e-0-50b29371df8a2
unix  2      [ ACC ]     STREAM     LISTENING     16594    6225/fast-user-swit /tmp/orbit-ron/linc-1851-0-ebaff1fb212
unix  2      [ ACC ]     STREAM     LISTENING     17097    6269/firefox        /tmp/orbit-ron/linc-187d-0-484277ece5bc4
unix  2      [ ACC ]     STREAM     LISTENING     18010    6883/gnome-terminal /tmp/orbit-ron/linc-1ae3-0-597300c139b2b
unix  2      [ ACC ]     STREAM     LISTENING     13128    -                   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     13900    -                   /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     13783    -                   @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     13280    -                   @/var/run/hald/dbus-2Vg1QHqUQi
unix  2      [ ACC ]     STREAM     LISTENING     12923    -                   /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     13296    -                   @/var/run/hald/dbus-gpAGdhX9ZG
unix  2      [ ACC ]     STREAM     LISTENING     12706    -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     13733    -                   /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     14784    6070/dbus-daemon    @/tmp/dbus-BcbJ7vHhO2
unix  2      [ ACC ]     STREAM     LISTENING     12474    -                   /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     13245    -                   /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     14062    -                   /usr/local/citadel/citadel.socket
unix  2      [ ACC ]     STREAM     LISTENING     14075    -                   /usr/local/citadel/lmtp.socket
unix  2      [ ACC ]     STREAM     LISTENING     14077    -                   /usr/local/citadel/lmtp-unfiltered.socket
unix  2      [ ACC ]     STREAM     LISTENING     13735    -                   @/var/run/dbus-RaCDsoc02g

---

### Post by Philio on 2008-11-14
Weird that should tell you the program names, but if Apache was already running then sounds like you've solved the problem anyway!

Which version of Ubuntu are you using, is strange the init script didn't notice Apache was running!

Also that netstat command should output something like this:

> tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4290/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      6145/vsftpd
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      6131/unbound
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      5085/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      5877/exim4
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      4290/apache2


As you can see on this server apache2 is running on 80 and 443.

---

### Post by quikone8 on 2008-11-14
Well that solved it, 

Thanks everyone

---

