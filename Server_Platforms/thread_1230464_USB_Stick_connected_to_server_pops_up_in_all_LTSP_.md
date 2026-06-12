---
title: "USB Stick connected to server pops up in all LTSP clients"
date: 2009-08-03
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-08-03
Dear all,

I am testing LTSP on Ubuntu Server 9.04 - 64-bit + ubuntu desktop 9.04
on a HP XW4600 workstation with 2GB RAM.

dpkg -l | grep ltsp
ii  ltsp-server                               5.1.65-0ubuntu2
                Basic LTSP server environment
ii  ltsp-server-standalone                    5.1.65-0ubuntu2
                Complete LTSP server environment
ii  ltspfs                                    0.5.10-0ubuntu1
                Fuse based remote filesystem for LTSP thin client

# Global defaults for all clients
# if you refer to the local server, just use the
# "server" keyword as value
# see lts_parameters.txt for valid values
################
[default]
   X_COLOR_DEPTH=16
   LOCALDEV=True
   SOUND=True
   NBD_SWAP=True
   SYSLOG_HOST=server
   #XKBLAYOUT=de
   #LDM_DEBUG=no


I am having problems mounting a 80GB NTFS USB drive on LTSP client.But it mounts on the server without any problems. 

Also, if i plug in any USB drive on the server, this comes up in all the
LTSP clients and they are in write mode which means they can view and
change the contents of the drive! how can i stop this from appearing in all the LTSP client machines.
I removed the "Access external storage devices automatically"  in User Privileges but it still appears. 

And, the LTSP client boots really slow, it takes more than a minute which was not the case with earlier version of LTSP and hardy. Infact, the server with Samba, LTSP, DHCP boots faster.

Kindly help
Avinash

---

### Post by Avinash.Rao on 2009-08-04
:confused:

---

