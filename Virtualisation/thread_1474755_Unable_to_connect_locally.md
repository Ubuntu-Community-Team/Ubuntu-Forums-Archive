---
title: "Unable to connect locally"
date: 2010-05-06
forum: Virtualisation
---

### Post by paul.willis on 2010-05-06
I'm running Ubuntu 8.04.4 LTS guest on VMWare Fusion 3.0.2 on Mac OS X 10.4.11 Server. I have networking set to Bridged and the Ubuntu server has it's own public IP address. Apache is running on the Ubuntu server with a default page

I am able to surf into, ping, telnet, curl to the Ubuntu server via either the IP or the hostname from the host OS X system or from any other external machine.

I can also ping, telnet, curl etc from the Ubuntu server to external IPs and hostnames

but...

If I try ping, telnet, curl from the Ubuntu machine to its own IP address or hostname it just times out.

i've disabled the firewall on both the Ubuntu guest server and the Mac OSX host but it made no difference.

I'm sure it's just a simple configuration issue but I'm stuck as to what or where to look, any ideas?

---

