---
title: "Cannot ssh Virtualbox from Ubuntu 20.04"
date: 2021-04-26
forum: Virtualisation
---

### Post by kg82 on 2021-04-26
Hello, I have been trying to make this work, I have looked at recommendations online around ufw and iptables rules, but unfortunately none worked. 

I do not know a lot about network settings, but here is the issue:

I have an Oracle Virtualbox 6.1 on my Ubuntu 20.04 pc and I cannot ssh to that Virtualbox from the pc. The distribution on the Virtualbox is Debian 9 (Stretch) and I have set-up 2 adaptors, one NAT and the second one as host-only. I can successfully ssh from the Virtualbox to the pc, but not from Ubuntu to the Virtualbox. When I try to ping the Virtualbox from the pc, I keep getting "icmp_seq=num Packet filtered" error.

I have exactly the same set-up on a laptop, i.e. Ubuntu 20.04 and Debian 9 Virtualbox sitting on the laptop, NAT and host-only adaptors, same WiFi connection and everything works fine.

Has anyone else come across something like this before and any suggestions please how to resolve it?

Many thanks!

---

### Post by TheFu on 2021-04-26
Use a bridged VM network connection.

---

### Post by kg82 on 2021-04-27
Hi, thanks, I tried this too (i.e. one NAT adaptor and one Bridged), but unfortunately it didn't work.

This time it doesn't seem to ping at all and I know for sure ssh is up and running on both ends.

---

### Post by slickymaster on 2021-04-27
*Thread moved to **Virtualisation**.*

---

### Post by &amp;KyT$0P# on 2021-04-27
How do you have networking set up in the guest OS?  Are you using NetworkManager in the guest?

Is the VM on your laptop an actual copy of the VM you're having trouble with, or is it just (supposed to be) set up the same?

---

### Post by TheFu on 2021-04-27
Any chance you can prove what is being claimed?
Seeing normal network troubleshooting commands and outputs would be helpful as well.
It is very difficult to be helpful with interpreted information.
**ssh -vvvv** would be very helpful too.

And please only have 1 NIC enabled at a time during troubleshooting.  Routing can get funky when multiple NICs are enabled.

---

### Post by ajgreeny on 2021-04-27
Just out of interest do you use the ***user@IP*** when using ssh to connect to another machine or do you use ***user@hostname*** or does it vary from machine to machine?

Are the machines all on the same LAN, ie connected to the same router?

---

### Post by SeijiSensei on 2021-04-28
First, I assume you're trying to ssh from the host's virtual IP to the VM's virtual IP, something like 10.8.x.y.

Any chance the firewall is enabled on the VM? 

You don't need two network interfaces. As TheFu says, this can only lead to trouble.  Create one adapter and set it to Bridged. Then the VM will receive an IP address in the same network as the host and should be visible to any machine on your network.

---

