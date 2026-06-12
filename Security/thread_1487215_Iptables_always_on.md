---
title: "Iptables always on?"
date: 2010-05-18
forum: Security
---

### Post by zozza on 2010-05-18
I suspect this is one of these questions from Window users who see something different in Ubuntu.  

My understanding is that the Ubuntu firewall (iptables) is always on.  However, the GUI client (firestarter) shows this more obviously. 

I suppose I am used to ZoneAlarm in XP where everything was displayed more obviously.  

So, iptables in not automatically displayed, but is working, right?

Thanks.

---

### Post by OpSecShellshock on 2010-05-18
Hmmm. Well, it's not so much always "on" so much as its rules are in force. By default no connections are allowed to be initiated from external devices. There will be no need to change this unless you're setting up a server.

Also, Firestarter is no longer being supported by its developers. The recommended tool for configuring rules for iptables is ufw, or if you prefer to use a gui you can install gufw. The rules are loaded at boot, so they'll be in force even though there's no graphical indicator.

---

### Post by bodhi.zazen on 2010-05-19
> **zozza said:**
> I suspect this is one of these questions from Window users who see something different in Ubuntu.  

My understanding is that the Ubuntu firewall (iptables) is always on.  However, the GUI client (firestarter) shows this more obviously. 

I suppose I am used to ZoneAlarm in XP where everything was displayed more obviously.  

So, iptables in not automatically displayed, but is working, right?

Thanks.

Linux is more modular then Windows, so with Linux there tend to be smaller applications that do one thing only (although there are exceptions to this general rule).

I think a better question to ask is what do you want a firewall to do ?


> **OpSecShellshock said:**
> Hmmm. Well, it's not so much always "on" so much as its rules are in force. By default no connections are allowed to be initiated from external devices. There will be no need to change this unless you're setting up a server.

Also, Firestarter is no longer being supported by its developers. The recommended tool for configuring rules for iptables is ufw, or if you prefer to use a gui you can install gufw. The rules are loaded at boot, so they'll be in force even though there's no graphical indicator.

By default, there are no significant open ports - so there is nothing to firewall.

iptables is a front end for netfilter , and these kernel modules are active when you boot.

By default, Ubuntu has not rules in iptables and the default policy is permissive, ie all traffic is allowed.

See : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

You may configure your firewall with any number of tools, from iptables to UFW to GUFW to firestarter.

If you want a graphical tool I suggest you start with GUFW.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

These tools are used to configure your firewall and you should then close them.

You may monitor your traffic with a number of methods including watching the logs or using Wireshark.

---

### Post by OpSecShellshock on 2010-05-19
I think new users should also know that, while traffic monitoring tools are available, they aren't going to be necessary for most home use. In a lot of cases, users will see that there aren't any events being displayed and will think that they configured the software incorrectly, when the fact is there's nothing displaying because nothing is happening. So there's no net gain even in peace of mind.

---

### Post by bodhi.zazen on 2010-05-19
> **OpSecShellshock said:**
> I think new users should also know that, while traffic monitoring tools are available, they aren't going to be necessary for most home use. In a lot of cases, users will see that there aren't any events being displayed and will think that they configured the software incorrectly, when the fact is there's nothing displaying because nothing is happening. So there's no net gain even in peace of mind.

I partially agree with that.

I think users should know that this is not Windows and the OS is already secure enough.

In addition Linux is not Windows, so behaviors / practices for Windows "security" , ie antivirus, spy ware scanners, etc, do not apply to Linux. This is partially due to security and partially due to the fact that there is no known active viruses or spyware "in the wild" that affects Linux.

If one wants to learn Security, Linux, Windows, or otherwise, they have a bit of reading to do. One needs to understand at least the basics of networking protocols and how a system works (file systems, permissions, etc).

IMO new users need to learn to relax and enjoy the freedom. After 3-6 months, if they wish, they can look under the hood a little and investigate these security issues.

Key points are :

1. There are no known active viruses for Linux.

2. There are no known active spyware applications for Linux (assuming one keeps to the official repositories).

3. Do not install software from untrusted sources.

4. By default there are no open ports on an Ubuntu Desktop.

If you install network monitoring software, snort for example, or watch your logs, you will see tons of suspicious activity on your network, assuming you are connected to  the internet.

Most of this is firewalled by your router. Most of the traffic is directed at Windows boxes:

> Top 50 signature matches:
      "MISC HP Web JetAdmin communication attempt" (tcp),  Count: 232,  Unique sources: 37,  Sid: 100084
      "MISC Microsoft SQL Server communication attempt" (tcp),  Count: 215,  Unique sources: 153,  Sid: 100205
      "ICMP Echo Reply" (icmp),  Count: 164,  Unique sources: 2,  Sid: 408
      "MISC VNC communication attempt" (tcp),  Count: 151,  Unique sources: 79,  Sid: 100202
      "BACKDOOR DoomJuice file upload attempt" (tcp),  Count: 139,  Unique sources: 23,  Sid: 2375
      "MISC Ghostsurf communication attempt" (tcp),  Count: 133,  Unique sources: 29,  Sid: 100203
      "MISC Radmin Default install options attempt" (tcp),  Count: 128,  Unique sources: 66,  Sid: 100204
      "MISC MS Terminal Server communication attempt" (tcp),  Count: 76,  Unique sources: 48,  Sid: 100077
      "PSAD-CUSTOM Slammer communication attempt" (udp),  Count: 56,  Unique sources: 23,  Sid: 100208
      "POLICY HP JetDirect LCD communication attempt" (tcp),  Count: 28,  Unique sources: 5,  Sid: 510
      "MISC Xtramail communication attempt" (tcp),  Count: 12,  Unique sources: 5,  Sid: 1636
      "MISC PCAnywhere communication attempt" (tcp),  Count: 3,  Unique sources: 2,  Sid: 100073

The "Sid" are snort id for the rule.

The "problem" is that without a basic understanding of networking traffic, packets, ports, etc the average user migrating from Windows has no idea what to do with this information.

---

