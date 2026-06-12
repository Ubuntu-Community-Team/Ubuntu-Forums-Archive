---
title: "Problem during DNS server setup on local network."
date: 2013-04-01
forum: Server Platforms
---

### Post by avanindra on 2013-04-01
Hi Folks,

I have a small local network , with few desktops and one server . The server machine has UBUNTU 12.04 server 64 bit installed on it. Some of the desktops are windows , one is Mac and others are ubuntu . What I am trying to accomplish is to create a local DNS server for my network and DNS server would be present on the server machine. My internet connection is DSL Broadband connection , though it generates IP's with DHCP , I have given static IP to all the machines present in my network. 

I followed this link [http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/](http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/)  for setting up the DNS server. I am attaching the concerned files which I modified or created ( I have added extra .txt at the end of them for attachment issues ). After following up all the instructions to best of my knowledge , at the end when I type following command

>> [COLOR=#008000]host -l trintranet.com
[/COLOR]
I get the following output

[COLOR=#ff0000]; Transfer failed.[/COLOR]
[COLOR=#ff0000]Host trintranet.com.trintranet.com not found: 9(NOTAUTH)[/COLOR]
[COLOR=#ff0000]; Transfer failed.[/COLOR]


where trintranet.com is the local domain-name I have chosen.

So what am I doing wrong here?....

Please let me know if you need anymore information.

regards
Avanindra Singh

---

### Post by darkod on 2013-04-01
As you can see by that output, the host command seems to be for looking up hosts, not the domain name. The way you used it, it's looking for trintranet.com.trintranet.com. Does a host like that exist? I assume not.

Also, if you only want a cached DNS it's much better and easier to use dnsmasq inetad of bind. Do you need a DNS that will be only cached, or full DNS?

---

### Post by avanindra on 2013-04-01
Hi darkod,

Thanks for the reply. I am trying to create cached DNS. I want to host a local web server , such that I could access it with simple addresses like example.intranet.com from any of the computer on the local network.

> *As you can see by that output, the host command seems to be for looking up hosts, not the domain name. The way you used it, it's looking for trintranet.com.trintranet.com. Does a host like that exist? I assume not.*

Actually that's what I am trying to figure out , why is it adding extra trintranet.com . If it's not too much trouble , can you point me which file to look into for fixing it . I am new to networking , please bear with me if I am asking bit trivial question.
 
Regards

Avanindra Singh

---

### Post by darkod on 2013-04-01
For such a simple task, definitely use dnsmasq.

First remove purge bind so that it doesn't interfere. It should be something like:
```
sudo apt-get remove --purge bind9
```

After that install dnsmasq (not sure if it's already installed in server 12.04):
```
sudo apt-get install dnsmasq
```

Add the host you want to use to open the webpage in /etc/hosts pointing to the private IP of the server, it should be something like:
192.168.x.x   example.intranet.com

Save and close the file.

That should be it I guess.

You should be able to test from the client machines using dig or nslookup:
dig example.intranet.com
nslookup example.intranet.com

PS. It is usually good practice to let dnsmasq only listen to the internal interface, and not the external interface leading to the internet. For that open the config file /etc/dnsmasq.conf and find the line #interface and change it into your internal interface, for example:
interface=eth1

Restart dnsmasq after that:
sudo service dnsmasq restart

If that doesn't work try:
sudo /etc/init.d/dnsmasq restart

---

### Post by avanindra on 2013-04-01
Thank you very much darkod. I would try to setup my dns server with dnsmasq. After a cursory read , it seems to serve my exact purpose.

regards

Avanindra Singh

---

### Post by SeijiSensei on 2013-04-01
Errors like "domain.name.domain.name" usually happen because you forgot a ending period on the domain in the zone file.  Remember that any fully-qualified name has to end with a dot, which is actually a reference to the root nameservers.  Example.com is a subdomain of .com, and that is a subdomain of the root, represented by just a dot.

Pay special attention to the statement of authority (SOA) record at the top of the zone file.  Does it look like this:
```

@     IN     SOA     example.com.     support.example.com. (

```

or like this 
```

@     IN     SOA     example.com     support.example.com (

```

The first. with trailing dots,  is correct; the second is not.

Omitting the trailing dot is probably the most common error when writing zone files.

---

### Post by ranger12 on 2013-04-01
After looking at your files, I noticed in your named.conf.local this:

zone "trintranet.com" IN {
    type master;
    file "/etc/bind/zones/trintranet.com.db";
};

I do not think the IN is supposed to be there.

---

