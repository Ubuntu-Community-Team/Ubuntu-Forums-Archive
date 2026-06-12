---
title: "How would I give myself an email address myname@mydomain.myextention?"
date: 2010-08-09
forum: The Cafe
---

### Post by Dustin2128 on 2010-08-09
I'm assuming it would involve setting up a mail server. Could it be done in a virtual machine? Would I have to access it from the mail server? What about uptime? I've never done anything like this before so bear with me if I ask stupid questions.

---

### Post by NCLI on 2010-08-09
Way easier to just setup a Google Apps account and [register a domain]("http://www.google.com/a/cpanel/domain").

You'll get the standard gmail interface and features, but even more customizable.

---

### Post by Bachstelze on 2010-08-09
Setting up your own mail server is one way to do it. Another is to use a registrar that also provides email hosting or redirection.  It all depends on what you want to do and why.

---

### Post by jroa on 2010-08-09
This might help.

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by Tristam Green on 2010-08-09
> **NCLI said:**
> Way easier to just setup a Google Apps account and [register a domain]("http://www.google.com/a/cpanel/domain").

You'll get the standard gmail interface and features, but even more customizable.

++

Buy a domain - they're dirt cheap.

---

### Post by Frak on 2010-08-09
> **NCLI said:**
> Way easier to just setup a Google Apps account and [register a domain]("http://www.google.com/a/cpanel/domain").

You'll get the standard gmail interface and features, but even more customizable.
++

I buy all my domains from Google now. Most awesomest registrar evar.

---

### Post by samalex on 2010-08-09
> **NCLI said:**
> Way easier to just setup a Google Apps account and [register a domain]("http://www.google.com/a/cpanel/domain").

You'll get the standard gmail interface and features, but even more customizable.

I agree here...  I have several domains running under Google Apps, and it's definitely easier and cheaper than finding a colo or virtual host.  And if Google Mail goes down, you're not the only one screaming :)  

Sam

---

### Post by Dustin2128 on 2010-08-09
I'm thinking of setting up my own server now. Could I do it in a VM? What if my computer was suspended or hibernating as the message is being received, would it still be in my inbox?

---

### Post by Bachstelze on 2010-08-09
> **Dustin2128 said:**
> I'm thinking of setting up my own server now. Could I do it in a VM?

Maybe. If you want to do it at home, you need 1) a static IP, and 2) an ISP that doesn't block port 25 (in either direction).

> **Dustin2128 said:**
> What if my computer was suspended or hibernating as the message is being received, would it still be in my inbox?

Most mail servers will just queue an outgoing message if the recipient server doesn't respond, and try again later, so that shouldn't be a problem.

---

### Post by samalex on 2010-08-09
I used to host a mail server at home, but you'll run into two major problems... 

First most residential IP addresses are on widely available email block lists to detour traffic from bots.  I ran into this on my TW connection, every email I sent was automatically dropped in the Spam folder of pretty much anyone I emailed.  Solution is relaying through your ISP, Google, or someone else.  This in of itself might be one thing someone wanting to host their own server wants to avoid (having a middle-man), but that's the nature of it.

And secondly, if you have a domain or email address you've used for years, or one that someone else was very active on before you got it, you'll undoubtedly get TONS of spam.  One of my first domain names, which I registered in 2000, gets upwards of 300-500 spam messages a day.  Granted that's only one every few minutes on average, but still that's lots of unwanted traffic coming to your home network.  

Plus running your own server you'll need to maintain spam assassin or some other spam application on your MTA plus keeping it updated.  Not a huge deal to do, but it's a PITA since you don't want ALL that crap coming to your Inbox.

I used to run my own email server, first at home then at a virtual web host, but it's just a pain to keep it going.  That's why I suggested Google because they have a great email solution with lots of bells and whistles.  I use it for an archive, so as I move between systems I just get a dump of all my email messages (if not copied from old client) and with some pre-set rules I have every message I've sent or received since April 2004, which is when I started using gmail.

Oh, and you do not need to have a dedicated IP at home.  I use Afraid DNS, and they have some great solutions if your home is using DHCP.  You can run wget to a predefined URL they provide every 30 minutes to hour to guarantee they have the correct IP.  That or they have other software you can run as well.  

Just some thoughts -- 

Sam

---

### Post by JT9161 on 2010-08-09
> **samalex said:**
> Solution is relaying through your ISP, Google, or someone else. 

This would be done by using Google/The ISPs SMTP server, no ?

---

### Post by Old_Grey_Wolf on 2010-08-09
> **samalex said:**
> 
First most residential IP addresses are on widely available email block lists to detour traffic from bots.  I ran into this on my TW connection, every email I sent was automatically dropped in the Spam folder of pretty much anyone I emailed.  Solution is relaying through your ISP, Google, or someone else.  This in of itself might be one thing someone wanting to host their own server wants to avoid (having a middle-man), but that's the nature of it.


+1
I ran into the same problem with a home server. I had to relay through the ISP; which, defeated the purpose.

---

