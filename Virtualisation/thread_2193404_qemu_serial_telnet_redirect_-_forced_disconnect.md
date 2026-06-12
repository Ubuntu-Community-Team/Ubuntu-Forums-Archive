---
title: "qemu serial telnet redirect - forced disconnect ?"
date: 2013-12-12
forum: Virtualisation
---

### Post by peter.debruyne on 2013-12-12
Hi,

I am using some qemu virtual machines on Ubuntu 12.04LTS, the virtual machines have their serial port mapped and available through a telnet server port (with the -serial telnet::9001,server,nowait  option)

This works fine for remote users to get access to the terminal.

However, this is a single user session, so when another tries to connect to the same port, it does not get any response.

* It is possible to show some kind of  'port already in use' message for the addtional connections ?
* In case a user is not actively using the session, I would need a mechanism to clear/reset the active telnet session to this serial port. Does anyone know how I can do a forced disconnect for a telnet session to the serial mapped port ?
* Would it be possible to make this a multi-user session, so the output of the serial could be shown on multiple client tcp sessions ? (similar to the fuctionality of some console servers)

Thank you ,
Peter.

---

