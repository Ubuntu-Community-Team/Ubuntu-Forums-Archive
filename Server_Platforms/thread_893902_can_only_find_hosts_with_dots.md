---
title: "can only find hosts with dots"
date: 2008-08-18
forum: Server Platforms
---

### Post by Elisei on 2008-08-18
hi there.

i've set up a dnsmasq as a local dns server. the problem that i am having is that other pachines on this network can only find host names if a dot (.) is appended to the end of the name:

for example : [http://test-server/](http://test-server/) is found on the server machine that has dnsmasq running but to open it on windows machine we have to to : [http://test-server./](http://test-server./) .

my /etc/hosts file looks like this:
127.0.0.1	localhost.localdomain localhost
192.168.1.14    test-server.localdomain  test-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

any suggestions are greatly appreciated, thanks;

---

### Post by cariboo on 2008-08-19
You don need dnsmasq or a dns server unless your are working with a large number of computers, if you are just running this on your local network just edit your hosts files to look like this:

```
127.0.0.1 localhost
192.168.1.14 test-server

```

You don't need any of the ipv6 entrues if you don't plan on using ipv6.

Jim

---

### Post by MJN on 2008-08-19
It is likely down to the configuration of the Windows client. Specifically, without adding the trailing period (indicating the root) it is adding on a search domain i.e. making the name fully qualified in order to ensure a resolution.
 
Increase the logging verbosity of dnsmasq or run a packet sniffer on the server (or client) to see exactly what request is being made. The suffix you'll see will give you an idea where the fault lies.
 
Edit: Having read [this post]("http://faqshop.com/forums/viewtopic.php?t=395") (looking through the rant) it would appear that even in the absence of a domain suffix Windows clients may well not make a DNS request at all for non-qualified names Hence your only solution would be to use a domain suffix for your DNS or, as mentioned above, not use DNS at all. This behaviour is probably a hangover from the days of NETBIOS and its differentiation with DNS.
 
Mathew

---

### Post by Elisei on 2008-08-19
thanks ! i added a dot (.) as a suffix in windows and it seems (3 knocks on the wood) to be working;

---

### Post by MJN on 2008-08-19
Ah, yes - good thinking! I hadn't thought to just add a . as the suffix (I'm surprised it didn't baulk at the idea)

Mathew

---

