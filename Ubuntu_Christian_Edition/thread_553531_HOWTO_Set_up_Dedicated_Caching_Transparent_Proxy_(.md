---
title: "HOWTO: Set up Dedicated Caching Transparent Proxy (with Dansguardian) Server at Home"
date: 2007-09-17
forum: Ubuntu Christian Edition
---

### Post by tak1150 on 2007-09-17
After some struggles (see [this thread]("http://ubuntuforums.org/showthread.php?t=525502") for some of the history behind it), I have been able to set up a dedicated proxy server that runs Dansguardian.

What this server will do is that all the client PC's will have to go through the Dansguardian proxy server so that they have no choice but to have filtered Internet access. I found that web browsing is somewhat faster now due to a) the Internet filtering is no longer done locally but at the server b) the proxy server also does caching of web files and DNS lookups.

I mainly wanted to set this system up so that when I extend my wireless network to a neighbor that I'm trying to help (long story; you can see the thread mentioned above), he will have "clean" Internet access (plus the added benefits mentioned earlier).

[The howto article is right here.]("http://taksuyama.com/?p=16#more-16")

I can answer questions you may have (as much as possible) here in the thread or on my website.

I see this system as a benefit even for single men that may be struggling with pornography. Since the filtering program is on a dedicated server, it is much more of a hassle to disable it should you be tempted (see the figure below). Moreover, if you have your friend administer this system (or just simply give the root pw to them after you set it up), it'd be (virtually) an uncompromisable system while you have full root access on your regular-use computer ;)

[IMG]http://taksuyama.com/images/proxy_server_hardware_config.png[/IMG]

God bless,
Tak

---

### Post by tak1150 on 2007-09-20
Below is a post from the thread I mentioned above. I decided to reply to here b/c it's more relevant to this thread.

> **shane2peru said:**
> Tak  I have been reading this thread for the learning aspect of it.  Very interesting.  Now we are venturing off topic a bit and I apologize, but I didn't want to start a new thread just for this simple question.  In theory then with a proxy, everything that connects to the web through the proxy would be protected (as far as firewall, as well as content filtering)  am I correct in assuming this?  This would make a very secure setup for 3 computers in one house that connect to the web (2 linux computers and one windows computer)  as well as making it easier to have my home network all setup???  Because the proxy would eliminate any potential security threat of being attacked from the web side?  (of course nothing can protect stupidity and opening things that will mess your computer up on the user side)  I'm liking this solution as well as the filtering on a proxy level rather than an individual computer basis!  Very nice how to on your web page too, I'm still reading through it.  My only problem is finding a cheap computer here in Peru (I'm a missionary in Peru).  Very interesting.  Thanks for the info!

Shane

With the system you'd make following my how-to, the only web traffic (ie www, of http traffic) that is allowed by the firewall has to go through the proxy. And the proxy hands all the http traffic to Dansguardian. So port 80 stuff is all filtered through Dansguardian.

All outgoing traffic are allowed by the setting I have in the how-to article, which may not be secure enough for some people, which I personally don't think is that big of a deal unless you're in danger of getting spyware and such.

The only other incoming traffic allowed are the SSH port, Pinging, and TCP port 88 for my web server. My ISP blocks incoming TCP 80, and to be able to view something on my web server, I use TCP port 88 instead of 80.

Also included in the how-to article is "denyhosts" which is a great program that protects your SSH server from brute force attacks.

Sorry if I didn't answer your questions. If I didn't let me know. I'm always honored to help people in ministries.

Tak

---

### Post by shane2peru on 2007-09-20
> **tak1150 said:**
> Below is a post from the thread I mentioned above. I decided to reply to here b/c it's more relevant to this thread.



With the system you'd make following my how-to, the only web traffic (ie www, of http traffic) that is allowed by the firewall has to go through the proxy. And the proxy hands all the http traffic to Dansguardian. So port 80 stuff is all filtered through Dansguardian.

All outgoing traffic are allowed by the setting I have in the how-to article, which may not be secure enough for some people, which I personally don't think is that big of a deal unless you're in danger of getting spyware and such.

The only other incoming traffic allowed are the SSH port, Pinging, and TCP port 88 for my web server. My ISP blocks incoming TCP 80, and to be able to view something on my web server, I use TCP port 88 instead of 80.

Also included in the how-to article is "denyhosts" which is a great program that protects your SSH server from brute force attacks.

Sorry if I didn't answer your questions. If I didn't let me know. I'm always honored to help people in ministries.

Tak

Thanks Tak a lot of great info here and very helpfull!  I will be looking into this, for me this is a great security measure as well as good protection using Dan's Guardian!  I'll be on my hunt for a very cheap computer.

Shane

---

### Post by jonathonblake on 2007-09-20
Something I didn't see mentioned, was how to configure the DNS server to block/redirect "bad" IP addresses/domains.

The advantage here is that directly entering the IP of the site won't get to the site.  In some circumstances, Dansguardian will allow the site to be accessed, if the IP address is used, even if the domain not is blocked.

On a more personal note, I prefer to simply toss URLs and IP addresses into a configuration file, and create a dummy host on an internal box. (But then I cut my DNS teeth with Cricket's book on one hand, and his mailing list in the other hand. An old 386 box running Redhat 5.0 serves nicely for "dummy" sites.)

xan

jonathon

---

### Post by tak1150 on 2007-09-21
jonathonblake,

thanks for replying. IP's and URL's can be specifically blocked in the /etc/dansguardian/bannedurllist and bannediplist (sorry if I remember the exact file names wrongly). I don't know of a way to do that with DNS server.

---

### Post by tak1150 on 2007-09-21
Shane,

I just saw your website. May God bless and anoint you bountifully and may many souls be won through you and those you equip to be ministers in Peru.

sorry - off topic i suppose.

Tak

---

### Post by jonathonblake on 2007-09-21
> **tak1150 said:**
> I don't know of a way to do that with DNS server.

Edit named.conf,by adding both the Zone for the domain and in-addr.arpa data.
Then configure etc/hosts on the "dummy sites" box.
Then configure apache to serve up the appropriate message.

The "dummy sites" box must be within the DMZ, 

xan

jonathon

---

### Post by shane2peru on 2007-09-22
> **tak1150 said:**
> Shane,

I just saw your website. May God bless and anoint you bountifully and may many souls be won through you and those you equip to be ministers in Peru.

sorry - off topic i suppose.

Tak

Thanks Tak.

Shane

---

### Post by tak1150 on 2007-09-28
Somebody just informed me that there were dead links (the[ Dansguardian]("http://taksuyama.com/?page_id=28") page and the [Extra Feature]("http://taksuyama.com/?page_id=30") page). Indeed they were dead! Apology to anybody that may have been frustrated by this.

Also, to answer some questions I received in the PM;

> does the shorewall take the place of the iptables (access control lists?) and bridging that other walkthroughs have? 

Shorewall is a program that simply writes the iptables commands for you. So technically it is not a firewall program. Your iptables is still the firewall. I probably should've mentioned that in the article.

> 
And secondly, is there any way to test parts of the system, for when it doesn't work. For instance, is there a way I incramentally test the parts to see where my problem is? I realize this might require temporarily changing the configs so a computer could test the proxy alone, or the filter, or whatever.
Any tests you do (pings, tcpdump, telnets, etc..) would be appreciated.

For the most part, when you restart each service and not get any errors, then it should be fine. To test your security, you could look into using [nessus]("http://www.nessus.org/nessus/"), which I have used before.
To test that Dansguardian/Squid are working, I usually just make the web browser window small so that in case the filtering doesn't work I won't accidentally see the abomination and just type into the address bar a web address that is obviously porn of some sort and it should filter the page.
I hope I kind of clarified some things. If anybody has any more questions, let me know.

---

### Post by Jake28 on 2010-09-29
To set this up on a home network would you have one Ethernet card from your server connected to your cable modem and the other network card connected to the "internet" port of your wireless router?

---

