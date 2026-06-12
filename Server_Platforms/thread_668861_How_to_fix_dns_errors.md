---
title: "How to fix dns errors ?"
date: 2008-01-15
forum: Server Platforms
---

### Post by dwhs.info on 2008-01-15
Hello,i checked on my ubuntu server dns with dnsstuff and i founded 5 error.First error is open dns server,is there tutorial for ubuntu which shows how to fix that?
And other 4 are this one:
1.All nameservers respond	
ERROR: Some of your nameservers listed at the parent nameservers did not respond. The ones that did not respond are:

12.46.148.788


Note: If you are running a Watchguard Firebox with DNS Proxy enabled, there may be a bug causing port numbers get mixed up -- if this is the case, you can contact Watchguard to see if they have a fix.

2.Missing (stealth) nameservers
FAIL: You have one or more missing (stealth) nameservers. The following nameserver(s) are listed (at your nameservers) as nameservers for your domain, but are not listed at the parent nameservers (therefore, they may or may not get used, depending on whether your DNS servers return them in the authority section for other requests, per RFC2181 5.4.1). You need to make sure that these stealth nameservers are working; if they are not responding, you may have serious problems! The DNSreport will not query these servers, so you need to be very careful that they are working properly.

ns.domain.com.
This is listed as an ERROR because there are some cases where nasty problems can occur (if the TTLs vary from the NS records at the root servers and the NS records point to your own domain, for example).
3.Missing nameservers 2	

ERROR: One or more of the nameservers listed at the parent servers are not listed as NS records at your nameservers. The problem NS records are:
NS1.domain.com.
NS2.domain.com.

4.Stealth NS record leakage	Your DNS servers leak stealth information in non-NS requests:

Stealth nameservers are leaked [ns.domain.com.]!

This can cause some serious problems (especially if there is a TTL discrepancy). If you must have stealth NS records (NS records listed at the authoritative DNS servers, but not the parent DNS servers), you should make sure that your DNS server does not leak the stealth NS records in response to other queries.
Any idea how to fix this?
I added opendns dns to resolv.conf but that didnt changed anything.

---

### Post by MJN on 2008-01-16
Post your domain name. Assisting with rectifying the 'faults' of a 3rd party DNS analysis without knowing the domain is a waste of everyone's time.
 
Mathew

---

### Post by dwhs.info on 2008-01-16
Here is link to dnstuff domain:
[http://private.dnsstuff.com/tools/dnsreport.ch?domain=lukastgp.biz](http://private.dnsstuff.com/tools/dnsreport.ch?domain=lukastgp.biz)

---

### Post by MJN on 2008-01-16
That's better!
 
> **dwhs.info said:**
> Hello,i checked on my ubuntu server dns with dnsstuff and i founded 5 error.First error is open dns server,is there tutorial for ubuntu which shows how to fix that?
 
Follow the link from the DNSReport - it gives step-by-step instrucitons for BIND (which I assume is what you are using).
 
> ERROR: Some of your nameservers listed at the parent nameservers did not respond.
 
That's right - 72.11.142.230 is not responding despite it being listed in the .biz zone as being an authoritive nameserver for your domain. Only you can fix that - is the machine on? Is there a firewall?

> 2.Missing (stealth) nameservers
 
This is where DNS reporting tools fall down - it's made what is likely an incorrect assumption.
 
You have stated in your zone file that ns.lukastgp.biz is an authoritive nameserver for your domain yet the .biz zone says only ns1 and ns2 are. Given that ns resolves to 72.11.142.229 I suspect this is configuration error - your machine is either ns or ns1 (not both).
 
> 3.Missing nameservers 2
 
Your machine at 72.11.142.229 is saying only ns.lukastgp.biz is authoritive for your domain, yet the .biz servers say ns1 and ns2 are.
 
> 4.Stealth NS record leakage    Your DNS servers leak stealth information in non-NS requests:
 
Ignore this - this is an erroneous claim based on the wrong assumption in point 2 above.
 
> Any idea how to fix this?
 
Take things easy and don't dive in - try and get a good understanding of how DNS works as whilst you may strike lucky with your first configuration you won't learn much in the process! :)
 
> I added opendns dns to resolv.conf but that didnt changed anything.
 
I'm not sure what you mean by this.
 
Mathew

---

