---
title: "Problem with Domainkeys (dk-filter) coming up 'bad signature' POSTFIX"
date: 2011-03-16
forum: Server Platforms
---

### Post by yopster on 2011-03-16
Hi guys
 
My Postfix mail server is up and running with no problems apart from Domainkeys authentication.  This is a professional server and I want my mail verified in every way possible.
 
I have tried several guides to try to get dk-filter working for Yahoo! authentication.  DKIM is working like a champ.  As is Sender-ID and SPF records.  
 
I'm using the same private and public key for the dkim-filter and dk-filter.  Is that right?  
 
Also I'm not sure my DNS entries are correct.
 
I have this as my DNS TXT records
 
**default._domainkey.myserver IN TXT "g=*; k=rsa; t=y; p=MIGf........."**
 
**_domainkey.myserver IN TXT "o=-; t=y; p=MIGf........."**
 
I am pulling my hair out I have followed several guides and I think I've made the mistake of not letting the DNS records propagate before changing settings again.
 
Thanks in advance for any replies!  :)

---

