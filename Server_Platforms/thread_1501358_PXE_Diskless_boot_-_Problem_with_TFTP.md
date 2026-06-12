---
title: "PXE Diskless boot - Problem with TFTP?"
date: 2010-06-04
forum: Server Platforms
---

### Post by yotamhc on 2010-06-04
Hi,

I'm posting here as I now see that mt previous post is probably in the wrong forum.
I am trying to setup a server for a diskless boot environment (computer lab).
I followed the steps in this tutorial: [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
Except that for getting the TFTP to work I had to also install xinetd

I use one computer as a server (runs ubuntu server 10.4, kernel version 2.6.32-21-server) and my macbook with a VM in it as a client.
Current situation is that the VM client retrieves addresses from DHCP but does not seem to successfully retrieve the files from TFTP.

To check the TFTP I used another VM I have on this laptop that already runs ubuntu 10.4 desktop. I could connect to the TFTP server and get the files with no problem.

This is the content of my /etc/dhcp3/dhcpd.conf:
```

allow booting;
allow bootp;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;
  option domain-name-servers 192.168.1.1;

  filename "/pxelinux.0";
}

```And here is the content of my /etc/xinetd.d/tftp:
```

service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = root
server = /usr/sbin/in.tftpd
server_args = -s /tftpboot
disable = no
}

```And this is the content of /etc/default/tftpd-hpa:
```

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /tftpboot"

```Sorry for the long post and that a lot for your help!
Yotam

---

### Post by yotamhc on 2010-06-04
OK, I found the problem - I used the wrong pxelinux.0 file (took it from server instead of client)

[EDITED:]
Now the machine boots but it seems like it cannot mount the NFS drive and I get a "kernel panic" message:
```

IP-Config: eth0 hardware address 00:0c:29:79:86:c1 mtu 1500 DHCP
[    2.775718] eth0: link up
IP-Config: no response after 60 secs - giving up
/init: .: line 3: can't open /tmp/net-eth0.conf
[   69.073555] Kernel panic- not syncing" Attempted to kill init!
[   69.073859] Pid: 1, comm: init Not tainted 2.6.32-22-generic #35-Ubuntu
< call trace - if it can help I can grab a screenshot >

```

I tested the NFS and it works from another VM - I can mount it and access files. I don't understand the error message here...

Thanks!

---

