---
title: "OpenVPN on ubuntu server, security concerns."
date: 2017-02-25
forum: Server Platforms
---

### Post by simonlap on 2017-02-25
Hi Guys!

So I installed openVPN using PiVPN on my Ubuntu server and it works like a charm but I have issues accessing the UDP port on some networks (university, Tim Horton's wifi, etc...). So I was wondering if it would be wise using another port (TCP) such as 80, 80880, 443 or 4443, but I am not quite sure if it would be safe or not.

Any thoughts on this?

Thanks!

---

### Post by SeijiSensei on 2017-02-25
I have point-to-point OpenVPN tunnels among a variety of machines.  All of them use arbitrary high ports like 54321.  Using such ports poses no more of a risk than using the default OpenVPN port of 1194.  

If your connections are not running as the root user, you won't be able to use ports below 1024.  

Some places block connections on "high" ports.  We do that at one site I work with.  No one can make a connection through the firewall from one port > 1023 to another > 1023.  That stops stuff like torrents, Skype, and other activities in the workplace while allowing well-known services like HTTP and HTTPS that operate on low-numbered, root-only ports.

---

### Post by simonlap on 2017-02-25
> **SeijiSensei said:**
> Some places block connections on "high" ports.  We do that at one site I work with.  No one can make a connection through the firewall from one port > 1023 to another > 1023.  That stops stuff like torrents, Skype, and other activities in the workplace while allowing well-known services like HTTP and HTTPS that operate on low-numbered, root-only ports.

So how do you with that place? My university blocks high ports for sure, as 1194 does not work and skype and other stuff is blocked as well. Any work around?

---

### Post by SeijiSensei on 2017-02-26
I can't answer that because of the Forum Code of Conduct: [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)  

"We do not support circumventing TOS, EULA, etc here."

You'll have to experiment on your own.

---

