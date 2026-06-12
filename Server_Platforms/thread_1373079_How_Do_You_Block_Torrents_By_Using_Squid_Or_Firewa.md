---
title: "How Do You Block Torrents By Using Squid Or Firewall? Is There A Better Way?"
date: 2010-01-05
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-01-05
Hi, I've been all around the net and can't find a "simple" answer how to block our LAN users from downloading torrents. Is it really that difficult?

Here's our setup:

Internet ---> Router ---> eth0
_____
|eth0|
|eth1|---> Switch ---> Workstations
|____| 
Karmic Koala Server

1. The Server's Configs:

sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
dns-nameservers 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.0.51
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
#gateway
dns-nameservers 192.168.1.254

2. sudo gedit /etc/squid/squid.conf

http_port 3128 transparent
acl goodsites dstdomain .google.com .yahoo.com .cnn.com
http_access allow goodsites

3. sudo gedit /etc/rc.local (to start Firewall rules on bootup)

sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'

sudo iptables --table nat --append POSTROUTING --jump MASQUERADE --source 192.168.0.0/24

sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

4. Server NOT a DHCP Server

5. No other iptables rules are configured, just the above ones.

Before in a 1 NIC setup, I blocked Workstations MAC addresses in the Router + Squid Proxy Server (Not Transparent), it worked, but some Online Java Apps didn't work and users can't send/receive email so I abandoned the method.

Now, I installed transparent Squid Proxy with 2 NIC cards, it works, but workstations can still download torrents! I know Squid doesn't block ports, right? So the answer must lie in Iptables Firewall? I basically use Squid just to deny access to Facebook, Friendster, or other "unproductive sites".

> Can you pls. help me how to block torrent downloading by using a Firewall? Or is there another "simple" way? Am I on the right path?

PS I've heard that it's better just to allow regular ports (80, 22, 465, etc...) then block all the rest, this way, you can prevent unnecessary ports. Is this the answer, so how do I do it? Thanks.

PPS I'm not an Iptables/Firewall expert so can you pls. explain it a bit more detailed if that's the case.

PPPS I'm also aware of just telling our users NOT to download torrents, but I just want to prohibit it entirely.

PPPPS I know I will be the most "uncool" employee in our office.

Thanks for reading.

---

### Post by BkkBonanza on 2010-01-05
There is no simple sure fire way to do this. I've heard that some ISPs spend a lot on fancy routers that can filter packets dependent on content but even that isn't foolproof because most torrent clients support encryption to prevent packet snooping.

Torrents can be run on any port. Peer-to-peer traffic can be between any ports. Even if you only leave open only certain known ports competent users can find ways around this. 

You can take some steps to mitigate the effects though. You can setup limits on open connections, which torrents tend to use voraciously. You could also set quotas on transfer so that people cannot use more than you set (suitable for normal work usage). You could probably set up some logging to track people who have high use and/or large numbers of open connections. 100+ connections open to high port numbers is somewhat telling. Most other apps will only have a few connections open at once.

Some routers have QoS functions built in that allow you to prioritize traffic based on source/destination ports. That's no guarantee but it can help stop it from affecting more important traffic.

---

### Post by AlexanderDGreat on 2010-01-06
@BkkBonaza thanks for replying.

> You can setup limits on open connections, which torrents tend to use voraciously. You could also set quotas on transfer so that people cannot use more than you set (suitable for normal work usage). You could probably set up some logging to track people who have high use and/or large numbers of open connections. 100+ connections open to high port numbers is somewhat telling.

So can you point me to the right direction how to achieve these? Thanks for the help.

Are there any other suggestions? :)

---

### Post by Vegan on 2010-01-06
Good luck trying to block torrents. By design they are made to evade being blocked. Most protocols are using strong encryption, making it impossible for an ISP who is snooping to see what is in the packet.

In Canada P2P is legal thanks to a friendly Judge who gave it back after taxing cds, dvds etc heavily. So its legal for to share iTunes, not that I do that, but its legal.

I have over 1000 CDs so what do I care.

So here is the deal, want to block anything, someone will find a way around it.

---

### Post by BkkBonanza on 2010-01-06
I would start with checking what functions your router has. If that isn't useful then 
you can use iptables to manually set up connection limits. You would have to make sure it integrates with whatever you already have in place.

The relevant module is "connlimit" and it prevents more than some number being open under given circumstances. So you would want to configure a limit on outgoing connections in the "high port" range for any given source ip address. I don't have a specific command for this as I haven't had to solve the problem. 

My initial googling turned up this as a starting point, (for use on a gateway/firewall doing forwarding using 192.168.1.34 as an example IP),

iptables -A FORWARD -p tcp &#8211;&#8211;syn -s 192.168.1.34 &#8211;&#8211;dport ! 80 -m connlimit &#8211;&#8211;connlimit-above 5 -j DROP

You may want to change this as follows,

- you would need to use a script to add rules for each src ip address 
- instead of --dport !80 you may want a different range
- you may want to allow more than 5 concurrent connections
- you may want to log as well as drop the packets so you can see who is repeatedly hitting limits

Another google turned up some info on the quotas module, so you may add something to above like,

iptables -A FORWARD -p tcp -s 192.168.1.34 &#8211;&#8211;dport ! 80 -m quota &#8211;&#8211;quota 1024000 -j ACCEPT
iptables -A FORWARD -p tcp -s 192.168.1.34 &#8211;&#8211;dport ! 80 -j DROP

This will allow about 1MB through under these conditions but after that limit will drop the packets.

Edit: Also found info on iplimit module - better for your use as it tracks the src ip automatically. Similar to above but no need for src ip,

iptables -A FORWARD -p tcp &#8211;&#8211;syn &#8211;&#8211;dport ! 80 -m iplimit &#8211;&#8211;iplimit-above 5 -j DROP


Here is a rather old page with this last info and other useful info,

[http://linuxgazette.net/108/odonovan.html](http://linuxgazette.net/108/odonovan.html)

Hope this all helps.

---

### Post by hardev on 2010-01-06
Blocking certain traffic (Torrent - in this case) on the Router is your best bet. If this a home network, I would suggest picking up a Linksys WRT54GL and flash it w/ DD-WRT. DD-WRT does a good job blocking P2P traffic.

---

### Post by HermanAB on 2010-01-06
Hmm, bandwidth limiting using Squid and bucket filters is one way to control things.  Hopefully most of your users are not computer savvy.  If however you have 500 computer scientists or engineers on staff, then about the only thing can do is keep the staff internet connection separated from the mail server using VLANs or such.

---

### Post by AlexanderDGreat on 2010-01-06
@vegan - > So here is the deal, want to block anything, someone will find a way around it.

Well, our users aren't that tech-savvy "yet" I guess so no harm in trying.

**@BkkBonaza - Appreciate all those search for me mate. You're a kind fellow, God bless you. I will put those things in action.**

@hardev - > I would suggest picking up a Linksys WRT54GL and flash it w/ DD-WRT. DD-WRT does a good job blocking P2P traffic.

Thanks for your help, although if I can do it first by software, I'll try it, if not, I'll try to use that Linksys hardware. Yes we're only SOHO.

@HermanAB - > Hmm, bandwidth limiting using Squid and bucket filters is one way to control things. can you show me how to do this?

Thank you vegan, BkkBonaza, hardev, HermanAB for the answers!

---

### Post by Thirtysixway on 2010-01-06
I would suggest taking a look at something like OpenDNS.com  Perhaps there's a way to integrate the services with your current setup, but you can pick and choose which content types to block including things like malware, adware, adult content, p2p traffic, and phishing.  I use it on my network to block adware/phishing and it's wonderful.

[http://www.opendns.com](http://www.opendns.com)

---

### Post by AlexanderDGreat on 2010-01-06
@Thirtysixway - Hi, thanks for the idea.

> I would suggest taking a look at something like OpenDNS.com Perhaps there's a way to integrate the services with your current setup, but you can pick and choose which content types to block including things like malware, adware, adult content, p2p traffic, and phishing. I use it on my network to block adware/phishing and it's wonderful.

Can Google DNS also do this 8.8.8.8 or 8.8.4.4? Is OpenDNS free? I'm a little out of cash right now, Christmas season just passed.

---

### Post by BkkBonanza on 2010-01-06
Google doesn't have filtering on their DNS... yet.

Besides this will just help prevent people getting to sites to locate torrents. It can't possibly have any effect on torrent traffic because torrent clients don't use DNS for finding other peers. 

Once your people see that the torrent site is blocked all they have to do is write down or remember the IP address and type it in manually to get there, or better still add it to their hosts file. No DNS, but can still get the site fine.

---

### Post by Vegan on 2010-01-06
Its impossible, P2P programs can simply change ports. Block them all is the same as snipping the internet cable.

---

### Post by vhinz on 2010-01-07
I'm not really sure if this will help you out.  If you are willing to try [Untangle]("http://www.untangle.com") out then it will greatly  help you out...but for better results, use it with OpenDNS.  The one you should look at for the Untangle module/feature is the Protocol Control.  Of course, you are also free to use their other modules (esp. the free ones).

I was pretty sure that there was a package for Ubuntu when I first heard of Untangle.  [The reason behind is they have discontinued the idea]("http://forums.untangle.com/installation/9271-announcement-untangle-ubuntu-discontinued.html").  

Both have free versions which will be sufficient in warding off what you do not want.

I am using this settings and is quite successful.

---

### Post by AlexanderDGreat on 2010-01-08
Hi BkkBonaza - can you help me?

> sudo iptables -A FORWARD -p tcp --syn -s 192.168.1.52 --dport ! 80 -m connlimit --connlimit-above 5 -j DROP

Produced this error: 

$ Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).

The commands regarding IP Limit and Quota have the same error. Tried removing the ! and the command executed, but the torrents were still successful.

> I'm not really sure if this will help you out. If you are willing to try Untangle out then it will greatly help you out...but for better results, use it with OpenDNS. 

@vhinz - I've tried Untangle before but I have to use a Virtualbox and it keeps hanging in the bootup screen, maybe because my computer doesn't have enough memory and VBox can't detect my VT-technology so only using 1 core!

Intel CD2 e7400
2gb ram

---

### Post by AlexanderDGreat on 2010-01-08
> I would suggest taking a look at something like **OpenDNS.com** Perhaps there's a way to integrate the services with your current setup, but you can pick and choose which content types to block including things like malware, adware, adult content, p2p traffic, and phishing. I use it on my network to block adware/phishing and it's wonderful.

I guess I will try **OpenDNS.**

Ooops... I forgot,

> Besides this will just help prevent people getting to sites to locate torrents. It can't possibly have any effect on torrent traffic because torrent clients don't use DNS for finding other peers.

I already blocked torrent sites with Squid.

---

### Post by BkkBonanza on 2010-01-08
> **AlexanderDGreat said:**
> 
$ Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).

The commands regarding IP Limit and Quota have the same error. Tried removing the ! and the command executed, but the torrents were still successful.

This message appears to be saying that, 

--dport !80

is incorrect syntax and that you should use,

! --dport 80

I just found this sample rule and haven't tried it. I'll give it a try shortly and see if I can help out with getting it right.

Note this should set a connection limit for any non-http (80) port but if you don't have the negation then it would only limit port 80, and hence not be effective at all. After inserting the rule you would want to test it by using "netstat -nt" to see what connections are open. And watch how it behaves as torrents are started. It won't "kill" torrents but it should limit what they can do with so few connections.

I think iplimit is the better way to go for a gateway or firewall as you don't need to set a specific IP.

EDIT: iplimit doesn't appear to be available for the Ubuntu kernel. At least the module isn't present in /lib/xtables/

---

### Post by BkkBonanza on 2010-01-08
I've done a series of tests here. connlimit is available and loads up but doesn't appear to work. At least not how I'm trying it. The docs do say it can be used for limiting server connections from clients so I don't know if reading between the lines here means that it won't work on any chain other than INPUT. I was trying to limit connections outgoing because I have Deluge running some torrents to test. There is very, very little docs on connlimit around the web that I could find so it's just a bit mysterious. 

I think there is a way to make this work but it doesn't appear to be very easy.

I also came across a module called ipp2p which was made to target p2p traffic. However, it doesn't appear to be available in Ubuntu and it seems like to use that it would require lots of work.

The "! --dport 80" syntax does work. I tried it with DROP target and it cut all traffic for torrents (but generally useless because it cuts all non port 80 traffic, not just torrents).

---

### Post by ndefontenay on 2010-01-08
But why would you do such a horrible thing anyway :shock:

---

### Post by vhinz on 2010-01-08
> **ndefontenay said:**
> But why would you do such a horrible thing anyway :shock:

Block torrents?  As simple as managing network bandwidth.  simultaneous downloads especially large files (mostly movies) from torrents can bring network to its knees.

---

### Post by vhinz on 2010-01-08
> **AlexanderDGreat said:**
> 

@vhinz - I've tried Untangle before but I have to use a Virtualbox and it keeps hanging in the bootup screen, maybe because my computer doesn't have enough memory and VBox can't detect my VT-technology so only using 1 core!

Intel CD2 e7400
2gb ram

[Untangle Deployment Options]("http://www.untangle.com/Deployment-Options") - Though as previously communicated, they've stopped the support Ubuntu/Debian.

[Virtual Appliance Installation using VMWare]("http://wiki.untangle.com/index.php/Untangle_Virtual_Appliance_on_VMware")

---

### Post by bodhi.zazen on 2010-01-12
Blocking torrents is not easy as basically the torrent clients are designed to evade such attempts on your part.

You have been given some good advice in your thread, I would point you at this thread.

[http://serverfault.com/questions/27088/using-linux-iptables-how-to-block-torrents-or-any-p2p-protocols](http://serverfault.com/questions/27088/using-linux-iptables-how-to-block-torrents-or-any-p2p-protocols)

I believe the best solution is to use a proxy server for web access, ie something like squid.

So, if you are on a low budget, configure a hardware firewall (which is nothing but an inexpensive box with two network cards) and install a firewall specific distro + squid.

You would then configure the firewall to allow as much internal traffic as you wish, but restrict outbound traffic to http and https (ports 80 and 443) which would be proxied by squid.

Yes it can still be abused.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

[http://www.linuxjunkies.org/html/Bandwidth-Limiting-HOWTO.html](http://www.linuxjunkies.org/html/Bandwidth-Limiting-HOWTO.html)

---

### Post by Fatjoint on 2010-01-12
> **vhinz said:**
> Block torrents?  As simple as managing network bandwidth.  simultaneous downloads especially large files (mostly movies) from torrents can bring network to its knees.



Not if you install 10 MBit switches on the client side ;)

Your core switches should always be a step above your client switches to prevent any single client from "bringing the network to its knees".

---

### Post by iponeverything on 2010-01-12
I have used connection limits to slow torrents to a crawl..

I had transparent bridge and the version of brctl control that it had on the box allowed for setting connection limits, both global and individual.  I had a global limit of 100 per internal IP address, and this managed to throttle torrents quite effectively. (I don't think anyone was able to pull over 30k / second)

[http://www.bandwidtharbitrator.com/modules.php?name=News&file=article&sid=4](http://www.bandwidtharbitrator.com/modules.php?name=News&file=article&sid=4)

BTW -- The neteq is a linux based transparent bridge device and it does an excellent job of providing very fine grained control over your network traffic.

---

### Post by AlexanderDGreat on 2010-07-12
@iponeverything:

[http://www.bandwidtharbitrator.com/modules.php?name=News&file=article&sid=4](http://www.bandwidtharbitrator.com/modules.php?name=News&file=article&sid=4)

Your link above doesn't work.

---

### Post by AlexanderDGreat on 2010-09-19
Please take a look at my POST #10 here at: [http://ubuntuforums.org/showthread.php?t=1576228]("http://ubuntuforums.org/showthread.php?t=1576228")

I can't block torrents but I can hamper their speeds.

It's the simplest way I know! Thanks UbuntuForums and all the good and patient people who helped me out. :)

---

### Post by Vegan on 2010-09-19
Those 2 DNS servers are public and anyone can use them.

I have them in my other DNS list in BIND9, along with a lot of other around the planet.

---

### Post by shafi on 2011-10-08
> **AlexanderDGreat said:**
> Please take a look at my POST #10 here at: [http://ubuntuforums.org/showthread.php?t=1576228]("http://ubuntuforums.org/showthread.php?t=1576228")

I can't block torrents but I can hamper their speeds.

It's the simplest way I know! Thanks UbuntuForums and all the good and patient people who helped me out. :)

As bittorrents are very complex and they are using various ports. Thus the best way to block them out is to install squid on your server and only allow the http, https and IMAP ports and deny all other ports using the "http_access deny all".
Now the torrents should not be able to function more.

---

### Post by SeijiSensei on 2011-10-08
I know this post is old, but I thought I'd pass along a different solution.

Most torrent traffic occurs on so-called "high" ports, ones numbered from 1024-65535.  Ports below this can only be opened by software running (at least initially) with root permissions like SMTP (port 25) and HTTP servers (80).  Ordinary users can run software like torrent clients that listen on the high ports.

At one site I consult to, we've simply blocked all traffic originating on a client computers' high ports from connecting to any remote's high ports like this:

```

iptables -A FORWARD -p tcp -s 10.10.0.0/16 --sport 1024:65535 -d ! 10.10.0.0/16 --dport 1024:65535 -j REJECT
iptables -A FORWARD -p udp -s 10.10.0.0/16 --sport 1024:65535 -d ! 10.10.0.0/16 --dport 1024:65535 -j REJECT

```

These allow machines within our network (10.10.0.0/16) to carry out high-port communication with each other, but forbids them from connecting to high ports on remotes.

These rules will block most torrent traffic and other bandwidth gobblers like streaming radio and gaming.  They may also block some legitimate traffic as well.  We log all packets that match this rule (by adding two identical rules above these with "-j LOG" instead of "-j REJECT") just in case.  Usually the IT department will hear complaints if a legitimate service (like, e.g. GoToMyPC) is blocked.

---

### Post by adtf01 on 2011-11-09
> **SeijiSensei said:**
> I know this post is old, but I thought I'd pass along a different solution.
 
Most torrent traffic occurs on so-called "high" ports, ones numbered from 1024-65535. Ports below this can only be opened by software running (at least initially) with root permissions like SMTP (port 25) and HTTP servers (80). Ordinary users can run software like torrent clients that listen on the high ports.
 
At one site I consult to, we've simply blocked all traffic originating on a client computers' high ports from connecting to any remote's high ports like this:
 
```

iptables -A FORWARD -p tcp -s 10.10.0.0/16 --sport 1024:65535 -d ! 10.10.0.0/16 --dport 1024:65535 -j REJECT
iptables -A FORWARD -p udp -s 10.10.0.0/16 --sport 1024:65535 -d ! 10.10.0.0/16 --dport 1024:65535 -j REJECT

```
 
These allow machines within our network (10.10.0.0/16) to carry out high-port communication with each other, but forbids them from connecting to high ports on remotes.
 
These rules will block most torrent traffic and other bandwidth gobblers like streaming radio and gaming. They may also block some legitimate traffic as well. We log all packets that match this rule (by adding two identical rules above these with "-j LOG" instead of "-j REJECT") just in case. Usually the IT department will hear complaints if a legitimate service (like, e.g. GoToMyPC) is blocked.
 
Hi SeijiSensei
 
I am have a similar problem but am new to linux.  Where would I put the code you recomend?

---

### Post by bodhi.zazen on 2011-11-10
> **adtf01 said:**
> Hi SeijiSensei
 
I am have a similar problem but am new to linux.  Where would I put the code you recomend?

You will have to learn iptables for those commands to work.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

