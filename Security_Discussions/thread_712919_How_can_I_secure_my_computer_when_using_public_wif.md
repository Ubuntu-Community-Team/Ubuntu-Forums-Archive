---
title: "How can I secure my computer when using public wifi?"
date: 2008-03-02
forum: Security Discussions
---

### Post by joriad on 2008-03-02
I regularly need to use public Wi-Fi to access the internet. i know there are many security issues when using public Wi-Fi's. Can someone tell me all the security issues involved when using these hotspots and solutions I can take to secure my system and information (hardrive, usernames, passwords, browsing history, and other transmitted data).
I would like to make my computer invisible to the server and all other users while still being able to access the server, is this possible?

Thanks for your help.

---

### Post by Jad on 2008-03-02
Spying on public-wifi is common; try to use secure protocols when sufring to make things harder on nosy people; httpS instead of HTTP same applies to IRC and instand messengers. 

I'm sure someone else can elaborate more on this issue.

---

### Post by rickyjones on 2008-03-02
1) Configure IP tables to disregard incoming connections, including ping (echo) requests.
2) Make sure you don't have any unnecessary services installed and/or running (i.e. SSH)
3) If you have SSH installed then change the port to a higher #. I like 22222.
4) Ensure you use strong passwords (at least 7 characters with #s, CAPITALS, and #@%$ symbols).
5) Don't leave your laptop alone.

That is about all that I can think of. Any more than that and you may be bordering on paranoia :P

I hope this helps!

-Richard

---

### Post by julian67 on 2008-03-02
You might want to have a look at [ssh tunnelling](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/) and [VPN](http://en.wikipedia.org/wiki/Virtual_private_network)

SSH tunnelling requires you to have ssh access to a remote computer (perhaps your desktop at home or office) while VPN can be used without having access to another PC. Companies like Relakks make it pretty easy to do and cheap too.  You can google for them, I don't want to post a link as I'm not promoting them, just using them as an example so it's easy to understand.

---

### Post by joriad on 2008-03-02
> **rickyjones said:**
> 1) Configure IP tables to disregard incoming connections, including ping (echo) requests.
2) Make sure you don't have any unnecessary services installed and/or running (i.e. SSH)
3) If you have SSH installed then change the port to a higher #. I like 22222.
4) Ensure you use strong passwords (at least 7 characters with #s, CAPITALS, and #@%$ symbols).
5) Don't leave your laptop alone.

That is about all that I can think of. Any more than that and you may be bordering on paranoia :P

I hope this helps!

-Richard

Ho do I configure Ip tables?

---

### Post by kevdog on 2008-03-02
you could just use a gui like firestater or guarddog since iptables is just a firewall, and these two programs are gui frontends to confgure the iptables.

---

### Post by FakeOutdoorsman on 2008-03-02
I second julian67's recommendation on SSH tunneling, but you must be able to trust the remote computer that you are connecting to.  I used this with great success.  Useful Firefox extensions for SSH tunneling: [SwitchProxy Tool]("https://addons.mozilla.org/en-US/firefox/addon/125") or [FoxyProxy]("https://addons.mozilla.org/en-US/firefox/addon/2464").

Another excellent tool is [Tor with Privoxy]("http://www.torproject.org/overview.html.en"), which can anonymize some online activities (meaning other wi-fi users on the same network don't know what you're doing and the end server doesn't know who you are).  Negatives include often slow service and it shouldn't be used for sensitive information such as connecting to your bank because you can't always fully trust the exit node.  Make sure to always use the [latest versions]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") of Tor/Privoxy ([installation instructions]("http://www.torproject.org/docs/tor-doc-unix.html.en")).  Also make sure to edit the Privoxy config file to disable/minimize logging.

---

### Post by julian67 on 2008-03-02
> **FakeOutdoorsman said:**
> I second julian67's recommendation on SSH tunneling, but you must be able to trust the remote computer that you are connecting to.  I used this with great success.  Useful Firefox extensions for SSH tunneling: [SwitchProxy Tool]("https://addons.mozilla.org/en-US/firefox/addon/125") or [FoxyProxy]("https://addons.mozilla.org/en-US/firefox/addon/2464").

Another excellent tool is [Tor with Privoxy]("http://www.torproject.org/overview.html.en"), which can anonymize some online activities.  Negatives include often slow service and it shouldn't be used for sensitive information such as connecting to your bank because you can't always fully trust the exit node.  Make sure to always use the [latest versions]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") of Tor/Privoxy ([installation instructions]("http://www.torproject.org/docs/tor-doc-unix.html.en")).  Also make sure to edit the Privoxy config file to disable/minimize logging.

I believe with tor you'll be fine with stuff like connecting to your bank because it will be using https not http so even if the exit node is a honey-pot your communication should be secure. What's dangerous is believing your regular unencrypted traffic is in any way secure (although your IP address should remain obscured) as the exit-node admin can capture the lot. I found tor to be mostly useful when I lived in a country whose government routinely blocked foreign news services or even ran transparent proxies and fake websites to capture personal and business information. It let me access such well known left wing subversive organisations such as the BBC news and youtube despite them being blocked by the authorities, who also blocked access to all well known proxy info sites and vendors of anonymising software. Luckily they hadn't got around to modifying or blocking the local debian and ubuntu mirrors so I could get all the free tools I needed :lolflag:

---

### Post by FakeOutdoorsman on 2008-03-02
julian67, I'm curious as to what country you are referring to.

Also, when using an SSH tunnel with Firefox, open about:config and set (this was omitted in the link above):
```
network.proxy.socks_remote_dns = true
```

This will tell Firefox to resolve DNS requests through the tunnel instead of on the local network where other LAN users may be able to see what you're doing.
[URL="http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel"]
Tunneling Firefox traffic over SSH[/URL]
[Encrypt your web browsing session (with an SSH SOCKS proxy)]("http://lifehacker.com/software/ssh/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy-237227.php")

---

### Post by julian67 on 2008-03-02
> **FakeOutdoorsman said:**
> julian67, I'm curious as to what country you are referring to.


Thailand. Even before the military coup they were very keen on censorship and afterwards it just got ridiculous. Luckily they were never that technically accomplished so usually you could see the evidence if they were using transparent proxy and fake sites. They were faking business sites probably to gain commercial information, also I'd assume they were busy collecting mail logins and passwords etc for anyone they were interested in. Using livehttpheaders add-on in Firefox can show you who you are actually connected with and using tor easily bypassed the govt measures (if you could get onto a foreign node). Often parts of BBC news were blocked but laughably if you switched from the graphical site to the text only news site it was all available. Sometimes sites were blocked by one ISP (the govt gives them lists of ip addresses and web sites to block, I even obtained a copy) but another ISP who was a bit slow or less competent/compliant would be making it available. I've been other places (UAE) where you can't even get onto a tor node, they're much more effective at censoship there.

---

### Post by joriad on 2008-03-02
I installed Firestarter and will look into ssh or vpn. hopefully I have Firestarter set up correctly. 

Thanks everyones for the help.

---

### Post by kevdog on 2008-03-02
If you have a router at home that you can run ddwrt -- such as a Linksys, you can flash the firmware so it can accept ssh tunnels.  This way you can tunnel your http connection through a socks proxy to your router at home, and then it leaves unencrypted from the router to the internet.  From your computer at the public wifi, to your router, this part of the connection is encrypted -- the part most likely to be sniffed.  

Although I know this may sound difficult, the whole process is actually very easy to do --- if you have ddwrt installed on your home router.

---

### Post by Skivache on 2008-03-03
> **kevdog said:**
> If you have a router at home that you can run ddwrt -- such as a Linksys, you can flash the firmware so it can accept ssh tunnels.  This way you can tunnel your http connection through a socks proxy to your router at home, and then it leaves unencrypted from the router to the internet.  From your computer at the public wifi, to your router, this part of the connection is encrypted -- the part most likely to be sniffed.  

Although I know this may sound difficult, the whole process is actually very easy to do --- if you have ddwrt installed on your home router.

I would love to know how to do that as I frequently use public wi-fi.Do you have any links to tutorials on how to do the with a linux computer?

---

### Post by PetePete on 2008-03-04
also dont accept any https certificates if they come up with an error. 
many man in the middle attacks use fake certificates to dupe you into thinking that a secure https is really secure when its not.

---

### Post by vik.vaughn on 2008-03-25
kevdog, awesome piece of advice! took me all of 5 seconds to set it up. (I was already using my PC for the same purpose.)

Skivache, here is a good tutorial:

[HOWTO: Tunneling HTTP over SSH with DD-WRT, DynDNS and Putty](" http://jstrassburg.blogspot.com/2006/01/howto-tunneling-http-over-ssh-with-dd.html")

---

### Post by kevdog on 2008-03-26
Yes great link and combine this with the info in this thread (not as thorough but informative):

[http://ubuntuforums.org/showthread.php?t=723025&highlight=tunnel](http://ubuntuforums.org/showthread.php?t=723025&highlight=tunnel)

---

