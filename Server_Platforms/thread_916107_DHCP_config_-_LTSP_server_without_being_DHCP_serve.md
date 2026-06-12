---
title: "DHCP config - LTSP server without being DHCP server?"
date: 2008-09-10
forum: Server Platforms
---

### Post by dstien on 2008-09-10
I'm trying to set up my server as an LTSP Server.  I've been able to log in through a thin client no problem, but other computers on the network are being assigned ip's by the dhcp server that I set up when installing the LTSP packages--and thus they can't connect to the internet.

I'd like to keep the DHCP server for the network on the router I have (running DD-WRT) if possible.  How can I configure my server machine to play nicely with the existing network configuration, only giving IPs to the thin clients on the network?

I'm very new at this, so I could be asking dumb questions along the way.  Also, not sure what information is helpful, but I'm running two network cards in the server, the first one gets a dhcp static IP from the router, and the second one I have set for 192.168.0.1, as it is the default address (I couldn't get the router to automatically give it the address with static dhcp).

Let me know if you can help.

---

### Post by dstien on 2008-09-17
For anyone reading this with the same question, I did learn that DHCP is not a necessary function for the LTSP server.  If you already have a DHCP server and you want to use that instead of the LTSP server machine to give IPs, you can set up your already existing DHCP server to direct boot requests to the LTSP server address.  First to prevent possible conflicts between the DHCP server and your LTSP server, it's a good idea to remove the DHCP package from the LTSP server machine.

```
sudo apt-get remove dhcp3-server
```

(reference [here]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP"))

If want to utilize a Windows DHCP server for IP assignment, follow the above link for more detail how to make specific machines boot from the LTSP server.

If you happen to have a DD-WRT router as I do, you can add this line to the DNSMasq additional options under the services tab:

"dhcp-boot=ltsp/i386/pxelinux.0,,192.168.1.132"

Just make sure you put the actual IP of your LTSP server there at the end instead of the IP in the example.  Thanks to Carl on [this]("http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg33980.html") thread.

This is an awesome feature of Ubuntu.  Linux continues to astound me.  Thanks to all the people who make this stuff work!

---

### Post by thebbxx on 2009-03-05
I handled this by editing the dhcpd.conf file to exclude any unknown clients, and then added each thin client by mac address to a group.  Below that I have another declaration for my non-thin client computers.

---

### Post by AlexanderDGreat on 2009-09-22
Hi I've tried this but upon unistalling dhcp3-server, it also wants to uninstall ltsp-server-standalone.

So it's useless for me, what should I do?

Thanks.

---

### Post by kuala on 2011-08-29
If you'd like to uninstall the DHCP server from your LTSP Alternate CD installation, check out the following steps taken directly from the "Installing dnsmasq" section of...

[UbuntuLTSPProxyDHCP]("https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP")  -  [URL="https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP"]https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP
[/URL]
[INDENT]Mark ltsp-server as manually installed, so that it doesn't get purged along with ltsp-server-standalone: [/INDENT][INDENT][INDENT]sudo apt-get install ltsp-server  # This may update ltsp-server instead
sudo apt-get install ltsp-server  # So do it twice to be certain[/INDENT]Remove dhcp3-server and ltsp-server-standalone: 
[INDENT]sudo apt-get --yes --auto-remove purge ltsp-server-standalone[/INDENT][/INDENT]

---

