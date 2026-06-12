---
title: "Good VPN for Ubuntu?"
date: 2012-09-25
forum: Security
---

### Post by shalviy on 2012-09-25
Hey, I am relatively new to Linux but I know how to work Terminal. I used to run Mac OSX and Windows and I used to use a VPN service called Spotflux. I am currently trying to find another VPN. SecurityKiss works but is dreadfully slow and is limited to 300mb/day (which I can easily go over). FreeCanadaVPN also works but only on very select networks and not on the network that I am on the most. I also used Hotspot shield until it mysteriously stopped working on my main networks. Any good VPNs out there?

(I do know how to setup PPTP VPNs)

(I have OpenVPN installed but I have no clue of how to work it...)

---

### Post by Lars Noodén on 2012-09-25
OpenVPN would be the way to go.  But are you sure you need a VPN at all?  What are you trying to use it for?

---

### Post by Welly Wu on 2012-09-25
I use WiTopia personal VPN Pro: [http://www.witopia.net](http://www.witopia.net). There are over 50 VPN gateways in North America, Europe, Asia, South America. It supports OpenVPN, CISCO IPSec, L2TP/IPSec, and PPTP. It costs $72 USD annually. There are no limitations or monitoring or recording of your activities. LifeHacker did a review of the top 5 VPN service providers and they awarded WiTopia as the best. Do a Google search.

---

### Post by orange2k on 2012-09-26
I think that Ipredator is probably one of the best. Costs 15 Euros for 3 months and even gives you a trial that lasts 3 days...

Works on windows, mac, linux, iphone, android...

---

### Post by sammiev on 2012-09-26
> **Welly Wu said:**
> I use WiTopia personal VPN Pro: [http://www.witopia.net](http://www.witopia.net). There are over 50 VPN gateways in North America, Europe, Asia, South America. It supports OpenVPN, CISCO IPSec, L2TP/IPSec, and PPTP. It costs $72 USD annually. There are no limitations or monitoring or recording of your activities. LifeHacker did a review of the top 5 VPN service providers and they awarded WiTopia as the best. Do a Google search.

+1 for WiTopia.

---

### Post by ooVoh9em on 2012-09-26
> **Welly Wu said:**
> I use WiTopia personal VPN Pro: [http://www.witopia.net](http://www.witopia.net). There are over 50 VPN gateways in North America, Europe, Asia, South America. It supports OpenVPN, CISCO IPSec, L2TP/IPSec, and PPTP. It costs $72 USD annually. There are no limitations or monitoring or recording of your activities. LifeHacker did a review of the top 5 VPN service providers and they awarded WiTopia as the best. Do a Google search.

I also recommend WiTopia. The service is affordable, price accordingly and was extremely reliable when I used it. They also support VPN connections all over the globe, and are one of the few services which also allow you to use AES-256.

I used the service for a year, and I was really satisfied with the service. I never had to use customer support, but I have heard from others that it is good as well.

Also, if you're using Network Manager, just get the OpenVPN plugin for it. It will then let you use Network Manager to connect to the VPN with ease.

The best part of WiTopia is their money back guarantee within 30 days. I actually tested this just to test it, and they refunded me on day 29 without any questions asked. The following day I had my refund, and then proceeded to renew for a full year. This is one of the very few VPN companies that I place any trust in at all.

---

### Post by Welly Wu on 2012-09-27
Whatever you choose to go with, don't use PPTP:

[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

---

### Post by Welly Wu on 2012-09-28
There are a couple of important bits of information that you need to know about WiTopia.

WiTopia offers two types of VPN service accounts for personal usage:

1. WiTopia personal VPN basic
2. WiTopia personal VPN PRO

Basically, PRO gives you access to OpenVPN protocol and you need to download and install your WiTopia SSL certificates in order to use OpenVPN. It requires that you renew your subscription annually to download new SSL certificates one month prior to the end of your first subscription. You can only subscribe to Personal VPN PRO on an annual basis for now. WiTopia does not offer multi-year subscriptions yet, but they are working on it. PRO gives you access to Blowfish CBC mode 256 bits 16 rounds SSL encryption and the most flexible options for connecting to WiTopia VPN gateways worldwide. You can even set your own custom OpenVPN ports if you have difficulty connecting to their OpenVPN gateways.

If you use Microsoft Windows XP, Vista, or 7 or Apple Macintosh OS X Snow Leopard, Lion, or Mountain Lion, then you can download and install the WiTopia Personal VPN software application that handles all of the installation and configuration details for you including your VPN password and SSL certificates. If you choose to subscribe to the PRO account, then you can set your initial entry VPN gateway and you can set a different VPN exit gateway for enhanced privacy, safety, and security, but this only applies if you use Windows or OS X. You can not do this with GNU/Linux like Ubuntu to the best of my knowledge.

WiTopia does weekly maintenance on Saturday evenings from 6 PM - 7 PM. It only takes them about 10 - 15 minutes to do the maintenance. At this time, you will not be able to connect to WiTopia VPN gateways on Saturdays from 6 - 7 PM EST.

WiTopia does not limit your bandwidth and it does not monitor or restrict your activities so long as you abide by their contract. Basically, they know that you are an adult and they treat you like an adult. Don't do anything criminal on their networks though.

In my tests, WiTopia Personal VPN PRO is the best VPN service provider and I have tried just about almost all of the other VPN service providers that offer service and support for Ubuntu users as well. They offer the absolute fastest speeds and performance and you should not see any degradation of bandwidth if you connect to WiTopia personal VPN PRO.

Finally, WiTopia allows you to connect up to 2 devices to their VPN gateways simultaneously. This is important if you want two devices that connect to an ISP to WiTopia at the same time. To the best of my knowledge, they are the only ones that offer this unique service.

Go with WiTopia and get the personal VPN PRO service if possible.

---

### Post by WhiteHatGuy on 2012-09-30
> **shalviy said:**
> Hey, I am relatively new to Linux but I know how to work Terminal. I used to run Mac OSX and Windows and I used to use a VPN service called Spotflux. I am currently trying to find another VPN. SecurityKiss works but is dreadfully slow and is limited to 300mb/day (which I can easily go over). FreeCanadaVPN also works but only on very select networks and not on the network that I am on the most. I also used Hotspot shield until it mysteriously stopped working on my main networks. Any good VPNs out there?

(I do know how to setup PPTP VPNs)

(I have OpenVPN installed but I have no clue of how to work it...)









The only free vpn I found for linux so far is TrustConnect from Comodo. They give 10 GB free for each month.

What do you guys think about this one, is it good?

---

### Post by sammiev on 2012-09-30
> **WhiteHatGuy said:**
> The only free vpn I found for linux so far is TrustConnect from Comodo. They give 10 GB free for each month.

What do you guys think about this one, is it good?

Not free any more for 10 GB. Starts at 19.95 to 99.95 for unlimited.

---

### Post by WhiteHatGuy on 2012-09-30
> **sammiev said:**
> Not free any more for 10 GB. Starts at 19.95 to 99.95 for unlimited.




Thats weird. I just tested, and I am able to login, it changed my ip address and everything.

They offer the paid version and free version, maybe the are not accepting new free accounts, but is working right now for me.


[http://help.comodo.com/topic-83-1-158-1304-How-To-Set-Up-TrustConnect-On-Linux.html](http://help.comodo.com/topic-83-1-158-1304-How-To-Set-Up-TrustConnect-On-Linux.html)

---

### Post by Stonecold1995 on 2012-10-03
Don't use any free VPNs.  They are slow, and they usually log the sites you visit, or inject adverts, etc.  Also don't use a VPN with servers located in the USA (or similar privacy invasive countries), because of sh*t laws that allow the VPN company to log what goes through their servers.  In general, I'd highly recommend a Swedish VPN, for example iPreditor, Anonine, VPNTunnel, or Mullvad.  I use BTGuard myself (it's servers are located in Canada and Germany, although I never use the Canadian servers because of poor privacy laws) for torrents and casual browsing, and although it has decent speed and great up-time, the customer service is crappy (overall it's pretty good).

And yes, you should never use PPTP for any VPN.

---

### Post by Welly Wu on 2012-10-07
You are promoting some misinformation there.

WiTopia is based in Virginia, USA. They do not record or monitor their customers unless they are trying to start a telephone company while using their VPN gateway servers. On Saturdays at 6 PM EST, they perform maintenance and they clear out their logs completely for most of their customers.

Free VPN service providers usually do limit bandwidth and they place data caps. You should review their contracts and check the fine print to see if they monitor and record customer activities.

---

### Post by Welly Wu on 2012-10-07
[http://news.cnet.com/8301-13554_3-9894851-33.html](http://news.cnet.com/8301-13554_3-9894851-33.html)

---

### Post by Stonecold1995 on 2012-10-07
> **Welly Wu said:**
> You are promoting some misinformation there.

WiTopia is based in Virginia, USA. They do not record or monitor their customers unless they are trying to start a telephone company while using their VPN gateway servers. On Saturdays at 6 PM EST, they perform maintenance and they clear out their logs completely for most of their customers.

I do not see it as misinformation.  I never said all VPNs with servers in the United States log traffic, I'm saying that they do not have the same privacy laws as places like Sweden and Germany.  For example, if a government organization were to demand logs from a US VPN, they would have to provide those logs if they are kept, whereas Swedish VPNs do not.  In fact, unless it changed, Swedish VPNs are legally not even *allowed* to log for more than what is required to protect their own servers from DDoS attacks, spam, etc.

I do not doubt that there are US-based VPN services that do not log, but my main point is that there's nothing stopping them from logging traffic, and honestly I don't trust every privacy policy I see a site advertise.

---

### Post by Stonecold1995 on 2012-10-07
[https://torrentfreak.com/which-vpn-providers-really-take-anonymity-seriously-111007/](https://torrentfreak.com/which-vpn-providers-really-take-anonymity-seriously-111007/)

---

### Post by Welly Wu on 2012-10-07
Again, you are making sweeping generalizations without providing any useful customer experience to back it up. This is why I called you out earlier.

Provide me with actual user experience with a US based VPN service provider in which you either can prove or disprove that they monitor and record customer activities. I have told you that WiTopia is based in Virginia, USA and they do not log customer activities unless you are trying to start a telephone company using their services.

You then go on to spew misinformation that makes sweeping generalizations about US based VPN service providers with no relevant and real customer experience to back it up.

How do you know for sure if that list of VPN service providers that you provided is legitimate? Have you tried several of them and their services to find out for sure yourself or not?

Don't make sweeping generalizations and expect not to get called out point blank.

As far as I am concerned, your are spreading FUD and it needs to stop right now.

You are taking this discussion in a direction that is not intended by the original poster and you are thread crapping.

Please stay on topic or refrain from commenting further.

WiTopia does not monitor or record customer activities. I should know because I am a WiTopia customer and I have done my fair share of peer to peer file sharing and I have downloaded data directly from websites. I won't specify what kind of data I have downloaded, but suffice it to say that WiTopia has not terminated my account with them yet. I am not going to elaborate further either.

Thank you.

---

### Post by Stonecold1995 on 2012-10-08
> **Welly Wu said:**
> Again, you are making sweeping generalizations without providing any useful customer experience to back it up. This is why I called you out earlier.

Provide me with actual user experience with a US based VPN service provider in which you either can prove or disprove that they monitor and record customer activities. I have told you that WiTopia is based in Virginia, USA and they do not log customer activities unless you are trying to start a telephone company using their services.

I never said WiTopia logs customer activities.  I never even said most US based providers log activities.  You cannot deny though that the privacy laws the US has in place allows servers to log and disclose information.  And a quick Google search can reveal "actual user experience", as well as the privacy laws of those services.  One extreme example would be the events with the hacktivist group "LulzSec" (Lulz Security), which allegedly had some of its users tracked down through the US based VPN provider "Hide My ***", which claimed it did not log yet still covertly collected personal information, enough information in fact that the US government was able to demand user logs from HMA, to the end of arresting some of the members of LulzSec.  Now I'm not saying that anyone here would be as high profile as this hacktivist group, but it does prove that HMA does in fact log user data.  And there are many similar sites which do the same.  Any service with a privacy policy that says they will disclose personal information to comply with court order also logs, at least to some extent (such as keeping limited user information for 30 days in your VPN's case).

> **Welly Wu said:**
> You then go on to spew misinformation that makes sweeping generalizations about US based VPN service providers with no relevant and real customer experience to back it up.

How is pointing out that the US law allows the logging and disclosing of such information "sweeping generalizations" and "spewing misinformation"?

> **Welly Wu said:**
> How do you know for sure if that list of VPN service providers that you provided is legitimate? Have you tried several of them and their services to find out for sure yourself or not?

The list I provided is legitimate.  I have tried BTGuard, Anonine, VPNTunnel, and the trial version of Mullvad.  I have never tried iPreditor though, so I'm just going of customer reviews on that one.

> **Welly Wu said:**
> Don't make sweeping generalizations and expect not to get called out point blank.

As far as I am concerned, your are spreading FUD and it needs to stop right now.

I'm not intending to spread FUD, and I don't see how pointing out current privacy laws in the US is spreading FUD.  And how was I called out "point blank" anyways?

> **Welly Wu said:**
> You are taking this discussion in a direction that is not intended by the original poster and you are thread crapping.

Please stay on topic or refrain from commenting further.

I think this is very much relevant to the thread.  OP asked for a good VPN for Ubuntu, and this whole topic has not strayed from VPNs.

> **Welly Wu said:**
> WiTopia does not monitor or record customer activities. I should know because I am a WiTopia customer and I have done my fair share of peer to peer file sharing and I have downloaded data directly from websites. I won't specify what kind of data I have downloaded, but suffice it to say that WiTopia has not terminated my account with them yet. I am not going to elaborate further either.

Thank you.

I do not doubt your claim.  I never said "WiTopia logs", and I don't have enough information on that specific VPN to make an informed decision.  And I have done my share of file sharing too.  I do not care what kind of files you share, and I'm not asking that you elaborate on it either.

The main point is, I did not say "all US based VPNs log and disclose information", and I did not expect to see my posts read that way.  There is no reason to get upset, I am not attacking WiTopia, and I am not attacking all US servers, I am pointing out that privacy laws *do* permit logging of activity, and that Swedish VPNs have stricter customer privacy laws than the US.  If OP is looking for a VPN that is less likely to log, then the *rule of thumb* is that Swedish VPNs are the way to go, but if you find a VPN that better fits your needs for whatever reason, that's fine too.

I did not attack your post, or your recommendation of WiTopia.  I just posted advice relating to the privacy laws of these two countries, and recommendations of four VPNs which I have personally tried, and one which I have heard is good from many sources, but have not tried myself.

EDIT: I just looked up more about WiTopia, and read their privacy policy.  They say they store limited login information for 30 days, and will store and disclose information if necessary to comply with court order.  Compare that with the privacy policy of VPNTunnel, which says "In accordance with swedish law, we do not store any data at all on our swedish servers."  You have to admit that not storing any data at all provides more privacy then "we store data for 30 days, and will disclose data in response to court order".

---

### Post by Welly Wu on 2012-10-08
Look, it's the end points that matter. These end points are outside of the scope of any VPN service provider especially if you leave behind a digital trail of evidence to collect and analyze data about you. One example would be to use social media outlets while connected to any VPN service provider's VPN gateway as evidence that you commmited a crime. In the US, you can not threaten to kill the US president or vice president or the GOP running mate on Facebook and expect to get away with that crime.

Peer to peer file sharing is not the same as login credentials. We are talking about network traffic here. WiTopia has to log your login credentials so it knows when you use their service. This is considered to be within the realm of acceptable logging in the United States and a lot of other VPN service providers do this as well in other countries except for Sweden. What we are more concerned with here is what kind of monitoring, recording, and logging of user's network traffic happens in accordance to a specific VPN service providers' contract with its users and how that information and data is handled in the event of a digital investigation.

WiTopia does not monitor or record your network traffic. This means that they don't keep tabs on me when I download or upload data even if it was copyrighted which I am not saying is happening here in my case or not. They clear their logs every Saturdays for maintenance.

Logging login credentials is pretty much useless information if you can not corroborate it with user's network activities and traffic.

You're making a bad assumption here. You're assuming that any type of logging is tantamount to monitoring and recording customer's network traffic data histories and you're assuming that all of those records get turned over to a court with a court order in the case of WiTopia. That is clearly not the case.

Finally, you have understand that it's your ISP that you should be much more concerned about. In the United States, most of the major ISPs do record and monitor their customer's network traffic and the MPAA and RIAA have agreements in place to alert and warn their customers of copyright infringment which could lead to law suits. VPN does not protect against this type of illegal behavior regardless of which VPN service provider because a lot of network traffic passes through the United States of America through a complex mesh of nodes and end points that you're not aware of.

This is the nature of P2P architecture. You have no idea who is sharing that data with you and where it traverses throughout the world.

VPNs also don't protect you if you register personally identifiable information on a web site that is not fully encrypted and located outside of the US and has its traffic routed outside of the US completely. This is an extreme example and it is an isolated case.

Bottom line: VPNs are useful for privacy and security, but don't think that you can't be attacked while connected to a VPN gateway by visiting malicious websites. VPNs don't control any data that is collected, analyzed, and eventually used to pinpoint users' location and activities outside of their entry and exit gateways. I would be much more concerned about this fact than a VPN service provider who logs all of my data.

I got news for you. Sweden is cracking down on copyright infringment. It won't be long before it bows to pressure from foreign governments and organizations to log users network traffic and identities. Don't make the assumption that connecting to a VPN service provider in Sweden guarantees anonymity, privacy, or security. That's a big caveat that's hard to ignore now that the Pirate Bay and its affiliates are getting hammered in courts worldwide.

---

### Post by Welly Wu on 2012-10-08
Look, I know a lot more about this subject than you do from a technical perspective because I have a lot of current IT certifications and most of them are in security specifically network security.

You are basing your information on what VPN service providers are willing to put into writing to advertise their services to potential customers and you are also making some big assumptions. Finally, you are negleting the open nature and architecture of the Internet itself. I doubt that you know enough about Swedish laws to tell me exactly how the founders of The Pirate Bay wound up getting caught and prosecuted and they were found guilty in Swedish courts. Mega Upload is based in New Zealand and they have pretty liberal laws regarding surveillance compared to the UK or USA or even PRC.

Once you access products or services or you access data that is located outside of your VPN service provider's gateway, you are fair game for anybody to target and attack you. This includes your network traffic history and data.

Do you have any idea how extremely expensive it would be to create an encrypted tunnel that extends throughout your entire network traffic worldwide? It's impossible.

The United States government has the most sophisticated digital investigative capabilities and technologies in the world. We have the most sophisticated surveillance systems worldwide. We can pretty much order almost any ISP or VPN service provider to divulge customer data at will especially if it relates to national security. The United Kingdom is not far behind either. Israel is pretty damn sophisticated too.

Look, a VPN service provider that logs your network traffic makes it more convenient for a government to request that they turn over their customer records. That's it. It reduces the amount of work that they have to do.

Finally, to belabor this point so that you understand it more clearly, it is important to note that no ISP or VPN service provider or web proxy or any future network technology can give your 100 percent foolproof privacy, security, anonymity, and safety. You take risks when you connect your PC and you create an identity on the Internet or any other network environment. Logging is considered to be low scale in terms of the pecking order. Logging makes it possible for active surveillance and targeted attacks to occur against people, individuals, organizations, groups, governments, corporations, etc. Logging is not necessarily negative and evil.

It comes down to who is after you and why. It also matters what kind of resources do they have and what kind of relationships do they have in their corner to make it easier for them to get to know you intimately.

VPN can not protect you against these types of threats. Best to keep a low profile.

---

### Post by Welly Wu on 2012-10-08
I would be much more concerned with who logs your information and data outside of the scope of your VPN service provider and how long they retain that data and what they ultimately use that data for which purposes than your VPN service provider logging all of your information.

You can choose another VPN service provider. You can choose another ISP. You can terminate your business with these companies.

However, you usually don't have full control over the 3rd parties involved when you do your business on the Internet or when you connect to another person's network environment like a business.

That's where they will get you.

Don't make the false assumption that VPN will protect you completely.

Logging is low level and low importance. What matters is who is after you and how can they get access to your data by connecting the dots back to you.

---

### Post by Stonecold1995 on 2012-10-08
> **Welly Wu said:**
> Look, it's the end points that matter. These end points are outside of the scope of any VPN service provider especially if you leave behind a digital trail of evidence to collect and analyze data about you. One example would be to use social media outlets while connected to any VPN service provider's VPN gateway as evidence that you commmited a crime. In the US, you can not threaten to kill the US president or vice president or the GOP running mate on Facebook and expect to get away with that crime.

That is completely irrelevant.  Of course a VPN won't protect you from that, no matter what VPN you use.  Even Tor won't protect you if you leave a trail of your activities.

> **Welly Wu said:**
> Peer to peer file sharing is not the same as login credentials. We are talking about network traffic here. WiTopia has to log your login credentials so it knows when you use their service. This is considered to be within the realm of acceptable logging in the United States and a lot of other VPN service providers do this as well in other countries except for Sweden. What we are more concerned with here is what kind of monitoring, recording, and logging of user's network traffic happens in accordance to a specific VPN service providers' contract with its users and how that information and data is handled in the event of a digital investigation.

I am saying Sweden has more strict privacy laws, not that WiTopia has poor privacy laws.  And US providers won't protect you "In the event of a digital investigation", whereas Swedish providers in general will.

> **Welly Wu said:**
> WiTopia does not monitor or record your network traffic. This means that they don't keep tabs on me when I download or upload data even if it was copyrighted which I am not saying is happening here in my case or not. They clear their logs every Saturdays for maintenance.

Logging login credentials is pretty much useless information if you can not corroborate it with user's network activities and traffic.

I never said they keep tabs on what you are downloading.  I do not know enough information on that specific VPN to say one way or another, I'm just going off what I read on their Privacy Policy.  And they clean their logs every Saturday?  OK, but you have to admit that's less secure than not keeping logs period.

> **Welly Wu said:**
> You're making a bad assumption here. You're assuming that any type of logging is tantamount to monitoring and recording customer's network traffic data histories and you're assuming that all of those records get turned over to a court with a court order in the case of WiTopia. That is clearly not the case.

I never said that, and I don't assume it.  I am saying Swedish VPNs don't have to hand over logs and aren't allowed to log.  Let me say again, **I never said WiTopia logs everything you do.**

> **Welly Wu said:**
> Finally, you have understand that it's your ISP that you should be much more concerned about. In the United States, most of the major ISPs do record and monitor their customer's network traffic and the MPAA and RIAA have agreements in place to alert and warn their customers of copyright infringment which could lead to law suits. VPN does not protect against this type of illegal behavior regardless of which VPN service provider because a lot of network traffic passes through the United States of America through a complex mesh of nodes and end points that you're not aware of.

This is the nature of P2P architecture. You have no idea who is sharing that data with you and where it traverses throughout the world.

I understand that.  That's one of the main purposes of a VPN.  The thing you aren't understanding is that most VPNs use encryption, which *prevents* ISPs from logging information.  That's what I use a VPN for, to protect me from my VPN.  I completely understand that a lot of network traffic goes through many servers we can't be aware of, but I also understand that encryption will prevent logging of personal information, because all personal information that goes through these relays and ISPs are encrypted, usually with BlowFish, which is a quite secure encryption algorithm.

> **Welly Wu said:**
> VPNs also don't protect you if you register personally identifiable information on a web site that is not fully encrypted and located outside of the US and has its traffic routed outside of the US completely. This is an extreme example and it is an isolated case.

That has nothing to do with a VPN's privacy laws.

> **Welly Wu said:**
> Bottom line: VPNs are useful for privacy and security, but don't think that you can't be attacked while connected to a VPN gateway by visiting malicious websites. VPNs don't control any data that is collected, analyzed, and eventually used to pinpoint users' location and activities outside of their entry and exit gateways. I would be much more concerned about this fact than a VPN service provider who logs all of my data.

Who said anything about malicious websites?  A VPN will encrypt data, it will not block someone from giving out personal info.  Again, this is completely off-topic.  There is no VPN in the world that will prevent such a thing.

> **Welly Wu said:**
> I got news for you. Sweden is cracking down on copyright infringment. It won't be long before it bows to pressure from foreign governments and organizations to log users network traffic and identities. Don't make the assumption that connecting to a VPN service provider in Sweden guarantees anonymity, privacy, or security. That's a big caveat that's hard to ignore now that the Pirate Bay and its affiliates are getting hammered in courts worldwide.

When did I say a Swedish VPN "guarantees anonymity"?  I said they have *better privacy laws than the US.*  I understand that they are cracking down, but does that mean they automatically have worse privacy than the US?  Yes, it is hard to ignore, and when I need to do simple web browsing that I don't trust my VPN to be safe enough, I'll use Tor, on the Tails OS, and with FireFox with NoScript, etc.

Last thing: **How is saying that Sweden has better privacy laws than US spreading misinformation?  And how is saying US based VPNs are able to log user data (again, I'm not saying WiTopia is one of those) spreading FUD?**

Please, let's end this conversation before it gets even more off-topic.  The bottom line is, Sweden has better privacy laws then the US.  I don't understand why you object so much to my recommendation of an offshore VPN over a US based VPN.

---

### Post by Stonecold1995 on 2012-10-08
Dude, why are you freaking out so much about this?  This is not a competition on who knows most about privacy laws!  This is not the place to continue this discussion either.  Please, take your own advise and stop going off topic!  I love discussions about internet privacy, but this here is not the time and place.  I do not want this to become a debate on the best privacy practices either.  This is a VPN recommendation thread.  If you want people to discuss paranoia-level internet security I suggest you look on the deep web.

I don't care who knows more about security.  I. Do. Not. Care.  I will not answer your "tests" of how much I know.  I am not trying to claim Swedish VPNs are bulletproof either, and that they don't ever log whatsoever, and that they will all protect you even if you are as high a profile target as The Pirate Bay.  Even the RBN wasn't totally bulletproof!

**Now, before this thread gets locked or we get warnings, please, stop arguing about this.  Frankly, I don't give a d*mn whether WiTopia logs or not, and I don't give a d*mn whether you or I has more knowledge.  The only reason I entered this thread was to recommend a few VPNs, and to mention that Swedish VPNs typically have better privacy than US VPNs, not to be confrontational!**


Also, yes, I am a Swedish citizen.  I have a European citizenship.  Although you are correct, I do not currently live in Sweden.

---

### Post by Welly Wu on 2012-10-08
This is going to be the last time that I reply to you in this thread.

You are making a very big assumption of which you have absolutely no first hand knowledge or proof of: Sweden does not log user information or data. You don't live in Sweden. You are not a Swedish citizen. You are not subject to Swedish laws, rules, or regulations. I know this about you. Yet, the Swedish courts have convicted the founders of the Pirate Bay and their affiliates of copyright infringment and other laws. They have taken down the Pirate Bay and their other peer to peer websites that hawk copyrighted materials. How do you think this was possible? Do you even know the details? I don't presume to know all of the details as I have not read the sealed court paper work.

You can not make a sweeping generalization about the United States and Sweden based upon your cursory knowledge of a very few number of their laws.

Look, tell the truth if you are going to have this conversation with me. At least be honest. Do you have any idea if your ISP or VPN or anyone else for that matter are investigating you specifically or not?

This is the true test of whether you know your stuff or not.

I paid a private investigator to go through my records which I supplied to him to see if I am under investigation last month. I am not under investigation.

Swedish ISPs and VPNs may or may not log customer records depending upon who is asking for them. You and I have no way to get that information because we are not officials related to law enforcement or government requesting such records about specific targets in an investigation. What I am saying is that it is clear to me that the founders of the Pirate Bay got caught for peddling copyrighted materials hosted in Sweden.

How do you think that happened that lead to their convictions in Swedish courts?

Tell me the answer to this question and I will tell you that your notion that Sweden does not log customer records is patently false.

The founders and members of the Pirate Bay used Swedish ISPs and VPNs as well as others located worldwide and they got caught and convicted under Swedish law. Think about how that happened under your premises to see if your assumptions are correct and in line with reality or not.

Then, get back to me and tell me the answer to my question. It will pertain to your assumption that Sweden does not log customer records.

Do your homework.

---

### Post by Welly Wu on 2012-10-08
I just wanted to say that I have nothing against you personally as I don't even know who you are or what your character is. Don't hold this as a grudge against me. I am not trying to single you out. If I came across as inflammatory, then please forgive me and let's move onward.

I just had to challenge some of your assumptions because they sounded off to me.

Another good VPN service provider that I can recommend is CyberGhost VPN. They are based in Romania and they have entry and exit VPN gateways in Germany and Holland. These countries typically do not monitor and record customer records unless you participate in a digital crime that prompts an investigation by their authorities. They are expensive and they have a limited number of VPN gateways, but they do offer services catered toward GNU/Linux users if you pay for their services. I have recommended it to a friend of mine and they do offer a free VPN service, but it is quite slow and there are a lot of advertisements. CyberGhost VPN does not log your customer records to the best of my knowledge, but I may be wrong on that so it is best to check with them directly to make sure.

---

### Post by Stonecold1995 on 2012-10-08
> **Welly Wu said:**
> I just had to challenge some of your assumptions because they sounded off to me.

I was just giving out a rule of thumb, that Sweden currently has better privacy laws than the US.  I never meant to claim Sweden was perfect and the US sucks, or that Swedish VPNs give perfect anonymity and US VPNs always log, and I apologize if I came off that way.

But yes, let's move on.

---

### Post by johnnytucats on 2012-10-17
I've been using [iVPN.net]("https://www.ivpn.net/aff.php?aff=145") for a few months. It's not perfect, I guess, but it's good considering price & features.

---

### Post by KegHead on 2012-11-02
Hi!

This is great info!

I've set up my network manager in Xubuntu correctly but have no free VPN to connect to.


Anyone?

Thanks!

KegHead

---

### Post by KegHead on 2012-11-05
Hi!

I'm using the following:

UKVPN.NewFreeVPN.COM

Anyone with comments or help?

Thanks!

KegHead

---

### Post by sammiev on 2013-04-09
> **KegHead said:**
> Hi!

I'm using the following:

UKVPN.NewFreeVPN.COM

Anyone with comments or help?

Thanks!

KegHead

I seen this before. UserID free, Password 1234, On too many sites with the same userid and password. I would think it's the same person who opens a site every other week and closes the others. I would think use at your own risk!

---

### Post by tubbygweilo on 2013-04-09
Sure is a lot of it about, Google says : About 26,700 results (0.44 seconds) for *vpn UserID=free Password=1234*

---

### Post by sammiev on 2013-04-09
I would suggest that the user change all their passwords as soon as possible if they were using the service.

---

### Post by hungrysquirrel on 2013-04-26
I have been using Ubuntu on a dual boot machine for 4 months now. Why was I keeping Windows? Well only because I could not get StrongVPN pptp to work properly with Ubuntu. I tried repeatedly. I spoke to them, I upgraded to open vpn because they thought that would solve all the problems. It didn't. Open vpn would not even connect to their servers. In the end they blamed my connection and said I must take it up with my ISP. But it works with Windows I kept telling them. . . . . . 

The last week I searched this forum for a solution (why didn't I look here before?). Some people seemed to suggest Witopia was good. So I tried it this morning. And within 15 minutes it was up and running with Ubuntu. No connection problems. No drop-outs. It just works. 

Many thanks to you guys. Now what do I need Windows for?  :):)

---

### Post by BigCityCat on 2013-06-24
This one works really good. $40 a year. No logging, lots of locations, works great on Ubuntu, OpenVPN. PrivateInternetAccess.

[https://www.privateinternetaccess.com/pages/buy-vpn/](https://www.privateinternetaccess.com/pages/buy-vpn/)

---

### Post by KlipperKyle on 2013-06-28
If you use OpenVPN, I recommend installing OpenVPN integration in NetworkManager (The network icon in the upper right corner of the screen). I believe the package name is network-manager-openvpn.

However, be prepared to do some manual configuration in NetworkManager. The import functionality is incomplete.

I would not trust the free VPNs (or TOR for that matter). They tend to attract criminal activity.

WiTopia looks pretty good (although I have never personally used it). They claim they will let you connect at most two devices simultaneously to their network.

The VPN service that I *can* vouch for is Astrill. It is the same price as WiTopia, and it works with almost every platform I have encountered. There are many servers, and they don't throttle your bandwidth. You can use their own client (which supports Ubuntu), or set up OpenVPN (which they provide instructions for). The only limitation is that you can connect only one device at a time. (Again, that's why WiTopia caught my eye as I perused this thread.)

[https://www.astrill.com/](https://www.astrill.com/)

---

### Post by Stonecold1995 on 2013-06-28
> **KlipperKyle said:**
> If you use OpenVPN, I recommend installing OpenVPN integration in NetworkManager (The network icon in the upper right corner of the screen). I believe the package name is network-manager-openvpn.

However, be prepared to do some manual configuration in NetworkManager. The import functionality is incomplete.

I would not trust the free VPNs (or TOR for that matter). They tend to attract criminal activity.

WiTopia looks pretty good (although I have never personally used it). They claim they will let you connect at most two devices simultaneously to their network.

The VPN service that I *can* vouch for is Astrill. It is the same price as WiTopia, and it works with almost every platform I have encountered. There are many servers, and they don't throttle your bandwidth. You can use their own client (which supports Ubuntu), or set up OpenVPN (which they provide instructions for). The only limitation is that you can connect only one device at a time. (Again, that's why WiTopia caught my eye as I perused this thread.)

[https://www.astrill.com/](https://www.astrill.com/)
I can understand avoiding free VPNs, but Tor?  Tor can be trusted far more than any VPN can, because you don't have to place absolute trust in any one node, whereas with a VPN you do.  As for "attracting" criminal activity, first of all, how does it affect you?  Criminals use it because it's secure (they also use VPNs), so why go for something less secure?  Either way using encryption gets you on the secret FBI watch list (look it up), regardeless of whether it's a VPN or Tor.  Second of all, Tor does a lot more good than it does bad, and it helps out the "good" guys just as much as the "bad" guys, simply by being secure.  Of course, Tor is slow, and doesn't support UDP traffic, so no torrents, etc.  Tor is good for browsing when you need very strong protection, but it is not a good replacement for a full VPN.

I would avoid WiTopia, it's privacy policy, tos, and copyright policy are a disastor.  Basically they're saying "We'll protect you, unless someone asks us to identify you in which case we'll give all your personal info away!".  And with the whole PRISM thing I'd be extra cautious.

---

### Post by dyrer on 2013-06-29
I have an account to cyberghostvpn and their openvpn settings works perfect with ubuntu
Give them a try, they offer free 1GB per month traffic

---

### Post by perlon on 2013-06-29
What do you guys think about [https://www.vpnbook.com/](https://www.vpnbook.com/) ?
It sounds good to me.

---

### Post by Stonecold1995 on 2013-06-30
> **perlon said:**
> What do you guys think about [https://www.vpnbook.com/](https://www.vpnbook.com/) ?
It sounds good to me.
I would avoid free VPNs if I were you.

---

