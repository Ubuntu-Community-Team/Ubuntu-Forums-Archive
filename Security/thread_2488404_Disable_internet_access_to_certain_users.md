---
title: "Disable internet access to certain users"
date: 2023-07-04
forum: Security
---

### Post by tornadof3 on 2023-07-04
Hi, I am trying to disable internet access by username on family computer, running Ubuntu 22.04 LTS.

I've tried all of the standard variations of:

```
sudo iptables -A OUTPUT -p tcp -m owner --uid-owner username -j DROP
```

with and without the -p tcp and with both -j DROP and -j REJECT.

I don't think it's a persistence issue as when I issue the command and then go and login to username's account without restarting computer, they can still browse the internet unrestricted. And yes, I have substituted username for the username eg joebloggs. All user accounts are standard local accounts in /etc/passwd so nothing fancy.

Any pointers?
Thanks

---

### Post by TheFu on 2023-07-04
iptables isn't meant to be used in this manner, as you've learned.  It is cumbersome.  OpenSnitch might be more what you seek. I found opensnitch to be too complicated for my needs. [https://itsfoss.com/opensnitch-firewall-linux/](https://itsfoss.com/opensnitch-firewall-linux/)

An easier way to accomplish what you seek would be to use a USB wifi dongle for internet access and have that USB wifi removed when you don't want someone to have any internet access.  Setup the router to block access by other devices, only allow the usb wifi device.  So, when approved people want to use the internet, they'd connect the usb-wifi.  Unapproved people wouldn't physically have the wifi dongle, so no internet.  The built-in wifi or wired ethernet would need to be disabled.

**OR**

Otherwise. I don't have a good answer that doesn't involve using a proxy server like squid and that proxy would need to be located on a different computer and the entire network would need to be forced to use the proxy. Basically, only the proxy server would have internet access. All other systems would be stuck on the LAN and unable to even **ping google.com**.

**OR**

I suppose you could setup the networking to be disabled by default.  Reboot wouldn't enable it.  Then "approved" users would use sudo to bring up networking (or drop a script that does it into their auto-run programs at login time. Similarly, have a little sudo script to disable networking at logout.  There's a ~/.bash_logout script that can be used for this.  I'd create a old-style start/stop/status script like we used for 40 yrs with init system.

Suppose you create a script in /usr/local/bin/network-on-off with these contents:
```
#!/bin/sh 

case "$1" in
  start)
       echo "starting "
       /usr/bin/sudo /usr/bin/nmcli  networking on
        ;;
  stop)
       echo "stopping "
       /usr/bin/sudo /usr/bin/nmcli  networking off
        ;;
  status)
        echo "status"
        /usr/bin/nmcli  connectivity check
        ;;
  *)
esac
exit 0
```
The network start/stop/status commands are different depending on which init system and network management tool is used on your box.  For most desktops, I'd look at **nmcli** commands as shown above.

Then setup the sudoers file to allow only those exact commands to the people you want to allow network access. Left as an exercise, but the manpage for the suders file has examples.

Your autostart would have  **/usr/local/bin/network-on-off  start**
Your ~/.bash_logout would have  **/usr/local/bin/network-on-off stop**

YMMV. I haven't tested any of this. While I think it will work, it may not.

---

### Post by tornadof3 on 2023-07-04
Thank you for the reply - sounds like this is way more difficult than I had thought! We have a desktop machine on a CAT6 wired network to home router. I was just hoping that mum & dad's accounts could access the internet fine and children's accounts would be denied.... I'll have a look at Open Snich

---

### Post by TheFu on 2023-07-04
> **tornadof3 said:**
> Thank you for the reply - sounds like this is way more difficult than I had thought! We have a desktop machine on a CAT6 wired network to home router. I was just hoping that mum & dad's accounts could access the internet fine and children's accounts would be denied.... I'll have a look at Open Snich

You could just power off the router - connect it to a smart-home power plug and use your phone to power it on/off like a light switch. Bit of a chicken/egg problem this.  When the router is off, you can't use the wifi on your phone to turn it on. ;)

There are probably 50 other methods, but for small kids, the easiest is really the wifi-dongle method.  Since they will see you plug it in and unplug it when you leave ... they will make the connection.  As they get older, there will be a challenge since the kids will want internet and will likely learn where you keep the wifi dongle.  They might even buy their own dongle and plug it in, expecting it to work, so be certain you actually user MAC filtering on the router to only allow this specific dongle to work.

For really small kids, you don't need to block the entire internet if you disable DNS and have a whitelist of places they can visit.  Content networks have screwed this method a bit, with those random names for different edge content servers.  You know, zyx234223.cloudflare.com ... names like that. 20 yrs ago, it was much easier to have and maintain a whitelist.  These days, you may want to use something like a pihole for a client-by-client DNS filter.

---

### Post by SeijiSensei on 2023-07-04
If the kids use their own computers, you could block by IP address.

The best method would be to set up "DHCP reservations" on your router so the kids' computers always get the same IP addresses. Then you can have rules like

```

iptables -A INPUT -s ip.of.kids.computer -j DROP

```

This will block all outbound traffic from that IP.

---

