---
title: "How to assign a permanent static IP address in 18.04"
date: 2018-12-19
forum: Virtualisation
---

### Post by rudlock on 2018-12-19
I am running an Ubuntu 18.04 server in Hyper-V on Windows 2012 R2. I am familiar with assigning static IPs in Mint 18.3 via the GUI tools, but not using only the CLI. I tried creating a 99_config.yaml file in the netplan directory that contains the following:
```

   network:
       version:   2
       ethernets:
           eth0:
               dhcp4:   false
               dhcp6:   false
               addresses:   [192.168.20.20/24]
               gateway4:    192.168.20.1

```
If I try to include lines for renderer or nameservers, I would get error messages when I ran the netplan apply command. The above does work and sets the IP address. The problem is that it doesn't always work automatically when I reboot and uses DHCP for an address. This messes up my client PCs using the MySQL server on my Ubuntu server.

What should I be doing to fix this? Thank you.

---

### Post by TheFu on 2018-12-19
indentation and spacing are ABSOLUTELY critical. Check those.  When you post here, use "code tags", so things line up.

---

### Post by rudlock on 2018-12-20
The indentation is correct and was when I entered it here. It obviously was lost when I posted it. What are  "code tags"?

---

### Post by coffeecat on 2018-12-20
> **rudlock said:**
> The indentation is correct and was when I entered it here. It obviously was lost when I posted it. What are  "code tags"?

It was not "lost", just obscured without the code tags. There is a link in my sig telling you how to use code tags. Code tags are just one of many types of BBCode which is worth learning how to use - not at all difficult - if you are going to use a forum, any forum. If you have ever used an online forum it would almost certainly have been possible to employ BBCode to enhance your posts.

Tip - in the message editor, click on the icon that looks a bit like A/A top-left in the toolbar and choose Source mode. Then you will be able to see the BBCode tags that you use. WYSIWYG mode is all very well but makes the use of BBCode awkward.

---

### Post by slickymaster on 2018-12-20
*Thread moved to **Virtualisation**.*

Be sure to use spaces in groups of four for indentation as Netplan does not appreciate tabs in its yaml files.

---

### Post by The Cog on 2018-12-20
> **coffeecat said:**
> Tip - in the message editor, click on the icon that looks a bit like A/A top-left in the toolbar and choose Source mode.

Blimey! I've been using these forums since Hoary Hedgehog and I still hadn't noticed that!

---

### Post by rudlock on 2018-12-26
I still have the problem. netplan apply sets my IP address, but it's not permanent. It reverts to the DHCP address quite often. I think I'm going to give up on Ubuntu and try Mint 18.3.

---

### Post by ubname on 2018-12-27
What I find strange in your config is the ethernet card  name you use, they are no longer called "ethx";
try to launch this command and post result:

```
ip address
```

---

### Post by KillerKelvUK on 2018-12-28
> **ubname said:**
> What I find strange in your config is the ethernet card  name you use, they are no longer called "ethx";
try to launch this command and post result:

```
ip address
```

+1 and also maybe the absence of the "renderer:" element to the config?

---

### Post by TheFu on 2018-12-29
According to netplan.io, renderer isn't necessary and will default to systemd-networkd [https://netplan.io/reference](https://netplan.io/reference) .  I don't know if Ubuntu installs that renderer or not.

Might be worth mentioning that netplan can be replaced by the old ifupdown method. There are guides for how to accomplish that.  I've not used netplan or 18.04, so I don't know if these issues are common or just people getting used to yml files.

---

### Post by rudlock on 2019-01-06
I added "renderer: networkd" to the file. Also "eth0" is the name of the interface according to ifconfig.

---

