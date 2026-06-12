---
title: "what come first? or where do I begin? server network"
date: 2011-11-18
forum: Server Platforms
---

### Post by Tasmac on 2011-11-18
I want to setup a home network. I know who doesn't, and i am sure this is not the first time this question is asked. I want a file server, DNS Server, and DHCP server. (well ssh to be included.)
    what I have:

    SMCGS24 unmanaged 24 port switch
    Linksys WRT310N wireless/4-port switch
    Linksys BEFSR41 4-port router/switch
    Dynex DX-GB8PRT switch
    1,000 ft cat6 shielded cabling
    windows Server 2008 (which I don't know how to use)
    Ubuntu-server Cd's from 8.04 to current 64bit and 32bit
    3- PC's to be used as servers

I know I don't need to use all the stuff listed above, but I have it if i need it. I have a location for the servers, and what rooms need a port (all of them, and maybe 2-ports each.

So, I guess my question is what comes after my modem ? is it a DNS, or DHCP, or maybe a home-made Linux firewall/ or can I use my routers? (problem with linksys my IP's would be stuck at 192.168.1.? and really don't want those IP's).  I want my PC-desktops on a private DNS, but be able for each PC to get access to the outside world . this make any sense?
Oh ya almost forgot, I also own a .com (hosted outside my home) and I have a static IP .

What I have read:

    Linux Bible-Christopher Negus
    Linux Administration-Wale Soyinka
    Ubuntu 10.10 Server: Administration and Reference-Richard Petersen ( loaned it to a friend...I may never see it again)
    Ubuntu Server Guide (on this site help.ubuntu.com)
    A Practical Guide to Fedora and Red Hat Enterprise Linux-Mark G Sobell ( I really don't like Fedora or red Hat, but it has some good stuff)

Just some helpful information to get me started in the right direction. I don't want to start building this to find out after a couple of weeks later I did step one wrong-
I feel very comfortable in terminal mode, matter of fact I prefer it over a GUI. One more important item I m going to connect a total of 5 PC's to this network, 3 are Ubuntu desktops, two are windows. I'll switch my HTPC to Ubuntu when Netflix drops Silverlight, and my old lady may never use Ubuntu-

Thanx in advanced, Tasmac

---

### Post by SeijiSensei on 2011-11-18
> **Tasmac said:**
> So, I guess my question is what comes after my modem ? is it a DNS, or DHCP, or maybe a home-made Linux firewall/ or can I use my routers? (problem with linksys my IP's would be stuck at 192.168.1.? and really don't want those IP's).

Make sure the Linux box has two Ethernet cards.  Give one a static address like 192.168.1.2 and connect it to the Linksys router.  Set the "gateway" in /etc/network/interfaces to the internal address of the Linksys, probably 192.168.1.1.  

Now give the other card an address in the local subnet you wish to create, say 10.1.1.1.  Make sure IP forwarding is enabled in /etc/sysctl.conf and add an outbound masquerading rule with iptables (that should be covered in what you've read).

Install the dhcp3-server package on the Linux box and configure it to provide addresses in 10.1.1.0/24 or whatever subnet you choose.  Make sure you bind the DHCP server to the internally-facing adapter using the INTERFACES directive in /etc/default/dhcp3-server as described [here]("https://help.ubuntu.com/community/dhcp3-server").

---

### Post by Tasmac on 2011-11-18
[FONT=Arial Black]Thank you[/FONT], [FONT=Arial Black][I]SeijiSensei
    Thats exactly what I wanted to know :D

thanx for the link
[/I][/FONT]

---

