---
title: "Ufw to protect my vps"
date: 2018-12-17
forum: Server Platforms
---

### Post by atux on 2018-12-17
Hi. I have a vps running Ubuntu 18.04 server and i would like to protect it. I have installed ufw and opened only a port for ssh in different port. So far so good. I wod like to log all bogus and attacks. Once those IPs logged, then add them in a ban list. The only portsnthat will be open are 223 (ssh) and 1196(openssh). I would like to allow only 3 concurrent connections at a time.
Alli know is how to open a port, remove a rule. Nothing else. May i have some help please?

---

### Post by TheFu on 2018-12-18
**fail2ban**.  You'll need to configure it for the alternate tcp port.

If you know where all the ssh connections will be coming from, you can block the world and put in some exceptions just for those IPs.

BTW, I would suggest that very high ports be used, definitely nothing in the first 10,000 which are commonly scanned.  Since you'll just setup the port in your ~/.ssh/config file anyways, you'll never need to actually know the port going forward. Every tool that supports ssh knows to look in that file for ssh connection settings.

For limiting the number of connections, I'd suggest checking out the sshd_config file and the manpage for it.  3 seems like a very low number if something bad happens.

ufw is a very simple tool and of limited use for complex firewall control.  To better control the kernel firewall, iptables will be needed, or a new tool, like firewalld.  I'm not sure which is available for 18.04 by default.  I do know that you can remove ufw + iptables and install firewalld, if that is easier for your needs.

---

### Post by slickymaster on 2018-12-18
*Thread moved to **Server Platforms**.*

---

