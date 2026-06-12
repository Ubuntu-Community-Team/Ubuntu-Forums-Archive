---
title: "[n00b] something is accessing my files"
date: 2006-04-03
forum: Server Platforms
---

### Post by tsr on 2006-04-03
Hi,

For some time now my machine has been a bit slow but it's slowiness reached a peak yesterday.

Assuming something was wrong I started to look around for signs of intrusion, etc.

I'm a real noob at this things but I found out that something is accesing many of my files frequently (by looking at the accessed column in nautilius :) )

I think I've managed to set up firestarter to only allow connections for me to access the internet on port 80 and to fetch my mail, but I'm not sure.

I have two questions:
1. Should I worry about the file-accessing? And if so what should I do about it? 
2. How do I set up firestarter to allow me to: surf the web (HTTP/S), use mail (POP3, IMAP, SMTP), transfer files (FTP, BitTorrent with Azureus). (I had a functioning apache2 install but I ony need it for local testing, apparently it has stopped working, not a big problem, I'll just purge and reinstall it)

Any help (in a ok-so-you-are-completely-ignorant-but-know-how-to-edit-files-at-least kind of way) is very appreciated.

/Tomas

---

### Post by colo on 2006-04-03
If something actually compromised your system (a thing I _highly_ doubt, to be honest), a properly set up packet filter probably won't save you, anyway.

Monitor the output of
```
netstat -nlp
```
for suspicious activities on listening sockets,
```
top
```
for unusual amounts of CPU-activity caused by unfamiliar processes,
get yourself **chrootkit** and run it,
check for open files you consider not necessarily to be opened by anything with **lsof**.

If you happen to have any questions to the points I mentioned, check back here with some more info on your possibly rooted box. ;)

---

### Post by tsr on 2006-04-03
Ok, thanks. (I too think it's probably not anything, but I wouldn't know!)

The thing that confuses me the most is that apparently all directories have been accessed by some process, but I don't understand why, maybe it's some standard checking that I'm not aware of, but I can't remember that to be the case before)

Ok, now over to your provided diagnostics tools:
```

netstat -nlp

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
udp        0      0 0.0.0.0:68              0.0.0.0:*                          9287/dhclient3
udp        0      0 0.0.0.0:68              0.0.0.0:*                          9246/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     9722     8302/gdm            /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     9070     8225/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     9917     8342/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18612    9003/firefox-bin    /tmp/orbit-tsr/linc-232b-0-4f45286adc50a
unix  2      [ ACC ]     STREAM     LISTENING     17554    8898/metacity       /tmp/orbit-tsr/linc-22c2-0-4b0e5b0cb18e8
unix  2      [ ACC ]     STREAM     LISTENING     10658    8811/ssh-agent      /tmp/ssh-galbhH8773/agent.8773
unix  2      [ ACC ]     STREAM     LISTENING     10682    8817/gconfd-2       /tmp/orbit-tsr/linc-2271-0-71e7fb78d6ac4
unix  2      [ ACC ]     STREAM     LISTENING     10692    8773/x-session-mana /tmp/orbit-tsr/linc-2245-0-79466942e998
unix  2      [ ACC ]     STREAM     LISTENING     11121    8773/x-session-mana /tmp/.ICE-unix/8773
unix  2      [ ACC ]     STREAM     LISTENING     11130    8847/gnome-keyring- /tmp/keyring-2RuMxh/socket
unix  2      [ ACC ]     STREAM     LISTENING     14794    8851/bonobo-activat /tmp/orbit-tsr/linc-2293-0-2c57aef889154
unix  2      [ ACC ]     STREAM     LISTENING     14815    8853/gnome-settings /tmp/orbit-tsr/linc-2295-0-4bdaf932cd327
unix  2      [ ACC ]     STREAM     LISTENING     17579    8902/gnome-volume-m /tmp/orbit-tsr/linc-22c6-0-1f40bd65a9123
unix  2      [ ACC ]     STREAM     LISTENING     17597    8900/gnome-panel    /tmp/orbit-tsr/linc-22c4-0-4d32a47fa55f
unix  2      [ ACC ]     STREAM     LISTENING     17624    8904/nautilus       /tmp/orbit-tsr/linc-22c8-0-329972528a751
unix  2      [ ACC ]     STREAM     LISTENING     17654    8906/update-notifie /tmp/orbit-tsr/linc-22ca-0-329972537dc46
unix  2      [ ACC ]     STREAM     LISTENING     30027    9142/evolution      /tmp/orbit-tsr/linc-23b6-0-46a1853e8b0e3
unix  2      [ ACC ]     STREAM     LISTENING     17743    8918/wnck-applet    /tmp/orbit-tsr/linc-22d6-0-412038819118
unix  2      [ ACC ]     STREAM     LISTENING     17751    8914/mail-notificat /tmp/orbit-tsr/linc-22d2-0-568d4ef7274da
unix  2      [ ACC ]     STREAM     LISTENING     17766    8920/trashapplet    /tmp/orbit-tsr/linc-22d8-0-41203884e708
unix  2      [ ACC ]     STREAM     LISTENING     17781    8926/gnome-vfs-daem /tmp/orbit-tsr/linc-22de-0-115698b05b36d
unix  2      [ ACC ]     STREAM     LISTENING     17791    8912/evolution-alar /tmp/orbit-tsr/linc-22d0-0-41203887151c
unix  2      [ ACC ]     STREAM     LISTENING     17885    8935/evolution-data /tmp/orbit-tsr/linc-22e7-0-58143a6ee9cf8
unix  2      [ ACC ]     STREAM     LISTENING     17910    8939/mapping-daemon /tmp/mapping-tsr
unix  2      [ ACC ]     STREAM     LISTENING     17936    8942/evolution-exch /tmp/orbit-tsr/linc-22ee-0-33c74c084d683
unix  2      [ ACC ]     STREAM     LISTENING     17992    8967/mini_commander /tmp/orbit-tsr/linc-2307-0-5c1d6f8978e1
unix  2      [ ACC ]     STREAM     LISTENING     18268    8970/notification-a /tmp/orbit-tsr/linc-230a-0-2b9d72f978b07
unix  2      [ ACC ]     STREAM     LISTENING     18285    8972/gnome-netstatu /tmp/orbit-tsr/linc-230c-0-2b9d72f991499
unix  2      [ ACC ]     STREAM     LISTENING     18342    8976/mixer_applet2  /tmp/orbit-tsr/linc-2310-0-58ccbb5430027
unix  2      [ ACC ]     STREAM     LISTENING     18358    8974/battstat-apple /tmp/orbit-tsr/linc-230e-0-58ccbb5437255
unix  2      [ ACC ]     STREAM     LISTENING     18386    8982/workrave-apple /tmp/orbit-tsr/linc-2316-0-58ccbb545daf9
unix  2      [ ACC ]     STREAM     LISTENING     18401    8978/clock-applet   /tmp/orbit-tsr/linc-2312-0-58ccbb5468051
unix  2      [ ACC ]     STREAM     LISTENING     18411    8980/cpufreq-applet /tmp/orbit-tsr/linc-2314-0-58ccbb546b768
unix  2      [ ACC ]     STREAM     LISTENING     18467    8984/workrave       /tmp/orbit-tsr/linc-2318-0-eda4e94df1a2
unix  2      [ ACC ]     STREAM     LISTENING     30708    9304/gnome-terminal /tmp/orbit-tsr/linc-2458-0-14313267da4cc
unix  2      [ ACC ]     STREAM     LISTENING     9086     8238/hald           @/tmp/hald-local/dbus-muoEHXoXjN
unix  2      [ ACC ]     STREAM     LISTENING     8991     8175/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     14829    8859/gam_server     @/tmp/fam-tsr-
unix  2      [ ACC ]     STREAM     LISTENING     10663    8815/dbus-daemon    @/tmp/dbus-DqUtfNDCaN

```

I suppose theese are acceptable, even though I don't have any idea on what bonobo, hald, gam_server or dbus-deamon are. dhclient is for getting connected to my adsl-modem and hence the internet :D 

```

top

```
Nothing unusual here (like I would know ;)  ) But at least nothing using resources, when I saw that the accessing of files where there wasn't any excessive use of resources either.

It appears as my home directory has been scanned just five minutes after I booted this time.

```

lsof

```
Produced an absurd quantity of lines, which I can't interpret in any constructive way.

Ok, maybe I'm just overly paranoid, I don't know. Anyhow thanks for the help. Oh and help concerning firestarter would be much appreciated.

/Tomas

---

### Post by h3llfyr3 on 2006-04-05
[QUOTE=colo]If something actually compromised your system (a thing I _highly_ doubt, to be honest), a properly set up packet filter probably won't save you, anyway.

Monitor the output of
```
netstat -nlp
```
for suspicious activities on listening sockets,
```
top
```
for unusual amounts of CPU-activity caused by unfamiliar processes,
get yourself **chrootkit** and run it,
check for open files you consider not necessarily to be opened by anything with **lsof**.

If you happen to have any questions to the points I mentioned, check back here with some more info on your possibly rooted box. ;)[/QUOTE]

Chap :) you can't trust any box that may have been rooted as rootkits replace your system binaries such as top , ls and netstat to hide naughtiness.
Scan the box from another machine to check open ports with nmap and use chrootkit ...

You could have had a full compromise with the recent breezy password in plain text issue , being able to read config files getting access to e-mail etc etc etc.

---

### Post by tsr on 2006-04-07
How do I do that?

I mean what am I going to expect from those scans, and how do I perform them?

/Tomas

---

