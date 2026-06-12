---
title: "Help backing up a friends DNS server"
date: 2006-08-19
forum: Server Platforms
---

### Post by chrisfay on 2006-08-19
I am hoping someone can help clarify my confusion regarding cris-crossing DNS servers in order to back up one another. A friend of mine is running Bind9 as well as myself and we would like to swap one of our name servers for eachothers with the intention of failsafeing our mail and web servers. 

The issue of confusion is what name server to list under the zone I make for his domain on my DNS. Do I list both name servers he has listed at his registrar or just the one using my subdomain?  

If he has ns1.hisdomain.com and ns2.mydomain.com listed, do I use both of those as name servers on the zone I make for him or just ns2.mydomain.com? I have a fealing I just list ns2.mydomain.com as its the one that will actually be pointing to my DNS but just want to double check.

The rest of the A and MX records I just point to his IP but the NS record has me confused.

---

### Post by MJN on 2006-08-19
Just as an aside to your question, I must ask if your web/mail server functions are sitting on the same box as your DNS? If so, then there is little point in providing secondary DNS functions for each other as if your DNS is down (or not accessible) then it's likely (if not a certainty) that so is your web/mail.

Of course, if these services are seperately hosted then you can ignore this, but I thought I'd point it out just in case as this is seemingly a very common mistake to make.

Mathew

---

### Post by chrisfay on 2006-08-19
> Just as an aside to your question, I must ask if your web/mail server functions are sitting on the same box as your DNS? If so, then there is little point in providing secondary DNS functions for each other as if your DNS is down (or not accessible) then it's likely (if not a certainty) that so is your web/mail.

True, but there's more to it.... 

This is from RFC2182:

> 3.3. A Myth Exploded

   An argument is occasionally made that there is no need for the domain
   name servers for a domain to be accessible if the hosts in the domain
   are unreachable.  This argument is fallacious.

     + Clients react differently to inability to resolve than inability
       to connect, and reactions to the former are not always as
       desirable.
     
     + If the zone is resolvable yet the particular name is not, then a
       client can discard the transaction rather than retrying and
       creating undesirable load on the network.
     
     + While positive DNS results are usually cached, the lack of a
       result is not cached.  Thus, unnecessary inability to resolve
       creates an undesirable load on the net.
     
     + All names in the zone may not resolve to addresses within the
       detached network.  This becomes more likely over time.  Thus a
       basic assumption of the myth often becomes untrue.

   It is important that there be nameservers able to be queried,
   available always, for all forward zones.


In terms of reaching my site or mail server yes, it's relitively pointles but there is still merit in terms of network integrity and good practice.

---

### Post by MJN on 2006-08-20
That's very interesting - thanks. Looks like it is I that has been commonly mistaken!

Mathew

---

