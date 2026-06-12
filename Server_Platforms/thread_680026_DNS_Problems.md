---
title: "DNS Problems"
date: 2008-01-27
forum: Server Platforms
---

### Post by .Shaun on 2008-01-27
Ok, I recently followed the perfect ubuntu 7.10 server with ispconfig guide, and installed ispconfig with no problems. I tried entering my site shaunsnetwork.com, no luck. I also tried another domain of mine pointed to my nameservers. no luck. SO then I tried to manually go through and enter the junk into /etc/bind/named.conf and make a database file. Still no luck. I can't make virtualhosts work either. Help please?

~Shaun

---

### Post by .Shaun on 2008-01-27
BUMP, please help, this is pretty urgent.

---

### Post by tlcoffee on 2008-01-27
What is your /var/log/messages and /var/log/syslog saying when you start bind up?

---

### Post by .Shaun on 2008-01-27
Im not sure what im looking for, but here's a little snipet.

```

Jan 27 14:51:00 server1 named[5109]: command channel listening on 127.0.0.1#953
Jan 27 14:51:00 server1 named[5109]: command channel listening on ::1#953
Jan 27 14:51:00 server1 named[5109]: zone 0.0.127.in-addr.arpa/IN: loaded serial 1
Jan 27 14:51:00 server1 named[5109]: zone 97.27.65.in-addr.arpa/IN: loaded serial 2008012703
Jan 27 14:51:00 server1 named[5109]: pri.shaunsnetwork.com:13: warning: '65.27.97.24.': MX is an address
Jan 27 14:51:00 server1 named[5109]: zone shaunsnetwork.com/IN: loaded serial 2008012703
Jan 27 14:51:00 server1 named[5109]: zone gamersho.info/IN: loaded serial 2008012701
Jan 27 14:51:00 server1 named[5109]: running

```

---

### Post by koenn on 2008-01-28
> **.Shaun said:**
> Ok, I recently followed the perfect ubuntu 7.10 server with ispconfig guide, and installed ispconfig with no problems. I tried entering my site shaunsnetwork.com, no luck. I also tried another domain of mine pointed to my nameservers. no luck. SO then I tried to manually go through and enter the junk into /etc/bind/named.conf and make a database file. Still no luck. I can't make virtualhosts work either. Help please?

~Shaun

putting junk in /etc/bind/named.conf is usually not a good idea.
Also, to have any hope of help with network and server problems, you need to provide a minimum of useful information, such as 
1- what exactly it is you're trying to do, 
2- ip addresses and other network config, what changes you made to the default configs of the servers (or other hosts) involved, ...

---

### Post by .Shaun on 2008-01-28
1) I want to be able to host multiple domains that have different root directories.

2) My internal IP is 192.168.1.101 and my server is conencted to my router via ethernet. I have not made any changes to system files.

---

### Post by koenn on 2008-01-28
just to majke sure we're on the same page ;
> **.Shaun said:**
>  I have not made any changes to system files.
so you didn't add anything to /etc/bind/named.conf, you didn't create a  zone file for your shaunsnetwork.com and others ? 

> **.Shaun said:**
> I want to be able to host multiple domains that have different root directories.
I assume you're talking about web sites with different domain names, in separate directories on a web server - apache probably ?

---

### Post by .Shaun on 2008-01-28
Oh, I see what your saying, I added this to /etc/bind/named.conf

```
zone "shaunsnetwork.com" {
type master;
file "/etc/bind/zones/shaunsnetwork.com.db";
};

```

And made the correspoding zone file. And yes, i want to host multiple domains in separate directories.

~Shaun

---

### Post by koenn on 2008-01-28
And in thet zone file, there's a record for your web server ('www', probably ?) with  the correct address ? That *is* an address on your LAN, isn't it ? you only mentioned
> My internal IP is 192.168.1.101 and my server is connencted to my router via ethernet
so I don't know if thats your PC's address, or the server's. 

maybe you should post the zone file. 
Or at least verify that you can do a valid dns lookup, Like this :
```
n@knix:~$ dig www.sandbox.xx

; <<>> DiG 9.3.2 <<>> www.sandbox.xx
;; global options:  printcmd
;; Got answer:

;; ANSWER SECTION:
www.sandbox.xx    0       IN      A       192.168.10.1


```

---

### Post by .Shaun on 2008-01-28
192.168.1.101 is my server's internal IP, and here is the zone file.

```
shaunsnetwork.com. IN SOA ns1.shaunsnetwork.com. admin.shaunsnetwork.com. (

2006081401
28800
3600
604800
38400 )

shaunsnetwork.com. IN NS ns1.shaunsnetwork.com.
IN A 65.27.97.24
mail.shaunsnetwork.com. IN MX 10 mail.shaunsnetwork.com.
shaunsnetwork.com. IN MX 10 mail.shaunsnetwork.com.

www IN A 65.27.97.24
mail IN A 65.27.97.24
ns1 IN A 65.27.97.24

```

And host and dig both come back with not found.

---

### Post by koenn on 2008-01-28
I think the line 
mail.shaunsnetwork.com. IN MX 10 mail.shaunsnetwork.com.
can be left out.

the line 
IN A 65.27.97.24
also (it's incomplete)


verify that the PC you're using is configured with 192.168.1.101 as (first) dns server. host or dig should tell you [www.shaunsnetwork.com](www.shaunsnetwork.com) = 65.27.97.24

since  you have multiple names with the same address, you should actually use CNAME ("alias") records eg
ns1 IN A 65.27.97.24
www IN CNAME ns1
but you can leave it for now. 


Your main problem is that, as soon as bind is working right, you'll get 65.27.97.24 for [www.shaunsnetwork.com](www.shaunsnetwork.com), and I'm not sure that address is actually going to work (to access the web server) from your LAN. It might.
Given that these are public addresses and that you have a domain name, I assume that sooner or later you'll want this server to be accessible from the internet ? That will mean you have to configure your router to forward dns and http traffic to that server ("port forwarding). that's assuming you have the usual broadband router with NAT. 
To test bind and apache from your web, you might (temporarily) set
www in A 192.168.1.101 ; your site will only be accessible from your LAN? but it will allow you to verify bind resolves the name correctly, and test your web site(s) / web server config.

lastly, you'll have to configuere apache for multiple web sites / domain names / doc roots. 

(See what I meant with explaining what you want to do and providing relevant info ?) It's bed time here, maybe someone else can look at what we have so far and take it a few steps further ?

---

### Post by .Shaun on 2008-01-28
Well, the thing is that when you go to [http://65.27.97.24/](http://65.27.97.24/) it is accessible. Also, I have port forwarding open on ports 80, 22, and 53. What others do I need? Also, how do I verify that the PC i am using is configured with 192.168.1.101 as my first DNS server?

---

### Post by koenn on 2008-01-29
OK, you've already set up portforwarding etc. well then, you're almost there. I checked :  Your DNS server returns a valid address for [www.shaunsnet](www.shaunsnet)..., it's just that your webserver isn't handling the multiple websites correctly yet. That's not a DNS issue, you manage that in apache. 

First, to set 192.168.1.101 as your DNS server : go to system : networking : DNS (in Gnome/ubuntu), or edit /etc/resolv.conf

you still need dns for hosts outside your domain, so you'll have to add an external dns server as well. A cleaner way to do that is to put a forwarder in /etc/bind/named.conf or  /etc/bind/named.conf.options, like so :
```
options {
	....
 		// If your ISP provided one or more IP addresses for stable nameservers, 
		// you probably want to use them as forwarders.  

		forwarders {
				195.130.132.53;
				212.31.2.2;
		};

	....
	};

```


Apache stuff:
have a look in /etc/apache2/sites-available and /etc/apache2/sites-enabled. in /etc/apache2/sites-available, you create a file for each site you'll be hosting, stating its name and a path to where the web pages will kept. There's a default that you can copy and modify. Then, put web pages in the appropriate directory, and create a symlink in /etc/apache2/sites-enabled that ponts to a file in /etc/apache2/sites-available, eg /etc/apache2/sites-enabled/shaunnet pointing to /etc/apache2/sites-available/shaunnet
reload apache and see how it goes. I(s been a while since I've done this, and I'm no expert. so you might have to post back to get advise from others here.

Remember that each site will need an entry in your dns. If they're different domains, eg [www.shaunnet.com](www.shaunnet.com) and [www.gamesomething.info](www.gamesomething.info), you'll need separate zone files.

I suggest you start with one, and when thats working 100%, do the same for the other sites.

---

### Post by .Shaun on 2008-01-29
Ok, i added 192.168.1.101 as my DNS server, I added the forwarders, and ISPConfig already created the neccessary Apache db files, and still nothing. [http://shaunsnetwork.com](http://shaunsnetwork.com) :(

~Shaun

---

### Post by koenn on 2008-01-29
from here,  it looks as if you're dns server is unavailable. 
Is it down ? did ahything change in the network ? you're not on a dynamic IP address, are you ? you're still 65.27.97.24 ?

---

### Post by .Shaun on 2008-01-29
I'm going to completely re-install without ISPConfig and try this. I'll keep you posted.

---

