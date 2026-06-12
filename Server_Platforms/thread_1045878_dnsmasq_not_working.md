---
title: "dnsmasq not working"
date: 2009-01-20
forum: Server Platforms
---

### Post by mjfroggy on 2009-01-20
Hello all,

Once again I am hoping someone can help me its really realted to another post I had but instead of just posting their since this question is about a specific package I thought it best to start another thread

Anyway I installed dnsmasq as per the instructions here [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)   
I am running ubuntu 8.10 which has a dhcp connection 
what I want to do is use a local domain name / nameserver to pullup a intranet page  so like [http://ubuntubox](http://ubuntubox) which would only be able to be pulled up in my house on my lan.
So I setup dnsmasq and even made sure to start it after the changes and still when I go to [http://ubuntubox](http://ubuntubox) nothing is found ??

In my etc/dnsmasq.conf file I have a line like so
# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
resolv-file=/etc/nameservers


# Add other name servers here, with domain specs if they are for
# non-public domains.
server=/ubuntubox/192.168.1.125


So I am hoping someone can point me to what step I missed?? thanks

---

### Post by capscrew on 2009-01-20
mjfroggy,

There are 2 things wrong with your install.  First is the incorrect use of:```
server=/ubuntubox/192.168.1.125

``` 

The second thing is; **these directions in the guide are for setting up redirection to public nameservers**.  This is not what you want to do.  You want to map local LAN IP addresses to hostnames.

I suggest you read [**[COLOR="DarkRed"]this[/COLOR]**]("http://www.enterprisenetworkingplanet.com/netos/article.php/3377351").    Read the part about local LAN DNS.  Then decide what you want to accomplish.  Do you have a local domain or a FQDN?  Are you using DHCP for the IP addressing?  Ask questions here and I will help.

---

### Post by mjfroggy on 2009-01-21
Hello Capscrew,

I read the tutorial you link to although that seems to also talk about editing a file on each workstation (PC) I am more interested in not having to edit a file on each individual workstation. 

My setup also if it helps is cable modem --> linksys router --> all work stations are then connected to the router although I also have two wireless laptops I use on the property as well. The server is also plugged into the router. 

I dont have any dedicated IP my internet provides me only a dynamic ip address connection. I am able to access the router directly if its in their I would need to edit anything to get this to work. 

To also answer your question I am trying to setup a local domain which is ubuntubox  so that any of my PC's within my property here would be able to just type in [http://ubuntubox](http://ubuntubox) and be able to pull up my intranet webpage I setup on the server here.
I as you know installed dnsmasq and uninstalled the default dns/bind9 that was on the ubuntu server from the default install.
My goal would be to have the server act as a local dns server besides from just being a box that serves up the internal only webpage I created. 

The biggest desire I have is to not have to go around my house and my garage (which is setup as an office) and change a configuration file in all of the 6 PC's I have. 

Thanks For your help
Jason

---

### Post by capscrew on 2009-01-21
> **mjfroggy said:**
> Hello Capscrew,

I read the tutorial you link to although that seems to also talk about editing a file on each workstation (PC) I am more interested in not having to edit a file on each individual 
workstation.

There is no getting around a visit to each of your PC's at least once.  Even if it is virtually via remote desktop.  We have to implement DNS (and reverse some of what you have misconfigured).

  The use of DNSmasq (any DNS) is for the management of any future updates or changes from a central location.  Remember;setup requires the modification of all of the computers in your network.> 

My setup also if it helps is cable modem --> linksys router --> all work stations are then connected to the router although I also have two wireless laptops I use on the property as well. The server is also plugged into the router. 

I dont have any dedicated IP my internet provides me only a dynamic ip address connection. I am able to access the router directly if its in their I would need to edit anything to get this to work. 


For what you are trying to do there no need to concern yourself with the ISP provided IP address.  That address is the external (public facing) address.   The router connects your external IP address to your internal private address (basically).  It looks like this: [COLOR="Red"]**ISP <-->modem/**[/COLOR][COLOR="Blue"]/router<--multiple hosts [/COLOR].  I show the external part in the above diagram as the red connection.  Your private IP network (shown in blue) is what we will be working with.
> 

To also answer your question I am trying to setup a local domain which is ubuntubox  so that any of my PC's within my property here would be able to just type in [http://ubuntubox](http://ubuntubox) and be able to pull up my intranet webpage I setup on the server here.FYI -- The domain is (in your case) the name you provide for all the hosts (computers) in your network to have in common.  A hostname is the name of the individual host (computer).  The naming convention for HTTP is configured in the web server itself.  What does ubuntubox represent?  Is it the hostname of one of your hosts or a domain name you have for your private network?  As an example lets say we have a domain name of cities and hosts named london and paris.  What do you think we would get if we typed in [http://cities?](http://cities?)  How about [http://london](http://london) ?  Or how about this: [http://paris.cities](http://paris.cities).  As you can see we can call a domain or host or a host.domain.  We have lots of options that can be set in the web server.  The DNS server can accomodate (map the names) any or all of this.> 
I as you know installed dnsmasq and uninstalled the default dns/bind9 that was on the ubuntu server from the default install.
My goal would be to have the server act as a local dns server besides from just being a box that serves up the internal only webpage I created. 

I assume that the webserver and DNS server (in fact all/any server daemons) are on this Linux host.  

Sometimes the terms can be confusing.  So let's define some terms:
```

box = physical hardware (no OS)
host = a device with an IP address.  
   My printer has an IP address and it's hostname is bb-hp1 
   and the router is called bb-gw1

hostname = a human recognizable name mapped to an IP address
   I can ping my printer or router by it's name 
   My desktop is named malibu and my wifes laptop 
   is called manila.  I can ping them by name also. 

server = a process (daemon) running on a host waiting for a 
     request from a client 
 Some of these servers (daemons) are:
   httpd (apache webserver)
   named (BIND DNS server)
   dnsmasq (dnsmasq DNS server)
   smbd (Samba file server) 

```

> 
The biggest desire I have is to not have to go around my house and my garage (which is setup as an office) and change a configuration file in all of the 6 PC's I have. 


As I said you will have to do this a least once to configure the naming services (or install remote desktop services).  Again, we need to make each host aware of the new naming service ie: the address of the dnsmasq server. In addition we need configure DHCP and make sure that the correct hostname is assigned to all.

For the above to be successfully implemented we need to know the following:

What is the OS on all of the laptops and desktops in your network?

domain = (this can be workgroup)

hostname = (for all hosts)

Are we using DHCP? ( I would - this means we can manage it all from one place)

What is the private (internal) IP addressing scheme (what is the network address)?

What web server are you using?


> 
Thanks For your help
Jason

---

### Post by koenn on 2009-01-21
> **capscrew said:**
> There is no getting around a visit to each of your PC's at least once.  
...  we need to make each host aware of the new naming service ie: the address of the dnsmasq server. In addition we need configure DHCP and make sure that the correct hostname is assigned to all.

dnsmasq can do dhcp and is perfectly capable of passing a nameserver to the hosts so I don't see why you'd have to go around and reconfigure everything by hand, unless he's not using dhcp yet, which would be unusual.


the names that you want dnsmasq to resolve, need to be added (with ip address) in /etc/hosts of the server where dnsmasq runs (an alternate file can be specified in dnsmasq.conf, but to get things up and troubleshoot, defaults are usually easier)

dnsmasq will also resolve names for addresses its dhcp server has leased out, if the dhcp client provided a hostname during the request. But for a web server, you probably have a static address, manually.

---

### Post by 2ndPlaceFinish on 2009-01-21
I am having a similar issue and could really use some help. 

I have a simple home network with 2 desktops and 1-2 laptops connected through a wireless router.

On one of the desktops I am running Ubuntu with Apache. I am able to view the website from ALL computers using the IP address (192.168.0.12) but I am only able to view the website on the Ubuntu desktop using the host name (web01).

I have installed Dnsmasq and would like to configure it to update all the computers in my network to resolve the specific host (web01) to the correct IP (192.168.0.12). I also would not want to go to each computer individually if it is possible because I would want laptops that come on the network to be able to see the website by using the host name (web01).

Any help would be greatly appreciated, I am running into a wall.

---

### Post by capscrew on 2009-01-22
> **2ndPlaceFinish said:**
> I am having a similar issue and could really use some help. 

I have a simple home network with 2 desktops and 1-2 laptops connected through a wireless router.

On one of the desktops I am running Ubuntu with Apache. I am able to view the website from ALL computers using the IP address (192.168.0.12) but I am only able to view the website on the Ubuntu desktop using the host name (web01).

I have installed Dnsmasq and would like to configure it to update all the computers in my network to resolve the specific host (web01) to the correct IP (192.168.0.12). I also would not want to go to each computer individually if it is possible because I would want laptops that come on the network to be able to see the website by using the host name (web01).

Any help would be greatly appreciated, I am running into a wall.

What have you read or tried?  Just as I have advised [COLOR="Green"]*mjfroggy*[/COLOR], you should have some idea that you can share with us as to what you do want to do.  DHCP?  Limit access to known hosts?  A need to name all hosts in the domain?

Read the dnsmasq.conf file -- available [[COLOR="Purple"]**here**[/COLOR]]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example")

The explanations are great.  If you have questions check back.

---

### Post by 2ndPlaceFinish on 2009-01-22
I have looked at the dnsmasq.conf file a little.

I have added this entry to the /etc/hosts file.

192.168.0.12    web01

I also set up the apache virtual hosts on my active site.

Like I said, I can access using web01 on my ubuntu desktop, but not on my windows laptop or my windows desktop (Only have access if I use the ip address)

I searched google for how to configure Dnsmasq but it does not seem to be running. According to the documentation I looked at:

address=/example.com/127.0.0.1 

Should route the request to my localpage when I run it on the Ubuntu desktop, but that does not even work. I did restart Dnsmasq after the changes.

I also followed some other examples and still it does not seem to be working. Is there anyway I can:

1) test to make sure Dnsmasq is working
2) get Dnsmasq to reroute all requests for web01, to the webpage running on my ubuntu desktop (For every computer behind my router)

Please let me know if you can provide any links or areas I can look into. If you can help, that would be great. Let me know if I was not clear in my explanations.

Thanks

---

### Post by capscrew on 2009-01-22
> **2ndPlaceFinish said:**
> I have looked at the dnsmasq.conf file a little.

I have added this entry to the /etc/hosts file.

192.168.0.12    web01

If you did the same to your Windows hosts you would be done> 

I also set up the apache virtual hosts on my active site.

Like I said, I can access using web01 on my ubuntu desktop, but not on my windows laptop or my windows desktop (Only have access if I use the ip address)

I searched google for how to configure Dnsmasq but it does not seem to be running. According to the documentation I looked at:

address=/example.com/127.0.0.1 

Should route the request to my localpage when I run it on the Ubuntu desktop, but that does not even work. I did restart Dnsmasq after the changes.

This is **not** intended for that purpose.  just as in spybot, it is to map external redirects to a black hole.
> 


I also followed some other examples and still it does not seem to be working. Is there anyway I can:

1) test to make sure Dnsmasq is working


To see if the dnsmasq daemon is running try running from the CLI:```
ps -ef|grep dnsmasq
```
> 

2) get Dnsmasq to reroute all requests for web01, to the webpage running on my ubuntu desktop (For every computer behind my router)

DNSmasq is a DNS server.  It maps hostnames to IP addreses.  It **does not** reroute anything.  It is best to think of it more like this; you send a data request to the host web01 the request is mapped to the IP address of web01 (192.168.0.12) by either DNSmasq or /etc/hosts.  There is one more step.  On a LAN the IP address is resolved to the ethernet address (MAC) by the protocol ARP.  You can use ARP to find all of the MAC addresses you will need to configure DNSmasq correctly.  Ping one of your hosts by IP address and then from the CLI try: ```
arp -a
```
You should get something like this:```
$ arp -a
newport (192.168.1.10) at 00:0F:EE:B5:22:D8 [ether] on eth0
rincon (192.168.1.2) at 00:22:75:DB:5C:C0 [ether] on eth0

```
> 
Please let me know if you can provide any links or areas I can look into. If you can help, that would be great. Let me know if I was not clear in my explanations.

This is a more pertinent section of the dnsmasq.conf file:```
# Always give the host with ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m
```

You can also set the lease time to "infinite" to create a consistent IP address for the server.  To obtain the ethernet address (MAC) on your Linux host try this from the CLI:```
ifconfig -a
```

you will get somthing like this:```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:76:CD:54:E0  
```
The "HWaddr 00:04:76:CD:54:E0" is what we want.

> 


Thanks

---

### Post by 2ndPlaceFinish on 2009-01-22
Thanks for the help, I will spend the next couple of days trying to get everything figured out and let you know what happens.

---

### Post by koenn on 2009-01-22
also look in /var/log/syslog occasionally. services such as dnsmasq log lots of what they're doing to that file, it might give you a clue of what is working and what isn't.

---

### Post by mjfroggy on 2009-01-22
Hello again

Ok so to answer some questions

my server is given a hostname of and it should have a dedicated IP that my router has given it. I should be running dhcp on the server as well (how do I check?) I did uninstall dns and bind9 and I though when I installed dnsmasq that that was also setting up the host(server) to run dhcp
Or maybe its my router itself that is running dhcp since that is the device that is dishing out ip's to all the different "hosts" I have connected (i.e., laptops, desktops, printer, server)

the word ubuntubox should represent the internal non public domain I want to give to the server inorder for any of the workstations to access the non-public webpage on the server. When I installed Ubuntu 8.10 it also asked to input a host name which is what I made ubuntubox be (not sure if I should of did that or should I have made it be something different). Again my thought was I want to access the server by host name so I thought thats why during install I put the hostname ubuntubox in their

All workstations and laptops have windows vista
I dont think I setup a domain or workgroup for all the PC's when I click on start --> network on my vista laptop I just see a listing of all the laptops and desktops which follow a naming convention like so personsname-laptop or personsname-pc 
I am not sure or really have any private IP addressing scheme
I guess I should connect to my linksys router and look for this
the webserver itself is ubuntu 8.10 server

thanks for your help
I should not if I right now login to one of my workstations and go to windows/system32/drivers/etc/hosts
and put the line 192.168.1.125 ubuntubox in it and then save it I then can open a web browser on the workstation and access the servers non-public domain name via [http://ubuntubox](http://ubuntubox)
So then my question how do I do this remotely can I not somehow just pushout to all servers a new host file that would overwrite the one on all workstations ?

---

### Post by capscrew on 2009-01-22
> **mjfroggy said:**
> Hello again

Ok so to answer some questions

my server is given a hostname of and it should have a dedicated IP that my router has given it. 

I see that the **hostname of the web server is ubuntubox**.  It is not the name of the domain.  This is fine.
> 
I should be running dhcp on the server as well (how do I check?)

DNSmasq is going to be both the DHCP and DNS server.  The DHCP server in the router will need to  be turned off.
> 

I did uninstall dns and bind9 and I though when I installed dnsmasq that that was also setting up the host(server) to run dhcp
Or maybe its my router itself that is running dhcp since that is the device that is dishing out ip's to all the different "hosts" I have connected (i.e., laptops, desktops, printer, server)

In a small LAN (Network) we only want one DHCP server.  We need DNSmasq to handle both DHCP and DNS.
> 

the word ubuntubox should represent the internal non public domain I want to give to the server inorder for any of the workstations to access the non-public webpage on the server.

Not the domain name; but rather it is the hostname.  You do not have a domain situation.
> 
When I installed Ubuntu 8.10 it also asked to input a host name which is what I made ubuntubox be (not sure if I should of did that or should I have made it be something different). Again my thought was I want to access the server by host name so I thought thats why during install I put the hostname ubuntubox in their

To confirm what the hostname is, try this from the CLI:```
hostname
```I'll bet it returns the hostname "ubuntubox"
> 
All workstations and laptops have windows vista
I dont think I setup a domain or workgroup for all the PC's when I click on start --> network on my vista laptop I just see a listing of all the laptops and desktops which follow a naming convention like so personsname-laptop or personsname-pc 
I am not sure or really have any private IP addressing scheme
I guess I should connect to my linksys router and look for this
the webserver itself is ubuntu 8.10 server

thanks for your help
I should not if I right now login to one of my workstations and go to windows/system32/drivers/etc/hosts
and put the line 192.168.1.125 ubuntubox in it and then save it I then can open a web browser on the workstation and access the servers non-public domain name via [http://ubuntubox](http://ubuntubox)

This is what I told you in the beginning.  It also confims the answer the question: "what is the hostname of the web server?"> 
So then my question how do I do this remotely can I not somehow just pushout to all servers a new host file that would overwrite the one on all workstations ?

In your case it will be easier (and safer) for you to manually do this at each vista host.  To "pushout" as you say, a new file would involve sharing a Vista "system folder" on each host. If you are there why not just add the web server to the file and be done with it.  As a practical matter it will use as much time to setup the "sharing" as it will setting up DNSmasq or manually configuring the system.

At this point we need to think what the goal is. Consider your own networking skills. You have 3 options.  

```

1. Manually modify the Vista windows/system32/drivers/etc/hosts files. 
   This is by far the simplest method.  You have already done one already.
You should also manually configure the IP address on each host too. 
This is because the drawback to using the hosts file is that if
something such as the hostname or the IP address changes you will need 
to reconfigure.  You should not use DHCP if you are doing this
(the IP address can change).

2. Use DNSmasq -- we only need to configure 3 files (all on the server).
They are /etc/dnsmasq.conf and /etc/hosts and /etc/resolv.conf.
We will need to turn off DHCP in the router.

3. Setup MS shares on each Vista host in an area of the filesystem 
that can considerably break your OS (I will not help in this area).  
It will take as much time to setup as option 1 and get you no more advatange.

```

At this point I think DNSmasq will be your best choice.  Your VIsta hosts are already setup for DHCP so not further modification is needed.  DNSmasq is a centralized place with 3 easy files to configure.  If you make changes we can adapt quickly.

Decide which path you wish to take and we will configure it together.  If you choose DNSmasq, then we need the ethernet address (MAC) of the server.  I explained how to find this in a previous post to this thread.

---

### Post by joel_gil on 2010-06-11
I am having trouble making dnsmasq work

Ive followed different instructions several times and ive come to indentify the problem

as far as i know the dnsmasq is configured correctly for both dns and dhcp, but none of them work, even when manually setting the dns server on the other machines of the network, dnsmasq wont respond to the requests.

using tools like nslookup dig and netstat i know that the daemon IS running and the server IS caching the websites i test from the server.

but again, nothing for the rest of the machines, trying to ping directly to each other ips work but not the hostnames assigned to each, only when i ping from the server

for all these reasons i believe the dnsmasq is correctly configured, but maybe some port is blocked? the requests arrive but no answer is sent

i hope u guys can tell me since this is the only post where i saw i a slightly similar problem

thanks in advace

---

