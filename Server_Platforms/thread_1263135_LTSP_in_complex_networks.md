---
title: "LTSP in complex networks"
date: 2009-09-10
forum: Server Platforms
---

### Post by glauco.b on 2009-09-10
Hello

I am in the need to set up an LTSP environment (jaunty) in a complex network

The topology needs to have the LTSP interface sitting in a network and the clients sitting in a completely different network (possibly over the internet...).

The topology is

```

------------                  ---------                ---------
|LTSP Server|---192.168.0.1---|routing|---172.16.0.1---|clients|
------------                  ---------                ---------

```

I solved the problem of distributing addresses using DHCP relays, but eventually I ran into a very strange problem, that I really wasn't able to solve:
- At every thin client boot everything works until the kernel and initrd boot off the TFTP folder
- When it comes to load the root FS image from nbd, the thin client is able to open the TCP connection to port 2000, but then the server simply does not send the image (it doesn't give any errors or messages, it simply does NOT send anything, leaving the client in the state of "Negotiating")
- If the thin client is on the same subnet as the LTSP server, everything works fine

It should not be a network problem, since the TCP connection to port 2000 is successful and the syslog says the server correctly accepted the nbd request and started serving the image (which, actually, is not being served at all...).

Is there any limitation in using LTSP/nbd server and client in different networks? Does LTSP make some kind of subtle and hidden configuration to limit this?  :confused:

thanks

---

### Post by glauco.b on 2009-09-11
Ok, solved the problem. I'm posting the solution here because it is a very subtle issue.

The configuration I was trying to use had the thin clients in a subnet and the LTSP server in another, with lots of layer 3 network devices between

The LTSP client boot process uses TFTP (udp port 69) to download the initial ramdisk image and then mounts the root file system via NBD (configured to listen on TCP port 2000).

It happens that port 2000 is registered to the cisco-sccp protocol (Skinny), the VoIP protocol used by Cisco IP phones. LTSP should NOT have used this registered port and instead chosen an upper port in the range 32000-64000, which are free.

Unfortunately, the layer 3 stuff my traffic was flowing through, also contained a Cisco ASA firewall module. The ASA is configured with some fixup rules by default. The fixup rules, in Cisco jargon, are used to ensure the traffic between two TCP/UDP ports contains the application-layer protocol that is supposed to be used. The firewall looks inside the TCP session and, if the content does not correspond to the expected protocol, it drops the packets.

Needless to say, the ASA has fixup rules for sccp. Obviously, the NBD protocol is NOT sccp and thus the ASA firewall dropped all the traffic.

I simply did the following:
- changed the default port of the NBD daemon (in  /etc/inetd.conf) to a high number above 32000 
- changed the corresponding port in the client image (it is in /opt/ltsp/i386/usr/share/initramfs-tools/scripts/ltsp-nbd) to match the previous
- ran update-initramfs -u from the chroot
- ran ltsp-update-image/kernels

and everything started working

BTW: choosing a lower registered TCP port for the NBD session by default is really a poor design choice :mad:

---

