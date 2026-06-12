---
title: "TFTPD32 server in Linux !!"
date: 2008-07-18
forum: Server Platforms
---

### Post by raedbenz on 2008-07-18
Hi, i have been reading some tutorials use TFTPD32 server under Windows to send files from PC to another PC or development board.
how can i use Ethernet for sending files under Linux?
is there equivalent to this TFTPD32 server???
Thanx

---

### Post by Sef on 2008-07-18
moved to server platforms.

---

### Post by promodus on 2008-07-18
```
apt-get install tftpd-hpa dhcp3-server
```

---

### Post by raedbenz on 2008-07-19
> **promodus said:**
> ```
apt-get install tftpd-hpa dhcp3-server
```

i have installed it , but how do i run it?
i tyopd:
$ tftpd-hpa
or 
$dhcp3-server

and it says :  command not found
hints?
thanks

---

### Post by promodus on 2008-07-20
For the dhcp3-server you will need a configuration file.
This is typically located in:
```
/etc/dhcp3/dhcpd.conf
```

man dhcpd.conf will provide you some info on syntax. 

simple dhcpd.conf configuration
Class B Private, with router, DNS, and tftp on 172.31.0.1
```
allow booting;
allow bootp;
authoritive; 
default-lease-time 600;
max-lease-time 7200;

subnet 172.31.0.0 netmask 255.255.0.0 
 {
  next-server 172.31.0.1;
  filename "pxelinux.0";
  option subnet-mask 255.255.0.0;
  range 172.31.0.1 172.31.255.254;
  option domain-name-servers 172.31.0.1;
  option routers 172.31.0.1;
 }
```

For your TFTP, I would believe this is started by inetd

The configuration as where the tftp daemon is started is in
```
/etc/inetd.conf
``` 

The location of the tftp files will typically be:
```
/var/lib/tftpboot
```

---

### Post by raedbenz on 2008-07-22
isnt there any graphical app equivalent for it?
like in windows.
thanks

---

### Post by promodus on 2008-07-22
```
apt-get install gdhcpd
```

As for the TFTP Daemon, it's easy enough to configure that by hand. 
I don't know of a GUI configuration utility for it. Could always write one :)

I prefer using a text editor myself.

---

### Post by raedbenz on 2008-07-22
> **promodus said:**
> ```
apt-get install gdhcpd
```

As for the TFTP Daemon, it's easy enough to configure that by hand. 
I don't know of a GUI configuration utility for it. Could always write one :)

I prefer using a text editor myself.

hi,
i have used this web to configure tftpd: [http://docs.blackfin.uclinux.org/doku.php?id=setting_up_a_tftp_server]("http://docs.blackfin.uclinux.org/doku.php?id=setting_up_a_tftp_server")
but step 5 returns "fail"
any hints?
thanks

---

