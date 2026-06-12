---
title: "DNS Setup - Tricky"
date: 2012-12-12
forum: Server Platforms
---

### Post by Houseton on 2012-12-12
I am trying to setup a DNS server when certain sites get requested those sites get a different IP address than the that of the client requesting it (to get around IP Location and help with anonymity)

Example:
Client 1 puts a DNS server address in USA as their primary/secondary DNS (the one I am setting up)

Client 1 wants to go to site.com (which displays stuff based on IP location targeted ads or anything like that)

When site.com receives the DNS lookup, the IP address that is sees is of the DNS server and not Client 1.

I not too sure how this works, I know it does work. I've looked up DNS spoofing (but that is more attack based). 

Does anyone have any input on this? What this would entail?

Thanks for any input.

edit:
This may be firewall related, now that I think about it....
If this was programming it would probably look like this
[Crappy code ahead haha]
If dns-search = *.site.com or site.com
then ipaddress = server
else ipadress = client
end if

---

### Post by Cheesemill on 2012-12-12
For this to work you need to set up a proxy server or a VPN, it has nothing to do with DNS.

---

### Post by dannyboy79 on 2012-12-12
i don't think that's possible. if you're trying to hide your IP, that's more like using an IP as a proxy so traffic is routed through the US based location and doesn't ever show the real IP. this may be over my understanding with the dns stuff

---

### Post by Houseton on 2012-12-12
Pretty much trying to set-up something like unblock-us, if you know what that service is. 

Now this service uses DNS and from what I've seen a reverse proxy to work.

All it does is tell services it is in the US. All the actual data stream to the client's IP address. That is what I am trying to re-create on a very small scale.

---

### Post by koenn on 2012-12-12
what cheesemill said.

Think about it; how would that work : you send a site a request, with a fake client ip address. Where is the reply to that request going to be sent to ? How would it ever reach the client ?

---

### Post by Houseton on 2012-12-12
I understand how the IP address system works... Maybe the DNS server is just for authentication purposes... I'm just wondering as to how it works. Unblock-us works. 
I thought it had to do with spoofing very specific look ups so that an authentication on those sites clears the check for IP location and allows access to more features.

---

### Post by koenn on 2012-12-12
i don't doubt unblock-us works.

I'm just saying your DNS-based attempt to mimic it makes no sense.

---

### Post by Cheesemill on 2012-12-12
From what I can gather looking at their website Unblock Us is a combination of a standard VPN solution and a custom DNS server. DNS lookups for certain sites return the IP address of their VPN server which acts as a proxy so that only traffic for specific sites gets routed through it instead of all your traffic.

---

### Post by Houseton on 2012-12-12
That makes more sense then the DNS thing I thought they were doing. So replicating that would need not only a DNS server but some sort of proxy or VPN... Putting the cost for a single user higher than needed.

Although A DNS server doesn't need much of anything... I think I could replicate that for about $10-15/month. The fun part would be setting up the DNS server and VPN/reverse proxy and having it work correctly.

Thanks to all for your input! Much appreciated!

---

