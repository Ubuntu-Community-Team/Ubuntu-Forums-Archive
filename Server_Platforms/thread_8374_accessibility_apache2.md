---
title: "accessibility apache2"
date: 2004-12-16
forum: Server Platforms
---

### Post by miss tina on 2004-12-16
hi,
i'm trying to run the apache2 server, its up and running, but the server can't be accessed from the internet on the local intranet it works, i've checked and checked again the permissions and the /etc/hosts file and the server configuration file looks good to me... 
Because the server is up and running i don't get any error messages, i don't know  how  to solve the  problem.
I've allso disabled the ipv6 (cause i ran into probs using ipv6 with apache on a gentoo-box before...) this is done by putting 
[COLOR=YellowGreen]alias net-pf-10 off[/COLOR] in /etc/modprobe.conf

/etc/hosts >
[COLOR=YellowGreen]127.0.0.1       localhost.tina.servepics.com tina
192.168.0.104   tina.servepics.com tina
192.168.0.104   tina.servepics.com
# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
[/COLOR]

/etc/hostname > tina
/etc/hosts.allow >ALL:ALL
/etc/hosts.deny > is empty
 


/etc/apache2/apache2.conf is back the default apache page from instal i've tried to do some vhosts stuff before but no succes still not accesible...

first i've tried was compiling apache2 from source but i ran into the same prob it only works local...
at the moment i'm using back the precompiled apache pakages from the distribution...
 please give me a hint 
tnx tina

ps. router ect is no prob cause apache2 works on my windows(but i don't boot that any more)
pps. I'm using the no-ip.com duc to do the dynamic update for my ip witch is also up and running.

---

### Post by Hellsteeth on 2004-12-19
I would start with checking if you can first access the internet from your server. Try pinging some external site that you know returns pings i.e. $ ping [www.cisco.com](www.cisco.com)

If this is ok, then you need to check on your own server if port 80 is open. If you are running a software firewall on the server, temporarily disable it to see if this is what is causing the problem. Alternatively you can download and run from your networked Windows machines a port scanner such as ipscan from [http://www.angryziber.com/ipscan/](http://www.angryziber.com/ipscan/).

If port 80 on the pc is ok then look to see if you need to open port 80 on your  modem or router. This will be under something like Firewall rules. You will have to specify the IP address of your linux server pc in your router. It may still be pointing at your old Windows machines IP address?

If this is ok and open you will need to look at exactly how you are accessing the url and from what machine.

Are you accessing by a url or an IP address?

A final thought. When you say you cannot see the webserver from the internet, is this fact realised from a pc on the internet that is _not_ also on your home network? This is an important point. You may find that you can in fact access your Apache2 webserever from your work pc or a neighbours house but not from within your own network that the webserver runs from. This is fixed a different way and is currently just fooling you into thinking you cannot see the webserver from the internet. 

I hope this has given you some pointers. If it still does not work perhaps you can follow up with some more info on how your network is setup?

---

