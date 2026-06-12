---
title: "VMM &amp; Bridging."
date: 2017-03-31
forum: Virtualisation
---

### Post by Sami_Mattila on 2017-03-31
I'm having trouble with Virtual Machine Manager (VMM) and Network Bridging.
I could get it to work if I manually edited /etc/networking/interfaces file but I would like to use Network Manager to create new network connections to use with VMM.
In the example below I have used Network Manager and created Bridge called Proxmox44 and used it with VMM but as you can see that comes with certain problems.
If I use macvtap connection network works fine for the VM but I can't access the client from the host.
How can I access the client from the host?

[ATTACH=CONFIG]274376[/ATTACH]

---

### Post by TheFu on 2017-03-31
Over the years, I've learned to never use a GUI to manage complex networking.  Best to use the config files directly if you want a solid, fast, bridge.  Usually people want to use the GUI because they are on a system that has changing networking - like a laptop.  

Plus, in the old days, 5 yrs ago, the GUI-created bridges were VERY SLOW performers, so if that wasn't sufficient, doing it manually was necessary.

Anyway, to solve the quick-change-for-networking issue, create 2 interface files (or 5) which reflect what you need in each different network location, then swap in the one you need and restart the networking.  I've found that since systemd got involved, I have to manually bring down the network devices, in the correct order, then bring them back up in the correct order to restart things. None of the 3 system methods to restart networking that should work, did.

In my situation, I needed to have a different bridge config depending on if I was using a wired or wifi connection and which subnet I might be on at the time - 10.x.x.x or 172.x.x.x or 192.168.x.x or DHCP.  Using DHCP is a hassle since both the hostOS and the guests will have unknown-until-after network addresses. I haven't scripted updating the /etc/hosts on both, but probably should.

Sorry I don't have a better answer.

---

### Post by 1clue on 2017-03-31
+1 for using the files. I never made it work right using network gui.

---

### Post by KillerKelvUK on 2017-04-01
It might help to understand your reason for wanting to use Network Manager?

> [COLOR=#000000]In the example below I have used Network Manager and created Bridge called Proxmox44 and used it with VMM but as you can see that comes with certain problems.[/COLOR]

So unless I'm going blind I can't see any problems...the screencap just shows the GUI config...that warning triangle isn't a problem and just pertains to how the macvtap driver works and that you *might* need a specific switching configuration in the environment.  Also I don't believe you are using the same bridge you created (Proxmox44).  Is there not another device shown in the Network Source list that then allows you to select the Proxmox44 bridge you've created in NM?

---

### Post by Sami_Mattila on 2017-04-01
@KillerKelvUK Thx 4 replying. Can you give me some advice how to use Network Manager to create a bridge that I can use with Virtual Machine Manager (VMM).
(And you are right... it seems I did not use the Proxmox44 bridge with VMM. My bad. I created it with NM in the beginning but seem to have "not used it" afterwards.)

---

### Post by KillerKelvUK on 2017-04-01
Its an awful process in NM and not one I care to document but others have, this ([http://ask.xmodulo.com/configure-linux-bridge-network-manager-ubuntu.html](http://ask.xmodulo.com/configure-linux-bridge-network-manager-ubuntu.html)) looks reasonable, I'd recommend you work your way through that and confirm the bridge is up and running, the remaining configuration in VMM is then simples as it should appear in the Network Sources list.

---

### Post by Sami_Mattila on 2017-04-02
Finally got it to work. I can now ping any VMM client from host (and back.)

/etc/networking/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
iface eth0 inet manual
auto vmbr0
iface vmbr0 inet static
        address  192.168.12.40
        netmask  255.255.255.0
        gateway  192.168.12.1
        bridge_ports eno1
        bridge_stp off
        bridge_fd 0
        dns-search ic4.eu
        dns-nameservers 8.8.8.8 8.8.4.4

[ATTACH=CONFIG]274406[/ATTACH][ATTACH=CONFIG]274407[/ATTACH]

[ATTACH=CONFIG]274408[/ATTACH]

---

### Post by TheFu on 2017-04-02
eno1 and eth0 should probably match in your interfaces file.  Under systemd (16.04+), the network interface names have all changed to be unique (think it used the MAC).  Wish the dmcrypt guys would learn that.

---

### Post by Sami_Mattila on 2017-04-10
> **TheFu said:**
> eno1 and eth0 should probably match in your interfaces file.  Under systemd (16.04+), the network interface names have all changed to be unique (think it used the MAC).  Wish the dmcrypt guys would learn that.

You are right. That would be better but it also works like this... sort of. It's kind of ugly though. I wish there was a better way. I can't figure out how to get Network Manager to do what I want while also working with VMM.

---

### Post by TheFu on 2017-04-10
It shouldn't work. You should fix it.

---

