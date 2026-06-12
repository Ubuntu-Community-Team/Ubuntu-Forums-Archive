---
title: "PXE booting troubles"
date: 2011-09-11
forum: Server Platforms
---

### Post by braunshedd on 2011-09-11
Hello!
I've been working on getting a working pxe boot setup and I must say, what a nightmare!
I've been working through a series of problems, but this one has me stuck.
I've been using etherboot as my pxe execution platform, and I always seem to get this error:
[IMG]https://lh5.googleusercontent.com/-IAy6QWTqNcI/TmzA1vnSyJI/AAAAAAAAAD8/Uj5JwvxOJwY/etherboot.png[/IMG]
I know that the tftp daemon is working, however, because when I remove the Image, I'll get a file not found error, and If i make the file non-executeable, it also gives and error for that. Here is a snapshot of wireshark output showing what data is traveling over the network:
[IMG]https://lh6.googleusercontent.com/-3tVbhxrA8Cc/TmzB9jGfEdI/AAAAAAAAAEI/cizLxvmVo8c/tshark.png[/IMG]
Any help would be appreciated

---

### Post by hydruid on 2011-09-11
We need much more information:

Network: DHCP Server IP, copy of dhcp config, Default Gateway IP

Server: OS, IP

Pxe: What image are you using on the server, custom? ltsp?

---

### Post by braunshedd on 2011-09-11
> **hydruid said:**
> We need much more information:

Network: DHCP Server IP, copy of dhcp config, Default Gateway IP

Server: OS, IP

Pxe: What image are you using on the server, custom? ltsp?

DHCP, server, gateway ip: 192.168.0.1
OS is a debootstrap version of debian. Nothing fancy
DHCPD.conf
```
### PART 1
# General options
INTERFACES="eth1";
option dhcp-max-message-size 2048;
use-host-decl-names on;
### PART 2
option domain-name "mycluster.home";
option domain-name-servers 192.168.0.1;
option ntp-servers ntp.network.net;

### PART 3
subnet 192.168.0.0 netmask 255.255.255.0 {
 option routers 192.168.0.1;
 option broadcast-address 192.168.0.255;
 # Define the first and last IP address to be authorized
 range 192.168.0.5 192.168.0.100;
 # This set up the node name to « krgnodeXX » with XX the id of the node (ip-address based).
 send host-name = concat("krgnode", binary-to-ascii(10, 8, ".", substring(leased-address, 3, 1)));
 # If you want to limit which boxes are using kerrighed, use something like this :
 # host ssi1 { fixed-address 192.168.0.101; hardware ethernet xx:xx:xx:xx:xx:xx; 
}

### PART 4
next-server 192.168.0.1;
filename "/srv/tftp/pxelinux.0";
#server-name "192.168.0.1";
option root-path "/NFSROOT/kerrighed/";

```
TFTPD-HPA:
```

INTERFACES="eth1"
RUN_DAEMON="yes"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/tftp"
TFTP_ADDRESS="192.168.0.1:69"
TFTP_OPTIONS="-l -vv"

```

---

### Post by hydruid on 2011-09-11
You failed to give the required information, I am unable to assist further

---

### Post by braunshedd on 2011-09-12
> **hydruid said:**
> You failed to give the required information, I am unable to assist further
I'm sorry, but what did I happen to miss?

---

