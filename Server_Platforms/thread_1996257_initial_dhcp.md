---
title: "initial dhcp"
date: 2012-06-04
forum: Server Platforms
---

### Post by R. M. Frank on 2012-06-04
Hi,

I'm wandering if the following is possible using standard installations (I know one could program it!):

For my servers, I'd like to use dhcp to get an initial setup after booting, then to set the information received as static setup once the system has successfully connected to the internet. All following boots would then first check if the information obtained by dhcp differs to the information stored. If not, or if dhcp doesn't respond, it would simply use the information last obtained. If there was a change, this would again be set as new static information.

Thanks for any insights.
-Robert

---

### Post by volkswagner on 2012-06-04
I'm having a difficult time understanding what you are trying to accomplish.

If you have a static ip setup either by script writing to /etc/network/interfaces, the ip should not change by definition of static ip.

When you mention initial setup, are you talking about installing the OS, or just a cold boot?

---

### Post by craigp84 on 2012-06-04
> **R. M. Frank said:**
> Hi,
I'd like to use dhcp to get an initial setup after booting, then to set the information received as static setup once the system has successfully connected to the internet. All following boots would then first check if the information obtained by dhcp differs to the information stored. If not, or if dhcp doesn't respond, it would simply use the information last obtained. If there was a change, this would again be set as new static information.


Hello, what you describe is very close to a common deployment pattern. The pattern nominally looks like:

1. All servers set in their bios to boot from network (netboot), failing back to local disk if network boot is not possible. That is, the kernel can be loaded from a tftpd server as directed by DHCP.

2. Kernel to be loaded via netboot is chosen by MAC address - the netbooting server looks on the tftpd server for the kernel based on it's mac address. On the tftpd server these files named by mac address are just symlinks to a standard boot kernel normally (equally they could just not exist as the servers will then fail to netboot and so will boot from disk instead). However, in the event a server is new or is to be rebuilt, the symlink will be pointed to the "installer" kernel. Now when that server is first powered on, or is rebooted, it will go through an unattended installation process (e.g. kickstart).

Implementing the pattern is straightforward - just install dhcpd and tftpd and configure following the above recipe. However if you get stuck following the conf files or anything, just ping back here.

Hope this helps

---

### Post by R. M. Frank on 2012-06-04
Ok, I wasn't completely clear:

I'm not referring to the second scenario, where we use a network boot, and I know about the static IP addresses. 

What I am asking for, is something inbetween pure dhcp (what we are doning now) and pure static IP addresses.

I'd lilke to have the benefit of being able to change parameters (IP address, DNS, gateway, NETBIOS server, etc) dynamically, but don't want the system to fail booting in case the dhcp service is offline.
Note: changes need only take effekt on reboot, not during normal operation.

I am, of course, using dhcp with fixed leases (ethernet address to IP address mappings), but if the server is down (or stays down after a powerfailure), all other servers will fail. I'd want them to continue booting with the last saved values (just like apple clients do ...)

So what I'd need is an entry in 'interfaces' of the kind: 'dhcp once' or 'dhcp boot'.

-Robert

---

### Post by craigp84 on 2012-06-04
Ahh ok, lookup cfengine, puppet or chef - do these fit better with what you had in mind?

Describe configuration of your hosts, these take responsibility for ensuring that config description materialises on the hosts.

---

