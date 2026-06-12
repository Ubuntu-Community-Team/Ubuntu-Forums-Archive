---
title: "How to Server ICS and DNS Config"
date: 2013-01-27
forum: Server Platforms
---

### Post by chrisguk on 2013-01-27
**PLEASE NOTE THERE ARE SOME THREADS AT THE BOTTOM OF THIS POST WITH QUESTIONS**


In around the forums and the general web population there are many tutorials on how to set up things.  Mostly the tutorials are custom in order to meet the writers needs and I am no exception to this rule.  In my small experience even the generic tutorials are open to interpretation and need to be tweaked to fit the needs of the individual.

As with anything I do I wish to share my recent ICS (internet connection sharing) and DNS Server setup below.

Feel free to use it but for the experts out there I am kind of hoping you will find areas that I have either missed or improvements.

One thing I need to add is with the config below I was unable to get a Windows client to access the internet outside the network without populating the google DNS 8.8.8.8 8.8.4.4 in the IPv4 tables in the ncpa.cpl.  If you know of a workaround based on my config below then please feel free to comment:

===Setting up a Internet Facing Network===

Before I begin this post, I want to thank Internet Connection Sharing &#8211; Ubuntu 10.04 NAT Gateway Setup (Abridged Version) for providing the bulk of the tutorial. I have made some modifications for Ubuntu 12.04.

The setup is simple: a single Ubuntu server will act as a gateway and DHCP server for a local network. All other machines on the local network will receive their IPs from the DHCP server. To make things easier, I&#8217;ll call this Ubuntu server &#8220;maggie&#8221; for the rest of the post.

maggie has two network interfaces, eth0 and eth1. eth0 is on the 192.168.178.1/24 subnet and this is the Internet facing interface. eth1 is on the 172.22.22.0/24 subnet, where all other machines are also present. Basically, eth0 will connect to the Internet and eth1 will serve DHCP requests and act as the gateway.

==Edit Network Interfaces==

```


/etc/network/interfaces


```

First you need to configure eth0 and eth1 for maggie. Edit the file and make sure it has at least the following settings (or whatever settings are appropriate for your environment).

```


sudo nano /etc/network/interfaces


```

```


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.178.130
        netmask 255.255.255.0
        network 192.168.178.0
        broadcast 192.168.178.255
        gateway 192.168.178.1

        

auto eth1
iface eth1 inet static
        address 172.22.22.40
        netmask 255.255.255.0
        network 172.22.22.0
        broadcast 172.22.22.255

        dns-nameservers 172.22.22.40
        dns-search bart.home



```

==Edit the sysctl==

```


/etc/sysctl.conf


```

You need to enable IPv4 forwarding. To do so, edit this file.

```


sudo nano /etc/sysctl.conf


```

And uncomment the line

```


# net.ipv4.ip_forward=1

so that it now appears as

net.ipv4.ip_forward=1


```

Save the file and run the following command to make the change effective without a reboot.

```


sudo sysctl -w net.ipv4.ip_forward=1


```

==Update the IP tables==

'''/etc/rc.local'''

You&#8217;ll need to allow iptables rules for NAT to work. Edit the file and save it.

```


sudo nano /etc/rc.local


```

Make sure the following two lines appear before the exit 0 line in the file.

```


/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE



```

To make these iptables rules active without rebooting, run the following commands:

```


sudo iptables -P FORWARD ACCEPT

sudo iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE


```

==Install DHCP server==

```


sudo apt-get install isc-dhcp-server


```

== Edit the dhcpd.conf ==

```


/etc/dhcp/dhcpd.conf


```

Configure your newly installed DHCP server. Edit the file and save.

```


sudo nano /etc/dhcp/dhcpd.conf


```

The file is very well commented and you can learn a lot reading it. Just make sure it has at least the following configuration.
ddns-update-style none;

```


# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "bart.home";
option domain-name-servers 172.22.22.40;

default-lease-time 3600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

subnet 172.22.22.0 netmask 255.255.255.0 {
  range 172.22.22.21 172.22.22.250;
  option subnet-mask 255.255.255.0;
  option broadcast-address 172.22.22.255;
  option routers 172.22.22.1;
}


# Fixed IP addresses can also be specified for hosts.   These addresses
# set.
host link {
  hardware ethernet 00:16:B6:4F:3C:8B;
  fixed-address 172.22.22.25;
}

host marge {
  hardware ethernet 00:30:05:FA:D7:CC;
  fixed-address 172.22.22.30;

}

host homer {
  hardware ethernet 00:30:05:FA:D7:CC;
  fixed-address 172.22.22.35;

}



```

```


/etc/default/isc-dhcp-server


```

We want to serve DHCP only on eth1 interface to we need to configure it that way. Edit the file and save it.

==Edit isc-dhcp-server==

```


sudo nano /etc/default/isc-dhcp-server


```

The line will look like this before you change it

```


INTERFACES=""

And after you change it, it will look like this:

INTERFACES="eth1"


```

==Stop and start the DHCP server==

```


sudo service isc-dhcp-server stop (if the service is already running; skip if it&#8217;s not running)
sudo service isc-dhcp-server start


```

==Conclusion==

Now any machines you have on the 172.22.22.0/24 network will get their IP address from maggie if they are set to DHCP. And maggie will also serve as their gateway.


**===Setting up a DNS Server===**

A further detailed guide can be found here:

[[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) BIND9ServerHowto]

To some this can be a daunting task.  This step be step guide will help you master the basics of DNS configuration.

'''In this tutorial "maggie" is the name of the server.'''

Tools used:

*  Ubuntu Server
*  BIND9
*  Ubuntu Client or MS Windows/MAC

Assuming you have Ubuntu server installed lets set things up in order to accommodate DNS configuration.

Its very important for a server to have a "Static IP".  It could cause you all sorts of problems if not.  

'''YOUR CONFIG:'''

Lets see how you are configured:
We are going to give linux a command to check our current IP and gateway etc.  Issue this below:

```


ifconfig


```

==Configure Interfaces==

You should be presented with an output similar to this:

```


# This file describes the network interfaces available on your system                                                         
# and how to activate them. For more information, see interfaces(5).                                                          
                                                                                                                              
# The loopback network interface                                                                                              
auto lo                                                                                                                       
iface lo inet loopback                                                                                                        
                                                                                                                              
# The primary network interface                                                                                               
auto eth0                                                                                                                     
iface eth0 inet dhcp                                                                                                        
                                                                                       
                                                                                                                              
auto eth1                                                                                                                     
iface eth1 inet dhcp                                                                                                        
        


```

You will see the highlight IP addresses above.  This is what we are going to use to make our IP static.
[B]
==Configure the server with a static IP==[/B]

First we are going to replace the default DHCP information with our own:

```


sudo nano /etc/network/interfaces


```

```


 # This file describes the network interfaces available on your system                                                         
# and how to activate them. For more information, see interfaces(5).                                                          
                                                                                                                              
# The loopback network interface                                                                                              
auto lo                                                                                                                       
iface lo inet loopback                                                                                                        
                                                                                                                              
# The primary network interface                                                                                               
auto eth0                                                                                                                     
iface eth0 inet static                                                                                                        
        address 192.168.178.130                                                                                               
        netmask 255.255.255.0                                                                                                 
        network 192.168.178.0                                                                                                 
        broadcast 192.168.178.255                                                                                             
        gateway 192.168.178.1                                                                                                 
                                                                                                                                                                                                               
                                                                                                                              
auto eth1                                                                                                                     
iface eth1 inet static                                                                                                        
        address 172.22.22.40
        netmask 255.255.255.0
        network 172.22.22.0
        broadcast 172.22.22.255

        dns-nameservers 172.22.22.40
        dns-search bart.home.



```

==Configure the hosts file==

We shouldn't have to do much editing in the hosts file but lets take a look:

```


sudo nano /hosts


```

```


127.0.0.1       localhost
172.22.22.40    maggie.bart.home maggie

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```

==REMOVE-NETWORK MANAGER==

At this stage we want to remove network-manager as it interferes with the modifications that we have and are about to make.  Essentially we don't want Network-manager to manage our configuration:

```


sudo apt-get remove network-manager network-manager-gnome


```

'''Lets restart the network to ensure there are no errors:'''

```


sudo service networking restart


```

==Edit the zone records==

```


sudo nano /etc/bind/named.conf.local


```

In this file you will be presented with a blank canvas.  All you have to do is enter the following elements below:

'''Explanation:''' In this file we are declaring the new zones.  The file locations below will be created in the next stage.  It is always good practice to call the file names similar to your new DNS config.  In the reverse area you will note that all this is the first three octets reversed and nothing more.  "bart.home" is the domain name and you can call it what you wish.  Its good practice however to add the ".db" on the end of the file name.

```


#FORWARD
zone "bart.home"
{

        type master;
        file "/etc/bind/zones/bart.home.db";                                               
                                                          
                                            
};

#REVERSE
#172.22.22.40
zone "22.22.172.in-addr.arpa"
{
        type master;  
        file "/etc/bind/zones/rev.22.22.172.in-addr.arpa"; 
                                                             
                                                              
                                                            
};


```

```


sudo nano /etc/bind/named.conf.options


```

In this file there is a little less to worry about.  All we need to do is enter a few IP address as illustrated below.  The IP starting with "172" is the gateway IP.  In my case its the server IP as this server is the gateway to the outside world.  The other two IP addresses should be fairly familiar as they are the DNS IPs for Google.

```


options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable 
        // nameservers, you probably want to use them as forwarders.  
        // Uncomment the following block, and insert the addresses replacing 
        // the all-0's placeholder.

         forwarders {
                172.22.22.40;
                192.168.178.1;
                8.8.8.8;
                8.8.4.4;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};



```


==Create zone folders==


```


sudo mkdir /etc/bind/zones


```

You will remember above regarding the naming of the forward and reverse zones.  Lets just grab a reminder of what those files should be called:

```


sudo cat /etc/bind/named.conf.local


```

'''CODE OUTPUT:'''

```


file "/etc/bind/zones/bart.home.db";


```

```


file "/etc/bind/zones/rev.22.22.172.in-addr.arpa";


```

So we just want to make new files to sit in the /etc/bind/zones folder as above and like so:

```


sudo nano bart.home.db


```

```


sudo nano rev.22.22.172.in-addr.arpa


```

Ensure you replace the IP with the reverse of your server IP

==The new Forward Record==

Lets populate the blank file below:

```


sudo nano /etc/bind/zones/bart.home.db


```

```

$TTL 3D
@       IN      SOA     maggie.bart.home. admin.bart.home. (
                        2013011403;
                        28800;  
                        3600; 
                        604800;  
                        3600 

);

bart.home.      IN      NS      maggie.bart.home.
router          IN      A       172.22.22.40
link            IN      A       172.22.22.25
marge           IN      A       172.22.22.30
homer           IN      A       172.22.22.35
maggie          IN      A       172.22.22.40
lisa            IN      A       172.22.22.45
www             IN      A       172.22.22.50
website         IN      CNAME   maggie
mediawiki       IN      CNAME   maggie
bacula          IN      CNAME   maggie



```

Once you have finished in that file just save and close.

==The new Reverse Record==

```


sudo nano /etc/bind/zones/rev.178.168.192.in-addr.arpa


```

As you can see the are some subtle differences between the forward and reverse.

```


$TTL 3D
@       IN      SOA     maggie.bart.home. admin.bart.home. (
                        2013011307;
                        28800;
                        3600;
                        604800;
                        38400 
);

                        IN      NS      maggie.bart.home.
40                      IN      PTR     router.bart.home
25                      IN      PTR     link.bart.home
30                      IN      PTR     marge.bart.home
35                      IN      PTR     homer.bart.home
40                      IN      PTR     maggie.bart.home 
45                      IN      PTR     lisa.bart.home
50                      IN      PTR     www.bart.home


```

==Edit resolv.conf==

The final editing we want to take care of is a file called "resolv.conf":

```


sudo nano /etc/resolve.conf


```

Your file will more than likely be populated with something similar to what we have below.  All you need to remember is to ensure you have the following lines:

```


search bart.home.
domain bart.home.
nameserver 172.22.22.40


```

Thats it.  Now restart the '''BIND service'''

```


sudo service bind9 restart


```

To check that everything works lets use NSLOOKUP:

```


nslookup maggie


```

You should see something similar to this:

```


Server:         172.22.22.40
Address:        172.22.22.40#53

Name:   maggie.bart.home
Address: 172.22.22.40


```

```


nslookup 172.22.22.40


```

Hopefully if all has gone well you should see something similar to this:

```


Server:         172.22.22.40
Address:        172.22.22.40#53

40.22.22.172.in-addr.arpa    name = maggie.bart.home.


```

==Errors==

If you start get errors after restarting BIND then I recommend to use the following command.  Its a great tool to help you find your errors:

```


tail -f /var/log/syslog


```

==LETS CONFIGURE YOUR CLIENT==

On the client, we would prefer to have a static IP address as well.  This can avoid any future complications that may occur.

```


sudo apt-get remove network-manager


```

Once that has been completed with need to carry out the same process for updating the network interfaces, but with a few different configurations:

==Client Network Interface==

Lets see what the interface file looks like:

```


cat /etc/network/interfaces


```

```


iface eth0 inet dhcp
 

```

It is possible that you will have something like the above.  We want to change it to not only create a static IP but to reflect the DNS server like below:

```


auto eth0
iface eth0 inet static
  address 172.22.22.35
  netmask 255.255.255.0
  network 172.22.22.0
  gateway 172.22.22.40
  broadcast 172.22.22.255
  # dns-* options are implemented by the resolvconf package, if installed
  dns-search bart.home.
  dns-nameservers 172.22.22.40



```

As you can see above I have declared the DNS server so that it will be included in the /etc/resolv.conf file each time the network is started or computer for that matter.

You can close and save that file now.

'''Next....'''

We want to edit the /etc/resolv.conf file to match the setting below but using the name of your server etc:

```


sudo nano /etc/resolv.conf


```

```


domain bart.home.
search bart.home.
nameserver 172.22.22.40


```

==Update Client hosts==

```


sudo nano /etc/hosts


```

My hosts file looks like this and seems to work ok:

```


127.0.0.1       localhost localdomain.localhost
172.22.22.40    homer.bart.home homer


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters



```

==Please restart your client PC.==

If you run the following commands '''(using your server details)''' you should see the details below:

```


nslookup bart


```

```


nslookup 172.22.22.40


```

```


Server:         172.22.22.40
Address:        172.22.22.40#53

Name:   maggie.bart.home
Address: 172.22.22.40


```

---

### Post by Doug S on 2013-01-27
Edit: This post will no longer make sense to the readers, as chrisguk has edited the original post.
 
I don't understand what is "Skyray". It seems to be "maggie" but the addresses don't make sense. I don't understand the 192.168.178.0 sub-net verses the 10.20.30.0 sub-net and or how they are related.
 
In a ubuntu server computer there is no "network-manager", so I don't understand.I also don't understand editing resolv.conf, it should be created automatically.

---

### Post by chrisguk on 2013-01-27
> **Doug S said:**
> I don't understand what is "Skyray". It seems to be "maggie" but the addresses don't make sense. I don't understand the 192.168.178.0 sub-net verses the 10.20.30.0 sub-net and or how they are related.
 
In a ubuntu server computer there is no "network-manager", so I don't understand.I also don't understand editing resolv.conf, it should be created automatically.

my apologies, they were typos.  As like most tutorials around the web this was a compilation and I left some parts in my tut from an old one.

The differences in the subnets are:

192.168.178.1 is the ISPs Router/hun with integrated phone
172.22.22.40 is everything behind my DNS server and cisco switch

I hope that helps

---

### Post by Doug S on 2013-01-27
O.K. that makes sense.
For your dhcpd setup, I would highly recommend that your dynamic address pool be exclusive of your mac address based addresses, to avoid potential future conflict. I'm suggesting that this:```
subnet 172.22.22.0 netmask 255.255.255.0 {
  range 172.22.22.21 172.22.22.250;
  option subnet-mask 255.255.255.0;
  option broadcast-address 172.22.22.255;
  option routers 172.22.22.1;
}
```be changed to (say) this:```
subnet 172.22.22.0 netmask 255.255.255.0 {
  range 172.22.22.100 172.22.22.250;
  option subnet-mask 255.255.255.0;
  option broadcast-address 172.22.22.255;
  option routers 172.22.22.1;
}
```Also, I'm confused, isn't the router at 172.22.22.40?

---

### Post by chrisguk on 2013-01-27
Hi,

I will take that advice and play around to see the affects.

I am glad you mentioned that about the 172.22.22.40 because that is something I have yet to figure out.

I made change after change to get the DNS to work on the LAN but making the IP 172.22.22.40 was the only way.  Of course you can see that the Server(the LAN gateway) is also 172.22.22.40.

What do you suggest?

---

### Post by Doug S on 2013-01-27
> My hosts file looks like this and seems to work ok:I would take out the line "172.22.22.40 homer.bart.home homer" It is both incorrect (homer is at .35) and isn't needed anyhow. Then you only have one master spot for the information.
 
Try changing the options routers line to what it actually is. Also, I don't undertstand why you had troubles making it 172.22.22.1. Yes, gateway and router are the same thing, in this context.

---

### Post by Doug S on 2013-01-27
My posting number 4 above is incorrect as to how to make the dynamic pool exclusive of the mac and static based addresses. There is a common segment that is needed for both, and then the individual segments. The related part of my dhcpd.conf is:```
# option definitions common to all supported networks...
 
default-lease-time 86400;
max-lease-time 93000;
option domain-name "smythies.com";
# option domain-name-servers 192.168.111.1, 75.154.133.68, 75.154.133.100;
option domain-name-servers 192.168.111.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.111.255;
option routers 192.168.111.1;
 
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;
 
# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;
 
# The Basic DHCP allocated addresses
 
subnet 192.168.111.0 netmask 255.255.255.0 {
  range 192.168.111.3 192.168.111.50;
}
 
# Some specifically declared static IP addresses
 
host Wireless-R {
  hardware ethernet 00:22:6B:82:01:55;
  fixed-address 192.168.111.57;
}
 
host Doug-XPS {
  hardware ethernet 00:23:4d:a6:ed:c4;
  fixed-address 192.168.111.100;
}
...
```

---

### Post by chrisguk on 2013-01-27
You did have me confused lol :)

as you can see I made the fixed address declaration

---

### Post by chrisguk on 2013-01-27
Im bumping this thread because something in the back of my mind is telling me that even though everything is working I haven't set my server up correctly.

Why?

Well this article for one:

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Gateway_set_up]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Gateway_set_up")

It talks about "sudo aptitude install dnsmasq" in Advanced gateway configuration.

Plus also a comment from Doug which kinda threw me off too.

I know that traditionally when you have a normal standard LAN the gateway is usually:

192.168.178.1 or similar

I thought that I couldn't issue a random IP address that doesn't bind to a NIC or MAC address.  

My reason for asking this is because I have the DNS on xx.xx.xx.40 and the gateway is also xx.xx.xx.40  I chose that because in the original tutorial it stated that it was the Card IP address that would be used as the gateway on eth1 and eth0 is the link to the outside world.

So is it possible for me to declare that 172.xx.xx.1 is the gateway and still have 172.xx.xx.40 as the DNS within the Internal network?

I shout out to the budding experts for some detailed clarification on this subject because in hind sight I am still a beginner at this Server admin thing.

Thanks in advance

---

### Post by Doug S on 2013-01-28
> It talks about "sudo aptitude install dnsmasq" in Advanced gateway configuration.dnsmasq can be used instead of bind9 to implement a DNS. Many on these forums recommend it, and it is now installed by default. I still use bind9 and don't know when I'll have the time to look into if I should switch to dnsmaq or not.> So is it possible for me to declare that 172.xx.xx.1 is the gateway and still have 172.xx.xx.40 as the DNS within the Internal network?
Sure, if 172.22.22.1 is a different computer than 172.22.22.40. For the network you have described, the gateway and the DNS are the same computer and so should have the same IP address, either 172.22.22.1 or 172.22.22.40> Plus also a comment from Doug which kinda threw me off too.Ugh oh... I was only trying to help not not make things worse...

---

### Post by jdthood on 2013-01-28
> **Doug S said:**
> dnsmasq can be used instead of bind9 to implement a DNS.

Dnsmasq is only a forwarding nameserver, not a recursive nameserver like BIND.

> Many on these forums recommend it, and it is now installed by default.

The dnsmasq-base package is installed by default in Ubuntu Desktop (not in Ubuntu Server). The standalone Dnsmasq package, called 'dnsmasq', which Depends on dnsmasq-base but includes additional configuration files, is not installed by default.

---

### Post by chrisguk on 2013-01-28
> **Doug S said:**
> dnsmasq can be used instead of bind9 to implement a DNS. Many on these forums recommend it, and it is now installed by default. I still use bind9 and don't know when I'll have the time to look into if I should switch to dnsmaq or not.Sure, if 172.22.22.1 is a different computer than 172.22.22.40. For the network you have described, the gateway and the DNS are the same computer and so should have the same IP address, either 172.22.22.1 or 172.22.22.40Ugh oh... I was only trying to help not not make things worse...

Everything is good Doug, in fact you helped a lot indirectly because you made me second guess my setup and check it was all correct.  

All my systems are working fine now and nagios shows that everything is well balanced too which is great of course.  I have reconfigured mx NAS drives too so at the moment I'm quite content except for the fact im replacing six drives tomorrow on one of the servers oh joy !

---

### Post by chrisguk on 2013-01-29
> **das2013 said:**
> hello sir,

can you help me configuring a dhcp server with ICS?

or configuring squid? as I am new in this platform

I think configuring ICS with dhcp would fit better lol ;)

There are a multitude of tutorials on the net about this subject including my tutorial here.  I can certainly try to help if you have a specific question.

**Just a note: ** I think it would be better to start a new thread with your questions because I am not sure if the community like thread hijacking if you get what I mean

---

### Post by Doug S on 2013-01-29
@jdthood: Thanks for the corrections about dnsmasq. I got the misconception that it was installed in the server edition from the 12.04 Beta1-02 ISO of 2012.03.14, where it was installed by default.
 
@chrisguk:> ... you helped a lot indirectly because you made me second guess my setup and check it was all correctHuh? No, I have been saying, and still say, you have several things incorrect. In addition to what I have already written, a couple of new points:```
sudo nano /etc/bind/zones/rev.178.168.192.in-addr.arpa
```should say:```
sudo nano /etc/bind/zones/rev.22.22.172.in-addr.arpa
```and the syntax within the file is incorrect. There should be a "." (period) at the end of each "PTR" line.
 
Edit: Oh, I forgot... this:```
         forwarders {
                172.22.22.40;
                192.168.178.1;
                8.8.8.8;
                8.8.4.4;
         };
 

```should be this:```
         forwarders {
                8.8.8.8;
                8.8.4.4;
         };
 

```

---

