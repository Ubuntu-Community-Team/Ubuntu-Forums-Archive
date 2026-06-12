---
title: "Disguise Your IP address"
date: 2010-02-27
forum: Security
---

### Post by Richiegs on 2010-02-27
I wonder if there is any program in Ubuntu (Hotspot Shield in Windows) which works well to disguise my true IP address. I tried Tor, but it was excessively slow. Thanks

---

### Post by HermanAB on 2010-02-27
You either need to tunnel (VPN or Socks) to a server somewhere else, or use tor.

---

### Post by Jekshadow on 2010-02-27
> **Richiegs said:**
> I wonder if there is any program in Ubuntu (Hotspot Shield in Windows) which works well to disguise my true IP address. I tried Tor, but it was excessively slow. Thanks

Hotspot shield works by routing your traffic through their servers, and is basically a VPN. If you want a nice VPN, I recommend checking out Ipredator ([https://www.ipredator.se/?lang=en](https://www.ipredator.se/?lang=en)). I have not used it personally, but good friends of mine have told me it works well.

Ipredator uses the PPTP VPN protocol, which can be used under Ubuntu. There is a nice guide on ubuntu geek, [http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html](http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html).

---

### Post by bodhi.zazen on 2010-02-27
> **Richiegs said:**
> I wonder if there is any program in Ubuntu (Hotspot Shield in Windows) which works well to disguise my true IP address. I tried Tor, but it was excessively slow. Thanks

IMO your IP address can always be traced.

---

### Post by ApEkV2 on 2010-02-27
There aren't enough people sharing their bandwidth for tor circuits.

---

### Post by ld.4lpha on 2010-02-28
> **bodhi.zazen said:**
> imo your ip address can always be traced.

+1

---

### Post by iwc5893 on 2010-02-28
> **bodhi.zazen said:**
> IMO your IP address can always be traced.

Yep, it's just a matter of how much time and effort somebody wants to put into it.

---

### Post by rookcifer on 2010-03-01
> **iwc5893 said:**
> Yep, it's just a matter of how much time and effort somebody wants to put into it.

In the case of Tor, it would take someone like the NSA to track it, and even then the job would be very difficult and cost a lot of money (if it could be done at all, which I am doubtful of).

---

### Post by Richiegs on 2010-03-03
> **Jekshadow said:**
> Hotspot shield works by routing your traffic through their servers, and is basically a VPN. If you want a nice VPN, I recommend checking out Ipredator ([https://www.ipredator.se/?lang=en](https://www.ipredator.se/?lang=en)). I have not used it personally, but good friends of mine have told me it works well.

Ipredator uses the PPTP VPN protocol, which can be used under Ubuntu. There is a nice guide on ubuntu geek, [http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html](http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html).

Which one is better, Tor or Ipredator?

---

### Post by rookcifer on 2010-03-03
> **Richiegs said:**
> Which one is better, Tor or Ipredator?

If you just want to hide your IP from a website and don't care if someone in the "middle" knows your real IP, then a VPN like Ipredator or Xerobank will be fine.  Remember the VPN will always have your personal info and thus can trace your true identity if approached by an outside party.

If you want the best anonymity possible (without breaking the law), Tor is the best bet.  Since there is no "man in the middle" that knows your real IP, it is not possible for someone to "back track" you through Tor.  Why?  Because the connection is encrypted along all the hops and all the hops are chosen randomly with each hop not knowing what the next hop is.  In order for you to be compromised on Tor, all 3 hops would need to be under the control of the same entity and this is extremely unlikely.  The main problem with Tor is that it's slower and some websites have banned connections originating from it.

---

### Post by Kinstonian on 2010-03-03
I haven't read the paper, but TOR has apparently had [problems](http://yro.slashdot.org/article.pl?sid=07/02/25/1913219) in the past, and I'd bet it will have problems in the future.

For example, AFAIK, if someone configures TOR to be an exit node, they can view all unencrypted traffic.  So you're open to eavesdropping/MITM attacks.  They could also act as a proxy and insert malicious mobile code in HTTP traffic such as JavaScript to reveal your IP.  Which is why I think it's important to use something like NoScript, and not expect 100%  security/anonymity in anything.  I doubt even the developers of TOR will say it offers complete anonymity.

---

### Post by Dayofswords on 2010-03-03
if you learn about how the internet works, and how tcp/ip works, your ip is findable, no doubt about it, i mean your isp knows who you are, exactly which ip you are and how long you have even used that ip

---

### Post by supershin on 2010-03-03
[https://www.torproject.org/download-unix.html.en]("https://www.torproject.org/download-unix.html.en")

Read the warning on that page. Just enabling tor doesn't protect you.

---

### Post by rookcifer on 2010-03-04
> **Kinstonian said:**
> I haven't read the paper, but TOR has apparently had [problems](http://yro.slashdot.org/article.pl?sid=07/02/25/1913219) in the past, and I'd bet it will have problems in the future.

For example, AFAIK, if someone configures TOR to be an exit node, they can view all unencrypted traffic.  

Yes, everyone knows this.  The Tor project has *never* claimed that Tor offers privacy.  It does, however, offer anonymity.  There *is* a difference in the two terms.  One should never give any personally identifiable info over a Tor connection, and one should never login to any website over Tor unless the website uses SSL.

And, btw, it is impossible for Tor (or any other technology) to encrypt the whole Internet end-to-end.  It's simply impossible without being in control of the destination and the source.  This is *not* a "weakness" with Tor -- it is simply a case of people not understanding basic networking and then blaming Tor for shortcomings Tor never claimed to solve in the first place.  Sadly, most people who dispute the efficacy of Tor make these common errors.

> So you're open to eavesdropping/MITM attacks.  They could also act as a proxy and insert malicious mobile code in HTTP traffic such as JavaScript to reveal your IP.  

Easily fixed by turning Javascript off or using Torbutton (which the Tor documentation clearly recommends).

> Which is why I think it's important to use something like NoScript, and not expect 100%  security/anonymity in anything.  I doubt even the developers of TOR will say it offers complete anonymity.

No, they don't claim it's perfect, but it's definitely the best (legal) means to obtain a reasonable level of anonymity.

> **Dayofswords said:**
> if you learn about how the internet works, and how tcp/ip works, your ip is findable, no doubt about it, i mean your isp knows who you are, exactly which ip you are and how long you have even used that ip

What the ISP knows is irrelevant here.  Tor protects against what they can and cannot know about the sites one visits.  All the ISP can see is that one connected *to* a Tor node -- it cannot see what the destination was.  And the destination website cannot see what the real originating IP was.  Indeed, the destination site cannot even see what the originating Tor node IP was.

Barring any configuration errors, the only reliable way to track someone through Tor is to own all 3 nodes along the path -- and that is extremely unlikely due to the sheer number of nodes.

---

### Post by Richiegs on 2010-03-04
If you want the best anonymity possible (without breaking the law), Tor is the best bet.  Since there is no "man in the middle" that knows your real IP, it is not possible for someone to "back track" you through Tor.  Why?  Because the connection is encrypted along all the hops and all the hops are chosen randomly with each hop not knowing what the next hop is.  In order for you to be compromised on Tor, all 3 hops would need to be under the control of the same entity and this is extremely unlikely.  The main problem with Tor is that it's slower and some websites have banned connections originating from it.[/QUOTE]

Since Tor is the best software for anonymity and is very slow, I am curious what softwares do hackers use to hide their IP addresses. I assume hackers look for anonymity and fast connection.

---

### Post by doas777 on 2010-03-04
> 
Since Tor is the best software for anonymity and is very slow, I am curious what softwares do hackers use to hide their IP addresses. I assume hackers look for anonymity and fast connection.they crack other peoples boxes, or rent services with other peoples credit cards. or they work with or from countries that have non-existent or limited enforcement capability. they work from libraries, colleges they do not attend, and starbucks far from their homes.
if they want speed, then someone elses high bandwidth server is a good bet.

---

### Post by rookcifer on 2010-03-04
> **doas777 said:**
> they crack other peoples boxes, or rent services with other peoples credit cards. or they work with or from countries that have non-existent or limited enforcement capability. they work from libraries, colleges they do not attend, and starbucks far from their homes.
if they want speed, then someone elses high bandwidth server is a good bet.


Yep and some people in the criminal underground will even rent the botnets they control out to other criminals.  These criminals can then simply bounce off a string of zombies.

Another method that is very easy to achieve is merely using open wifi access points.  Spoofing MACs and cracking WEP are both very simple to do when those "security" features are enabled on a router.

---

### Post by Jekshadow on 2010-03-05
> **Richiegs said:**
> Which one is better, Tor or Ipredator?

A VPN such as Ipredator will give you faster speeds, but the VPN provider can see any non-encrypted traffic that passes through, and will be able to track you.

Tor is more secure, because even though the outproxy can still see non encrypted traffic, they cannot trace any of the traffic back to your IP. Tor will also give you a max of 25kb/s

This has already been discussed here: [http://ubuntuforums.org/showthread.php?t=1363150](http://ubuntuforums.org/showthread.php?t=1363150)

---

### Post by Richiegs on 2010-03-05
"The main problem with Tor is that it's slower and some websites have banned connections originating from it."

I wonder how some websites know the connections come from Tor since a sufficiently large number of people provide the bandwidth for Tor?

---

### Post by rookcifer on 2010-03-05
> **Richiegs said:**
> "The main problem with Tor is that it's slower and some websites have banned connections originating from it."

I wonder how some websites know the connections come from Tor since a sufficiently large number of people provide the bandwidth for Tor?

Because the Tor node list is made public and some websites, IRC servers, etc. ban any IP on these lists.  Making the list private would provide little benefit as everyone would figure it out anyway.

---

### Post by Richiegs on 2010-03-05
"If you just want to hide your IP from a website and don't care if someone in the "middle" knows your real IP, then a VPN like Ipredator or Xerobank will be fine."

Both Ipredator and Xerobank  require monthly payment. With the economy still  in recession, Is there any free VPN?
I

---

### Post by doas777 on 2010-03-05
> **Richiegs said:**
> "If you just want to hide your IP from a website and don't care if someone in the "middle" knows your real IP, then a VPN like Ipredator or Xerobank will be fine."

Both Ipredator and Xerobank  require monthly payment. With the economy still  in recession, Is there any free VPN?
I
no. that kind of service costs real money to provide, so no one would provide it for free without some way to entice revenue flow.

---

### Post by 0xyg3n on 2010-07-15
> **supershin said:**
> [https://www.torproject.org/download-unix.html.en](https://www.torproject.org/download-unix.html.en)

Read the warning on that page. Just enabling tor doesn't protect you.

Neither does a VPN.

---

### Post by bodhi.zazen on 2010-07-15
> **bodhi.zazen said:**
> IMO your IP address can always be traced.

If that were not the case ^^ you would not get a response from the (web) server you are trying to connect to.

---

### Post by rookcifer on 2010-07-15
> **bodhi.zazen said:**
> If that were not the case ^^ you would not get a response from the (web) server you are trying to connect to.

You quoted yourself. :p  

And I disagree with your statement.  To track a correctly configured Tor connection would require all three Tor nodes to be under the control of the same individual(s), and that is highly unlikely as the Tor nodes are chosen at random.  Another option would be someone who can "see" the entire Internet (like NSA), and then conduct timing attacks against a suspect.  But they would already have to have a suspect in mind.

So, yes, theoretically Tor should be able to be tracked since, as you said, all packets have to be routed.  The problem is a practical one -- it would take an all powerful adversary.  The Tor circuit is encrypted and no node knows what the other node is doing.  This obviously means that it cannot be "sniffed" (since it's all encrypted).  The NSA might be able to trace a connection, but not read it (unless they can crack RSA, which is doubtful).

---

### Post by bodhi.zazen on 2010-07-15
> **rookcifer said:**
> You quoted yourself. :p  

And I disagree with your statement.  To track a correctly configured Tor connection would require all three Tor nodes to be under the control of the same individual(s), and that is highly unlikely as the Tor nodes are chosen at random.  Another option would be someone who can "see" the entire Internet (like NSA), and then conduct timing attacks against a suspect.  But they would already have to have a suspect in mind.

So, yes, theoretically Tor should be able to be tracked since, as you said, all packets have to be routed.  The problem is a practical one -- it would take an all powerful adversary.  The Tor circuit is encrypted and no node knows what the other node is doing.  This obviously means that it cannot be "sniffed" (since it's all encrypted).  The NSA might be able to trace a connection, but not read it (unless they can crack RSA, which is doubtful).

What you say is true, and I do not dispute those facts.

But there are other methods of tracking ...

---

### Post by wacky_sung on 2010-07-16
In short there is no such thing as disguise your ip address unless you hijacked into another person system without his/her knowledge.Proxy / VPN can only enhance your privacy but not anonymous.Everything in the net can be trace with a log file in a matter of time and even in TOR.

---

### Post by ooVoh9em on 2010-07-16
While it is true that an Internet Protocol address can always be tracked, you also have to also consider the fact that the 
third-party would need a starting place to actually attempt this. 

For example, if Bob connects to a third-party server directly from his ISP, the server now has logs of his exact geographical location. All that is left is for someone to contact the ISP and attempt to get information regarding this particular address.

In our second example, Alice connects to a third-party server, using another server on the Internet. The third-party now has the address of the server she connected through; her real IP address remains unknown to this party. 

In the first example, Bob was vulnerable to **any** third-party having knowledge regarding his geographical location, and ISP. **Anyone** can now call and attempt to use social engineering tactics to further learn more about Bob himself. Most ISP technicians aren't typically trained to be aware of such deceptive methods. Especially the entry-level technician in charge of customer support.

In the second example, if the third-party wanted more information regarding Alice, they would need to contact an Administrator of the server she connected through. If she is using a paid VPN service - they are typically very security-aware, and it would be much harder for them to locate Alice in general.

While a Government organization can easily gain access to this information; stalkers, scammers, pedophiles and other unwanted parties cannot.

If we follow the logic: "Any IP can be traced", then we may as well completely forget about all security measures, as there will always be a vulnerable attack vector and new vulnerabilities will be found. This would be a very silly way of looking at things. Just as that statement is a silly way of looking at enhancing ones privacy.

Sure, there are other methods one could deploy to find out the geographical location/ISP of an individual, but none of it is outside of the control of the user. Using a proxy or VPN simply ensures you do not have to entrust the overworked and underpaid entry-level tech at your ISP to completely protect your identity.

a VPN (Virtual Private Network) service is often used to transmit information over an untrusted open network, utilizing encryption to prevent third-parties from sniffing the data going across said network. It is generally overkill if you simply want to "hide your IP". Most people that wish to have the extra security a service like this would offer understand the cost behind it. Also, avoid a PPTP implementation as it is by far the weakest in terms of security. Opt for a service using OpenVPN instead. Keep in mind, this is a **privacy** service

Proxies will do the job of simply preventing your IP address from being exposed to third-parties in some cases, but they often leak information - a simple proxy is not a good solution in most cases.

You can opt for a simple SSH tunnel, and use that as a better method minimizing the exposure of your IP across the Internet. There are many services that offer SSH tunnels for as low as $5/month. Some free shells allow you to do this if you contact them in advance.

If you truly require a free method of doing this, then TOR or JAP are the best options for the cost. Unless you can talk someone into letting you tunnel through them. However, using a service like TOR compromises privacy for anonymity. 

Keep in mind that everything I have described here is completely superficial. There are more aspects regarding privacy and anonymity. as well as the technologies used. However, this should be a sufficient description of each to better help you achieve your overall goal.

---

### Post by 0xyg3n on 2010-07-16
TOR was created by the U.S. Naval Research Lab and is monitored by the U.S. government.  They catch pedos and hackers on it.  There's a lot of servers within the TOR network and you don't know who owns what.

---

