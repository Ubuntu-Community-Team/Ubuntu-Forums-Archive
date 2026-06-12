---
title: "OpenVPN on 8.04 LTS"
date: 2010-10-30
forum: Security
---

### Post by MicroBlueChip on 2010-10-30
Hi all,

I have been searching for an answer to this for the last 2 weeks.

I have a 1&1 dedicated server which uses Ubuntu 8.04 LTS.

The OpenVPN package in the repository is 2.1rc7 which seems pretty old as the current stable version is 2.1.3.

Does anyone know if I can easily update this or if I can install a later deb file.

I tried a deb file from a later release but other dependencies were also out of date such as OpenSSL and LZO.

Thanks.
MicroBlueChip

---

### Post by OpSecShellshock on 2010-10-30
If other dependencies are out of date then those should be updated as well. I'd suggest just checking for updates in general and then applying them all. 8.04 is still supported at the moment, so the repositories should be good. It should be reaching end of life in 6 months, though, and will no longer be supported (not pressing, just something to keep in mind). Software should be updated regularly. If the server is actually owned by the hosting company, I'd think it would be their responsibility to keep it up to date, but you'd have to read over your service agreement to know.

---

### Post by spynappels on 2010-11-01
You could always copy all your conf files and keys etc to a safe location and start from scratch, using ```
apt-get install openvpn
``` and then update the dependencies using ```
apt-get -f install
``` and then reuse all your conf files and key.

In a default install, it is always a good idea to copy the easy-rsa folder away from it's default location to somewhere like the /etc/openvpn folder to avoid your settings and keys being overwritten during an upgrade.

Have you also tried ```
apt-get update
``` followed by ```
apt-get upgrade
``` to see if your openvpn is updated?

---

