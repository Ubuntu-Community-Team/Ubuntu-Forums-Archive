---
title: "HowTo: UFW ) Block Outgoing Ports Except Those Needed + More"
date: 2011-12-11
forum: Security
---

### Post by fairskies on 2011-12-11
Contents - 

[B]Part 1: (. Novice .) - Block Outgoing Ports Except Those Needed
                       allow: 20-21, 53, 80, 123, 443 outgoing only
Part 2: (. Moderate .) - Sysctl: configure kernel parameters at runtime
Part 3: (. Moderate .) - Configuring before*.rules
Part 4: (. Advanced .) - Blocking Private Networks
[/B] ###################################################

[B]Part 1: (. Novice .) - Block Outgoing Ports Except Those Needed
                       allow: 20-21, 53, 80, 123, 443 outgoing
[/B] 
I have tested this at the command line and it works. Here are the instructions on how to block outgoing ports except those specified using ufw at the command line. This guide assumes you have previously modified /etc/ufw/ufw.conf to enable auto-launching on system startup and ufw is running. 

This configuration will allow the following outbound ports: 20-21, 53, 80, 123, 443 which is all that is required for many users. The outbound port mapping may be customized by you for your setup if it's your desire for allowing other applications using different ports. This guide does not cover configuration of apps which would reside in /etc/ufw/applications.d 

1. Open a Terminal window
2. With ufw started and configured for system startup with the default inbound deny, begin:


sudo ufw deny out 1:19/tcp
sudo ufw deny out 1:19/udp
sudo ufw deny out 22:52/tcp
sudo ufw deny out 22:52/udp
sudo ufw deny out 54:79/tcp
sudo ufw deny out 54:79/udp
sudo ufw deny out 81:122/tcp
sudo ufw deny out 81:122/udp
sudo ufw deny out 124:442/tcp
sudo ufw deny out 124:442/udp
sudo ufw deny out 444:65535/tcp
sudo ufw deny out 444:65535/udp


3. Check your work in one or two ways:


sudo ufw status verbose
sudo ufw status numbered


Configuration is complete. To test this configuration you may start applications requiring the use of another port, such as a torrent application and when it fails to function, your leak test is a success. If you prefer retaining the above configuration, you may customize applications which allow it to use ports 80 or 443 to function. Or, you may prefer to redo the above differently with your own port range to allow for ports you need open. 

I wrote this post because I couldn't find the information on-line on blocking outbound, or the information found was in error for the current version of Ubuntu 11.10. Or, there were posts where users *wanted* this functionality but people would post back unhelpful information in different ways, including but not limited to, &quot;You don't need to do this.&quot; Yes, some would like this functionality, otherwise they wouldn't have asked for the information! 

When you've finished using the sudo command in your Terminal, close it out with: 

sudo -K 

followed by: 

exit 

If you're continuing to use sudo for other operations at the command line, don't type sudo -K until you've finished. 

One example of an application which may be customized for this setup is Vidalia/Tor: 

- Open Vidalia's Control Panel and click on Settings.
- Now click on the Network Icon.
- Next, click the box which says, &quot;My firewall only lets
me connect to certain ports - Firewall Settings&quot;, from
here it should say 80,443 by default, you're done here,
click OK.


When you reload Vidalia/Tor, it will have written those port settings to the Tor configuration file and it will launch using the above two ports only. 

This is very useful when running Tor if you want an outbound blocking policy in ufw, as Tor by default connects to several different ports and it would be impossible to configure them all, as they change per Tor node(s). 

################################################### 

[B]Part 2: (. Moderate .) - Sysctl: configure kernel parameters at runtime
[/B] 

This is interesting in Ubuntu 11.10, as Sysctl is found/referenced in three different locations: 

/etc/sysctl.conf
/etc/sysctl.d/ (contains a few files)
/etc/ufw/sysctl.conf


Within /etc/ufw/sysctl.conf it reads: 

&quot;Please note these settings override /etc/sysctl.conf and /etc/sysctl.d. If you prefer to use /etc/sysctl.conf, please adjust IPT_SYSCTL in /etc/default/ufw.&quot; 

Let's start by modifying /etc/default/ufw, use one of the two options, nano if you're comfortable with using nano, or gedit if you'd rather use a graphical editor: 

For nano copy/paste: sudo nano /etc/default/ufw
For gedit copy/paste: gksudo gedit /etc/default/ufw


Modify the following section to match this value: 

# IPT backend
# only enable if using iptables backend
IPT_SYSCTL=/etc/sysctl.conf


Save document and exit.


We've changed the default setting to specify
the use of /etc/sysctl.conf here.


Now we modify the /etc/sysctl.conf file. Start
the editor you wish to use, nano or gedit:


sudo nano /etc/sysctl.conf gksudo gedit /etc/sysctl.conf 

* Uncomment (remove the '#' before each line) the following sections: (these are my recommended settings) If you prefer, you could simply copy/paste these lines into /etc/sysctl.conf rather than hunting down each section for uncommenting, it's faster: 

kernel.printk = 3 4 1 3
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.tcp_syncookies=1
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0
net.ipv4.conf.all.log_martians = 1


* Copy/paste the following into /etc/sysctl.conf: 

#from /etc/sysctl.d
kernel.kptr_restrict = 1
kernel.yama.ptrace_scope = 1
vm.mmap_min_addr = 65536


* Copy/paste the following into /etc/sysctl.conf: 

#from /etc/ufw/ directory
net.ipv4.icmp_echo_ignore_broadcasts=1
net.ipv4.icmp_ignore_bogus_error_responses=1
net.ipv4.icmp_echo_ignore_all=0


Save the document and exit, now copy/paste at the command line: 

sudo sysctl -p 

and you're done with the sysctl configuration! If you know what you're doing, you may alter the configuration above, but know what you're doing before you add anything further, or subtract from my recommended settings. 

References: 

- [https://en.wikipedia.org/wiki/Sysctl](https://en.wikipedia.org/wiki/Sysctl) 

After completion: 

sudo ufw disable
sudo ufw enable


When you've finished using the sudo command in your Terminal, close it out with: 

sudo -K 

followed by: 

exit 

If you're continuing to use sudo for other operations at the command line, don't type sudo -K until you've finished. 

################################################### 

**Part 3: (. Moderate .) - Configuring before*.rules**


I won't elaborate on the purpose of this section, it should become obvious should you read the files. The following are my recommendations: 

sudo nano /etc/ufw/before.rules
or: gksudo gedit /etc/ufw/before.rules


under #ok icmp codes comment all entries in this section by adding a # mark at the beginning of each line. There's no reason for my computer to allow icmp. I don't care what someone else says or why, this is my preference, ignore me here if your preferences are different. 

under #allow dhcp to work comment out the line if your system is setup for static ip use, if your system needs dhcp for networking, do not comment this section, leave it as-is. 

under #allow MULTICAST mDNS for service discovery comment out the line 

under #allow MULTICAST UPnP for service discovery comment out the line 

Save file and exit 

Repeat the above configuration modifications to the file before6.rules, loading it with nano or gedit, save and exit. 

After completion: 

sudo ufw disable
sudo ufw enable


When you've finished using the sudo command in your Terminal, close it out with: 

sudo -K 

followed by: 

exit 

If you're continuing to use sudo for other operations at the command line, don't type sudo -K until you've finished. 

################################################### 

**Part 4: (. Advanced .) - Blocking Private Networks**


I assume you know what you're doing in this portion of the guide. If you do not, please skip this section. 

To block private networks (including the pesky multicast if you don't need it) this works, but look out for the 192.168.0.0/16 which may be your local private network and shouldn't be blocked. 

Subsection 2(1): Blocking Private Networks: [1] 

sudo ufw deny out to 10.0.0.0/8
sudo ufw deny out to 172.16.0.0/12
sudo ufw deny out to 192.168.0.0/16


2(1),[1] References:
- [https://en.wikipedia.org/wiki/Private_network#Private_IPv4_address_spaces](https://en.wikipedia.org/wiki/Private_network#Private_IPv4_address_spaces)
- [https://tools.ietf.org/html/rfc1918](https://tools.ietf.org/html/rfc1918)


Subsection 2(2): Blocking MULTICAST: [2] [2/I]


sudo ufw deny out to 239.0.0.0/10 (or 239.0.0.0/8) sudo ufw deny out to 224.0.0.0/4 

2(2),[2] References:
- [https://en.wikipedia.org/wiki/Multicast_address](https://en.wikipedia.org/wiki/Multicast_address)
- [https://www.ietf.org/rfc/rfc2365.txt](https://www.ietf.org/rfc/rfc2365.txt)


2(2),[2/I] Information: Google about MULTICAST and many users on the web experiencing flooding from their routers with messages in their log from these addresses frustrating them. You may ignore these messages if you see them in your logs by backtracking to Part 2 in this guide above, and modifying the line within /etc/sysctl.conf to: net.ipv4.conf.all.log_martians = 0 instead of the value = 1. Personally, I like seeing martians logged, you may not, for reasons of sanity when combing log files and disk space. 

When you've finished using the sudo command in your Terminal, close it out with: 

sudo -K 

followed by: 

exit 

If you're continuing to use sudo for other operations at the command line, don't type sudo -K until you've finished.

---

### Post by MadsRC on 2011-12-12
Is there a reason you don't do:
```
sudo ufw deny out to any
```and then just do:
```
sudo ufw allow out 20,21,53,80,123,442/tcp
sudo ufw allow out 20,21,53,80,123,442/udp
```That would give the samre result, but make the UFW status more readable (IE you actually see what ports are open, instead of which are closed).

My UFW Status Verbose looks like:
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
20,21,80,443,8001/tcp      ALLOW OUT   Anywhere
1863/tcp                   ALLOW OUT   Anywhere
465                        ALLOW OUT   Anywhere
993                        ALLOW OUT   Anywhere
51413                      ALLOW OUT   Anywhere
23399                      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere

```Or is there something I missed?

---

### Post by fairskies on 2011-12-12
Thank you for the information, have you tested this with a leak test? 

Is it possible to create a default deny out rule as your ufw status output appears strange: 

> Default: deny (incoming), **allow (outgoing)**Take notice of the > allow (outgoing) part 

then: 

> Anywhere                   DENY OUT    AnywhereOr is this simply how ufw works, you can, as you've demonstrated, deny out but ufw doesn't allow for a default deny out option? In my opinion this is something the developers should allow for, if it's not available, a default deny out option instead of a rule which conflicts with the default outbound status display. 

I'll test this myself and if it works on my system, which I'm sure it will, thank you, I'll edit my OP to include your suggestion above my suggestion as the method of choice in handling the issue.

---

