---
title: "Quick check..."
date: 2007-07-14
forum: Server Platforms
---

### Post by ginge6000 on 2007-07-14
I've spent the last week searching forums and googling away and I think I've finally worked out the solution but was hoping someone could give me a quick thumbs up (or tell me that I've got completely the worng end of the stick!!!).

I'm about the install Ubuntu 7.04 server on VMware (for about the 9th time!).  I own a domain (peakescourt.co.uk) through [http://1and1.co.uk]("http://1and1.co.uk").  I also have a dynamic IP and have registered ubuntusrv.homelinux.com with [http://dyndns.com]("http://dyndns.com").  I had set up the server previously so that it was on server1.ubuntusrv.homelinux.com but this annoyed me as it seemed too long!.

What I want is to have it as server1.peakescourt.co.uk and so I changed the CNAME at 1and1 to ubuntusrv.homelinux.com.

Will this now work?  I've contemplated loads of different solutions - I also have an account with [http://zoneedit.com]("http://zoneedit.com") - but I want to use DynDNS as my router automatically updates to this and I'd rather have one less peice of software to reinstall everytime I rebuid the server.

Hope that all makes sense.  It almost makes snese to me now!

Ben

---

### Post by Mr. C. on 2007-07-14
Sure.  Here's (an abbreviated) **dig** query:

```
$ dig server1.peakescourt.co.uk

; <<>> DiG 9.4.1 <<>> server1.peakescourt.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64708
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 5, ADDITIONAL: 5

;; QUESTION SECTION:
;server1.peakescourt.co.uk.     IN      A

;; ANSWER SECTION:
server1.peakescourt.co.uk. 86400 IN     CNAME   ubuntusrv.homelinux.com.
ubuntusrv.homelinux.com. 46     IN      A       213.246.66.63

```

As you can see, a query of server1.peakescourt.co.uk returns the answer that server1 is a CNAME for ubuntusrv.homelinux.com.  The resolver will then query the A record for ubuntusrv.homelinux.com, which resolves to your current IP address.

MrC

---

### Post by ginge6000 on 2007-07-15
Brilliant!  Thank you for doing that!

Do I need to set up a seperate subdomain (and corresponding CNAME record) for each thing like www, ftp, mail etc?

I can have another 4 subdomains with 1and1 (I'm already using one for server1) so I guess this wouldn't be a problem.  DynDNS is set to allow wildcards but I'm guessing that unless the 1and1 nameservers know where to point each subdomain things won't work?

Thanks for you help to a poor old noob!

Ben

---

### Post by Mr. C. on 2007-07-15
You can either use separate A records for the "www", "ftp", etc. subdomains, or use a single wildcard A record that directs all requests for *.mydomain.com to your site.  This always depeneds on what your DNS providers allow.

MrC

---

