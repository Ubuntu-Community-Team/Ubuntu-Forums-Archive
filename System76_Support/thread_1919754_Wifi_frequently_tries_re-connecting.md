---
title: "Wifi frequently tries re-connecting"
date: 2012-02-03
forum: System76 Support
---

### Post by 130s on 2012-02-03
My netbook, System 76 star3 (hope it's still being used by some others!), frequently tries reconnecting wifi in the environments where my other System 76 machine doesn't (Serval). Since it happens with any network/access points, I suspect my star3 has an issue. I don't have an idea what should I report other than phenomenon description below. Can someone teach me about it?

(Phenom) I can't re-produce intentionally but the wifi signal icon often shows reconnection status. I feel that once this begins, it occurs more often. Roughly I usually see it happening more than once per hour.
Sometimes it even says disconnected, after long (longer than 1 minute) of reconnection trial.

(Actions I've taken) I did clean install twice after purchase when it came originally with Ubuntu 10.04 netbook edition. Now it's running Ubuntu 10.10 upgraded from 10.04 netbook ed. The phenomen was already happening in my 2nd generation installation (now is 3rd gen), where OS was 10.04 netbook. I didn't really used much during 1st gen for a reason.
After clean installation, System 76 driver is installed by adding a file [http://www.planet76.com/sources.list.d/system76.list](http://www.planet76.com/sources.list.d/system76.list) to /etc/apt/sources.list.d, then update.

---

### Post by dodo3773 on 2012-02-04
Could be a lot of different things. Take a look at "dmesg". That should at least give you an idea of what is going on. Try setting a static ip for yourself in your router and upgrading or downgrading your kernel.

---

### Post by isantop on 2012-02-06
Building on that, you might try running the computer from a Live USB of Ubuntu 11.10, since there has been a lot of work in Wireless there since 10.10. In addition to that, the Unity environment present in 11.10 is much faster than what's available in 10.10 netbook edition.

---

### Post by 130s on 2012-02-09
Thank you folks. Though not entirely sure, 11.10 via live-USB seemed better so I upgraded.

Haven't tested enough, I still see similar issue when I'm in office - not exactly the same with what I have described earlier though, but I would say I feel it got worse; wifi symbol shows it stays connected but ping and other connection gets stunned, only a few minutes after it got connected (so if I was a too naive user I might have even not realized that there's a network issue).
However, there's been no problem at home (pinging 20k+ made 0% loss).

Here's the current dmesg output: [http://pastebin.com/vPnmNMq0](http://pastebin.com/vPnmNMq0)
Here's dmesg output when the netbook was on Ubuntu 10.10: [http://pastebin.com/aE9syqv1](http://pastebin.com/aE9syqv1)

Thanks.

---

### Post by 130s on 2012-02-14
I tested in my office and it worked pretty good. Though I've only tested for 2 hours, the issue used to happen very frequently even during such a short period as I reported above. 

So I'm just curious what does this mean? Is the issue in the version of Ubuntu itself (in my case 10.10 or older) or is it the compatibility issue b/w starling device and Ubuntu? On my other notebook (Sony Vaio FS-92S bought in 2005), wifi on 10.10 works perfect btw.

---

### Post by varunendra on 2012-02-16
So the dmesg outputs show that you have an Realtek **RTL8192SE/RTL8191SE** card using **rtl8192se** driver. I have seen similar problems with this card, although couldn't figure out the reason or a sure-shot solution. If you face the problem again, please post the outputs of (when the problem occurs):
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
iwconfig
```

---

### Post by 130s on 2012-02-21
> **varunendra said:**
> If you face the problem again, please post the outputs of (when the problem occurs):
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
iwconfig
```

varunendra,

thanks for the suggestion. And I still experience the same issue (trying to connect to wifi forever w/o getting connected) only at my office. Here's the log [http://pastebin.com/5J0bpwd9](http://pastebin.com/5J0bpwd9) (private info (e.g. ESSID, IP addr) is removed). But overall I hardly see the issue happens in other location after I've upgraded to Ubuntu 11.10. 

Thank you again for your concern!
Isaac

---

### Post by ctsdownloads on 2012-02-21
> **130s said:**
> My netbook, System 76 star3 (hope it's still being used by some others!), frequently tries reconnecting wifi in the environments where my other System 76 machine doesn't (Serval). Since it happens with any network/access points, I suspect my star3 has an issue. I don't have an idea what should I report other than phenomenon description below. Can someone teach me about it?

(Phenom) I can't re-produce intentionally but the wifi signal icon often shows reconnection status. I feel that once this begins, it occurs more often. Roughly I usually see it happening more than once per hour.
Sometimes it even says disconnected, after long (longer than 1 minute) of reconnection trial.

(Actions I've taken) I did clean install twice after purchase when it came originally with Ubuntu 10.04 netbook edition. Now it's running Ubuntu 10.10 upgraded from 10.04 netbook ed. The phenomen was already happening in my 2nd generation installation (now is 3rd gen), where OS was 10.04 netbook. I didn't really used much during 1st gen for a reason.
After clean installation, System 76 driver is installed by adding a file [http://www.planet76.com/sources.list.d/system76.list](http://www.planet76.com/sources.list.d/system76.list) to /etc/apt/sources.list.d, then update.

It may be power management related. While this is reported to not help with this specific issue and driver, you can give it a whirl anyway.

```
sudo iwconfig wlan0 power off
```

If that does nothing, might as well turn it back on

```
sudo iwconfig wlan0 power on
```

It's reported that this driver is still a problem even in the 3.x kernel. But wait, here's where it gets strange. For some reason, there are reports that turning off ACPI "helps". THis is the one single change that I've heard of getting results. The problem is of course,  that's *not* a solution.

Personally, when dealing with dropping wifi, I take the following approach in this order.

**1) Ping and DNS**. Can I ping outside of my LAN but domains such as Google.com are hit and miss? Time to start using OpenDNS.

```
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ gksudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
Restarted  PC
```

**2) Heat.** With some chipsets, heat can be an issue. Just for giggles, you might see if a cooling pad helps. If the laptop isn't hot to the touch, then this might not be the issue.

**3) Another network manager.** Even in recent releases of Ubuntu, sometimes I've found that Wicd simply works better with some wireless devices than the default network manager. It's rare, but it happens. [http://ubuntuforums.org/showthread.php?t=1680600](http://ubuntuforums.org/showthread.php?t=1680600)

---

