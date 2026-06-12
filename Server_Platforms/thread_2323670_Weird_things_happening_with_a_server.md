---
title: "Weird things happening with a server"
date: 2016-05-07
forum: Server Platforms
---

### Post by soamz on 2016-05-07
I have a server, which has 2 ports only. 
1 port is connected directly to the router to give it the public IP access. 
2nd port is connected to my access network switch, which has more than 100+ devices, which are on private IP, 7.7.7.xxx , 10.10.10.xxx , 10.10.11.xxx


Now in the server, all the devices show up perfectly fine, if I do arp -a command.

But if I try to ping any random devices, it doesnt ping. Then again it starts pinging after 5 mins, again stops, again pings in 1 day. Its all random ghost!

What could be the issue. 

here is what my etc/network/interfaces look like. 
Do you see an idea with the config ?

---

### Post by darkod on 2016-05-07
1. 7.7.7.x is NOT a private network!!! Yes, it can work if you do proper routing rules, etc, but there are enough private subnets to use and you should be careful and leave the public subnets alone. The private subnets are 10.x.x.x, 172.16.x.x and above, and 192.168.x.x.

For example, 172.10.x.x is public, but 172.20.x.x is private.

So, I suggest you change the 7.7.7.x to something like 10.10.12.x.

2. No need to use the 'network' option in /etc/network/interfaces. It is calculated from netmask automatically. It only creates possibility for an error. In fact in your case I think the 'network' option is a problem because you use netmask 255.0.0.0 and not 255.255.255.0. In such case the 'network' value you are using is not correct.

3. Related to the above: If you plan to use a subnet like 10.10.10.x better to use netmask 255.255.255.0, not 255.0.0.0 like in your case. It splits the subnet more appropriately.

4. You use only one gateway, not on each interface. Unless your setup needs it, but in this case I think it doesn't.

So, with all of the above, change your three private interfaces to:
```
address 10.10.10.250
netmask 255.255.255.0
```

That's all you need. Adjust for 10.10.11.x and 10.10.12.x accordingly. And you don't need to use .250 unless you really want to. If you plan this machine to be the gateway for the clients on those private networks, usually you would make this machine to be 10.10.10.1 and the clients use that IP as gateway. But you can use 10.10.10.250 if you prefer. Just use it accordingly later.

---

### Post by soamz on 2016-05-07
7.7.7.XXX series is fine. 
But its the serious of 10.10.11.xx and 10.10.10.xx which is going crazy.

---

### Post by darkod on 2016-05-07
That's because the network and netmask parameters are good for 7.7.7.x and not for the other two. Did you read the whole of my post? Because you didn't say anything more about it. Why do you ask if you don't want to apply the answers?

And just because that subnet work right now, that doesn't change the fact that it is NOT a private subnet and you should NOT use it as such... But have it your way...

---

### Post by soamz on 2016-05-07
leaving the 7.7.7.xx thing, as it works perfect. 


Only changing this in the interfaces


iface eth1:2 inet static
       address 10.10.10.250
       netmask 255.255.255.0




iface eth1:3 inet static
        address 10.10.11.250
        netmask 255.255.255.0

Now it looks like this. 
Still it doesnt ping. 
For example, 7.7.7.1 pings, 7.7.7.4 pings, but 7.7.7.3 doesnt ping 7.7.7.203 doesnt ping. [ATTACH=CONFIG]268889[/ATTACH]

> **darkod said:**
> 

2. No need to use the 'network' option in /etc/network/interfaces. It is calculated from netmask automatically. It only creates possibility for an error. In fact in your case I think the 'network' option is a problem because you use netmask 255.0.0.0 and not 255.255.255.0. In such case the 'network' value you are using is not correct.

Do you mean, remove the 3 private virtual interfaces entries from here ?
But if we do that, how will the server know the devices are connected ?

---

### Post by darkod on 2016-05-07
The interfaces settings look good now. What pings and what not will depend on client settings too, not just the server settings...

---

### Post by soamz on 2016-05-07
> **darkod said:**
> The interfaces settings look good now. What pings and what not will depend on client settings too, not just the server settings...

I removed everything from the interfaces, still the 7.7.7.xx and 10.10.10.xx and 10.10.11.xx pings. 
But its random, sometimes its pings and sometimes its not. 

I guess, the last solution left is putting a dedicated two /24 public IP :(

---

### Post by Habitual on 2016-05-07
> **darkod said:**
> 1. 7.7.7.x is NOT a private network!!! 
possibly.
```
NetRange:       7.0.0.0 - 7.255.255.255
CIDR:           7.0.0.0/8
NetName:        DISANET7
NetHandle:      NET-7-0-0-0-1
Parent:          ()
NetType:        Direct Allocation
OriginAS:       
Organization:   DoD Network Information Center (DNIC)
```

I find the references to 7.0.0.0/8 in this post to be laughable, and if this isn't a DoD system, 
they'd certainly be all up his backside about trying to use their AS 
and the OP wouldn't be posting for "help" on this venue. </opinion>

But if I was using a DoD assigned address in the 7.0.0.0/8 range I'd expect "Weird things to happen to my server."

---

### Post by soamz on 2016-05-07
> **darkod said:**
> The interfaces settings look good now. What pings and what not will depend on client settings too, not just the server settings...


See the screenshot. 
Tried 6 live devices, all 6 are live and showing on arp -a but doesnt ping from the server. 

Scratching my head now :(

1 pings , others are not, while all are live only. 
[ATTACH=CONFIG]268891[/ATTACH]

> **Habitual said:**
> possibly.
```
NetRange:       7.0.0.0 - 7.255.255.255
CIDR:           7.0.0.0/8
NetName:        DISANET7
NetHandle:      NET-7-0-0-0-1
Parent:          ()
NetType:        Direct Allocation
OriginAS:       
Organization:   DoD Network Information Center (DNIC)
```

I find 7.7.7.x in this post to be laughable, and if this isn't a DoD system, 
they'd certainly be all up his backside about trying to use their AS 
and the OP wouldn't be posting for "help" on this venue. </opinion>

its being used as private IP. 
We dont own it, neither its public.

---

### Post by volkswagner on 2016-05-07
In my opinion, it's unreasonable to come to this or any forum (even paid support) and expect help after sound advise has been given, but ignored.

If this were paid support for software, the simple response would be, "we don't support public ip ranges as private subnets".

It's not like you asked for networking help, and got marital advise.

Regardless of the fact that using 7.X.X.X address space MAY not be your problem, it's bad practice and MAY be causing this or other problems.
Until this is fixed, I wouldn't offer any advise.

Again, my opinions.

---

### Post by bab1 on 2016-05-07
> **soamz said:**
> I have a server, which has 2 ports only. 
1 port is connected directly to the router to give it the public IP access. 
2nd port is connected to my access network switch, which has more than 100+ devices, which are on private IP, 7.7.7.xxx , 10.10.10.xxx , 10.10.11.xxx

I agree completely with @volkswagner.  I don't think you understand TCP/IP networking at all.  In this instance you do not understand alias IP addressing of NIC interfaces.  Here is the rule you have to follow >  After the primary interface IP address (e.g. eth0 ipaddr) all additional network IP address must be in same subnet. For example if your eth0 using 10.0.0.7 IP address then alias must be setup using a subnet in the same network range as determined by the subnet mask. 
You simply can't do this```
7.7.7.xxx , 10.10.10.xxx , 10.10.11.xxx
```

---

### Post by soamz on 2016-05-07
> **volkswagner said:**
> In my opinion, it's unreasonable to come to this or any forum (even paid support) and expect help after sound advise has been given, but ignored.

If this were paid support for software, the simple response would be, "we don't support public ip ranges as private subnets".

It's not like you asked for networking help, and got marital advise.

Regardless of the fact that using 7.X.X.X address space MAY not be your problem, it's bad practice and MAY be causing this or other problems.
Until this is fixed, I wouldn't offer any advise.

Again, my opinions.

Sir, we have removed 7.7.7.x now. 
Now only left is 10.10.11.xx and 10.10.10.xx

Can you help suggest ?

> **bab1 said:**
> I agree completely with @volkswagner.  I don't think you understand TCP/IP networking at all.  In this instance you do not understand alias IP addressing of NIC interfaces.  Here is the rule you have to follow  
You simply can't do this```
7.7.7.xxx , 10.10.10.xxx , 10.10.11.xxx
```

bab, eth0 is the public IP. 
And eth1 is where the switch is connected which has all devices connected. 
It has devices like 10.10.11.xx and 10.10.10.xx

And I read, we should add virtual interfaces for eth1 if we have multiple subnets using. 

What did I miss ?

---

### Post by bab1 on 2016-05-07
> **soamz said:**
> bab, eth0 is the public IP. 
And eth1 is where the switch is connected which has all devices connected. 
It has devices like 10.10.11.xx and 10.10.10.xx

And I read, we should add virtual interfaces for eth1 if we have multiple subnets using. 

What did I miss ?
Everything.  You should start with understanding the basic principles of IP addressing.  There are thousands of pages on the Internet that provide information on this.  Where did you read "* we should add virtual interfaces for eth1 if we have multiple subnets using"*?
 
Regardless of what the NIC name is (eth0 or eth1 etc) you don't seem to understood what the point really is.  That being; all ***alias *** IP addresses of any interface must be in the same subnet as the base IP address of that interface.  These are ***alias*** IP addresses, not *virtual*; meaning they are alternatives to the base IP address of the interface.

---

### Post by soamz on 2016-05-07
> **bab1 said:**
> Everything.  You should start with understanding the basic principles of IP addressing.  There are thousands of pages on the Internet that provide information on this.  Where did you read "* we should add virtual interfaces for eth1 if we have multiple subnets using"*?
 
Regardless of what the NIC name is (eth0 or eth1 etc) you don't seem to understood what the point really is.  That being; all ***alias *** IP addresses of any interface must be in the same subnet as the base IP address of that interface.  These are ***alias*** IP addresses, not *virtual*; meaning they are alternatives to the base IP address of the interface.
[http://askubuntu.com/questions/549200/adding-virtual-interfaces-in-etc-network-interfaces-is-not-permanent](http://askubuntu.com/questions/549200/adding-virtual-interfaces-in-etc-network-interfaces-is-not-permanent)

---

### Post by bab1 on 2016-05-07
> **soamz said:**
> [http://askubuntu.com/questions/549200/adding-virtual-interfaces-in-etc-network-interfaces-is-not-permanent](http://askubuntu.com/questions/549200/adding-virtual-interfaces-in-etc-network-interfaces-is-not-permanent)
I'm not going to debate this with you.  Read the literature.  

You have to be able to discuss what you are doing, rather than using an unrelated hyperlink as your entire reply.

---

### Post by volkswagner on 2016-05-07
I'm not sure I agree with @bab1, I believe you can use alias interfaces for multiple subnets on same interface.
You definitely don't want to have multiple gateways though. Multiple gateways are a whole different animal, which I have yet to tackle.

I believe I've used virtual interfaces much like shown in the legacy model [here]("https://wiki.debian.org/NetworkConfiguration#Multiple_IP_addresses_on_one_Interface").

@soamz, please don't use screenshots to paste text results. Use the [HTML]```

```[/HTML] tags to wrap pasted text.

You should be able to use virtual interfaces or have multiple ipAddreses/netmask configured inside one interface, which is also show in above link.

The ping results shown on your earlier screen shot show pings to three hosts on same subnet, with two out of three not responding. This seems as it could
easily be a remote host issue, firewall issue, or other. Since one host in the same subnet does respond, it seems your config is working.

To update please post the following:

```
cat /etc/network/interfaces
```

```
route
```

```
iptables -L
```

In my experience "weird" or unexpected/unpredictable networking results was almost always related to some firewall rule or typo in network config.

Please also take the time to explain your environment/topology, hosts, switch(s), router, firewalls, etc. A [network diagram]("http://www.telecom.otago.ac.nz/tele301/student_html/virtualbox-vyatta-ubuntu-vlan.html") may be helpful.

---

### Post by soamz on 2016-05-08
Before I start typing the reply, Im looking for the THANK YOU BUTTON!!

Where is it ??

> **volkswagner said:**
> I'm not sure I agree with @bab1, I believe you can use alias interfaces for multiple subnets on same interface.
You definitely don't want to have multiple gateways though. Multiple gateways are a whole different animal, which I have yet to tackle.

I believe I've used virtual interfaces much like shown in the legacy model [here]("https://wiki.debian.org/NetworkConfiguration#Multiple_IP_addresses_on_one_Interface").

@soamz, please don't use screenshots to paste text results. Use the [HTML]```

```[/HTML] tags to wrap pasted text.

You should be able to use virtual interfaces or have multiple ipAddreses/netmask configured inside one interface, which is also show in above link.

The ping results shown on your earlier screen shot show pings to three hosts on same subnet, with two out of three not responding. This seems as it could
easily be a remote host issue, firewall issue, or other. Since one host in the same subnet does respond, it seems your config is working.

To update please post the following:

```
cat /etc/network/interfaces
```

```
route
```

```
iptables -L
```

In my experience "weird" or unexpected/unpredictable networking results was almost always related to some firewall rule or typo in network config.

Please also take the time to explain your environment/topology, hosts, switch(s), router, firewalls, etc. A [network diagram]("http://www.telecom.otago.ac.nz/tele301/student_html/virtualbox-vyatta-ubuntu-vlan.html") may be helpful.



Okay here are the output :

[HTML]
jetnms@jetnms:~$ cat /etc/network/interfaces# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).
# The loopback network interfaceauto lo eth0 eth1:1 eth1:2 eth1:3iface lo inet loopback
# The primary network interfaceiface eth0 inet static        address 103.194.232.9        netmask 255.255.255.240        network 103.194.232.0        broadcast 103.194.232.15        gateway 103.194.232.1        # dns-* options are implemented by the resolvconf package, if installed        dns-nameservers 8.8.8.8jetnms@jetnms:~$
jetnms@jetnms:~$ cat /etc/network/interfaces# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).
# The loopback network interfaceauto lo eth0 eth1:1 eth1:2 eth1:3iface lo inet loopback
# The primary network interfaceiface eth0 inet static        address 103.194.232.9        netmask 255.255.255.240        network 103.194.232.0        broadcast 103.194.232.15        gateway 103.194.232.1        # dns-* options are implemented by the resolvconf package, if installed        dns-nameservers 8.8.8.8jetnms@jetnms:~$[/HTML][HTML]


jetnms@jetnms:~$ routeKernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Ifacedefault         103.194.232.1   0.0.0.0         UG    0      0        0 eth07.7.7.0         *               255.255.255.0   U     0      0        0 eth110.10.10.0      *               255.255.255.0   U     0      0        0 eth110.10.11.0      *               255.255.255.0   U     0      0        0 eth1localnet        *               255.255.255.240 U     0      0        0 eth0jetnms@jetnms:~$
[/HTML]

[HTML]
jetnms@jetnms:~$ iptables -Lmodprobe: ERROR: could not insert 'ip_tables': Operation not permittediptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)Perhaps iptables or your kernel needs to be upgraded.

[/HTML]

Attached screenshot. 
[ATTACH=CONFIG]268914[/ATTACH]


[ATTACH=CONFIG]268915[/ATTACH]

The problem is, 
the devices ping from the server command line now, then stops after 5-10 mins, then again pings. 

I even monitor the ping every second, you can see how it comes and goes. 
[ATTACH=CONFIG]268916[/ATTACH]

And there is absolutely no issue with the devices, or remote hosts. 
IM able to ping them all continuous without fail. 

But they play tricks within the server only, dont know whats really happening.
Its ghost effect!!!!

For example, if I have a device, and I have set it to static IP 10.10.11.27 / 255.255.255.0 subnet / 10.10.11.1 default gateway.

It doesnt ping when I connect. 
While connected, I simply change the subnet to 255.0.0.0 or change gateway IP to 10.10.11.0 or something. 
Then immediately the ping starts working. 

Then again it stops after 5-10 mins, then again works, then if I refresh or change it to 255.255.255.0 , then again works, then again stops. 
It feels like, everytime the device gets restarted, ping works, then stops, vice versa. 

GHOST!!

I have removed the entries from /etc/network/interfaces , still I see the data inside the ifconfig command. 
Dont know, where it got hard coded. 

[ATTACH=CONFIG]268917[/ATTACH]

---

### Post by volkswagner on 2016-05-08
@soamz, please read the [FAQs]("http://ubuntuforums.org/faq.php?faq=policy#faq_vb3_board_usage") and learn about proper posting.

Perhaps my request to enter text in code tags was not easy to understand. I wrapped the request in html tags because
it was the easiest way to display. As a beginner you should avoid using "post quick reply" and use "go advanced". This way
you'll see the different tags to wrap you information. The code tags will properly format your text. As you can see in your html wrapped
paste, the info is not easily readable (not properly formatted).

I'll repeat, please don't use screenshots to post text based info. If you need a reason to follow this request I'll say this... For me, opening
a screenshot is inconvenient, the text contents can't be copied an pasted into my own searches to easily help you, it's also not searchable/indexable
by forum search or search engine bots. This means if someone has similar problem, config, or mis-config, it won't reference your post.

---

### Post by volkswagner on 2016-05-08
> **soamz said:**
> I have removed the entries from /etc/network/interfaces , still I see the data inside the ifconfig command. 
Dont know, where it got hard coded. 

[ATTACH=CONFIG]268917[/ATTACH]

Did you restart networking or reboot after making changes?

Also you'll need to use sudo for your iptables command. I didn't write sudo, because your previous posts showed you were logged in as root.

```
sudo iptables -L
```

---

### Post by soamz on 2016-05-09
yes, I had restarted and even restarted the server 3-4 times. 

Here is the output of iptables -L

```
[FONT=Menlo]jetnms@jetnms:~$ sudo -i[/FONT][FONT=Menlo][sudo] password for jetnms: [/FONT]
[FONT=Menlo]root@jetnms:~# iptables -L[/FONT]
[FONT=Menlo]Chain INPUT (policy ACCEPT)[/FONT]
[FONT=Menlo]target     prot opt source               destination         [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Chain FORWARD (policy ACCEPT)[/FONT]
[FONT=Menlo]target     prot opt source               destination         [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Chain OUTPUT (policy ACCEPT)[/FONT]
[FONT=Menlo]target     prot opt source               destination         [/FONT]
[FONT=Menlo]root@jetnms:~#[/FONT]
```

---

### Post by volkswagner on 2016-05-09
Do you have a Desktop environment installed (is network manager installed)?

Lets see if eth0 is found in configs elsewhere, please post output of following.

```
grep -R "eth0" /etc/
```

Let's make sure network-manager isn't running.
```
ls /etc/init.d
```

---

### Post by soamz on 2016-05-09
```

root@jetnms:~# grep -R "eth0" /etc/
/etc/initramfs-tools/initramfs.conf:# Specify a specific network interface, like eth0
/etc/rc4.d/S30pf_ring:  MGMT_INTERFACE="eth0"
grep: /etc/alternatives/ghostscript-current/Resource/CIDFSubst/DroidSansFallback.ttf: No such file or directory
/etc/rc6.d/K30pf_ring:  MGMT_INTERFACE="eth0"
/etc/bmon.conf: * element eth0 {
/etc/rc5.d/S30pf_ring:  MGMT_INTERFACE="eth0"
/etc/rc1.d/K30pf_ring:  MGMT_INTERFACE="eth0"
grep: /etc/blkid.tab: No such file or directory
/etc/samba/smb.conf:;   interfaces = 127.0.0.0/8 eth0
grep: /etc/ssl/certs/dcc9acbe.0: No such file or directory
grep: /etc/ssl/certs/50063f21.0: No such file or directory
grep: /etc/ssl/certs/80716153.0: No such file or directory
grep: /etc/ssl/certs/fcc9ee9a.0: No such file or directory
/etc/rc0.d/K30pf_ring:  MGMT_INTERFACE="eth0"
/etc/network/run/ifstate:eth0=eth0
/etc/network/run/ifstate.eth0:eth0
/etc/network/if-up.d/upstart:	# Ignoring unknown interface eth0=eth0.
/etc/network/interfaces~:auto lo eth0 eth1:1 eth1:2 eth1:3
/etc/network/interfaces~:iface eth0 inet static
Binary file /etc/network/.interfaces.swp matches
/etc/network/interfaces:auto lo eth0 eth1:1 eth1:2 eth1:3
/etc/network/interfaces:iface eth0 inet static
/etc/mail/sendmail.conf:# DAEMON_NETIF="eth0";  string SMTP interface(s)
/etc/mail/sendmail.conf:DAEMON_NETIF="eth0";
/etc/dhcp/dhclient.conf:#  interface "eth0";
/etc/dhcp/dhclient.conf:#  interface "eth0";
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:a0:0e:e6:20", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/init.d/pf_ring:  MGMT_INTERFACE="eth0"
/etc/rc2.d/S30pf_ring:  MGMT_INTERFACE="eth0"
/etc/rc3.d/S30pf_ring:  MGMT_INTERFACE="eth0"
root@jetnms:~#

```

```

root@jetnms:~# ls /etc/init.d
README                                              console-setup      mysql           procps          sendmail   umountnfs.sh
acpid                                               cron               networking      rc              sendsigs   umountroot
airControl2Server                                   dbus               nprobe          rc.local        single     unattended-upgrades
aircontrol-v2.0-beta21.1852.160506.1716-unix64.bin  dns-clean          ntop            rcS             skeleton   urandom
apache2                                             friendly-recovery  ntopng          reboot          smokeping  webmin
apparmor                                            grub-common        ondemand        redis-server    snmpd      x11-common
apport                                              halt               pf_ring         resolvconf      ssh
atd                                                 irqbalance         postfix         rsync           sudo
cento                                               killprocs          postgresql-9.5  rsyslog         udev
cluster                                             kmod               pppd-dns        screen-cleanup  umountfs
root@jetnms:~#

```

```

root@jetnms:~# grep -R "eth1" /etc/
/etc/modprobe.d/blacklist.conf:blacklist eth1394
grep: /etc/alternatives/ghostscript-current/Resource/CIDFSubst/DroidSansFallback.ttf: No such file or directory
grep: /etc/blkid.tab: No such file or directory
grep: /etc/ssl/certs/dcc9acbe.0: No such file or directory
grep: /etc/ssl/certs/50063f21.0: No such file or directory
grep: /etc/ssl/certs/80716153.0: No such file or directory
grep: /etc/ssl/certs/fcc9ee9a.0: No such file or directory
/etc/network/run/ifstate:eth1:1=eth1:1
/etc/network/run/ifstate:eth1:2=eth1:2
/etc/network/run/ifstate:eth1:3=eth1:3
/etc/network/run/ifstate.eth1:3:eth1:3
/etc/network/run/ifstate.eth1:2:eth1:2
/etc/network/run/ifstate.eth1:1:eth1:1
/etc/network/interfaces~:auto lo eth0 eth1:1 eth1:2 eth1:3
/etc/network/interfaces~:iface eth1:1 inet static
/etc/network/interfaces~:iface eth1:2 inet static
/etc/network/interfaces~:iface eth1:3 inet static
/etc/network/interfaces:auto lo eth0 eth1:1 eth1:2 eth1:3
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:a0:0e:e6:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
root@jetnms:~# 


```

---

### Post by volkswagner on 2016-05-09
I'm not saying this is wrong, but I don't think it is the best laid out method of addressing interfaces.

In your /etc/network/interfaces you have:
```
auto lo eth0 eth1:1 eth1:2 eth1:3
```

The auto directive should be located at each interface not all interfaces in one line. This way if you delete an interface, you won't forget to remove the auto directive.

Here is my example:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
 auto eth0
 iface eth0 inet static
        address 192.168.7.2
        netmask 255.255.255.0
        network 192.168.7.0
        broadcast 192.168.7.255
        dns-search home
        dns-nameservers 192.168.7.5 192.168.7.1
```

You'll also notice a file like /etc/network/interfaces~
You should delete that file and clean up your interfaces file, restart networking and see if stale interfaces still show up.

```
sudo rm /etc/network/interfaces~
```

I'm not sure what causes those files with the tilde on the end. I thought it was a file lock mechanism when editing with a graphical text editor. Again, I'm not 
sure what causes those odd name, but I'm pretty sure they can cause issues.

You didn't explain your network topology, nor the reason for segmenting your LAN.

---

### Post by soamz on 2016-05-10
> **volkswagner said:**
> I'm not saying this is wrong, but I don't think it is the best laid out method of addressing interfaces.

In your /etc/network/interfaces you have:
```
auto lo eth0 eth1:1 eth1:2 eth1:3
```

The auto directive should be located at each interface not all interfaces in one line. This way if you delete an interface, you won't forget to remove the auto directive.

Here is my example:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
 auto eth0
 iface eth0 inet static
        address 192.168.7.2
        netmask 255.255.255.0
        network 192.168.7.0
        broadcast 192.168.7.255
        dns-search home
        dns-nameservers 192.168.7.5 192.168.7.1
```

You'll also notice a file like /etc/network/interfaces~
You should delete that file and clean up your interfaces file, restart networking and see if stale interfaces still show up.

```
sudo rm /etc/network/interfaces~
```

I'm not sure what causes those files with the tilde on the end. I thought it was a file lock mechanism when editing with a graphical text editor. Again, I'm not 
sure what causes those odd name, but I'm pretty sure they can cause issues.

You didn't explain your network topology, nor the reason for segmenting your LAN.


1. I had removed it all from /etc/network/interfaces 2 days back and also restarted the server. When I do sudo nano to that /etc/network/interfaces also, I dont see the entries. But is it like, getting cached somewhere ? Weird. 

2. Confused about the auto directive thing, which you stated. 

3. Do you mean, delete the /etc/network/interfaces file and create a new file ? 

4. Okay here is the network topology : I have access network which has lets say 6 managed switches, 2 are on 10.10.10.2 , 10.10.10.3 and other 2 are on 10.10.11.2 , 10.10.11.3 and other 2 are on 7.7.7.2 and 7.7.7.3

so, its like 3 different IP private ranges. 
And all those 6 switches are connected to one switch, which is then connected to the server 2nd ether port thats how the server is able to ping to those devices.

---

### Post by volkswagner on 2016-05-10
I'm finding it very difficult to get anywhere with you. Perhaps English is not your native language, but it's the only one that I know.

According to your output in post#28, you did not remove ALL references to your alias interfaces. According to post#28 your /etc/network/interfaces file contains the following:

```
auto lo eth0 eth1:1 eth1:2 eth1:3
```

Please change it to:
```
auto lo
```

Please read  my last post again, for some reason things are just passing you by, and I have to reword or rewrite. Look at my example, see how my loopback just has "auto lo"
then the next line is also only referencing the loopback with "iface lo inet loopback". My eth0 interface has it's own line "auto eth0", then the remaining config for just eth0.

I'm saying again, you didn't remove ALL information regarding eth1:1, eth1:2, etc.

I said you have a file called /etc/network/interfaces~. I also mentioned the [tilde]("https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=tilde") at the end. I also asked you to delete it with the following command:

```
sudo rm /etc/network/interfaces~
```
Then restart networking or reboot.

Please explain why I should continue to help, when it seems you don't read what people post?

Again, please don't use 7.7.7.anything. Just because I can use a watermelon as a hat doesn't mean I should.
There are plenty of private subnets to use, you should not be using 7.7.7.x

I can only think of one good reason to use a public ip as a private ip. Let's say for example you are developing a website, which has a public ip of 7.7.7.97, but you don't want to edit files directly on the server for development, but you also want to test using the domain.com. You could simply edit the /etc/hosts file on you development machine to point the public ip to the ip of the development server.

What are you using Webmin for? I think Webmin can be the cause of your files containing a tilde. Using Webin will create unexpected and undesired results with Ubuntu. It hasn't been supported in nearly ten years. Yes, you can install it, yes you can use it, but do expect strange results.

---

### Post by soamz on 2016-05-10
> **volkswagner said:**
> I'm finding it very difficult to get anywhere with you. Perhaps English is not your native language, but it's the only one that I know.

According to your output in post#28, you did not remove ALL references to your alias interfaces. According to post#28 your /etc/network/interfaces file contains the following:

```
auto lo eth0 eth1:1 eth1:2 eth1:3
```

Please change it to:
```
auto lo
```

Please read  my last post again, for some reason things are just passing you by, and I have to reword or rewrite. Look at my example, see how my loopback just has "auto lo"
then the next line is also only referencing the loopback with "iface lo inet loopback". My eth0 interface has it's own line "auto eth0", then the remaining config for just eth0.

I'm saying again, you didn't remove ALL information regarding eth1:1, eth1:2, etc.

I said you have a file called /etc/network/interfaces~. I also mentioned the [tilde]("https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=tilde") at the end. I also asked you to delete it with the following command:

```
sudo rm /etc/network/interfaces~
```
Then restart networking or reboot.

Please explain why I should continue to help, when it seems you don't read what people post?

Again, please don't use 7.7.7.anything. Just because I can use a watermelon as a hat doesn't mean I should.
There are plenty of private subnets to use, you should not be using 7.7.7.x

I can only think of one good reason to use a public ip as a private ip. Let's say for example you are developing a website, which has a public ip of 7.7.7.97, but you don't want to edit files directly on the server for development, but you also want to test using the domain.com. You could simply edit the /etc/hosts file on you development machine to point the public ip to the ip of the development server.

What are you using Webmin for? I think Webmin can be the cause of your files containing a tilde. Using Webin will create unexpected and undesired results with Ubuntu. It hasn't been supported in nearly ten years. Yes, you can install it, yes you can use it, but do expect strange results.


Sorry, I just meant not to make any mistake. 
Now, I have made it auto lo. 
And also removed the file. 

And then rebooted. 

Now the server is not reachable :(

[FONT=Menlo]MacBook-Pro-4:~ soamz$ ssh jetnms@103.194.232.9[/FONT]
[FONT=Menlo]ssh: connect to host 103.194.232.9 port 22: Network is unreachable[/FONT]

---

### Post by Habitual on 2016-05-10
I thought the tilde files were from ~/.vimrc
```
set backup
set backupcopy=yes
```

---

### Post by soamz on 2016-05-10
> **Habitual said:**
> I thought the tilde files were from ~/.vimrc
```
set backup
set backupcopy=yes
```

The server has lost connectivity. 
I need to run to office and connect cable. 
So, login to ubuntu local and do what ?

As the /etc/network/interfaces still have the public IP, but still the server is not reachable. 

Clue less, why it broke

---

### Post by The Cog on 2016-05-10
It's a shame you didn't manage to post the original interfaces file. Anyway, here's one I made up which I suggest you use as a replacement for when you get to site.```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 103.194.232.9
    netmask 255.255.255.240
    gateway 103.194.232.15
    dns-nameservers 8.8.8.8

auto eth1:1
iface eth1:1 inet static
    address 7.7.7.250
    netmask 255.255.255.0
    #gateway 7.7.7.1

auto eth1:2
iface eth1:2 inet static
    address 10.10.10.250
    netmask 255.255.255.0
    #gateweay 10.10.10.1

auto eth1:3
iface eth1:3 inet static
    address 10.10.11.250
    netmask 255.255.255.0
    #gateway 10.10.11.1

```
A few points:

Files ending with '~' are often dropped by text editors, and are a backup copy of the previous version, made when you save changes. Useful for recovering from mistakes.

You need to restart networking after making a change to the interfaces file: **sudo service networking restart**

Using 7.x.x.x locally will not do any harm except that you will never be able to connect to devices belonging to the real owner of 7.x.x.x over the internet. 
In theory, you or network administrator should use filtering to prevent packets sourced from 7.x.x.x being sent towards the internet where they may be mistaken for packets from the real 7.x.x.x. 
Actually, your ISP should be doing that filtering too, but I think many ISPs don't bother.

Specifying multiple default gateways (on different interfaces) can be problematic, and I don't recommend it. That's why I have commented out the other ones in the above file. If you have an interface in each subnet that you want to talk to, there should be no need to use a gateway (router) to talk to the local devices anyway.

Using multiple IP addresses will not necessarily be a problem, but also may not be needed. However, you must make sure you use the same subnet mask as the other machines on the network are configured for. Log onto some other machines and use the command ifconfig (or ipconfig on windows). If the proper mask is 255.0.0.0 then both eth1:2 and eth1:3 are in the same subnet, and you don't need both addresses, you might as well remove one of them. 

If proper the mask is 255.255.255.0 (I suspect it is) then the interfaces are in different subnets. You may choose to place a network interface into each subnet  (as you have done).However, I would guess that your other devices don't all have multiple IP addresses configured. I guess that most only have one address and that there is a router somewhere that provides connectivity between the different subnets. The simplest thing for you do is to use the same scheme. Just pick one local address, and use the internal router to talk to other subnets. Below is a sample interfaces config that may well work for you:
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 103.194.232.9
    netmask 255.255.255.240
    gateway 103.194.232.15
    dns-nameservers 8.8.8.8

auto eth1
iface eth1 inet static
    address 10.10.10.250
    netmask 255.255.255.0
    up ip route add 7.7.7.0/24 via 10.10.10.1
    up ip route add 10.10.17.0/24 via 10.10.10.1


```

Getting the mask wrong may well be the cause of your intermittent ping problems. For instance, the multicast addresses used in ARP requests won't be recognised and responded to as expected.

---

### Post by soamz on 2016-05-10
> **The Cog said:**
> It's a shame you didn't manage to post the original interfaces file. Anyway, here's one I made up which I suggest you use as a replacement for when you get to site.```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 103.194.232.9
    netmask 255.255.255.240
    gateway 103.194.232.15
    dns-nameservers 8.8.8.8

auto eth1:1
iface eth1:1 inet static
    address 7.7.7.250
    netmask 255.255.255.0
    #gateway 7.7.7.1

auto eth1:2
iface eth1:2 inet static
    address 10.10.10.250
    netmask 255.255.255.0
    #gateweay 10.10.10.1

auto eth1:3
iface eth1:3 inet static
    address 10.10.11.250
    netmask 255.255.255.0
    #gateway 10.10.11.1

```
A few points:

Files ending with '~' are often dropped by text editors, and are a backup copy of the previous version, made when you save changes. Useful for recovering from mistakes.

You need to restart networking after making a change to the interfaces file: **sudo service networking restart**

Using 7.x.x.x locally will not do any harm except that you will never be able to connect to devices belonging to the real owner of 7.x.x.x over the internet. 
In theory, you or network administrator should use filtering to prevent packets sourced from 7.x.x.x being sent towards the internet where they may be mistaken for packets from the real 7.x.x.x. 
Actually, your ISP should be doing that filtering too, but I think many ISPs don't bother.

Specifying multiple default gateways (on different interfaces) can be problematic, and I don't recommend it. That's why I have commented out the other ones in the above file. If you have an interface in each subnet that you want to talk to, there should be no need to use a gateway (router) to talk to the local devices anyway.

Using multiple IP addresses will not necessarily be a problem, but also may not be needed. However, you must make sure you use the same subnet mask as the other machines on the network are configured for. Log onto some other machines and use the command ifconfig (or ipconfig on windows). If the proper mask is 255.0.0.0 then both eth1:2 and eth1:3 are in the same subnet, and you don't need both addresses, you might as well remove one of them. 

If proper the mask is 255.255.255.0 (I suspect it is) then the interfaces are in different subnets. You may choose to place a network interface into each subnet  (as you have done).However, I would guess that your other devices don't all have multiple IP addresses configured. I guess that most only have one address and that there is a router somewhere that provides connectivity between the different subnets. The simplest thing for you do is to use the same scheme. Just pick one local address, and use the internal router to talk to other subnets. Below is a sample interfaces config that may well work for you:
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 103.194.232.9
    netmask 255.255.255.240
    gateway 103.194.232.15
    dns-nameservers 8.8.8.8

auto eth1
iface eth1 inet static
    address 10.10.10.250
    netmask 255.255.255.0
    up ip route add 7.7.7.0/24 via 10.10.10.1
    up ip route add 10.10.17.0/24 via 10.10.10.1


```

Getting the mask wrong may well be the cause of your intermittent ping problems. For instance, the multicast addresses used in ARP requests won't be recognised and responded to as expected.


Cog, thanks for your code. 
You pasted two. Shall I try with the 1st one first ? 


And in all the devices one 7.7.7.x, we have gateway as 7.7.7.1 and the ones with IP 10.10.11.x, they have subnet as 255.255.255.0 and gateway as 10.10.11.1 and same for 10.10.10.x and so on. 
So, basically all the managed switches or routers which has a private IP, its set this way.

---

### Post by The Cog on 2016-05-10
> **soamz said:**
> Cog, thanks for your code. 
You pasted two. Shall I try with the 1st one first ? 


And in all the devices one 7.7.7.x, we have gateway as 7.7.7.1 and the ones with IP 10.10.11.x, they have subnet as 255.255.255.0 and gateway as 10.10.11.1 and same for 10.10.10.x and so on. 
So, basically all the managed switches or routers which has a private IP, its set this way.

In that case, I would suggest trying the second one first. I think that will probably do what you want and be more "normal" than the second. But either should at least restore your remote connectivity.

Sorry I didn't reply sooner - I was in the pub.

---

### Post by soamz on 2016-05-11
> **The Cog said:**
> In that case, I would suggest trying the second one first. I think that will probably do what you want and be more "normal" than the second. But either should at least restore your remote connectivity.

Sorry I didn't reply sooner - I was in the pub.


Cog, now the server is back online. 
And here is the interfaces file.
```


  GNU nano 2.2.6                         File: /etc/network/interfaces                                                         


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 103.194.232.9
        netmask 255.255.255.240
        gateway 103.194.232.1
        dns-nameservers 8.8.8.8


auto eth1
iface eth1 inet static
        address 10.10.10.250
        netmask 255.255.255.0
        up ip route add 7.7.7.0/24 via 10.10.10.1
        up ip route add 10.10.11.0/24 via 10.10.10.1

```

Still the same issue. Some pings and some doesnt.

All 7.7.7.xx and 10.10.11.xx are down now. 

Only 10.10.10.xx are all working.

And if I do this, then it says fail for ll network services :

```

# The primary network interface
auto eth0
iface eth0 inet static
    address 103.194.232.9
    netmask 255.255.255.240
    gateway 103.194.232.15
    dns-nameservers 8.8.8.8

auto eth1:1
iface eth1:1 inet static
    address 7.7.7.250
    netmask 255.255.255.0
    #gateway 7.7.7.1

auto eth1:2
iface eth1:2 inet static
    address 10.10.10.250
    netmask 255.255.255.0
    #gateweay 10.10.10.1

auto eth1:3
iface eth1:3 inet static
    address 10.10.11.250
    netmask 255.255.255.0
    #gateway 10.10.11.1
```

Bro, is there any chance the network card is buggy ?
Can that be a reason or some ghost effect ?

---

### Post by The Cog on 2016-05-12
Aargh! There is a typo in that second interfaces file. Somehow there is an unwanted 5 at the end of the gateway address for eth0. Eth0 should definitely have **gateway 103.194.232.1**.

No I'm sure the network card is not buggy. Something else is going on.

Since you don't seem to be able to route between the three local LANs, then I guess you really do need the three separate subinterfaces of eth1, one on each subnet. So go with the first interfaces file I posted, but correct the eth0 gateway.

Once that's stable, let's look at the ping problem again. When pings aren't working, do all addresses stop pinging at the same time, or just one/some addresses. Could it be that one subnet (e.g. 10.10.10.x) stops pinging while the other subnets still ping?

One thing that may help: When you find one address not answering pings, can you try to ping it in one console and while the ping is failing, run this command in another window for 5-6 seconds:
```
sudo tcpdump -np -i eth1 icmp or arp
```
then post the output here. Please use code tags (the # symbol in the Go Advanced reply editor) not html tags.
We'll see what we can work out from that trace. Actually, it may be good if you can run the same trace when the same ping target is working as well, for comparison.

---

### Post by soamz on 2016-05-12
> **The Cog said:**
> Aargh! There is a typo in that second interfaces file. Somehow there is an unwanted 5 at the end of the gateway address for eth0. Eth0 should definitely have **gateway 103.194.232.1**.

No I'm sure the network card is not buggy. Something else is going on.

Since you don't seem to be able to route between the three local LANs, then I guess you really do need the three separate subinterfaces of eth1, one on each subnet. So go with the first interfaces file I posted, but correct the eth0 gateway.

Once that's stable, let's look at the ping problem again. When pings aren't working, do all addresses stop pinging at the same time, or just one/some addresses. Could it be that one subnet (e.g. 10.10.10.x) stops pinging while the other subnets still ping?

One thing that may help: When you find one address not answering pings, can you try to ping it in one console and while the ping is failing, run this command in another window for 5-6 seconds:
```
sudo tcpdump -np -i eth1 icmp or arp
```
then post the output here. Please use code tags (the # symbol in the Go Advanced reply editor) not html tags.
We'll see what we can work out from that trace. Actually, it may be good if you can run the same trace when the same ping target is working as well, for comparison.

1. Bro, I had placed 1 only, thats how I had internet back to the server, so thats fine. 

2. Do you mean, keep eth1 only to 10.10.10.xx for like 1-2 hours and monitor all 10.10.10.x devices and see if any issues or not ?

Its random!
For example, 7.7.7.207, 10.10.11.33 , 10.10.10.21 stops. 
And they stop and come back to life also randomly.

For example 10.10.10.21 doesnt ping now. 

If I run, sudo tcpdump -np -i eth1 icmp or arp shows a huge long list of output.

YOu can see the screenshot. 
How pings work and then dissapear. 

Even trace fails when it fails.

See the video, 
[https://youtu.be/UZWhlsRDV1E](https://youtu.be/UZWhlsRDV1E)

You can see how 10.10.11.2 and 10.10.11.27 was not pinging, I refresh device ping instantly worked.

If I keep the ping on, then the device doesnt stop.

But I stop the ping and then try again after 5 mins, the device doesnt ping anymore.

---

### Post by The Cog on 2016-05-13
OK, what I get from the video is that these two switches 10.10.11.27 and 10.10.11.2 had problems independently : you reset one and it starts working, but the other one still doesn't work until you reset that one as well. You don't lose all of them at the same time.

I also saw that 10.10.11.x is on VLAN1. 
Can I ask what VLAN the other two subnets (10.10.10.x and 7.7.7.x) are on? 

Can you post the output of  the command "ipconfig /all" and "route print" from your windows PC. This might give some clues, as the windows box is clearly still able to talk to the boxes that Ubuntu can't.

Does the problem still happen if you shut down two of the three local interfaces ("sudo ifdown eth1:1" and "sudo ifdown eth1:2") and leave just one local interface left active?

Can you estimate how many lines per second the previous tcpdump was outputting? 
Can you post the output of this command (while a failed ping is running in anther console) - it should print 20 lines and stop:
sudo tcpdump -np -e -c 20 -i eth1 icmp or arp

Is it only the switches that stop answering pings, or does it ever happen with windows boxes too? If it happens with windows boxes, can you run the command "arp -a" and check the arp entry for when it's working and when it's not.

I have a feeling that it might be an ARP problem in the devices you are trying to ping, or a MAC forwarding table problem in the switches somewhere, possibly a bridging loop between two switches.

---

### Post by soamz on 2016-05-14
> **The Cog said:**
> OK, what I get from the video is that these two switches 10.10.11.27 and 10.10.11.2 had problems independently : you reset one and it starts working, but the other one still doesn't work until you reset that one as well. You don't lose all of them at the same time.

I also saw that 10.10.11.x is on VLAN1. 
Can I ask what VLAN the other two subnets (10.10.10.x and 7.7.7.x) are on? 

Can you post the output of  the command "ipconfig /all" and "route print" from your windows PC. This might give some clues, as the windows box is clearly still able to talk to the boxes that Ubuntu can't.

Does the problem still happen if you shut down two of the three local interfaces ("sudo ifdown eth1:1" and "sudo ifdown eth1:2") and leave just one local interface left active?

Can you estimate how many lines per second the previous tcpdump was outputting? 
Can you post the output of this command (while a failed ping is running in anther console) - it should print 20 lines and stop:
sudo tcpdump -np -e -c 20 -i eth1 icmp or arp

Is it only the switches that stop answering pings, or does it ever happen with windows boxes too? If it happens with windows boxes, can you run the command "arp -a" and check the arp entry for when it's working and when it's not.

I have a feeling that it might be an ARP problem in the devices you are trying to ping, or a MAC forwarding table problem in the switches somewhere, possibly a bridging loop between two switches.


Yes, i have sets of switches, routers, POPs, one runs on 7.7.7.x and one on 10.10.10.xx and one on 10.10.11.x 
All 3 are connected to the same switch. 
I connected a PC and kept the ping to all those switches from the PC Run CMD screen and not a single ping breaks. 

But the server pings and breaks, pings and breaks. 


Right now, I have removed all virtual interfaces and only kept this, 

```





# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 103.194.232.9
        netmask 255.255.255.240
        gateway 103.194.232.1
        dns-nameservers 8.8.8.8


auto eth1
iface eth1 inet static
        address 10.10.12.1
        netmask 255.255.255.0





```

And made 3 switches IP 10.10.12.5 , 10.10.12.6 and 10.10.12.7 

And rebooted the server. 
Still they doesnt ping, only gateway 10.10.12.1 IP pings.

---

