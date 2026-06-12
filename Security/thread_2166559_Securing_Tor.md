---
title: "Securing Tor"
date: 2013-08-10
forum: Security
---

### Post by HaviarBarbar on 2013-08-10
Ive been doing some research into improving the security of my Tor connections and came across two sites.

They both advocate the use of multiple Tor and Privoxy services running simultaneously and managed by Squid.

My concern is that the guides where written in '08 and '09.

Are they still valid? Is there a better way of doing things?

[http://www.howtoforge.com/ultimate-security-proxy-with-tor](http://www.howtoforge.com/ultimate-security-proxy-with-tor)
Example Image of proposed Network: [http://img300.imageshack.us/img300/636/torprivoxysquid.png](http://img300.imageshack.us/img300/636/torprivoxysquid.png)

[http://body0r.wordpress.com/2009/06/24/tor-privoxy-squid-a-little-howto/](http://body0r.wordpress.com/2009/06/24/tor-privoxy-squid-a-little-howto/)
Example Image of proposed Network: [http://body0r.files.wordpress.com/2009/06/squidprivtor.png](http://body0r.files.wordpress.com/2009/06/squidprivtor.png)

---

### Post by Hungry Man on 2013-08-10
Step 1) Set NoScript to disable Javascript globally

Step 2) Create an Apparmor profile for Vidalia, and a profile for the TOR Firefox.

That'll stop that stupid FBI attack recently. But in terms of ensuring that your TOR traffic remains encrypted, not sure what you can do, not my area.

---

### Post by Traxster on 2013-08-10
> **Hungry Man said:**
> 

That'll stop that stupid FBI attack recently. But in terms of ensuring that your TOR traffic remains encrypted, not sure what you can do, not my area.

I think [this]("http://www.thewhir.com/web-hosting-news/fbi-likely-behind-new-malware-that-attacks-tor-anonymity-say-researchers") article is what you are talking about.

---

### Post by Hungry Man on 2013-08-10
That's correct.

---

### Post by samiux on 2013-08-10
> **Traxster said:**
> I think [this]("http://www.thewhir.com/web-hosting-news/fbi-likely-behind-new-malware-that-attacks-tor-anonymity-say-researchers") article is what you are talking about.

Freedom Hosting of hidden services of Tor network is not compromised by FBI but NSA instead.  For details, please read [this article]("http://samiux.blogspot.com/2013/08/anonymity-network-tor-has-been.html").

Samiux

---

### Post by HaviarBarbar on 2013-08-10
Are the mentioned guides still valid for 13.04? Should I use any different programs then Privoxy or Squid?

Thanks for the replies so far, some good reading and learning.

---

### Post by samiux on 2013-08-10
> **HaviarBarbar said:**
> Are the mentioned guides still valid for 13.04? Should I use any different programs then Privoxy or Squid?

Thanks for the replies so far, some good reading and learning.

NightHawk only tested on Ubuntu 12.04 LTS.  I did not test it on 13.04 or 13.10.  By the way, it only works on Ubuntu.

Samiux

---

### Post by HaviarBarbar on 2013-08-13
My main question still hasn't really been answered. I will rephrase it. The above mentioned guides propose a more anonymous and secured network. The setup of this new network would take a good deal of time.

Is there anything that I should add to the setup to harden it or something to take out that weakens it?
Are there better ways of going about achieving the proposed "Ultimate Network Security"?

I don't mind the work or spending vast amounts of time on nailing down my network/Internet anonymity and security. I am currently in the process of setting up a local DNS Server utilizing [http://insanitybit.com/](http://insanitybit.com/) as the primary lookup.

---

### Post by samiux on 2013-08-13
> **HaviarBarbar said:**
> My main question still hasn't really been answered. I will rephrase it. The above mentioned guides propose a more anonymous and secured network. The setup of this new network would take a good deal of time.

Is there anything that I should add to the setup to harden it or something to take out that weakens it?
Are there better ways of going about achieving the proposed "Ultimate Network Security"?

I don't mind the work or spending vast amounts of time on nailing down my network/Internet anonymity and security. I am currently in the process of setting up a local DNS Server utilizing [http://insanitybit.com/](http://insanitybit.com/) as the primary lookup.

In my opinion, anonymity and security is two different things although hackers may found anonymity can protect themselves from being revealing their IP addresses.

For the DNS server, I recommend you to read [this article]("http://technet.microsoft.com/en-us/security/hh972393.aspx") before going further if you are really interested in security.

Samiux

---

