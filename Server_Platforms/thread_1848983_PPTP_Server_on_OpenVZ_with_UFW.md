---
title: "PPTP Server on OpenVZ with UFW"
date: 2011-09-23
forum: Server Platforms
---

### Post by fogNL on 2011-09-23
This has been driving me nuts for a while, and I can't seem to find accurate information that will help me.

I got a PPTP server running on a Ubuntu 10.04 VPS.  That seems to be working fine, but I can't seem to get UFW to co-operate.  With UFW enabled, trying to connect to the PPTP just holds on "Verifying username/password", as soon as I drop the UFW firewall, it goes through fine and all is well.

On the firewall, I've enabled port 1723/tcp.

In /etc/default/ufw I have "DEFAULT_FORWARD_POLICY" set to "ACCEPT".  And have net/ipv4/ip_forward=1 in my sysctl.conf.

I think my problem lies in /etc/ufw/before.rules , I just can't seem to get the proper rules.  Just say my ip is static "142.163.5.121" (example) and I have the pptpd set to distribute addresses of 10.1.0.1-100 , what do I put in my /etc/ufw/before.rules ?  Oh, my network interface is venet0 and a venet0:0 (the venet0:0 has my public ip address while the venet0 has a 127.0.0.2 address)

Thanks for any help.

---

### Post by fogNL on 2011-09-26
After a few days, I've still had no luck in getting this going.  Attempting to login from Windows 7 with UFW enabled on the server causes the login to stick on "Verifying Username and Password"

---

