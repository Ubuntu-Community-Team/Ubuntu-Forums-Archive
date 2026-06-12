---
title: "Tor, Polipo, and DNS leaks."
date: 2010-04-09
forum: Security
---

### Post by zozza on 2010-04-09
I want to clarify the situation about Tor, Polipo, and DNS resolution.

My current set-up is that Firefox is set to transport all HTTP and HTTPS traffic through port 8118 (Polipo) which then forwards all traffic to Tor on port 9050. 

AIUI, DNS requests are pushed through the HTTP proxy (Polipo) which then transfers them to the SOCKS proxy (Tor).   Tor then does the DNS resolution at the final exit node.

Can you confirm that both Polipo and Tor bypass my ISPs DNS?  And I think that Tor does the DNS resolution, not Polipo?

I know I can use Tor directly and setup Firefox with network.proxy.socks-remote_dns = true but I am talking here about using Polipo and Tor. 

Thanks.

---

### Post by cdenley on 2010-04-09
If polipo handles the request, then it will send the DNS query through the parent proxy, if one is configured. Firefox doesn't have to resolve the DNS in order to send a request to an http proxy (polipo). If firefox attempts to make a connection without using polipo (such as an FTP connection), then whether or not it sends the DNS query through the socks server (tor) depends on the setting network.proxy.socks-remote_dns.

I'm fairly sure about this, and the packet captures I just performed seem to support this.

---

### Post by zozza on 2010-04-10
Thanks.  

So, to confirm, if Polipo is forwarded to Tor then Polipo will never do DNS resolution itself and pass that on to Tor?  Tor does the DNS resolution at the final exit node. 

I ask because in the Polipo configuration for Ubuntu located at  [https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf)  the DNS section in the config file says:

# Uncomment this to disable Polipo's DNS resolver and use the system's 
# default resolver instead. If you do that, Polipo will freeze during 
# every DNS query: 

dnsUseGethostbyname = yes 

However, section 3.9 of the Polipo manual says: 

Polipo usually tries to speak the DNS protocol itself rather than using  the system re- 
solver5 . Its precise behaviour is controlled by the value of  dnsUseGethostbyname. If 
dnsUseGethostbyname is false, Polipo never uses the system resolver. If  it is reluctantly 
(the default), Polipo tries to speak DNS and falls back to the system resolver if a name server could not be contacted. If it is happily, Polipo tries to speak DNS, and  falls back to the system resolver if the host couldn’t be found for any reason (this is not a  good idea for shared proxies). Finally, if dnsUseGethostbyname is true, Polipo never tries to speak DNS itself and uses the system resolver straight away (this is not recommended). 

Since "yes" is not one of the four options listed in 3.9 what  does this mean? 

I assume that the "yes" does not matter since Polipo is not doing the DNS but simply passing the request on to Tor for it to do the resolution.  

Does that sound correct?

---

### Post by cdenley on 2010-04-10
> **zozza said:**
> 
So, to confirm, if Polipo is forwarded to Tor then Polipo will never do DNS resolution itself and pass that on to Tor?  Tor does the DNS resolution at the final exit node. 


Yes, it does it through tor. There may be a setting to forcibly change this, but I tested with the default configuration for polipo, and there were no DNS queries sent unencrypted.

---

### Post by zozza on 2010-04-10
When you say tested I assume you used Wireshark or tcpdump?

I have never used this type of software - I wonder if you could suggest the best one for a total novice. 

Also, if you look at the section 3.9 options, my point is that if one changed the setting from "yes" (which,  as mentioned, does not exist) to for example "reluctantly" then I will assume (but I do not know) that DNS would still go via Tor because ALL traffic is set to be forwarded to Tor - would this be correct in your opinion?

Thanks.

---

### Post by cdenley on 2010-04-10
I used wireshark. I only use tcpdump if there is no GUI, then use wireshark to view the traffic I captured with tcpdump.

By default, the setting you mentioned is commented out in ubuntu. I'm not sure what uncommenting it would do since "yes" isn't a value listed in the documentation. Reading the documentation, it seems that by default, if polipo's DNS resolver (through tor) fails to use a nameserver, then the system resolver would be used by default, which would leak DNS queries. I'm not sure how DNS works with tor or if this can happen. I think setting it to false would ensure you never have a DNS leak.

---

### Post by zozza on 2010-04-11
My setting is now "false" but previously it was "yes".

Actually, in the Polipo config here [https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf) that the Tor people say you should use in place of the Polipo config that comes with Polipo, the "yes" is uncommented so I assume this means that this value is ignored because I cannot imagine the Tor people would write it so DNS was leaked due to a value that did not exist.

---

### Post by cdenley on 2010-04-11
I just tested it, and yes is the same as true, and no is the same as false. Also, with either setting, I couldn't seem to generate any unencrypted DNS queries, so maybe using the system resolver still tunnels it through tor.

---

### Post by zozza on 2010-04-12
Thanks - I need to learn Wireshark!

So, to confirm, I think your impression is that all values "true", "false", "reluctantly", and "happily", push all DNS requests (whether from the system resolver or Polipo) through Tor.

I wonder if you tested "reluctantly"?

Is that correct?

Many, many, thanks!

---

### Post by cdenley on 2010-04-12
> **zozza said:**
> Thanks - I need to learn Wireshark!

So, to confirm, I think your impression is that all values "true", "false", "reluctantly", and "happily", push all DNS requests (whether from the system resolver or Polipo) through Tor.

I wonder if you tested "reluctantly"?

Is that correct?

Many, many, thanks!

I briefly tested "true" and "false". This covers both resolvers. Maybe I will test more thoroughly or see if I can understand the source code a little later.

---

