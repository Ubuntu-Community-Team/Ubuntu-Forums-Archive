---
title: "nslookup vs the nameserver"
date: 2011-05-21
forum: Security
---

### Post by conradin on 2011-05-21
hi all, perhaps I'm just being paranoid but I'm wondering how much information my company name-server should give up when any-ol-joe 
uses nslookup on a company ip. 

I can understand, that internal nslookup requests should get processed in one way or another. As in from an internal IP, I could gather other internal IP addresses host-names, and server info. What I'm having trouble with, is how come I (or anyone, anywhere) can leave the company network, and still successfully use nslookup to get host-names with corresponding IPs and routing info. 

Am I just being paranoid? or is this a serious problem?
```
nslookup ip
```

---

### Post by HermanAB on 2011-05-23
Why do you allow 'any old joe' to access your internal DNS?  Firewall it.

---

### Post by conradin on 2011-05-23
Im thinking that the name-server could have a designation of which servers to respond to. I think thats a setup in BIND 8 and higher. 

I didn't set this stuff up, and I don't have direct access to the setup of the system, so I can not make any changes just yet. 

What I need to do is make a good case about why it needs to be changed, either in BIND and or with a firewall as well. Thats Just the bureaucracy of it. 

That said, can anyone give me a solid argument to fix this? I spoke with some guys in networking, and they just don't seem to think its a problem. 
I have a list of roughly 21000 hosts which are plainly visible from anywhere, via the name-server, including network resources, like printers, cameras, conference devices, etc.. but also poorly named hosts like "2ndFloorFiniancialDept@"  and so on. 

My perspective is this is a massive fault, any hacker / script-kiddie who stumbles on to the name-server would have thousands of opportunities to strike network resources. Additionally, "secure clients" are still visible from the net because the name-server confirms their identity.

For example, when I port-scan my department, I get 18 hosts which respond to ping requests. I know for a fact there are 246 clients on our subnet, of which I have made most of them drop unsolicited packets etc.  Should someone poll the name-server, those 228 clients would be visible with both hostname, IP and routing IPs.

What other arguments Can I make to try and get the guys in Networking to fix this??

---

### Post by HermanAB on 2011-05-23
I don't think it matters what information the DNS divulges.  However, if your internal DNS is accessible from the wild wild world, then anyone on the planet can DOS your private DNS with recursive querries.

---

### Post by tgm4883 on 2011-05-23
Why is there not a perimeter firewall between your internal network and the internet?

---

