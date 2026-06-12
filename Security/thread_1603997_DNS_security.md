---
title: "DNS security"
date: 2010-10-23
forum: Security
---

### Post by dogdo on 2010-10-23
Can someone please give me a few pointers on how to secure the dns on my network? 

So for ive changed the dns on my home router to Opendns and ive added this [https://addons.mozilla.org/en-US/firefox/addon/64247/](https://addons.mozilla.org/en-US/firefox/addon/64247/) to firefox..

What does a dns attack look like? how would i know is my dns was poisoned or if i was under a kaminsky style attack?

---

### Post by CharlesA on 2010-10-23
Unless you are hosting a server, you really shouldn't have to worry about DNS attacks/poisoning.

---

### Post by wacky_sung on 2010-10-23
> **CharlesA said:**
> Unless you are hosting a server, you really shouldn't have to worry about DNS attacks/poisoning.

Disagreed.Most people perform dns attacks/poisoning is by spoofing themselves and steal your vital information.

See below link in which may be helpful to you.
[http://ubuntuforums.org/showthread.php?t=1551267](http://ubuntuforums.org/showthread.php?t=1551267)

---

### Post by CharlesA on 2010-10-23
> **wacky_sung said:**
> Disagreed.Most people perform dns attacks/poisoning is by spoofing themselves and steal your vital information.

See below link in which may be helpful to you.
[http://ubuntuforums.org/showthread.php?t=1551267](http://ubuntuforums.org/showthread.php?t=1551267)

Talking about hijacking DNS and redirecting a legitimate URL to a phishing site?

I suppose that's possible, but it would be red flagged quickly, wouldn't it?

You'd also need to have something change the DNS settings on your machine to point to a compromised/fake DNS server wouldn't you?

Thanks for the link btw.

---

### Post by wacky_sung on 2010-10-23
> **CharlesA said:**
> Talking about hijacking DNS and redirecting a legitimate URL to a phishing site?

I suppose that's possible, but it would be red flagged quickly, wouldn't it?

You'd also need to have something change the DNS settings on your machine to point to a compromised/fake DNS server wouldn't you?

Thanks for the link btw.

You do not need to change anything on your side to point to a compromised/fake DNS server because the attacker usually did is redirect you to the fake site.The attacker does not really need to attack your system but your dns server.Beside that,MTM(Man in The Middle) often allow the attackers to perform the attacks especially those people using wifi.

---

### Post by CharlesA on 2010-10-23
> **wacky_sung said:**
> You do not need to change anything on your side to point to a compromised/fake DNS server because the attacker usually did is redirect you to the fake site.The attacker does not really need to attack your system but your dns server.Beside that,MTM(Man in The Middle) often allow the attackers to perform the attacks especially those people using wifi.

Gotcha. That makes sense then.

Thanks.

---

### Post by willblock on 2010-10-23
Agreed wacky, wireless attacks on routers are becoming more popular as Easy tools become available.
Have had a D-link router compromised by the old hnap exploit, and then by the dd-wrt root exploit, just redirecting your DNS can easily expose you installing malware. Manualy, or via loaded exploits (PDF anyone?)

---

### Post by OpSecShellshock on 2010-10-24
The easiest way to avoid the most obvious DNS risks (MiTM over wireless, for example) is to never do anything sensitive over a local network outside your control. Actually, I'd extend that to include not merely sensitive activities, but all those that make use of authentication (because those can't all necessarily be described as sensitive). That means no authentication on a public wifi setup, and also means no authentication at work or when you're a guest in someone else's home.

Next, do not configure your home router's administration page to be accessible from the internet. This won't solve everything, but it's a big step. If you absolutely must allow it, then be sure to max out your password length and make it as random as you can. This is probably good practice even if it's not accessible from the internet.

When setting up your own wireless access, use the most robust encryption available. If your router does not offer WPA2, then it will have to be replaced. Sorry.

Check your router's administration page from time to time and make sure that the IP listed for your DNS is actually allocated to your home ISP. Also, make sure that RFC-1918 reserved IP addresses used by your router/within your LAN are never able to resolve to domain names (well, unless you have a server on your LAN that absolutely must have a name rather than an IP address, I suppose). There are certain techniques for spoofing predictable internal IP addresses even though you're communicating with an external host. Using something like NoScript in the browser will help with a lot of that (scripts embedded in web pages are where you'd most likely see that sort of thing) unless you've allowed the site in question to work.

Unfortunately, a lot of DNS hijacking takes place on the server side, at the ISP and/or hosting provider level. Individual providers will have to take care of that themselves, and most of them probably haven't because it's expensive and outside the scope of any data security standard that they'd probably be audited against. This is particularly a problem for consumer ISPs that make use of regional caching.

---

### Post by wacky_sung on 2010-10-24
On the other hand,i personally practice using external dns server as my link posted above to prevent my ISP collection of my personal web surfing habit.Apart from that, some dns server provide additional/ enhance features such as opendns, clearcloud, etc.

---

### Post by CharlesA on 2010-10-24
> **OpSecShellshock said:**
> The easiest way to avoid the most obvious DNS risks (MiTM over wireless, for example) is to never do anything sensitive over a local network outside your control. Actually, I'd extend that to include not merely sensitive activities, but all those that make use of authentication (because those can't all necessarily be described as sensitive). That means no authentication on a public wifi setup, and also means no authentication at work or when you're a guest in someone else's home.

Thanks for the info. Would tunneling yer traffic get around that bit, or would it still be vulnerable, since DNS lookups aren't tunneled (as far as I know at least)?

---

### Post by dogdo on 2010-10-24
> **CharlesA said:**
> Thanks for the info. Would tunneling yer traffic get around that bit, or would it still be vulnerable, since DNS lookups aren't tunneled (as far as I know at least)?

I assume if you were using a vpn then wouldn't dns lookups be also encrypted then? 

I have another question on dns exploits-are most of these socially engineered-eg redirects to phished pages? If there were a viral component to these exploits then is it safe to assume that these wont work on ubuntu?

---

### Post by CharlesA on 2010-10-24
> **dogdo said:**
> I assume if you were using a vpn then wouldn't dns lookups be also encrypted then? 

I was thinking more along the lines of a SOCKS proxy using an SSH tunnel.

---

### Post by OpSecShellshock on 2010-10-24
I would imagine that you could SSH using an IP address directly as a way of avoiding DNS entirely. That wouldn't work if the SSH server was behind a NAT firewall, though. If you don't know what the IP address of the server is going to be at any given time, there may not be a way around the use of DNS.

The problem is that DNS expects things to be a certain way, such that if the DNS was hijacked you'd only ever get NXDOMAIN responses from the DNS server. Unfortunately, respecting the protocol is voluntary, which is why there are things such as landing pages with ads on them when a domain fails to resolve properly  (at least for some providers).

I suspect that in the case of hijacked DNS, the SSH session would simply fail unless the server had been configured to only redirect certain sites (which is probably more likely). I assume that once the tunnel is established, domain resolution is done by the SSH server, and not on the client side. Hopefully that's  the case.

---

### Post by OpSecShellshock on 2010-10-24
> **dogdo said:**
> I have another question on dns exploits-are most of these socially engineered-eg redirects to phished pages? If there were a viral component to these exploits then is it safe to assume that these wont work on ubuntu?

I think that for the most part they'd all technically fall under MiTM. There might be an initial phase where the local settings are altered on the client side by way of a trojan, but those would mostly be written for Windows, and would be stymied by permissions in Linux. Phishing by using email links is different than DNS hijacking, in that a phish is not using the real domain name, whereas a DNS hijack would. The net effect, of course, would be the same (i.e. credential and authentication compromise).

It is also important to keep in mind that DNS can be hijacked without making any changes at all to the client system. There are perfectly good low-tech methods like impersonating site administrators on the phone, and there are site administrator account compromises that can be used at the hosting and registrar levels. There is also the possibility of compromising the website's authoritative name server such that it maps things incorrectly, and sends incorrect information to all DNS servers that perform lookups against it, which then get added to caches or used by other DNS servers downstream. Those techniques don't involve the home user's machine at all.

---

### Post by CharlesA on 2010-10-24
> **OpSecShellshock said:**
> I would imagine that you could SSH using an IP address directly as a way of avoiding DNS entirely. That wouldn't work if the SSH server was behind a NAT firewall, though. If you don't know what the IP address of the server is going to be at any given time, there may not be a way around the use of DNS.

The problem is that DNS expects things to be a certain way, such that if the DNS was hijacked you'd only ever get NXDOMAIN responses from the DNS server. Unfortunately, respecting the protocol is voluntary, which is why there are things such as landing pages with ads on them when a domain fails to resolve properly  (at least for some providers).

I suspect that in the case of hijacked DNS, the SSH session would simply fail unless the server had been configured to only redirect certain sites (which is probably more likely). I assume that once the tunnel is established, domain resolution is done by the SSH server, and not on the client side. Hopefully that's  the case.

Thanks for the info. I've not actually tried seeing if DNS requests are sent locally or over the tunnel, but it would make sense that they would be, since it's acting as a proxy.

---

