---
title: "HOWTO: Setup Ubuntu as a wireless router"
date: 2007-03-04
forum: Server Platforms
---

### Post by pedalwrench on 2007-03-04
[COLOR=Red][B][SIZE=5][SIZE=3]Update: this is _*now*_ working.
     It looks like my issue with bridging was and is a hardware issue.
     The Atheros card will not come on-line after a reboot, but will come up on a hard power cycle. :)

[/SIZE][/SIZE][/B][/COLOR]My first How To, and it is kind of long.

Basically I was sick of my Linksys router being to slow and I decided I wanted some more power.

This took a long time to work through and get running.  Hopefully I got it all.

First off you will need a spare machine, some NICs and a lot of patience.  Also a working knowledge of nano and the console would be nice.

**My Hardware Specs:**
Old Micron Desktop Computer with everything onboard/built in
Celeron 400 MHZ
384mb RAM
40GB HDD
Atheros based cheap wireless NIC from Compusa
2 Realtek 10/100 NICs

I chose the Atheros card because it was laying around in storage gathering dust. I also have a nice 10db antenna that hooks up to it. 

For comments or complaints email me. 
pedalwrench007 at gmail dot com

Here goes and have fun:
[COLOR=Blue][B]
GOAL[/B][/COLOR] 

To have a seamless replacement for my Linksys WRT54G with more wireless range and more control.

**[COLOR=Blue] INITIAL[/COLOR]**

Install the basic Ubuntu Server [NO DNS or LAMP]
Enable the Universe Repo
apt-get update

Since this is a long How to you should just be *root* to config the server.  

type the command:
```
sudo su -
```and enter your password...

**[COLOR=Blue] SETUP THE NETWORK[/COLOR]**
3 interface setup

my eth0 is broken and on-board so I had to add a card [YMMV]
eth1 is the WAN interface (gateway)
eth2 is the LAN interface
ath0 is the wireless card
br0 is the bridged connection of ath0 and eth2

** Setup bridging**
```
apt-get install bridge-utils
```Then edit the network config
```
nano /etc/network/interfaces
``````
 # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#MY BROKEN INTERFACE (3com on-board)
#auto eth0
#iface eth0 inet dhcp
#pre-up iptables-restore < /etc/iptables.conf

# Gateway 
# You **should** set this to DHCP if your cable/DSL ISP provides it.
# the "pre-up" command brings up the iptables "firewall"
# it is just set to static for testing purposes.  see eth0 for DHCP setup.
auto eth1
iface eth1 inet static
address 192.168.1.17
netmask 255.255.255.0
gateway 192.168.1.1
pre-up iptables-restore < /etc/iptables.conf

#Wireless Setup
auto ath0
iface ath0 inet manual
wireless-mode master
# CHANGE ME!!! to your own ESSID
wireless-essid pivotpoint

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth2 ath0
 
```**[COLOR=Blue]WIFI SETUP[/COLOR]**

Atheros card setup for routing
[resource = [https://help.ubuntu.com/community/Router/Madwifi](https://help.ubuntu.com/community/Router/Madwifi)]
You have to install the Source to get the driver into **Master** mode for a WAP

```
wget http://umn.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.2.1.tar.gz 
tar -xvzf madwifi-0.9.2.1.tar.gz
cd madwifi-0.9.2.1
apt-get install build-essential linux-headers-server 
make
make install
```Edit your kernel modules loaded at boot time:

```
 nano /etc/modprobe.d/madwifi
```add this to make sure the wireless card goes into **Master** mode:

```
options ath_pci autocreate=ap 
```**[COLOR=Blue]FIREWALL[/COLOR]**

run these commands:
[resource = [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/firewall-configuration.html ](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/firewall-configuration.html ) ]

[NOTE: ETH1 is the gateway interface. YMMV]

```
iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o eth1 -j MASQUERADE
iptables -A FORWARD -s 10.1.1.0/24 -o eth1 -j ACCEPT
iptables -A FORWARD -d 10.1.1.0/24 -m state --state ESTABLISHED,RELATED -i eth1 -j ACCEPT
```for logging add:

```
iptables -A INPUT -m state --state NEW -p tcp --dport 80 -j LOG --log-prefix "NEW_HTTP_CONN: "
```The above log will also appear in /var/log/messages, /var/log/syslog, and /var/log/kern.log. 

save to /etc/iptables.conf

```
iptables-save > /etc/iptables.conf
```[I]NOTE: This is a basic setup that only routes NAT packets.  Please read up on firewalli
ng to protect your machine.[/I]

**# Enable packet forwarding in the Kernel**

```
nano /etc/sysctl.conf
```# Uncomment the next line to enable packet forwarding for IPv4
```
net.ipv4.conf.forwarding=1
```[I]
NOTE: Ubuntu has this for default:
[COLOR=Red]#net.ipv4.conf.**default**.forwarding=1[/COLOR]

Make sure you remove the word "default." there is no need for it [/I]

[B][COLOR=Blue]DHCP SERVER SETUP

[/COLOR][/B] A basic 10 machine DHCP server.  Nothin' fancy

Install DHCP server:
```
apt-get install dhcpd
```Config the server:
```
 nano /etc/dhcpd.conf
``````
 # MY BASIC CONFIG /etc/dhcpd.conf

default-lease-time 600;
max-lease-time 7200;

#CHANGE THIS TO YOUR DNS SERVERS
option domain-name-servers 68.87.69.146, 67.87.85.98;
option domain-name "youdomainnamehere.com";

#Subnet for DHCP Clients
subnet 10.1.1.0 netmask 255.255.255.0 {
# range of 10 machines
range 10.1.1.50 10.1.1.60;
option subnet-mask 255.255.255.0;
option broadcast-address 10.1.1.255;
option routers 10.1.1.1;
} 


```You also need to edit /etc/default/dhcp file to specify the interfaces dhcpd
should listen to. By default it listens to eth0.  We need to only have it listen to our local NIC {br0}

```
nano /etc/default/dhcp
```Then add br0 like so:

```
 INTERFACES="br0"
```

**[COLOR=Blue]INSTALL MONITORING[/COLOR]**

**Darkstat**

Stats with a http server

```
apt-get install darkstat
```edit the config

```
nano /etc/darkstat/init.cfg
``````
 # Turn this to yes when you have configured the options below.
START_DARKSTAT=yes

# Don't forget to read the man page.

# You must set this option, else darkstat may not listen to
# the interface you want
INTERFACE="-i eth1"

PORT="-p 8888"
#BINDIP="-b 127.0.0.1"
#LOCAL="-l 10.1.1.0/24"
#FIP="-f 127.0.0.1"
#DNS="-n"
#SPY="--spy eth1"
```

To see this point a browser to [http://10.1.1.1:8888](http://10.1.1.1:8888)

**Saidar**

a neat little ap that shows server usage

```
apt-get install saidar
```then

```
saidar
```**[COLOR=Blue]OTHER OPTIONAL[/COLOR]**

*Disabling IPv6 for some speed improvments*


```
nano /etc/modprobe.d/aliases
```Comment out this line:  
```
alias net-pf-10 ipv6
```Save the file then

```
nano /etc/modprobe.d/blacklist
```Add this line:  
```
blacklist ipv6
```Save the file 

**[COLOR=Blue]FINISH[/COLOR]**

restart your computer. Hopefully everything worked.  If so, back it up!

**[COLOR=Blue]BACKUP[/COLOR]**

[Reference = [http://doc.gwos.org/index.php/Backup_restore_system](http://doc.gwos.org/index.php/Backup_restore_system) ]
```
sudo su -
cd /
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/media --exclude=/mnt --exclude=/dev --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/tmp --exclude=/sys /
```You will then have a tar ball that is your server all wrapped up in a bundle.
Store in a cool dry place.

[COLOR=Blue]**FUTURE GOALS**[/COLOR]

Add Squid, and DNS-Masq.
Add Port Forwarding

 
**[COLOR=Blue]References:[/COLOR]**
[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces) [https://help.ubuntu.com/community/UbuntuWirelessRouter/New](https://help.ubuntu.com/community/UbuntuWirelessRouter/New)
[http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html](http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html) [http://www.debianadmin.com/monitor-your-debianubuntu-system-with-saidar.html](http://www.debianadmin.com/monitor-your-debianubuntu-system-with-saidar.html)  [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html) [http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html](http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html)

VERSION:
0.1 3-11-2007 - Re-Write.  Setup is a little different.  Changed firewall config, deleted squid, and dns-masq.
0.0 3-4-2007 - Initial write-up

---

### Post by esaym on 2007-03-05
Good work!  Looks promising!

---

### Post by BeachBum on 2007-03-05
Cool!  I just reinstalled Edgy (reverted back to i386) and need to provide some type of network access, much like you describe here.  I wanted to know why you chose bridging, instead of routing?  Besides the actual data "routing", are there any key differences between bridging and routing?  

Thanks for any thoughts!

---

### Post by pedalwrench on 2007-03-05
> **BeachBum said:**
> Cool!  I just reinstalled Edgy (reverted back to i386) and need to provide some type of network access, much like you describe here.  I wanted to know why you chose bridging, instead of routing?  Besides the actual data "routing", are there any key differences between bridging and routing?  

Thanks for any thoughts!


Well, I just thought that would be the best way to make it look seamless, like a linksys or d-link router.

That is a great idea though.  I may drop the bridging and go that route.  The madwifi driver and wireless-tools doesn't seem to work well together with bridge-utils.  Unless I am missing something.

For routing with out the bridge it should be pretty simple.  just set the network up with separate interfaces, point dhcp and dns-masq to those interfaces, and then reconfig the firewall accordingly.  It actually works that way.

---

### Post by genesis[OFT] on 2007-03-06
You probably should also note that it is of CRITICAL importance that you have a Wireless NIC that supports MASTER MODE.

---

### Post by pedalwrench on 2007-03-11
> **'genesis[OFT] said:**
> You probably should also note that it is of CRITICAL importance that you have a Wireless NIC that supports MASTER MODE.

so true, do you know of a list of approved wireless NICs/Drivers that support it. I will add it to the resource area.

I have to build the Madwifi driver from source to get it going.

---

### Post by pentium4borg on 2007-03-12
Isn't it better to sudo -s instead of sudo su - ?

---

### Post by luca.b on 2007-03-12
Some suggestions:

Instead of manipulating iptables directly, consider using shorewall ([http://shorewall.net](http://shorewall.net)) it makes configuring iptables much easier and also enables creating "trusted" and "untrusted" zones pretty easily. Also doing NAT/masquerade and port forwarding is also easy.

Second, instead of installing a dhcp server, consider using the dnsmasq package. It's both a DHCP server and a DNS cache and works rather nicely on my Ubuntu software router (I notice you put it in the future plans, though).

For easy web administration, I use webmin ([http://webmin.com](http://webmin.com)). It's not in the Ubuntu repository but you can find a binary package on their web page. You can configure a lot of settings like that, including shorewall.

---

### Post by Tichondrius on 2007-03-12
To become root you only need to type "sudo -s"

And running a PC 24/7 will cost you 10 times as much as a wireless router, as far as the electricity bill.

---

### Post by flashingcurser on 2007-03-12
Very nice work!

I see you are thinking about some future additions to this article. A couple that I would like to suggest are:

Squid/dansguardian- So that if it was an open network no one could use it for illegal porn.

bandwidth control, total and for each individual connection- So no one could saturate your bandwidth with bittorent

homepage redirect- So people could see my shiny new site first. I think this could be done with squid.

I know that "Open wireless network" is a much maligned term. If secured properly, their usefulness is too good to be ignored.


Thank you

---

### Post by luca.b on 2007-03-14
> **Tichondrius said:**
> To become root you only need to type "sudo -s"

And running a PC 24/7 will cost you 10 times as much as a wireless router, as far as the electricity bill.

Depends which PC. I have a PC that runs as my router. It has a mini-ITX board with a VIA C3 and a converter to use a fanless 12V power supply. Mass storage is a 100 Gb 2.5" HD. All contained in a small plastic case my brother made.
It doesn't suck up much power.

---

### Post by pedalwrench on 2007-03-18
Good to see people taking this and moving forward.  This is just a how to get it going.  Hopefully people are able to connect the dots and build onto it.  like the previous post, it is possible to make this out of energy efficient components, but it is up to you to do it.

Here are some of the reasons I did it:

1. To learn something new
2. To re-use old outdated hardware
3. To teach others the skills I have learned
4.  As a Do-It-Yourself (DIY) type guy, I like disecting things and getting them to work on my own.

There are multiple ways to do everything, I found that this is the best method for me.  Your mileage may very on everything but have fun doing it.

---

### Post by zophiel on 2007-03-25
Hey Thanks for the awesome guide, I just got my home network setup in a few minutes!

(starts diddling with making a DNS server and WPA security)

if anyone is still looking to this guide, people should note that Madwifi-9.3.0 doesn't play very well!

---

### Post by encompass on 2007-03-29
Can I keep my current configuration of a server... but give it the power to let others connect to my wireless adapter.  It is a situation like this....
(created in dia...)

---

### Post by pedalwrench on 2007-04-12
> **encompass said:**
> Can I keep my current configuration of a server... but give it the power to let others connect to my wireless adapter.  It is a situation like this....
(created in dia...)

I don't see an issue with it.  

Looks like you will have 2 different networks with that setup, and using this as a server.  your wife's computer will be isolated.  

sorry for the late reply I was on vacation.

---

### Post by hazza96 on 2007-05-14
What about encryption?

I don't want the next door neighboor piggy backing on my ADSL connection or snooping what I am sending back and forth between my laptop and server.

Also, does anyone have a list of cards that can be set to MASTER?

---

### Post by pedalwrench on 2007-05-15
> **hazza96 said:**
> What about encryption?

I don't want the next door neighboor piggy backing on my ADSL connection or snooping what I am sending back and forth between my laptop and server.

Also, does anyone have a list of cards that can be set to MASTER?

Not really sure about that, use the wiki and search for wep or wpa.  

Check out the following:

WPA
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)
[http://hostap.epitest.fi/](http://hostap.epitest.fi/)

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29#head-865d0d28eb6aad9e2faa5e869766fceecc12456d](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29#head-865d0d28eb6aad9e2faa5e869766fceecc12456d)

good luck

---

### Post by phin on 2007-06-07
ok, i have this working, but i cannot seem to get outside of my internal network and ping outside.

the main dif, is i couldnt get my card into master mode, so i set it to ad-hoc

---

### Post by amlucent23 on 2007-06-08
this guide would work just as well if you removed the wireless aspect of it and continued to let your linksys handle wireless clients right. I mean turn it off Gateway mode and turn on AP mode and just forward dns/dhcp to the ubuntu box? (that way I don't have to worry about Master mode drivers or even having a pci wifi card) NOTE: I'm not sure the stock linksys firmware will allow this but I'm using DD-WRT firmware and it most defiantly will.

---

### Post by pedalwrench on 2007-06-09
> **phin said:**
> ok, i have this working, but i cannot seem to get outside of my internal network and ping outside.

the main dif, is i couldnt get my card into master mode, so i set it to ad-hoc

I am pretty sure you need master mode in order to share the connection

---

### Post by pedalwrench on 2007-06-09
> **amlucent23 said:**
> this guide would work just as well if you removed the wireless aspect of it and continued to let your linksys handle wireless clients right. I mean turn it off Gateway mode and turn on AP mode and just forward dns/dhcp to the ubuntu box? (that way I don't have to worry about Master mode drivers or even having a pci wifi card) NOTE: I'm not sure the stock linksys firmware will allow this but I'm using DD-WRT firmware and it most defiantly will.

You are correct

---

### Post by tuprox on 2007-08-01
I am having trouble after I change my /etc/network/interfaces file.  This is what it looks like before I make any of your changes.  Also note that I am running 2 NIC's and no wireless so what should I do dor the other NIC?

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Malh on 2007-08-01
sweet thanks, this will prove useful

---

### Post by gigahz on 2007-08-09
> **pedalwrench said:**
> 
     The Atheros card will not come on-line after a reboot, but will come up on a hard power cycle. :)

Hi just dropping a line to say I had a similar problem with a Xircom PCMCIA ethernet card. It would not work after removing the cable and replugging it (say, changing to another switch port).

I had to do 
```
cardctl eject 0
cardctl insert 0
```

to manually power cycle the card. I eventually put the respective lines into eth0-ifdown and eth0-ifup, to automate it.

Obviously, this is a lot quicker than rebooting :)

---
arno

---

### Post by Paris Heng on 2007-08-13
Dear pedalwrench,

**It is must use Ubuntu Server rather than the normal Ubuntu Desktop?**

Following your instruction and guide. I using Ubuntu Desktop and  my mobile laptop able to connect to the AP (the wireless part) but unable to use the Internet. How ya? Am i having problem with the bridging?

My interface are:-

ath0 (AP)
eth0 (which connect to the Internet LAN. (same as you .png figure that you attached)

I bridging between ath0 and eth0


I wonder why you using 2 interface? eth1 (WAN) and eth2 (LAN) ? Why you need eth1 ? after i type ***ifconfig***, i only have until eth0, i don't have the WAN interface in my laptop.


Please reply, thank you.

---

### Post by Paris Heng on 2007-08-17
Dear,

I have follow your Madwifi How-To in the forum. I installed in Ubuntu 7.04, and i can connect to internet, I mean it works great!! I able to change mode to like Ad-hoc and AP. 

And when i add a route to **ath0 **:-

**route add -net 192.168.1.1 netmask 255.255.244.0 dev ath0**

**it give unrecognized interface for ath0!!!**


So, it is wrong in installing the Madwifi for your guide that you have post previously?


Thank you.

---

### Post by pedalwrench on 2007-08-18
Paris,

i just PM'd you on your other question, for this question do you know the dev id of the card (ath0, ath1, wlan0 ?)  

it may have installed weird



> **Paris Heng said:**
> Dear,

I have follow your Madwifi How-To in the forum. I installed in Ubuntu 7.04, and i can connect to internet, I mean it works great!! I able to change mode to like Ad-hoc and AP. 

And when i add a route to **ath0 **:-

**route add -net 192.168.1.1 netmask 255.255.244.0 dev ath0**

**it give unrecognized interface for ath0!!!**


So, it is wrong in installing the Madwifi for your guide that you have post previously?


Thank you.

---

### Post by stinkylemon on 2007-08-27
Pedalwrench,

I used your howto and got my server running!  Thanks for the great post!  I have 2 questions now:

1.)  When we tried to get the network clients up through their access points, we'd only see the signal sporadically.  If you were to look at our ping 192.168.1.1 -t, you'd see it reply for a while, but then it would time out for long periods of time and then come back online.  The response times would fluctuate wildly.  Is that a hardware problem, or is that due to the distance I'm shooting the wireless signal (300 meters)?  The signal is amplified, so even at 300 meters, we'd still get 4 out of 5 bars when connecting off of wireless cards on laptops.  I just think the wifi card wasn't working right.

2.) I couldn't get that working reliably, so my next task was to swap out the wifi card with a CAT 5 NIC from D-Link to use an access point to forward traffic to the Linux box.  Ubuntu recognized that card as eth2 and the onboard NIC as eth0.  It didn't seem to matter what I did, I couldn't get that bridge to work!  Every time I set the bridge up, I'd lose my ability to ping out to the Web.  Also, sometimes Linux would randomly call the D-Link NIC eth1.  What would cause that to happen?  I think that, if I can get around that problem, the bridge will work right.

Thanks for putting up great posts, and let me know what you think!

Stinkylemon

---

### Post by sjcire on 2007-08-31
Great guide, thanks.  I having a hard time getting an internet connection established to my wireless client, my laptop.  The laptop can detect my AP, connect, get correct IP but will not open web pages.  I feel it has to do with nat but not sure how to fix it.  I thought i followed the guide to the T.  I have a similar configuration 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
	

auto eth1
iface eth1 inet dhcp
pre-up iptables-restore < /etc/iptables.conf

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet manual
wireless-mode master
wireless-essid linuxsucks

auto wlan0
iface wlan0 inet dhcp

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth0 ath0


I have tried bridge port options eth0 ath0, eth1 ath0, and eth2 ath0.  eth1 is the WAN, eth0 is the LAN, ath0 is ap, and eth2 doesnt actually exist but Ubuntu loves to write that in their.  Everything is a cut and past (i'm lazy).  When I start my router box i do not get a internet access until i type in the terminal sudo dhclient3 br0.  Then i can connect.  I'm stumped. Cheers Eric

---

### Post by ebs16 on 2007-10-26
how can I enable upnp support on this type of setup?

---

### Post by Sluff on 2008-01-26
Great Document!

I recently setup an Ubuntu LAMP Server and added DHCP, BIND, Open-SSH, Drupal, and a few other things.  Now that it's running, and running well, I considered adding a wireless NIC and letting it do my wireless also.  I have a few PCM/CIA cards which I would need a PCI adapter for, and I have one PCI card wireless NIC.  Either a D-link or Belkin.  I currently run the Linksys WRT-54G but would love to turn it off.  I would like it to be a secure wireless network.  The bridge option never dawned on me.  I kind of like that idea.  Thanks for the great post.   I have to give this a try. :)

---

### Post by TheCl@ssic on 2008-01-27
I would like to continue using my current wireless router, but use my Ubuntu machine to get my wireless incapable Xbox on my network. I want the Xbox to be seen by all devices on my network, so I think I want my Ubuntu box to act as a switch instead of a router (am I right?). I prefer acting as a switch as opposed to a hub to keep traffic between the Xbox from going through my Linksys router. How would I modify your instructions to make this happen?

---

### Post by TheCl@ssic on 2008-02-01
[SIZE="2"]I'm sure I followed the instructions substituting the correct adapter names. When I run diagnostics from Vista everything looks good except I get the following: Ping Network 192.168.2.255 : Failed
Does anybody have any suggestions for what I might be doing wrong? I would be extremely happy if somebody could help me get this working.[/SIZE]

Heres my interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.2.1
    network 192.168.2.0
    netmask 255.255.255.0
    broadcast 192.168.2.255

More info:
I've followed the instructions but haven't been successful. My setup differs in that I'm using a wireless card as the gateway and eth0 as a LAN interface. I can ping the gateway but I haven't been able to ping outside the LAN from the device connected to eth0 (a Vista machine). Please confirm:
Since the LAN is a single interface I don't need a bridge.
Since the wireless card is the WAN interface and not a LAN interface I don't need to worry about enabling master mode.
Since I'm making an adapter to adapter connection, I'm using a cross-over cable.

The wireless is connecting to a Linksys router. I also noticed that I have a wmaster interface listed in my ifconfig, I have no idea what that is.

---

### Post by TheCl@ssic on 2008-02-02
In your instructions for iptables you use the address 10.1.1.0/24
I used 192.168.2.0/24

I'm not sure what the "24" after the slash is for. Did I do this correctly?

---

### Post by TheCl@ssic on 2008-02-02
I got it working using FireStarter. If anybody can answer my previous questions though, I'd like to be able to do this without using Firestarter. I'm glad I finally got it working though.

---

### Post by reauthor on 2008-02-09
> **pedalwrench said:**
> Good to see people taking this and moving forward.  This is just a how to get it going.  Hopefully people are able to connect the dots and build onto it.  like the previous post, it is possible to make this out of energy efficient components, but it is up to you to do it.

Here are some of the reasons I did it:

1. To learn something new
2. To re-use old outdated hardware
3. To teach others the skills I have learned
4.  As a Do-It-Yourself (DIY) type guy, I like disecting things and getting them to work on my own.

There are multiple ways to do everything, I found that this is the best method for me.  Your mileage may very on everything but have fun doing it.

very good work...thanks man.And great reasons too.

---

### Post by faulkes on 2008-02-09
> **TheCl@ssic said:**
> In your instructions for iptables you use the address 10.1.1.0/24
I used 192.168.2.0/24

I'm not sure what the "24" after the slash is for. Did I do this correctly?

The /24 after the ip blocks is CIDR notation (classless inter-domain routing), it is a way of subnetting networks beyond the traditional classful method (A,B,C,D, etc).  A /24 is the equivalent of a class C address block (255).

Faulkes

---

### Post by faulkes on 2008-02-09
> **TheCl@ssic said:**
> 
More info:
I've followed the instructions but haven't been successful. My setup differs in that I'm using a wireless card as the gateway and eth0 as a LAN interface. I can ping the gateway but I haven't been able to ping outside the LAN from the device connected to eth0 (a Vista machine). Please confirm:
Since the LAN is a single interface I don't need a bridge.
Since the wireless card is the WAN interface and not a LAN interface I don't need to worry about enabling master mode.
Since I'm making an adapter to adapter connection, I'm using a cross-over cable.

The wireless is connecting to a Linksys router. I also noticed that I have a wmaster interface listed in my ifconfig, I have no idea what that is.

It sounds like ip forwarding is not turned on, also note that the linksys router must also have a route pointing back to the wireless interface to know how to send traffic back (unless you are using nat).

```

sysctl -a | grep net.ipv4.ip_forward

```

If that value is set to 0 (zero) then ip forwarding is not turned on.

you can turn it by doing

```

sysctl -w net.ipv4.ip_forward="1"

```

Note that this only temporarily turns it on, if you reboot the setting will be lost, see the sysctl.conf manpage for adding it for more permanent behaviour.

Faulkes

---

### Post by ways on 2008-05-02
has anyone tested this on hoary?

---

### Post by scorp123 on 2008-05-02
> **ways said:**
> has anyone tested this on hoary? Hoary?? That's hopelessly outdated.

I suggest you consider upgrading to a newer release.

---

### Post by diablo75 on 2008-05-20
Is there a shorter version of this tutorial that could be written for Backtrack?  I like to use it's Live CD because it automatically puts the madwifi drivers in place, and lets me do whatever I want to the card.

All I want to do is share an Internet connection from my ethernet interface with a Nintendo Wii wirelessly.  Sure, I'm putting off spending 20 or 30 bucks for a USB ethernet adapter for the Wii, but I would be a fun little experiment to get it working by turn my laptop into a wireless router.

---

