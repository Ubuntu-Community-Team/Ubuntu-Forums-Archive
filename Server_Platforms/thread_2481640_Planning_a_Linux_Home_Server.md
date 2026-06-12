---
title: "Planning a Linux Home Server"
date: 2022-12-05
forum: Server Platforms
---

### Post by wp.rauchholz on 2022-12-05
HW is ordered should arrive soon and I’d like to start with the planning of setting it up. This i what I get:
Quad Core Mini PC Core i7 7820HK/HQ, Mini Computer,16G DDR4/,1T SSD,HDMI+DP Support 2 Monitors,Dual LAN NUC PC
I plan to attach 2 external USB SSD disks of 1 TB each for backup and maybe RAID1.


I plan to configure the server in 2 phases; (1) setup server as modem/router, and (2) setup services like media server, web server, etc…

Hardware has two Ethernet network devices. One will be used as internal (LAN) and the other as external (WAN)

 ------------------           ----------------------------------------
        | ISP/internet | ---------- | ISP modem, in bridge mode |
        ------------------           ----------------------------------------
                                                |
                                ---------------------------
                                |   Home Server               | 
                                |    ppp0/eth 0: WAN       | 
                                |     eth1: LAN                | 
                                --------------------------
                                                |
                                                |    Internal private network
                                                |    Subnet: 192.168.0/24
                                                |
  ------------------     ---------------------       -------
  | Network Printer |     | Workstation 1 .. x |        | TV  | 
  ------------------     ---------------------       --------

If have been doing quite some search on the net, but I don't seem to be able to find documentation on how to define the interfaces ppp0/eth0, eth1 of my config.
Is there anybody here who has done it and can point me to a solution/documentation?

Thanks, Wolfgang

---

### Post by ian-weisser on 2022-12-05
Keep in mind that if the modem/router is part of your server, any crash or problem with the server will also take down your network. Every reboot of the server will take down your network briefly. And while troubleshooting server problems, you won't have network access for reference and help.

Boy, oh boy, that caused me pain when I tried it years ago. Nevertheless, perhaps you will have better fortune than I did.

Were I doing it today, I would create a set of LXD containers. Each major function goes into a different container (File sharing, Backups, Automations). Very little on the base system, so less to go wrong. Modem/Router goes into its own container.

Keep notes on exactly how to rebuild the base system and the modem/router from scratch without network access. Maintain the tools to do so on-hand (LiveUSB, extra packages, notes). You might need those notes and tools on a bad day. Spin up a test container and practice once or twice.

If I recall correctly, ModemManager is where the modem config goes. However, much may have changed since I last mucked with it. Much also depends upon the modem hardware.

---

### Post by TheFu on 2022-12-05
1) Pick a better, odd, subnet, not 192.168.0.0/24.   If you have a server, you might want to VPN into it some day and you'll likely need a different subnet for that. If you start with a different subnet now, you won't need to go through this later.  Say 192.168.93.0/24 as an odd, seldom used subnet anywhere else.  Avoid common subnets that cafes, restaurants, hotels, businesses and conference centers use.  That means, none of the obvious choices should be used.  This tiny change now, avoids issues in the future.

2) Don't to any RAID over USB connections.  Just - DON'T.

3) Having a dedicated router/firewall on a dedicated hardware device is an important security choice.  Keep data and files off that system.  The more data you have to risk, the farther away from the internet connection that data needs to be so you can have more than 1 layer of protection.  Software fails to work as we think. Software gets misconfigured.  Software doesn't always start up in a secure mode, leaving systems unprotected for 5-90 seconds.  That's why we need layers for security and separate devices.

There used to be lots and lots of network diagrams made by professionals on the internet.  The server that had all those diagrams was taken off line, which is really sad.  Unfortunately, the wayback machine doesn't handle dynamic, DB driven, websites well, so effectively the 20K diagrams are lost and cannot be used to see what others did.

I'm all for having a home server or 10.  I'm 100% against them being on a WAN router device.  That's a terrible idea.  Someone needed to say that.  In fact, you should probably have another layer between the internet and this server for added protection against internet cracking attempts.
```

Internet
&#9492;&#9472;&#9472; Router
    &#9500;&#9472;&#9472; Gateways (reverse-proxy, smtp, VPN, etc)
    &#9474;** &#9500;&#9472;&#9472; LAN-Desktops
    &#9474;** &#9474;** &#9500;&#9472;&#9472; Her-desktop wired ethernet
    &#9474;** &#9474;** &#9492;&#9472;&#9472; His-desktop wired ethernet
    &#9474;** &#9492;&#9472;&#9472; LAN-Servers
    &#9474;**     &#9500;&#9472;&#9472; Jellyfin wired ethernet
    &#9474;**     &#9500;&#9472;&#9472; NAS wired ethernet
    &#9474;**     &#9500;&#9472;&#9472; Nextcloud wired ethernet
    &#9474;**     &#9492;&#9472;&#9472; Print-Spooler wired ethernet
    &#9492;&#9472;&#9472; Untrusted_LAN
        &#9500;&#9472;&#9472; IoT-IoS_devices probably wifi and likely to be scanning the network they can access for more information
        &#9474;** &#9500;&#9472;&#9472; Security_Cams (and connected home appliances)
        &#9474;** &#9500;&#9472;&#9472; Fire-Stick
        &#9474;** &#9500;&#9472;&#9472; Game_Consoles
        &#9474;** &#9492;&#9472;&#9472; Roku
        &#9500;&#9472;&#9472; Kids-computers (virus central, I'm not joking)
        &#9492;&#9472;&#9472; Wifi_connections Treat these like raw internet from the firewall and gateway perspective.
            &#9500;&#9472;&#9472; House-Guests never trust guests - let them get to the internet, but nowhere else
            &#9500;&#9472;&#9472; Laptops - high risk devices. These need to be fully encrypted and always suspect for nasty software if they leave your sight.
            &#9500;&#9472;&#9472; Smartphones probably the least secure device in any house.
            &#9492;&#9472;&#9472; Tablets probably the 2nd least secure device in any house.

```
Directories get different subnets for firewalling and access controls.  All wifi connected devices that need access to internal servers should use a VPN. Never trust wifi, even at your house. It isn't secure.
So, you'll need **at least** 3 subnets.  I put wifi on the ISP router 10.1.10.0/24 network and have my /29 public IPs bridged to my WAN router which splits into 3 subnets. My subnets are split based on risk levels, not the same as above.  I run a VPN server to provide internal access for local wifi devices to my servers and for when I'm away using internet, say from the library or halfway across the world. Doesn't matter.  

It really is too bad that professional network architects had their personal home setups disappeared from that online resource. There was much to be learned.

---

