---
title: "Reinstallation of OS"
date: 2009-07-29
forum: Server Platforms
---

### Post by asai on 2009-07-29
Hi,
This question may sound a little strange, but here it is.. ;)
I have a server running 8.04 LTS. On this server I have tried a lot of different things and learned many lessons.
One thing I have learned is using VirtualBox for testing...
However, now I would like to use this server for real again, but have some trouble getting it to run like it should.
This server i located in a loft, without screen and kb. Using SSH to connect to it.

So the question: Is there a way to completely reinstall the system without having to take the server down from the loft and attach screen and kb?

---

### Post by asai on 2009-08-24
Since I haven't got any replies to this post, I will try to ask another question:

Is there a way to create a image with all installation questions answered? Then I can install unantended... :o
Is it possible to create a floppy which can read the image trough SSH from a server in the network?

---

### Post by cascade9 on 2009-08-24
> **asai said:**
> So the question: Is there a way to completely reinstall the system without having to take the server down from the loft and attach screen and kb?

Yep, there is-

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by asai on 2009-08-30
So I tried this... But it doesn't seem to work correctly for me... :(
I have a slightly different set up than the guide, but it should work.
Someone have an idea?

Here is my setup:
I have a DHCP-server and a file-server.
The ip address for the DHCP is 10.10.160.1 and the file-server is 10.10.160.7
I installed these packages on the fileserver:
```
apt-get install tftpd-hpa tftp-hpa xinetd
```

In the /etc/dhcp3/dhcpd.conf on the DHCP-server I added these lines:
```
filename "/var/lib/tftpboot/pxelinux.0";
option root-path "/var/lib/tftpboot/";
next-server 10.10.160.7;

```
Downloaded the appropriate package from here:
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/")
Unpacked it like this on the file-server:
```
tar -xvzf netboot.tar.gz -C /var/lib/tftpboot/
chown -R nobody:nogroup /var/lib/tftpboot
```
Added the file /etc/xinet.d/tftp on the file-server looking like this:
```
service tftp
  {
        disable                 = no
        socket_type             = dgram
        wait                    = yes
        user                    = root
        server                  = /usr/sbin/in.tftpd
        server_args             = -v -s /var/lib/tftpboot
        only_from   = 10.10.160.148/28
        interface   = 10.10.160.1
  }
```
Now, when I try to boot from the client, I get these messages:
```
PXE-T01: File not found
PXE-E3B: TFTP Error - File not found
PXE-M0F: Exiting Intel PXE ROM
FATAL: Could not read from the boot medium! System halted.
```

EDIT: I have also tried to put the tftp-server and installation files on the DHCP-server, and altered the /etc/dhcp3/dhcpd.conf file like this:
```
filename "/var/lib/tftpboot/pxelinux.0";
option root-path "/var/lib/tftpboot/";

```
Looks like the client connects fine to the server. I find this line in the daemon.log:
```
Aug 30 13:30:40 dhcpserver in.tftpd[24718]: RRQ from 10.10.160.148 filename /var/lib/tftpboot/pxelinux.0
```

---

### Post by asai on 2009-08-30
Solved it!

Altered one line in the dhcpd.conf file to this:
```
filename "pxelinux.0";

```

---

