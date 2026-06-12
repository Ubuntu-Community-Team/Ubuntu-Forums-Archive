---
title: "How to determine how a packet gets through UFW?"
date: 2011-07-25
forum: Security
---

### Post by robolange on 2011-07-25
(EDIT: How to trace iptables rule usage is solved in post # 2.  Why you can't use iptables to filter DHCP traffic is explained in post # 5.  How to filter DHCP traffic is solved in post # 6.)

What, if any, are the tools or techniques to determine how a packet navigates through the UFW/iptables rules?

I ask this because I have a UFW configuration that is allowing DHCP requests through, but I cannot figure out **why** the requests are getting through.

The machine is a NAT/router/server bridging my local network with the Internet.  I run a dhcpd instance that listens on eth1, and the Internet is connected to eth0.  Naturally, I want to allow DHCP request packets from eth1.  However, while auditing my firewall configuration, I discovered that I never added a rule to allow this, and from my reading of the rules, it should not happen.

I attached my iptables rules.

When I run wireshark and connect a computer to my network, I see a packet come into eth1 with source address 0.0.0.0:68 to destination 255.255.255.255:67.

From my reading of the iptables rules, it should trigger:

INPUT: line 5 to ufw-before-logging-input
ufw-before-logging-input: fall through back to INPUT
INPUT: line 6 to ufw-before-input
ufw-before-input: line 11 to ufw-not-local
ufw-not-local: line 3 return to ufw-before-input
ufw-before-input: line 13 to ufw-user-input
ufw-user-input: fall through back to ufw-before-input
ufw-before-input: fall through back to INPUT
INPUT: line 7 to ufw-after-input
ufw-after-input: line 5 to ufw-skip-to-policy-input
ufw-skip-to-policy-input: line 1 DROP

Note: ufw-before-input line 10 does **not** trigger because the source port is 68 and the destination port is 67.

So, from my understanding of these rules, a DHCP request packet (not from interface virbr0) should be dropped.  Obviously, that is not happening, since my server is seeing the packet and assigning an IP address to the client.

So, first, if anyone can explain why these packets are making it through the firewall, I would be grateful.  Furthermore, if anyone can point me to any tools that would highlight a packet's path through the UFW/iptables rules, I would be even more grateful.

---

### Post by robolange on 2011-07-25
Zoredache from serverfault.com had the answer.

[http://serverfault.com/questions/122157/debugger-for-iptables/126079#126079](http://serverfault.com/questions/122157/debugger-for-iptables/126079#126079)

In short, you can put in lines in iptables to trace the route of matching packets through the rules tables.  In my case, the following lines worked:

```
sudo iptables -t raw -A PREROUTING -p udp --destination 255.255.255.255 --dport bootps -j TRACE
sudo iptables -t raw -A OUTPUT -p udp --destination 255.255.255.255 --dport bootps -j TRACE
```

---

### Post by robolange on 2011-07-25
Attached are two excerpts from syslog with traces.  For the first, I did the trace using my normal ufw rules.

In the syslog, it shows that dhcpd processed the DHCPDISCOVER discover packet before iptables did, but I chalked that up to the uncertainty of two different processes writing to the log file at nearly the same time...

Then I looked at the trace results.  The packet triggered exactly the rules I thought it would, including terminating at a DROP rule.

To confirm this, I manually added the following rule to the beginning of the INPUT chain, just to be perfectly crystal clear:

```
sudo iptables -I INPUT 1 -p udp --dport bootps -j DROP
```

Since it was a new rule, it had a 0 packet counter.

I then re-connected my client box to the network and got the second trace.  As you can see, it terminates at the first rule of INPUT (the DROP rule) ...

... and then dhcpd promptly sees and responds to the packet!!!

To confirm, I looked at the iptables counters again and the first rule of INPUT (the DROP rule) had incremented by 1 packet.

So, iptables is dropping the traffic, but dhcpd is getting it anyway. Is it possible for a program to see IP traffic before iptables processes it?!  Wouldn't that be a security vulnerability? What is going on here?

---

### Post by robolange on 2011-07-25
I filed a bug with the iptables/netfilter people about this issue:

[http://bugzilla.netfilter.org/show_bug.cgi?id=730](http://bugzilla.netfilter.org/show_bug.cgi?id=730)

---

### Post by robolange on 2011-07-27
Looks like it is not a bug with ufw or iptables.

Per Mark Andrews of isc.org:

"DHCP uses packet filters and these tie into the IP stack before the
firewall."

A different topic, but the explanation is also relevant here:

[https://lists.isc.org/pipermail/dhcp-users/2010-January/010723.html](https://lists.isc.org/pipermail/dhcp-users/2010-January/010723.html)

Apparently dhcpd uses raw sockets to maximize its robustness and reliability in dealing with DHCP. Also, it uses as a fallback a UDP socket, and it was the packets to this fallback that iptables was dropping.

So, if your DHCP server operates on the same machine as your firewall, don't expect your firewall to stop traffic to it.

---

### Post by robolange on 2011-08-01
If you want to filter raw sockets, like those used by DHCP, on the same machine as the receiving process, you will need to use ebtables instead of iptables to do the filtering. (You can use iptables and ebtables at the same time, and you should continue using iptables to filter anything except raw sockets.)

ebtables is the ethernet bridge firewall ruleset.  Support for it is installed in the Ubuntu kernel by default, but you will need to install the following extra packages: bridge-utils ebtables.

ebtables can only filter ethernet bridge interfaces, not regular network interfaces.  Therefore, to use it you will need to make a bridge interface containing just the network interface(s) you want to filter. Caution: by making a network interface into a bridge interface, you will lose the ability to manage it using the GUI Network Manager.

I assume that your bridge interface (henceforth, br0) will contain only one network interface (in this tutorial, eth1) and the network IP you will use is 192.168.0.1.  Modify the instructions accordingly if you want a different configuration.

First, delete any configuration you may have in Network Manager for eth1.  If you do not do this, Network Manager may attempt to "help" by restoring eth1's settings, thus breaking your manual setup.

Once that is done, add the following to /etc/network/interfaces:

```
auto br0
iface br0 inet static
  address 192.168.0.1
  netmask 255.255.255.0
  pre-up ifconfig eth1 down
  pre-up brctl addbr br0
  pre-up brctl addif br0 eth1
  pre-up ifconfig eth1 0.0.0.0
  post-down ifconfig eth1 down
  post-down ifconfig br0 down
  post-down brctl delif br0 eth1
  post-down brctl delbr br0
```

Restart all networking (Network Manager and networking).  It might be easier to just reboot to make sure everything stuck.  ifconfig should show br0 with 192.168.0.1 and eth1 with no IPv4 address.  `route -n` should show the route for 192.168.0.0/24 through br0 and nothing through eth1.

In the case of dhcpd, you will need to modify /etc/default/isc-dhcp-server to reference br0 instead of eth1.  Any other references to eth1 you may have in configuration files (other than /etc/network/interfaces and udev) will probably also need to be changed to br0.  Restart any networking services so modified.  (Note, br0 comes up later during boot than Network Manager-managed interfaces, so you may have to modify init scripts of some services to wait for it to come up.)

Now, you can list ebtables rules using:

```
sudo ebtables -t filter -L
```

Note that it's a default accept policy.  This is probably what you want; let UFW/iptables do the heavy lifting for everything but raw sockets.

Now, add a rule to drop incoming DHCP requests:

```
sudo ebtables -t filter -A INPUT -p IPv4 --ip-protocol udp --ip-destination-port 67 -j DROP
```

Now list ebtables rules again and see that the INPUT chain has a rule to drop DHCP requests.

Since ebtables is not supported by default in Ubuntu, there are no fancy init scripts to restore ebtables rules on reboot.  You will have to make your own, but it's a simple matter of executing the above line after the bridge interface comes up.

---

### Post by The Cog on 2011-08-02
Nice monologue. Thanks for posting the explanation.

---

### Post by trungvkvk on 2011-08-04
[http://ubuntuforums.org/showthread.php?p=11004029](http://ubuntuforums.org/showthread.php?p=11004029)
sorry. I am a newbie to use ubuntu.
 hopefully I'll get experience from people.
 What people experience when using ubuntu addiction please share.
 thanks.

---

