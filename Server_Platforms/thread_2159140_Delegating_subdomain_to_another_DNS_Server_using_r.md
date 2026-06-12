---
title: "Delegating subdomain to another DNS Server using redundant master-slave"
date: 2013-07-02
forum: Server Platforms
---

### Post by Undo_Rider on 2013-07-02
[TABLE="class: tborder, align: center"]
[TR]
[TD="class: alt2"]Hello,

I want to ask regarding the DNS Server, about delegation subdomain to another dns server
I've actually successed delegating subdomain to another dns server,  but  there is still doubt in myself, whether the dns servers that are out  there (on internet) are also using the method I use? 

When I was searching on internet a lot of tutorials said glue records  are used when delegating a subdomain to another DNS server ,but it  doesn't work.

After  continually searching , glue record is not enough to delegate  subdomains,it need to use redundant master slave too (but this tutorial  is less than just using glue record) I have tried and it works.


My doubts arise, whether when we want to build delegation subdomain to  another dns server , means should be create a new zone for the  subdomain (in the main domain dns server) as a slave, if there are a lot  of subdomains, file named.conf will always have a zone of subdomain as a slave? :confused::confused:

regards

 		 	 		 		 		 		  		 		 		 		 		 	 	[/TD]
 [/TR]
 [TR]
 	[TD="class: alt2"]   		  		 		 		  	[/TD]
  	 	[/TR]
[/TABLE]

---

### Post by SeijiSensei on 2013-07-02
Since people here often use "subdomains" when they mean a hostname, lets make sure we are both using the same definition.  I'll be referring to "sub.example.com" below.  Hosts in the subdomain have names like host.sub.example.com.

A subdomain requires only that a NS record exist in the zone file for the parent, in this case example.com.  So that zone file would have an entry like this:

```

sub       IN     NS    ns-sub.example.com.
          IN     NS    ns2-sub.example.com.

ns-sub    IN     A     10.10.10.10
ns2-sub   IN     A     10.10.10.11

```

Now DNS servers will know to query 10.10.10.10 or 10.10.10.11 to get information about sub.example.com and its host names like host.sub.example.com. The zone file for sub.example.com should also have MX records for servers that will accept mail sent to [email]user@sub.example.com[/email].

That's what I think of when the term "subdomain" is used.

I don't think it matters what servers host the records for sub.example.com; it could even be the same servers that host example.com.  What matters more is that there are two of them, preferably separated both geographically and topologically from each other.

---

### Post by Undo_Rider on 2013-07-17
> **SeijiSensei said:**
> Since people here often use "subdomains" when they mean a hostname, lets make sure we are both using the same definition.  I'll be referring to "sub.example.com" below.  Hosts in the subdomain have names like host.sub.example.com.

A subdomain requires only that a NS record exist in the zone file for the parent, in this case example.com.  So that zone file would have an entry like this:

```

sub       IN     NS    ns-sub.example.com.
          IN     NS    ns2-sub.example.com.

ns-sub    IN     A     10.10.10.10
ns2-sub   IN     A     10.10.10.11

```

Now DNS servers will know to query 10.10.10.10 or 10.10.10.11 to get information about sub.example.com and its host names like host.sub.example.com. The zone file for sub.example.com should also have MX records for servers that will accept mail sent to [EMAIL="user@sub.example.com"]user@sub.example.com[/EMAIL].

That's what I think of when the term "subdomain" is used.

I don't think it matters what servers host the records for sub.example.com; it could even be the same servers that host example.com.  What matters more is that there are two of them, preferably separated both geographically and topologically from each other.

thanks for your reply
yes, maybe I mean "hostname"  

thats configuration I have been using before , but didn't works

---

### Post by SeijiSensei on 2013-07-18
A hostname like [www.example.com](www.example.com) is referenced with an A or CNAME record in the domain's zone file.  Either

```

www     IN  A  10.10.10.10

```

or

```

www   IN  CNAME something.

```

or

```

www   IN  CNAME something.somewhere-else.net.

```

---

