---
title: "What is the best SSH Proxy Pay Service?"
date: 2008-10-22
forum: Security
---

### Post by user9015 on 2008-10-22
What is everybody's opinion as to which is the best pay SSH Proxy Service in terms of low cost and anonymity?  I'm trying to choose a service, but certainly don't want a "honey-pot" whom would be quick to hand over my information.

Thanks,

Linux Newbie

---

### Post by pirattrev on 2008-10-22
same question, I'm going to China soon and I want to avoid people (and the chinese government) snooping in on me. Is a service best or should I just set up my own proxy/pseudo-anonymizer from my own domain. For the previous statement, how would I go about doing that? Anyone?

---

### Post by Gamma746 on 2008-10-23
You could use Tor.  [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by user9015 on 2008-10-24
i used tor....  and found it extremely slow

---

### Post by hyper_ch on 2008-10-24
you cuold a server or rent a virtual private server. you could then setup a vpn to the server and use it as proxy - the cheapest dedicated servers I've seen are &#8364; 20.-/m

---

### Post by admash on 2008-10-24
I have used [www.findnot.com]("http://www.findnot.com") for years. They have ssh and OpenVPN available with each subscription, offer 30 servers and are 13.00 per month.

---

### Post by daleus on 2008-11-05
13 per month? you could get a whole VPS server for £5/$10usd a month!

vt6.co.uk we're always great, so we're cheapvps!

---

### Post by horizonuser on 2008-11-05
You would need to be certain that the network you're on allow outward VPN connections. You would be better tunneling over port 80 if you can. Can't you setup an SSH server on your Ubuntu box at home and tunnel through that?

---

### Post by daleus on 2008-11-07
> **horizonuser said:**
> ou would be better tunneling over port 80 if you can.

A great idea, although may I suggest port 443?
443 is usually used for secure http traffic, and even corporate firewalls have it open for https sessions (web based email needs it, web banking, anything that uses a secure connection)
Also, encrypted traffic would probably go 'less' noticed on there as all the other traffic on there is also secure.

---

### Post by Chayak on 2008-11-08
> **user9015 said:**
> i used tor....  and found it extremely slow

Tor may be slow but that's the price you pay for anonymity.  It's probably the safest to use in China.  If you use an SSH proxy make sure you test it before you go in country and when you connect make sure the key doesn't change.   I remember mention somewhere of some man in the middle attacks during the Olympics.  If you get a warning that they key has changed on the SSH server don't accept, disconnect.

---

### Post by daleus on 2008-11-13
Tor really isn't secure and I wouldn't trust it for any kind of information.

Anyone who wants to be a tor node, can just sniff everything they send/transmit.

anyhow, if you do need to use the internet via ssh, and you are using firefox, type about:config and find "remotedns" and set it to TRUE, otherwise every dns request you make goes through your normal internet connection, allowing people to basically know what sites you are going on.

---

### Post by rosv on 2008-11-13
One suggestion might be to set up your own ssh server. Then use ssh -D 5555 username@youbox to configure a ssh tunnel from your client PC to your ssh server. If you want to use this tunnel from firefox, simply add 127.0.0.1 on port 5555 as your proxy server.

---

### Post by rosv on 2008-11-13
I should probably mention that ssh -D doesn't work in firefox 3. Due to......well a bug. See [http://ubuntuforums.org/showthread.php?t=787982]("http://ubuntuforums.org/showthread.php?t=787982") for more info.

---

### Post by hyper_ch on 2008-11-13
> **daleus said:**
> Tor really isn't secure and I wouldn't trust it for any kind of information.

In what way is TOR not secure?

---

### Post by daleus on 2008-11-18
It's not secure due to the fact anyone who acts as an exit node can sniff all traffic they are passing to the internet. The traffic is only encrypted inside the TOR network, those on the edge can sniff what they are sending out.

[[Google]("http://www.google.co.uk/search?q=tor+exit+node+sniffing&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a")]

---

### Post by Gamma746 on 2008-11-18
> **daleus said:**
> It's not secure due to the fact anyone who acts as an exit node can sniff all traffic they are passing to the internet. The traffic is only encrypted inside the TOR network, those on the edge can sniff what they are sending out.

[[Google]("http://www.google.co.uk/search?q=tor+exit+node+sniffing&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a")]

That's no worse than not using Tor in the first place.

---

### Post by shqip on 2008-11-18
[try this one]("http://proxify.com/")

---

### Post by hyper_ch on 2008-11-19
> **daleus said:**
> It's not secure due to the fact anyone who acts as an exit node can sniff all traffic they are passing to the internet. The traffic is only encrypted inside the TOR network, those on the edge can sniff what they are sending out.

TOR does not encrypt anything. TOR is an anonymizer, not an encrypting tool. So, TOR is secure for what it's intented to do.

---

### Post by daleus on 2008-11-20
If your trafic is being sniffed, you really aren't going to be anonymous, Your browsing habits and traffic through tor will show who you are sooner or later.

Also, not on the same point, but it's deathly slow.

---

### Post by hyper_ch on 2008-11-20
> **daleus said:**
> If your trafic is being sniffed, you really aren't going to be anonymous
you are ;) it can't be traced where the query originates from and where it is aimed to ;)

> 
Description

Aiming to protect its users against traffic analysis attacks, volunteers operate an overlay network of onion routers that enable anonymous outgoing connections and anonymous "hidden" services.

So, tell me again, in what way is TOR not secure - and keep in mind what TOR is designed for ;)

---

