---
title: "DNS nameserver Yahoo arggg!"
date: 2007-12-29
forum: Server Platforms
---

### Post by ckennow on 2007-12-29
Ok heres what I got:

Perferct server 7.1 + ISPConfig
Main Site: kennow.net
second site: chadkennow.net

I want to be able to add subdomains to both sites (i.e. whatever.kennow.net / whatever.chadkennow.net etc...etc...etc

I have been reading up a bit and am more confused the more i research

I have ns1.kennow.net and ns2.kennow.net set up at Yahoo! Domains as A NAME servers as well as ns1.chadkennow.net and ns2.chadkennow.net all pointing to my external IP address. 

I was trying to then change the nameservers at Yahoo! Domains to point to ns1.kennow.net and ns2.kennow.net and it tells me:

> Unable to process request 
We're sorry! We are unable to process your request at this time.

Please try again later.

If the problem persists, click the Back button on your browser, then click the Help link at the top right corner of the page. This link will provide you with information specific to your request and how to contact Customer Care if you need further assistance.

So I sent them an e-mail and the sent me this:

> Hello Chad,

Thank you for writing to Yahoo! Domains.

I am glad that you have forwarded your concern to us.

I understand that you are unable to change the NameServers for the 
domain "chadkennow.net".

Chad, I have checked your Yahoo! Domains account and it is in full 
working order. Our servers are running normally at this time, so you 
should not be experiencing any problems. 

Further, I have checked the the details for the settings provided by you
and noticed that the nameservers provided by you are not registered at 
your hosting provider. I am pasting below the search result:

No match for nameserver "NS1.KENNOW.NET".
>>> Last update of whois database: Sat, 29 Dec 2007 03:04:18 UTC <<<

No match for nameserver "NS1.TECHIEJOHN.COM".
>>> Last update of whois database: Sat, 29 Dec 2007 03:16:34 UTC <<<

you can verify the result at:

[http://registrar.verisign-grs.com/cgi-bin/whois?whois_nic=ns1.techiejohn.com&x=18&y=4&type=nameserver&whois_tld=Whois+TLD](http://registrar.verisign-grs.com/cgi-bin/whois?whois_nic=ns1.techiejohn.com&x=18&y=4&type=nameserver&whois_tld=Whois+TLD)

I would suggest you to write back to us to register "NS1.KENNOW.NET" 
with the valid IP for the domain "KENNOW.NET". However, I also noticed 
that the domain 'techiejohn.com' is not registered yet, So, you could 
not register 'ns1.techiejohn.com' without registering the domain name. 

Once the name servers get registered at your registrar end, I am sure 
that you will be able to edit your configuration without any problem.

I sincerely apologize if this is not accommodating your need and your 
cooperation in this regard is appreciated. 

Thanks for you understanding on this matter.

Please do not hesitate to reply if you need further assistance.

Have a great Day!

Regards,

Emily

Yahoo! Customer Care

For assistance with all Yahoo! services please visit:
  
  [http://help.yahoo.com/](http://help.yahoo.com/)



Original Message Follows:
-------------------------

Yahoo Id: Wick422
First Name: Chad
Last Name: Kennow
Email Address: [email]wick422@yahoo.com[/email]
Domain Name: chadkennow.net
Comments: I would like to use my dns on my ubuntu Gutsy server.  I am 
trying to change nameservers to ns1.kennow.net and ns1.techiejohn.com it
tells me it is unable to process your request.  I was referred to e-mail
you about this problem in order to solve it.
Subject: Name servers
Browser: Internet Explorer
Operating System: Windows XP
Email Tool: none
Site Building Tool: none
Internet Connection: Cable
Permit Test: yes

  NS1.KENNOW.NET
Go to Site 
Search the Web
 
  ns1.kennow.net
Go to Site 

Search the Web

now I am comletely lost as to what to do from here...Please Help:(

---

### Post by ckennow on 2007-12-29
Also I was able to add the CNAME Record of ns1.kennow.net for *.chadkennow.net and this seems to allow me to type in whatever.chadkennow.net which gives me a "Shared IP' error page, but I cannnot add ns1.kennow.net or ns1.chadkennow.net to the kennow.net domain. it tells me: > Sorry, we cannot create that CNAME record. The source *.kennow.net cannot point to a subdomain of the same domain. Please choose a unique source or change the destination and try again. What gives? Am I even on the right track?

---

### Post by ckennow on 2007-12-29
hmmmm.... upon setup of my ubuntu server should I not have labeled it's local domain kennow.net.  I just assumed that because i would be hosting kennow.net as my main site i figured that I would just use that.  What say you?

---

### Post by ckennow on 2007-12-29
Can I assume by no response either no one knows or I posted in the wrong forum or you all hate my signature. :P

---

