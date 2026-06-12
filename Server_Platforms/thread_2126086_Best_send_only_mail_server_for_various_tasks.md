---
title: "Best send only mail server for various tasks"
date: 2013-03-15
forum: Server Platforms
---

### Post by xkaliburx on 2013-03-15
We run our real mail through an enterprise system, but it does not allow relaying, so I looking to setup a mail server that can be used for our webservers, and other processes that need to send mail.  Some systems goto customers, so currently a lot of mail is either being rejected to put into spam due to various reasons like no reverse dns, no spf, etc. so I am going to make those DNS records to a subdomain like notices.mydomain.com this way things are legit.

I know I don't need a real mail server on each server (some are behind load balancers, etc.) so as I think I have to do it would be;

1. Setup public mail server (what would be the best for a strictly send only mail server).
2. Setup local servers when they are sending mail to use him

I don't think I am missing much else, so are there any how-to's or at least some feedback on a best method?

Thanks.

---

### Post by sanderj on 2013-03-16
Don't create a mail server unless you really know what you're doing and you're willing to monitor it 24x7.

Why don't you use the smart host (=smtp relay server) of the location the server is in?

And: what is from-address-domain and the to-address-domain?

---

### Post by CharlesA on 2013-03-16
> **sanderj said:**
> Don't create a mail server unless you really know what you're doing and you're willing to monitor it 24x7.

Why don't you use the smart host (=smtp relay server) of the location the server is in?

And: what is from-address-domain and the to-address-domain?

+1 to all of the above.

I use a similar setup on my home server to send notifications of updates, backups, etc.

---

### Post by smeerbartje on 2013-03-16
> **CharlesA said:**
> +1 to all of the above.

I use a similar setup on my home server to send notifications of updates, backups, etc.

Can you please tell me how you have set this up?

---

### Post by CharlesA on 2013-03-16
Check out the Postfix tutorial here: [http://charlesa.net/tutorials/tutorials.php](http://charlesa.net/tutorials/tutorials.php)

It might give you an idea.

---

### Post by smeerbartje on 2013-03-17
Thanks; will the php mail() function also work with this Postfix thing?

---

### Post by CharlesA on 2013-03-17
> **smeerbartje said:**
> Thanks; will the php mail() function also work with this Postfix thing?

It should, but I haven't tested it.

---

### Post by xkaliburx on 2013-03-21
Sorry was away for a few days.  So, to answer;

> **sanderj said:**
> Don't create a mail server unless you really know what you're doing and you're willing to monitor it 24x7.

I don't have an issue, I already have 50+ servers monitored using nagios, so another server/service is no biggie.   I am familiar with setting up a postfix box, locking it down to specific relaying, setting up the spf/dkim signing, but this is another task since it's not one server local sending mail.

> **sanderj said:**
> Why don't you use the smart host (=smtp relay server) of the location the server is in?    
This is more what I was looking for.  I will have setup the standalone mail server, but was unsure on how to tell the webserver or other service don't send the mail using the local but go over to that mail server who will send and won't have a problem.   So it's more the =smtp relay I am looking to setup.   Now that I am back, I will start doing some more reading ...

tnx

---

