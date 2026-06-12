---
title: "HOWTO: be in two places at once a.k.a Ipredator independant of the default route"
date: 2010-05-04
forum: Server Platforms
---

### Post by simonn on 2010-05-04
I have a home server running Lucid which basically runs our home lan, but I also wanted to be able to run transmission-daemon over an ipredator VPN connection completely independently of the ethernet port (as far as the application layer is concerned anyway). 

Most of the howtos for setting up VPN use the VPN as the default route, however I still wanted to run a webserver, dnsmasq etc, not to mention free bandwidth access to my ISP etc.

Thus, this howto.

The ppp connection still tunnels through eth0, but as far everthing else is concerned my server has two independent network ports eth0 and ppp0 and applications use the default route via eth0 to our router unless explicitely directed down pppX.

I assume that you already have transmission-daemon installed.

Firstly, install linux-pptp:

```

$ sudo apt-get install linux-pptp

```

Create /etc/ppp/peers/ipredator, replace <username> with your user name.

```

pty "pptp vpn.ipredator.se --nolaunchpppd --loglevel 0"
lock
noauth
nobsdcomp
nodeflate
name <username>
remotename ipredator
ipparam ipredator
require-mppe-128
refuse-eap
maxfail 0
persist
mru 1435
mtu 1435
nolog

```

Edit /etc/ppp/chap-secrets and add a line like so, replacing <username> and <password> with your username and password:

```

# Secrets for authentication using CHAP
# client	server		secret		IP addresses
<username>	ipredator	<password>	vpn.ipredator.se

```

For the ppp interface to work independantly, we need to create a routing table for it. Edit /etc/iproute2/rt_tables and add the 100 predator line so it looks like below:

```

#
# reserved values
#
255	local
254	main
253	default
0	unspec
#
# local
#
#1	inr.ruhep
100	ipredator

```

Edit /etc/default/transmission-daemon and add the BIND_ADDRESS parameter. Do set BIND_PARAMETER to 1.2.3.4 below. The ip address will be changed to the ip address of the ipredator ppp connection by /etc/ppp/ip-up.d/010ipredator when the connection is started/restarted.

```

# defaults for transmission-daemon
# sourced by /etc/init.d/transmission-daemon

# change to 0 to disable daemon
ENABLE_DAEMON=1

# this directory stores some runtime information, like torrent files and config
CONFIG_DIR="/var/lib/transmission-daemon/info" 

BIND_ADDRESS=1.2.3.4

# default options for daemon, see transmission-daemon(1) for more options
OPTIONS="-g $CONFIG_DIR -i $BIND_ADDRESS"

```

Create /etc/ppp/ip-up.d/010ipredator. This script is run whenever a connection is started. We use this script to set up the routing rules, firewall rules and to restart transmission-daemon binding it to the ip address of the ppp connection.

Note that you have to script this as a restart as /etc/ppp/ip-down.d/010ipredator is not called if the connection drops.

```

#!/bin/sh
#PPP_IPPARAM	: ipparam set in /etc/ppp/peers/ipredator
#IFNAME		: interface name. Usually ppp0.
#PPP_REMOTE	: remote ip address
#PPP_LOCAL	: local ip address, i.e. the ip address of pppX

if [ "$PPP_IPPARAM" = "ipredator" ]; then
	# Delete any dangling ipredator rules
	ip rule | sed -n 's/.*\(from[ \t]*[0-9\.]*\).*ipredator/\1/p' | while read RULE
	do
		ip rule del $RULE
	done

	# Delete any unneccesary and dangling ipredator routes
	ip route | sed -n 's/^\(93.182.[0-9]*.2\).*/\1/p' | while read ROUTE
	do
		ip route del $ROUTE
	done

	# Add the rule to direct all traffic from pppX ip address to
	# the ipredator routing table
	ip rule add from $PPP_LOCAL lookup ipredator

	# Add the route to direct all traffic using the the ipredator 
	# routing table to the pppX interface
	ip route add default dev $IFNAME table ipredator 

	# ntpd will use the pppX interface, so block it
	iptables -A OUTPUT -o $IFNAME -p udp --dport 123 -j DROP

	# Open DHT port on pppX
	iptables -A INPUT -i $IFNAME -p tcp --dport 51413 -j ACCEPT

	# Bind transmission-daemon to the address of pppX
	sed -i "s/BIND_ADDRESS=[0-9\.]*/BIND_ADDRESS=$PPP_LOCAL/g" /etc/default/transmission-daemon

	# Restart transmission-daemon. Uncomment after testing.
	#/etc/init.d/transmission-daemon restart

fi

```

Create /etc/ppp/ip-down.d/010ipredator. No comments as it should be clear what is going on here. This is run whenever the ipredator connection is stopped. It is not run if the connection drops.

```

#!/bin/sh

if [ "$PPP_IPPARAM" = "ipredator" ]; then
	ip rule | sed -n 's/.*\(from[ \t]*[0-9\.]*\).*ipredator/\1/p' | while read RULE
	do
		ip rule del $RULE
	done

	ip route | sed -n 's/^\(93.182.[0-9]*.2\).*/\1/p' | while read ROUTE
	do
		ip route del $ROUTE
	done

	/etc/init.d/transmission-daemon stop

	iptables -D OUTPUT -o $IFNAME -p udp --dport 123 -j DROP
	iptables -D INPUT -i $IFNAME -p tcp --dport 51413 -j ACCEPT
fi

```


To start ipredator:

```

$ sudo pon ipredator

```

After a few seconds and all things going well running ifconfig should return a pppX entry, e.g.

```

$ ifconfig
....
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:93.182.x.x  P-t-P:93.182.x.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1431  Metric:1
          RX packets:28291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9986616 (9.9 MB)  TX bytes:25842958 (25.8 MB)
....

```

inet addr:93.182.x.x is the ip address of the vpn connection.

If this interface does not appear look in /var/log/syslog for pppd messages.

Test the connection:

The following should return the ip address supplied by your ISP:

```

$ wget -qO - ip1.dynupdate.no-ip.com

```

The following, replacing <pppX ip address> with the obvious, should return your ipredator ip address (the pppX ip address):

```

$ wget --bind-address <pppX ip address> -qO - ip1.dynupdate.no-ip.com

```

If both the wget tests above work, all is well in the world. Uncomment out the "/etc/init.d/transmission-daemon restart" line in /etc/ppp/ip-down.d/010ipredator and...

```

$ sudo poff ipredator
$ sudo pon ipredator

```

This will start transmission-daemon automatically. 

Using netstat -a you should see loads of connections to ipredatator made by transmission-daemon when torrents are started.

You can use many other commands via ipredator, but you have to expicitly use the pppX interface or ip address, e.g. wget as above, traceroute etc. If you want to use a browser via pppX you will need to setup a proxy server and bind/{,re}start it like transmission-daemon in /etc/ppp/ip-down.d/010ipredator, tinyproxy is probably your best bet for this.

I wish I had kept a record of all the sources on the internet I used to create this howto, but I did not. So thanks, whoever you are!

---

### Post by hazzek on 2010-05-23
Thanks! Worked lite a dream! :D =D> :D

---

### Post by hazzek on 2010-05-24
Opinion:
I think sometimes the 'ip route add' at ip-up will not get added, but if I first flush the table 'ip route flush table ipredator' it appears to work better. Does that make sense? :confused:

---

### Post by manu69 on 2010-11-02
After I was warned off, because my friends downloaded too much random stuff through my server, this is just what I needed. Very elegant solution. thanks!!!

Some remarks:

-why not exchange all the individual rule-deleting for *ip route flush table ipredator*?
-witopia.org has a PPTP-vpn for just 35 USD/year. With coupon from retailmenot.com. Their service is quite good. I've been using it for a year, while in CN.

---

### Post by sissou on 2010-11-05
Your solution has been working great on my server for a couple of months.
Thanks a lot.

A question though : are you facing frequent interrupts with ipredator service (downloading and uploading  = 0 kb/s) that brings you to restart manually (poff, pon ipredator) ?
And if you are, any solution ?

Thanks again !

NB : sorry for my bad english speaking straight from france... :(

---

### Post by chaynlynk on 2010-11-17
This thread is definitely helpful. I was pretty stuck on how to segregate the traffic.

I wanted to add something after having played around with the iptables. I'm using a default policy of ACCEPT. I didn't want to do anything with any other traffic except ppp0. So my /etc/ppp/ip-up.d/010ipredator looks like this.

```

#!/bin/sh
#PPP_IPPARAM    : ipparam set in /etc/ppp/peers/ipredator
#IFNAME         : interface name. Usually ppp0.
#PPP_REMOTE     : remote ip address
#PPP_LOCAL      : local ip address, i.e. the ip address of pppX

if [ "$PPP_IPPARAM" = "ipredator" ]; then
        # Delete any dangling ipredator rules
        ip rule | sed -n 's/.*\(from[ \t]*[0-9\.]*\).*ipredator/\1/p' | while read RULE
        do
                ip rule del $RULE
        done

        # Delete any unneccesary and dangling ipredator routes
        ip route | sed -n 's/^\(93.182.[0-9]*.2\).*/\1/p' | while read ROUTE
        do
                ip route del $ROUTE
        done

        # Add the rule to direct all traffic from pppX ip address to
        # the ipredator routing table
        ip rule add from $PPP_LOCAL lookup ipredator

        # Add the route to direct all traffic using the the ipredator
        # routing table to the pppX interface
        ip route add default dev $IFNAME table ipredator

        #Flush the tables
        iptables -F

        #Drop any traffic coming in from ppp0 that isn't established or related.
        iptables -A INPUT -i $IFNAME -m state ! --state ESTABLISHED,RELATED -j DROP
fi

```

---

### Post by nordge1 on 2010-12-23
This awesome tutorial works perfect for me up to the point where you check the IP of the PPP0.

The following, replacing <pppX ip address> with the obvious, should return your ipredator ip address (the pppX ip address):

Code:
$ wget --bind-address <pppX ip address> -qO - ip1.dynupdate.no-ip.com

The response I get is that it hangs with no response. I can Ctl-C and cancel the command. The command I am issuing is:
wget --bind-address 93.182.133.71 -qO - ip1.dynupdate.no-ip.com

Where 93.182.133.71 is the IP on the PPP0

Also I'm running this in a VM with a bridged network adapter to the host.

Any help would be greatly appreciated

---

### Post by devcloud on 2011-01-18
> **nordge1 said:**
> This awesome tutorial works perfect for me up to the point where you check the IP of the PPP0.

The following, replacing <pppX ip address> with the obvious, should return your ipredator ip address (the pppX ip address):

Code:
$ wget --bind-address <pppX ip address> -qO - ip1.dynupdate.no-ip.com

The response I get is that it hangs with no response. I can Ctl-C and cancel the command. The command I am issuing is:
wget --bind-address 93.182.133.71 -qO - ip1.dynupdate.no-ip.com

Where 93.182.133.71 is the IP on the PPP0

Also I'm running this in a VM with a bridged network adapter to the host.

Any help would be greatly appreciated

I just followed this guide and had exactly the same result as you.
After spending more of the evening than i would care to admit trying to see what i've done wrong i re-read the guide again and then #-o it clearly says "Create /etc/ppp/ip-up.d/010ipredator. This script is run whenever..."

/etc/ppp/ip-up.d/010ipredator & /etc/ppp/ip-down.d/010ipredator are scripts and so need to be executeable so...

sudo chmod +x /etc/ppp/ip-up.d/010ipredator
sudo chmod +x /etc/ppp/ip-down.d/010ipredator

...and now since this is working i can stop scratching my head and go to sleep :)

---

### Post by nordge1 on 2011-01-19
devcloud
You are the MAN!!!!! 
Oh thank you, that's been killing me for months.
thank you

---

### Post by Icovada on 2011-05-15
I've been trying to set this up for two weeks now but nobody helped. Thanks a ton!

Hope you'll come up with an OpenVPN version as well

---

### Post by rcastberg on 2012-05-11
I've always though that my sever was safe behind the router, and didn't think much after applying the scripts in the first post.

Recently due to other problems i started cleaning up on the server and noticed that i had a lot of connections to my samba server from people using the vpn.

I liked the idea chaynlynk posted though closed all the ports and thus i can't receive incoming connections.

i changed the iptables to the code below:
```

    #Allow all established connections
    iptables -A INPUT -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT
    # Open DHT port on pppX
    iptables -A INPUT -i ppp0 -p tcp -m tcp --dport 51413 -m state --state NEW,ESTABLISHED -j ACCEPT
    #Drop everything else
    iptables -A INPUT -i ppp0  -p tcp -j DROP

```

From a portscan on my public ip it appears that the public port 51413 is still open and everything else is closed.

Any comments or ideas are appreciated.

---

