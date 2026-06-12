---
title: "DHCP server position on home network"
date: 2008-09-02
forum: Server Platforms
---

### Post by HunterA3 on 2008-09-02
I posted a thread over on the network section, but this may more appropriate here. 
I'm building a PXE build/DHCP server and I'm running my network on an ADSL modem attached to a wireless router. The router is currently acting as my DHCP server, but I need to shut this off in order to create the PXE server because it will be the DHCP server. However, if you go over to the other post, it sits on the far side of my network and I'm not sure if it will issue DHCP leases from there to the rest of the network. Anyone know if this will work or will I need to reposition this to just before or after the router?

Here is the link to the previous thread which includes my network layout:
[http://ubuntuforums.org/showthread.php?t=908498]("http://ubuntuforums.org/showthread.php?t=908498")

Thanks

---

### Post by mellowd on 2008-09-02
DHCPDiscovery and DHCPRequest packets are broadcasts, which your router will block. On Cisco devices you can use IPHELPER to forwards these types of messages, check to see if your router has a similar option

---

### Post by windependence on 2008-09-02
I'm kinda wondering why you need the router behind your wireless router. Can't you just plug in the switch to your wireless router?

The DHCP server shouldn't matter as long as you can reach it from your other boxes. Of course it will have a static IP and that IP should be accessible from the other side of your network.

BTW, what tool did you use for the drawing? ;)

-Tim

---

### Post by HunterA3 on 2008-09-02
I would assume it would block DHCP Discovery and DHCP Request on the outside of the firewall. I just wasn't sure if it would be a factor if all internal traffic was filtered through as well.

The second router is setup as a switch, I just labeled it as such because that was it actually is.

As for the tool, I was at work and limited, so I used MS powerpoint. :-?

---

### Post by mellowd on 2008-09-02
> **HunterA3 said:**
> I would assume it would block DHCP Discovery and DHCP Request on the outside of the firewall. I just wasn't sure if it would be a factor if all internal traffic was filtered through as well.

The second router is setup as a switch, I just labeled it as such because that was it actually is.

As for the tool, I was at work and limited, so I used MS powerpoint. :-?

No, remember switches break up collision domains while routers break up broadcast domains. Regardless of your firewall settings, all routers drop broadcasts by default. You will need to change this behaviour in order for dhcp to correctly work

---

