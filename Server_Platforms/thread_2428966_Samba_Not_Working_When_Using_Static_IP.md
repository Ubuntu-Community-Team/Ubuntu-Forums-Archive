---
title: "Samba Not Working When Using Static IP"
date: 2019-10-11
forum: Server Platforms
---

### Post by bryanmcconkey on 2019-10-11
Hello,
I'm having a problem getting samba to work on a ubuntu 18.04 server with a static IP.
If I have default IP (dynamic) settings samba works fine (I can access via ip or name from other computers(windows) on the network).

When i configure netplan for a static ip (with the following)
```

network:
    version: 2
    renderer: networkd
    ethernets:
        enp6s0:
            dhcp4: false
            dhcp6: false
            address: [192.168.25.6/23]
            gateway4: 192.168.25.1
            nameservers:
                addresses: [192.168.25.1]

```

I get the ip I expect in ifconfig. I can ping it via ip from other machines without issue. I can NOT ping via the hostname. And I can not access the samba share via either the hostname or ip.

If i change back to dhcp4: true, i get a dynamic ip and samba and hostname resolution works.

I feel I must be missing something simple, but have not been able to figure it out.
Any help would be appreciated, thanks!

---

### Post by DuckHook on 2019-10-11
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

### Post by TheFu on 2019-10-11
I suspect your DHCP server is also providing DNS for any DHCP leases.
If you run avahi, then you can try using {hostname}.local in samba/CIFS URLs.
If you don't run avahi, you'll need to configure the DNS with the correct name-to-IP mapping.

---

### Post by bryanmcconkey on 2019-10-12
While I could see this being the issue for the hostname resolution, I would expect I could access samba share with the static ip. I can not access the samba share with an ip when using the staic ip, but can when using a dynamic one.

---

### Post by TheFu on 2019-10-12
> **bryanmcconkey said:**
> While I could see this being the issue for the hostname resolution, I would expect I could access samba share with the static ip. I can not access the samba share with an ip when using the staic ip, but can when using a dynamic one.

If it doesn't work with an IP in the URL, then look to an old ARP table or firewall. 
Just to clarify, the static IP is well outside the DHCP subnet range, correct?  Static IPs can't been in the IP range managed by the DHCP server.

---

