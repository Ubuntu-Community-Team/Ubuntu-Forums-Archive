---
title: "back orifice infected my computer??!"
date: 2006-05-01
forum: Server Platforms
---

### Post by Nikusan on 2006-05-01
please refer to my post here: [http://ubuntuforums.org/showthread.php?t=168728](http://ubuntuforums.org/showthread.php?t=168728)
The UDP traffic keeps going. I saw in the active connections list something with the service back orifice. Please somebody help me remove this. There is nothing sus looking is my ps list.

---

### Post by az on 2006-05-01
[QUOTE=Nikusan]please refer to my post here: [http://ubuntuforums.org/showthread.php?t=168728](http://ubuntuforums.org/showthread.php?t=168728)
The UDP traffic keeps going. I saw in the active connections list something with the service back orifice. Please somebody help me remove this. There is nothing sus looking is my ps list.[/QUOTE]
bittorrent?

---

### Post by Nikusan on 2006-05-01
[QUOTE=azz]bittorrent?[/QUOTE]

I dont know... I don't think so. I definately saw back orifice in the active connection list. :'(

---

### Post by Nikusan on 2006-05-01
[QUOTE=Nikusan]I dont know... I don't think so. I definately saw back orifice in the active connection list. :'([/QUOTE]

```
dan@problemchild:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  160 ?        00:00:00 pdflush
  161 ?        00:00:00 pdflush
  163 ?        00:00:00 aio/0
  162 ?        00:00:00 kswapd0
  750 ?        00:00:00 kseriod
 1742 ?        00:00:00 ata/0
 1745 ?        00:00:00 scsi_eh_0
 1746 ?        00:00:00 scsi_eh_1
 1910 ?        00:00:00 khubd
 2000 ?        00:00:00 kjournald
 2228 ?        00:00:00 udevd
 3042 ?        00:00:00 shpchpd_event
 3098 ?        00:00:00 khpsbpkt
 3104 ?        00:00:00 knodemgrd_0
 3656 ?        00:00:00 kjournald
 4003 ?        00:00:00 acpid
 4093 ?        00:00:00 syslogd
 4119 ?        00:00:00 dd
 4121 ?        00:00:00 klogd
 4440 ?        00:00:00 gdm
 4452 ?        00:00:00 gdm
 4457 tty7     00:24:54 Xorg
 4479 ?        00:00:00 hpiod
 4494 ?        00:00:00 python
 4537 ?        00:00:01 cupsd
 4560 ?        00:00:00 dbus-daemon
 4575 ?        00:00:01 hald
 4576 ?        00:00:00 hald-runner
 4581 ?        00:00:00 hald-addon-acpi
 4632 ?        00:00:00 hald-addon-keyb
 4643 ?        00:00:00 hald-addon-stor
 4644 ?        00:00:00 hald-addon-stor
 4646 ?        00:00:01 hald-addon-stor
 4647 ?        00:00:01 hald-addon-stor
 4957 ?        00:00:00 hddtemp
 5815 ?        00:00:00 nmbd
 5817 ?        00:00:00 smbd
 5824 ?        00:00:00 sensord
 5877 ?        00:00:00 ntpd
 5893 ?        00:00:00 smbd
 5894 ?        00:00:00 hcid
 5898 ?        00:00:00 sdpd
 5912 ?        00:00:00 krfcommd
 5926 ?        00:00:00 mdadm
 5966 ?        00:00:00 atd
 5979 ?        00:00:00 cron
 6067 tty1     00:00:00 getty
 6068 tty2     00:00:00 getty
 6069 tty3     00:00:00 getty
 6070 tty4     00:00:00 getty
 6071 tty5     00:00:00 getty
 6072 tty6     00:00:00 getty
 6092 ?        00:00:00 dhclient3
 6102 ?        00:00:00 x-session-manag
 6144 ?        00:00:00 ssh-agent
 6147 ?        00:00:00 dbus-launch
 6148 ?        00:00:00 dbus-daemon
 6150 ?        00:00:01 gconfd-2
 6153 ?        00:00:00 gnome-keyring-d
 6155 ?        00:00:00 bonobo-activati
 6157 ?        00:00:04 gnome-settings-
 6162 ?        00:00:00 esd
 6166 ?        00:00:37 metacity
 6177 ?        00:00:06 gnome-panel
 6179 ?        00:00:15 nautilus
 6182 ?        00:00:00 gnome-volume-ma
 6188 ?        00:00:01 update-notifier
 6190 ?        00:00:02 mono
 6195 ?        00:00:06 beagled
 6200 ?        00:00:01 gnome-cups-icon
 6203 ?        00:00:00 gnome-vfs-daemo
 6211 ?        00:00:19 wnck-applet
 6212 ?        00:00:00 gnome-power-man
 6217 ?        00:00:01 trashapplet
 6219 ?        00:00:03 deskbar-applet
 6250 ?        00:00:00 mapping-daemon
 6261 ?        00:00:00 evolution-data-
 6269 ?        00:00:01 gweather-applet
 6271 ?        00:00:02 clock-applet
 6273 ?        00:01:38 multiload-apple
 6275 ?        00:00:10 sensors-applet
 6277 ?        00:00:00 notification-ar
 6279 ?        00:00:01 mixer_applet2
 6291 ?        00:00:05 gnome-screensav
 6327 ?        00:42:11 firestarter
 6329 ?        00:00:00 gconfd-2
 6333 ?        00:00:00 esd
 6612 ?        00:00:01 beagled-helper
 6885 ?        00:00:00 evolution-alarm
 7274 ?        00:03:55 firefox-bin
 8161 ?        00:00:00 bonobo-activati
 8163 ?        00:00:00 gnome-vfs-daemo
14140 ?        00:00:01 gaim
14443 ?        00:00:00 snort
14960 ?        00:00:00 gam_server
15027 ?        00:00:00 gnome-terminal
15028 ?        00:00:00 gnome-pty-helpe
15029 pts/0    00:00:00 bash
15049 pts/0    00:00:00 ps

```

---

### Post by Nikusan on 2006-05-01
I found these links: [http://www.derkeiler.com/Newsgroups/comp.os.linux.security/2005-09/0292.html](http://www.derkeiler.com/Newsgroups/comp.os.linux.security/2005-09/0292.html)
[http://www.derkeiler.com/Newsgroups/comp.os.linux.security/2005-09/0248.html](http://www.derkeiler.com/Newsgroups/comp.os.linux.security/2005-09/0248.html)

Maybe you are right azz? I sure hope so. I am scanning everything with AVG right now, I'll post again when it's done. Any more advice?

---

### Post by LordHunter317 on 2006-05-01
Back orifice can't be it, as it doesn't exist for Linux.  I don't even know how you got that idea.

It can't be bittorrent as it doesn't use UDP.  What we need is the output of 'netstat -an'.

---

### Post by Nikusan on 2006-05-01
[QUOTE=LordHunter317]Back orifice can't be it, as it doesn't exist for Linux.  I don't even know how you got that idea.

It can't be bittorrent as it doesn't use UDP.  What we need is the output of 'netstat -an'.[/QUOTE]

I got the idea from the service column in the active connections in firestarter. It showed back orifice. But from what I've read I guess that was just a guess that firestarter made based on the port? It might have been bittorrent. I'll post netstat when I get home tonight. Thanks.

---

### Post by LordHunter317 on 2006-05-01
[QUOTE=Nikusan]I got the idea from the service column in the active connections in firestarter. It showed back orifice.[/quote]Yes, but that's because that is the name for the port in the service file, that doesn't mean back orifice was actually running.  For example, /etc/services says port 80 is www, but if I run my SSH server on there, I'm obviously not using it for that.  But the firewall doesn't know that, it just looks up what the file says.

> But from what I've read I guess that was just a guess that firestarter made based on the port?It read /etc/services, but essentially, yes.

>  It might have been bittorrent. I'll post netstat when I get home tonight. Thanks.It was most likely an outgoing connection of sorts.

---

### Post by Nikusan on 2006-05-02
netstat -an

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:52836         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:34537         0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 10.1.1.4:41987          66.102.7.147:80         TIME_WAIT
tcp        0      0 10.1.1.4:41988          66.102.7.147:80         TIME_WAIT
tcp        0      0 10.1.1.4:38433          130.95.3.26:80          ESTABLISHED
tcp        0      0 10.1.1.4:56289          65.54.239.81:80         TIME_WAIT
tcp        0      0 127.0.0.1:52836         127.0.0.1:39388         ESTABLISHED
tcp        0      0 127.0.0.1:7634          127.0.0.1:48553         TIME_WAIT
tcp        0      0 127.0.0.1:39388         127.0.0.1:52836         ESTABLISHED
udp        0      0 10.1.1.4:137            0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 10.1.1.4:138            0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 10.1.1.4:123            0.0.0.0:*
udp        0      0 127.0.0.1:123           0.0.0.0:*
udp        0      0 0.0.0.0:123             0.0.0.0:*
udp6       0      0 :::123                  :::*
Active UNIX domain sockets (servers and established)
*snip*

```

The situation now is about 1 or 2 connection attempts a minute. No more udp, it's all tcp. much lowers ports now, 1025 and 1043 seem popular. The services are showing as unkown and ms-sql-s.

---

### Post by LordHunter317 on 2006-05-02
You either have been compromised, or they're not actually attacking you (DOS gone astray?).  

Anyway, I would do this:[list][*]Shut the box down and pull it from the Internet[*]Boot off a rescue CD.[*]Run rkhunter and chkrootkit on the machine and see what it shows.[/list]

Beforehand though, please post 'netstat -pln --inet' and 'lsof -i'.

---

