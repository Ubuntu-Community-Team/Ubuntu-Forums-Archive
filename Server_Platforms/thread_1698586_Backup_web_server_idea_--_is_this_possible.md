---
title: "Backup web server idea -- is this possible?"
date: 2011-03-02
forum: Server Platforms
---

### Post by garfonzo on 2011-03-02
Hey Folks:

I have a Ubuntu server running a website for the company I work for. I have it hooked up to a UPS so if there is a power outage, I can safely power down. A power outage occurred this morning and got me thinking, is it possible to have a backup website?

Here's what I'm thinking: 
[LIST]
[*]I currently have the website running off the Ubuntu server in my garage
[*]I have a Windows 7 "server" in a remote office about 1,100 miles away which simply serves files to the LAN (the LAN has a static IP, btw)
[*]When the power goes out at my place, I'd like the website to automatically be served from the Windows machine where, in all likelihood, the power would still be on.
[/LIST]

Is this possible? I would imagine that I would have to have identical websites built and ready to go on both machines and somehow have the domain registrar records setup in a way that it tries the Ubuntu server first, then when that fails, it tries the Windows machine. 

What do you think? Crazy idea? Plausible?

---

### Post by SteveMayne on 2011-03-02
If this is a static site (i.e. no database backend) - or are happy to accept the fact that your backup database may be out of date, then this is no problem at all.  You could rig up your poor-man's HA (High Availability) arrangement by doing the following:

1) Ensure that you have some means to keep your home-based mirror in-sync.  You could do this in a variety of ways depending on the level of volatility of your website, and how important it is that the backup is up-to-date.  You could rig up some simple cron scripts (or scheduled tasks on Windows) to download your website content from the 'master' server on a regular basis.

2) Ensure that your DNS TTL for your website's A record(s) is low, so that if you have an outage, you can change the IP address quickly, and have it propagate in short order.

3) Have another script running from home that monitors your master website, and changes DNS to point to your backup server if it can't establish a connection.

There are far better solutions if up-to-date backups are required etc. - but this would get you going.

Steve

PS - I run a website backup company if you need to make sure your files are kept backed up!

---

### Post by garfonzo on 2011-03-02
> **SteveMayne said:**
> If this is a static site (i.e. no database backend) - or are happy to accept the fact that your backup database may be out of date, then this is no problem at all.  You could rig up your poor-man's HA (High Availability) arrangement by doing the following:

1) Ensure that you have some means to keep your home-based mirror in-sync.  You could do this in a variety of ways depending on the level of volatility of your website, and how important it is that the backup is up-to-date.  You could rig up some simple cron scripts (or scheduled tasks on Windows) to download your website content from the 'master' server on a regular basis.

2) Ensure that your DNS TTL for your website's A record(s) is low, so that if you have an outage, you can change the IP address quickly, and have it propagate in short order.

3) Have another script running from home that monitors your master website, and changes DNS to point to your backup server if it can't establish a connection.

There are far better solutions if up-to-date backups are required etc. - but this would get you going.

Steve

PS - I run a website backup company if you need to make sure your files are kept backed up!

Thanks for the reply. The site is a static site, just a bunch of information about the company. So, a one-off sync of the data should suffice. The thing about the DNS settings is that when you change them, it can take a few days to propagate across the net. This is not useful if the outage would only last for a few hours at most.

---

### Post by SteveMayne on 2011-03-02
> **garfonzo said:**
> Thanks for the reply. The site is a static site, just a bunch of information about the company. So, a one-off sync of the data should suffice. The thing about the DNS settings is that when you change them, it can take a few days to propagate across the net. This is not useful if the outage would only last for a few hours at most.

Ah, you missed my point about TTL (time to live) in your DNS settings.  You can specify how long the records from your DNS server/zone should be cached.  By setting this value low, you'll increase the number of DNS lookups people have to perform, but it means changes will propagate much faster / almost instantly.

Services such as Dynamic DNS use this technique to facilitate DNS entries for people without static IPs.

---

### Post by SeijiSensei on 2011-03-03
If you control both your primary and secondary nameservers, you can use the trick described [here](http://www.wight-hat.com/guides/hosting6.html).  In a nutshell, you host one copy of the website on the primary server and one of the secondary.  On each nameserver the A record for the "www" host points to that machine's IP address.  Then if one machine falls over, new requests will be handled by the other nameserver which will give out its address for the web host.

As Steve says, you need to have short TTLs to make these kinds of solutions work effectively.

---

### Post by garfonzo on 2011-03-03
This is great. It looks like this might be a real solution. Thanks for the help!

To take it a step further, if I also use the server (which hosts the website) as a MySQL database which users log onto and use, is it possible to keep a synced copy of this database on the remote server? 

For example, what if I dropped a Linux box into the remote office (the one 1,100 miles away) and on it I setup the website as a backup (as we discussed already in this thread), but also have a nightly mirrored copy of my MySQL database. Thus, when I have a power outage, employees simply log into the remote server instead of the on in my garage. Is that possible? 

Thanks!

---

### Post by garfonzo on 2011-03-03
Actually, scratch my last post about MySQL. I want to come back to the DNS settings. 

What if I don't have access to the TTL values of the Name Server? Then what? What if I just set up two A records, one for each IP of the two web servers? If I have two A records, doesn't that mean that traffic will simply go to one Server or the Other? Then, if one server goes down, won't all traffic, by default, go to the other server? Or, will the request (by the person trying to surf to my site) simply fail and that's it?

---

### Post by SeijiSensei on 2011-03-04
The process you describe is called "[round-robin]("http://en.wikipedia.org/wiki/Round-robin_DNS")" DNS.  The server gives out a randomly-chosen IP address from a list for each request.  You'd set up the records like this:

```

www     IN     A     10.1.1.1
        IN     A     10.1.1.2
        IN     A     10.100.3.9

```

This works well for load-balancing but not for redundancy.  If 10.1.1.1 is dead, the nameserver will still happily give out this address 1/3 of the time.  

The approach I linked to above uses NS records instead.  If the primary nameserver goes down, DNS queries are routed automatically to the secondary.  If the primary and secondary have different A records for the "www" host, then you'll have redundancy.

As for controlling TTLs, I take it you aren't running your own BIND servers but relying on a DNS host?  Maybe you should have the NS records on your DNS host point to servers you maintain with the actual records.

Finally, in response to your MySQL question, database-driven sites obviously have problems with methods like these to provide redundancy.  Either they share a common database, creating a new "single point of failure," or you need to use replication to synchronize the two database copies.  You'll also need to be careful if you use sessions to track users.  You want to insure that a user stays on the same server throughout.

---

### Post by BkkBonanza on 2011-03-04
If you don't have access to TTL on your name server then consider using a better name server service. Many of them have failover capaibilty built in, although they usually charge for it. ZoneEdit is one that comes to mind that is also very cheap (or free) but has a failover and round robin function, plus full editing of TTL etc.

When you get more advanced with MySql you can use replication to maintain a backup copy on a second server. You can configure PHP (if you use that) session support to store session data in MySql so it is also carried over to the second server. You can automate the failover but if not done carefully it can lead to false events and so you may want to manually failover the mysql. More complex arrangements can also be used  but it can get messy too.

Another tool to consider is configuring and testing a backup server on Amazon EC2 and have it ready to go. When "stopped" it costs almost nothing and can be started in a moments notice and be brought online for temporary periods at very low hourly cost. Very little overhead, and quick availability. I use this now to maintain a somewhat current backup server so if my normal host flakes out I am only minutes away from a ready to go backup server without managing any hardware or second locations. As soon as I start it a secure tunnel for mysql replication starts and updates the database automatically. If my primary server isn't online then I can make a DNS change and have my backup online right away (though usually the data lags since I don't have it update that often - but I could have it scheduled to update very regularly). Just more ideas.

---

### Post by garfonzo on 2011-03-04
> **SeijiSensei said:**
> The process you describe is called "[round-robin]("http://en.wikipedia.org/wiki/Round-robin_DNS")" DNS.  The server gives out a randomly-chosen IP address from a list for each request.  You'd set up the records like this:

```

www     IN     A     10.1.1.1
        IN     A     10.1.1.2
        IN     A     10.100.3.9

```

This works well for load-balancing but not for redundancy.  If 10.1.1.1 is dead, the nameserver will still happily give out this address 1/3 of the time.  

The approach I linked to above uses NS records instead.  If the primary nameserver goes down, DNS queries are routed automatically to the secondary.  If the primary and secondary have different A records for the "www" host, then you'll have redundancy.

As for controlling TTLs, I take it you aren't running your own BIND servers but relying on a DNS host?  Maybe you should have the NS records on your DNS host point to servers you maintain with the actual records.

Finally, in response to your MySQL question, database-driven sites obviously have problems with methods like these to provide redundancy.  Either they share a common database, creating a new "single point of failure," or you need to use replication to synchronize the two database copies.  You'll also need to be careful if you use sessions to track users.  You want to insure that a user stays on the same server throughout.

After I posted, I did a bunch of research and, as you pointed out, realised that what I was describing was a round-robin scenario. This isn't a solution, really, to redundancy. 

What I am unclear about on your post is that you say that if a nameserver goes down, DNS request will be routed through the secondary nameserver. But, in my scenario, I assume that the nameservers (handled and maintained by some other company) are always in working order. I'm concerned with **my** server going down. So, if ip address #1 goes down, I want the name server to stop giving out that IP, and instead give out IP address #2. I believe this is called "DNS Failover".

Am I right in what you are saying?

---

### Post by garfonzo on 2011-03-04
> **BkkBonanza said:**
> If you don't have access to TTL on your name server then consider using a better name server service. Many of them have failover capaibilty built in, although they usually charge for it. ZoneEdit is one that comes to mind that is also very cheap (or free) but has a failover and round robin function, plus full editing of TTL etc.

When you get more advanced with MySql you can use replication to maintain a backup copy on a second server. You can configure PHP (if you use that) session support to store session data in MySql so it is also carried over to the second server. You can automate the failover but if not done carefully it can lead to false events and so you may want to manually failover the mysql. More complex arrangements can also be used  but it can get messy too.

Another tool to consider is configuring and testing a backup server on Amazon EC2 and have it ready to go. When "stopped" it costs almost nothing and can be started in a moments notice and be brought online for temporary periods at very low hourly cost. Very little overhead, and quick availability. I use this now to maintain a somewhat current backup server so if my normal host flakes out I am only minutes away from a ready to go backup server without managing any hardware or second locations. As soon as I start it a secure tunnel for mysql replication starts and updates the database automatically. If my primary server isn't online then I can make a DNS change and have my backup online right away (though usually the data lags since I don't have it update that often - but I could have it scheduled to update very regularly). Just more ideas.

Thanks for the ideas. Interesting, indeed. I plan on contacting my ISP regarding nameserver controls. When they set up my business internet connection, they give me two nameservers to use. However, when I setup my domain, the domain registrar indicated that I had to use their nameservers in order for DNS management to work. 

I suppose what I need to do is setup my domain registrar to use my ISP's nameservers, then use my ISP's nameservers to manage my DNS records. With this setup, I could setup the failover methods you describe in your post. 

I have been looking into paid-for failover services. They come relatively cheap (around $50 for the year) and may be a decent option. I'll look into the provider you mention.

---

### Post by BkkBonanza on 2011-03-04
That's right. Usually with your domain registrar you can change the name servers you use. At least with the ones I've dealt with they have an option in their control panel to set nameservers when you don't want to use the ones they provide. Once you change the namerservers you cannot use their DNS controls but have to use the facility provded at the new nameservers.

---

### Post by SeijiSensei on 2011-03-04
> **garfonzo said:**
> What I am unclear about on your post is that you say that if a nameserver goes down, DNS request will be routed through the secondary nameserver. But, in my scenario, I assume that the nameservers (handled and maintained by some other company) are always in working order. I'm concerned with **my** server going down.

The method I linked to is based on *running your own nameservers on the same hosts* that are providing the web service.  If you intend to rely entirely on third-party nameservers, this method won't work for you.

---

### Post by garfonzo on 2011-03-04
> **SeijiSensei said:**
> The method I linked to is based on *running your own nameservers on the same hosts* that are providing the web service.  If you intend to rely entirely on third-party nameservers, this method won't work for you.

Ah, that makes sense. I was actually looking into running my own nameserver but, meh, if someone else can do it for $50 a year, that is one less thing to worry about.

---

