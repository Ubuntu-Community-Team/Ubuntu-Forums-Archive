---
title: "Web Server in Virtualbox"
date: 2013-06-13
forum: Virtualisation
---

### Post by KineticSq on 2013-06-13
Hi everyone. I've been having some issues with a webserver (apache2) running on Ubuntu 12.04 Server in VirtualBox.
My network settings are
(1) Bridged
(2) NAT
for the VM.

My Virtual Machine can be accessed from internally (192.168.x.x), and I have it setup to port forward. When I try to access the server from externally it just hangs waiting and never loads. This has been confirmed by multiple friends.
Can anyone here please help me? I hope I've provided enough detail, ask if you need more.

Also, it's not my router. Forwarding port 80 has worked on another server, but not in VirtualBox.

---

### Post by lmarmisa on 2013-06-13
You should configure your network settings as bridged (not NAT). According to your comments, this seems to work properly.

You can check what is your local IP address with this command:

> 
ifconfig

Use this IP address for port fordwarding on router.

If you are using DHCP for local IP address negotiation, the router could assign different IP addresses to your VM and this could be a problem. Try to use a static local IP address for your VM. Do not assign a static IP to your VM belonging to the DHCP pool defined in the router. Typically lowest local IP addresses (for example, 192.168.1.2, 192.168.2.4, 192.168.3.5, etc) are used for server static IP addresses.

Best regards,

Luis

---

