---
title: "webserver mail forwarding"
date: 2008-08-17
forum: Server Platforms
---

### Post by stefansjs on 2008-08-17
I recently purchased myself a domain, and I would like to have an email address associated with that domain.  I already have the web server up and running (DNS points to my computer) and I would like to install a mail server that I can use to forward to my gmail account.  I don't actually want to host email on my computer, I just want it to serve as a forwarding server.  I have read several guides with no luck.  I've already install postfix, configured it for tls and ssl, and created server certificates.  What I would like to know is two things:
1.  How do I configure the mail server to forward all my email to gmail.
2.  If I can't figure out how to forward my mail, how do I access the mail server and/or configure the mail server for access from thunderbird (or any other client).  (I may want to do this in the future anyways)

thanks in advance

---

### Post by mbeach on 2008-08-17
if you are doing this for interest sake, then by all means - fill your boots.  If you want a less labour intensive solution, I'd suggest using Google hosted services (google apps) which will give you email address @ your domain with the gmail interface.

what I like about this
- if you are already using Gmail, it allows you send mail from both accounts from your current gmail - ie when you are sending a message you can send it from either you@yournewdomain, or [email]you@gmail.com[/email]
- you already know the benefits of gmail (pop,imap,forwarding etc)
- storage space
- nothing to setup on your own server

The only issue I've really had so far was getting a fax/scanner to send mail from a gmail address - the fax machine couldn't deal with gmail's certificates etc, so postfix was utilized for that acting as the middleman.

[http://www.google.com/a/help/intl/en/index.html](http://www.google.com/a/help/intl/en/index.html)
its free.

[edit:]video overview at:
[http://www.google.com/a/help/intl/en/admins/resources/setup/](http://www.google.com/a/help/intl/en/admins/resources/setup/)

---

### Post by stefansjs on 2008-08-18
I would like to know how to set up a mail server, not how to get access to an email account with my domain as the address.  Yeah, Google will do all the work for me, but I want to know how to set it up so that I might be able to in the future just switch over to my mail server (with as much storage as my hard drive will hold).

---

### Post by HermanAB on 2008-08-18
Use nullmailer.

Cheers,

Herman

---

