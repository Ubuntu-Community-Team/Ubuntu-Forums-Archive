---
title: "ltsp fails in tftp under Ubuntu 9.10"
date: 2010-02-17
forum: Server Platforms
---

### Post by jmcarval on 2010-02-17
In Jaunty (9.04) I've setup a small (eleven-terminal) ltsp network at the local school. It handled around 6600 working hours with ease.
Now I've upgrade the server to Karmic Koala (9.10) and it just stopped working.
1) The clients have PXE NICs
2) They get the proper IPs from the DHCP server and respond appropriately to changes in the DHCP configuration files. 
3) DHCP server also points the clients to
filename=/ltsp/i386/pxelinux.0
4) When the clients try to download the pxelinux.0 over tftp they just timeout
5) /etc/inetd.conf has an entry like
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot
6) The file /var/lib/tftpboot/ltsp/i386/pxelinux.0 exists on the server

I'm lost at all these configuration files and protocols.
Any help or link to help is welcomed.

Thanks

Joao

---

### Post by bmathis on 2010-02-19
If you made any changes to the DHCP file or the image that the clients boot from, then run these 3 commands 
> sudo ltsp-update-sshkeys
sudo ltsp-update-kernals
sudo ltsp-update-image


If that doesnt work, then restart the DHCP > sudo /etc/init.d/dhcpe-server restart restart the server itself, or check the router/switch to see if it is locked up.

A good source for Ubuntu LTSP is [https://help.ubuntu.com/community/UbuntuLTSP]("https://help.ubuntu.com/community/UbuntuLTSP") and the IRC channel.

---

### Post by amit@nitttrchd.ac.in on 2010-03-25
> **jmcarval said:**
> In Jaunty (9.04) I've setup a small (eleven-terminal) ltsp network at the local school. It handled around 6600 working hours with ease.
Now I've upgrade the server to Karmic Koala (9.10) and it just stopped working.
1) The clients have PXE NICs
2) They get the proper IPs from the DHCP server and respond appropriately to changes in the DHCP configuration files. 
3) DHCP server also points the clients to
filename=/ltsp/i386/pxelinux.0
4) When the clients try to download the pxelinux.0 over tftp they just timeout
5) /etc/inetd.conf has an entry like
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot
6) The file /var/lib/tftpboot/ltsp/i386/pxelinux.0 exists on the server

I'm lost at all these configuration files and protocols.
Any help or link to help is welcomed.

Thanks

Joao



Mr Joao


I am also facing the same problem , in ubuntu 8.04 and 8.10 it is working fine but problemm of ligin at client end and when we are doing with 9.10 it is giving same problem of tftp timed out


please email  nitttrchd[at] gmail.com

---

### Post by nick_stokie on 2010-03-27
I had a similar problem moving from 8.10 to 9.04. If you have an old version of pxelinux.0 (from an old install) try substituting that for the new pxelinux.0 (in var/lib/ltsp/tftpboot).

I found the new pxelinux.0 (14.4kB) didn't work, but the old one (13.8kB) did. Do NOT run ltsp-update-image after this as it will overwrite the pxelinux.0

---

### Post by ene_dene on 2010-04-01
I've tried installing the LTSP on ubuntu server 9.10 as well.
I already had installed the server, and now I wanted LTSP, I installed it by command:
```
sudo aptitude install ltsp-server-standalone
sudo ltsp-build-client
sudo ltsp-update-sshkeys
sudo ltsp-update-kernals
sudo ltsp-update-image

```
Then the directories with:
```
/opt/ltsp/amd64
```
file system and
```
/opt/ltsp/images/
```
amd64.img file are created.

When trying to connect the thin client it gets an IP from DHCP but it stops at TFTP, saying "TFTP open timeout".

I concluded that the problem is in /etc/ltsp/dhcpd.conf file where the directories have the wrong path:
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.100;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```
I don't have i386 directories or pxelinux.0 and dmi.img file. Instead I have:
```
/opt/ltsp/amd64
/opt/ltsp/images/amd64.img
```
So I changed last few lines in config dhcp file to:
```
option root-path "/opt/ltsp/amd64";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/amd64/pxelinux.0";
    } else {
        filename "/ltsp/images/amd64.img";
    }
}
```
But it still doesn't want to boot the thin client. How do I solve this?
Btw, I've tried it on 10.04 server beta and still the same problem.

---

### Post by ene_dene on 2010-04-02
I have found the problem, but not the solution. My ufw firewall was blocking the connection. Now I need to know which port do I need to open so it can function with firewall turned on?

---

### Post by KB1JWQ on 2010-04-03
TFTP works over UDP port 69.

---

### Post by ene_dene on 2010-04-05
> **KB1JWQ said:**
> TFTP works over UDP port 69.
Thanks, that works.

---

