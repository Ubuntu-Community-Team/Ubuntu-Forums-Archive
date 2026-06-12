---
title: "Dual Ethernet"
date: 2009-05-15
forum: Server Platforms
---

### Post by number65 on 2009-05-15
_**My Setup**_
I just completed a fresh install of Ubuntu Server edition on a system that has dual gigabit ethernet ports. One port has the T1 line coming into it with a static IP, and the other port goes out to the switch which connects all the other computers in the office.

_**My Question**_
How do I setup the one ethernet port's static IP and my ISPs DNS servers? And How do I setup the other ethernet card/port to act as a DHCP server for the other workstations in the office?

Thanks for your help guys!

---

### Post by NetworkGuy on 2009-05-15
I'm start you off by getting your interfaces correct.   Edit the /etc/network/interfaces file.   Change eth0 and eth1 accordingly.

**EDIT** Missed the DNS thing.   Edit /etc/resolv.conf to reflect the DNS servers your ISP wants you to use.

**EDIT #2**  Make sure you activate ufw.  Even though there are no open ports by default in Ubuntu, turn on your firewall if you are directly attaching to the Internet.  Also add a rule that will allow your internal network to see this server.  Without that, you won't be able to get DHCP working.

DHCP - Load the dhcp server from the repositories.  (This will also help to make sure your ISP interface is correct.)  Do a little bit of reading to determine how you want to configure the server and go from there.  If you still have issues understanding the dhcp.conf file, then post back.

Are you making some form of Internet proxy server??

---

### Post by number65 on 2009-05-15
The main use of the server is for simple DNS/DHCP and Samba, that is it.

I was looking through the guides for ufw, is there a way to allow a range of IPs and not just a specific IP?

Thanks!

---

### Post by NetworkGuy on 2009-05-15
You can specify a subnet mask I think by using the / option.   like 192.168.1.0/25 is the same as 255.255.255.128   The 25 specifies the number of bits in the subnet mask.

---

