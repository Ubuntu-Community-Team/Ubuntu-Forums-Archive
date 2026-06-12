---
title: "/etc/hosts and /etc/hostname"
date: 2012-05-22
forum: Server Platforms
---

### Post by ranger12 on 2012-05-22
Okay I am totally confused about this getting so many different answers from around the net. I believe this is what is giving me grief with ldap on the server. If my fqdn for my server is server1.elrancho.net than how should this be set in both of these files. I am a newbie at this so be patient with me please.

After doing some research I have changed the entries in the files to this:
I have this currently in my /etc/hostname file
server1.elrancho.net

I have this in my /etc/hosts file:
127.0.0.1 server1.elrancho.net elrancho

I do not currently have a line of:
127.0.0.1 localhost or xxx.xxx.xxx.xxx server1.elrancho.net or 127.0.1.1 elrancho.

I got out of the post on setting up the ldap server that, if I understand him should be
127.0.0.1 server1.elrancho.net elrancho. Sorry but like I said I am completely confused on this. I am alos running a dns server on the same box for resolving entries [www.elrancho.net]("http://www.elrancho.net"), ns.elrancho.net etc.

I also think something is not quite right since according to the docs on the hostname command "hostname" and "hostname -f" should not both return server1.elrancho.net.
I will continue to work with it myself to see if I can stumble on the right combo between the two. I am still researching on understanding the relationship between the two files.

I wonder if I should be using this in the /etc/hosts file:
127.0.0.1 server1.elrancho.net server1
127.0.1.1 server1

Hmm, according to the Ubuntu manual for hostname it states:
/etc/hostname  This  file  should only contain the hostname and not the
       full FQDN.

Then maybe this would be the proper setup.

/etc/hosts:
127.0.0.1 server1.elrancho.net server1
127.0.1.1 server1

/etc/hostname:
server1

Despite what the man page states - hostname with no arguments and hostname -f return the same string. I think I will change the value in /etc/hostname back to server1.elrancho.net. The docs I believe are confusing and seem to me to be misleading unless I am misunderstanding them.

---

### Post by capscrew on 2012-05-22
> **ranger12 said:**
> Okay I am totally confused about this getting so many different answers from around the net. I believe this is what is giving me grief with ldap on the server. If my fqdn for my server is server1.elrancho.net than how should this be set in both of these files. I am a newbie at this so be patient with me please.

After doing some research I have changed the entries in the files to this:
I have this currently in my /etc/hostname file
server1.elrancho.net

I have this in my /etc/hosts file:
127.0.0.1 server1.elrancho.net elrancho

I do not currently have a line of:
127.0.0.1 localhost or xxx.xxx.xxx.xxx server1.elrancho.net or 127.0.1.1 elrancho.

I got out of the post on setting up the ldap server that, if I understand him should be
127.0.0.1 server1.elrancho.net elrancho. Sorry but like I said I am completely confused on this. I am alos running a dns server on the same box for resolving entries [www.elrancho.net]("http://www.elrancho.net"), ns.elrancho.net etc.

I also think something is not quite right since according to the docs on the hostname command "hostname" and "hostname -f" should not both return server1.elrancho.net.
I will continue to work with it myself to see if I can stumble on the right combo between the two. I am still researching on understanding the relationship between the two files.

I wonder if I should be using this in the /etc/hosts file:
127.0.0.1 server1.elrancho.net server1
127.0.1.1 server1

Hmm, according to the Ubuntu manual for hostname it states:
/etc/hostname  This  file  should only contain the hostname and not the
       full FQDN.

Then maybe this would be the proper setup.

/etc/hosts:
127.0.0.1 server1.elrancho.net server1
127.0.1.1 server1

/etc/hostname:
server1

Despite what the man page states - hostname with no arguments and hostname -f return the same string. I think I will change the value in /etc/hostname back to server1.elrancho.net. The docs I believe are confusing and seem to me to be misleading unless I am misunderstanding them.

The documentation is sometimes misleading.  :-)

The */etc/hostname* file should contain the hostname only

The */etc/hosts* file is a mapping of hosts to IP addresses and traditionally has used hostname only as the primary name.

So what is a host name and a FQDN?  The hostname is the name of a host.  Maybe it your help to define a host.  In this instance a host is the specific machine.  If we had a machine named ***oak*** in the DNS domain of ***trees.com*** we would have this```
host = **[COLOR="Blue"]oak[/COLOR]**
FQDN = **[COLOR="Blue"]oak[/COLOR]**.trees.com
```

The contents of the /etc/hostname file would look like this```
oak
```

The etc/hosts file is a little different. It is the primitive of DNS naming.  The mapping of IP addresses to *hostnames* (not FQDN) in the beginning.  It would look like this```

127.0.0.1	localhost
192.168.1.2	oak [COLOR="Red"]oak.trees.com[/COLOR]
192.168.1.3     maple [COLOR="Red"]maple.trees.com[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

The IP address 127.0.0.1 (actually anything that starts with 127.) is for a virtual NIC that is local to the host you are using.  The IP address you should be mapping is the IP address of the real NIC the host uses, especially if you are using DNS.

The /etc/hosts file accepts alias names (see red above).  You can use either one with ping but it will always resolve to the hostname and IP address you mapped.  You can see that here ```
ping [COLOR="Red"]maple.trees.com[/COLOR]
PING [COLOR="Blue"]maple[/COLOR] (192.168.1.3) 56(84) bytes of data.
64 bytes from [COLOR="Blue"]maple[/COLOR] (192.168.1.3): icmp_seq=1 ttl=64 time=0.017 ms
```
The second name in the hosts file is an alias not the real FQDN, it's an alias.. The hosts file is only for that local machine (local host).  All Ubuntu hosts look for name resolution first to the local hosts file and then DNS.  
The bottom line is ```
host = server1
FQDN = elrancho.net 
```

The /etc/host file should be```
127.0.0.1 localhost
xxx.xxx.xxx.xxx [COLOR="Blue"]server1[/COLOR] [COLOR="Red"]server1.elrancho.net[/COLOR] 
```The /etc/hostname file should contain ```
server1
```

---

### Post by ranger12 on 2012-05-23
Okay that is fine - however when youj do run this:

hostname

it returns: server1 as the docs state but if you do this:
hostname -f it resturns server1 but according to the docs it says it should retrun:
server1.elrancho.net

if I run this:
hostname -d it returns server1 but according to the docs it should return the domain name which should be elrancho.net

If I run dnsdomainname it should return elrancho.net but it returns nothing. So there is some inconsistency than here. That is another bit of confusion I am trying to clear up.  According to that than I do not have a domain name set up -  just a hostname.  I am going to do some more research on this. That still seems a bit odd to me.

According to the docs, shouldn't the alias be the last entry in the line and not the second plus running hostname -a returns server1.elrancho.net not server1?

---

### Post by capscrew on 2012-05-23
> **ranger12 said:**
> Okay that is fine - however when youj do run this:

hostname

it returns: server1 as the docs state but if you do this:
hostname -f it resturns server1 but according to the docs it says it should retrun:
server1.elrancho.net

if I run this:
hostname -d it returns server1 but according to the docs it should return the domain name which should be elrancho.net

If I run dnsdomainname it should return elrancho.net but it returns nothing. So there is some inconsistency than here. That is another bit of confusion I am trying to clear up.  According to that than I do not have a domain name set up -  just a hostname.  I am going to do some more research on this. That still seems a bit odd to me.

According to the docs, shouldn't the alias be the last entry in the line and not the second plus running hostname -a returns server1.elrancho.net not server1?

The FQDN and the domain name are not supplied directly from the hostname file.  Those switches (-d and -f) invoke the resolver libs and report back the domain and FQDN via DNS from the resolver routine.

Have you setup a local DNS server?  Have you configured /etc/resolv.conf?

What is the output of these```

cat /etc/resolv.conf

cat /etc/network/interfaces
```

---

### Post by kennethconn on 2012-05-23
/etc/hosts:
127.0.1.1 server1

Uncomment this line in file and try your hostname commands with all the switches and see if it returns results you expect.

---

### Post by ranger12 on 2012-05-23
I have gotten hostname to function properly with this in my /etc/hosts file:

127.0.0.1 localhost
xxx.xxx.xxx.xxx server1.elrancho.net server1

...and this in the /etc/hostname file:

server1

Restarted both services.
Output of hostname:
hostname: server1
hostname -a: server1
hostname -f: server1.elrancho.net
hostname -d: elrancho.net

Output of dnsdomainname:
 elrancho.net

Yes I do have the dns server on the same box up and configured. I am getting forward and reverse lookups with the records in my zone file with dig and nslookup.

---

### Post by kennethconn on 2012-05-23
So ... solved?

---

### Post by ranger12 on 2012-05-23
Oh sorry - yes solved!:P

---

### Post by cybercity@localhost on 2012-06-08
the same issue! :) i have configured /etc/hosts file as
```
 127.0.0.1 localhost
xxx.xxx.xxx.xxx server.domain.com server
```
yet i cannot resolve domain name from windows or any other pc?

hostname -d outputs
domain.com

---

### Post by capscrew on 2012-06-08
> **cybercity@localhost said:**
> the same issue! :) i have configured /etc/hosts file as
```
 127.0.0.1 localhost
xxx.xxx.xxx.xxx server.domain.com server
```
[I][B]yet i cannot resolve domain name from windows or any other pc?
[/B][/I]
hostname -d outputs
domain.com

The hosts file resolves for that machine only.  You need one on each host.  If your LAN had host1 and host2 and you wanted both to resolve each other, **both **would need to have /etc/hosts files with host1 and host2 entries.

---

### Post by kennethconn on 2012-06-08
> **cybercity@localhost said:**
> the same issue! :) i have configured /etc/hosts file as
```
 127.0.0.1 localhost
xxx.xxx.xxx.xxx server.domain.com server
```
yet i cannot resolve domain name from windows or any other pc?
 
You'll have to repeat this for other machines on the network including the Windows machine, or centralise some services, but either way you have more to do.
 
> **cybercity@localhost said:**
>  
hostname -d outputs
domain.com
That is as expected.

---

