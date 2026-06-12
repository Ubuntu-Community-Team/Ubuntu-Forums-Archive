---
title: "How do I find what service is running on this port?"
date: 2011-12-26
forum: Security
---

### Post by Wiking on 2011-12-26
Hello I was doing an nmap scan of my home network and would just like to know what service is running on a specific port. 

Input:

```
user@Kubu7AA-A2L:~$ nmap -v -A 192.168.0.4, 192.168.0.100, 192.168.0.101
```

Where: 192.168.0.4 is D-Link Router, 192.168.0.100-101 are my two clients.

Output: Here is a small excerpt

```
Discovered open port 80/tcp on 192.168.0.4
Discovered open port 53/tcp on 192.168.0.4
Completed Connect Scan against 192.168.0.100 in 0.03s (1 host left)
Discovered open port 49152/tcp on 192.168.0.4
```

How can I find out what service is running on -port 49152?

I looked in my router's IP tables (D-link wbr-1310) but did not find anything.

I read on the internet that torrent programs use -p 49152, so I'm guessing that perhaps the torrent program is using -p 49152 on my router to reach the internet? But then why is it open when torrent is off? 

I would just like to verify what service it is, but how can I verify through a firewall if it is -p 49152 on the router and not the PC? 

I also checked for ranges 49152-49170 and they were all closed except for 49152.

I did the scan from my pc without ufw enabled. 

When I did a scan on CRG I got this:

```
Results from probe of port: 49152

    0 Ports Open
    0 Ports Closed
    1 Ports Stealth
---------------------
    1 Ports Tested

THE PORT tested was found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.
```

Thanks

---

### Post by CharlesA on 2011-12-26
```
sudo netstat -nlp
```

---

### Post by Wiking on 2011-12-26
I got some outputs but none of them identified  port 49152:


user@Kkubuntu-A2L:~$ sudo netstat -nlp
[sudo] password for user:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:000           0.0.0.0:*               LISTEN      1406/cupsd      
tcp6       0      0 ::1:000                 :::*                    LISTEN      1406/cupsd      
udp        0      0 0.0.0.0:68             0.0.0.0:*                           7167/dhclient   
udp        0      0 0.0.0.0:5300            0.0.0.0:*                           1069/avahi-daemon: 
udp        0      0 0.0.0.0:60039           0.0.0.0:*                           1069/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                1069/avahi-daemon: 
udp6       0      0 :::39934                :::*                                1069/avahi-daemon: 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     9686     1807/pulseaudio     /home/user/.pulse/92d01a03164aba92e25f09720000000c-runtime/dbus-socket
unix  2      [ ACC ]     STREAM     LISTENING     1023384  7222/chrome         /tmp/.com.google.Chrome.CynRmc/SingletonSocket
unix  2      [ ACC ]     STREAM     LISTENING     14038    1798/nepomukservice /tmp/ksocket-user/nepomuk-socket
unix  2      [ ACC ]     STREAM     LISTENING     11716    1758/mysqld         /home/user/.local/share/akonadi/socket-KJ377AA-A2L/mysql.socket
unix  2      [ ACC ]     STREAM     LISTENING     8495     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     8010     1142/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     380946   3699/kio_http_cache /tmp/ksocket-user/kio_http_cache_cleaner
unix  2      [ ACC ]     STREAM     LISTENING     8093     1177/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     8797     1043/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     8055     1165/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8035     1145/kdm            /var/run/xdmctl/dmctl/socket
unix  2      [ ACC ]     STREAM     LISTENING     11777    1756/akonadiserver  /home/user/.local/share/akonadi/socket-KJ377AA-A2L/akonadiserver.socket
unix  2      [ ACC ]     STREAM     LISTENING     10343    1145/kdm            /var/run/xdmctl/dmctl-:0/socket
unix  2      [ ACC ]     STREAM     LISTENING     13666    1807/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     SEQPACKET  LISTENING     8538     485/udevd           @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     9340     1406/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     8829     1069/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     9130     1562/dbus-daemon    @/tmp/dbus-fjrmFkUfei
unix  2      [ ACC ]     STREAM     LISTENING     8056     1165/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11302    1557/ssh-agent      /tmp/ssh-pdxcOSBM1511/agent.1511
unix  2      [ ACC ]     STREAM     LISTENING     9125     1558/gpg-agent      /tmp/gpg-xjYBCK/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     9411     1625/kdeinit4: kdei /tmp/ksocket-user/kdeinit4__0
unix  2      [ ACC ]     STREAM     LISTENING     9147     1626/kdeinit4: klau /tmp/ksocket-user/klauncherMT1626.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     9182     1658/kdeinit4: ksms /tmp/.ICE-unix/1658
unix  2      [ ACC ]     STREAM     LISTENING     1011503  1807/pulseaudio     /home/user/.pulse/92d01a03164aba92e25f09720000000c-runtime/cli
unix  2      [ ACC ]     STREAM     LISTENING     5842     1177/bluetoothd     /var/run/sdp                                                                
unix  2      [ ACC ]     STREAM     LISTENING     12183    1874/virtuoso-t     /tmp/virt_1111
unix  2      [ ACC ]     STREAM     LISTENING     9181     1658/kdeinit4: ksms @/tmp/.ICE-unix/1658
unix  2      [ ACC ]     STREAM     LISTENING     12415    1807/pulseaudio     /home/user/.pulse/92d01a03164aba92e25f09720000000c-runtime/native

---

### Post by emiller12345 on 2011-12-26
if the port 49152 is on your d-link router, this is a non-standard port and will probably be difficult to determine.  If the router is actively sending and receiving data from this port you might be able to capture some of it using tcpdump or wireshark, and google important bits of data to figure out what service it is (maybe some kind of multicast DNS). You can also send D-link an email inquiring about it and they might be able to help you.

---

### Post by Wiking on 2011-12-26
thanks for the replies. I will sign up on a d-link forum and look into it. 

Just out of curiosity could malicious maleware infect the router and do damage to the network or would it have to be on a pc as root to have any affect?

I'm assuming a sniffer on a router could do quite the damage.

---

### Post by emiller12345 on 2011-12-27
because the router is the central point of your network, it is probably one of the most important parts of your computer(s).  Malware infecting most propriety firmware routes is not likely I would think.  Some routers maybe more likely, it just depends. Having someone mess with your routers settings is quite likely.  Main targets are probably DNS addresses, (external) Remote Administration activation, and uPnP activation.  make sure that the DNS addresses that you are using are either ones your ISP has provided (contact them) or ones you are choosing to use.  Remote Administration should be disabled (I don't know why companies are still including this with routers, cause I don't know anyone that would use it). uPnP should be disabled (this can be used to disable part of the routers firewall by port forwarding).

---

### Post by Wiking on 2011-12-27
After playing around I discovered it was nPNP that was using port 49152 on my router, disabling it made nmap report a closed port.

---

### Post by Soul-Sing on 2011-12-27
```
netstat -nlp
```
or ```
sudo netstat -nlp
```
whats the difference?

---

### Post by OpSecShellshock on 2011-12-28
> **leoquant said:**
> ```
netstat -nlp
```or ```
sudo netstat -nlp
```whats the difference?

Running it without privilege escalation will only show processes owned by the user running the command, whereas running it with sudo will show all processes owned by all users, including root.

---

### Post by Soul-Sing on 2011-12-28
> **OpSecShellshock said:**
> Running it without privilege escalation will only show processes owned by the user running the command, whereas running it with sudo will show all processes owned by all users, including root.

thank you.

---

