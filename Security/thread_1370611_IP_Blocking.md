---
title: "IP Blocking ?"
date: 2010-01-02
forum: Security
---

### Post by Capt_Zaphod on 2010-01-02
Let me start off by saying I'm paranoid and anti-social, not a criminal.  I hate people looking over my shoulder, and I love to work autonomously.

That said, is there a real way to block my IP address?  I'm on Ubuntu 9.10 & have a router.

Thank you;
-Z

---

### Post by lovinglinux on 2010-01-02
Do you mean hide your IP? Then look for [TOR](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29) or a [VPN](http://en.wikipedia.org/wiki/VPN) service. Nevertheless, you can't completely hide your IP. Someone will always be able to see it.

If you are looking for an IP blocker, so you can block unwanted IP addresses, which btw does not protect your privacy, then look for [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/).

---

### Post by teward on 2010-01-02
What you're asking is, "How do I block my external network IP from view to the internet?"


Well, the short answer is "YOU CAN'T"

The long answer is:  "YOU CAN'T, BECAUSE YOU'll F*** UP YOUR INTERNET ACCESS!"  This is because if you're hiding your external IP from things, such as internet servers, there's no way to get the information back to you.  Blocking your external network IP from view means basically not having one, meaning you can't use the internet, and can access things **only **on your local network.

---

### Post by jflaker on 2010-01-02
> **Capt_Zaphod said:**
> Let me start off by saying I'm paranoid and anti-social, not a criminal.  I hate people looking over my shoulder, and I love to work autonomously.

That said, is there a real way to block my IP address?  I'm on Ubuntu 9.10 & have a router.

Thank you;
-Z

please explain what you want to accomplish and we may be able to find a solution to you question.

---

### Post by uljanow on 2010-01-02
Just disable your network card and work autonomously.


Alternatively using a VPN service might be an option.

---

### Post by Capt_Zaphod on 2010-01-03
> **jflaker said:**
> please explain what you want to accomplish and we may be able to find a solution to you question.
On-line invisibility.  I want control of my personal information.  I don't want any information, that I don't chose share, to be available to others.

---

### Post by Capt_Zaphod on 2010-01-03
> **uljanow said:**
> Just disable your network card and work autonomously.


You're quite a card, aren't ya?

---

### Post by Capt_Zaphod on 2010-01-03
> **lovinglinux said:**
> Do you mean hide your IP? 

Yes, that's what I mean.
> **lovinglinux said:**
> Then look for [TOR](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29) or a [VPN](http://en.wikipedia.org/wiki/VPN) service. 

I'll check these out, thank you.

> **lovinglinux said:**
> Nevertheless, you can't completely hide your IP. Someone will always be able to see it.

Had the feeling this would be the answer, but, I was hopeful.

Thank you

---

### Post by Capt_Zaphod on 2010-01-03
> **TrekCaptainUSA said:**
> What you're asking is, "How do I block my external network IP from view to the internet?"


Well, the short answer is "YOU CAN'T"

The long answer is:  "YOU CAN'T, BECAUSE YOU'll F*** UP YOUR INTERNET ACCESS!"  This is because if you're hiding your external IP from things, such as internet servers, there's no way to get the information back to you.  Blocking your external network IP from view means basically not having one, meaning you can't use the internet, and can access things **only **on your local network.

<sighs>  Ya don't need to shout.

My apologies that my question upset you.  I didn't mean to offend.

---

### Post by teward on 2010-01-03
> **Capt_Zaphod said:**
> <sighs>  Ya don't need to shout.

My apologies that my question upset you.  I didn't mean to offend.

Nah, sorry, was half crazed on caffeine overload, was out cold for 6 hours after that.  sorry if it was perceived as shouting, wasn't my intention.  Nevertheless, what I said still stands.  Controlling your personal information is easier than hiding your IP, just dont give any info out unless you have to.

---

### Post by Project PWNED on 2010-01-03
Tor is garbage: it's slow, unreliable, and its too easy for an exit node operator to sniff/capture logins/passwords/emails/etc. The thinking behind running an exit node to capture everything is why are people using Tor anyways? 

You're better off with a VPN, or purchasing a cheap VPS account to build OpenVPN on. You can purchase a VPS account with a prepaid gift card at most gas stations, grocery stores, etc. for $100 which would cover the VPS expenses. I've seen a few VPS accounts advertised online for $5-7/mo with about 100-350gb of transfer a month.

Figure out how much bandwidth you go through a month and see if this is worth it, but any kind of "free" service like Tor has its drawbacks.

---

### Post by HermanAB on 2010-01-04
You can use a Socks Proxy on a server somewhere.  Google for 'Skype VPN' services.  There are lots, but they cost a few Bob a month.

---

### Post by bodhi.zazen on 2010-01-04
I would advise you secure firefox (basically I advise you install NoScript).

Then run a proxy server, such as privoxy.

Last, learn how to configure apparmor and limit the access Firefox has to your home directory.

---

### Post by njdove on 2010-01-05
While I concur that [TOR]("https://www.torproject.org/") is slow and unreliable when used with the Firefox plugin [TorButton]("https://addons.mozilla.org/en-US/firefox/addon/2275") it goes a *long* way to protect privacy. Even though exit nodes can "capture everything", they can't relate that back to the client's IP nor can they correlate data with other exit IPs.

I will add that your ISP will still be able to see your DNS lookups unless you take further measures to avoid this, as discussed in the [TOR FAQ]("https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#IkeepseeingthesewarningsaboutSOCKSandDNSandinformationleaks.ShouldIworry.3F").

---

