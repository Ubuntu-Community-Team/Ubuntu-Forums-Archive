---
title: "cant connect to update server"
date: 2010-01-24
forum: Server Platforms
---

### Post by Gregor386 on 2010-01-24
or for that matter to any server.

For instance:

ping [www.google.com](www.google.com)
works.

wget [www.google.com](www.google.com)
resolves but cant establish a connection

same thing happens with repository urls rendering updating imposible.



I'm running 9.10 server in vmware using a NAT connection. I chose LAMB and SSH server in the instalation, both of which work great now. I'd like to add a ftp and a samba server now, but cant.

I can ping from the host machine, connect via ssh, dyn dns does not work (router is configured properly).

Host machine is windows 7




Gregor

---

### Post by Gregor386 on 2010-01-24
Also, it seems I cant connect to my router via a bridged connection - even if I turn firewall in windows 7 off.

---

### Post by Pindaman on 2010-01-24
I have exactly the same problem.

With DHCP and default install iam able to ping, nslookup and host check urls. When i set it to static i still can. But as soon as i try to sudo apt-get update or something else using apt-get it cant resolve the URLs. I can still ping the urls manually.

Ive tried for over 4 hours to get this working. Here are the things ive tried:
- Tried VMware Server 2 instead of VMware Workstation
- Install Ubuntu Desktop instead of Server version, same problem
- Checked Host firewall
- Used OpenDNS servers in /etc/resolv.conf
- Disabled IPV6 in Grub bootloader
- Static and DHCP ip addresses

Ive been to the IRC channel, and have been greatly helped by user jrib. But the problem still persists.

Ps. I am using NAT because i would like to (i work at school and home all the time)

---

### Post by wxman on 2010-01-24
Ok this is just strange. I just came here looking for a reason my server stopped connecting to the Internet, and found this thread.

I connect to my server from work using a wireless broadband card, and VPN. Sometime Saturday afternoon, I noticed that if I was connected to my VPN, I couldn't connect to other web sites. If I disconnect the VPN the sites came back. Today I VPN'ed into the server, connected to a terminal through SSH and found I also can't connect to any updates. I tried pinging Google without any luck as well. I have a few Drupal sites on the server, and they can't connect with the Drupal update site. 

My family says the house is still on the Internet just like normal. I was able to ping Google directly from my primary firewall/router interface. Normally that would tell me that something blocking the server at the firewall, but nothing has changed.

---

### Post by wxman on 2010-01-24
Well I fixed it. I don't know why, but I tried two new nameservers in /etc/resolv.conf, the did a networking reset /etc/init.d/networking restart, and all is back to normal.

---

