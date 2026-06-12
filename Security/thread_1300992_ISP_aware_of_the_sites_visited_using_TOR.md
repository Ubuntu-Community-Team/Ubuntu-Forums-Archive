---
title: "ISP aware of the sites visited using TOR?"
date: 2009-10-25
forum: Security
---

### Post by emigrant on 2009-10-25
Hi,
The annonymity is btwn the user and the site or the ISP also dsnt know the visited sites? (if used TOR)

Thank you very much.

---

### Post by insane_alien on 2009-10-25
no the ISP doesn't know. the people transmitting your data doesn't know either. the exit node knows what site was requested, but not who requested the site. the site itself doesn't know who you are either.

---

### Post by gnuisancev3 on 2009-10-25
actually yes, the ISP can know the sites you visit as Firefox (and most browsers) still send their DNS requests through the normal gateway rather than through the proxy.  This is assuming you use your ISPs DNS servers.  Either way its still transmitted in plaintext and unencrypted.

To solve this in firefox:

1. go to about:config
 2. search for network.proxy.socks_remote_dns
 3. Set to true, which will have the proxy server perform DNS lookups.

---

### Post by emigrant on 2009-10-25
Thanks for the replies. Then what about typing the ip address instead of the url.?
Will this solve the problem?
Thanks a lot.

---

### Post by iwc5893 on 2009-10-25
Your ISP can find out what you've been browsing on the internet over their connections, if they wish to expend the time and effort to do so.  Most of the time, it is not worth it to them unless they have a compelling reason to do so.

---

### Post by __p1n__ on 2009-10-25
There aren't many public Tor exit nodes: [http://torstatus.kgprog.com/](http://torstatus.kgprog.com/) so odds are pretty good that the server traffic is monitored.

Best thing to do is to run a cluster of private Tor servers yourself and run them on servers that you're not connectable with. 

I'm specifically not recommending this but *you* might consider trying a typically vulnerable government that runs Microsoft-IIS/6.0 behind a squid proxy on port 80 to exploit/inject/run your private tor network on.  Please note that it's really critical to acquire formal permission to use anyone else's server for your own purposes.

---

### Post by emigrant on 2009-10-26
hi gnuisancev3, its already set to true :KS
> **gnuisancev3 said:**
> actually yes, the ISP can know the sites you visit as Firefox (and most browsers) still send their DNS requests through the normal gateway rather than through the proxy.  This is assuming you use your ISPs DNS servers.  Either way its still transmitted in plaintext and unencrypted.

To solve this in firefox:

1. go to about:config
 2. search for network.proxy.socks_remote_dns
 3. Set to true, which will have the proxy server perform DNS lookups.

---

### Post by gnuisancev3 on 2009-10-26
> **emigrant said:**
> hi gnuisancev3, its already set to true :KS

then you should be good to go then.  Tor/Privoxy plus that setting in Firefox will protect you from being sniffed or monitored on your local network or by your ISP.

The ISP can see what the exit node is going to, but will not be able to trace that exit node back to you.

I would not put a username and password into any site through any network you don't wholly control, that's not https.   Anyone sniffing the exit traffic of an exit node WILL be able to gain access to usernames and passwords this way.  It's not common for people to do so, but nothing is stopping a malicious hacker from running their own exit nodes.

---

### Post by emigrant on 2009-10-26
thanks for the help gnuisancev3,
on a side note, im not using privoxy; i use polipo :)

---

