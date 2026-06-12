---
title: "Multiple IP on my Ubuntu 12.04 VPS want to use them as DNS"
date: 2013-04-08
forum: Server Platforms
---

### Post by travelpal on 2013-04-08
Guys,
I have this VPS installed with Ubuntu 12.04 LTS version and I got two IP address as well. Right now I have my nameserver pointed to 8.8.8.8 (default I think). My VPs provider don't have domain name server, so I was using free cloudflare for managing my domains. I also installed zpanel. 
Now, I am not too happy with cloudflare reason is its expensive for Pro as I have multiple domains and same website but they charge additional per domain :(. 
I am thinking of setting up my own domain name server, but I have no idea how to do it. I read lots of tutorial online but I always end up non working DNS. I have bind9 installed and all those tools, could somebody please help me so that I can use same ns1.example.com point to my 1st IP and ns2.example.com point to my second IP. 
And my four domains can use this same DNS server for its contents, which will anyway be redirected in apache config. 

Here is my /etc/network/interfaces contents :

```

        down route del default dev venet0
        down ifconfig venet0 down




iface venet0 inet6 manual
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:6feb:b684/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:6feb:b684/128
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:1725:8e5a/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:1725:8e5a/128
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:b1fc:4d57/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:b1fc:4d57/128
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:76c5:47fe/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:76c5:47fe/128
        up route -A inet6 add default dev venet0
        down route -A inet6 del default dev venet0


auto venet0:0
iface venet0:0 inet static
        address 193.183.99.227 <== IP 1
        netmask 255.255.255.255


auto venet0:5
iface venet0:5 inet static
        address 193.183.99.4 <== IP 2
        netmask 255.255.255.255

```

---

### Post by CharlesA on 2013-04-08
Why not just use the DNS manager at the place you registered your domain? Mine allows you to manage DNS settings but they also provide hosting too (which I don't use, I use a VPS now).

---

### Post by cerealcable on 2013-04-10
This guide should tell you everything you need to know about setting up bind9 and using it.  However, it will take some reading and time to understand.  You will gain a ton of understanding of how DNS works and its incredibly important to the internet which makes it worth it!

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by sandyd on 2013-04-10
> **travelpal said:**
> Guys,
I have this VPS installed with Ubuntu 12.04 LTS version and I got two IP address as well. Right now I have my nameserver pointed to 8.8.8.8 (default I think). My VPs provider don't have domain name server, so I was using free cloudflare for managing my domains. I also installed zpanel. 
Now, I am not too happy with cloudflare reason is its expensive for Pro as I have multiple domains and same website but they charge additional per domain :(. 
I am thinking of setting up my own domain name server, but I have no idea how to do it. I read lots of tutorial online but I always end up non working DNS. I have bind9 installed and all those tools, could somebody please help me so that I can use same ns1.example.com point to my 1st IP and ns2.example.com point to my second IP. 
And my four domains can use this same DNS server for its contents, which will anyway be redirected in apache config. 

Here is my /etc/network/interfaces contents :

```

        down route del default dev venet0
        down ifconfig venet0 down




iface venet0 inet6 manual
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:6feb:b684/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:6feb:b684/128
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:1725:8e5a/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:1725:8e5a/128
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:b1fc:4d57/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:b1fc:4d57/128
        up ifconfig venet0 add 2a00:dcc0:eda:98:183:193:76c5:47fe/128
        down ifconfig venet0 del 2a00:dcc0:eda:98:183:193:76c5:47fe/128
        up route -A inet6 add default dev venet0
        down route -A inet6 del default dev venet0


auto venet0:0
iface venet0:0 inet static
        address 193.183.99.227 <== IP 1
        netmask 255.255.255.255


auto venet0:5
iface venet0:5 inet static
        address 193.183.99.4 <== IP 2
        netmask 255.255.255.255

```
there are a few free ones
[http://dns.he.net](http://dns.he.net) is the first one that comes to mind atm

If your looking for something paid, but not exorbitantly expensive, go with amazon route 53 or dnsmadeeasy.

Generally, I would not not setup my own DNS Server at all, just because there is no redundancy (unless you actually have multiple vpses with Bind9 Slaves and such), and if you don't set it up correct, you can potentially become [part of a DNS Amplification attack]("http://blog.cloudflare.com/deep-inside-a-dns-amplification-ddos-attack")

---

