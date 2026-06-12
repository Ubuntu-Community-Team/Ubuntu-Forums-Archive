---
title: "Monitoring LDAP Users"
date: 2012-01-10
forum: Server Platforms
---

### Post by maverickaddicted on 2012-01-10
I have configured one Zentyal Ubuntu Server. It serves only as web server (for internal development process) and Domain Controller. It has not been configured as DHCP Server, however I have created several LDAP users, which is used by other machines to login. There are around 18 machines, including both Windows and Ubuntu. 

Is there any way I can monitor the browsing history of those LDAP users?

---

### Post by maverickaddicted on 2012-01-11
Has someone tried this before?

---

### Post by maverickaddicted on 2012-01-19
so, I think there is no way to log the activity of LDAP users.

---

### Post by Dry Lips on 2012-01-19
I understand LDAP stuff can be tricky. (I'm sorry but I'm no expert myself :(). 
If nobody around here are able to help you out, I would recommend you to visit:
[http://forum.zentyal.org/](http://forum.zentyal.org/)

Good luck.

---

### Post by maverickaddicted on 2012-01-20
I tried to register on their forum twice, but not got any response from them. That's why I thought that someone will help me here.

---

### Post by SeijiSensei on 2012-01-20
The only method I know of to track users' browsing pattern is by putting a proxy like Squid between them and the Internet and logging their requests.  If you do that, those people deserve to be informed that you are tracking them.

---

### Post by maverickaddicted on 2012-01-23
OK, thank you very much for your reply. I will read more about the Squid proxy and will update you. As this is my first server (Most Important Ubuntu), I was wondering What else administration tasks I can do with LDAP Users. Moreover, this is not a DHCP server.

---

### Post by maverickaddicted on 2012-01-31
What type of administration tasks can I do with LDAP users? Those users are on Windows as well as Ubuntu Machines. And My Server is not a DHCP server. Those clients connect to Internet directly via a router.

---

### Post by ruffEdgz on 2012-01-31
> **maverickaddicted said:**
> What type of administration tasks can I do with LDAP users? Those users are on Windows as well as Ubuntu Machines. And My Server is not a DHCP server. Those clients connect to Internet directly via a router.

So I see many questions here so I will do my best to answer them as well as I can:

* LDAP stands for 'Lightweight Directory Access Protocol'. From the name of this service, its a directory of user information that can be accessed from a client to gather/check that information

* LDAP has logs and can make record information about what service has tried to search the LDAP service and if the search was successful or not. Depending on the log level, it can be just emergency or it can be debugging. Example LDAP log content below:
```

[31/Jan/2012:12:13:21 -0500] conn=13415609 fd=64 slot=64 connection from 192.168.0.101 to 192.168.0.100
[31/Jan/2012:12:13:21 -0500] conn=13415609 op=0 BIND dn="" method=128 version=3
[31/Jan/2012:12:13:21 -0500] conn=13415609 op=0 RESULT err=0 tag=97 nentries=0 etime=0 dn=""
[31/Jan/2012:12:13:21 -0500] conn=13415609 op=1 SRCH base="dc=example,dc=com" scope=1 filter="((objectClass=posixAccount))"
.... 
ETC 
....

```

* To repeat what @SeijiSensei said, the only way I know how to watch web searches will be using a proxy like squid. It will have nothing to do with LDAP but more to do with IP/DHCP as squid will keep records of what was allowed. For example below (its RedHat because I work with RedHat at work):
```

1327834107.509    328 141.210.8.133 TCP_MISS/200 3268 CONNECT xmlrpc.rhn.redhat.com:443 - DIRECT/209.132.183.44 -
1327834108.573      0 141.210.8.133 TCP_MEM_HIT/200 2400 GET http://yum.puppetlabs.com/el/6Server/products/x86_64/repodata/repomd.xml - NONE/- application/xml
1327834108.848    269 141.210.8.133 TCP_MISS/200 3993 CONNECT xmlrpc.rhn.redhat.com:443 - DIRECT/209.132.183.44 -
1327834109.192    244 141.210.8.133 TCP_MISS/200 3015 CONNECT xmlrpc.rhn.redhat.com:443 - DIRECT/209.132.183.44 -
1327834109.565    329 141.210.8.133 TCP_MISS/200 3108 CONNECT xmlrpc.rhn.redhat.com:443 - DIRECT/209.132.183.44 -
1327834109.565   2025 141.210.8.133 TCP_MISS/200 18513 CONNECT mirrors.fedoraproject.org:443 - DIRECT/66.35.62.166 -
1327834346.449    358 141.210.2.30 TCP_MISS/200 6652 CONNECT xmlrpc.rhn.redhat.com:443 - DIRECT/209.132.183.44 -

```

I Hope this helps.

---

### Post by maverickaddicted on 2012-01-31
> **ruffEdgz said:**
> So I see many questions here so I will do my best to answer them as well as I can:

* LDAP stands for 'Lightweight Directory Access Protocol'. From the name of this service, its a directory of user information that can be accessed from a client to gather/check that information

* LDAP has logs and can make record information about what service has tried to search the LDAP service and if the search was successful or not. Depending on the log level, it can be just emergency or it can be debugging. Example LDAP log content below:

Thank You very much. What I was thinking that instead of using Squid proxy, I will install "browser-history" package on each user machines and will create one PHP or Python script (However I don't know both programming languages, but will try)on the server to fetch those log files created by browser-history by IP Addresses.
I don't know if this is a good idea or not. Today, I just read about the package and thought that I should use that.

---

### Post by SeijiSensei on 2012-02-01
It's a heck of lot easier to track browsing at the proxy.  You have one log with all the requests indexed by IP address.  There are also tools to create reports from this log like [SARG]("http://sarg.sourceforge.net/").

---

### Post by ruffEdgz on 2012-02-01
> **SeijiSensei said:**
> It's a heck of lot easier to track browsing at the proxy.  You have one log with all the requests indexed by IP address.  There are also tools to create reports from this log like [SARG]("http://sarg.sourceforge.net/").

+1 on this suggestion

---

### Post by maverickaddicted on 2012-02-02
> **SeijiSensei said:**
> It's a heck of lot easier to track browsing at the proxy.  You have one log with all the requests indexed by IP address.  There are also tools to create reports from this log like [SARG]("http://sarg.sourceforge.net/").

Thanks for giving more idea. I will do it. Now, I have one more question. I have internet connection provided by two ISP. Gateway for one Router A is 192.168.1.3 and 192.168.2.1 for second Router B. 

There are two switches, Switch A for Router A and Switch B for Router B. I have connected both switches via LAN cable, so that If one network is down, I can access Internet via other one. 
The server is configured on the Router A. Now, the machines connected on Switch A is able to access the server. 

So, is there any way I can make the server available for those machines which are connected to Switch B (Router B).

---

### Post by SeijiSensei on 2012-02-02
You'd probably need to add static routes to the routers to handle traffic for the other IP subnet.

An easier solution may be simply to add another network adapter to the server and connect it to router B.  If you want traffic on Router B's subnet to see machines in the Router A subnet, you'll need to look into routing on the Linux box.

---

### Post by maverickaddicted on 2012-02-03
> **SeijiSensei said:**
> You'd probably need to add static routes to the routers to handle traffic for the other IP subnet.

An easier solution may be simply to add another network adapter to the server and connect it to router B.  If you want traffic on Router B's subnet to see machines in the Router A subnet, you'll need to look into routing on the Linux box.

My server has two Ethernet cards. I am really dump on networking. so can you explain a little more, considering me as a dump guy about adding static routes on the linux box. Please.

---

### Post by SeijiSensei on 2012-02-03
> **maverickaddicted said:**
> My server has two Ethernet cards. I am really dump on networking. so can you explain a little more, considering me as a dump guy about adding static routes on the linux box. Please.

I think you mean "dumb," and not understanding networking doesn't make you dump, I mean dumb.

Here's a good HOWTO: [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

You'll need two entries like the one given there, one for eth0 and one for eth1.  Only one interface should have a default gateway defined that points to the Internet, or you can have both of them point to their respective Internet routers, with one route assigned a higher "metric" than the other.  This is an advanced configuration; for now, just give eth0 a default gateway.

This will let both machines see the server, though machines connected to one network won't be able to send traffic to the other unless you enable IP forwarding in /etc/sysctl.conf.  Read the instructions in that file for details.

If traffic coming to eth1 needs to get out to the Internet, you'll need to use "masquerading" via the iptables command.  If eth0 points to the Internet, you'd run the command:

```
sudo iptables -t nat -o eth0 -A POSTROUTING -j MASQUERADE
```

---

### Post by maverickaddicted on 2012-02-06
> **SeijiSensei said:**
> I think you mean "dumb," and not understanding networking doesn't make you dump, I mean dumb.

Here's a good HOWTO: [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

You'll need two entries like the one given there, one for eth0 and one for eth1.  Only one interface should have a default gateway defined that points to the Internet, or you can have both of them point to their respective Internet routers, with one route assigned a higher "metric" than the other.  This is an advanced configuration; for now, just give eth0 a default gateway.

This will let both machines see the server, though machines connected to one network won't be able to send traffic to the other unless you enable IP forwarding in /etc/sysctl.conf.  Read the instructions in that file for details.

If traffic coming to eth1 needs to get out to the Internet, you'll need to use "masquerading" via the iptables command.  If eth0 points to the Internet, you'd run the command:

```
sudo iptables -t nat -o eth0 -A POSTROUTING -j MASQUERADE
```


First of all sorry for the typo error. I will do the configuration tomorrow, since today I am not in the office and will get back to you with the update.

---

### Post by maverickaddicted on 2012-02-08
> This will let both machines see the server, though machines connected to one network won't be able to send traffic to the other unless you enable IP forwarding in /etc/sysctl.conf. Read the instructions in that file for details.

If traffic coming to eth1 needs to get out to the Internet, you'll need to use "masquerading" via the iptables command. If eth0 points to the Internet, you'd run the command:

I didn't understand the above sentences.

My network interfaces file is -

```

root@openserver:/home# cat /etc/network/interfaces
auto lo eth0 eth1

iface lo inet loopback
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

iface eth1 inet static
        address 192.168.2.5
        netmask 255.255.255.0
        broadcast 192.168.2.255

```

Is the inteface file correctly configured. eth0 is used for connecting the Internet is the default connection, while I added eth1 manually as you said in the previous post. What changes should I made now in sysctl.conf file. 
And sysctl.conf file is


```

root@openserver:/home# cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
root@openserver:/home#

```

---

### Post by SeijiSensei on 2012-02-08
These.

```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1
```

As for masquerading, it's the process by which the server replaces the source address of each packet with its own external address.  "Private" addresses like those in 192.168.0.0/16 cannot be routed over the Internet, so the router has to "masquerade" as the machines behind it using its public IP address.

A simple masquerading rule is:

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

This tells the machine to masquerade all traffic that is passed through eth0.  However in your case, it looks like you're sending all your traffic through the router at 192.168.1.2, so it may be handling all the masquerading for you.  It may not handle the traffic on 192.168.2.0/24 correctly though.  If those machines cannot see the Internet, you'll need the masquerading rule on the Linux box so the traffic appears to the upstream router as if it's coming from 192.168.1.5.

---

### Post by maverickaddicted on 2012-02-08
I did what you have said -

1)uncommented the IPv4 line
2)added the masquerade rule

Now, I am able to ping 192.168.2.1 from the server. So does that mean that I will be able to see both network machines. Just for checking these are few configuration files -

```

root@openserver:/home# cat /etc/network/interfaces
auto lo eth0 eth1

iface lo inet loopback
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

iface eth1 inet static
        address 192.168.2.5
        netmask 255.255.255.0
        broadcast 192.168.2.255

```

```

root@openserver:/home# cat /etc/hosts
127.0.0.1       localhost       openserver.nexusone.local
127.0.0.1       openserver.nexusone.local       openserver
192.168.1.5     openserver.nexusone.local       openserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
```

root@openserver:/home# cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
root@openserver:/home#

```

Do I need to modify something else?

---

### Post by SeijiSensei on 2012-02-08
> **maverickaddicted said:**
> Now, I am able to ping 192.168.2.1 from the server. So does that mean that I will be able to see both network machines.

Do I need to modify something else?

Can you ping a machine (other than this server) in the 192.168.1.0/24 network from a machine in 192.168.2.0/24?  

Can machines in both networks browse the Internet?

---

### Post by maverickaddicted on 2012-02-09
Thank You very much for helping. It is working now. I am able to see both networks machines and also they are able to communicate with each other. I am facing one more problem with the server, so can you help me with this -

[http://ubuntuforums.org/showthread.php?t=1921591](http://ubuntuforums.org/showthread.php?t=1921591)

---

### Post by SeijiSensei on 2012-02-09
I answered this in [that thread]("http://ubuntuforums.org/showpost.php?p=11675623&postcount=3").

---

