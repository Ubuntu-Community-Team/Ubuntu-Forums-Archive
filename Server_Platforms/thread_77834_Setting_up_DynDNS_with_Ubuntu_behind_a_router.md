---
title: "Setting up DynDNS with Ubuntu behind a router"
date: 2005-10-17
forum: Server Platforms
---

### Post by Randall311 on 2005-10-17
Hi everyone,
I am trying to set up DynDNS on my newly installed Ubuntu 5.10 "Breezy Badger" on a pentium III PC. My PC is behind a Linksys WCG200 router.  The router is an all-in-one solution with cable modem, wireless 802.11 g, and router built in.   I have installed apache2 webserver (default port 80) and my router configured to port-forward all traffic on port 80 to my computer's router assigned IP address: 192.168.0.13.  I have installed the dyndns helper script called ddclient, which seems to be working properly. I also have DHCP configuring my connection both on the router, and my PC's network device (eth0) I cannot do a static IP address, because my ISP assigns the IP via DHCP.  I have bind9 installed to map the DNS also.  The dyndns address that I am trying to use is [http://randall.kicks-ass.org](http://randall.kicks-ass.org) Whew... here is my problem:

The server times out.  

When I run traceroute for my routers external IP address I get the following... 

>> traceroute 65.174.54.136
```
Host  	Packet loss 	rec.	sent 	Best(ms) Avg(ms) Worst(ms)
66.92.0.1  	0%  	1  	1  	540.96  540.96  540.96
69.17.83.181 	0% 	1 	1 	581.71 	581.71 	581.71
209.249.11.177 	0% 	1 	1 	518.60 	518.60 	518.60
64.125.28.222 	0% 	1 	1 	515.68 	515.68 	515.68
64.125.30.2 	0% 	1 	1 	530.48 	530.48 	530.48
64.125.30.177 	0% 	1 	1 	481.54 	481.54 	481.54
64.125.12.90 	0% 	1 	1 	475.53 	475.53 	475.53
66.28.4.134 	0% 	1 	1 	506.00 	506.00 	506.00
66.28.4.69 	0% 	1 	1 	457.65 	457.65 	457.65
66.28.4.186 	0% 	1 	1 	499.53 	499.53 	499.53
66.28.4.109 	0% 	1 	1 	483.50 	483.50 	483.50
66.28.5.130 	0% 	1 	1 	457.06 	457.06 	457.06
38.112.24.210 	0% 	1 	1 	466.39 	466.39 	466.39
    ???       100% 	0 	1 	0.00 	0.00 	000
```

I get the same results with traceroute randall.kicks-ass.org.

I've tried to follow all of the instructions at [http://www.howtoforge.com/book/print/59](http://www.howtoforge.com/book/print/59) on how to set up my server to be public.  I have not been successful thusfar, but I don't want to give up hope.  

If any of you have suggestions on how to get my router accepting incomming requests (as I think this is were the problem lies) then I would be most appreciative.  

-Justin

---

### Post by Randall311 on 2005-10-17
Sorry if this is confusing anyone.  Basically I'm just trying to figure out why the server is not responding (timed out) and if I can do anything about it.

---

### Post by cheredenine on 2005-10-18
I have a very similar set-up to you - Ubuntu box running Apache behind a router over a broadband connection with a dynamically assigned WAN IP address.  I use DDclient as well and it all works a treat.

I had a thought about the problems you're experienced - it might be an obvious one you've already checked, but its worth mentioning.  You obviously own the randall.kicks-ass.org domain, but is this correctly set to point to your DynDNS account address?

To give you an example:  I own a domain (cheredenine.co.uk), this is set to redirect to my DynDNS account domain (cheredenine.dnsalias.org), which is in-turn set via the updates from DDClient to redirect web traffic to my routers dynamic IP address.  Sounds like its that first step thats missing in your case...

---

### Post by Randall311 on 2005-10-18
Hi cheredenine, thanks for your reply.  Unfortunately I don't own the randall.kicks-ass.org domain, it is just my dyndns account.  ;)  It looks at first glance that my cable internet provider (Norwood Light Broadband) is blocking any pings to my address via firewall.  I'm not sure if there is anything I can do about it.  Here is the output for a tracetoute using dnsstuff.com. I can ping the address from within my home network, but it just times out when I'm outside. [http://www.dnsstuff.com/tools/tracert.ch?ip=randall.kicks-ass.org](http://www.dnsstuff.com/tools/tracert.ch?ip=randall.kicks-ass.org)

---

### Post by cheredenine on 2005-10-18
oops - my mistake.  Having gone for a plane DynDNS address I didn't realise that kick-ass.org was a domain they offered!  Apologies for any confusion!

I had a play with that DNS site you mentioned and got the following result when pointing it directly at my DynDNS account address:
[http://www.dnsstuff.com/tools/tracert.ch?ip=cheredenine.dnsalias.org](http://www.dnsstuff.com/tools/tracert.ch?ip=cheredenine.dnsalias.org)

The interesting points are hop 13, which doesn't respond, and hop 14, that does.  If i'm interpreting it correctly, hop 13 is the router doind its firewall job correctly, and hop 14 is my webserver.  When i set up my router i had to adjust settings in two areas - not only is it set to redirect port 80 traffic to the IP of my webserver, but the firewall settings also had to be adjusted to allow incoming traffic on port 80 through the firewall.  
Perhaps a double check of your router settings is in order? The notes at the bottom of your DNS test seem to suggest that the problem exists at hop 15 and subsequnet hops may be misleading - if your router's firewall isn't correctly configured maybe its rejecting all incoming traffic and causing the problems.

---

### Post by Randall311 on 2005-10-18
hmm Interresting points.  I do have port forwarding on port 80 enabled on my router, but perhaps my router's firewall is blocking this traffic.  Also another possibility is that my ISP is blocking incomming requests at port 80.  If that is the case, I wonder if maybe I can configure apache to listen on an arbitrary port like 4000, and set up port forwarding on 4000 as well.  I will try these things tonight when I get home.  Hopefully I will get different results.  Thanks for the advice. I will post back with results.

---

### Post by cheredenine on 2005-10-18
Good luck!  If your ISP is the root of the problem then redirecting http traffic to a port other than port 80 is, like you suggest, a valid option -never tried it myself, but heard it mentioned and theres no reason why it shouldn't work.  You'll just need to reconfigure Apache to 'listen' on the alternate port..

---

### Post by Randall311 on 2005-10-19
Unfortunately I was unsuccessful last night :(  I thought that if I used a different port I could get though, but I have the same dead end tracert going on (packets lost after they hit my ISP's hop.)  In the meantime I've configured PHP and MySQL to run a photo album on my server (in hopes that someday I'll figure out how to get it running to the outside world.)  I haven't given up yet, but it is very frusturating to say the least.  Thanks for your help and suggestions so far, I appreciate it very much. :)

---

### Post by strikeforce on 2005-10-19
Does it work if you put your current ip address in the title bar.  If it does then more then likely its a dns issue.

I run strikeforce.dyndns.org and I have a dynamic ip as well so I use ddclient to update my ip address information.  Its possible that your isp is blocking port 80 for viruses.

My ISP did this and I turned that off since my firewall takes care of that.  If you want to run it on a different port its under your config settings.  After that you need to point it to [www.mywebsite.com:portnumber](www.mywebsite.com:portnumber) since browsers default to 80 I believe.

---

### Post by Randall311 on 2005-10-20
SUCCESS!!! Ah sweet success!  Thank you cheredenine and strikeforce for your support.  Finally, I was able to set up Apache to listen on port 4000 (non standard port) because sure enough my ISP blocks port 80.  My tracert now works, and my website is up and running! :D  (right now I just have a stupid portal up, but that will change soon.  Thank you all so much for your help!

I did it like this...

In the apache config file httpd.conf instead of just Listen 80... I now have

listen localhost:80
listen localhost:4000
listen 192.168.0.13:80
listen 192.168.0.13:4000
listen 65.174.54.136:80
listen 65.174.54.136:4000

sweet!!!

---

### Post by cheredenine on 2005-10-21
Ahhh.. Good news!  Sites looking good - you're using a similar colour scheme to my site ([www.cheredenine.co.uk](www.cheredenine.co.uk) for a shameless plug) but with a bit more content.  Glad to hear you got it working despite your ISP's best efforts!

---

### Post by Randall311 on 2005-10-21
Haha yes I defeated my ISP!  Thanks to your help.  I appreciate it.  Yeah when I looked at your site I noticed a similar color scheme by coincidence.  Great minds think alike. Good luck with your web developing.  Your site is looking good too.  I think I'm going to try to host a forum and picture gallery on mine.  I love PHP!!  Cheers.

---

### Post by Z3K3 on 2005-10-26
Ok,

The reason that this borks initially, where you can only browse to [http://localhost](http://localhost) but pages are not displayed when browsing to [http://you.isp.ip.address](http://you.isp.ip.address) is because apache2 is setup to listen to IPv6 by default, and since most people do not use IPv6 in home, they use IPv4 (ip.ip.ip.ip) it will not display the site.

The fix is even simpler than above.

edit your /etc/apache2/ports.conf

change from:
Listen 80
to
Listen 0.0.0.0:80

restart apache2

It will now listen for requests on IPv4, which will allow your page to work from outside the router.

FYI: I found this info here:

[http://lists.debian.org/debian-apache/2005/06/msg00029.html](http://lists.debian.org/debian-apache/2005/06/msg00029.html)

Looks like they are working on an upstream patch that will set it back to IPv4 by default.

Cheers

Z3K3:cool:

---

### Post by Jad on 2005-10-26
How about the NAPT settings?

---

