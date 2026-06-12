---
title: "server 8.10, lamp, dns nameserver question"
date: 2008-11-27
forum: Server Platforms
---

### Post by thebigkraze on 2008-11-27
I have recently completed the perfect server guide [http://www.howtoforge.com/perfect-server-ubuntu-8.10]("http://www.howtoforge.com/perfect-server-ubuntu-8.10") but have hit a wall since trying to link my domain name thebigkraze.com to my ubuntu server set up.  I had the domain name registered at godaddy.com and have since found out how to edit the nameservers for the domain, but don't know what mine would be.  I've looked all around and have registered an account with zoneedit for dns management.

  I always thought that setting the server up was the hard part, but I just don't know how to connect them i guess.  The next question i had was to how to go about actually editing the page.  I'm a complete noob with this and have no idea how to take a web site created with frontpage or something and import it into my servers data.   Anyways,  thanks for any help.

---

### Post by thebigkraze on 2008-11-28
Well i'll try to explain more.. .  From what I understand, bind9 is the program responsible for the DNS server.  The terminal method get's me slightly confused with the status of my server, but typing the server's ip into my browser get's the "It Works" page, which I assume means nothing more than it's running.  After installing MySQL and ISPconfig, I've tried accessing the GUI web page with the server's IP at port 81 but get nothing.  I'm not sure if i should disable the SSL or if that's not the problem.

The domain was purchased from godaddy.com, and I have sense found out how to change the domains nameservers.  After creating my account at zoneedite, i added the provided nameservers to my domain, and now I get an error page.

---

### Post by thebigkraze on 2008-11-28
Alrighty.  I think I'm making some progress.  I've gone through the bind9 documentation and edited the conf files for a primary server.  I can ping thebigkraze.com and get results back with it's local ip shown, but when I try named-checkzone command on thebigkraze.com it returns

NS 'ns.thebigkraze.com.thebigkraze.com' has no address records (A or AAAA)

I thought i added the A record under the reverse zone file, but can't see how ns.thebigkraze.com.thebigkraze.com became one object.

Heres my /etc/bind/db.thebigkraze.com


; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     thebigkraze.com.         root.thebigkraze.com. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.thebigkraze.com
@       IN      A       192.168.1.101
ns      IN      A       192.168.1.101

---

### Post by Coreigh on 2008-11-28
Does your server have internet access and if so how? Is it on a dedicated ISP for the purpose of running servers for internet or is this a home server on a home internet account? What you have to do to make your serve available on the internet differs based on which scenario you are following.

---

### Post by thebigkraze on 2008-11-28
It's just for a home server.  My isp is comcast and there are comcast DNS servers listed under my router's page.  I wasn't sure to use those because I thought those were comcast's, and not the bind9 server I have.  If those are good, would I simply put two of theme into the nameservers option at godaddy.com  and then would my server pick it up from my isp to host the site?

---

### Post by andguent on 2008-11-29
I would give this link a good read. It sounds like someone else is working through the same issues you are. Make sure you scroll ALLLLL the way to the bottom to read the thread.
[http://www.experts-exchange.com/Web/Hosting/Q_21113070.html](http://www.experts-exchange.com/Web/Hosting/Q_21113070.html)

The long and short of it is I don't think you need your own DNS server. You can run one if you want.

---

### Post by thebigkraze on 2008-11-30
alrighty.  so after much time roaming around godaddy.com's terribly ambiguous site, i found out how to register my dsn server ns.thebigkraze.com with my routers external ip address.  I'm guessing that the domain is now linked with my dns nameserver by tying it to my router's ip, and thus the bind9 dns server on my network?   Kind of going at this blindly.  Assuming this is what I needed to do, anyone able to point me in the right direction to start developing a web page and uploading it to my server here?  I assume it has something to do with Apache...there isn't a whole lot out there on the complete process from hosting to designing...

---

### Post by andguent on 2008-12-01
Some questions before we can really get into the meat of the setup:
* Does your Comcast Internet connection have a static IP? If you don't know, or it does not, then hosting a webpage on it gets more complicated.
* Do you know for sure that Comcast will not block web server traffic? It wouldn't surprise me if they do. They have had issues in the past with viruses creating mail servers and started blocking that.
* Is it safe to assume that you definitely do want this website accessible for all the world to see? You sound like you know what you are doing, but I have to ask just to confirm.
* What ports have you already opened on your comcast modem/router to allow outside access into your network?

My recommendations for next steps are as follows:
* Leave the forwarding ports closed on your router for now. See below.
* Research very heavily how to harden & secure an Apache setup. Apache is indeed the recommended web server program to use when hosting a site off of your own Linux box. Unfortunately it does definitely have some known security holes that can be resolved if you know what you are doing. I am not an expert at Apache, but googling 'apache harden security' should give you some good info.
* On your server, experiment with the contents of /var/www. I personally would move the apache-default directory to apache-default.original-junk and create /var/www/index.html. It doesn't even need html code, just a Hello World will work for now. Verify you can view this new page when you point a web browser to your server while on your internal network.

Let us know when you get that far.

---

### Post by thebigkraze on 2008-12-02
hmm.  It doesn't seem as though my residential service offers static IP.  Does this mean I'm s.o.l. or do services such as DyneDNS offer the correct nameserver resolution I need.  Not sure if this is similiar to the ZoneEdit.com account I have now.  Also, when I type in the local ip address of my server I see the html code present in the www/ folder.  I"m guessing this mean it's working fine and I just need my DNS problems fixed.  I've looked over some security for Apache and some other things, I think some of that was included in the perfect server guide I followed.

---

### Post by andguent on 2008-12-04
> **thebigkraze said:**
> hmm.  It doesn't seem as though my residential service offers static IP.  Does this mean I'm s.o.l. or do services such as DyneDNS offer the correct nameserver resolution I need.  Not sure if this is similiar to the ZoneEdit.com account I have now.
You definitely should sign up for a free DynDNS account, or competitor. There are probably 5+ companies that do this type of service. Keep in mind that with a changing IP address, your website won't be consistently up. All you need is a 30 second power outage, and your website may be down for 24 hours while DNS updates.

>   Also, when I type in the local ip address of my server I see the html code present in the www/ folder.  I"m guessing this mean it's working fine and I just need my DNS problems fixed. 
This means that Apache is configured properly for basic serving needs. I still would consider leaving your firewall forwarding ports closed until you have most everything else in place.

>  I've looked over some security for Apache and some other things, I think some of that was included in the perfect server guide I followed.
Good. Just know that there always is a vulnerability somewhere in something, its just a question of who finds it, and how quickly until you patch it. Apache really isn't bad at all compared to the competition, but I would hate to see your server hacked.

I highly recommend setting up your web server so it cannot access the Internet directly. With firewall software, you can set it so that it can respond to web page requests it is asked for, but not be able to start pulling files from the Internet on its own. This is just a standard safety thing, but causes inconvenience later.

---

### Post by theozzlives on 2008-12-04
> **thebigkraze said:**
> I have recently completed the perfect server guide [http://www.howtoforge.com/perfect-server-ubuntu-8.10]("http://www.howtoforge.com/perfect-server-ubuntu-8.10") but have hit a wall since trying to link my domain name thebigkraze.com to my ubuntu server set up.  I had the domain name registered at godaddy.com and have since found out how to edit the nameservers for the domain, but don't know what mine would be.  I've looked all around and have registered an account with zoneedit for dns management.

  I always thought that setting the server up was the hard part, but I just don't know how to connect them i guess.  The next question i had was to how to go about actually editing the page.  I'm a complete noob with this and have no idea how to take a web site created with frontpage or something and import it into my servers data.   Anyways,  thanks for any help.

Your registrar should be able to send your domain to your IP (but you need a static IP). You just use your router to forward requests to whatever local IP your server is on. That's how I setup my site.

---

### Post by Presto-X on 2009-01-18
Hello thebigkraze,

I am also trying to get a domain working with my ubuntu server, I also used Comcast's residential internet service, but I had to signup for Comcast's business class service this week to get a static ip, Comcast blocks port 53 and a few others so that home users to do not setup servers at home. This is why they offer business class service, faster plus you get a static ip address.

---

