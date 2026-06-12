---
title: "FQDN not working"
date: 2011-09-23
forum: Server Platforms
---

### Post by maverickaddicted on 2011-09-23
Hello,

I have installed Ubuntu 11.04 server edition. I have connected several windows and ubuntu machine not it.
FQDN of my server is openserver
However, whenever I try to open it from the browser (Chrome or Firefox) using this [http://openserver](http://openserver) or [http://openserver:80](http://openserver:80).
It gets redirected to Google search results. However, it works perfectly using the IP.
Please help me.

---

### Post by volkswagner on 2011-09-23
In order to use hostnames, you need an entry in each clients hosts file to resolve the IP address, or you need a functioning, local DNS server.

Here are a few related threads.

[http://ubuntuforums.org/showthread.php?t=1848776](http://ubuntuforums.org/showthread.php?t=1848776)
[http://ubuntuforums.org/showthread.php?p=10685641](http://ubuntuforums.org/showthread.php?p=10685641)
[http://ubuntuforums.org/showthread.php?t=1731236](http://ubuntuforums.org/showthread.php?t=1731236)

My personal favorite is to use the router as the DNS server, and have any necessary static ip's get an address via a reserved DHCP from the router.  This tends to help with hostname resolution.

---

### Post by maverickaddicted on 2011-10-09
Actually the problem is that it works on few machines, but not on all machines. For few machines, if I type openserver, it displays the default index.html file. However, for some machines, its get redirected to Google search results. 
Is it really a DNS issue?

---

### Post by redmk2 on 2011-10-09
> **maverickaddicted said:**
> Actually the problem is that it works on few machines, but not on all machines. For few machines, if I type openserver, it displays the default index.html file. However, for some machines, its get redirected to Google search results. 
Is it really a DNS issue?

Yes, this is an issue of mapping the host name to the IP address on the machines that fail.  A DNS server does the mapping for the network in a central place (the DNS server), while using the /etc/hosts file configures each machine to resolve the other machines name/IP mapping.

For a small network that doesn't change IP addressing, the mapping the /etc/hosts files work fine.

---

### Post by maverickaddicted on 2011-10-13
Does this mean that I have to reconfigure the bind9.

---

### Post by volkswagner on 2011-10-13
Are  you currently running bind9?

Did you read my first post?

---

### Post by Jonathan L on 2011-10-13
> **maverickaddicted said:**
> Actually the problem is that it works on few machines, but not on all machines. For few machines, if I type openserver, it displays the default index.html file. However, for some machines, its get redirected to Google search results. 
Is it really a DNS issue?

Hi Maverick

Are you quite sure that "openserver" is your fully qualified domain name?  It looks like just a hostname, and your full name would be something like openserver.example.com.  [http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)

If it's a hostname, then the issue is one of domain search paths, and you need example.com in the domain search path; this is usually set up in the DHCP server, and ends up in /etc/resolv.conf, and ends up either as "domain example.com." or "search".  This tells the browsing computer to add domains on the end, if there are no dots in the domain.    Read especially the parts about short names in [http://manpages.ubuntu.com/manpages/lucid/man5/resolver.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/resolver.5.html)  Windows and Macintosh have similar mechanisms and I understand they use the DHCP settings properly.

Finally, the browser can decide to do a Google or Wikipedia or Bing or whatever search if it feels like it.  Configuration would be entirely dependent on the browser.

So if your DNS server is returning correct results the config is on the clients, probably from the DHCP server.  As volkswagner says though, you can definitely fix things to use short names in /etc/hosts, but if you've gone to the trouble to run a local DNS server then it's better to fix it in one place.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by maverickaddicted on 2011-10-13
> **volkswagner said:**
> Are  you currently running bind9?

Did you read my first post?

Yes, I read your first post, I also followed it, but it was not working.

---

### Post by maverickaddicted on 2011-10-13
> **Jonathan L said:**
> Hi Maverick

Are you quite sure that "openserver" is your fully qualified domain name?  It looks like just a hostname, and your full name would be something like openserver.example.com.  [http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)

If it's a hostname, then the issue is one of domain search paths, and you need example.com in the domain search path; this is usually set up in the DHCP server, and ends up in /etc/resolv.conf, and ends up either as "domain example.com." or "search".  This tells the browsing computer to add domains on the end, if there are no dots in the domain.    Read especially the parts about short names in [http://manpages.ubuntu.com/manpages/lucid/man5/resolver.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/resolver.5.html)  Windows and Macintosh have similar mechanisms and I understand they use the DHCP settings properly.

Finally, the browser can decide to do a Google or Wikipedia or Bing or whatever search if it feels like it.  Configuration would be entirely dependent on the browser.

So if your DNS server is returning correct results the config is on the clients, probably from the DHCP server.  As volkswagner says though, you can definitely fix things to use short names in /etc/hosts, but if you've gone to the trouble to run a local DNS server then it's better to fix it in one place.

Hope that helps.

Kind regards,
Jonathan.


Yes you are right "openserver" is a hostname. FQDN is "openserver.nexusone.local". However, I have not configured it as DHCP server, it is just a web server. 

My /etc/hosts file is - 

127.0.0.1       localhost mail.nexusone.local
#192.168.1.4    openserver.nexusone.com openserver
192.168.1.5     openserver.nexusone.local openserver 
192.168.1.5     mail.nexusone.local
192.168.1.5     openserver
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by Jonathan L on 2011-10-13
> **maverickaddicted said:**
> Yes you are right "openserver" is a hostname. FQDN is "openserver.nexusone.local". However, I have not configured it as DHCP server, it is just a web server. 

My /etc/hosts file is - 

127.0.0.1       localhost mail.nexusone.local
#192.168.1.4    openserver.nexusone.com openserver
192.168.1.5     openserver.nexusone.local openserver 
192.168.1.5     mail.nexusone.local
192.168.1.5     openserver
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Hi

This /etc/hosts looks perfectly okay: is it from one of the clients which ends up browsing at google?  I tried your /etc/hosts fragments on my computers (with my IP addresses) and they worked correctly for web browsing to my local network by short name.

It's worth checking /etc/nsswitch to check you have 'files' listed for hosts, so that name lookups will actually look in /etc/hosts.  My /etc/nsswitch.conf has default values:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

Any other differences between clients which get to openserver and the ones which go search on google?

Is your local router your DHCP server?  You might consider putting the domain name in there.

Hope that helps.

Jonathan.

---

### Post by maverickaddicted on 2011-10-18
> **Jonathan L said:**
> Hi

This /etc/hosts looks perfectly okay: is it from one of the clients which ends up browsing at google?  I tried your /etc/hosts fragments on my computers (with my IP addresses) and they worked correctly for web browsing to my local network by short name.

It's worth checking /etc/nsswitch to check you have 'files' listed for hosts, so that name lookups will actually look in /etc/hosts.  My /etc/nsswitch.conf has default values:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```Any other differences between clients which get to openserver and the ones which go search on google?

Is your local router your DHCP server?  You might consider putting the domain name in there.

Hope that helps.

Jonathan.

My nsswitch.conf looks like this

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

**hosts:          files wins dns**
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by Jonathan L on 2011-10-18
> **maverickaddicted said:**
> My nsswitch.conf looks like this
**hosts:          files wins dns**


Hi Maverick

That looks okay too.  But my question is: was that on one of the computers which is redirected to Google or one of them which doesn't?

I'd try narrowing your problem down to two machines, one which redirects and one which doesn't. Can you find two Ubuntu machines, one which has the problem and one that doesn't?

Then try to find another program which isn't the web browser to do the name lookup; ping is a good example.  I have your settings from /etc/hosts and "ping openserver" gets the correct internal address.

Then check on the two machines:
```
/etc/nsswitch.conf
/etc/resolv.conf
/etc/hostname
```

Hope that's of some use.

Kind regards
Jonathan

---

### Post by redmk2 on 2011-10-18
> **maverickaddicted said:**
> My nsswitch.conf looks like this

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.
...
**hosts:          files [B][COLOR="Red"]wins[/COLOR]** dns[/B]
...



I believe this line is wrong.

Try it this way:
hosts:          files  dns **[COLOR="Red"]wins[/COLOR]**

The system is never getting to the DNS routines because it's choking at **[COLOR="Red"]wins[/COLOR]**.

---

### Post by maverickaddicted on 2011-10-19
> **Jonathan L said:**
> Hi Maverick

That looks okay too.  But my question is: was that on one of the computers which is redirected to Google or one of them which doesn't?

I'd try narrowing your problem down to two machines, one which redirects and one which doesn't. Can you find two Ubuntu machines, one which has the problem and one that doesn't?

Then try to find another program which isn't the web browser to do the name lookup; ping is a good example.  I have your settings from /etc/hosts and "ping openserver" gets the correct internal address.

Then check on the two machines:
```
/etc/nsswitch.conf
/etc/resolv.conf
/etc/hostname
```

Hope that's of some use.

Kind regards
Jonathan

Ok, the file which I shown you before was the nsswitch.conf of my server, Now this is of my laptop - 

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Do I need to make changes on this file also. However, I was wondering about my Windows machines. What can I do on those machines?

---

### Post by maverickaddicted on 2011-10-19
> **redmk2 said:**
> I believe this line is wrong.

Try it this way:
hosts:          files  dns **[COLOR="Red"]wins[/COLOR]**

The system is never getting to the DNS routines because it's choking at **[COLOR="Red"]wins[/COLOR]**.

I have changed the settings as you said, I also did this - 

sudo service smbd restart 
sudo service nmbd restart

but, this not working. Do I need to restart the machine?

---

### Post by redmk2 on 2011-10-20
> **maverickaddicted said:**
> I have changed the settings as you said, I also did this - 

sudo service smbd restart 
sudo service nmbd restart

but, this not working. Do I need to restart the machine?

Answering you question directly...no, but let's start at the beginning again.

If you want to use the DNS TLD suffix of .local then you need to have either manually set it up in /etc/resolv.conf and/or use AVAHI. Post the output of ```
cat /etc/resolv.conf
```

If you are using AVAHI (Apple Bonjour) then your nsswitch.conf file should look like your laptop's configuration```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

In fact you can do away with the *wins *entry in the server; it's not doing anything anyway.  The parts with: *mdns4* are for AVAHI.  If you look at the line you will see that the: *files dns * are the only other entries.

If you want to refer to a host by its hostname (the local host or a remote one on your LAN), you must add that to the /etc/hosts file on each machine (and the IP address must be non-changing).  since we only have 2 that should be easy.

To be absolutely correct the /etc/hosts file should really look like this```
127.0.0.1 localhost localhost.nexusone.local
#192.168.1.4 openserver openserver.nexusone.com 
192.168.1.5 openserver openserver.nexusone.local mail.nexusone.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Note that the format is ```

127.0.0.1 localhost localhost.domain.name
IP_address hostname alias.domain.name 2nd.alias.domain.name
```

The network 127.0.0.1/8 is reserved for the loopback interface (lo) only.  Following this will allow this machine to resolve everything to 192.168.1.5 except the name *localhost *

The nsswitch tells the system which database (files, DNS or avahi (mdns) to look in and in what order.

What hasn't been mentioned is what service on the host *openserver *you are trying to connect to.  Is this a web server (http)?

I hope this isn't to confusing.  Ask questions, even if they sound dumb.  How else will you learn.  :D

-Red

---

### Post by maverickaddicted on 2011-10-20
> **redmk2 said:**
> Answering you question directly...no, but let's start at the beginning again.

If you want to use the DNS TLD suffix of .local then you need to have either manually set it up in /etc/resolv.conf and/or use AVAHI. Post the output of ```
cat /etc/resolv.conf
```

If you are using AVAHI (Apple Bonjour) then your nsswitch.conf file should look like your laptop's configuration```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

In fact you can do away with the *wins *entry in the server; it's not doing anything anyway.  The parts with: *mdns4* are for AVAHI.  If you look at the line you will see that the: *files dns * are the only other entries.

If you want to refer to a host by its hostname (the local host or a remote one on your LAN), you must add that to the /etc/hosts file on each machine (and the IP address must be non-changing).  since we only have 2 that should be easy.

To be absolutely correct the /etc/hosts file should really look like this```
127.0.0.1 localhost localhost.nexusone.local
#192.168.1.4 openserver openserver.nexusone.com 
192.168.1.5 openserver openserver.nexusone.local mail.nexusone.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Note that the format is ```

127.0.0.1 localhost localhost.domain.name
IP_address hostname alias.domain.name 2nd.alias.domain.name
```

The network 127.0.0.1/8 is reserved for the loopback interface (lo) only.  Following this will allow this machine to resolve everything to 192.168.1.5 except the name *localhost *

The nsswitch tells the system which database (files, DNS or avahi (mdns) to look in and in what order.

What hasn't been mentioned is what service on the host *openserver *you are trying to connect to.  Is this a web server (http)?

I hope this isn't to confusing.  Ask questions, even if they sound dumb.  How else will you learn.  :D

-Red

My /etc/resolv.conf is 

# Generated by NetworkManager
nameserver 202.149.208.91
nameserver 202.149.208.92
nameserver 8.8.8.8
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 8.8.4.4


And Yes, this is a webserver, but only for internal development process, not for others.

---

### Post by redmk2 on 2011-10-20
> **maverickaddicted said:**
> My /etc/resolv.conf is 

```
[COLOR="Red"]# Generated by NetworkManager[/COLOR]
nameserver 202.149.208.91
nameserver 202.149.208.92
nameserver 8.8.8.8
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 8.8.4.4

```

And Yes, this is a webserver, but only for internal development process, not for others.

In you first post (the first sentence) you state: *"I have installed Ubuntu 11.04 server edition"*.  To most folks that means you have no GUI desktop and that you will be configuring the host via the config files.

Network Manager (NM) is not part of Ubuntu Server.  NM is a Gnome project that is part of most GUI desktops.  The /etc/resolv.conf file appears to be configured by NM and the modified by you.

How is the networking setup on this host?  Have you added a GUI desktop to the OS?

---

### Post by maverickaddicted on 2011-10-20
> **redmk2 said:**
> In you first post (the first sentence) you state: *"I have installed Ubuntu 11.04 server edition"*.  To most folks that means you have no GUI desktop and that you will be configuring the host via the config files.

Network Manager (NM) is not part of Ubuntu Server.  NM is a Gnome project that is part of most GUI desktops.  The /etc/resolv.conf file appears to be configured by NM and the modified by you.

How is the networking setup on this host?  Have you added a GUI desktop to the OS?

First of all, I want to say Thank You, you are helping me a lot, thank you very much. Yes, I have added the GUI desktop to it and it is not a DHCP server. This is my /etc/network/interfaces file - 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

Should I reconfigure the bind9 using this - [http://www.server-world.info/en/note?os=Ubuntu_11.04&p=dns](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=dns). I have followed (at most) this guide for setting up the server.

---

### Post by redmk2 on 2011-10-21
> **maverickaddicted said:**
> First of all, I want to say Thank You, you are helping me a lot, thank you very much. Yes, I have added the GUI desktop to it and it is not a DHCP server. 
I have a host with Ubuntu 10.04 Desktop that I removed NM from as well as 2 Ubuntu 10.04 Server hosts.  All 3 configure networking the same way. I will explain what to do and why you should do it.

[CENTER][SIZE="3"]**[COLOR="Red"]Please read this all the way through at least once and then we can discuss this further.[/COLOR]** [/SIZE]
It's not hard but you need to understand all of what you are doing before you start. [/CENTER]

First I think you should remove NM so that you are certain that it is not going to interfere with your static setup.  To do this from the command line you do this```
sudo apt-get purge network-manager-gnome 
```

You can test this to see what will be purged like this```
sudo apt-get **[COLOR="Red"]-s [/COLOR]**purge network-manager-gnome
``` 

Then you configure the **[COLOR="purple"]/etc/network/interfaces[/COLOR]** file.  You have done this and it look correct.  You have all the correct parts in the file.

Then you need to configure the **[COLOR="purple"]/etc/resolv.conf[/COLOR]** file.  The file tells  the kernel if there are the nameservers that will resolve IP address that you are going to use.  For the internet I use Google's DNS servers. If you want to use your own local DNS server to map IP addresses to hostnames or DNS names (FQDN)  on the LAN, you may add that DNS server's ip address too.  In addition you can add a domain name to automatically use as a suffix to the hostname.  Thus creating a FQDN. Mine looks like this```
# search <dns_domain> [COLOR="Red"]<-- Do this you do not need to add the domain in the /etc/hosts file
# You would use nexusone instead of <dns_domain> [/COLOR]
nameserver 192.168.1.1 [COLOR="Red"]<-- This is my local DNS server[/COLOR]
nameserver 8.8.8.8
nameserver 8.8.4.4

```

Then you need to configure your **[COLOR="purple"]/etc/hosts[/COLOR]** file.

The hosts file is the primitive of what later became DNS naming.  With DNS, the *domain.tld* is appended to the *hostname*.  Like this```
[COLOR="Green"]hostname[/COLOR].[COLOR="Blue"]domain[/COLOR].[COLOR="Red"]tld[/COLOR]
```

If I owned the domain *trees.com* and had a host named pine or oak, I would have DNS names (FQDN) like this```
pine.trees.com

oak.trees.com
```
The hostname to IP mapping in the /etc/hosts file could look like this```

# The DNS domain (nexusone) is added in the resolv.conf file
# The DNS sufix (.local) is added via AVAHI (mDNS)  
127.0.0.1	localhost
192.168.1.5	openserver mail
```

**[COLOR="purple"]These are the 3 files you need[/COLOR]** to provide basic networking and LAN hostname to IP addressing.

You asked about reconfiguring BIND9.  Are you running BIND9 as a local (LAN side) DNS server?  On which host is it running on?  If you only have a few hosts on your network (and they are statically configured) you can get by using the /etc/hosts file config.

Let me know that you understand all of this.

-Red

---

### Post by maverickaddicted on 2011-10-21
> **redmk2 said:**
> I have a host with Ubuntu 10.04 Desktop that I removed NM from as well as 2 Ubuntu 10.04 Server hosts.  All 3 configure networking the same way. I will explain what to do and why you should do it.

[CENTER][SIZE=3]**[COLOR=Red]Please read this all the way through at least once and then we can discuss this further.[/COLOR]** [/SIZE]
[/CENTER]
 
-Red
Yes, I got it, I will get back to you shortly, after performing all these steps.

---

### Post by maverickaddicted on 2011-10-24
Hi Red,

After removing the gnome-network-manager and rebooting the machine, - /etc/resolv.conf became like this

nexusadmin@openserver:~$ cat /etc/resolv.conf
# Generated by NetworkManager

I edited it again and its still showing the blank resolv.conf file.

---

### Post by redmk2 on 2011-10-24
> **maverickaddicted said:**
> Hi Red,

After removing the gnome-network-manager and rebooting the machine, - /etc/resolv.conf became like this

nexusadmin@openserver:~$ cat /etc/resolv.conf
# Generated by NetworkManager

I edited it again and its still showing the blank resolv.conf file.

It sounds like we haven't removed everything.  Try this```
sudo apt-get purge network-manager
```

Then edit the /etc/resolv.conf file; including removing the header (# Generated by NetworkManager).

Then reboot and see if that works.  It looks as if the package name changed.  Sorry about that.

-Red

---

### Post by maverickaddicted on 2011-10-24
> **redmk2 said:**
> It sounds like we haven't removed everything.  Try this```
sudo apt-get purge network-manager
```

Then edit the /etc/resolv.conf file; including removing the header (# Generated by NetworkManager).

Then reboot and see if that works.  It looks as if the package name changed.  Sorry about that.

-Red
Hi Red,

Now resolv.conf issue is resolved. However, I didn't reboot my server, but I restarted the networking service. Can you check these configuration now - 

nexusadmin@openserver:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 18749
ssh stop/waiting
ssh start/running, process 18855
                                                                         [ OK ]
nexusadmin@openserver:~$ cat /etc/hosts
127.0.0.1       localhost mail.nexusone.local
#192.168.1.4    openserver.nexusone.com openserver
192.168.1.5     openserver.nexusone.local openserver 
192.168.1.5     mail.nexusone.local
192.168.1.5     openserver
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
nexusadmin@openserver:~$ hostname
openserver
nexusadmin@openserver:~$ hostname -f
openserver.nexusone.local
nexusadmin@openserver:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
search nexusone.local
nexusadmin@openserver:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

auto eth1
iface eth1 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

nexusadmin@openserver:~$

---

### Post by capscrew on 2011-10-24
> **maverickaddicted said:**
> Hi Red,

Now resolv.conf issue is resolved. However, I didn't reboot my server, but I restarted the networking service.
Great! > 
 Can you check these configuration now - 

nexusadmin@openserver:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 18749
ssh stop/waiting
ssh start/running, process 18855
                                                                         [ OK ]
This is most probably now an Upstart job.> 
nexusadmin@openserver:~$ cat /etc/hosts
127.0.0.1       localhost mail.nexusone.local
#192.168.1.4    openserver.nexusone.com openserver
192.168.1.5     openserver.nexusone.local openserver 
192.168.1.5     mail.nexusone.local
192.168.1.5     openserver
...
I would do this differently, but this may work for you.  The first name after the IPv4 address is the hostname.  The second name is the alias (FQDN).  You have that backwards.  In addition you have 2 lines for the 192.168.1.5 address.  This should not happen.  One last thing is the .local suffix.  Are you running AVAHI?  If so then you do not need to declare the .local suffix.> 
nexusadmin@openserver:~$ hostname
openserver
nexusadmin@openserver:~$ hostname -f
openserver.nexusone.local

In the order I said above.  This should stay the same> 
nexusadmin@openserver:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
search nexusone.local
What happens if you don't add nexusone.local in the /etc/hosts file?  (e.g just add the hostname> 
nexusadmin@openserver:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

auto eth1
iface eth1 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

nexusadmin@openserver:~$

You can't configure 2 interfaces with the same IP address.  In fact you can't configure 2 interfaces in the same subnet (i.e: 192.168.1.5 and 192.168.1.6) 

Why do you need 2 interfaces?

---

### Post by maverickaddicted on 2011-10-25
> **capscrew said:**
> 

You can't configure 2 interfaces with the same IP address.  In fact you can't configure 2 interfaces in the same subnet (i.e: 192.168.1.5 and 192.168.1.6) 

Why do you need 2 interfaces?

Actually, I wanted to do something else with that port. 
We have broadband connection from two different ISP. One router is having IP 192.168.1.2 and other is having 192.168.2.1. However, I have connected both router to one switch, so that I will have access to both connection. 

Now, my server is configured on this router 192.168.1.2. Therefore, it works only with those machines which are using connected to this router. So my question is that, Can I use my server with the machines connected to this router 192.168.2.1.

---

### Post by capscrew on 2011-10-25
> **maverickaddicted said:**
> Actually, I wanted to do something else with that port. 
We have broadband connection from two different ISP. One router is having IP 192.168.1.2 and other is having 192.168.2.1. However, I have connected both router to one switch, so that I will have access to both connection. 

Now, my server is configured on this router 192.168.1.2. Therefore, it works only with those machines which are using connected to this router. So my question is that, Can I use my server with the machines connected to this router 192.168.2.1.

Actually you can.  You have a couple of alternatives. You can bridge the two networks together and have one network, or you can route to specific machines.  

In my opinion neither will gain you any advantage.  The bridge is of now help you could just move all the host to one subnet and accomplish the same thing.  Most subnets are set up to allow 200+ hosts.  The second one means that you will have to go out of one subnet into the other subnet and back.  Why do that for simple LAN type networking.  When you are communicating between you own hosts on a LAN you don't even need a router, just the switch.  The router is to interconnect different networks like 192.138.2.1 to 192.168.1.1 or 192.168.1 5 to google.com.

On advantage to 2 ISP connections is for failover.  If one goes down the other becomes the connection to the Internet.  In a home network this really isn't critical.

---

### Post by maverickaddicted on 2011-10-31
> **capscrew said:**
> Actually you can.  You have a couple of alternatives. You can bridge the two networks together and have one network, or you can route to specific machines.  

In my opinion neither will gain you any advantage.  The bridge is of now help you could just move all the host to one subnet and accomplish the same thing.  Most subnets are set up to allow 200+ hosts.  The second one means that you will have to go out of one subnet into the other subnet and back.  Why do that for simple LAN type networking.  When you are communicating between you own hosts on a LAN you don't even need a router, just the switch.  The router is to interconnect different networks like 192.138.2.1 to 192.168.1.1 or 192.168.1 5 to google.com.

On advantage to 2 ISP connections is for failover.  If one goes down the other becomes the connection to the Internet.  In a home network this really isn't critical.

Sorry for replying so late, since there was a one week holiday. My server is a Samba PDC and few of my machines are not connected to this machine, they are in there different workgroup. So, is this an issue?

---

### Post by capscrew on 2011-10-31
> **maverickaddicted said:**
> Sorry for replying so late, since there was a one week holiday. My server is a Samba PDC and few of my machines are not connected to this machine, they are in there different workgroup. So, is this an issue?

A workgroup is a notion that is for graphical association of hosts; so you can see them together.  It has nothing to do with them being able to communicate with with your server (or any other host) via TCP/IP.

In short: if all the machines are on the same subnet you should be able to communicate with all of them and see them via the GUI even if they are in separate workgroups.

---

### Post by maverickaddicted on 2011-11-01
It is working now, thank you very much for your help. However, it is working only on windows machine not on ubuntu machines.

One of my client machine configuration files are like this - 

rahul@thinki05:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

rahul@thinki05:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 202.149.208.91
nameserver 202.149.208.92
nameserver 8.8.8.8
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 8.8.4.4
rahul@thinki05:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:7e:e2:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1901824 (1.9 MB)  TX bytes:123278 (123.2 KB)
          Interrupt:47 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:267345 (267.3 KB)  TX bytes:267345 (267.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:71:53:b6  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe71:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23461150 (23.4 MB)  TX bytes:8418398 (8.4 MB)


Do I need to configure the interfaces file of this client machine manually? I have configured it with network manager

IP Address - 192.168.1.89

Gateway - 192.168.1.2 (sometime I use 192.168.1.3)

---

### Post by capscrew on 2011-11-01
> **maverickaddicted said:**
> It is working now, thank you very much for your help. However, it is working only on windows machine not on ubuntu machines.

What is not working on the client Ubuntu machines?  Do you have shares on these clients?> 

One of my client machine configuration files are like this - 

```
rahul@thinki05:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

rahul@thinki05:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 202.149.208.91
nameserver 202.149.208.92
nameserver 8.8.8.8
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 8.8.4.4
rahul@thinki05:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:7e:e2:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1901824 (1.9 MB)  TX bytes:123278 (123.2 KB)
          Interrupt:47 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:267345 (267.3 KB)  TX bytes:267345 (267.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:71:53:b6  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe71:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23461150 (23.4 MB)  TX bytes:8418398 (8.4 MB)


```
It would be helpful if you surround the data with [CODE] brackets.  You can do this by clicking on the # tab at the top of the editor when replying.> 
Do I need to configure the interfaces file of this client machine manually? I have configured it with network manager

IP Address - 192.168.1.89
This seems good.  You should be able to use any address in the 192.168.1.0/24 range (e.g. .1 to .254)> 

Gateway - 192.168.1.2 (sometime I use 192.168.1.3)
This is okay too.

It helps if you describe the failure a little bit.  If there are any error messages, include those also.

---

### Post by maverickaddicted on 2011-11-03
Following are the configuration files of my ubuntu client machine. 


```

rahul@thinki05:/$ sudo cat /etc/network/interfaces
[sudo] password for rahul: 
auto lo
iface lo inet loopback

```

```

rahul@thinki05:/$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4


```

```

rahul@thinki05:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:7e:e2:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229624 (229.6 KB)  TX bytes:229624 (229.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:71:53:b6  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe71:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106749914 (106.7 MB)  TX bytes:24715950 (24.7 MB)


```


When I try to open the url openserver in browser it gets redirected to google search results. However, this works perfectly with windows machines. Only problem is coming on ubuntu machines.

---

### Post by capscrew on 2011-11-03
> **maverickaddicted said:**
> Following are the configuration files of my ubuntu client machine. 


```

rahul@thinki05:/$ sudo cat /etc/network/interfaces
[sudo] password for rahul: 
auto lo
iface lo inet loopback

```

```

rahul@thinki05:/$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4


```

```

rahul@thinki05:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:7e:e2:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229624 (229.6 KB)  TX bytes:229624 (229.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:71:53:b6  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe71:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106749914 (106.7 MB)  TX bytes:24715950 (24.7 MB)


```


When I try to open the url openserver in browser it gets redirected to google search results. However, this works perfectly with windows machines. Only problem is coming on ubuntu machines.

Okay, I'm a little confused here.  Originally you were having problems reaching your webserver from the local host (e.g. from itself).  Did that get taken care of?  Are you now having problems only from other Ubuntu hosts trying to connect to the remote server (openserver)?

---

### Post by maverickaddicted on 2011-11-06
Yes, now I am having problems to remotely connect to my server.

---

### Post by capscrew on 2011-11-07
> **maverickaddicted said:**
> Yes, now I am having problems to remotely connect to my server.

You will need to do something similar to what you did on the host openserver.

On the remote host post the output of these commnds```

hostname
cat /etc/network/interfaces
cat /etc/hosts
cat /etc/resolv.conf

```

---

### Post by maverickaddicted on 2011-11-07
```

rahul@thinki05:/$ sudo cat /etc/network/interfaces
[sudo] password for rahul: 
auto lo
iface lo inet loopback

```

```

rahul@thinki05:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:7e:e2:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229624 (229.6 KB)  TX bytes:229624 (229.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:71:53:b6  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe71:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106749914 (106.7 MB)  TX bytes:24715950 (24.7 MB)

```

```

rahul@thinki05:/$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4

```

```

rahul@thinki05:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       NEXUSONE        thinki05
192.168.1.89    thinki05
192.168.1.90    thinki05

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

```

rahul@thinki05:~$ hostname
thinki05

```

---

### Post by capscrew on 2011-11-07
I see this hosts networking is managed by Network Manager.  Is the IP address reserved so that it stays the same all the time?  Did you edit the /etc/hosts file on this host?  Is this the only other host on the LAN besides openserver?

---

### Post by maverickaddicted on 2011-11-07
Yes, It is a static IP Address. All the systems in my LAN is having static IP - 

192.168.1.89 - When connected via wireless
192.168.1.90 - When connected via wired connection.


All Ubuntu Systems (around 25) are configured in the same way. No machine is configured to get the IP automatically from the router; all are configured manually.

---

### Post by capscrew on 2011-11-07
> **maverickaddicted said:**
> Yes, It is a static IP Address. All the systems in my LAN is having static IP - 

192.168.1.89 - When connected via wireless
192.168.1.90 - When connected via wired connection.


All Ubuntu Systems (around 25) are configured in the same way. No machine is configured to get the IP automatically from the router; all are configured manually.

The /etc/hosts file is a DNS primitive in that it was the starting point for what we now know as DNS names (FQDN).  The file is a mapping of IP address to hostname (also FQDN if you wanted).  You can map any IP to hostname so that there is no need for a DNS server, but...and it is a big point; You need to do this to every host that you want this mapping done.  If you have 2 hosts then both hosts need the same IP address (not including the loopback addresses (127.0.0.0 /8 )).

Go back and look at Red's post #20 and my post #25.  You can make all the entries for the LAN addresses the same in all the /etc/hosts files.  So if you have open server at 192.168.1.5 then you add that to all /etc/hosts files of the hosts that you are using.  If all of the Ubuntu hosts need to resolve the IP address of the host openserver then you need to configure each and every one.

This is where you might consider a DNS server.  I think you mentioned BIND9.  You can also use DNSmasq.  DNSmasq uses a single /etc/hosts file to service all hosts in the LAN.

---

### Post by maverickaddicted on 2011-11-08
> **capscrew said:**
> The /etc/hosts file is a DNS primitive in that it was the starting point for what we now know as DNS names (FQDN).  The file is a mapping of IP address to hostname (also FQDN if you wanted).  You can map any IP to hostname so that there is no need for a DNS server, but...and it is a big point; You need to do this to every host that you want this mapping done.  If you have 2 hosts then both hosts need the same IP address (not including the loopback addresses (127.0.0.0 /8 )).

Go back and look at Red's post #20 and my post #25.  You can make all the entries for the LAN addresses the same in all the /etc/hosts files.  So if you have open server at 192.168.1.5 then you add that to all /etc/hosts files of the hosts that you are using.  If all of the Ubuntu hosts need to resolve the IP address of the host openserver then you need to configure each and every one.

This is where you might consider a DNS server.  I think you mentioned BIND9.  You can also use DNSmasq.  DNSmasq uses a single /etc/hosts file to service all hosts in the LAN.

It is working now, I have just added this line in each computer's /etc/hosts file

192.168.1.5      openserver

You have helped me a lot, thank you very much. Can you help me with this thread

[http://ubuntuforums.org/showthread.php?t=1813689](http://ubuntuforums.org/showthread.php?t=1813689)

I am trying to setup Samba LDAP Server.

---

### Post by capscrew on 2011-11-08
> **maverickaddicted said:**
> It is working now, I have just added this line in each computer's /etc/hosts file

192.168.1.5      openserver

You have helped me a lot, thank you very much. Can you help me with this thread

[http://ubuntuforums.org/showthread.php?t=1813689](http://ubuntuforums.org/showthread.php?t=1813689)

I am trying to setup Samba LDAP Server.

I'm glad you got it working.

In regards to your other thread; I think you need to better understand basic Linux operation and LDAP databases to be successful on that project.  

I don't advise that you reinvent the wheel here.  Most folks don't really understand what work has been put into creating Windows Server Active Directory.  If you don't want to spend the money for Windows I would experiment with both [**_[COLOR="DarkSlateGray"]Samba4[/COLOR]_**]("http://wiki.samba.org/index.php/Samba4") which has an LDAP directory or as others have pointed out [Zentyal]("http://www.zentyal.com/").

---

### Post by maverickaddicted on 2011-11-09
> **capscrew said:**
> I'm glad you got it working.

In regards to your other thread; I think you need to better understand basic Linux operation and LDAP databases to be successful on that project.  

I don't advise that you reinvent the wheel here.  Most folks don't really understand what work has been put into creating Windows Server Active Directory.  If you don't want to spend the money for Windows I would experiment with both [**_[COLOR="DarkSlateGray"]Samba4[/COLOR]_**]("http://wiki.samba.org/index.php/Samba4") which has an LDAP directory or as others have pointed out [Zentyal]("http://www.zentyal.com/").

Ok, I will try to configure Samba4 and make it working. I am also marking this thread as Solved.
**THANK YOU VERY MUCH**.

---

