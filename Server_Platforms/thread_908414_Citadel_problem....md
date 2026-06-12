---
title: "Citadel problem..."
date: 2008-09-02
forum: Server Platforms
---

### Post by enigma_0Z on 2008-09-02
I'm trying to set up a citadel groupware server, but I'm having a small issue.

Using webcit, I can mail to and from any user, but using SMTP & IMAP, I can only receive e-mail. I've set up a simple bind9 server to provide the MX record necessary for remote mail to work, but every time I send mail to user@citadel-server, it goes to the admin user on the citadal server instead.

Is this *normal* or have I screwed something up?

Thanks.

---

### Post by jamesrfla on 2008-09-02
You need to edit the user's settings and make sure it has the right internet e-mail address for that user.

---

### Post by enigma_0Z on 2008-09-02
Do you mean the "Primary Internet E-mail Address" under the user's address book entry? I've had that already set... Or is there some other setting that I'm missing?

-- edit --

Maybe I wasn't making myself clear... I want to create internet e-mail addresses for users using citadel... do I need a separate package for that? I'd like mail to be able to delivered to and from user@server where server is my citadel server.

I've got the whole thing set up in a virtual environment, and I've got bind9 running on the citadel server for the MX record necessary, is there something with my environment that I missed?

---

### Post by jamesrfla on 2008-09-02
All I did was add the new user in the administration tab. Then put in the Primary Internet E-mail Address and that was it. Have you port forwarded port 25 in your router yet? I would try log in into webcit. Going to administration on the left. Then click Edit site-wide configuration. The make sure in the first tab that you changed Fully qualified domain name to your domain name. Hope this helps :)

---

### Post by lazyart on 2008-09-02
To create new email addresses, you have to first own a domain (or sub-domain) of some sort.  Once you've got that you'll set up an MX record with a DNS service that tells the world where email for your new domain should be routed to.  Likely it's going to your IP address.

If your IP address is like most of ours and it changes often (or even occasionally) you'll need a service like DYNDNS or NoIP that can update your MX record when your IP address changes.

It's a multi-step process (and a learning process) but it's not too bad.  Domains are pretty cheap to purchase (I think I paid $60 for 3 years for a .com), and the IP updating services are free also (I use freedns.org).  I have a cron job that updates my ip address once an hour.  I used Citadel for quite a while but then moved to Zimbra a couple weeks ago.  A bit more complicated but a much nicer interface and more flexible.

---

### Post by enigma_0Z on 2008-09-08
> **lazyart said:**
> To create new email addresses, you have to first own a domain (or sub-domain) of some sort.  Once you've got that you'll set up an MX record with a DNS service that tells the world where email for your new domain should be routed to.  Likely it's going to your IP address.

If your IP address is like most of ours and it changes often (or even occasionally) you'll need a service like DYNDNS or NoIP that can update your MX record when your IP address changes.

It's a multi-step process (and a learning process) but it's not too bad.  Domains are pretty cheap to purchase (I think I paid $60 for 3 years for a .com), and the IP updating services are free also (I use freedns.org).  I have a cron job that updates my ip address once an hour.  I used Citadel for quite a while but then moved to Zimbra a couple weeks ago.  A bit more complicated but a much nicer interface and more flexible.

Hmm. I shouldn't have to pay money for a domain if I set up everything outside of the Internet. I've got a slightly different issue than I described at first, now. 

The issue I'm getting now is "no such recipient", but first, here's the deal on the whole setup I'm working with:

I have two virtual computers, networked on a 192.168 subnet. The citadel server called "serve" (dns name is "serve") is @ 192.168.0.10 and is running citadel and bind9 (for the MX record req'd). The client server called "desktop" has a fixed address of 192.168.0.3, and points to 0.10 for DNS lookups, ergo:

```
$ host serve
serve has address 192.168.0.10
serve mail is handled by 10 serve.
```

I have a user on the desktop and on the citadel installation called "user". 

When I send mail on the desktop system (through smtp, in kmail) to "user@serve" manually, and "user@serve" is not in "primary internet e-mail address" for "user", the mail goes through with no problem, and lands in user's inbox. However, whenever I put "user@serve" into the primary internet e-mail address (so it will show up in the global address book), I get the message "no such recipient".

---

