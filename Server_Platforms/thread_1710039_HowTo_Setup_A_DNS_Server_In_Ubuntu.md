---
title: "HowTo Setup A DNS Server In Ubuntu"
date: 2011-03-19
forum: Server Platforms
---

### Post by linuxsyst on 2011-03-19
[CENTER][SIZE="2"]Overview[/SIZE][/CENTER]

Would you like to setup a DNS Server in Ubuntu? How about setting up a private internal domain name at home? Well, you’ve come to the right place. There are number of tutorials on the internet showing you how to setup a DNS Server with Ubuntu using Bind 9. So, why another how-to document? That’s a good question. I’ve decided I needed to write a simple tutorial that anyone with a little bit of Linux knowledge would be able to follow. In the process, I hope readers are also able to learn how DNS works. Ok, let’s jump right to it!

[CENTER][SIZE="2"]What is DNS?[/SIZE][/CENTER]

First of all, let’s cover the basics. What is DNS? DNS stands for Domain Name Server. It’s a service that runs on a server that translates humanly recognizable domain names such as [www.yahoo.com](www.yahoo.com) or [www.google.com](www.google.com) into its assigned IP addresses. If the DNS server does not recognize the domain name being requested, it will forward the domain name request to another DNS server and so on until the name is resolved.

A typical DNS request is when someone is accessing a website. Let’s use the [www.yahoo.com](www.yahoo.com) domain as an example. When a user clicks a Yahoo link or types the Yahoo URL on the address bar of the browser, the DNS server processes the domain request. If it doesn’t find [www.yahoo.com](www.yahoo.com) on its DNS table, it will forward the request to another DNS server with a higher authority and so on until it finds a server with the URL entry. The IP address information is then sent back to the user’s browser. If the domain name is not found, a “server not found” message is displayed on the browser.

[SIZE="2"][CENTER]Assumptions[/CENTER][/SIZE]

Enough with the DNS background. Let’s now start configuring our own DNS server. Let’s assume that we have the following: we want to create a private internal domain name called mydomain.com, our private internal network is 192.168.0.x and our router and gateway is set at 192.168.0.1. Let’s assume all devices are going to be configured with static IP addresses. Normally, most computer systems nowadays are configured to automatically obtain IP addresses from the DHCP server/router. In this example, we will use static IP addresses to show how DNS works. Finally, we have 3 computers connected to our network:

Ubuntu Server, the DNS server – 192.168.0.9
Ubuntu Desktop – 192.168.0.10
PC – 192.168.0.11

[CENTER][SIZE="2"]Instructions[/SIZE][/CENTER]

1. To install the DNS server, we need to install Bind 9.

```
sudo apt-get install bind9
```
2. Let’s configure Bind. We need to touch 5 files.

We will edit 3 files.

```
/etc/bind/named.conf.local
```
```
/etc/bind/named.conf.options
```
```
/etc/resolv.conf
```
We will create 2 files.

```
/etc/bind/zones/mydomain.com.db
```
```
/etc/bind/zones/rev.0.168.192.in-addr.arpa
```
A. First step. Lets add our domain zone – mydomain.com.

```
sudo vi /etc/bind/named.conf.local
```
[PHP]# Our domain zone
zone "mydomain.com" {
   type master;
   file "/etc/bind/zones/mydomain.com.db";
};

# For reverse DNS
zone "0.168.192.in-addr.arpa" {
   type master;
   file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};[/PHP]
Save file. Exit.

We just created a new domain. Please note: later we will create two files named mydomain.com.db and rev.0.168.192.in-addr.arpa files. Also, notice the reverse IP address sequence in the reverse DNS section.

B. Let’s add the DNS servers from your ISP. In my case, I’m using Comcast DNS servers. You can place the primary and secondary DNS servers here separated by semicolons.

```
sudo vi /etc/bind/named.conf.options
```
[PHP]forwarders {
   68.87.76.178;
};[/PHP]
Save file. Exit.

C. Now, let’s modify the resolv.conf file found in /etc and place the IP address of our DNS server which is set to 192.168.0.9.

```
$ sudo vi /etc/resolv.conf
```
[PHP]search mydomain.com.
nameserver 192.168.0.9[/PHP]
D. Now, let’s define the zones.

```
sudo mkdir /etc/bind/zones
```
sudo vi /etc/bind/zones/mydomain.com.db
$TTL 3D
@ IN SOA ns.mydomain.com. admin.mydomain.com. (
   2007062001
   28800
   3600
   604800
   38400
);
mydomain.com.  IN      NS         ns.mydomain.com.
ubuntudesktop  IN      A          192.168.0.10
www            IN      CNAME      ubuntudesktop
pc             IN      A          192.168.0.11
gw             IN      A          192.168.0.1
                       TXT        "Network Gateway"[/CODE]
The TTL or time to live is set for 3 days
The ns.mydomain.com nameserver is defined
ubuntudesktop, pc and gateway are entered as an A record
An alias of www is assigned to ubuntudesktop using CNAME

E. Let’s create a “rev.0.168.192.in-addr.arpa” file for reverse lookup.

```
sudo vi /etc/bind/zones/rev.0.168.192.in-addr.arpa
```
[PHP]$TTL 3D
@       IN      SOA     ns.mydomain.com. admin.mydomain.com. (
                2007062001
                28800
                604800
                604800
                86400
)
        IN      NS      ns.mydomain.com.
1       IN      PTR     gw.mydomain.com.
10      IN      PTR     ubuntudesktop.mydomain.com.
11      IN      PTR     pc.mydomain.com.[/PHP]
3. Let’s restart Bind to activate our latest changes.

```
sudo /etc/init.d/bind9 restart
```
4. Finally, let’s test our new domain and DNS entries.

Dig

$ dig mydomain.com
Nslookup

```
nslookup gw
```
5. That’s it.

---

### Post by ovanoudenhove on 2011-04-13
Hi , 
 
If you want to create custom directories for your zone files , keys ( for dnssec ) etc... , what access rights do they require and who should be the owner ?
 
I've installed ubuntu server 10.04lts , during install I have selected DNS server and ssh server , performed the basic bind setup , but I got stuck from the moment I created my own customer directories for my zone files and keys ( for example , I created 3 directories : /dnszones , /dnsreversezones , /keys
 
At first I thought apparmor was blocking access to my direcories and zone file , but after disabling apparmor completely ( for testing purposes only ) , I still noticed access denied problems in my syslog from bind. 
 
I ended up making those directories owned by root:root , and granted them 777 rights. This may be more than needed , but at least it works now and bind answers my local dig queries.
 
Could someone tell me what really needed / recommended ? I don't think my solution is the most secure one...

---

### Post by SeijiSensei on 2011-04-13
Are you running a chrooted server with the -u switch?  ("ps aux | grep named" will answer the question.)  If you are, then the username appearing after -u will need to own the files and directories in the chroot tree.  In Ubuntu, this user is called "bind".

---

