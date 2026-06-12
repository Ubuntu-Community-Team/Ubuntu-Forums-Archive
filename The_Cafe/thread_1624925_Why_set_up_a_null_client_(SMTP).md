---
title: "Why set up a null client (SMTP)?"
date: 2010-11-18
forum: The Cafe
---

### Post by Cuddles McKitten on 2010-11-18
On a network with a central mail server, what is the benefit of setting up a machine that can only send mail?  

Is the answer is that each machine still needs an SMTP daemon to actually send mail since POP/IMAP/etc don't do this job?  When I used to get mail through POP3 from my ISP over ten years ago, I don't remember having to set up anything to send messages.

---

### Post by samalex on 2010-11-18
It's good network practice to have one server with port 25 (SMTP) open to the Internet so if a virus or malware infects computers within the network it's not able to send email to any external networks or the Internet.  Email is relayed through the central SMTP server instead.

Also depending on the policies some companies don't want just anyone sending email to the Internet, which is another huge reason.  So they might require all mail to be relayed through a central SMTP server for logging, auditing, etc.

As for an ISP in most cases the residential blocks of IP's are blacklisted where the ISP's primary SMTP server is not.  This is why even though an ISP might have port 25 open it's probably best to relay through the ISP's SMTP server or even someone elses (I often use Google).

So lots of reasons to use a separate outgoing SMTP server whether at home or on a larger network.

Sam

---

### Post by Cuddles McKitten on 2010-11-18
Thank you!  I Googled/Wikipedia'd for a full hour finding only instructions on how to configure a null client but no explanations.

---

### Post by lisati on 2010-11-18
Another reason to have an SMTP server is that you can do extra checks that can help you avoid being branded as a spammer or as a sender of malware.

---

### Post by czr114 on 2010-11-18
> **samalex said:**
> 

As for an ISP in most cases the residential blocks of IP's are blacklisted where the ISP's primary SMTP server is not.  This is why even though an ISP might have port 25 open it's probably best to relay through the ISP's SMTP server or even someone elses (I often use Google).



This is a horrendous practice by ISPs. Customers shouldn't have to funnel their messages through an ISP's system that is doing who knows what with their private data. Given the generally poor track record of ISPs around the world as far as privacy is concerned, and management's affinity for revenue-enhancing tracking clients from marketing companies, ISP servers should be avoided at all costs.

Smaller ISPs with weaker security departments are also likely targets of hackers, who would love to grep through every email sent and received to harvest addresses on behalf of spammers.

Secure SMTP runs over port 465. I've never seen a specific block on that port, except on tightly locked institutional intranets which are blocking almost everything. In 2010, we should be using secure protocols anyway.

It might not be a big deal to some people now, but they have every reason to be concerned should their laptop or notebook start roaming on public WiFi.

If SMTPS is offered, people should take the extra few seconds to enable it and be done with worry and hassle.

---

