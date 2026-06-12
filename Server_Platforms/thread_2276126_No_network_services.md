---
title: "No network services"
date: 2015-04-30
forum: Server Platforms
---

### Post by chriso0258 on 2015-04-30
Sorry if this is the wrong forum. However, the problem started when I installed ubuntu desktop on my ubuntu 12.04 server. I can connect to the network (I have not rebooted yet so I don't know if that will go away after a reboot), I just can't access the network settings from the desktop. When I access the network from system settings, I get the following message,

"The system network services are not compatible with this version"

I'm hesitant to reboot in case I lose the network connection.

Thanks for any advice.

---

### Post by dino99 on 2015-04-30
as i understand, you have made a fresh installation, right ?  so that error suppose a conflicting version, which is not logic with the previous supposition. Not clear at all.
open the logs to find where is the problem (syslog/dmesg)

---

### Post by steeldriver on 2015-04-30
@dino99 I would interpret the OP to mean that they installed the ubuntu-desktop *package* on top of an existing server installation

So perhaps the issue is that network-manager by default ignores interfaces that were configured using /etc/network/interfaces?

---

### Post by chriso0258 on 2015-04-30
You are correct steeldriver. I installed ubuntu server 12.04 LTS. A few months later I ran > sudo apt-get install --no-install recommends ubuntu-desktopWhen I go to the network settings it says it's not compatible. It does not say not compatible with what? I'm assuming with ubuntu 12.04 but I don't know. Any ideas? If so, can it be fixed?

Thanks for your assistance.

---

### Post by steeldriver on 2015-04-30
Hmm... because you used --no-install-recommends perhaps you ended up with the GUI applet but either no network-manager service or an incompatible version

What does 
```

dpkg -l network-manager*

```

say? especially about the versions of network-manager-gnome versus network-manager

---

### Post by sylkarp on 2015-04-30
from terminal
> ifconfig

then do 

> sudo ifconfig wlan0 up
sudo dhclient wlan0



or 
> sudo ifconfig eth0 up
sudo dhclient eth0 
 then You connected by cable to router

---

### Post by wildmanne39 on 2015-05-01
*Thread moved to **Server Platforms**.*

---

### Post by chriso0258 on 2015-05-01
> **steeldriver said:**
> Hmm... because you used --no-install-recommends perhaps you ended up with the GUI applet but either no network-manager service or an incompatible version

What does 
```

dpkg -l network-manager*

```

say? especially about the versions of network-manager-gnome versus network-manager

I'm getting the following:

> Desired=unknowns/install/Remove/Purge/Hold
Status=Not/Inst/Conf-files/Unpacked/half-conf/Half-inst/trig-await/Trig-Pend
Err?=(none)/Reinst-required(Status,Err: uppercase=bad)

Then six lines of:
> un network-manage <none>     (no description available

I am showing an IP address when I do an ifconfig. Hope this helps.

---

### Post by SeijiSensei on 2015-05-01
What is the contents of the file /etc/network/interfaces?  If it looks like this:
```

auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
That's all you need to get an address from a DHCP server.  If you want to use a static address, replace the second stanza with:
```

auto eth0
iface eth0 inet static
address 192.168.1.27
netmask 255.255.255.0
gateway 192.168.1.254

```
replacing the gateway address with the LAN address of your router and an appropriate address for your server.  If your router uses DHCP, assign your server an address outside the range the router manages.

I'd just remove the network manager icon from your GUI interface and rely on /etc/network/interfaces.

---

### Post by chriso0258 on 2015-05-01
Hello [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"),

Here is the contents of my interfaces file,

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp



Connecting to the network is not the problem. I'm not sure why the post got moved here. My problem is, when I try to access network services from the desktop (System Settings -> Network). When I click on Network, then I get the not compatible message. It seems more an issue with 12.04 and the current version of ubuntu-desktop than a network issue. Also, as steeldriver referenced, maybe I shouldn't have used --no install-recommends.

---

### Post by darkod on 2015-05-01
Have you tried to remove the ubuntu-desktop package and install it again? I can't comment on the package itself since I have never attempted to install a desktop GUI package on uubntu server OS. Do you really need the desktop GUI or you simly wanted to see how it will go?

---

### Post by SeijiSensei on 2015-05-01
> **chriso0258 said:**
> When I click on Network, then I get the not compatible message.
Try deleting the "eth0" stanza from /etc/network/interfaces, then logout and log back in.  Can you use the GUI network manager now?  If not, try rebooting.

---

### Post by steeldriver on 2015-05-01
It looks like you don't have the network-manager / network-manager-gnome packages installed - I'm not quite sure how you have the GUI nm-applet at all (I thought it was provided by the latter package) however if you want to control your interface(s) via the GUI you are going to need to install / reinstall those, I think

```

sudo apt-get install --reinstall network-manager network-manager-gnome

```

(personally I would add --dry-run to that at first, just to see what additional stuff it may install / remove - since you have come at this from a slightly unconventional direction).

You will then have two choices how to proceed:

1) leave your existing eth0 definition in the /etc/network/interfaces file, but allow network-manager to 'manage' it by editing the /etc/NetworkManager/NetworkManager.conf file, setting

```

[ifupdown]
managed=**true**

```
or

2) (preferred) remove or comment out the eth0 interface definition in /etc/network/interfaces and just use the GUI - for a wired connection, the default IPv4 settings (everything via DHCP) should work out of the box

---

