---
title: "My first server attempt: I can access my web page but no-one else can."
date: 2007-03-07
forum: Server Platforms
---

### Post by BongoBob on 2007-03-07
Hello. I recently installed an Ubuntu 6.06 LAMP server, and configured it using mainly [this guide]("http://www.cjfay.com/lamp.html") and various other google sources. I can access my web page just fine on all the computers on my network by using [my IP]("http://68.108.182.226:80"), but none of my friends can. I'm on a Linksys BEFSR41v3 router, I configured a static IP for the server server, and forwarded port 80 to the static IP on both UDP and TCP.

Can anyone help me out or point me in the right direction?

Thanks in advance.

-BongoBob

---

### Post by Mr. C. on 2007-03-07
If that IP is correct, you are not pingable, and there is no response from any services.  Your firewall is blocking traffic.

MrC

---

### Post by BongoBob on 2007-03-07
Ok, this is probably a *really* newbish question, but does the LAMP install install a firewall automatically? If so how do I configure it to fix this? Or are you simply talking about my Router?

---

### Post by Mr. C. on 2007-03-07
I can't tell what is doing the blocking - it could be your router, or your linux system.  By default, I do not believe your linux system has it configured. Find out as in a terminal window:

sudo iptables -L

if you get :

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

there are no firewall rules enabled, and it is your router.

All one can tell from the outside is either a) nothing responds, therefore its blocked, or b) there is a response but the connection fails.  I see (a).

MrC

---

### Post by BongoBob on 2007-03-07
Well after looking around in my routers configuration page I found under UPnP HTTP port 80 was disabled, so I enabled it and set it to my servers static ip.

If anyone can test and see if this works I would really appreciate it.

[http://68.108.182.226:80/](http://68.108.182.226:80/)

-BongoBob

---

### Post by Mr. C. on 2007-03-07
HTTP has nothing to do with UPnP.

All you need is to port forward port 80 WAN to your LAN server's IP address port 80

You are still blocked.

MrC

---

### Post by BongoBob on 2007-03-07
I figured that UPnP had nothing to do with it, but I figured it was worth a shot anyways.

I already have port 80 forwarded to my static IP.

Here's a screenshot of my routers config page...

[http://img179.imageshack.us/img179/939/portsscreenshotzf5.png](http://img179.imageshack.us/img179/939/portsscreenshotzf5.png)

---

### Post by Mr. C. on 2007-03-07
Yes, indeed, that is correct.  Good.

Is this on a vmware server, or native install?

Does your router have any diag tools (like ping, etc.) under Status, or elsewhere?  Or Logs showing number of packets accepted, blocked, etc. ? I don't recall all the pages on that router. 

MrC

---

### Post by BongoBob on 2007-03-07
It is a native install.

There is a Log page, but it says Logviewer IP Adress: 192.168.1.255

Is this correct?

EDIT: I turned on the log and it's working.

---

### Post by Mr. C. on 2007-03-07
Ok, I'm trying again to connect.  You should see log entries from a 204.11... address.

Do you see any?

---

### Post by Mr. C. on 2007-03-07
Wait, hold the presses!

I see that your edit on the previous post shows you can see your logs at the address: 192.168.1.255.  This is not a /24 network.  I hope that you have your netmask set correctly on your other systems to a /16 network (eg. netmask 255.255.0.0) !

This would cause this type of trouble.  Show output of

ifconfig -a

and check the netmask on your router.  They must be the same on the LAN side.

MrC

---

### Post by BongoBob on 2007-03-07
Ok, ifconfig -a outputs this

inet addr:192.168.1.102  Bcast:192.168.1.255 Mask: 255.255.255.0

How can I change this?

EDIT: Wait, I sudo nano /etc/network/interfaces and changed the netmask from 255.255.255.0 to 255.255.0.0. Is this correct?

---

### Post by Mr. C. on 2007-03-07
Well, there's your problem.  You have two different networks.

Network Settings, select your Wired connection, change its properties.  Change the subnet mask to 255.255.0.0.  Gateway address should be the IP of your router.

Be sure ALL your clients on your LAN have the same subnet mask!

MrC

---

### Post by scxtt on 2007-03-07
for what it's worth, i have a linksys router w/ a 192.168.1.1 IP and my "ifconfig" shows:
```
[font=courier]eth0      Link encap:Ethernet  HWaddr 00:13:D4:CB:7E:54
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fecb:7e54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:206225698 (196.6 MiB)  TX bytes:20604662 (19.6 MiB)
          Interrupt:10 Base address:0xe400[/font]
```and i've had no issues like this one w/ apache and port forwarding ... i've even forwarded HTTP traffic to port 80 (w/ both linux (apache) and windows (IIS)) plus using a different port (1111) ...

---

### Post by BongoBob on 2007-03-07
Well, I changed the IP addys on all my network computers to static IPs and their subnet mask to 255.255.0.0 with no problems.

Any results?

EDIT: I just noticed on the main page of the router setup page, it says Subnet mask 255.255.255.0, with a dropdown box with many others in it.

---

### Post by scxtt on 2007-03-07
mine is set to 255.255.255.0 ... i wouldn't change it and i'd put those back, our networks are setup similarly and i've not had this problem ...

i'm also able to use the **already defined** "UPnP Forwarding" of HTTP ... which means i can use that setting OR "Port Range Forwarding" ... this *feels* like a firewall issue ... did you check "sudo iptables -L"?

just me tho :)

---

### Post by BongoBob on 2007-03-07
Could it have something to do with WebMin then?

---

### Post by BongoBob on 2007-03-07
Here's my /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1

I just found this however from [this tutorial]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3?")

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

What would my network entry be and what about my broadcast (I assume broadcast is 192.168.1.255, but I don't know about the network one)?

EDIT: I just added these two lines to my /etc/network/interfaces
broadcast 192.168.1.255
network 192.168.1.0

Can anyone see if my webpage is working now?

[http://68.108.182.226:80](http://68.108.182.226:80)

EDIT: I'm going to bed now, but I shall hopefully have a half an hour to spare when I wake up to mess around with it, any and all ideas are welcome.

---

### Post by scxtt on 2007-03-07
my entry looks like:
```
[font=courier]auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1[/font]
```not sure what the "network" entry is for (defining default network?), i don't have one ... but if i had to guess, it'd be set to 192.168.1.0 ...

---

### Post by BongoBob on 2007-03-07
Hmmm. Could you try clicking the link in my previous post to see if it works?

---

### Post by Mr. C. on 2007-03-07
Ok, we're thrashing here; let's avoid the voodoo, and solve this on step at a time.  I'm not sure where we are now with all the changes that have been made.

First, you can chose whatever subnet mask you desire from the private network space (i'm not being precise here, because its too complicated to be accurate in this short space).  They just have to be the same on all systems.

Webmin is a simply candy-coated command lines.  It is not causing a block.

What we don't know is:

a) did you restart the interface when you changed the address: do an ifconfig -a via command line to ensure that it changed.

b) are you seeing any of my connect attempts in your firewall logs. You should see plenty.

c) your router needs a firmware update.  You want version 1.05.00 . It has never been updated, and has at least 1 security flaw.  This also might be causing trouble.  I looked at the release notes quickly; nothing was obvious there.  Here are instructions:
[http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=4030](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=4030)

d) Your router may not be IPv6 compatible; I see nothing in either the datasheet or manual that indicates it is.  You can disable IPv6 in Ubuntu like this:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
I believe it was a bad decision to enable IPv6 in a general release.

Lets go from here.

MrC

---

### Post by Mr. C. on 2007-03-07
The network entry describes your ... guess what ... network!

The network, netmask and broadcast are ALL related.  If you care about the details, see: Week 2 Notes: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php) .

As of this posting, still no go.

MrC

---

### Post by scheuri on 2007-03-07
Okay...

If we try to ping or connect to 68.108.182.226 (which is or was your PUBLIC IP) we try to connect to your router.
Which is fine.

You only need to tell your router where it needs to forward the request to.

So, your public interface on the router (which goes to the internet, literally speaking) and there is no need to change that...
Your internatl interface of your router is for your LAN...and needs to be configured that the (web)server can be connected.
So these two network devices (router and webserver) need to see each other (try to ping).

If that works, it is very likely a problem at the router.

My first thought, when reading the first few posts, was that you actually configured the PORTforwarding (NAT), but forgot to tell the built-in-Firewall of your router to let request to port 80 trough!

My router has two things:
A built in firewall which just blocks everything and need to be told to let in whatever port you need and GUI to configure the portforwarding (80 goes to webserver, 22 to my desktopserver and so on).

If I were you, check if there is a firewall in the router which blocks the request before the portforwarding even gets involved in the whole process...

Good luck
Stefan

---

### Post by BongoBob on 2007-03-07
Well, I disabled IPv6 on the server box, and I upgraded the firmware. But I notced something about the Netmask in my router. Unfortunately, I had to leave for school right as I did. I will post it when I get back, but if I remember correctly, the netmask for my WAN IP was 255.255.252.0, while the netmask for my LAN is 255.255.255.0.

I'll post more in about 6 or 7 hours, once I get home.

---

### Post by Mr. C. on 2007-03-07
Different masks for *different* networks is the norm.  Your ISP has allocated a group of addresses, and requires them to use a particular mask to achieve this.  The mask is only relevant for next hop routing.  It uses the IP combined with netmask i index its routing table.

As I said, it is your choice how you configure your LAN; it is their choice how they configure your broadband. 

scheuri - portforwarding *is* your way of of configuring your firewall.  It opens a hole in the firewall, to allow inbound (or outbound) traffic, and may pass through to a NAT/PAT chain to tranlsate the IP/port combination from external / internal.

MrC

---

