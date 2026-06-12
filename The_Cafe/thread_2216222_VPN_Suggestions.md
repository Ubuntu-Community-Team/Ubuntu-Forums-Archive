---
title: "VPN Suggestions"
date: 2014-04-10
forum: The Cafe
---

### Post by pancho5 on 2014-04-10
Does anyone recommend a safe, trustworthy VPN to use?  I'm new to Linux, converting from a WinXP system.  I looked/tried at a lot of VPN's, but for some reason I don't feel comfortable with any of them.  Though DuckDuckGo is okay, but if I want to DL a movie for my wife and I to watch on occasion, I would like to do that.  Or, if I want to do some research on medical stuff, I want to go through a VPN.  Any suggestions?:confused:

---

### Post by Xanthius on 2014-04-10
DuckDuckGo is not really a VPN, as it just "hides" your search queries from Google, Yahoo, etc. But if the government wants to get you, they still can see you visited this page: "https://duckduckgo.com/?q=a+movie+for+my+wife", and the page after that, etc.
You could take a look at the tor project, that with browser plugins to switch between your main connection and the private connection would allow you to privately search the web for anything with the push of a button.

---

### Post by sandyd on 2014-04-10
Not support - moved to cafe

---

### Post by PartisanEntity on 2014-04-11
I personally have been using Witopia for some years now and I am happy with them. Easy setup for Windows, OSX and Linux.

---

### Post by Lars Noodén on 2014-04-11
A VPN won't help much with privacy though it can reduce the likelihood of having your traffic intercepted from wireless, say at a cafe.  If you are more interested in privacy look at the above suggestion for Tor.  In particular, the Tor Browser Bundle might be of use as it will set up automatically a fairly private system using a specially configured, customized version of Firefox.

---

### Post by SeijiSensei on 2014-04-11
I wonder how many Tor nodes have fixed the [OpenSSL bug]("https://blog.torproject.org/category/tags/openssl") in their implementations.

---

### Post by mattlach on 2014-04-11
> **SeijiSensei said:**
> I wonder how many Tor nodes have fixed the [OpenSSL bug]("https://blog.torproject.org/category/tags/openssl") in their implementations.

Very good point!

And I played with TOR a number of years back.  I found that it was too slow for me.  I wanted privacy, but not at that cost.

---

### Post by sammiev on 2014-04-11
> **PartisanEntity said:**
> I personally have been using Witopia for some years now and I am happy with them. Easy setup for Windows, OSX and Linux.

Been using Witopia for 2 years as well and also would recommend them.

---

### Post by PartisanEntity on 2014-04-12
> **SeijiSensei said:**
> I wonder how many Tor nodes have fixed the [OpenSSL bug]("https://blog.torproject.org/category/tags/openssl") in their implementations.

Concerning TOR, I read that it is quite easy for organizations/agencies with enough resources to setup thousands of exit nodes. How does that affect your privacy when using TOR?

---

### Post by coldraven on 2014-04-12
I don't know about VPNs but I too would be interested in finding a good one.
But for private searches you could try [https://startpage.com/](https://startpage.com/)

I use various add-ons in Firefox to help keep my life private. 
NoScript (Selectively block Javascript)
Ghostery (Blocks widgets and trackers)
BetterPrivacy (gets rid of Flash "Super cookies")
RefControl (Fakes your site visiting history)
AdBlockPlus (Blocks adverts)

If you want to be shocked about how much data is shared about you then install the "Collusion" add-on for a day and then click on it's icon. Scary stuff!

---

### Post by bashiergui on 2014-04-12
> **SeijiSensei said:**
> I wonder how many Tor nodes have fixed the [OpenSSL bug]("https://blog.torproject.org/category/tags/openssl") in their implementations.Yup. Perhaps the only folks with guaranteed privacy are luddites.

---

### Post by micjustin33 on 2014-05-13
I'd recommend ExpressVPN, VPNArea, NordVPN they are best for Linux and have good features and security protocols.. at bestvpnservice.com you can read their reviews..

---

### Post by linuxyogi on 2014-05-14
I have used vpnbook for a while. [URL="http://www.vpnbook.com/"]http://www.vpnbook.com/ 

[/URL]

---

### Post by mastablasta on 2014-05-14
are these VPN free?
there is also Logmein Hamachi :)

i wonder why OpenVPN is so difficult to setup. in 85 easy steps... i mean come on...

---

### Post by SeijiSensei on 2014-05-14
For [point-to-point static tunnels]("http://openvpn.net/static.html"), OpenVPN is pretty easy to set up.  I communicate with my public servers and with clients' networks using such tunnels.  With virtual server rental fees down as low as $5/month, setting up your own VPN is pretty inexpensive.

Nevertheless, your terms of service agreement with the virtual server provider probably forbids the use of their machines for copyright infringement.  I don't download torrents on my Linode machines, for instance, because I don't want to put my comfortable relationship with them at risk.

---

### Post by mastablasta on 2014-05-14
yeah well i occasionally play some old games with my bro and i think we would need a more complex setup. was thinkign of doing it on Rpi or an old laptop but i saw the steps that need to be taken, uff...

hamachi on the other hand sets it all up (it's not perfect since it often has connection issues). otherwise we do not need a VPN. but maybe sometimes it would come in handy.

---

### Post by HiImTye on 2014-05-14
> **SeijiSensei said:**
> For [point-to-point static tunnels]("http://openvpn.net/static.html"), OpenVPN is pretty easy to set up.  I communicate with my public servers and with clients' networks using such tunnels.  With virtual server rental fees down as low as $5/month, setting up your own VPN is pretty inexpensive.

Nevertheless, your terms of service agreement with the virtual server provider probably forbids the use of their machines for copyright infringement.  I don't download torrents on my Linode machines, for instance, because I don't want to put my comfortable relationship with them at risk.

iptables is incredibly useful for filtering web traffic by connection ;)

---

### Post by SeijiSensei on 2014-05-15
> **HiImTye said:**
> iptables is incredibly useful for filtering web traffic by connection ;)

Yes it is, but I don't see how that's relevant to either part of my comment.

---

### Post by HiImTye on 2014-05-15
it's relevant in that you can filter your traffic you wish to avoid your VPN (or whatever other service you wish to avoid) so that it never goes to it

---

