---
title: "Block IPs and ICMP IPTables"
date: 2010-05-27
forum: Security
---

### Post by guimaster on 2010-05-27
Hello!

I use the following command to block IP Addresses with IPTables:

iptables -I INPUT -s 0.0.0.0 -j DROP

This works fine until I reboot, and then all of my settings are lost. How do I block an attacking IP Address permanently (so that the settings aren't lost on reboot)?

Also, I have Firestarter set to Filter ICMP, yet I continually fail the GRC Shield's Up test by having a ping get through to my computer. How can I put a stop to ICMP reaching my computer? I want to be able to easily disable and re-enable ICMP in case I need to do connection troubleshooting.

Thanx - GuiMaster

[[IMG]http://www.scorpionagency.com/imagehosting/uploads/ef444efcfc.png[/IMG]]("http://www.scorpionagency.com/imagehosting/")

---

### Post by bodhi.zazen on 2010-05-27
first, if you are using both iptables and firestarter they will conflict.

Second I would advise you use ufw / gufw

If you want to learn how to use iptables , see

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

If you are already familiar with iptables, there are several ways to save your changes.

Personally I use iptables-save and call iptables-restore in /etc/rc.local, although you can call it from /etc/network/interfaces as well if you wish (post-up ...)

Details in the link above.

ufw is also very easy to use and will save your rules. If you want a graphical front end, use gufw.

You will need to purge firestarter though

```
sudo apt-get purge firestarter
sudo apt-get install gufw
```

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Last, ShieldsUp is not the best way to check for open ports / ping as it is scanning your ROUTER not your Ubuntu box.

Use nmap (graphical tool = zenmap) or one of the commands in my iptables linky.

---

### Post by AcidMoon on 2010-05-27
You can find ICMP rules in:
gksu gedit /etc/ufw/before.rules
Commenting out "-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT" will block sending echo responses. If that helps!!

---

### Post by anomie on 2010-05-28
[QUOTE=guimaster]I continually fail the GRC Shield's Up test by having a ping get through to my computer. How can I put a stop to ICMP reaching my computer?[/QUOTE]

It's neither here nor there (since your "home router/NAT device" is likely responding), but I don't think it is a particularly necessary - or good - thing to drop ICMP echo requests. I wish grc's scanning service would not represent that as a problem. 

In the future, if you'd like to see what's happening with ICMP traffic on your host, you can watch it with tcpdump. 

For example: 
```
$ sudo tcpdump -i <int> icmp
```
... where <int> should be the network interface you're monitoring, e.g. eth0 or wlan0. 
[list]
[*] If you observe icmp echo requests and replies, then the ping request is reaching your host and being replied to. 
[*] If you observe icmp echo requests but *not* replies, then the ping request is reaching your host and being filtered/ignored. 
[*] If you observe neither, the request is not reaching your host at all..
[/list]

---

### Post by The Cog on 2010-05-28
Are you sure it's not your router that's answering pings?

---

