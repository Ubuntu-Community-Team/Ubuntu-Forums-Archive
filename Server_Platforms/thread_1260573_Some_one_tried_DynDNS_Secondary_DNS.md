---
title: "Some one tried DynDNS Secondary DNS?"
date: 2009-09-07
forum: Server Platforms
---

### Post by Spikerok on 2009-09-07
I have a slight problem... I have dynamic ip address, soon it will change, but while I have it some thing has to be done. If I get disconnected from internet my IP address will be changed, if nameservers set on that ip, they will be down for one-two days after I modify nameservers on current ip address. 
So here is the question.. will secondary DNS redirect users on my ip straight after my ip was changed? or is their any other service which can do given task?

---

### Post by Cardale on 2009-09-07
I'm not exactly sure what your trying to do here, but you probably know that there is a update client.

---

### Post by Spikerok on 2009-09-08
basically I don't want to have two day down time, and I need some service which will keep pointing to my server. If im correct if I will use basic free dyndns, and place it us nameserver i will still have downtime for 1-2 days! Actually if I'm correct it's impossible to put basic free dyndns name as nameserver.

---

### Post by denver on 2009-09-08
I dont know about DynDNS, i have only used no-ip.com, but I think they do offer DNS hosting for your own domain name. Not sure if it's free or not, but it is possible. If you only need DNS hosting and not the entire webhosting package (web/email) then a DNS hosting plan is best for you. 

You will find the aproriate nameservers to set for your domain name after login. They also have a support system where you can ask any question you might have regarding what steps you need to take in order to host your domain name.

The IP update works in exactly the same way as they do for any free account, and takes up to 5 minutes.

[http://freedns.afraid.org/](http://freedns.afraid.org/)

is a DNS hosting site, but for free accounts, i have found it to be unreliable. There are a few others, feel free to look arround for whatever suits you best.

---

### Post by Spikerok on 2009-09-08
I have tried [http://freedns.afraid.org/](http://freedns.afraid.org/) but when I enter my domain on web site it seems to be broken, even if i set it up correctly.


As well i have experienced some massive downtimes every 20-30min for 1-2min. Until it totally gone off after 5 days or some thing.
Maybe because domain was shown as broken?

---

### Post by denver on 2009-09-08
Like I said, freedns.afraid.org has been unreliable for me as well. Long update intervals, lots of errors during updates, but it is free after all. They do have a payed service that works well.

To troubleshoot name resolution the 2 most usefull tools are whois and host.

```
whois example.com
```

to find out the nameservers set for your domain name. These should be set to your DNS service provider. Presuming that one of the nameservers for your domain is ns.example.com 

```
host example.com ns.example.com
```

this should give you the "A" record (IP address) for your domain name.

NOTE: Replace example.com with your domain name and ns.example.com with the nameserver set for your domain name.

If no A record is returned by your nameserver, and you configured everything corectly, you must contact your DNS service provider.

Good luck!

---

