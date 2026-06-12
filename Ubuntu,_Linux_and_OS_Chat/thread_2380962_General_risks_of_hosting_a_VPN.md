---
title: "General risks of hosting a VPN"
date: 2017-12-24
forum: Ubuntu, Linux and OS Chat
---

### Post by MaindotC on 2017-12-24
I realize this is not a ubuntu-related question but I hope some other security professionals here will provide feedback as I'm an avid Ubuntu user and setting up a VPN i[s easily accomplished]("https://help.ubuntu.com/lts/serverguide/vpn.html") with a Ubuntu distro.

What are the risks of hosting VPN services and what would be sufficient, from a high level, to operate safely?  It seems to me that VPN hosts should not freely offer service to whomever purchases a subscription, or host a free VPN farm for that matter, as cyber criminals could easily use that VPN connection to conduct illegal activity.  If you wanted to host a legitimate VPN service such as [Private Internet Access]("https://www.privateinternetaccess.com/") or [Tunnelbear]("https://www.tunnelbear.com/") I would think you'd need to invest heavily in providing evidence that any illegal activity was not initiated by your service, but was initiated by the subscriber.  Perhaps you should have monitoring measures in place to stop any such activity if it violates the ToS but that might go against any guarantee of privacy that is offered. How do VPN services operate and likely provide a passthrough for illegal activity and also protect themselves from prosecution?  I've tried googling phrases like "VPN Server / Hosting risks" and several tutorials on setting up a VPN server, but I can't find anything that addresses the risks.

Also - I realize that a VPN is supposed to provide a secure, encrypted connection to the VPN service.  However, if you're connecting to a site providing SSL how is that different than using a VPN?  The SSL-enabled site provides a security connection using public and session keys. I realize that VPN offers more options: more security protocols, authentication methods, and it seems a VPN connection is less susceptible to man-in-the-middle attacks, but what about your data being sent from the VPN service exit node and the destination host?  Is that segment of the connection not open to the same vulnerabilities?  Isn't the SSL connection again being setup between the SSL-enabled site and the VPN exit node?  If that's the case, then it seems the VPN is more about serving as an intermediary, not for its encrypted traffic between itself and the subscriber.

---

### Post by Irihapeti on 2017-12-26
Not really a support request. Moved to ***Ubuntu, Linux and OS Chat***.

---

### Post by TheFu on 2017-12-28
Lots of opinions follow.

While there are legal reasons to have a paid VPN, the primary reasons people get them generally are not.

Legal reasons:
* Avoid free-wifi security issues.
* Avoid hotel and other "suspect" network tracking. Airports, restaurants, hotels, motels, B&B locations. BTW, I wouldn't trust any cellular network data encryption without using a full IPsec VPN.  Cellular encryption is really poor.
* Perform Security work (pentesting, etc) from different locations around the world - with written approval from the VPN provider.  I have lots and lots of friends, peers, who use VPN services for this purpose. I block many VPS providers from accessing my public servers because of all the SEO and security hacking going on from VPS systems.
* Avoid untrusted govt/ISP network tracking (in countries where the govt cannot be trusted). Sadly, many of those countries mandate that VPN providers give them all the certs, so we don't actually get secured connections. If a CA and DNS is controlled, HTTPS isn't secure. A few ISPs in the USA look at all network traffic for their clients and insert advertisements ( and highly sticky tracking methods - verizon).
* Connectivity for "road warriors" back into the corporate network. This would not be a good method to use the type of VPN you are suggesting.  Also, it is not a good method to VPN to your home network.  Both home and corporate VPNs really need to be run from the house and the corporation, not some VPS in a public data center.

Most VPNs that cost $20/month or less let people use pptp as the protocol. pptp was hacked in 2005 and made trivial for anyone with a tiny bit of technical skill to hack in 2012. It shouldn't be used since 2005 any more than telnet or plain FTP should be used since 1995.  VPN providers who allow pptp are just showing that they really don't care about their clients.  OTOH, if ease of use trumps security in the VPN, then PPTP **is** a viable option.  I'm amazed at the number of people who think that pptp has any security purpose at all.

If you want real security, then using an IPSec-based VPN really is the gold standard.  SSL-based VPN security might not be nearly as secure as we believe today.  Only time will prove how secure or not the openssl libraries really are. 

Legally, there are all sorts of risks, but those will completely depend on your specific location and who/where your clients are located.  Laws in the USA are different from laws in the UK or Russia or China.  In the USA, different states have very different data protection laws too. You need to talk to a lawyer directly about this. Someone knowledgeable about internet privacy laws for your specific jurisdiction.  Or you need to have a plan to close the business when the govt comes knocking.

Most consumer-friendly VPN services don't keep logs - they do log things, but a few minutes after the connection is closed/dropped, they delete those logs.  That has gotten PIA out of trouble for initial data requests, but I'd bet they received another request to keep logs for specific users a day or 2 after that with a gag order attached.  In no way would I trust any VPN with business locations in any of the major "western" countries to keep my traffic secure if they had any belief that I were trying to do harm to any other person, anywhere, in the world.   If you start a VPN connection on your router and keep it active for a week, then there are a week of logs on the service.  Is that really what most people intend?  I bet it isn't.  Without log retention, I don't have any idea how a VPN provider would determine that a client is doing anything illegal.  Plus, things that are illegal in the USA aren't illegal in many parts of the world, so is the VPN provider supposed to be an expert on all those different laws?

Whether they (law enforcement) would come after an individual for copyright infringement is a different question. 

Not all encryption is created equal.  We stopped using AES for our ssh connections in 2016.  Every end-user has a different risk tolerance.  As a provider, all you can do is let the customer know what you offer, and hopefully guide them towards the appropriate level of security for their needs and risks.  Grandma sharing secret family recipes probably doesn't need the same level of protection as a political activist or reporter would.

So ... with all that written (said), what do I actually do?
* I pay for a VPN provider for use from my home/work when I'm performing security consulting.  I don't want to burn my home public subnet from access to the different clients I'm trying to break into (with their paid approval).  This is an LT2P+openVPN connection.  I make a point to connect and disconnect every few hours to have the logs deleted.  Some IRC servers block connections from well-known VPN subnets. That has been (and is) an issue for me.  I can VPN back to my business network, then out to the IRC servers without problems, however.
* I run my own VPNs (openssh and openvpn and libreswan) to get from outside my network back inside.  About 98% of the time, I use an ssh tunnel.  From android devices, I use openvpn to access internal cloud services and to protect against untrusted wifi networks when traveling.  From my travel laptops, I'll use ssh, openvpn or libreswan connections, depending on different considerations.  

Data sent from the VPN system to the next layer only has the protections that the protocol used supports.  That is usually HTTP or HTTPS, but really neither of those are secure for the level of security I'd want.  People don't really understand all the issues with HTTPS, it is clear.  It is a house of cards, with 1,000+ players in the world who can insert a trick deck and get away with it almost every time.  In some parts of the world, the govt has been caught doing this and it isn't always from well-know totalitarian places.  Some NATO countries and some good friends to Europe and the USA have been doing it.   There is equipment available (since around 2005-ish) that lets anyone MITM HTTPS connections, if they have enough money. As processors get faster, that ability has become easier and easier even without placing a cert onto the end-user machine.  Large telecoms and many countries have this equipment, I'm certain.

I wouldn't run a VPN service that was available to the general public.  The risks (personal and business) are just too high for my liability.  I have run VPN service for corporations, small businesses and myself for decades. People are generally on their best behavior when on work networks when their job is at risk over poor behavior. That has been my experience, anyway.  YMMV.

Anyway ... I wish you well, if you choose to try and do this.  Only you can decide if running a VPN fits with your legal and business risks.

---

