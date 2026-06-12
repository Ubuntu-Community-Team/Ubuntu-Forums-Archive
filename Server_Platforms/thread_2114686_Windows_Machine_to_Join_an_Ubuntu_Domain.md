---
title: "Windows Machine to Join an Ubuntu Domain"
date: 2013-02-10
forum: Server Platforms
---

### Post by chrisguk on 2013-02-10
Hi,

I think I have posted on this before but not quite sure.

I have an Ubuntu Server running on a dedicated Proliant server which operates as the DNS and gateway for all machines on the network.  I have been trying for a while to get a windows machine to join the domain.

I took the steps:

1.  Right click on Computer > Change Name > Member of: Domain.
2.  I type the domain name in bart.home.

I then get this error:

An Active Directory Domain Controller (AD DC) for the domain 'bart.home' could not be contacted.

Any ideas what I am doing wrong here?

---

### Post by lingpanda on 2013-02-10
Your Windows client doesn't seem to be able to resolve your domain name. Can you ping the server from your client? Did you set you DNS to your DC IP?

---

### Post by chrisguk on 2013-02-10
> **lingpanda said:**
> Your Windows client doesn't seem to be able to resolve your domain name. Can you ping the server from your client? Did you set you DNS to your DC IP?

Thanks for the reply.

Yes I can ping the server with the host name and IP address.  The DNS is set in the network settings ncpa.cpl within Windows.

Is it something I missed in the BIND DNS setup config?

---

### Post by chrisguk on 2013-02-11
I am still having problems with this topic.

With Ubuntu machines I am able to be part of the domain no problem so when I navigate to one of the intranet sites the browser knows it is supposed to resolve to the DNS server for the content.

I have tried everything I know to get this to work but just cant figure it out.  Surely it isnt that hard to join a windows machine to the domain of my Ubuntu Server is it?

---

### Post by koenn on 2013-02-11
you got al your terminology mixed up to the point that you should rephrase your problem/question into an accurate description of what you're trying to do.

A domain, and domain membership, is MS parlance for an Active Directory Domain - hence the error "Active Directory Domain Controller could not be contacted". Do you have a Windows Server with Active Directory Services ? Or Samba as an AD Domain Controller ?

and is setting up an AD Domain really what you are trying to do ? If so, are you sure you need/want it ? I haven't met many sysadmins who would try to join a PC to a domain while not knowing  they have to  create the domain first and that they'd need a DC to do so.

---

### Post by collisionystm on 2013-02-11
If its Windows Vista or 7, you need to apply a change to the registry to join.

> Windows Registry Editor Version 5.00 
 
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanManWorkstation\Parameters] 
"DNSNameResolutionRequired"=dword:00000000 
"DomainCompatibilityMode"=dword:00000001


Save that in notepad as samba.reg

double click on the file to add it to the registry. You should then be able to join.

---

### Post by chrisguk on 2013-02-11
Firstly I wish to thank you for your reply and for pointing out that my terminology is wrong because I believe if people dont correct you, you always go on thinking you are right.

Okay I will rephrase my question a little.

I have the following setup on my server:

DNS Bind
Samba
LAMP Stack

I have created the appropriate zone records for the DNS and all of the normal NSLOOKUP checks work no problem.  Even on the clients, they all ping to the DNS server IP and hostname (including windows clients)

On the DNS server I have setup various virtualhost blocks, just hosting some development websites im working on.  

When I goto a Ubuntu client and navigate to:

[http://www.mysite.home](http://www.mysite.home) 

It resolves no problem and knows the apache server is on the DNS server at 172.22.22.40

When I try the same from a Windows client it doesnt.

The file sharing within Samba etc is all working great so thats not the issue.

So essentially I guess I just want to be able to produce the same browsing results and the buntu machine.

Does that make any sense?

---

### Post by chrisguk on 2013-02-11
Its Windows 7

---

### Post by SeijiSensei on 2013-02-11
Open a terminal in Windows by running "cmd" from the main menu.  Then type the command "ipconfig /all".  Verify that your machine is using the correct DNS server addresses.

---

### Post by chrisguk on 2013-02-11
Hi its configured for the correct DNS server after running config/all

---

### Post by koenn on 2013-02-11
> When I goto a Ubuntu client and navigate to: [http://www.mysite.home](http://www.mysite.home) It resolves no problem and knows the apache server is at 172.22.22.40

When I try the same from a Windows client it doesnt.

What does the bowser on the windows machine say, then ?

---

### Post by chrisguk on 2013-02-11
It says this:

"Oops! Google Chrome could not find website"

---

### Post by koenn on 2013-02-11
> **chrisguk said:**
> It says this:

"Oops! Google Chrome could not find website"

Ah, Chrome's also one of those browsers that think stripping out useful information makes for a better user experience. 

Assuming that message is baby language for "couldn't find the address for that website", you **do** have a DNS problem. 

Please post the output of that ipconfig command. 
Abd the output of ```
nslookup www.mysite.home 
```

---

### Post by chrisguk on 2013-02-11
> **koenn said:**
> Ah, Chrome's also one of those browsers that think stripping out useful information makes for a better user experience. 

Assuming that message is baby language for "couldn't find the address for that website", you **do** have a DNS problem. 

Please post the output of that ipconfig command. 
Abd the output of ```
nslookup www.mysite.home 
```

Hi,

Just by the output after typing that code from my windows client, it seems I do have a DNS issue.  Here is the output because I dont know how to fix it:

--------    snip   ----------



Microsoft Windows [Version 6.2.9200]
(c) 2012 Microsoft Corporation. All rights reserved.

C:\Users\chrisguk>nslookup website.home
Server:  maggie.bart.home
Address:  172.22.22.40

*** maggie.bart.home can't find website.home: Non-existent domain


--------- end snip --------------

---

### Post by koenn on 2013-02-11
What do you use for DNS server ?

---

### Post by chrisguk on 2013-02-11
> **koenn said:**
> What do you use for DNS server ?

I assume you mean software?

I use BIND9

---

### Post by darkod on 2013-02-11
> **chrisguk said:**
> I assume you mean software?

I use BIND9

Nope, what is the dns server machine that the win7 client is using? If you are using public DNS from your ISP provider for example, it has no idea where your domain is. It's only local domain.

I suggest you post the output of the ipconfig /all that Sensei asked for.

---

### Post by chrisguk on 2013-02-11
> **darkod said:**
> Nope, what is the dns server machine that the win7 client is using? If you are using public DNS from your ISP provider for example, it has no idea where your domain is. It's only local domain.

I suggest you post the output of the ipconfig /all that Sensei asked for.

I will post it just give me a sec.  The DNS Server resides within my own private LAN.  It has an internet facing NIC and LAN facing NIC all routed through a 24 port cisco switch.

It is also running as a DHCP server too for any other clients that join the network.

Windows 7 is just on a normal standard desktop machine.  Ubuntu server is on a Proliant DL380 G3 server.


Here is the ipconfig/all:

```


Microsoft Windows [Version 6.2.9200]
(c) 2012 Microsoft Corporation. All rights reserved.

C:\Users\chrisguk>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : akira
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : TAP-Win32 Adapter V9
   Physical Address. . . . . . . . . : 00-FF-CD-1E-DB-69
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros L1 Gigabit Ethernet 10/100/1000Ba
se-T Controller
   Physical Address. . . . . . . . . : 00-1D-60-AE-DE-C3
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::11da:2e77:b0bd:3dc7%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 172.22.22.35(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 172.22.22.40
   DHCPv6 IAID . . . . . . . . . . . : 251665760
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-A9-FF-E2-00-1D-60-AE-DE-C3

   DNS Servers . . . . . . . . . . . : 172.22.22.40
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
   Physical Address. . . . . . . . . : 08-00-27-00-4C-88
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::38d9:7c58:4fb8:55e8%23(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.56.1(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 537395239
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-A9-FF-E2-00-1D-60-AE-DE-C3

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{B11E8370-4F30-4866-9C30-471330B7F439}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{1502B7E4-8BF0-48FE-AA2B-96012D61BC53}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes



```

---

### Post by koenn on 2013-02-11
> **chrisguk said:**
> I assume you mean software?

I use BIND9

your zone config is probably wrong - 
if your server calls himself maggie.bart.home, he'd be 
host maggie in domain/zone _bart.home_

your webserver, likewise, seems to be
(host www) in zone/domain _website.home_

you want them both in the same zone, or you need to have your DNS servers maintain 2 zones, or you need to call your website by its rightful name (eg [www.bart.home](www.bart.home), assumingtherse a record for www in the bart.home zone already)

something like that.
Can't help you with the details, it's been a while since i've done bind and I'd have to go look it all up myself (while its getting near bed time and I should be winding down). 

You could also switch to dnsmasq, which is fairly easy to set up, it simply uses the server's /etc/hosts as a zone file

---

### Post by chrisguk on 2013-02-11
Hi,

In the forward looking zone file I have the website setup as an A record like so:

```


websitename      IN CNAME maggie


```

maggie is the the name of the DNS server.  Here is my zone file:

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
akira           IN      A       172.22.22.35
maggie          IN      A       172.22.22.40
lisa            IN      A       172.22.22.45
www             IN      A       172.22.22.50
win7            IN      A       172.22.22.90
mediawiki       IN      CNAME   maggie
bacula          IN      CNAME   maggie
mediawiki       IN      CNAME   maggie
phpmyadmin      IN      CNAME   maggie
websitename     IN      CNAME    maggie



```

Hope that makes more sense

ps.  hope you like my simpsons theme lol

---

### Post by darkod on 2013-02-11
Yeah, you are correctly using 172.22.22.40 as DNS server. So it must be something with the config. I also don't know bind details but you can compare your config with a link I have for easy bind setup:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

You don't need to do exactly the same of course, just compare the important parts. koenn already gave some pointers.

---

### Post by koenn on 2013-02-11
assuming you can resolve names in the bart.home zone, i.e. a client can get an address for, say, maggie.bart.home or router.bart.home, these urls should work

[http://www.bart.home](http://www.bart.home) - provided there's a webserver at 172.22.22.50
[http://websitename.bart.home](http://websitename.bart.home) - provided there's a webserver at 172.22.22.40

do they ? 


You have a talent for making things confusing (weren't we talking about [http://www.mysite.home](http://www.mysite.home) earlier ?) and I need to go get some sleep.

---

### Post by chrisguk on 2013-02-11
> **koenn said:**
> assuming you can resolve names in the bart.home zone, i.e. a client can get an address for, say, maggie.bart.home or router.bart.home, these urls should work

[http://www.bart.home](http://www.bart.home) - provided there's a webserver at 172.22.22.50
[http://websitename.bart.home](http://websitename.bart.home) - provided there's a webserver at 172.22.22.40

do they ? 


You have a talent for making things confusing (weren't we talking about [http://www.mysite.home](http://www.mysite.home) earlier ?) and I need to go get some sleep.

Sorry about the name change of the site I wasnt thinking, I guess its because I was tired and frustrated too.  The answer was staring me in the face though.

---

