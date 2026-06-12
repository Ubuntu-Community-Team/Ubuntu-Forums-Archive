---
title: "Listening ports (more than one)"
date: 2009-09-16
forum: Security
---

### Post by sopadeajo on 2009-09-16
What is the purpose of all those listening ports?

Note than this information (scary for me) was gotten with the good-old terminal (not with the unjustly accused Firestarter

-desktop:~$ netstat -al | grep LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     7247     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     7039     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     6310     @/var/run/hald/dbus-HPv96rko3u
unix  2      [ ACC ]     STREAM     LISTENING     7137     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     6245     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     7022     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     6040     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     7138     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8248     /tmp/keyring-PRGAIN/socket
unix  2      [ ACC ]     STREAM     LISTENING     10460    /tmp/ssh-EeEmIN3489/agent.3489
unix  2      [ ACC ]     STREAM     LISTENING     11029    /tmp/orbit-/linc-f56-0-5a0188ef472e5
unix  2      [ ACC ]     STREAM     LISTENING     11279    /tmp/orbit-/linc-f54-0-1b29369261395
unix  2      [ ACC ]     STREAM     LISTENING     11289    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     11292    /home//.pulse/7ec17fb8b2078fff5cb60dad4aa7205c:runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     11332    /tmp/seahorse-AZI8qL/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     11371    /tmp/.ICE-unix/3489
unix  2      [ ACC ]     STREAM     LISTENING     11395    /tmp/orbit-/linc-da1-0-11054d126ac20
unix  2      [ ACC ]     STREAM     LISTENING     11433    /tmp/orbit-/linc-f61-0-119fe838dc4ec
unix  2      [ ACC ]     STREAM     LISTENING     7094     /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     11563    /tmp/orbit-/linc-f72-0-33e0abf73dc23
unix  2      [ ACC ]     STREAM     LISTENING     11587    /tmp/orbit-/linc-d84-0-5aab58a48b7e
unix  2      [ ACC ]     STREAM     LISTENING     11591    /tmp/keyring-PRGAIN/socket.ssh
unix  2      [ ACC ]     STREAM     LISTENING     11593    /tmp/keyring-PRGAIN/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     11726    /tmp/orbit-/linc-f7a-0-6d20b2aa43079
unix  2      [ ACC ]     STREAM     LISTENING     11742    /tmp/orbit-/linc-f79-0-21b0d7f5b075d
unix  2      [ ACC ]     STREAM     LISTENING     16595    @/tmp/dbus-1uANDDQL10
unix  2      [ ACC ]     STREAM     LISTENING     12301    /tmp/orbit-/linc-f8b-0-4029bcaf164ff
unix  2      [ ACC ]     STREAM     LISTENING     12467    /tmp/orbit-/linc-f7f-0-5e75ce598f6cd
unix  2      [ ACC ]     STREAM     LISTENING     12589    /tmp/orbit-/linc-f7b-0-9d90c5f42ae
unix  2      [ ACC ]     STREAM     LISTENING     12808    /tmp/orbit-/linc-f7d-0-3425265b84c31
unix  2      [ ACC ]     STREAM     LISTENING     12490    /tmp/orbit-/linc-f80-0-5e75ce59957b0
unix  2      [ ACC ]     STREAM     LISTENING     12495    /tmp/orbit-/linc-f82-0-752404f795c1e
unix  2      [ ACC ]     STREAM     LISTENING     12601    /tmp/orbit-/linc-f8e-0-552adcc167d2
unix  2      [ ACC ]     STREAM     LISTENING     12630    /tmp/orbit-/linc-f9c-0-12a3b57829aeb
unix  2      [ ACC ]     STREAM     LISTENING     12665    /tmp/orbit-/linc-f83-0-3ae806cba23b1
unix  2      [ ACC ]     STREAM     LISTENING     12728    /tmp/orbit-/linc-f84-0-14ef980cbbf24
unix  2      [ ACC ]     STREAM     LISTENING     12890    /tmp/orbit-/linc-fb7-0-70ad8fd6c0444
unix  2      [ ACC ]     STREAM     LISTENING     12949    /tmp/orbit-/linc-fbf-0-347a5a6e4992c
unix  2      [ ACC ]     STREAM     LISTENING     13768    /tmp/orbit-/linc-fc8-0-e27072a81a1a
unix  2      [ ACC ]     STREAM     LISTENING     13798    /tmp/orbit-/linc-1036-0-354f4bb9a7c4e
unix  2      [ ACC ]     STREAM     LISTENING     14163    /tmp/orbit-/linc-104d-0-465f514c7331c
unix  2      [ ACC ]     STREAM     LISTENING     14186    /tmp/orbit-/linc-1050-0-4db9ae50a624b
unix  2      [ ACC ]     STREAM     LISTENING     14207    /tmp/orbit-/linc-104a-0-36d44eeb8974
unix  2      [ ACC ]     STREAM     LISTENING     15070    /tmp/orbit-/linc-1092-0-66a1af2714f2f
unix  2      [ ACC ]     STREAM     LISTENING     19553    /tmp/orbit-/linc-1410-0-36f17e7c791ec
unix  2      [ ACC ]     STREAM     LISTENING     19158    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16529    /tmp/orbit-linc-1193-0-1b2eb4df204f3
unix  2      [ ACC ]     STREAM     LISTENING     6332     @/var/run/hald/dbus-8dr65GBmM6
unix  2      [ ACC ]     STREAM     LISTENING     16612    /tmp/orbit-root/linc-119b-0-4753ff11c52d3
unix  2      [ ACC ]     STREAM     LISTENING     16631    /tmp/orbit-root/linc-1194-0-4b4cb3a1d035a
unix  2      [ ACC ]     STREAM     LISTENING     10573    @/tmp/dbus-FwQAqEcWx7

---

### Post by __p1n__ on 2009-09-16
All those unix-domain sockets are internal ports that various services are listening on.  Judging by the beau coup amount of gnome corba servers my guess is that you're running ubuntu and not kubuntu and also have a lot of things switched on.

---

### Post by rookcifer on 2009-09-16
Those are [Unix Domain Sockets]("http://en.wikipedia.org/wiki/Unix_domain_socket") and are *not* listening to the Internet at large.  They are not TCP services.

If you just want to see what TCP ports are listening, you need to tweak that netstat command a bit.  Try this:

```
sudo netstat -atpvnl
```

---

### Post by sopadeajo on 2009-09-16
> **rookcifer said:**
> Those are [Unix Domain Sockets]("http://en.wikipedia.org/wiki/Unix_domain_socket") and are *not* listening to the Internet at large.  They are not TCP services.

If you just want to see what TCP ports are listening, you need to tweak that netstat command a bit.  Try this:

```
sudo netstat -atpvnl
```

I get this: LISTEN      2983/cupsd  which did not appear when using Netstat with  the excellent GUI: Network Tools happily included with Ubuntu.
Hope this port is not kind of dangerous when listening.
Edited: it could be a program instead of a port, i do not know.
Edited2: ok, i can see now it is the internal number of the program that runs printers, not a port.

---

### Post by cdenley on 2009-09-17
> **sopadeajo said:**
> I get this: LISTEN      2983/cupsd  which did not appear when using Netstat with  the excellent GUI: Network Tools happily included with Ubuntu.
Hope this port is not kind of dangerous when listening.
Edited: it could be a program instead of a port, i do not know.
Edited2: ok, i can see now it is the internal number of the program that runs printers, not a port.

The whole line should be

```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4063/cupsd
```
The local address column has "127.0.0.1:631". This means it is listening on 127.0.0.1 port 631. It is a TCP port as the first column indicates. This should show up in the Network Tools GUI. That GUI does not display the process name and process ID, which is the part you posted.

---

### Post by sopadeajo on 2009-09-17
> **cdenley said:**
> The whole line should be

```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4063/cupsd
```The local address column has "127.0.0.1:631". This means it is listening on 127.0.0.1 port 631. It is a TCP port as the first column indicates. This should show up in the Network Tools GUI. That GUI does not display the process name and process ID, which is the part you posted.
Ok,i get
```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2990/cupsd 
```The number 4063 or 2990 is a variable.


But i still would like to understand much more why are all these ports (though no TCP ports (are they UDP ports?)) are listening and to what are they listening.To processes, to programs??
What kind of hardware(or software ?) architecture is it? I am a newbie unsatisfied when not understanding.

---

### Post by cdenley on 2009-09-17
> **sopadeajo said:**
> 
The number 4063 or 2990 is a variable.

But i still would like to understand much more why are all these ports (though no TCP ports (are they UDP ports?)) are listening and to what are they listening.To processes, to programs??
What kind of hardware(or software ?) architecture is it? I am a newbie unsatisfied when not understanding.

The number 4063 or 2990 is the [PID (process ID)]("http://en.wikipedia.org/wiki/Process_identifier") as the column header indicates. The protocol for most of the output in your first post is "unix". The column headers were printed, but didn't match your grep expression.
[http://en.wikipedia.org/wiki/Unix_domain_socket](http://en.wikipedia.org/wiki/Unix_domain_socket)
It is used for inter-process communication, not network communication. A process can listen for data from another process like with a network protocol, except it is more efficient and can only be accessed through the filesystem.

---

