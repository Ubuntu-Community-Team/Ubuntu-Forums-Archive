---
title: "Internet OK but Ping does not work (VMWARE)"
date: 2009-02-10
forum: Virtualisation
---

### Post by ppatrick on 2009-02-10
VMWARE

Host: MS Vista
Guest: Ubuntu 8.10 Jeos
Networking : NAT, (I have to use NAT).

The Host has full Internet access
The Guest has Internet access but ping fails in a weird way.
$ping [www.google.com](www.google.com)
returns the first line displaying the IP address of [www.google.com](www.google.com)
but there are not returned ping packets; lost 100%

No 3rd party firewalls on my host...
host antivirus ESET Nod32 Business Ed
from the host I can establish ssh sessions against the Ubuntu
w/o problem....

I've found on the net people with exactly the same problem
[http://jars.de/linux/ubuntu-710-vmware-image-download-english#comment-1390](http://jars.de/linux/ubuntu-710-vmware-image-download-english#comment-1390)


how can I solve this?

---

### Post by dmizer on 2009-02-10
What vmware product are you using, and how did you install it?

Edit:
Moved to virtualization.

---

### Post by JK3mp on 2009-02-10
Hmmm...odd problem..usually i encounter people who have opposite..ping but no internet..sorry no that doesn't help..but heres an article i googled up of a similiar problem solved.

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/23296](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/23296)

---

### Post by ppatrick on 2009-02-10
Sorry I might've sent my post to the wrong forum, it's my first time here.

dmizer
I've made my VM using WMware workstation 6 / 6.5 , I've installed Ubuntu 8.10 Jeos (Server option JEOS) and works perfect... everything but the ping command from the guest to the outside world... 

JK3mp
exactly the very same problem but not solution was posted there.....

---

### Post by dmizer on 2009-02-10
No worries about posting in the wrong place. You're just more likely to get help if you do post in the right place.

On the Ubuntu VM, try disabling IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by ppatrick on 2009-02-10
I just checked it out, but no luck.
The DNS resolution part of the Ping command is done perfectly...

~$ ping www.google.com                                       
PING www.l.google.com (**216.239.59.104**) 56(84) bytes of data.
^C
--- www.l.google.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4018ms

~$


but there are no ICMP packets going out and/or coming back....

---

### Post by dmizer on 2009-02-10
Sounds to me like something in Vista is blocking access then. Firewall perhaps?

---

### Post by dmizer on 2009-02-10
Also note, that not all versions of Vista are capable of running vmware. Is your Vista version listed here? [http://pubs.vmware.com/ws65_ace25/ws_user/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ws_user&file=intro_sysreqs_ws.html](http://pubs.vmware.com/ws65_ace25/ws_user/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ws_user&file=intro_sysreqs_ws.html)

Click: Host System Requirements > Host Operating System

---

### Post by ppatrick on 2009-02-10
Host OS is the VMware supported Windows Vista 32 Business Edition.

Firewall in host is Vista default, but for testing I've removed the VMware interfaces from the Firewall watch without any change on the problem.

The funny thing is that from the guest I have internet access, I'm checking out repositories, I'm able to install Ubuntu packages, I'm able to stablish SSH sesions from the host to the Guest w/o problem etc etc

that's why I think is not just a firewall thing....

---

### Post by dmizer on 2009-02-10
From the guest, what is the output of:
```
sudo ifconfig
```

---

### Post by ppatrick on 2009-02-10
```
~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0c:29:c2:21:dd
          inet addr:192.168.232.128  Bcast:192.168.232.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11332 (11.3 KB)  TX bytes:11625 (11.6 KB)
          Interrupt:18 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


I think I haven't said it, from the Host I'm able to ping the Guest, but from the guest I cannot ping the Host....

---

### Post by dmizer on 2009-02-10
Can you ping anything by IP address rather than url?

Edit:
Found you -> [http://communities.vmware.com/thread/191654?tstart=0](http://communities.vmware.com/thread/191654?tstart=0) ;)

This is a Vista problem. From what I've found, the Vista firewall blocks ICMP. Apparently even though you say you have it disabled, Vista is still blocking ICMP. Found this: [http://www.howtogeek.com/howto/windows-vista/allow-pings-icmp-echo-request-through-your-windows-vista-firewall/](http://www.howtogeek.com/howto/windows-vista/allow-pings-icmp-echo-request-through-your-windows-vista-firewall/) posted here: [http://www.certforums.co.uk/forums/showthread.php?t=27718](http://www.certforums.co.uk/forums/showthread.php?t=27718)

Take a look and see if either of those help you.

---

### Post by mpsii on 2009-02-10
I have found that if I have a VMWare guest that does not have a bridged network connection (connects directly to the same network with the host), but has a NAT connection (shares the connection, but uses a different IP/subnet address), that the guest cannot ping due to the NAT interface.

For example:

Bridged (able to ping):
Host = 10.0.1.199
Guest = 10.0.1.200

NAT (unable to ping):
Host = 10.0.1.199
Guest = 192.168.1.2

---

### Post by ppatrick on 2009-02-11
> **dmizer said:**
> Can you ping anything by IP address rather than url?
The DNS service works perfectly, pinging by IP or URL gives exactly the same problem...

> **dmizer said:**
> 
Edit:
Found you -> [http://communities.vmware.com/thread/191654?tstart=0](http://communities.vmware.com/thread/191654?tstart=0) ;)
Yes I've been there too, fortunately I've got more interest on this issue here than there... 
> **dmizer said:**
> 
This is a Vista problem. From what I've found, the Vista firewall blocks ICMP. Apparently even though you say you have it disabled, Vista is still blocking ICMP. Found this: [http://www.howtogeek.com/howto/windows-vista/allow-pings-icmp-echo-request-through-your-windows-vista-firewall/](http://www.howtogeek.com/howto/windows-vista/allow-pings-icmp-echo-request-through-your-windows-vista-firewall/) posted here: [http://www.certforums.co.uk/forums/showthread.php?t=27718](http://www.certforums.co.uk/forums/showthread.php?t=27718) 

I've followed the instructions, the **File and Printer Sharing (Echo Request - ICMPv4-In)** & **File and Printer Sharing (Echo Request - ICMPv4-out)**where open...
the problem stills the same...

I can't believe it...

---

### Post by ppatrick on 2009-02-11
> **mpsii said:**
> I have found that if I have a VMWare guest that does not have a bridged network connection (connects directly to the same network with the host), but has a NAT connection (shares the connection, but uses a different IP/subnet address), that the guest cannot ping due to the NAT interface.

For example:

Bridged (able to ping):
Host = 10.0.1.199
Guest = 10.0.1.200

NAT (unable to ping):
Host = 10.0.1.199
Guest = 192.168.1.2

I cannot use bridged connections....
why on earth is this happening??

---

### Post by ppatrick on 2009-02-11
more info,
I've loaded the very same VM on Windows Server 2003 as Host instead of Vista;
Ping works....

how can I solve this on Vista?

---

### Post by dmizer on 2009-02-11
Why is it that you need NAT rather than bridged?

I ask because perhaps there is an alternative configuration which will allow you to have a separate subnet for your Ubuntu virtual guest but also allow you to used a bridged connection in Vista.

---

### Post by Dedoimedo on 2009-02-12
Hello,

There should be no problem. I can use ping from within the virtual machines against other subnets and Internet addresses. Both on Windows and Linux hosts.

Sometimes, you will have to enable forwarding on the host and permit icmp in the host firewalls.

What does the guest /etc/resolv.conf say?

Can you ping by IP instead of names? If you can, then you need to fix the above file so that it contains a reachable nameserver.

If you can't, you might have routing problems or firewall problems. Can you surf from within the virtual machine. If you can, this leaves firewall as the culprit.

Dedoimedo

---

### Post by ppatrick on 2009-02-12
> **dmizer said:**
> Why is it that you need NAT rather than bridged?

I ask because perhaps there is an alternative configuration which will allow you to have a separate subnet for your Ubuntu virtual guest but also allow you to used a bridged connection in Vista.
I have to use NAT; I'm developing an appliance that has to get internet connection right out of the box.... with users not trained on configuring network stuff... So far NAT was the best option, no matter where I've tested the VM if the Host has Internet connection my guest gets it w/o touching anything...

> **Dedoimedo said:**
> Hello,

There should be no problem. I can use ping from within the virtual machines against other subnets and Internet addresses. Both on Windows and Linux hosts.

Sometimes, you will have to enable forwarding on the host and permit icmp in the host firewalls.

What does the guest /etc/resolv.conf say?

Can you ping by IP instead of names? If you can, then you need to fix the above file so that it contains a reachable nameserver.

If you can't, you might have routing problems or firewall problems. Can you surf from within the virtual machine. If you can, this leaves firewall as the culprit.

Dedoimedo
please the DNS is WORKING... my problem is how to configure Vista's Firewall in order to let the ICMP packages going back and forth... it seems nobody really knows how....

---

### Post by dmizer on 2009-02-12
Ping works fine on my NAT connections with an Ubuntu host and Ubuntu guest. I'm using Vmware server though.

I don't think this is an Ubuntu, or Vmware problem at this point, but I don't have a workstation license, so I can't test it from that angle. I'll talk to one of my friends this evening and see if he can do some testing as he does have a license.

---

### Post by dmizer on 2009-02-12
Well, after doing some extensive testing courtesy of my friend, I have to say that this really does look like a problem specific to Vista. All of his NAT guests can ping to the WAN with no problem.

Only difference is that his host is Linux.

---

### Post by ppatrick on 2009-02-12
I agree I'm trying to get my firewall set correctly but everything looks fine... honestly I do not know what else I can do...

---

### Post by Perryg on 2009-02-12
Why don't you try turning off the firewall in Vista and see if that allows you to ping.  I would put my money on the fact that it is not bridged.  I have Vista business as host and Ubuntu as guest and it will not let me ping internal addresses if it is not bridged.

---

### Post by ppatrick on 2009-02-12
I already did, I turned the firewall OFF and the probl;em persists...
OK there's a problem with VISTA-NAT-Firewall but the solution is not using Bridging...
I said it 10 times... I need NAT; It has to work with NAT; It will work with NAT.
thanks

---

### Post by Perryg on 2009-02-12
You can still use NAT!
Bridging just puts you in the ballpark with your host.
I have one dynamic and one static as we speak.
The only problem you have is trying to do this in a virtual enviornment.  As for the I have said 10 times. (I did read all of the posts) It came up several times that Vista was causing the problem.  My suggestion was only to allow you to prove it to yourself and everyone else that Vista was not causing the problem.  Sorry if you mis-understood what I was saying.

---

### Post by ppatrick on 2009-02-12
1)I have only NAT and from a Vista HOST console I can Ping my Ubuntu Guest, I can start PuTTy SSH sessions against the Ubuntu Gest, etc etc... You do not need bridging for that... It is PROVED...

2) do you think that a simultaneous NAT + Bridging makes sense??
I do not want to finish my applaince with NAT, BRIDGING, SWITCHING, and a monk with a candle praying for getting Internet on the first try...ok? this has to be more simple

I've debugged the problem using a sniffer
see my post here
[http://communities.vmware.com/message/1170376#1170376](http://communities.vmware.com/message/1170376#1170376)

---

### Post by Perryg on 2009-02-12
PPatrick,

Let me see if I can make this a little more clear to you.  
If you are like most you have a router of some kind that allows you to get to the internet.  Whether it is a wireless router or other router. If for instance you do not have a router and are just connected via one ethernet cable to a cable modem or what ever, Vista can be configured to work as NAT for you. It is called a shared connection.  We can get to that later if this is the way you need to connect.

I assume Vista gets its address scheme from that point.
So the presence of NAT is already setup for you there as well as DHCP if you want to make it truely automatic to log into the Internet.

Now you also have the virtual software that is running on Vista.
At this point you are dependant on the addressing Scheme that is provided to Vista since the virtual software must use the same NIC to get to the outside world.  From experience I have found that it is much easier to get the virtual software to behave if it is bridged to the Vista host.  This does not mean that you are bridging the guest software.  Ubuntu gives you only a few choices and that is DHCP, Static, or localconf, so I would think you are using DHCP. 

With that said I would consider trying it and see if it works for you.  I seriously doubt that you will get it to work properly without doing so.  This is a work around as everything is when you are using virtual software to emulate a real computer.

Please understand that I as most of the fine folks here are trying to help.  I hope you can understand that not being able to actually touch the machine makes it a lot harder to give you 100% do this because there are a lot of variables that can change the way things happen.

Please let me know how it goes and I will check back later to see how you are doing.

---

### Post by henkhenk_ on 2009-07-16
> **JK3mp said:**
> Hmmm...odd problem..usually i encounter people who have opposite..ping but no internet..sorry no that doesn't help..but heres an article i googled up of a similiar problem solved.
 
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/23296](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/23296)
 
i have a problem u mentioned and I discribed it on the following link:
 
[http://ubuntuforums.org/showthread.php?p=7624608#post7624608](http://ubuntuforums.org/showthread.php?p=7624608#post7624608)
 
henk

---

