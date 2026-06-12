---
title: "SSL Encryption at Proxy or Web server level?"
date: 2019-08-07
forum: Server Platforms
---

### Post by LHammonds on 2019-08-07
I can imagine there are not many people here that handles such a scenario but thought I'd ask anyway.

I am working on documenting a highly-available web platform design such as the image below.

Let's Encrypt (certbot) will be used to automatically renew SSL certificates for various websites.

The SSL certificate can be used / terminated at the proxy level but you kinda have to do backflips to do certificate renewals when doing at the proxy level.

One could also do the SSL renewal process at the web server level which keeps it fairly standard in how certbot works out-of-the-box but you do have to temporarily disable the other web nodes while it does the renewal process to ensure it reaches the correct webserver during the authentication process.

I am leaning towards running certbot at the web server level once per month.

***Anyone out there do this and have any advice on which way they decided to go and why?***

Thanks,
LHammonds
[IMG]https://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/IMG]

---

### Post by TheFu on 2019-08-07
Right? How many people here do HA ...   you and me, perhaps 5 others?

I do it at the reverse proxy servers with downtime.  I didn't want to be forced into having all the public web services actually directly available to the public internet, whereas the reverse proxy servers already where and have DNS records to hit both - so it is active-active, not active-failover.  If the reverse proxy systems have to be in different physical locations so they work for DR needs too, the active-failover is a good, cheap solution.

I use the **acme.sh** script and the built-in web server it provides to do new and renewal certs.  The only trick is that the reverse proxy servers have to be off for the new cert period.  Let me check my notes ... 

```
sudo service nginx stop  # stop on rp1 and rp2

for D in "www-1  www-2  www-3  www-4  www-5  www-6  www-7  www-8  www-9  www-10  www-11  www-12  www-13  www-14  www-15  www-16  www-17  www-18  www-19  www-20" ; do 
   DOMAIN=$D.example.com
   sudo ./acme.sh --renew -d $DOMAIN --standalone
   # Deploy cert
   sudo ./acme.sh --install-cert -d $DOMAIN \
               --cert-file /etc/nginx/ssl/$DOMAIN/cert.pem \
               --key-file /etc/nginx/ssl/$DOMAIN/key.pem \
               --fullchain-file /etc/nginx/ssl/$DOMAIN/fullchain.pem
done;
sudo rsync -avz /etc/nginx/ssl/   deploy659@rp2:/etc/nginx/ssl/   # deploy account is root-equiv/could use the backup account instead

# restart on rp1 and rp2
sudo service nginx start

```
I don't trust this script to be run directly yet. I've not used it for renewals.  Did use something similar for the initial requests after fighting with certbot and acme.sh the last 3 renewals.  Manual copy/paste each line at this point.  My next use will be in about 3 weeks.  My certs expire in early Sept.

This way, the web servers don't have to be touched, just the reverse proxies.  But that only works if the connection between the proxies and real web servers isn't at risk for network highjacking (basically on the same physical LAN) or the connections were going through a strong VPN.   I need to think about that a little longer, as I'm planning to move some of my gateway and proxy servers to public VPS locations, while retaining the real servers under physical control.  And be certain that you enable micro-caching on the reverse proxy systems.  It is crazy how much a 0.2-1 sec cache helps performance with the systems start getting hammered.

I did have fewer certs originally.  Merged 3-5 into a single request, but I found that web spammers were using the cert records to find unpublished sites to hit. Switched to 1 site, 1 cert last renewal.  The unwanted hits stopped.

I haven't had to setup DBMS HA in over a decade.  I'd probably do it using sheepdog n+1 block replication because my current DBs are low transaction and run in KVM VMs.  Previously used shared RAID storage, BCVs, and log replication.  I'd use log replication if I needed higher transaction support than the block replication handles, perhaps with A-->B-->ReportingDB tiered replication.  But I haven't researched it too much in recent years.

---

### Post by LHammonds on 2019-08-08
Thanks for the info.  The complete separation of user and backend server sounds interesting but I don't like the sound of downtime.  My method so far only has backend web server capacity shrink from N to 1 during the time I do the certbot renewal once a month and it is fully automated.  I'm currently documenting how I setup the [MariaDB Cluster]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=262") and the [Load Balancing front end]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264") if you want to look through it...but it is not finalized yet.  When I complete it, I will create a duplicate post on this forum for discussions.

---

### Post by LHammonds on 2019-08-09
I have found a very-specific reason to terminate SSL at the proxy level and there is no other way around it.

Client IP logging.  This CANNOT be done if the packets are encrypted all the way to the web server.

When using HAProxy, you can set the mode to HTTP and utilize the "option forwardfor" but if using SSL and TCP mode, you cannot access/modify any headers and thus your web logs will only ever show client connections as if originating from the proxy server.

I might continue to document how I do this with SSL terminating at the web server and just keep a record of advantages / disadvantages of doing it this way....then maybe create another document showing how to do the same thing but terminate SSL at the proxy.  Jeez...if only I got paid for this stuff. hehehe.

LHammonds

---

### Post by TheFu on 2019-08-09
I've never used HAProxy.
Are you certain that HAProxy won't pass the original IP through?  
nginx will.
```

                proxy_set_header  X-Real-IP  $remote_addr;
                proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
```

IPs are outside any HTTPS encryption, unless using Tor or a VPN based on SSL.

---

### Post by sevendogs1337 on 2019-08-09
Not sure what you mean by "complete separation of user and backend server". Do you mean separate web and db tiers as in your drawing?  If so, that is the ONLY way to securely set up a web app.

---

### Post by LHammonds on 2019-08-09
> **sevendogs1337 said:**
> Not sure what you mean by "complete separation of user and backend server". Do you mean separate web and db tiers as in your drawing?  If so, that is the ONLY way to securely set up a web app.Sorry, I did not word that well.  I'm talking about the SSL connection from the user's browser and where it terminates.

If you terminate the SSL at the proxy level, the web traffic is decrypted from port 443 and THEN routed to the web server on port 80.

If you terminate the SSL at the web server levels, the web traffic is decrypted directly at the web server and thus, the web server itself is running on port 443.

And the only way one can really "secure a web server" is to lock it in a room and remove all remote and physical access to said server (granted, a talented thief can still gain physical access). ;)  Granting various ways to access that device is all about mitigating risk as you increase the attack surface to reach a happy compromise between accessibility for intended users and risk of successful hacks.

LHammonds

---

### Post by sevendogs1337 on 2019-08-09
I got it, thanks for the clarification. I come from the gov IT world where E2E encryption is the standard. So all channels are encrypted. At a bare minimum, obviously browser to proxy because then you are in a controlled environment at that point, but if you can do TLS all the way back to the actual we server to prevent sniffing, why not. Not saying that is perfect, but it's a mitigation.

---

### Post by LHammonds on 2019-08-09
> **sevendogs1337 said:**
> I got it, thanks for the clarification. I come from the gov IT world where E2E encryption is the standard. So all channels are encrypted. At a bare minimum, obviously browser to proxy because then you are in a controlled environment at that point, but if you can do TLS all the way back to the actual we server to prevent sniffing, why not. Not saying that is perfect, but it's a mitigation.E2E is how I'm going to document this initially but it is irking me to lose the client IP in the web logs.  I can make it work without SSL but there is no point since you want to route all client web servers over SSL.  You lose your demographics in log reports and even lose out on some security features such as fail2ban blocking failed web login attempts.

LHammonds

---

