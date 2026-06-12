---
title: "OpenVPN certain traffic"
date: 2012-01-16
forum: Server Platforms
---

### Post by CyberCowboy on 2012-01-16
Here's a basic layout of what I have:

Remote server in Chicago is mail server, backup server and public facing
FTP server due to higher bandwidth.

I want the remote server to VPN back to a local server so that on the
local network it is addressable on the internal network (say it has an
address of 10.8.0.6) and then nightly a script will go and rsync data from
local server to the remote.

The problem right now is that if I open the VPN connection external
connections stop, so no one can FTP into the box, and SMTP connections (as
well as webmail) get refused because the system is no longer listening on
the external address

If it matters the server is Ubuntu 10.04.3 LTS

---

### Post by SeijiSensei on 2012-01-16
> **CyberCowboy said:**
> I want the remote server to VPN back to a local server so that on the
local network it is addressable on the internal network (say it has an address of 10.8.0.6) and then nightly a script will go and rsync data from
local server to the remote.

Don't give the remote an address in your local subnet.  Just use a different address space and set up the tunnel between the remote server and the local backup device.

---

### Post by CyberCowboy on 2012-01-16
ah that makes sense.  THanks.

---

