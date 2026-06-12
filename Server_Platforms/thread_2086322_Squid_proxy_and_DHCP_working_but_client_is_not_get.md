---
title: "Squid proxy and DHCP working but client is not getting internet"
date: 2012-11-20
forum: Server Platforms
---

### Post by lestertorres on 2012-11-20
I have configured my ISC-DHCP-SERVER and it is working. I have my SQUID3 PROXY working as well. When I access internet through the server pc with proxy configured I can access internet but when I connect a client to the server (eth1) it shows that there is a connection with DHCP giving it an ip add, broadcast, etc. but when I open a web browser it gives me a *unable to resolve the server's dns address* but I am using Google dns of 8.8.8.8 8.8.4.4

Any ideas?

---

### Post by Kirk Schnable on 2012-11-20
Any number of possibilities here... it could be a misconfiguration in your Squid proxy, a DHCP issue, a missing default gateway, or other things.  In order to better help the Ubuntu Forum community solve your question, please respond to the below.


**Please respond to these questions about the client:**
Can you ping internal IP addresses, like the IP address of your router?
ex: ping -c 4 192.168.1.1

Can you ping external IP addresses, like the IP address of Google DNS?
ex: ping -c 4 8.8.8.8

Can you ping a domain name and get an IP address from it, such as Google.com?
ex: ping -c 4 google.com


**Please run these commands on the client, and post the output for us.**
```
sudo ifconfig
```

```
sudo route -n
```


From there, we should have a better idea of what's going on.

Thanks,
Kirk

---

### Post by Kirk Schnable on 2012-11-20
Why is this thread marked as solved?  Did you figure it out on your own?

Cheers
Kirk

---

### Post by lestertorres on 2012-11-21
Hi Kirk,

I actually did figure out. Thanks for the reply. What I did was configure the dns to my providers dns (AT&T) and it began work after. Its all set up good now and working. Thanks again!

---

