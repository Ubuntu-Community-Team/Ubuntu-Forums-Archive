---
title: "NFS setup"
date: 2009-08-13
forum: Server Platforms
---

### Post by Amatøren on 2009-08-13
Hi, new on this forum and neew some help.

I'm settig ut at ubuntu server 9.04 and samba is OK (got files on Windows PC's!), but can't get NFS up and running. I got this msg:

 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [fail] 

I trieed: **[1. setup]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")** and a **[2. setup]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html")**.

If I run: **sudo rpcinfo -p**
I get: **rpcinfo: can't contact portmapper: RPC: Remote system error - Connection refused**


Any help please:confused:

---

### Post by jocampo on 2009-08-13
Make sure portmapper service is up and running...

---

### Post by alastair on 2009-08-13
> **Amatøren said:**
> 
I get: **rpcinfo: can't contact portmapper: RPC: Remote system error - Connection refused**

Any help please:confused:

That's odd.

Do you have "nfs-common" installed? Check and install if not.

---

### Post by Iowan on 2009-08-13
[This]("http://ubuntuforums.org/showthread.php?t=249889") one provide any new hints?

---

### Post by Amatøren on 2009-08-14
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=249889") one provide any new hints?

Yes - and thank for all help but still a BIG problem!

Portmapper up and running.
nfs-common is installed.

I have ubuntu desktop (GUI) installed for easier working on the server.

From my files

/etc/default/portmap

NOTE: I have an extra 4 port LAN card in the server but not used before all is up and running and I put it in my "server" room.

```

# Portmap configuration file
#
# Note: if you manually edit this configuration file,
# portmap configuration scripts will avoid modifying it
# (for example, by running 'dpkg-reconfigure portmap').

# If you want portmap to listen only to the loopback
# interface, uncomment the following line (it will be
# uncommented automatically if you configure this
# through debconf).
#OPTIONS="-i 127.0.0.1"
OPTIONS="-i 192.0.0.150"
#OPTIONS="-i 192.0.0.151"
#OPTIONS="-i 192.0.0.152"
#OPTIONS="-i 192.0.0.153"
#OPTIONS="-i 192.0.0.154"

```/etc/exports

```

# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/media/usb.intern/epg       192.0.0.0/24(rw,no_root_squash,sync,no_subtree_check)
/media/usb.intern/nfs-share 192.0.0.0/24(rw,no_root_squash,sync,no_subtree_check)

```My /etc/network/interfaces (use only eth0 at testing):

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (motherboard)
auto eth0
iface eth0 inet static
address 192.0.0.150
netmask 255.255.255.0
network 192.0.0.0
broadcast 192.0.0.255
gateway 192.0.0.138

# The 4 port lan card
auto eth1
iface eth1 inet static
address 192.0.0.151
network 192.0.0.0
netmask 255.255.255
broadcast 192.0.0.255

auto eth2
iface eth2 inet static
address 192.0.0.152
network 192.0.0.0
netmask 255.255.255.0
broadcast 192.0.0.255

auto eth3
iface eth3 inet static
address 192.0.0.153
network 192.0.0.0
netmask 255.255.255.0
broadcast 192.0.0.255

auto eth4
iface eth4 inet static
address 192.0.0.154
network 192.0.0.0
netmask 255.255.255.0
broadcast 192.0.0.255

```Any more files to check?
:-?

---

### Post by eigma on 2009-08-25
In Linux the interfaces "lo" and "eth0" are distinct. If an application is listening on eth0 only, then it is not listening on lo. In terms of IP addresses, if you're listening on 192.0.0.150 only, you're not listening on 127.0.0.1.

When rpcinfo talks to portmap, it likely uses localhost, but portmap is not listening there, hence the "Connection refused" error.

This still doesn't explain why *other* machines can't seem to connect. In fact, they can connect to portmap, but no daemon has registered itself. RPC registration also uses "localhost"; there are probably "Connection refused" errors in your boot log.

Unfortunately since portmap doesn't support multiple "-i" options, as far as I can tell, the only option is to allow portmap to listen on all interfaces and enforce your policy with iptables.

This should get you started:
iptables -A INPUT -s ! 192.0.0.0/24 -p udp --dport 111 -j DROP

---

