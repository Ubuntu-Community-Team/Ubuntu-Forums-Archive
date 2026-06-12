---
title: "VPN &amp; security"
date: 2013-04-08
forum: Security
---

### Post by Lupi on 2013-04-08
I have a question regarding VPN and whether it's worth using it. I am often on the internet and security is always a concern. I've recently heard that having a VPN makes it much more secure when using internet. Is it true? I've also heard that some people use a VPN for file sharing (like torrents). Does this mean that, thanks to a VPN, even file sharing is anonymous and that nobody, even their internet providers, can see the traffic that took place?

Thanks

---

### Post by Soul-Sing on 2013-04-08
> Does this mean that, thanks to a VPN, even file sharing is anonymous and that nobody, even their internet providers, can see the traffic that took place?

It depends on the license, terms of use. That's different with each VPN service. You have to read them. And take a look at reviews on the internet.

---

### Post by CharlesA on 2013-04-08
Don't forget that security isn't the same thing as privacy.

Just throwing that out there.

---

### Post by mike acker on 2013-04-08
> **Lupi said:**
> I have a question regarding VPN and whether it's worth using it. I am often on the internet and security is always a concern. I've recently heard that having a VPN makes it much more secure when using internet. Is it true? I've also heard that some people use a VPN for file sharing (like torrents). Does this mean that, thanks to a VPN, even file sharing is anonymous and that nobody, even their internet providers, can see the traffic that took place?

Thanks

the critical point to remember about security is that hackers often -- if not generally -- use un-authorized programming, often know as "malware", -- to compromise their victim

if you have, for example, a root-kit infecting your PC then nothing in the way of VPNs, or 2-factor passwords, or PGP encryption -- is of any use . the malware becomes your eyes and hands, reading your screen and providing inputs

a banking trojan for example can wait for you to log into your bank and then use your credentials to transfer all your funds to the Ukraine and then display your screen showing you paid your house payment and your other bills and have the proper balance remaining

when you get the over-due note from your mortgage company it's too late to recover the money

this, in my view, is the strongest argument to favor Linux over alternate systems.  you may have noticed that with Ubuntu/Linux we normally do not run logged on as "root".  --I don't even have the password to log on as root.  this is a major difference from other systems -- in which you can do whatever you please. 

i can use sudo to update an app on my system but -- as i understand it -- the scope of the sudo activity will be limited to the terminal session which i use for the install.

the critical point in computer security is in restricting such software updates.  "Approved software only" is the Order of the Day; otherwise you proceed at your own risk

---

### Post by Lupi on 2013-04-09
Thanks for the input.

---

### Post by salamat2 on 2013-04-12
I need also some help on this subject. How to install dnscrypt-proxy in a simple way. I have downloaded the package from dnscrypt.org and convert it to .deb but it did not install properly and it is wraped with lock. Is there a good dnscrypt-proxy in deb format. Tanks.

---

### Post by CharlesA on 2013-04-12
See here:
[https://github.com/opendns/dnscrypt-proxy](https://github.com/opendns/dnscrypt-proxy)

And here:
[http://askubuntu.com/questions/108390/dnscrypt-proxy-not-working](http://askubuntu.com/questions/108390/dnscrypt-proxy-not-working)

---

### Post by Clicksights on 2013-04-13
> **Lupi said:**
> I have a question regarding VPN and whether it's  worth using it. I am often on the internet and security is always a  concern. I've recently heard that having a VPN makes it much more secure  when using internet. Is it true? I've also heard that some people use a  VPN for file sharing (like torrents). Does this mean that, thanks to a  VPN, even file sharing is anonymous and that nobody, even their internet  providers, can see the traffic that took place?

Thanks

Your question, if i filtered it right, is: makes using VPN my internet  connection saver? And can i use it for filesharing and am i sharing  anonymous if i use VPN?

As said above, your computer is as save as you make it... And a password  is as save as you keep/make it! Keeping that in mind... 
(don't stick your password on a paper on the monitor... Yes i've seen it!!!)
If you set up VPN correctly, i would say YES.

A VPN encrypts your connection (no-one can look at the data you are  sending/recieving, it can be used to stop ISP block) and (most) change  your IP (makes it _more_ anonymous)
Certainly on open networks, and wireless networks i would use VPN. 

Depending on the VPN provider you can use your bittorrent on the VPN to make sharing more safe.
Keep in mind that it takes a lot more to do save file sharing, like  using a ban list, setting up your client the correct way etc. to stay  anonymous.
I am not going to expand on that.

Now all that said, keeping to the topic, VPN is as safe as you make it, just using VPN doesnt garranty your safe and anonymous.
VPN has to be set up correctly, use an anonymous email address, pay  anonymous and you have to find a secure and good VPN provider (no logs)  and _set your browser setting correctly_. (cookies, history, etc)

As on advice on VPN, it is very easy to set it up in Ubuntu, i prefer  OpenVPN not PPTP, (is fundamentally insecure) there is are several good  tuto's on it.
And after setting up your VPN you need to keep some things in mind, your  browser still gives a lot away, opening a movie can give your real ip,  as can scripts (Anonymity test see links), watch out for DNSleaks, what  provider you choose (see links below) and how you pay...

Alternative you can use TOR or JonDO, Both free, but slow. NOT for filesharing!
I like the JonDoFox (gives also firefox profiles) as you can make several Firefox profiles, and choose between TOR and JonDo.

Usefull Firefox Browser Ad-ons:

https-everywhere: Always use Https if available! It isnt as good  encrypted or as safe as VPN but it is saver than http. (you can use  https IN your VPN tunnel).
Googlesharing: To anonimize your google searches
No-script : stop scripts
Cookie monster : manage cookies
Better privacy : removing lso cookies
AdBlock+ : Remove annoying adds.

Usefull links: 

Basics - Wikki : [https://en.wikipedia.org/wiki/Virtual_private_network](https://en.wikipedia.org/wiki/Virtual_private_network)
DNS leaktest :  [http://www.dnsleaktest.com/](http://www.dnsleaktest.com/)
Torrentfreak:    [https://torrentfreak.com/how-to-make-vpns-even-more-secure-120419/](https://torrentfreak.com/how-to-make-vpns-even-more-secure-120419/)
VPN providers:  [https://torrentfreak.com/which-vpn-providers-really-take-anonymity-seriously-111007/](https://torrentfreak.com/which-vpn-providers-really-take-anonymity-seriously-111007/)
                      [https://torrentfreak.com/vpn-services-that-take-your-anonymity-seriously-2013-edition-130302/](https://torrentfreak.com/vpn-services-that-take-your-anonymity-seriously-2013-edition-130302/)
Anonymity test: [http://ip-check.info/](http://ip-check.info/)
JonDoFox :        [https://anonymous-proxy-servers.net/](https://anonymous-proxy-servers.net/)
TOR :               [https://www.torproject.org/](https://www.torproject.org/)                     

Ow and there is no such thing as free VPN, as in free beer.... :wink:
                     
Hope it helps...

---

### Post by HermanAB on 2013-04-14
Uhmmm, a VPN or a proxy server only forwards your connection somewhere else.  So while you are in a coffee shop in Praha CZ, your connection appears to be in Scottsdale AZ for example.  Apart from that, it does nothing.  So, it may protect you against a WiFi sniffer at the next table, but it will do nothing against a sniffer installed on a web site that you are visiting, or on the VPN/proxy server that you are using.

I think that most people using VPN/Proxy connections will be better served by the Tor Browser Bundle, which costs nothing and results in the same thing:
[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

---

### Post by Soul-Sing on 2013-04-14
> **HermanAB said:**
> Uhmmm, a VPN or a proxy server only forwards your connection somewhere else.  So while you are in a coffee shop in Praha CZ, your connection appears to be in Scottsdale AZ for example.  Apart from that, it does nothing.  So, it may protect you against a WiFi sniffer at the next table, but it will do nothing against a sniffer installed on a web site that you are visiting, or on the VPN/proxy server that you are using.

I think that most people using VPN/Proxy connections will be better served by the Tor Browser Bundle, which costs nothing and results in the same thing:
[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

A VPN service with openvpn in it, will protect you on open wifi spots, and increases security. Why would TOR do the same?
VPN services without PPPoE protcol are imho the best.

---

### Post by HermanAB on 2013-04-16
Tor encrypts your connection inside the Tor network, so it provides the same protection as a VPN when you are in a coffee shop.

Because I live in a somewhat weird country, I use Tor all the time.  It is significantly slower than a SSH socks proxy to a dedicated server, but it costs nothing, so I can't complain.

---

### Post by Solsun on 2013-04-18
Tor is great for open wifi connections but not for downloading anonymously and VPN's typically wont protect you from doing illegal things and will give out your information if pressured.  A slow option would be to read up on i2p and i2psnark.  Speeds are real slow but if privacy/anonymity is your concern then it is an option.

---

### Post by Flatuance on 2013-04-18
I would have to agree with the previous posts.  I currently use WiTopia VPN on all of my Linux boxes and I've been very happy with the level of protection and service.  I still make sure that each of my PCs are secured locally with good firewall rules, AppArmor profiles, and installing software from trusted sources.  Clicksights (Post #8) was right on about using those Add-ons for Firefox.  I would even add Ghostery to the list as a very useful Add-on too.  :)

---

