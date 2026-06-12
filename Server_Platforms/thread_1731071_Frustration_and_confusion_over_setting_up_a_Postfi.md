---
title: "Frustration and confusion over setting up a Postfix mail server on my Ubuntu server."
date: 2011-04-16
forum: Server Platforms
---

### Post by dag10 on 2011-04-16
To start off, It's worth mentioning that I'm still very confused about how the whole mail server thing works, and 

what software handles what job. From my understanding POP3 and IMAP are protocols to pull email from a mail server, 

and SMTP is used to push email to a server. There are many programs that I've seen involved with creating a mail 

server, but I'm trying to use just Postfix. Postfix can send and receive email right?

My server runs in my basement and runs Ubuntu Server 10.10. It uses Cherokee as its web server, and it runs several 

other servers as well (SSH, FTP, Git, etc). My goal is to set up a mail server so that websites I run such as a 

Redmine or a web forum can send emails to people (e.g. an activation email for a user registering on a forum).

Anyway, I set up postfix, and now my server can receive email. I've been able to send an email from my Gmail address 

to [email]drew@myhostname[/email] (my server), and it works. However, if I try to send email from [email]

drew@myhostname[/email] to my Gmail, it never goes through. I don't care about receiving email, as my only goal 

is to be able to send it.

I can post any configuration files you want to see. Any help is appreciated!

---

### Post by usatonycuba on 2011-04-16
You do receives mail from these external sources, it means that your server is configured correctly, then what happens? .... 

The mail servers have a different way of seeing things .. remember that if there were no rules .. then anyone can have a mail server and infect the outside world with e-span, virus .. and other things.

Mail servers such as hot mail, gmail and others .. allow not RECEIVE emails from sources considered "unreliable" or "not proven" as real sources.

Therefore, in order to your mail server, run to these other servers as they do to yours, you have, in the first instance, need to have a static IP, a FQDN, get your MX record very well specified on your server, etc, etc.

> **usatonycuba said:**
> 

 On the other hand, Hot-mail does not receive email from your email sever, because it recognizes as span .. do you have static IP, valid registered domain? ...

 You can check those link's

[http://ubuntuforums.org/showthread.php?t=614257](http://ubuntuforums.org/showthread.php?t=614257)

[URL="http://www.emailaddressmanager.com/tips/mail-settings.html"]http://www.emailaddressmanager.com/tips/mail-settings.html
[/URL]

---

### Post by dag10 on 2011-04-16
> **usatonycuba said:**
> You do receives mail from these external sources, it means that your server is configured correctly, then what happens? .... 

The mail servers have a different way of seeing things .. remember that if there were no rules .. then anyone can have a mail server and infect the outside world with e-span, virus .. and other things.

Mail servers such as hot mail, gmail and others .. allow not RECEIVE emails from sources considered "unreliable" or "not proven" as real sources.

Therefore, in order to your mail server, run to these other servers as they do to yours, you have, in the first instance, need to have a static IP, a FQDN, get your MX record very well specified on your server, etc, etc.

I have a dynamic IP that changes at most every 6 months. I have a domain registered through dyndns.org mapped to my IP address.

---

### Post by lisati on 2011-04-16
> **dag10 said:**
> I have a dynamic IP that changes at most every 6 months. I have a domain registered through dyndns.org mapped to my IP address.

Setting up Postfix to work with a dynamic IP address can be confusing for the newcomer, but isn't impossible. 

The most likely reason I can think of at the moment is that Dyndns has the "wrong" ip address. There are a couple of possible solutions to this. One involves setting your modem/router to automatically update Dyndns's records automatically, assuming your modem/router supports this. Another is to use software that runs on your server to do this automatically: if memory serves correctly, Dyndns has software to do this for you.

Another possibility is that your router needs to be set to forward port 25 to your server.

---

### Post by usatonycuba on 2011-04-16
STATIC IP.. meant to be static... no dynamic (even that dynamic IP takes 3 years to change to a new one)

---

### Post by dag10 on 2011-04-16
> **lisati said:**
> Setting up Postfix to work with a dynamic IP address can be confusing for the newcomer, but isn't impossible. 

The most likely reason I can think of at the moment is that Dyndns has the "wrong" ip address. There are a couple of possible solutions to this. One involves setting your modem/router to automatically update Dyndns's records automatically, assuming your modem/router supports this. Another is to use software that runs on your server to do this automatically: if memory serves correctly, Dyndns has software to do this for you.

Another possibility is that your router needs to be set to forward port 25 to your server.

My DNS's IP is correct. My websites are all online, and as I said, my mail server can *receive* mail. It's just unable to send it out for some reason.

Here is the contents of /var/log/mail.log if it helps:
[http://pastebin.com/1tY8iW2k](http://pastebin.com/1tY8iW2k)

---

### Post by dag10 on 2011-04-16
> **usatonycuba said:**
> STATIC IP.. meant to be static... no dynamic (even that dynamic IP takes 3 years to change to a new one)

Any particular reason why? How does an outside server know if you have a static IP or not?

(Woops, forgot about multi-quote)

---

### Post by usatonycuba on 2011-04-16
> **lisati said:**
> Setting up Postfix to work with a dynamic IP address can be confusing for the newcomer, but isn't impossible. 

The most likely reason I can think of at the moment is that Dyndns has the "wrong" ip address. There are a couple of possible solutions to this. One involves setting your modem/router to automatically update Dyndns's records automatically, assuming your modem/router supports this. Another is to use software that runs on your server to do this automatically: if memory serves correctly, Dyndns has software to do this for you.

Another possibility is that your router needs to be set to forward port 25 to your server.
Any link would be nice to take notes ?

I have tried this type of configuration in the past .. a total waste of time and no luck at all .. with a set DNS for my dynamic ip address, behind a router configured to redirect all request to my DNS server, with a no-ip.com software on my server to detect changes in my IP of my server and used to redirect all incoming request >> constantly pointing to my FQDN, and none of the solutions worked .. until I had to hire a static ip, which solved all my problems.

---

### Post by usatonycuba on 2011-04-16
> **dag10 said:**
> Any particular reason why? How does an outside server know if you have a static IP or not?

(Woops, forgot about multi-quote)
Dynamic Host Configuration Protocol <<and>> DNS

An easy way ... [http://searchwindevelopment.techtarget.com/definition/static-IP-address-dynamic-IP-address](http://searchwindevelopment.techtarget.com/definition/static-IP-address-dynamic-IP-address)

---

### Post by lisati on 2011-04-16
> **dag10 said:**
> My DNS's IP is correct. My websites are all online, and as I said, my mail server can *receive* mail. It's just unable to send it out for some reason.

Here is the contents of /var/log/mail.log if it helps:
[s][http://pastebin.com/QdJ4mrv1](http://pastebin.com/QdJ4mrv1)[/s]
[http://pastebin.com/1tY8iW2k](http://pastebin.com/1tY8iW2k)
Sorry, my bad.

It's possible that your ISP is blocking outbound mail. Some get a bit fussy like that, and unless you arrange with them for outgoing mail to be unblocked, it won't get out. An alternative to getting on your ISP's case to unblock outgoing mail is with Postfix's ["relayhost"]("http://www.postfix.org/postconf.5.html#relayhost") parameter.


edit: oops forgot to say to use the relayhost parameter to send email via your ISP's servers

---

### Post by MakOwner on 2011-04-16
.

---

### Post by SeijiSensei on 2011-04-16
As that "someone" I'll recommend a different test to see if your outbound mail is blocked.  From your server, run:

```
telnet gmail-smtp-in.l.google.com 25
```

If your connection times out, you're blocked.

(The sequence MakOwner quoted is to test whether a mail server is an "open relay."  You'd run this sequence of commands from an external machine to test whether you can push messages addressed with randomly-chosen From and To address through your server.  That's an important thing to test for, too, but it's not relevant to your current problem which concerns *outgoing* mail rather than incoming mail.)

---

### Post by MakOwner on 2011-04-16
> **SeijiSensei said:**
> As that "someone" I'll recommend a different test to see if your outbound mail is blocked.  From your server, run:

```
telnet gmail-smtp-in.l.google.com 25
```

If your connection times out, you're blocked.

From the horse's mouth :)

---

### Post by dag10 on 2011-04-16
> **SeijiSensei said:**
> As that "someone" I'll recommend a different test to see if your outbound mail is blocked.  From your server, run:

```
telnet gmail-smtp-in.l.google.com 25
```

If your connection times out, you're blocked.

(The sequence MakOwner quoted is to test whether a mail server is an "open relay."  You'd run this sequence of commands from an external machine to test whether you can push messages addressed with randomly-chosen From and To address through your server.  That's an important thing to test for, too, but it's not relevant to your current problem which concerns *outgoing* mail rather than incoming mail.)

Timed out. What can I do?

I was, however, able to telnet to outgoing.verizon.net:25

---

### Post by dag10 on 2011-04-16
Someone just pointed out to me that my IP might be blacklisted from sending direct email on Spamhaus.org. Indeed it is blacklisted on the PBL Advisory: [http://www.spamhaus.org/query/bl?ip=173.49.136.135](http://www.spamhaus.org/query/bl?ip=173.49.136.135)

The "reason" is that, as some of you said, Verizon wants me to send out emails through their servers. How can I do that? I know it has to do with the *relayhost* property, but I already tried outgoing.verizon.net and outgoing.verizon.net:25, and my emails still won't reach anybody. What can I do?

---

### Post by MakOwner on 2011-04-16
> **dag10 said:**
> Someone just pointed out to me that my IP might be blacklisted from sending direct email on Spamhaus.org. Indeed it is blacklisted on the PBL Advisory: [http://www.spamhaus.org/query/bl?ip=173.49.136.135](http://www.spamhaus.org/query/bl?ip=173.49.136.135)

The "reason" is that, as some of you said, Verizon wants me to send out emails through their servers. How can I do that? I know it has to do with the *relayhost* property, but I already tried outgoing.verizon.net and outgoing.verizon.net:25, and my emails still won't reach anybody. What can I do?

It's my uninformed opinion that it's Verizon's effort to get more cash out of you.  For resident level accounts they block most ports and will only open them if you pay for a business account -- typically more than double the $$, but over the very same facilities you get the residential service.  

If I had any real options ...

---

### Post by SeijiSensei on 2011-04-16
Try using port 587 at Verizon instead of 25.

---

### Post by dag10 on 2011-04-16
> **MakOwner said:**
> It's my uninformed opinion that it's Verizon's effort to get more cash out of you.  For resident level accounts they block most ports and will only open them if you pay for a business account -- typically more than double the $$, but over the very same facilities you get the residential service.  

If I had any real options ...

I currently have no incoming/outgoing ports blocked.

---

### Post by dag10 on 2011-04-16
-snip double post-

---

