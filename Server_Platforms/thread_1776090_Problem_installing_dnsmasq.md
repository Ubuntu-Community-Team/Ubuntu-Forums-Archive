---
title: "Problem installing dnsmasq"
date: 2011-06-05
forum: Server Platforms
---

### Post by FrenziedEngi on 2011-06-05
I am having a problem installing dnsmasq (see below). What am I doing wrong? How can I get this to properly install?

```
sudo apt-get install dnsmasq
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dnsmasq: Depends: dnsmasq-base (>= 2.52-1ubuntu0.1) but 2.52-1 is to be installed
E: Broken packages
```

It appears that dnsmasq is already installed, but there is no entry in /etc/init.d to start/stop, and there is no default/starter configuration file at /etc/dnsmasq.conf

```
dnsmasq --version
Dnsmasq version 2.52  Copyright (c) 2000-2010 Simon Kelley
Compile time options IPv6 GNU-getopt DBus I18N DHCP TFTP
```

_**What I have tried:**_
[LIST]
[*]Manually install dnsmasq-base
[*]Force install dnsmasq
[*]apt-get update / apt-get upgrade
[/LIST]

**_Background info:_**
**Install Info:**
```
uname -a
Linux farmer1 2.6.32-306-ec2 #11-Ubuntu SMP Tue Jun 1 14:35:25 UTC 2010 x86_64 GNU/Linux
```

**Sources.list**
```
sudo cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu lucid main
deb http://security.ubuntu.com/ubuntu lucid-security main

deb http://archive.canonical.com/ lucid partner
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

deb http://badgerports.org lucid main
```

**Ubuntu Version**
```
cat /etc/issue
Ubuntu 10.04.1 LTS \n \l
```

**Installed dns packages**
```
dpkg --get-selections | grep dns
libavahi-compat-libdnssd1                       install
libdns64                                        install
libnss-mdns                                     install
```

---

### Post by brettg on 2011-06-05
You could try purging dnsmasq

apt-get purge dnsmasq

Then manually make sure all references are removed from /etc

---

### Post by FrenziedEngi on 2011-06-05
> **brettg said:**
> You could try purging dnsmasq

apt-get purge dnsmasq

Then manually make sure all references are removed from /etc

Does not look like it is even recognized as being installed... :confused:

```
apt-get purge dnsmasq
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package dnsmasq is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by brettg on 2011-06-05
try this;

apt-get purge dnsmasq-base

and

apt-get install -f

this will fix any broken packages/dependencies in your system

---

### Post by FrenziedEngi on 2011-06-05
> **brettg said:**
> try this;

apt-get purge dnsmasq-base

and

apt-get install -f

this will fix any broken packages/dependencies in your system

Update (see below):
```
sudo apt-get purge dnsmasq-base
Reading package lists... Done
Building dependency tree
Reading state information... Done
**Package dnsmasq-base is not installed, so not removed**
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by brettg on 2011-06-06
The problem is that the version of dnmasq-base that is being installed is newer than the dnsmasq package itself. This is most likely because the repositories are in the middle of being changed and the correct packages haven't been fully updated.

It could be just waiting a day or so and then doing an apt-get update again will see the problem fixed.

Alternately if you are in a hurry you could switch to another repository and try that out;

sed -i s/us.archive/archive/g /etc/apt/sources.list

This will change your system to use the primary archive "archive.ubuntu.com" instead of the US local archive.

You will need to do an apt-get update after changing your sources.list file of course.

---

### Post by FrenziedEngi on 2011-06-06
> **brettg said:**
> The problem is that the version of dnmasq-base that is being installed is newer than the dnsmasq package itself. This is most likely because the repositories are in the middle of being changed and the correct packages haven't been fully updated.

It could be just waiting a day or so and then doing an apt-get update again will see the problem fixed.

Alternately if you are in a hurry you could switch to another repository and try that out;

sed -i s/us.archive/archive/g /etc/apt/sources.list

This will change your system to use the primary archive "archive.ubuntu.com" instead of the US local archive.

You will need to do an apt-get update after changing your sources.list file of course.

I took this advice and changed over to the global servers in sources.list. Did apt-get update and then tried to install again. Same error as before:

```
The following packages have unmet dependencies:
  dnsmasq: Depends: dnsmasq-base (>= 2.52-1ubuntu0.1) but it is not going to be installed
E: Broken packages
```

---

### Post by redmk2 on 2011-06-06
> **FrenziedEngi said:**
> I took this advice and changed over to the global servers in sources.list. Did apt-get update and then tried to install again. Same error as before:

```
The following packages have unmet dependencies:
  dnsmasq: Depends: dnsmasq-base (>= 2.52-1ubuntu0.1) but it is not going to be installed
E: Broken packages
```

What is the output of ```
sudo apt-get -s install dnsmasq
```

What version of Ubuntu are you running?

---

### Post by FrenziedEngi on 2011-06-06
> **redmk2 said:**
> What is the output of ```
sudo apt-get -s install dnsmasq
```

What version of Ubuntu are you running?

Here is the output (looks familiar...).

```
sudo apt-get install -s -V dnsmasq
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dnsmasq: Depends: dnsmasq-base (>= 2.52-1ubuntu0.1) but it is not going to be installed
E: Broken packages
```

Please see full version information in my original post at start of thread.

---

### Post by collisionystm on 2011-06-06
May I ask why you are installing dnsmasq instead of bind9?

---

### Post by FrenziedEngi on 2011-06-06
> **collisionystm said:**
> May I ask why you are installing dnsmasq instead of bind9?

I don't have much experience in the way of server administration. I have been working on a small project to create a VPN server (at a remote location) so that all web traffic from my house (which is out over an unsecured wireless network) can be client to the VPN server & secured.

I have been able to establish the VPN client/server connection, but this last 5% with getting dnsmasq up and running on the server has been killing me. I was loosely following the advice given in the article here: [http://library.linode.com/networking/openvpn/ubuntu-10.04-lucid#sph_tunnel-all-connections-through-the-vpn](http://library.linode.com/networking/openvpn/ubuntu-10.04-lucid#sph_tunnel-all-connections-through-the-vpn)

I am open to suggestions. If there is a tutorial you can point me to in order to get this last bit setup and configured, please do. I am not "set" on dnsmasq.

---

### Post by redmk2 on 2011-06-06
> **FrenziedEngi said:**
> Here is the output (looks familiar...).

```
sudo apt-get install -s -V dnsmasq
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dnsmasq: Depends: dnsmasq-base (>= 2.52-1ubuntu0.1) but it is not going to be installed
E: Broken packages
```

Please see full version information in my original post at start of thread.

I saw the info at the beginning.  Just confirming that you have not upgraded the version. The problem is definitely a package problem at your end.  I am running 10.04 LTS myself, but the latest version ```
Ubuntu 10.04.**[COLOR="Red"][SIZE="3"]2[/SIZE][/COLOR]** LTS \n \l

```instead of yours```
Ubuntu 10.04.[SIZE="4"][COLOR="Blue"]**1**[/COLOR][/SIZE] LTS \n \l

```

When I use ```
sudo apt-get -s install dnsmasq
``` I get this```
sudo apt-get -s install dnsmasq
[sudo] password for red: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  resolvconf
The following NEW packages will be installed:
  dnsmasq
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Inst dnsmasq (2.52-1ubuntu0.1 Ubuntu:10.04/lucid-updates)
Conf dnsmasq (2.52-1ubuntu0.1 Ubuntu:10.04/lucid-updates)

```

As it should be.

Maybe a dist upgrade?

---

### Post by collisionystm on 2011-06-06
Do you know your ISP's DNS servers at your remote location? I assume at the remote is where you are installing DNS.

```
sudo apt-get purge dnsmasq
``````
sudo apt-get install bind9
``````

nano /etc/bind/named.conf.options
```Uncomment forwarders
  >  [...]          forwarders {              1.2.3.4;              5.6.7.8;         };          [...][FONT=monospace]Done. Now all your DNS queries to the remote location will forward to the ISP DNS on its network connection. You can even use google public DNS if you wish to make it even more secure. 

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

And make sure you get ride of that dnsmasq. Having multiple services listening on the DNS port will cause issues. Just do a service --status-all and see if you see dnsmasq running. if you do, do a 

ps aux | grep dnsmasq

kill -9 PIDofDNSmasq

If you wish to go more in depth with bind9 and add hostname's etc.... see this, [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

but other than that, the setup I gave you will work for your purposes. 
[/FONT]

---

### Post by FrenziedEngi on 2011-06-06
Thanks for the help, collisionystm!

I was able to get started with the links you provided.
I still had a problem with the bind9 configuration (lookups were getting denied).

So in /etc/bind/named.conf.options I added this section:
```
        allow-query {
                127.0.0.1/32;
                10.8.0.0/24;
        };
```

Now when it starts up I see this in the logs:
```
Jun  6 22:17:03 hostname named[1263]: listening on IPv6 interfaces, port 53
Jun  6 22:17:03 hostname named[1263]: listening on IPv4 interface lo, 127.0.0.1#53
Jun  6 22:17:03 hostname named[1263]: listening on IPv4 interface eth0, MYPUBLICIP#53
Jun  6 22:17:03 hostname named[1263]: listening on IPv4 interface tun0, 10.8.0.1#53
```

Not sure why it is listening on MYPUBLICIP. But my firewall does not have that port open anyway.

However, now my VPN connection (on 10.8 subnet) can now use the DNS for lookups and traffic is being tunneled!:guitar:

---

### Post by collisionystm on 2011-06-06
> **FrenziedEngi said:**
> Thanks for the help, collisionystm!

I was able to get started with the links you provided.
I still had a problem with the bind9 configuration (lookups were getting denied).

So in /etc/bind/named.conf.options I added this section:
```
        allow-query {
                127.0.0.1/32;
                10.8.0.0/24;
        };
```

Now when it starts up I see this in the logs:
```
Jun  6 22:17:03 hostname named[1263]: listening on IPv6 interfaces, port 53
Jun  6 22:17:03 hostname named[1263]: listening on IPv4 interface lo, 127.0.0.1#53
Jun  6 22:17:03 hostname named[1263]: listening on IPv4 interface eth0, MYPUBLICIP#53
Jun  6 22:17:03 hostname named[1263]: listening on IPv4 interface tun0, 10.8.0.1#53
```

Not sure why it is listening on MYPUBLICIP. But my firewall does not have that port open anyway.

However, now my VPN connection (on 10.8 subnet) can now use the DNS for lookups and traffic is being tunneled!:guitar:


Excellent! I am glad you were able to get going!

---

