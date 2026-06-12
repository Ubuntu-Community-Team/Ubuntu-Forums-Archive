---
title: "DoS by google"
date: 2011-09-12
forum: The Cafe
---

### Post by jarrah-95 on 2011-09-12
so i wake up this morning, and decideto check my router log, it seems that a google based ip has sent a DoS attack at me. does this seem odd to anyone else?

---

### Post by haqking on 2011-09-12
> **jarrah-95 said:**
> so i wake up this morning, and decideto check my router log, it seems that a google based ip has sent a DoS attack at me. does this seem odd to anyone else?


Why do you presume a DoS attack ? was it ACK scans ?

DoS attacks can not be prevented completely from the modem or router. Syn Cookies can allow some protection  against certain types of DoS attacks,  but the effectiveness is limited  and requires the client and server to be preconfigured. By the time a  standard DoS attack hits the modem or router, the pipe is already full.

If you don't have any port forwarding configured on the router, then  you have nothing to worry about from the network side. You are simply  not worth the effort it would take to bypass NAT's firewall effect. Your  biggest threat is from websites and email.

That scan was likely a mass scan of your entire subnet looking for  Apache web servers

as for odd then only thing that is odd about skynet...oops i mean google is there sudden rise to power...LOL ;-)

---

### Post by SlugSlug on 2011-09-12
most likely a spider

---

### Post by jarrah-95 on 2011-09-12
i think your right, on the ack scan, as that is what it was, however even if it was a DoS the router is what stoped it, as most ports are forwarded to no where. but what do you mean about emails and websites?

---

### Post by haqking on 2011-09-12
> **jarrah-95 said:**
> i think your right, on the ack scan, as that is what it was, however even if it was a DoS the router is what stoped it, as most ports are forwarded to no where. but what do you mean about emails and websites?


http requests, get etc and email spam which can help spread the Do or prevent you from using your email.

[http://www.us-cert.gov/cas/tips/ST04-015.html](http://www.us-cert.gov/cas/tips/ST04-015.html)

---

### Post by 3rdalbum on 2011-09-12
> **jarrah-95 said:**
> so i wake up this morning, and decideto check my router log, it seems that a google based ip has sent a DoS attack at me. does this seem odd to anyone else?

It's probably a false positive and not really a DoS. In any case, your router stopped it. If you connect to some popular torrents you might get a pattern of traffic that looks like a DDoS but isn't; even after disconnecting from the torrent in some instances.

---

