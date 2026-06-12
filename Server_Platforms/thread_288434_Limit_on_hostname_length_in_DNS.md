---
title: "Limit on hostname length in DNS?"
date: 2006-10-29
forum: Server Platforms
---

### Post by bmillsap on 2006-10-29
Not strictly an Ubuntu question, but - I'm using my ubuntu machine as a DNS and DHCP server for my home network.  For one item on my network, my TiVo, the DHCP update of the DNS database fails.  Since the update works for my laptops, I was speculating that it might have something to do with the fact that the TiVo uses a hostname consisting of TIVO_ followed by the TiVo's 15-digit service number for a total of 20 characters, which seems kind of long.  Is there a limit on the length of a single level of a domain name (I'm using dhcp3 and bind9), or should I look for another problem?  My quick Google searches seem to say there's not, but I'm not sure why else DNS updates would work for everything but this.

---

### Post by rbalfour on 2006-10-29
No. Underbar is allowed and the max length is 255 octets.
You may want to check your log files and see what is happening when the Tivo box request an IP address and then see what the DNS server is recording.

---

### Post by bmillsap on 2006-10-29
The error in the log (other than the "timed out" error that DHCP throws because it can't update the DNS database) is:

named[23888]: zone [my domain].com/IN: TIVO_[my tivo's SN].[my domain].com/A: bad owner name (check-names)

I haven't run across this one in setting up and debugging my DHCP/DNS setup.

---

### Post by bmillsap on 2006-10-29
Note: I found some postings on other websites that indicate it could be that BIND 9.3 doesn't like underscores in hostnames by default.  I'll see if I can set it up to allow them.  Thanks for your reply.

---

### Post by MJN on 2006-10-30
That's right - the RFCs don't allow them in hostnames and BIND enforces this by default.
 
You can tell BIND to warn rather than fail if this (and similar) rule is broken using the **check-names warn** directive (as opposed to check-names fail).
 
With regards to component length (i.e. between the dots), the maximum is 63 characters (at least as far as the RFCs are concerned).
 
Mathew

---

### Post by bmillsap on 2006-10-30
Yes, that was it, changing the check-names setting made it work.  Thanks for your help.

---

### Post by milli on 2006-10-30
It is a common misconception that the underscore character is okay to use in Internet hostnames...  it is actually illegal (not allowed) if you read the Internet specs on the subject ([RFC 1123]("http://www.ietf.org/rfc/rfc1123.txt") and [RFC 952]("http://www.ietf.org/rfc/rfc952.txt")).  It is something that should, however, be restricted on the host when you set it's name, but often is allowed (PCs allow it, for example).

Your Tivo suprises me.  Being Linux-based, I wouldn't expect it to set it's name to something with an underscore in it... ](*,)

---

### Post by bmillsap on 2006-10-30
I doubt they expected anyone to actually care.  This was more to make sure my DNS setup was working in general.  Anyway, given the hostname, it'll be easier to find the IP if I need to access it rather than type in TIVO_123456789012345.mydomain.com, even assuming I could remember what my version of 123456789012345 actually is.

---

