---
title: "sudo netstat -nlp Output??"
date: 2011-12-29
forum: Security
---

### Post by themanfromdelmonte on 2011-12-29
Is this ok?

```
ian@ian-HP-G62-Notebook-PC:~$ sudo netstat -nlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      902/cupsd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      902/cupsd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1373/dhclient   
udp        0      0 0.0.0.0:50062           0.0.0.0:*                           874/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           874/avahi-daemon: r
udp6       0      0 :::44243                :::*                                874/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                874/avahi-daemon: r
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     6791     1025/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     7137     1481/gnome-keyring- /tmp/keyring-8z32Yr/control
unix  2      [ ACC ]     STREAM     LISTENING     11322    1526/ssh-agent      /tmp/ssh-ADPmanPw1490/agent.1490
unix  2      [ ACC ]     STREAM     LISTENING     10960    1490/gnome-session  /tmp/.ICE-unix/1490
unix  2      [ ACC ]     STREAM     LISTENING     11411    1481/gnome-keyring- /tmp/keyring-8z32Yr/gpg
unix  2      [ ACC ]     STREAM     LISTENING     11412    1481/gnome-keyring- /tmp/keyring-8z32Yr/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     11413    1481/gnome-keyring- /tmp/keyring-8z32Yr/ssh
unix  2      [ ACC ]     STREAM     LISTENING     10959    1490/gnome-session  @/tmp/.ICE-unix/1490
unix  2      [ ACC ]     STREAM     LISTENING     9189     1575/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     9191     1575/pulseaudio     /home/ian/.pulse/13e11e721a55c1ca2385e17c00000007-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     11506    1575/pulseaudio     /home/ian/.pulse/13e11e721a55c1ca2385e17c00000007-runtime/dbus-socket
unix  2      [ ACC ]     STREAM     LISTENING     6342     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     160393   12178/npviewer.bin  @/org/wrapper/NSPlugins/libflashplayer.so/12159-2/1505346641
unix  2      [ ACC ]     STREAM     LISTENING     6829     1087/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     6750     1002/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     6790     1025/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     SEQPACKET  LISTENING     1916     297/udevd           @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     10945    1530/dbus-daemon    @/tmp/dbus-gEr90HM3Ug
unix  2      [ ACC ]     STREAM     LISTENING     8844     874/avahi-daemon: r /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     166031   902/cupsd           /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     6826     1087/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     6640     860/dbus-daemon     /var/run/dbus/system_bus_socket
```

---

### Post by CharlesA on 2011-12-29
Looks fine.

Check this page out: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Soul-Sing on 2011-12-29
Do you use cpusd, avahi, bluetooth?
If not why not disable these services? (via /etc/init)

many services can be disabled in ubuntu 11.10 (gnome)
```
cd /etc/xdg/autostart/
```
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Via dash: startup managment you can manage/disable many unused services.

---

