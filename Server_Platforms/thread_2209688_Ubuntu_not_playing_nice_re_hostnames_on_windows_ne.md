---
title: "Ubuntu not playing nice re hostnames on windows network"
date: 2014-03-06
forum: Server Platforms
---

### Post by remush on 2014-03-06
Hi all,

I'd like to setup a Ubuntu Server 12.04 based system to provide:
 - SSH Access
 - File Server
 - Backup to offsite drive

I'm testing the file server using Virtualbox.

SSH access is working fine, but only via IP address.

I wanted the share management to be as easy as possible, so have installed lxde and system-config-samba
Samba shares are setup and working fine using the gui tools, and I'm not having any trouble with that.

Our network runs of an ADSL Modem, that feeds a 1Gb switch. The modem acts as the rounter/dns/DHCP server by default and required no setup
All computers on the network have a manually configured static ip address.

Ubuntu system is able to ping all other computers on my LAN via IP Address, but not hostname

All computers on the network can ping the ubuntu server via ip address but not by hostname

It may be worth noting that I have setup a few microcore linux computers to act as file servers on our network, and they have no problem with hostnames by default. The microcore linux servers have static ip address's.

I've found a few forum threads advising that I have to install winbind, I did so and discovered that it was already installed.
Other forums suggesting placing wins before dns in the /etc/nsswitch.conf file, I did this but the problem persist's
Other forums suggested placing wins code into the /etc/samba/smb.conf file, I did this as suggested but the problem persists.

I'm hoping the problem is fairly straight forward.

I've set a static ip address to the ubuntu server.

Here are my /etc/network/interfaces settings.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.1.1.140
netmask 255.255.255.0
gateway 10.1.1.1
network 10.1.1.0
broadcast 10.1.1.255
dns-nameservers 10.1.1.1

I may have made an error when making changes to try and fix the hostname, so have restored the system to the following state.
- Fully udpated, upgraded
- lxde installed
- system-config-samba installed
- one basic share setup and tested via ip address
- ssh installed, and tested via ip address
All changes that were made to alter hostname functionality have been removed.


Thanks in advance for all comments and suggestions.

---

### Post by TheFu on 2014-03-07
Windows uses a different protocol for system discovery than every other network in the universe.  Linux follows the IP standards with DNS and /etc/hosts.

What does this mean?  You have a few choices.
a) setup a proper DNS server that understands the hostname to IP and reverse mapping.
b) modify the /etc/hosts file (and equiv on Windows) so that all hostnames to IPs are known.
c) make the Linux machine broadcast like it is a Windows machine in the Windows way. I think that is called WINS.  There is a setting to use WINS from the Linux side somewhere - perhaps the /etc/nsswitch.conf file?

I use "b."  MS-Windows machines are 2nd class on my network, so they are forced to speak IP standards, not invent their own. ;)

BTW, if you have ssh working, then you can use sftp from any client to access the files securely. With ssh-keys, it is very convenient AND more secure.  Just have every client push their public ssh-key to the server using **ssh-copy-id**. Very easy. No need for samba at all. WinSCP or Filezilla are great sftp clients for the "other OS". sftp is built-into pretty much any file browser on Linux and the CLI version works just like FTP, but it is secure.

If you need to mirror directories, **rsync** will work over ssh by default as will most current-gen backup utilities for Linux.

---

### Post by bab1 on 2014-03-07
> **remush said:**
> Hi all,

I'd like to setup a Ubuntu Server 12.04 based system to provide:
 - SSH Access
 - File Server
 - Backup to offsite drive

I'm testing the file server using Virtualbox.

SSH access is working fine, but only via IP address.

I wanted the share management to be as easy as possible, so have installed lxde and system-config-samba
Samba shares are setup and working fine using the gui tools, and I'm not having any trouble with that.

Our network runs of an ADSL Modem, that feeds a 1Gb switch. The modem acts as the rounter/dns/DHCP server by default and required no setup
All computers on the network have a manually configured static ip address.

Ubuntu system is able to ping all other computers on my LAN via IP Address, but not hostname

All computers on the network can ping the ubuntu server via ip address but not by hostname

It may be worth noting that I have setup a few microcore linux computers to act as file servers on our network, and they have no problem with hostnames by default. The microcore linux servers have static ip address's.

I've found a few forum threads advising that I have to install winbind, I did so and discovered that it was already installed.
Other forums suggesting placing wins before dns in the /etc/nsswitch.conf file, I did this but the problem persist's
Other forums suggested placing wins code into the /etc/samba/smb.conf file, I did this as suggested but the problem persists.

I'm hoping the problem is fairly straight forward.

I've set a static ip address to the ubuntu server.

Here are my /etc/network/interfaces settings.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.1.1.140
netmask 255.255.255.0
gateway 10.1.1.1
network 10.1.1.0
broadcast 10.1.1.255
dns-nameservers 10.1.1.1

I may have made an error when making changes to try and fix the hostname, so have restored the system to the following state.
- Fully udpated, upgraded
- lxde installed
- system-config-samba installed
- one basic share setup and tested via ip address
- ssh installed, and tested via ip address
All changes that were made to alter hostname functionality have been removed.


Thanks in advance for all comments and suggestions.
My guess is that you do not have LAN DNS configured.  if you don't have many hosts (computers) to manage you can map the IP address to hostname in the /etc/hosts file.  In the end Samba converts DNS/host names to NETBIOS names.  Another option is to just declare the NETBIOS name explicitly in the smb.conf file like this (in the [global] section)```
netbios name = <some_name>
```...where <some_name> is a name you select that is less than 15 characters).

---

### Post by bab1 on 2014-03-07
> **TheFu said:**
> Windows uses a different protocol for system discovery than every other network in the universe.  Linux follows the IP standards with DNS and /etc/hosts.

The TCP/IP protocol has no DNS standard.  DNS and NETBIOS are naming services that map TCP/IP addressing to human usable naming. 

> 
...
c) make the Linux machine broadcast like it is a Windows machine in the Windows way. I think that is called WINS.  There is a setting to use WINS from the Linux side somewhere - perhaps the /etc/nsswitch.conf file?

WINS is not a broadcast method.  It's a dynamic database for NETBIOS names.  It's not needed in a single segment (network) LAN.  The /etc/nsswitch.conf file should not be changed from it's default.  Changing this can cause lengthy delays when looking for none existent name service databases. 
> 

I use "b."  MS-Windows machines are 2nd class on my network, so they are forced to speak IP standards, not invent their own. ;)
Windows has always used IP addressing.  It does use a *different naming scheme* that was created before hostnames and DNS was created.  In fact there were NETBIOS names used with Novel IPX/SPX.

---

### Post by Habitual on 2014-03-07
> **TheFu said:**
> 
b) modify the /etc/hosts file (and equiv on Windows) so that all hostnames to IPs are known.
edit C:\Windows\System32\drivers\etc\hosts and add an entry for the remote host.

---

### Post by TheFu on 2014-03-07
> **bab1 said:**
> The TCP/IP protocol has no DNS standard.  DNS and NETBIOS are naming services that map TCP/IP addressing to human usable naming. 

WINS is not a broadcast method.  It's a dynamic database for NETBIOS names.  It's not needed in a single segment (network) LAN.  The /etc/nsswitch.conf file should not be changed from it's default.  Changing this can cause lengthy delays when looking for none existent name service databases. 

Windows has always used IP addressing.  It does use a *different naming scheme* that was created before hostnames and DNS was created.  In fact there were NETBIOS names used with Novel IPX/SPX.

@bab1, on MS-Windows networking, you area almost always correct. We all make mistakes - I do daily.

[https://tools.ietf.org/html/rfc883](https://tools.ietf.org/html/rfc883) - DNS in 1983.
[https://en.wikipedia.org/wiki/Windows_3.1x](https://en.wikipedia.org/wiki/Windows_3.1x) - says that IP was added to Windows in 1994. 

I stand corrected on the WINS mistake and that Microsoft didn't invent NetBEUI which many small businesses used into the mid-1990s. If you only had 1 LAN segment, routing wasn't necessary. NetBEUI fit that need perfectly, even with a few warts. Every protocol has warts. ;)

So - how is the OP doing on a solution?

---

### Post by bab1 on 2014-03-07
> **TheFu said:**
> @bab1, on MS-Windows networking, you area almost always correct. We all make mistakes - I do daily.

[https://tools.ietf.org/html/rfc883](https://tools.ietf.org/html/rfc883) - DNS in 1983.
[https://en.wikipedia.org/wiki/Windows_3.1x](https://en.wikipedia.org/wiki/Windows_3.1x) - says that IP was added to Windows in 1994. 

I stand corrected on the WINS mistake and that Microsoft didn't invent NetBEUI which many small businesses used into the mid-1990s. If you only had 1 LAN segment, routing wasn't necessary. NetBEUI fit that need perfectly, even with a few warts. Every protocol has warts. ;)


We all make mistakes, that is for sure. However, you can always check your facts before you post to the thread.  For example:```
 RFC 882 proposes a *domain name system  * -- DOMAIN NAMES - CONCEPTS and FACILITIES in [COLOR="#008000"]**1983**[/COLOR].
```  The RFC that describes hostnames and DNS is ```
RFC 1035 -- DOMAIN NAMES - IMPLEMENTATION AND SPECIFICATION.  [COLOR="#0000FF"]This was in November 1987[/COLOR]
```.  The RFC that describes NETBIOS over TCP (NBT) is ```
RFC 1002 -- PROTOCOL STANDARD FOR A NetBIOS SERVICE ON A TCP/UDP TRANSPORT: DETAILED SPECIFICATIONS [COLOR="#FF0000"]just 8 months earlier in March of 1987[/COLOR].
```

These are indeed minor details.  Sometimes the details are important.  Sometimes not so much.  FYI: NetBUI is not NetBIOS.  NetBIOS over TCP is routable, but certainly not advisable over the Internet.  NETBIOS (NBT) using WINS works across networks.  ;-)

You and I have talked before about stating opinions as if they are facts.  The OP can't tell if your point is a guess, opinion or the raw facts.  My feeling is that  the information is easily available to verify what is stated is correct and we should do that.  Certainly opinions are always welcomed when it's obvious that this is what they are.  We all have opinions.

I'm certainly no Microsoft apologist.  I haven't used their products in years.  But there is no reason to demean any protocol, product of company when diagnosing a specific problem. >   
 So - how is the OP doing on a solution?
I know no more than you do.

---

### Post by remush on 2014-03-09
HI guys,

Thanks for the advice. I had a look at the smb.conf file and it did not include a "netbios name = something" line.

I have added 

   netbios name = afs

to my smb.conf file, and its working from a terminal on the server using

   smbclient //afs/test -U%

However its still not working from a windows machine using

   \\afs\test

Windows machines are only able to connect using ip address.

  \\10.1.1.140\test

I"m sure its a simple matter of finding the right ubuntu way of doing it, as I've got things working fine on a microcore linux samba server.

---

### Post by remush on 2014-03-09
I decided to try a "ping afs" command from the ubuntu server

it started pinging 127.0.01

So I checked /etc/hosts and I had

127.0.0.1       localhost
127.0.1.1     afs
10.1.1.140      afs

So I removed the line

127.0.0.1      afs

I rebooted the server, however its still not working.

I decided that I might try manually editing my smb.conf file to keep it simple, and now have the following.
```
[global]
workgroup = workgroup
netbios name = afs

name resolve order = bcast lmhosts host wins

log file = /etc/samba/smb.log.%m
log level = 2
max log size = 50
debug timestamp = yes

load printers = no
show add printer wizard = no
printcap name = /dev/null
disable spoolss = yes

[test]
comment = test share
path = /samba.shares/test
read only = no
guest ok = yes
browsable = yes

```

However the only way to access the ubuntu server is via ip address, hostname is still not working.

---

### Post by bab1 on 2014-03-10
> **remush said:**
> I decided to try a "ping afs" command from the ubuntu server

it started pinging 127.0.01

So I checked /etc/hosts and I had

127.0.0.1       localhost
127.0.1.1     afs
10.1.1.140      afs

So I removed the line

127.0.0.1      afs

I rebooted the server, however its still not working.

I decided that I might try manually editing my smb.conf file to keep it simple, and now have the following.
```
[global]
workgroup = workgroup
netbios name = afs

name resolve order = bcast lmhosts host wins

log file = /etc/samba/smb.log.%m
log level = 2
max log size = 50
debug timestamp = yes

load printers = no
show add printer wizard = no
printcap name = /dev/null
disable spoolss = yes

[test]
comment = test share
path = /samba.shares/test
read only = no
guest ok = yes
browsable = yes

```

However the only way to access the ubuntu server is via ip address, hostname is still not working.
The Samba NETBIOS name is not the same name as the DNS hostname.  This means TCP/IP tools that rely on DNS such as PING won't work with a NETBIOS name.  In short PING afs does not use the same name space as browsing for the Samba server //afs.

But you have other problems that we should diagnose.  Are the Windows machines also VM's?  What is the hostname of the host with the address 10.1.1.140?  Post the output from its terminal of these commands```
ifconfig -a

hostname

```

What is the IP address of one of the Windows machines?  What is it's hostname?  Do you have PuTTY installed on that Windows host?  Can you ssh by IP address to the Samba server //afs?

If the Windows machines are in different IP subnet you will not be able to see the Samba server //afs by NETBIOS with out a WINS server.  At the present time it is set up to use bcast.  This limits the viability to the subnet it is on.

Are the "microcore linux servers" real machines or virtual?  What is different about them (IP addressing or nameservices or smb.conf)?

---

### Post by remush on 2014-03-10
Hi bab1


> Are the Windows machines also VM's?
 No, i'm testing from windows xp and windows 7 installed onto actual physical computers.

> What is the hostname of the host with the address 10.1.1.140?
 hostname of computer with ip address 10.1.1.140 is afs, this is the virtual machine I'm testing with.


It may be worth mentioning a few more details about VirtualBox.
- VirtualBox version : 4.3.8 r92456
- Virtual Machine Network is set to : Bridged Adapter (This network mode has allowed my virtual machines to have access to and from my lan and the internet in the past)


```
user@afs:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:94:7b:8f
          inet addr:10.1.1.140  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe94:7b8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22254 (22.2 KB)  TX bytes:11240 (11.2 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2700 (2.7 KB)  TX bytes:2700 (2.7 KB)

user@afs:~$ hostname
afs

```


> What is the IP address of one of the Windows machines? What is it's hostname?
Ip address 10.1.1.123 , hostname of this machine is steve. This machine is where the virtual machine is installed and running from.

> Do you have PuTTY installed on that Windows host?
 Yes putty is installed onto that windows host

> Can you ssh by IP address to the Samba server //afs?
 Yes I can ssh with putty to the vm's ip address but not its hostname

> If the Windows machines are in different IP subnet you will not be able to see the Samba server //afs by NETBIOS with out a WINS server. At the present time it is set up to use bcast. This limits the viability to the subnet it is on.
 Ok, this one got me thinking and I had a look at my Windows 7 computer's TCP/IPv4 settings, here they are.
```
IP address: 10.1.1.123
Subnet mask: 255.0.0.0
default gateway: 10.1.1.1
preferred DNS server: 10.1.1.1

```

So I then had a look at the /etc/network/interfaces settings on my virtual machine hostname afs to compare, here it is.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.1.1.140
netmask 255.255.255.0
gateway 10.1.1.1
network 10.1.1.0
broadcast 10.1.1.255
dns-nameservers 10.1.1.1
```


I then had a look at the network settings for one of my microcore linux servers. (static network settings are run from a sh file each boot up, here's the file)
```
ifconfig eth0 10.1.1.150 netmask 255.0.0.0 broadcast 10.255.255.255 up
route add default gw 10.1.1.1
echo nameserver 10.1.1.1 > /etc/resolv.conf
```


I can see some differences here
Windows subnet mask : 255.0.0.0
Microcore linux netmask : 255.0.0.0
Linux VM hostname afs netmask : 255.255.255.0


So... as you say
> If the Windows machines are in different IP subnet you will not be able to see the Samba server
I changed the Linux VM hostname afs netmask from 255.255.255.0 to 255.0.0.0, and rebooted the machine. I left it alone for 5 minutes and can now ping the VM via hostname afs, and I can access via ssh with hostname afs, AND I can access shares via hostname \\afs

Thanks for your thorough analytically approach bab1.
I was wondering if you could explain to me the correct way to use these settings, our network is 10.1.1.x where x can be any number between 1 and 255. However I'm not a network guru, and could use a bit of mentoring.

Thanks again.

---

### Post by bab1 on 2014-03-11
> **remush said:**
> Hi bab1
... i'm testing from windows xp and windows 7 installed onto actual physical computers.
[The]hostname of computer with ip address 10.1.1.140 is afs, this is the virtual machine I'm testing with.

It may be worth mentioning a few more details about VirtualBox.
- VirtualBox version : 4.3.8 r92456
- Virtual Machine Network is set to : Bridged Adapter (This network mode has allowed my virtual machines to have access to and from my lan and the internet in the past)

{The host machine (hypervisor) has] Ip address 10.1.1.123 , hostname of this machine is steve. This machine is where the virtual machine is installed and running from.

Yes putty is installed onto that windows host  Yes I can ssh with putty to the vm's ip address but not its hostname


..[I] had a look at the network settings for one of my microcore linux servers. (static network settings are run from a sh file each boot up, here's the file)
```
ifconfig eth0 10.1.1.150 netmask 255.0.0.0 broadcast 10.255.255.255 up
route add default gw 10.1.1.1
echo nameserver 10.1.1.1 > /etc/resolv.conf
```


I can see some differences here
Windows subnet mask : 255.0.0.0
Microcore linux netmask : 255.0.0.0
Linux VM hostname afs netmask : 255.255.255.0

I changed the Linux VM hostname afs netmask from 255.255.255.0 to 255.0.0.0, and rebooted the machine. I left it alone for 5 minutes and can now ping the VM via hostname afs, and I can access via ssh with hostname afs, AND I can access shares via hostname \\afs

Thanks for your thorough analytically approach bab1.
I was wondering if you could explain to me the correct way to use these settings, our network is 10.1.1.x where x can be any number between 1 and 255. However I'm not a network guru, and could use a bit of mentoring.

Thanks again.
I think you got to where it all works but not in a normal way.

The subnet mask describes the number of bits used to identify the network.  For example the IP address 10.1.1.140 does not fully describe all of it's attributes.  

Is the subnet mask 8 bits (255.0.0.0) or 24 bits (255.255.255.0)?  You would use these: 10.1.1.140 /8 (for 255.0.0.0) or 10.1.1.140 /24 (for 255.255.255.0).  Why all of this?  The subnet mask identifies the [COLOR="#0000FF"]network[/COLOR]+[COLOR="#FF0000"]host[/COLOR] numbers.  Using the /8  the ***network*** identified as the first 8 contiguous bits (shown in blue) and the rest is the host number (in red)```

decimal
[COLOR="#0000FF"]10[/COLOR].[COLOR="#FF0000"]1.1.140[/COLOR]
binary
[COLOR="#0000FF"]00001010[/COLOR].[COLOR="#FF0000"]00000001.00000001.10001100[/COLOR]
with a subnet mask of 
[COLOR="#0000FF"]11111111[/COLOR].[COLOR="#FF0000"]00000000.00000000.[/COLOR][COLOR="#FF0000"]00000000[/COLOR]

```

If we use /24 we are using the first 24 bits we get this
```

decimal
[COLOR="#0000FF"]10[/COLOR].[COLOR="#FF0000"]1.1.140[/COLOR]
binary
[COLOR="#0000FF"]00001010.00000001.00000001.[/COLOR][COLOR="#FF0000"]10001100[/COLOR]
with a subnet names of 
[COLOR="#0000FF"]11111111.11111111.11111111.[/COLOR][COLOR="#FF0000"]00000000[/COLOR]

```

As you can see the /8 network has more numbers in it.  More importantly in your case, The /24 network is inside of the /8 network.  It is a subset of the larger network.

NETBIOS names use broadcasts to find names.  The broadcast number is always the ***last number in the network***.  This means that the /24 network is limited to the last octet of numbers 0-255 where as the /8 network spans the last 3 octets with the range of 16,777,216 numbers (10.0.0.1 to 10.255.255.255).  You just added all the machines into the same broadcast domain.  In theory you could have added all the machines into the /24 network (255.255.255.0 mask).

What this also tells me is that broadcasts don't traverse bridged networks so you had to put everything in the same network.  If it works for you then I would leave it.  If you have weirdness down the road it may be due to this configuration.

What would you have done if the 2 networks were: 10.1.1.0 /8 and 192.168.0.0 /24 ?  Your subnet mask trick would not have worked.

---

### Post by remush on 2014-03-12
HI bab1,

thanks for taking the time to help me with the solution, and the network theory education.

Its a bit over my head, but very much appreciated, i'll go looking for a "for dummy's tutorial online"

Thanks again.

By they way, how to I mark this as solved ?

---

### Post by Iowan on 2014-03-12
> **remush said:**
> By they way, how to I mark this as solved ?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

