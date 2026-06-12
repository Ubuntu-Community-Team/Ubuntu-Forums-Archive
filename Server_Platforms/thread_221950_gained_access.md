---
title: "gained access?"
date: 2006-07-24
forum: Server Platforms
---

### Post by chalkedup on 2006-07-24
hello
im worried my computers been compromised
ive done a couple of online scans and all ports are closed but ive ran the test on another site and it said that some are open and its ports i cant find info on
i was trying to clean up my pc yesterday and i started getting alot of hits that showed up in firestarter then after than none were showing up as serious in red
ive run netstat and there are things listening and i have things in my /tmp/ folder like these are duplicated
```
 /tmp/orbit-bob
 /tmp/.ICE-unix/21804
 /tmp/.X11-unix/X0
/tmp/orbit-root/linc-
/var/run/dbus/system_
 @/tmp/dbus-DOCVgkABf8

unix  3      [ ]         STREAM     CONNECTED     25820    /tmp/orbit-bob
/tmp/mapping-bob
```

```
bob@bob-desktop:~$ ps aux |grep -i firestarter
bob  5968  0.0  0.9  11660  5052 ?        S    Jul23   0:00 gksu firestarte r
root      5969  4.5  3.1  78932 16428 ?        Ssl  Jul23   4:44 firestarter
bob 15484  0.0  0.1   2884   860 pts/0    S+   00:34   0:00 grep -i firesta rter
```


this is doing my head in is there anything i can do to clean this pc up or find out whats going on?

---

### Post by LordHunter317 on 2006-07-24
Seeing as you didn't post what the scan said, no one can help you.

---

### Post by chalkedup on 2006-07-24
sorry im new to linux and the list was quite long 

```
bob@bob-desktop:~$ sudo netstat -l -np -p
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:58770         0.0.0.0:*               LISTEN     4209/hpiod
tcp        0      0 127.0.0.1:50739         0.0.0.0:*               LISTEN     4213/python
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4854/cupsd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          4637/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     24827    21804/x-session-man /tmp/orbit-bob/linc-552c-0-61fcf4f17b05a
unix  2      [ ACC ]     STREAM     LISTENING     24978    21855/gnome-keyring /tmp/keyring-H6kivw/socket
unix  2      [ ACC ]     STREAM     LISTENING     24990    21857/bonobo-activa /tmp/orbit-bob/linc-5561-0-3b7fe23ae0d91
unix  2      [ ACC ]     STREAM     LISTENING     25058    21859/gnome-setting /tmp/orbit-bob/linc-5563-0-6813b821be6a6
unix  2      [ ACC ]     STREAM     LISTENING     25501    21985/metacity      /tmp/orbit-bob/linc-55e1-0-323ded714f529
unix  2      [ ACC ]     STREAM     LISTENING     11783    4820/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     25530    21990/gnome-panel   /tmp/orbit-bob/linc-55e6-0-4405bbe84be0
unix  2      [ ACC ]     STREAM     LISTENING     25561    21992/nautilus      /tmp/orbit-bob/linc-55e8-0-2bc7f0d814b75
unix  2      [ ACC ]     STREAM     LISTENING     25569    21995/gnome-volume- /tmp/orbit-bob/linc-55ea-0-2bc7f0d88ab0a
unix  2      [ ACC ]     STREAM     LISTENING     25612    22001/update-notifi /tmp/orbit-bob/linc-55f1-0-189acd98a15c5
unix  2      [ ACC ]     STREAM     LISTENING     25637    22004/gnome-vfs-dae /tmp/orbit-bob/linc-55f4-0-471c67aed6a89
unix  2      [ ACC ]     STREAM     LISTENING     25676    22039/gnome-power-m /tmp/orbit-bob/linc-55f6-0-4d25812187902
unix  2      [ ACC ]     STREAM     LISTENING     25705    22012/gnome-cups-ic /tmp/orbit-bob/linc-55fc-0-6127a7b347e20
unix  2      [ ACC ]     STREAM     LISTENING     25727    22020/trashapplet   /tmp/orbit-bob/linc-5604-0-6127a7b39ca97
unix  2      [ ACC ]     STREAM     LISTENING     25813    22052/drivemount_ap /tmp/orbit-bob/linc-5624-0-34c71a72c9f32
unix  2      [ ACC ]     STREAM     LISTENING     25830    22054/gnome-diction /tmp/orbit-bob/linc-5626-0-1a94e7bd4190b
unix  2      [ ACC ]     STREAM     LISTENING     25903    22061/mixer_applet2 /tmp/orbit-bob/linc-562d-0-3e4c9c106d45d
unix  2      [ ACC ]     STREAM     LISTENING     25920    22063/clock-applet  /tmp/orbit-bob/linc-562f-0-2c918559a4ef1
unix  2      [ ACC ]     STREAM     LISTENING     10772    4285/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     26101    22074/gnome-screens /tmp/orbit-bob/linc-5637-0-4cd7fc9aa0a20
unix  2      [ ACC ]     STREAM     LISTENING     26122    22076/gksu          /tmp/orbit-bob/linc-563c-0-2a45cfd894e49
unix  2      [ ACC ]     STREAM     LISTENING     26160    22079/gconfd-2      /tmp/orbit-root/linc-563f-0-656242d12d3a9
unix  2      [ ACC ]     STREAM     LISTENING     26167    22077/firestarter   /tmp/orbit-root/linc-563d-0-3fb9f0b02f4c8
unix  2      [ ACC ]     STREAM     LISTENING     27100    22819/firefox-bin   /tmp/orbit-bob/linc-5923-0-69c1f0afcfc85
unix  2      [ ACC ]     STREAM     LISTENING     43553    22818/gedit         /tmp/orbit-bob/linc-5922-0-262cd291d013
unix  2      [ ACC ]     STREAM     LISTENING     43721    23012/gnome-termina /tmp/orbit-bob/linc-59e4-0-6022d02c8ae21
unix  2      [ ACC ]     STREAM     LISTENING     11821    4854/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     10594    4180/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     24969    21804/x-session-man /tmp/.ICE-unix/21804
unix  2      [ ACC ]     STREAM     LISTENING     10796    4300/hald           @/tmp/hald-local/dbus-svOGDvDvLB
unix  2      [ ACC ]     STREAM     LISTENING     10552    4176/gdm            /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     25773    22030/mapping-daemo /tmp/mapping-bob
unix  2      [ ACC ]     STREAM     LISTENING     43557    22818/gedit         /tmp/gedit.bob.3254146351
unix  2      [ ACC ]     STREAM     LISTENING     24798    21850/dbus-daemon   @/tmp/dbus-DOCVgkABf8
unix  2      [ ACC ]     STREAM     LISTENING     10797    4300/hald           @/tmp/hald-runner/dbus-8cyqfBSJCb
unix  2      [ ACC ]     STREAM     LISTENING     24793    21846/ssh-agent     /tmp/ssh-dSxJM21804/agent.21804
unix  2      [ ACC ]     STREAM     LISTENING     24817    21852/gconfd-2      /tmp/orbit-bob/linc-555c-0-693fda506da9f

```


ive also just run rkhunter heres the text from that
```
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory)

gpg: WARNING: unsafe ownership on configuration file `/home/bob3073x/.gnupg/gpg.conf'

   Searching for /etc/passwd...                               [ Found ]
MD5
MD5 compared: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 0

Scanning took 628 seconds


```

if you need any other logs just say which ones

---

### Post by LordHunter317 on 2006-07-24
The online scan(s), I mean.  What did the online scan that alarmed you say?

---

### Post by chalkedup on 2006-07-24
i used this site and scanned the ports it showed in netstat
[http://freescan.seifried.org]("http://freescan.seifried.org")

Number of open TCP ports: 0 Number of closed TCP ports: 0
Number of filtered TCP ports: 68 Number of closed UDP ports: 0
Number of open UDP ports: 29

---

### Post by LordHunter317 on 2006-07-24
I would bet money their scanner is broken.  Accurately detecting "open" UDP ports is rather difficult.

Either way, I see no cause for alarm.

---

### Post by chalkedup on 2006-07-24
thanks Lordhunter
is there any way i can keep a check of whats going on as i think by the time im posting on here things are changed or switched off so arent showing up, ive had problems in the past with being hacked on win thats why i changed to linux
is there something i can instal to lock down my pc limiting me to surfing and ftp now and again to my site ?
would bastille be a option ?

---

### Post by _mrv on 2006-08-02
As far as I understand, those ports are UNIX sockets (not TCP or UDP sockets) which are used for the interprocess communications (IPC):

[http://www.ecst.csuchico.edu/~beej/guide/ipc/usock.html](http://www.ecst.csuchico.edu/~beej/guide/ipc/usock.html)

I wouldn't worry about those.

_mrv

---

