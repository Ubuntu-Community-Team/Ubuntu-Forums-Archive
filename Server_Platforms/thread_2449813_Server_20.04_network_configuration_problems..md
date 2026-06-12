---
title: "Server 20.04 network configuration problems."
date: 2020-09-02
forum: Server Platforms
---

### Post by corollaattori on 2020-09-02
Configuration is as follows: Fortinet VPN router without DHCP that has direct internet access. Behind that is Switch and Ubuntu server with DHCP. I managed to get DHCP running and other computers connected to that switch gets ip and internet works. But server itself fails to connect internet and takes few minutes to boot because of that.

I tried configuring it with that guide, but no luck. 

[https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)
> [COLOR=#111111][FONT=Ubuntu]Static IP Address Assignment[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]To configure your system to use static address assignment, create a netplan configuration in the file /etc/netplan/99_config.yaml. The example below assumes you are configuring your first Ethernet interface identified as *eth0*. Change the *addresses*, *gateway4*, and *nameservers* values to meet the requirements of your network.[/FONT][/COLOR]
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
        - 10.10.10.2/24
      gateway4: 10.10.10.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [10.10.10.1, 1.1.1.1]
[COLOR=#111111][FONT=Ubuntu]The configuration can then be applied using the netplan command.[/FONT][/COLOR]
[COLOR=#111111][FONT=&quot]sudo netplan apply[/FONT][/COLOR]





I now see that there are different guides with other netplan configs. Which is correct and simplest way to do it?
[http://itprohelper.com/setting-up-static-ip-on-ubuntu-server-20-04-lts/](http://itprohelper.com/setting-up-static-ip-on-ubuntu-server-20-04-lts/)

[IMG]https://i.postimg.cc/Y2PTHBQs/Whats-App-Image-2020-09-02-at-17-55-54.jpg[/IMG]
If i share wired network from my Ubuntu laptop it works fine, so only static config is flawed.

Server also runs when finished Mate desktop and is Samba fileserver with WXP and W10 in virtualbox. Is Ubuntu Server best choice, or should i install desktop version of Ubuntu Mate instead, and add server components to that? Stability is most important. Main function is to use those windowses remotely with RDP and to be DHCP and file server.

---

### Post by The Cog on 2020-09-02
Please post the netplan config again, this time putting it in code tags (use go advanced, then highlight the text and click the # button at the top). Indentation is critical with netplan configs.

---

### Post by corollaattori on 2020-09-02
> **The Cog said:**
> Please post the netplan config again, this time putting it in code tags (use go advanced, then highlight the text and click the # button at the top). Indentation is critical with netplan configs.

Sorry that previous was just the quote from the link.

This is the config i made.

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
        - 10.150.200.10/24
      gateway4: 10.150.200.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [8.8.8.8, 8.8.4.4]
```

---

### Post by TheFu on 2020-09-02
```
dhcp4: false
dhcp6: false
```
at the same level as 
```
addresses:
```

Then run
```
sudo netplan generate
sudo netplan apply --debug
```

---

### Post by corollaattori on 2020-09-02
> **TheFu said:**
> ```
dhcp4: false
dhcp6: false
```
at the same level as 
```
addresses:
```

Then run
```
sudo netplan generate
sudo netplan apply --debug
```

So like this?
I'll try tomorrow when i get back to office.

```
network:  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
	dhcp4: false
	dhcp6: false
        - 10.150.200.10/24
      gateway4: 10.150.200.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [8.8.8.8, 8.8.4.4]
```

---

### Post by TheFu on 2020-09-02
No. At the same level.  BTW, **do not use tabs in this file.  Be 100% consistent following the YAML standard.**
```
      addresses:
        - 10.150.200.10/24
      dhcp4: false
      dhcp6: false
```
Don't split up a subsection from the parent.

---

### Post by math492m on 2020-09-03
use server 18.04 instead that was the only thing that fixed my problem

---

### Post by TheFu on 2020-09-03
> **math492m said:**
> use server 18.04 instead that was the only thing that fixed my problem

I haven't had any issues with 20.04 simplistic networking using a fairly short netplan.yaml file for static IPs. Now, doing more complex network steps didn't work on 18.04 until sometime in 2020 (they didn't work in fall 2019), but since around Feb'20, the netplan stuff in 18.04 and 20.04 have worked for simple, bridged, bonded, and a few other network configurations using single and multiple NICs.

I've been using yaml config files for a long time, so netplan was not the first introduction to them. Ansible, Ruby and Perl use yaml easily.  Sure, I had the interfaces working perfectly already and would have preferred no change, but as changes go, 2-4 yrs after first introduces, netplan hasn't been too bad.  resolvconf and systemd.resolved have been far worse over the years.

IMHO.

---

### Post by corollaattori on 2020-09-08
Tried all kinds of things unsuccesfully. Finally i re-installed it, and there was network settings in the setup and gave it static ip there and problem solved.

---

### Post by TheFu on 2020-09-08
Glad you got it working, but I suspect it was just an indentation problem between spaces vs tabs. Just because the indentation *appears* to be the same, if spaces and tabs are mixed, they are not the same. People unfamiliar with YAML often have the issue.

---

