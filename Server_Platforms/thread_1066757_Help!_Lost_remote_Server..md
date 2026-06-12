---
title: "Help! Lost remote Server."
date: 2009-02-11
forum: Server Platforms
---

### Post by spynappels on 2009-02-11
Hi guys,

   I've just lost all contact with a remote server. Someone is on their way to connect a monitor and keyboard, but is there anything you can think of which is causing the server to be completely unresponsive, even after multiple reboots?

 I cannot even ping it from a machine on the local LAN.

  Any ideas?

  Edit: Server is running a LAMP + SSH + Samba Webapp server. Static Local IP. Port forwarded from external IP. No issues before this.

---

### Post by koenn on 2009-02-11
> **spynappels said:**
> 

 I cannot even ping it from a machine on the local LAN.
Any ideas?

network problem (NIC, cable, switch, NIC configuration, blocking port on the switch, ...)

---

### Post by Masuran on 2009-02-11
A messed up iptables configuration can do this. For example a rule that drops all input.

---

### Post by dca on 2009-02-11
If you're standing next to the server and it looks like the lights are flashing then I would think it's a faulty NIC.  How is the machine being rebooted?

---

