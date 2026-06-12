---
title: "IPSec and OpenSwan Install Issue"
date: 2006-07-31
forum: Server Platforms
---

### Post by Maddog Battie on 2006-07-31
I've been trying to install Openswan on Dapper server so as to be able to connect to it and its local network from an XP machine. Unfortunately, the install process didn't work as expected.
[FONT="Courier New"]
$ sudo apt-get install openswan
$ sudo ipsec verify[/FONT]

gives

[FONT="Courier New"]Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.4.4/K2.6.15-23-server (netkey)
Checking for IPsec support in kernel                            [OK]
Checking for RSA private key (/etc/ipsec.secrets)               [FAILED]
ipsec showhostkey: no default key in "/etc/ipsec.secrets"
Checking that pluto is running                                  [OK]
Two or more interfaces found, checking IP forwarding            [FAILED]
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]
Checking for 'setkey' command for NETKEY IPsec stack support    [OK]
Opportunistic Encryption Support                                [DISABLED][/FONT]

with the RSA private key [FAILED] being the problem. Now, the install process has chucked the following into /etc/ipsec.secrets

[FONT="Courier New"]# RCSID $Id: ipsec.secrets.proto,v 1.3.6.1 2005/09/28 13:59:14 paul Exp $
# This file holds shared secrets or RSA private keys for inter-Pluto
# authentication.  See ipsec_pluto(8) manpage, and HTML documentation.

# RSA private key for this host, authenticating it to any other host
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS,
# or configuration of other implementations, can be extracted conveniently
# with "ipsec showhostkey".
: RSA /etc/ipsec.d/private/sunbeamKey.pem
[/FONT]

and /etc/ipsec.d/private/sunbeamKey.pem exists and appears to contain a suitable key but the above format of ipsec.secrets does not match the manual entry for ipsec.secrets. The external reference does not seem to be an option. Is this likely to be problem? If so what is a good way to fix it?

Thanks for any help MdB.

---

### Post by Maddog Battie on 2006-08-01
a bit more info.

[FONT="Courier New"]$ sudo ipsec showhostkey --left
ipsec showhostkey: no default key in "/etc/ipsec.secrets"
[/FONT]
(fails not too surprisingly after the fail in the ipsec verify)

my guess is there is something wrong in the setup process. I'm going to have an attempt to see if I can work this out myself but if anyone fancies giving me any hints as to how to go about this, then this would be most welcome.

---

