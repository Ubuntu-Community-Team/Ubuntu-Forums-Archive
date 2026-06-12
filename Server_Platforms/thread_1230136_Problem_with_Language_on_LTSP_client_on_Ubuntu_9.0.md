---
title: "Problem with Language on LTSP client on Ubuntu 9.04"
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
                Fuse based remote filesystem for LTSP thin c

After installing LTSP, i couldnot find lts.conf file under
/var/lib/tftboot/ltsp/i386/ directory, instead it was in
/opt/ltsp/i386/usr/share/doc/ltsp-client-core/examples/lts.conf and
/opt/ltsp/i386/etc/lts.conf

The lts.conf file under /var directory just Donot use this file, it
has been moved to /var/lib/tftboot/ltsp/i386/ . but its not there or i
guess i have to create it.I copied the lts.conf file from
/opt/ltsp/i386/usr/share/doc/ltsp-client-core/examples/ to
/var/lib/tftboot/ltsp/i386/ and it looks something like this.

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

The ltsp client boots, but the language is in German So, i commented the
#XKBLAYOUT=de to disable the option and rebooted the client but i am
getting the same thing. Also, the client takes more time to boot than
normal.

can anybody help me
Avinash

---

