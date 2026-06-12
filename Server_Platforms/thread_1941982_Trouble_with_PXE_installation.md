---
title: "Trouble with PXE installation"
date: 2012-03-16
forum: Server Platforms
---

### Post by absoord on 2012-03-16
Hi guys! I'm trying to configure both DHCP & TFTP servers in order to do PXE installations, but there's something I'm not doing ok since LAN booting is not working... I'm gonna explain what I did:

1) apt-get install dhcp3 tftpd-hpa tftp-hpa

2) My DHCP3 config (/etc/dhcp3/dhcpd.conf):

```

authoritative;

ddns-update-style none;

option domain-name "homeserv";

# por defecto
default-lease-time 600;
max-lease-time 7200;

log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.101 192.168.0.130;
  option domain-name-servers 192.168.0.1;
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  filename "pxelinux.0";
}

# This one's for VMWare installations (IPs like 192.168.153.*)
subnet 192.168.153.0 netmask 255.255.255.0 {
  range 192.168.153.101 192.168.153.130;
  option domain-name-servers 192.168.153.1, 62.42.230.24;
  option routers 192.168.153.1;
  option broadcast-address 192.168.153.255;
  filename "pxelinux.0";
}

```

The dhcp server is running ok:

```

root@homeserv:~# ps ax | grep dhcp
 1785 ?        Ss     0:00 /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf eth0

```

3) My TFTP config (/etc/default/tftpd-hpa):

```

RUN_DAEMON="yes"
TFTP_USERNAME="root"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"
OPTIONS="-l -c -v"

```

The TFTP server is running ok

```

root@homeserv:~# ps ax | grep tftp
 1729 ?        Ss     0:00 /usr/sbin/in.tftpd --listen --user root --address 0.0.0.0:69 --secure /var/lib/tftpboot

```

Furthermore, I was able to connect to 'localhost' via TFTP and download a file from the TFTP server (from the specified dir), so I assume it's ok.

4) I downloaded NETBOOT for [ubuntu lucid 10.04 repository]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/"), downloaded and decompressed in /var/lib/tftpboot.

Well, the problem is that I start a client machine with PXE option and it doesn't even detect the dhcp server. I mean, I get an error like: "PXE-E53: No boot filename received" after a while.

Also tried to debug with:

```
root@homeserv:/var/lib/tftpboot# tcpdump -s 1600 -neeevvvX 'proto (\udp or \tcp) and port 69'
```

And there's nothing... The server doesn't even receive a request for the PXE installation on that port :(

Any ideas of what I'm doing wrong? any additional checks?

Thanx a lot!

---

### Post by vikjon0 on 2012-03-18
I remember it to be a bit more complicated than that. Do you have any other dhcp server on the net?

---

### Post by absoord on 2012-03-18
> **vikjon0 said:**
> I remember it to be a bit more complicated than that. Do you have any other dhcp server on the net?

Thanx for your response!

Well, I've been investigating a bit more, and I've found out that there could be a problem with the router device, also providing DHCP, so there might be a conflict. I also read that there must be some specific net topology in order to get the installation work, in my case all devices are connected to a switch (also the router connection...). Could it be that?

---

### Post by boethius on 2012-03-22
> **absoord said:**
> Thanx for your response!

Well, I've been investigating a bit more, and I've found out that there could be a problem with the router device, also providing DHCP, so there might be a conflict. I also read that there must be some specific net topology in order to get the installation work, in my case all devices are connected to a switch (also the router connection...). Could it be that?
You're missing the following setting in your DHCP server config: 

```

next-server ip.address.of.tftpserver; 

```

[See here]("http://linux.die.net/man/5/dhcpd.conf") for more information on this option but basically this puts DHCP option 66 into the DHCP OFFER packet and tells the PXE client on the NIC where to bootstrap pxelinux.0 from. 

There are ways to do PXE booting without option 66 with gPXE/iPXE but that's another story and well beyond the scope of what you're asking.

---

### Post by absoord on 2012-03-23
> **boethius said:**
> You're missing the following setting in your DHCP server config: 

```

next-server ip.address.of.tftpserver; 

```

[See here]("http://linux.die.net/man/5/dhcpd.conf") for more information on this option but basically this puts DHCP option 66 into the DHCP OFFER packet and tells the PXE client on the NIC where to bootstrap pxelinux.0 from. 

There are ways to do PXE booting without option 66 with gPXE/iPXE but that's another story and well beyond the scope of what you're asking.

Thx boethius for your reply! Yes, I realized it's an important parameter so I set it up but it still doesn't work. I guess it's the way to tell the PXE client where yo look for the pxelinux.0, but on the server side I don't even get a DHCP request for it :-( There's something else I'm missing...

---

