---
title: "Connecting 2 VMs on same PC?"
date: 2011-01-26
forum: Virtualisation
---

### Post by shad0wman on 2011-01-26
Hello,

I am trying to simulate a client-server system where syslog messages are sent from the server to the client system. Currently, I have 2 VMs running on the same computer and I was wondering if it's possible to simulate the above-mentioned system?

From what I know both VMs are having the same IP address and I understand that I need to manually configure them with IP addresses in the same IP subnet. But I'm not sure how to do that. Can someone guide me in doing so?

- Noob to ubuntu :( -

---

### Post by dmizer on 2011-01-26
> **shad0wman said:**
> Hello,

I am trying to simulate a client-server system where syslog messages are sent from the server to the client system. Currently, I have 2 VMs running on the same computer and I was wondering if it's possible to simulate the above-mentioned system?

From what I know both VMs are having the same IP address and I understand that I need to manually configure them with IP addresses in the same IP subnet. But I'm not sure how to do that. Can someone guide me in doing so?

- Noob to ubuntu :( -

Should be a fairly simple thing to accomplish, and it shouldn't require static IP, but we'll need more information.

[LIST]
[*]What software are you using for your virtual server?
[*]What OS is hosting the virtual guests
[*]What OSs are running on your virtual guests?
[*]Is the virtual guest network adapter configured for host-only, NAT, bridged, or something else?
[/LIST]

PS, I've moved this to the virtualization section as this section will cover your particular problem better.

---

### Post by HermanAB on 2011-01-26
Two VMs is equivalent to two separate machines.

If your internet router is 192.168.1.1:

On Host
$ sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0
$ sudo route add default gw 192.168.1.1

On one VM:
$ sudo ifconfig eth0 192.168.1.11 netmask 255.255.255.0
$ sudo route add default gw 192.168.1.1

On other VM:
$ sudo ifconfig eth0 192.168.1.12 netmask 255.255.255.0
$ sudo route add default gw 192.168.1.1

Now they should all be able to communicate with each other.

The easiest way to make it work is to use the DHCP feature of your internet router.

---

### Post by Cheesehead on 2011-01-26
The easy way in VirtualBox:

1) Close both guest machines. You cannot adjust VM network settings while the VM is running.
2) Open the VM Virtualbox Manager
3) For each machine, go to Settings -> Network
       Look for the 'Attached to' setting. Change it from 'NAT' to 'Bridged Adapter'
It's that easy.

Now when you restart each VM, your network router will see each VM as a separate machine with different names and MAC addresses. Each will naturally request (and receive) a different IP address via DHCP.

Chapter 4 of the VirtualBox Manual is far superior at explaing what happens and why. If you use VirtualBox, that should really be your first stop.

---

### Post by JKyleOKC on 2011-01-26
If you're using VirtualBox to provide the VMs, be sure to change the Network Adapter setting of each of them from the default "NAT" to "Bridged" on order to be able to control the network addresses. The default setting makes it difficult for one VM to contact another, but when set to "Bridged" each VM acts like a totally independeent machine.

I'm sure there's an equivalent situation for the other virtualization programs, but VBox is the only one with which I'm familiar.

---

### Post by shad0wman on 2011-01-27
many thanks to Cheesehead & JKyleOKC for the answers I needed!

it now works as i wanted and the 2 VMs are able to connect to each other after i've changed the settings!

thank you once again :)

---

### Post by shad0wman on 2011-01-27
I have successfully set up my system as mentioned above and now i wish to test my stunnel to see if it's working.

I read that this can be done using Wireshark, therefore my question is:

will wireshark capture packets just within my computer and not affect my whole corporate network?

---

### Post by dmizer on 2011-01-27
> **shad0wman said:**
> I have successfully set up my system as mentioned above and now i wish to test my stunnel to see if it's working.

I read that this can be done using Wireshark, therefore my question is:

will wireshark capture packets just within my computer and not affect my whole corporate network?

It's been mentioned before in this thread but: If you are using a bridged connection, you should think of the VMs as though they are two additional and real computers connected to the entire LAN. As far as wireshark is concerned, it would be the same as though you were trying to capture packets from your coworker's computer.

---

