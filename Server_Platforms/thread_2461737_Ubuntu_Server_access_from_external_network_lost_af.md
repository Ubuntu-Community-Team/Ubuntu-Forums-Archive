---
title: "Ubuntu Server access from external network lost after server reboot"
date: 2021-05-06
forum: Server Platforms
---

### Post by kattey on 2021-05-06
Hello!

I try to study Ubuntu Server and face one problem.

I configured static ip address in Netplan by creating 01-config.yaml file:

```

network:  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
      addresses: [192.168.0.18/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.4.4, 8.8.8.8]

```

So, I also changed SSH port to 7822, allow port in ufw and change default politics allowing incomings.

I allow port 7822 on my router:

[ATTACH=CONFIG]288431[/ATTACH]

And it works fine! I have Windows 10 as main PC, and I use Windows Terminal and Telnet: checking my external ip shows everything seems to be fine:

[ATTACH=CONFIG]288432[/ATTACH]

Also I played around with Apache and some simple sites and opened my sites from external network with no problems.

The main problem is, after reboot it is not working at all. Until I change internal ip. For example: I can't get access to my Ubuntu Server from external network after rebooting. Internal ip of server machine is 192.168.0.18. I change it to 192.168.0.19, allow port in router, and everything is fine again. Until. next reboot.

Of course I try to use previous IP a few times, but it does not work. E.g., I used 192.168.0.18, 192.168.0.19, 192.168.0.20 and then try to use 192.168.0.18 again, and it does not work.

So I have a strong feeling I do something wrong. And I'm running out of internal ip. :) So I need to fix it.

I would appreciate any help, thank you for attention, be safe and good luck!

---

### Post by slickymaster on 2021-05-06
*Thread moved to **Server Platforms**.*

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by TheFu on 2021-05-06
Assuming the posted conf above is correct and the ONLY file in the /etc/netplan/ directory, there are some clear issues.
01-config.yaml looks wrong. 

```
network:  
[COLOR="#FF0000"]  version: 2[/COLOR]
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
[COLOR="#FF0000"]      dhcp6: no[/COLOR]
      addresses: 
[COLOR="#FF0000"]          - 192.168.0.18/24[/COLOR]
      gateway4: 192.168.0.1
      nameservers:
          addresses: [COLOR="#FF0000"][ 8[/COLOR].8.4.4, 8.8.8.[COLOR="#FF0000"]8 ][/COLOR]
```

Putting the correct entries on the correct lines matters.
Spacing is critical.
Indentation levels must be consistent for the same level.

After modifying the yaml file, 2 more steps, perhaps 3, are required:
```
sudo netplan generate
sudo netplan apply --debug
```

I prefer NOT to change the default ssh port on the LAN, but to have the router do "port translation" for me.  This way, the WAN port for each service is some non-standard port, but inside the LAN, the standard port is still used, so other tools that are pre-configured just work correctly.  Then you can probably connect to the WAN-IP:port or the LAN-IP:22 for ssh as a way to test whether it is working.  Not all WAN routers allow internal connections to WAN IPs for services. This is an old cracker trick to get the router to open a connection with a spoofed source IP, bypassing the router's firewall state. Beware.  There are lots of other techniques that can be used to accomplish something similar - tricking our cheap routers into opening ports that we didn't actually intend to be opened.

Anyways, the 
WAN-IP:exPort --> LAN-IP:inPort
So setup the forwarding to something like this:
64.233.177.100:63022 --> 192.168.21.18:22

There are reasons we don't want our 192.168.21.x/24 subnet to be a standard subnet like 192.168.0.x/24 or 192.168.1.x/24.

---

