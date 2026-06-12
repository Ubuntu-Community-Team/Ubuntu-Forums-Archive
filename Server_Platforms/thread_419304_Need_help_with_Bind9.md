---
title: "Need help with Bind9"
date: 2007-04-22
forum: Server Platforms
---

### Post by Dzenhax on 2007-04-22
Hi guys,

     Iv'e read books, online info and serched the forums before I decided to make my own post.  Here's my situation.  I am in a dorm type situation and we have no internet connectivity on my floor to any room but mine.  So we can share files and leave messages among students I've decided to make a wireless email server with the zabra collaboration suite, but can't get past setting up bind.

     The problem is with my zone file.  Here it is:

$TTL 1d

@   1d    IN    SOA    cncv01.conclave.org.   dzenhax.conclave.org (
                                2007042508 ; serial
                                43200 ; Refresh      
                                900 ; Retry        
                                604800 ;Expire     
                                10800 ; Nagative Cache TTL      
                                )
@	IN              NS      cncv01.conclave.org.
                        A       127.0.0.1

cncv01	IN	A	192.168.2.30
Medea	IN	A	192.168.2.25
gateway IN	A	192.168.2.2

And it works fine this way.  But when I try to make an MX record by adding:

@     IN     MX     cncv01.conclave.org.

and restart bind I now cannot resolve hosts.  I get the message:

Host Medea not found: 3(NXDOMAIN)

I place this line right under the A 127.0.0.1

I have tried it without the @ at the front of the line and changing the name to mail.conclave.org and giving it an alias record.  All with the same results.  But when I delete the line, it all starts working again and resolves hosts fine.

I just have one computer running as the server so it will be the DNS server and Mail server and will probably later be the DHCP server as well.

Any help would be appreciated and I thank you in advance.  I won't be able to log onto the forum again until the weekend, but please post.  Next Saturday I will try to get it working again.

---

### Post by Dzenhax on 2007-04-27
I fixed the problem.  I'll post it here in case anyone else has the same issue.  My solution was to give an alias name to the server and list it in the Start of Authority section.  It answers DNS under one name and mail under another.  Then I added a CNAME record to point back at the original name in the hosts portion.  The new file looks like this:

$TTL 1d

@   1d    IN    SOA    cncv01.conclave.org.   dzenhax.conclave.org (
                                2005103008 ; serial
                                43200 ; Refresh      
                                900 ; Retry        
                                604800 ;Expire     
                                10800 ; Nagative Cache TTL      
                                )
@	IN              NS      cncv01.conclave.org.
                        A       127.0.0.1
@	IN	MX	10	mail.conclave.org.

cncv01	IN	A	192.168.2.30
Medea	IN	A	192.168.2.25
mail  	IN  	CNAME  	cncv01

---

