---
title: "apt-cacher on headnode of a cluster"
date: 2010-06-23
forum: Server Platforms
---

### Post by abraxas334 on 2010-06-23
I have a problem with apt-cacher.(Apologies its on a debian system at the moment, but I will need to set it up on ubuntu as well, so I thought I'll ask about it straight away). Just to be clear I don't really know much about networking/ clusters etc. All i know is that i need to get apt-cacher working on a head-node of a 10 node cluster, to facilitate updates and installation of software.
I had managed to get it to work before, but then the proxy got changed and now i can't get it back to work and don't know why.
Here the content of the hosts file:
```

27.0.0.1       localhost
128.243.xx.xxx  headnode.domain        headnode

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
192.168.100.0 headnode.domain headnode

#Beowulf nodes
192.168.100.1 node01
192.168.100.2 node02
192.168.100.3 node03
192.168.100.4 node04
192.168.100.5 node05
192.168.100.6 node06
192.168.100.7 node07
192.168.100.8 node08
192.168.100.9 node09
192.168.100.10 node10



```
Then the content of the apt-cacher.conf file well the interesting bits, where I define the proxy etc.
```

# Apt-cacher can pass all its requests to an external http proxy like
# Squid, which could be very useful if you are using an ISP that blocks
# port 80 and requires all web traffic to go through its proxy. The
# format is 'hostname:port', eg: 'proxy.example.com:8080'.
#http_proxy=wwwcache.domainname.xx.uk:3128 (<- old proxy)
http_proxy=mainproxy.domainname.xx.uk:8080

# Use of an external proxy can be turned on or off with this flag.
# Value should be either 0 (off) or 1 (on).
use_proxy=1

# External http proxy sometimes need authentication to get full access. The
# format is 'username:password'.
#http_proxy_auth=proxyuser:proxypass

# Use of external proxy authentication can be turned on or off with this flag.
# Value should be either 0 (off) or 1 (on).
use_proxy_auth=0

# This sets the interface to use for the upstream connection.
# Specify an interface name, an IP address or a host name.
# If unset, the defaul route is used.
#interface=



```

and then I am pointing the apt source list to the apt-cacher info like this:
```

deb http://headnode.domainname.xx.uk/apt-cacher/ftp.uk.debian.org/debian stable main contrib
deb http://headnode.domainname.xx.uk/apt-cacher/security.debian.org  stable/updates main contrib


```
output of sudo apt-get update:
```


Hit http://headnode.domainname.xx.uk stable Release.gpg
Ign http://headnode.domainname.xx.uk stable/main Translation-en_GB
.
.
.
.
Reading package lists... Done



```
or if i want to install something like this
sudo apt-get install hexedit
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  hexedit
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 26.4kB of archives.
After this operation, 106kB of additional disk space will be used.
Get: 1 http://headnode.domainname.xx.uk stable/main hexedit 1.2.12-3 [26.4kB]


```
The Get will carry on but it will never be downloaded.
I think it has something to do with the DNS ?!? Any help would be greatly appreciated, because I don't know where else to look.
Thanks

---

### Post by clrg on 2010-06-23
1. Does nslookup [www.google.com](www.google.com) work? Then its not the DNS.
2. Look at /etc/apt/apt.conf, because that's the place where the proxy would be configured.

---

### Post by abraxas334 on 2010-06-24
Yes it was the /etc/apt/apt.conf that i forgot about. 
I managed to get it working fine....so I thought. I installed some stuff using apt-get install fine. (fai-client, server and quickstart packages)
There were some issues with dependencies for this so I manually installed this package, which i downloaded from the UK mirror
libapt-pkg-perl_0.1.24_i386.deb
but somehow now if I want to run apt-get update I get this:
```


Err http://hostname.domainname.xx.uk stable/updates/contrib Translation-en_GB
  Could not connect to hostname.domainname.xx.uk:3142 (128.243.xx.xxx). - connect (111: Connection refused)
Reading package lists... Done
W: Failed to fetch http://hostname.domainname.xx.uk/apt-cacher/ftp.uk.debian.org/debian/dists/stable/Release.gpg  Could not connect to hostname.domainname.ac.uk:3142 (128.243.xx.xxx). - connect (111: Connection refused)



```
Any ideas what is wrong here?
Thanks

---

### Post by clrg on 2010-06-24
Looks like your firewall doesn't want you to communicate with the outside world. Check with the security dpt of your company.

---

### Post by abraxas334 on 2010-06-24
Well I am sitting behind a proxy, but I had it all working before and all i did was to install a few programs could they have changed some config files? Might it be a confusion between ip4 and ip6 addresses?

---

### Post by clrg on 2010-06-25
Well, if you configured the proxy right, then it's the proxy refusing the connection. Check its configuration.

If you tried without the proxy, then your firewall is the problem (only allowing connections through the proxy).

---

