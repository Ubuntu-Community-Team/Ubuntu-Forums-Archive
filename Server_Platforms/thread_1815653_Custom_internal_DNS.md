---
title: "Custom internal DNS"
date: 2011-07-31
forum: Server Platforms
---

### Post by tomsdongle on 2011-07-31
Hi Everyone,

I was just wondering if this is achievable:

At home I'm running 10.04 on my internal network, I use the server for various projects, namely PHP dev.

What i'd like to do is enter "http://redmine.tom" or even just [http://redmine](http://redmine) on any of my machines in the house and have it take me to my internal redmine site.

On my Ubuntu box I have LAMP running along with Bind.

Is this achievable? does anyone know of any resources to help me? I've found a ton of Bind tutorials but none of them apply to this scenario.

Aswell as this, I do not want to access my internal sites when out of the house, I just want to access them internally.

any help welcome,

Tom

---

### Post by CharlesA on 2011-07-31
Check out DNSMasq. Easier to set up then BIND.

---

### Post by tomsdongle on 2011-07-31
thank you :)

---

### Post by tomsdongle on 2011-08-01
would someone be able to give some pointers, every dnsmasq tutorial I find I applies to a setup different to mine.

I just want to host webpages internally on the same machine and instead of visiting 192.168.0.1/typo3... id just like to to use [http://tom](http://tom) or [http://redmine.tom](http://redmine.tom) etc.

thanks again

---

### Post by CharlesA on 2011-08-01
What are you having problems with?

I found a page [here]("http://www.dd-wrt.com/wiki/index.php/DNSMasq_-_DNS_for_your_local_network_-_HOWTO"), that might help. I use dnsmasq on my DD-WRT router for local name resolution.

---

### Post by tomsdongle on 2011-08-01
thanks again Charles,

basically I just dont know how to approach this and wanted to find a nice tutorial that matched my scenario

---

### Post by CharlesA on 2011-08-01
You are going to be using it just for DNS, not DHCP right?

---

### Post by tomsdongle on 2011-08-02
yeah, *just* DNS. My airport extreme is dealing with DHCP

---

