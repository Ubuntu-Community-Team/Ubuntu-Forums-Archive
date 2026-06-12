---
title: "DNS Server"
date: 2012-09-09
forum: Server Platforms
---

### Post by mortrca on 2012-09-09
I am trying to setup a DNS server for my home and I have become very confused. Here is what I want:

1. I want all of my computers to send their DNS requests to my server - I know how to handle this part using my router.
2. I want to manually define custom domains on my server (ie. example.home) - This is a big source of confusion, I want to host the example.home website on the same server I am using for DNS and I don't know how to setup the zone file for this.
3. I want any DNS requests that I haven't manually defined on my server to be resolved using Google's DNS servers (8.8.8.8 and 8.8.4.4). - I have defined them as forwarders in the named.conf.options file.
4. I want the server to send all DNS requests to itself so it properly resolves the domains that I have manually configured.

I have no experience with this sort of thing and your assistance is greatly appreciated.

---

### Post by darkod on 2012-09-09
See if these instructions can help. They look simple and precise.
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

---

### Post by mortrca on 2012-09-09
> **darkod said:**
> See if these instructions can help. They look simple and precise.
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

When trying to set this up, I followed essentially the same steps. I did not do step 0 (what purpose does that step serve?) but I have completed the other steps up to step 6. I have copied the template file as suggested here:
[https://help.ubuntu.com/community/BIND9ServerHowto#Zone_File](https://help.ubuntu.com/community/BIND9ServerHowto#Zone_File)
But that is where I get confused. I don't know how to setup the zone file so the domain points to the same server I am using for DNS.

---

### Post by darkod on 2012-09-09
You don't se the purpose of step 0? You can set up your own nameservers, but you are not authority to assign domain names. You need to buy them from a registrar/company that has the authority.
So, lets say you buy your domain gtom GoDaddy. By default it uses their nameservers. You can go into the control panel and change that to the IPs of your nameservers.

When someone types example.com in their browser, the internet knows that domain is registered at GoDaddy and checks which nameservers to use to resolve it. Since you will put your IPs there, the process will be redirected to your nameservers.

This step is crucial so that the resolution of example.com to an IP to be correct.

The only case when you don't need the above is if you want your nameserver to resolve the domains only for your home computers. But in that case, you don't need a full dns server, you only need to work with the hosts file.

What exactly do you want to achieve, your dns server to be the main nameserver for the domain for all of the world, or only for your home network and the rest of the world will use the registrar nameservers? There is important difference in the setup.

---

### Post by mortrca on 2012-09-09
Alright, right now I only want to resolve the domains for my home computers. I want to be able to type example.home into any of the computers ***in my house*** and have it resolve to the same server that is handling the domain name resolution (DNS and web server in one machine). The part I don't understand is how to setup the zone file on the DNS/web server to accomplish this.

---

### Post by darkod on 2012-09-09
Just for the record, for in house it's much more simpler to use a package called dnsmasq than to configure a full nameserver.

But if you want to give bind a go, in those instructions it says to use your server IP instead of the xxx.xxx.xxx.xxx. So, your server has a static private IP on your network I guess, something like 192.168.x.x. Just use this private IP in the dns zone files.

The computers will try your nameserver first (because that is what your router dhcp settings are telling them), and the zone file will point them to the server private IP.

This won't work for the world, but for your network it should.

---

