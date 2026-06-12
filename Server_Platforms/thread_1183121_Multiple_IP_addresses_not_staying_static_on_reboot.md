---
title: "Multiple IP addresses not staying static on reboot"
date: 2009-06-09
forum: Server Platforms
---

### Post by csalsb on 2009-06-09
I have been searching on a way to deal withthis issue.  I am running 9.04 32 bit.  I have added my IP addresses to my interfaces file.  I restart networking and all my IP address work with no issues. When I reboot the server only my main IP address works.  i have to issue the restart networking command and all the ip's start to ping again.  What do I need to do to get all IP's to activate on boot?

---

### Post by windependence on 2009-06-09
Can you post your config files here?

-Tim

---

### Post by TwiceOver on 2009-06-09
sudo apt-get remove dhcp3-client

This has been an issue for a while now.  The DHCP client still wants to get an address and replace the static.  If they are going to be static, just remove the client.

---

### Post by LepeKaname on 2009-06-09
If you don't restart, kill also any "*dhcp*" process... It happened to me once.

---

### Post by csalsb on 2009-06-10
> **TwiceOver said:**
> sudo apt-get remove dhcp3-client

This has been an issue for a while now.  The DHCP client still wants to get an address and replace the static.  If they are going to be static, just remove the client.

That did the trick.  Thank you gor the assist

csalsb

---

