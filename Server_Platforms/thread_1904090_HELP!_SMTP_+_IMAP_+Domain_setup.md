---
title: "HELP! SMTP + IMAP +Domain setup"
date: 2012-01-04
forum: Server Platforms
---

### Post by balagosa on 2012-01-04
Situation:

I have an SMTP + IMAP server. This server is behind a firewall with the correct setting for it to work. This server is also connected to the internet via a STATIC IP which comes from my ISP (called hereafter as ISP). Also, I have a web domain registered under a company (called hereafter as domain provider). The DNS settings of my web domain are setup with guides from the internet (A, MX, CNAME). 

Problem:
The server was working fine in the first weeks of operation, the problem occurred when domain checkers blacklisted me.

Sample domains are [mxtoolbox]("http://www.mxtoolbox.com/blacklists.aspx"). I have found out that my ISP did not give me an RDNS (Reverse DNS) to my domain. Another [domain checker tool]("http://lookupserver.com/") I found.

As a result, ALL my outgoing emails are blocked by domains such as google, yahoo. But incoming is OK, no problem there.

Ideas considered:
1) My outgoing email will pass through domain provider but I do not know what to change with my server, DNS settings
2) Ask my ISP to enable my RDNS

Any ideas are appreciated.

---

### Post by apollothethird on 2012-01-04
> **balagosa said:**
> Situation:

I have an SMTP + IMAP server. This server is behind a firewall with the correct setting for it to work. This server is also connected to the internet via a STATIC IP which comes from my ISP (called hereafter as ISP). Also, I have a web domain registered under a company (called hereafter as domain provider). The DNS settings of my web domain are setup with guides from the internet (A, MX, CNAME). 

Problem:
The server was working fine in the first weeks of operation, the problem occurred when domain checkers blacklisted me.

Sample domains are [mxtoolbox]("http://www.mxtoolbox.com/blacklists.aspx"). I have found out that my ISP did not give me an RDNS (Reverse DNS) to my domain. Another [domain checker tool]("http://lookupserver.com/") I found.

As a result, ALL my outgoing emails are blocked by domains such as google, yahoo. But incoming is OK, no problem there.

Ideas considered:
1) My outgoing email will pass through domain provider but I do not know what to change with my server, DNS settings
2) Ask my ISP to enable my RDNS

Any ideas are appreciated.

                               Start out by running your own DNS server.  Put your mail server as a canonical name to whatever the IP reverses to.  That should pass the RDNS qualifications.

-- L. James

--  
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by balagosa on 2012-01-04
> **apollothethird said:**
> Start out by running your own DNS server.  Put your mail server as a canonical name to whatever the IP reverses to.  That should pass the RDNS qualifications.

-- L. James

--  
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Thanks for the reply. I am a bit slow with this issue, probably due to the saturation of ideas.
Do you mind explaining a bit more? Documents, links, guides will be useful.

Edit: (Trying to understand)
"**My own DNS server**" 
I already have one but it is internal for the site only and is not exposed to the WAN.

"**Mail Server as CNAME**" 
The domain provider stated above is capable of an RDNS to their own domain, also to the IP Adress they have provided. So no problem there. I will try to implement this one and add a CNAME record pointing to my mail server.

Edit2: (Tried to implement; I have a feeling my problem could be solved by tweaking my DNS settings on my domain provider)
"**Mail Server as CNAME**"
for example I name the following:
provider.com as the A record which is capable of RDNS. This is also the default settings given by my domain provider
mydomain.com as the mail server that I have on my site. An MX record also points to this server
11.11.11.11 is the IP address given by my domain provider. It is a static address
22.22.22.22 is the IP address given by my ISP. It is also a static address

provider.com   IN   A   11.11.11.11
mail.mydomain.com   IN   A   22.22.22.22
web.mydomain.com    IN   A   22.22.22.22

provider.com   IN   MX   10   mail.mydomain.com

[www.provider.com](www.provider.com)   IN   CNAME   web.mydomain.com
--- SHOWN ABOVE IS THE CURRENT SETUP ---

**Put your mail server as a canonical name to whatever the IP reverses to.**
This is the part where I do not understand.
mail.mydomain.com   IN   CNAME   provider.com **(Is this what you are referring to?)**
I have read an [online document]("http://rscott.org/dns/cname.html") that disallows this. 
> Problem? If you have a CNAME entry, make sure that it is the ONLY resource record for that domain. For example, if you have "www.example.com CNAME sparky.example.com", you must not have any A records, MX records, etc. for "www.example.com". [RFC1034 3.6.2] [RFC1912 2.4]

---

### Post by balagosa on 2012-01-05
bump :guitar:

---

### Post by balagosa on 2012-01-05
no hope?

---

### Post by SeijiSensei on 2012-01-05
Adding an [SPF]("http://www.openspf.net/") record for your domain might help.  However the best approach is a static IP and correct reverse resolution for the address. 

You could still have problems if your IP falls into a residential address block.  If you can relay mail through your provider's SMTP host using your domain (i.e., the provider will forward mail from [email]user@example.com[/email] even though the provider's domain is not example.com), that may solve the problem as well.  You can just use the ISP's server as your "[smart host]("http://en.wikipedia.org/wiki/Smart_host")."

---

### Post by balagosa on 2012-01-06
> **SeijiSensei said:**
> Adding an [SPF]("http://www.openspf.net/") record for your domain might help.  However the best approach is a static IP and correct reverse resolution for the address. 

You could still have problems if your IP falls into a residential address block.  If you can relay mail through your provider's SMTP host using your domain (i.e., the provider will forward mail from [email]user@example.com[/email] even though the provider's domain is not example.com), that may solve the problem as well.  You can just use the ISP's server as your "[smart host]("http://en.wikipedia.org/wiki/Smart_host")."

i dont think SPF is the solution here. if you think so, explain to me how.

I am negotiating to use my domain provider as relay. With the Smart Host setup you suggested.

---

### Post by apollothethird on 2012-01-07
Hi, Balagosa.  First I'll mention that I follow the topics where I type until they are closed as solved or the individual indicates he's not looking for my assistance.  It might take me a few days at times to get back to the topics where I'm typing.  But I'll followup based on my available time.

> **balagosa said:**
> Thanks for the reply. I am a bit slow with this issue, probably due to the saturation of ideas.
Do you mind explaining a bit more? Documents, links, guides will be useful.

Edit: (Trying to understand)
"My own DNS server" 
I already have one but it is internal for the site only and is not exposed to the WAN.

To resolve the issues you're having, you'll have to have control over the DNS server.  This can either be done by your ISP who's DNS server you're using, performing the needed tasks, which you say they are not cooperative with, or setting up your own.  Based on your previous message you're left with setting up your own.  If it's local only, then you really don't have a usable DNS server.  It has to be on the Internet and usable by the world.

> "Mail Server as CNAME" 
The domain provider stated above is capable of an RDNS to their own domain, also to the IP Adress they have provided. So no problem there. I will try to implement this one and add a CNAME record pointing to my mail server.

Edit2: (Tried to implement; I have a feeling my problem could be solved by tweaking my DNS settings on my domain provider)
"Mail Server as CNAME"
for example I name the following:
provider.com as the A record which is capable of RDNS. This is also the default settings given by my domain provider
mydomain.com as the mail server that I have on my site. An MX record also points to this server
11.11.11.11 is the IP address given by my domain provider. It is a static address
22.22.22.22 is the IP address given by my ISP. It is also a static address

provider.com IN A 11.11.11.11
mail.mydomain.com IN A 22.22.22.22
web.mydomain.com IN A 22.22.22.22

provider.com IN MX 10 mail.mydomain.com

[www.provider.com]("http://www.provider.com") IN CNAME web.mydomain.com
--- SHOWN ABOVE IS THE CURRENT SETUP ---

Put your mail server as a canonical name to whatever the IP reverses to.
This is the part where I do not understand.
mail.mydomain.com IN CNAME provider.com (Is this what you are referring to?)
I have read an online document that disallows this.My recommendation will only work if you setup a DNS server that you have control over.  If you're having problems setting up the DNS server (for the Internet, not just your local environment) I can help you with that and go to the next step.

As far as canonical name you can find the resolution of your IP by running host on the IP address:

```

host 50.56.30.217

```Take the resulting host name (in this case, apollo2.apollo3.com) and set your mail server to that canonical name.

```

mysmtp.mydomain.com.    IN CNAME apollo2.apollo3.com.

```> **balagosa said:**
> i dont think SPF is the solution here. if you think so, explain to me how.


Actually I think that's the precise solution.  The other details of my messages are steps to get there.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by balagosa on 2012-01-10
> **apollothethird said:**
> Hi, Balagosa.  First I'll mention that I follow the topics where I type until they are closed as solved or the individual indicates he's not looking for my assistance.  It might take me a few days at times to get back to the topics where I'm typing.  But I'll followup based on my available time.



To resolve the issues you're having, you'll have to have control over the DNS server.  This can either be done by your ISP who's DNS server you're using, performing the needed tasks, which you say they are not cooperative with, or setting up your own.  Based on your previous message you're left with setting up your own.  If it's local only, then you really don't have a usable DNS server.  It has to be on the Internet and usable by the world.

My recommendation will only work if you setup a DNS server that you have control over.  If you're having problems setting up the DNS server (for the Internet, not just your local environment) I can help you with that and go to the next step.

As far as canonical name you can find the resolution of your IP by running host on the IP address:

```

host 50.56.30.217

```Take the resulting host name (in this case, apollo2.apollo3.com) and set your mail server to that canonical name.

```

mysmtp.mydomain.com.    IN CNAME apollo2.apollo3.com.

```

Actually I think that's the precise solution.  The other details of my messages are steps to get there.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

I read you reply. This will take time to absorb the info. Also, I did contact my domain provider and they refuse to relay my email for outside. That is one idea to consider down.

> 
Actually I think that's the precise solution. The other details of my messages are steps to get there.

An SPF record as the precise solution? I have read guides on the net for SPF1 setup and their requirement is **Reverse DNS** which I do not have.

Some more edits may take place in my post while I do a trial-error.

---

### Post by apollothethird on 2012-01-10
> **balagosa said:**
> I read you reply. This will take time to absorb the info. Also, I did contact my domain provider and they refuse to relay my email for outside. That is one idea to consider down.

At a glance it looks like a lot.  However, if you will perform the task in steps you'll find it very simple.

The first step is to make DNS server which you mentioned is just for your local network visible to the world.

Your provider won't have anything to do with that, nor do they need to have anything to do with it.

> An SPF record as the precise solution? I have read guides on the net for SPF1 setup and their requirement is **Reverse DNS** which I do not have.

Some more edits may take place in my post while I do a trial-error.I won't see the edits that you put into your post.  I'll only see the new messages you post.  If you have updates after making changes, you'd best put it in a new post.  I'll be notified that you have something new and I'll revisit the thread to assist you.

Every thing I mentioned to you are components that are within your control (or the control of the person who registered your domain).  That is the person that specifies the IP address of the domain server.  So all you have to do is go into your DNS records and specify the Domain Server that you create and maintain as the server of your domain.

If you have a problem with this, just tell me where you're getting stuck.

As far as reverse IP, that's resolved by using the CNAME pointer in your DNS records.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by SeijiSensei on 2012-01-10
> **apollothethird said:**
> As far as reverse IP, that's resolved by using the CNAME pointer in your DNS records.

No, it isn't.  It depends on whether there's a correct record for his IP address in the in-addr.arpa domain for his network block.  In most instances the ISP is authoritative for the blocks they administer and must create an appropriate reverse entry.

balagosa, if they aren't willing to forward your mail, can they at least give you a correct reverse DNS entry?  Since you have a static address, any competent provider should be able to set up your reverse DNS entry.

---

### Post by apollothethird on 2012-01-10
> **SeijiSensei said:**
> No, it isn't.  It depends on whether there's a correct record for his IP address in the in-addr.arpa domain for his network block.  In most instances the ISP is authoritative for the blocks they administer and must create an appropriate reverse entry.

balagosa, if they aren't willing to forward your mail, can they at least give you a correct reverse DNS entry?  Since you have a static address, any competent provider should be able to set up your reverse DNS entry.

It's very rare occasion that there won't be a record for an assigned IP.  It's so rare that I'm certain the user can depend on it just by typing "host IP" and getting it.

The steps I provided are steps that the user can don on his own and it's unlikely those steps will fail.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by SeijiSensei on 2012-01-10
> **apollothethird said:**
> It's very rare occasion that there won't be a record for an assigned IP.  It's so rare that I'm certain the user can depend on it just by typing "host IP" and getting it.

ISPs often assign arbitrary names to IP addresses for reverse DNS, but that doesn't help when it comes to sending mail.  Many SMTP servers expect the server's forward and reverse lookups to match.  For instance, my ISP (Verizon FiOS) reports the name of my router as "static-12-345-67-89.bstnma.fios.verizon.net" (using my real IP address, of course).  If I were sending mail through this device as "mail.example.com", some remote SMTP servers will object because the forward and reverse names don't match.  That would be true even if "mail.example.com" correctly resolves to the same IP address.

Unless the ISP "delegates" reverse name service using [RFC 2317]("http://www.ietf.org/rfc/rfc2317.txt"), the end-user has no control over the reverse ("PTR") records.

---

### Post by apollothethird on 2012-01-10
> **SeijiSensei said:**
> ISPs often assign arbitrary names to IP addresses for reverse DNS, but that doesn't help when it comes to sending mail. Many SMTP servers expect the server's forward and reverse lookups to match. For instance, my ISP (Verizon FiOS) reports the name of my router as "static-12-345-67-89.bstnma.fios.verizon.net" (using my real IP address, of course). If I were sending mail through this device as "mail.example.com", some remote SMTP servers will object because the forward and reverse names don't match. That would be true even if "mail.example.com" correctly resolves to the same IP address.

Unless the ISP "delegates" reverse name service using RFC 2317, the end-user has no control over the reverse ("PTR") records.

Hi, Seijisensei.  Most or all of what you say might be true.  However, that doesn't negate the steps I provided the user.  The steps I gave him has to be done (or should be done anyway).  They might work.  But if there is a chance his mail fails, it would leave him with still simple steps to follow.  Most likely the last one would be for him to put in a ticket indicating the resolve for his purchased (rented) IP.  Most likely his ISP would provide this for him if it were presented clear enough.

Looking at the user's previous post, his request to his ISP might have had an element of vague which caused them to give him a blanket response that he's not paying for IT services and setup... just the working components of his package.  It might have appeared that he was asking them to setup an mail server for him and resolve all the technical components.

The mail from my server worked when I used IP addresses and CNAMES, as what I suggested for this user.  There was a time when my mail server resolved to the name of my upstream (216-153-132-69-choiceone.com).  I used a canonical name for years (outgoing.apollo3.com IN CNAME [name given by upstream]).  I eventually sent in a ticket requesting the IP be resolved to the hostname I provided in the ticket.

If he setup his DNS server and has this one element left and it fails, it would be simple for him to proceed with the same.

Since I have a number of domains I work with, I'm going to setup a test mail server and see if it'll work with the CNAME.

I would like to remind you that I gave the user steps to follow.  Again, each of the steps I gave him are important.  He made it clear that he was having problems understanding the full scope.  So he can consider performing the steps I gave him, which is first to setup his DNS server... making it visible to the internet.  Use the CNAME for his smtp server.  Complete that step and let us know if he continues to have problems.

Again, if the CNAME entry fails, I'm certain his ISP would prefer to make a simple entry in his DNS server rather than loose the client (unless of course he really doesn't have the dedicated IP, but it's shared with other customers).

He can check if he really has the dedicate IP by creating a web page and attempting to access that page by the IP itself.

I understand that many of you have your own systematic approach for resolving issues and setting up services.  But I believe the method I describe is also viable.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by balagosa on 2012-01-14
Just got back online. Starting to read the replies. Thanks guys for the help

When making edits or additional info, I will create a new reply. Give me time to absorb the information.

---

### Post by balagosa on 2012-01-14
> **SeijiSensei said:**
> No, it isn't.  It depends on whether there's a correct record for his IP address in the in-addr.arpa domain for his network block.  In most instances the ISP is authoritative for the blocks they administer and must create an appropriate reverse entry.

balagosa, if they aren't willing to forward your mail, can they at least give you a correct reverse DNS entry?  Since you have a static address, any competent provider should be able to set up your reverse DNS entry.

still contacting my ISP for the reverse DNS. damn they are slow. But on my domain provider, everything is ok with the reverse DNS for my website. They just wont relay mail for me.

---

### Post by SeijiSensei on 2012-01-14
> **balagosa said:**
> still contacting my ISP for the reverse DNS. damn they are slow. But on my domain provider, everything is ok with the reverse DNS for my website. They just wont relay mail for me.

Is your website running on a virtual machine that you control, or do you have only a web service account?  If you have a real VM, you could forward the mail through it and take advantage of the existing reverse-DNS configuration.  

All the mail I handle goes through a [Linode]("http://www.linode.com/") VM.  All their VMs have static IPs and the ability to designate a reverse DNS entry through the control panel.

---

### Post by balagosa on 2012-01-14
> **apollothethird said:**
> Hi, Seijisensei.  Most or all of what you say might be true.  However, that doesn't negate the steps I provided the user.  The steps I gave him has to be done (or should be done anyway).  They might work.  But if there is a chance his mail fails, it would leave him with still simple steps to follow.  Most likely the last one would be for him to put in a ticket indicating the resolve for his purchased (rented) IP.  Most likely his ISP would provide this for him if it were presented clear enough.

Looking at the user's previous post, his request to his ISP might have had an element of vague which caused them to give him a blanket response that he's not paying for IT services and setup... just the working components of his package.  It might have appeared that he was asking them to setup an mail server for him and resolve all the technical components.

The mail from my server worked when I used IP addresses and CNAMES, as what I suggested for this user.  There was a time when my mail server resolved to the name of my upstream (216-153-132-69-choiceone.com).  I used a canonical name for years (outgoing.apollo3.com IN CNAME [name given by upstream]).  I eventually sent in a ticket requesting the IP be resolved to the hostname I provided in the ticket.

If he setup his DNS server and has this one element left and it fails, it would be simple for him to proceed with the same.

Since I have a number of domains I work with, I'm going to setup a test mail server and see if it'll work with the CNAME.

I would like to remind you that I gave the user steps to follow.  Again, each of the steps I gave him are important.  He made it clear that he was having problems understanding the full scope.  So he can consider performing the steps I gave him, which is first to setup his DNS server... making it visible to the internet.  Use the CNAME for his smtp server.  Complete that step and let us know if he continues to have problems.

Again, if the CNAME entry fails, I'm certain his ISP would prefer to make a simple entry in his DNS server rather than loose the client (unless of course he really doesn't have the dedicated IP, but it's shared with other customers).

He can check if he really has the dedicate IP by creating a web page and attempting to access that page by the IP itself.

I understand that many of you have your own systematic approach for resolving issues and setting up services.  But I believe the method I describe is also viable.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Actions to do:
1) Look for a guide to setup a DNS server exposed to WAN. Any hints or tips?
2) contact ISP for reverse DNS

You have an above comment of dedicated IP. Yes, I do have a dedicated IP. From what I understand of your post. I have the right tools with the wrong implementation.

---

### Post by apollothethird on 2012-01-14
> **balagosa said:**
> still contacting my ISP for the reverse DNS. damn they are slow. But on my domain provider, everything is ok with the reverse DNS for my website. They just wont relay mail for me.

Is your DNS server visible from the Internet (not just your local network)?

What do you get when you run from a terminal prompt:

```

host [yourmailsmptserver] 8.8.8.8

```Substitute the "[yoursmtpserver]" for the smpt server you have in the DNS configurations that you maintain (without the brackets of course).

The steps that> **balagosa said:**
> still contacting my ISP for the reverse DNS. damn they are slow. But on my domain provider, everything is ok with the reverse DNS for my website. They just wont relay mail for me.

Is your DNS server visible from the Internet (not just your local network)?

What do you get when you run from a terminal prompt:

```

host [yourmailsmptserver] 8.8.8.8

```Substitute the "[yoursmtpserver]" for the smpt server you have in the DNS configurations that you maintain.

The steps that I provided you so far are all under your control.  Your ISP doesn't come into the picture at all.

If you setup everything on your end, it'll probably work without problems.  If you do have a problem,  any support ticket submitted to your IP would be very direct and easily resolvable.

> **balagosa said:**
> Actions to do:
1) Look for a guide to setup a DNS server exposed to WAN. Any hints or tips?
2) contact ISP for reverse DNS

You have an above comment of dedicated IP. Yes, I do have a dedicated IP. From what I understand of your post. I have the right tools with the wrong implementation.

I'll start out with #1.  Configure your domain to use the IP of your DNS server for it's Name Server.

You can check it by running the cli:

```

whois [domainname]

```Substitude Domainname for the name of your domain without the brackets.  You can also use "apollo3.com" or "microsoft.com" to see other examples.

You should find a control panel on the site where you registered your domain to set up the name servers.  You'll have to use two... a primary and secondary server.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")


 I provided you so far are all under your control.  Your ISP doesn't come into the picture at all.

If you setup everything on your end, it'll probably work without problems.  If you do have a problem,  any support ticket submitted to your IP would be very direct and easily resolvable.

> **balagosa said:**
> Actions to do:
1) Look for a guide to setup a DNS server exposed to WAN. Any hints or tips?
2) contact ISP for reverse DNS

You have an above comment of dedicated IP. Yes, I do have a dedicated IP. From what I understand of your post. I have the right tools with the wrong implementation.

I'll start out with #1.  Configure your domain to use the IP of your DNS server for it's Name Server.

You can check it by running the cli:

```

whois [domainname]

```Substitude Domainname for the name of your domain without the brackets.  You can also use "apollo3.com" or "microsoft.com" to see other examples.

You should find a control panel on the site where you registered your domain to set up the name servers.  You'll have to use two... a primary and secondary server.  You can actually setup an account on a site such as [http://opendns.org](http://opendns.org) for the secondary name server.  Opendns is a free resource.  You can find others via a Google search.

But again, you'd either have your DNS maintainer setup this configuration (of which you're saying they won't do) or you'd setup your own.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

