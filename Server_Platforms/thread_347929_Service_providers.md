---
title: "Service providers"
date: 2007-01-28
forum: Server Platforms
---

### Post by crabhunter on 2007-01-28
Can any one tell me of a UK service provider that they are able to use Apache/Ubuntu as a webserver.
I am using Talktalk and seem to be having problems.
I have tried port forwarding and although noip is telling me that port 8080 is open I cannot view my content from outside my own network.
Before I goto the ridiculous performance of installing my USB modem to get a direct connection and bypass my router I thought I would try a friends connection, but it would help if I knew one that does work before I try it.
Mike

---

### Post by proxima estacion on 2007-01-28
I am running an Apache2 server from my home PC and use Telewest Blueyonder, Im in the UK. 

I was having problems viewing pages outside of my home network, turned out it was my firewall(!) 

good luck

---

### Post by crabhunter on 2007-01-28
As far as I know the firewall is off on my router and I have a standard install of 6.10 and I cannot see any settings for firewall so I assume there is not one installed.
If there is, where do I find it?
I have not been using Ubunto for very long.
Thanks.
Mike

---

### Post by chrisfay on 2007-01-28
If you didn't actively install one then you don't have one...

But, just to be sure you can run the command:

```
sudo iptables flush
```

...this would 'flush' any firewall rules you have in the form of iptables.

---

### Post by Wim Sturkenboom on 2007-01-28
The output of *sudo iptables -L -n* will tell you which firewall rules apply at that moment.
If the firewall is not running, you will see three sets as below; one for *input* one for *output* (shown) and one for *forward*.
```

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Please note that the policy **must be** *accept*.

---

