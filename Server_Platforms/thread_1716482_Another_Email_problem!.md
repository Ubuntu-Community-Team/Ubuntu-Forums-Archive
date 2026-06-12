---
title: "Another Email problem!"
date: 2011-03-28
forum: Server Platforms
---

### Post by Robert the Kat on 2011-03-28
[SIZE=2]  The more I read about setting up and getting an Email server working the more I have to cheer for those that really get it to work! The latest "problem" I have found is the "Unaccepted mail due to no reverse DNS(no PTR record)."   From what I have read this is something your ISP must do and will not. Along with port 25 being blocked.
So how do you get past this problem with Email?
 
RK
 
[/SIZE]

---

### Post by stefangr1 on 2011-03-28
I assume that you own a domain name? You need make sure the DNS settings are correct.

If your provider blocks port 25, I don't think it's possible to get a mailserver working.

---

### Post by SeijiSensei on 2011-03-28
No, it doesn't have anything to do with *his* domain.  The error Robert reports occurs when there is no *reverse* DNS record (a so-called "pointer" or "PTR" record).

When you set up a name server for a domain, it provides "forward" resolution from human-readable host names to IP addresses.  There's also an equivalent "reverse" service that returns the host name associated with a given IP address.

The only people who can set up reverse DNS resolution are ISPs (unless the ISP supports [RFC2317]("http://www.apps.ietf.org/rfc/rfc2317.html") delegation). Many mail servers treat messages sent by servers without proper reverse resolution as likely spam.  Some mail servers, like mine, will increase the "spamminess" score for such messages, but not necessarily reject them out of hand.  Others, as Robert discovered, simply refuse to accept any mail from servers without proper reverse resolution.

Robert, the easiest answer to your question is either to pay for a "business-class" Internet connection with proper reverse resolution and no port blocking, or rent a virtual machine.  I do both.  Trying to run a mail server for any purpose other than a hobby over a residential Internet connection will encounter all sorts of problems like the ones you've reported.

---

### Post by Robert the Kat on 2011-03-28
> **SeijiSensei said:**
> .
 
Robert, the easiest answer to your question is either to pay for a "business-class" Internet connection with proper reverse resolution and no port blocking, or rent a virtual machine. I do both. Trying to run a mail server for any purpose other than a hobby over a residential Internet connection will encounter all sorts of problems like the ones you've reported.
 
100% Correct!  The many hours I have put into this server has shown me just what you have stated.  Your selection would be too costly for a mostly hobby issue.  I did gather a great amount of information while attempting to get this Email working.  At least this "old" machine will still make a good security camera server.  Something I do many of.
 
Thanks for your great info.
 
 RK  
:)

---

### Post by kampman on 2011-03-29
You can usually relay your outgoing mail through your ISP's SMTP server. Your ISP will have the correct reverse DNS set up already so your mail won't get rejected. If you're using Postfix it's relayhost = ISP Server Address in main.cf.

---

