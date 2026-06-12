---
title: "Multiple email servers, single public IP?"
date: 2009-12-12
forum: Server Platforms
---

### Post by erict43 on 2009-12-12
I am running several servers behind a single static public IP.  A couple of web servers, for which I use reverse proxy, and a Windows SBS server which handles the email for my domain.

I would like to run a Linux server to host email for my brother-in-law's business, but I don't know if it's possible to do that within my network.  My router can only port forward, so anything coming in on SMTP can only be directed to a single internal server.

What would be the best way to do this, that would not involve me paying another $40/month for additional IP's?

Thanks!

---

### Post by JeSTeR7 on 2009-12-12
I think you might be better off just setting up your existing SBS server to also handle your brothers domain.

---

### Post by erict43 on 2009-12-12
True, but I don't believe that SBS allows more than the installed domain.  And, I wanted to try to keep his stuff seperate from mine.

---

### Post by JeSTeR7 on 2009-12-12
I fully understand if you want to keep it separate, but you can certainly add another email domain to your sbs (not another NT domain).

I don't know if there is a way around getting another IP because SMTP will only use port 25.  

Another option is using Google Apps email.  It's really the perfect solution for a small org.  You can use your own domain name but the interface is identical to Gmail.

---

### Post by volkswagner on 2009-12-12
> **erict43 said:**
> .....What would be the best way to do this, that would not involve me paying another $40/month for additional IP's?

Thanks!

You may consider renting a VPS solution.  You can get a few small VPS's from [Fivebean]("http://ubuntuforums.org/showthread.php?t=1128094") with Ubuntu Forum member discount, for $40/mo.

---

### Post by erict43 on 2009-12-15
I don't really need a VPS.  I've got a server with plenty of capacity running ESXi, and my other server is running my SBS domain.  Basically I'm looking for a reverse proxy for email.

I wonder, is it possible to set up a mail forwarder within my network, and add MX records to my internal DNS server directing email to the appropriate server?  Sounds too complex, but now I'm kind of wondering how it would be possible to make this work.

---

### Post by BkkBonanza on 2009-12-16
Unless you're worried about privacy issues then I second the google apps method as easiest overall. It works brilliantly for several domains I have. And it's free. Setting up involves adding dns entries for google and then you have both web mail and pop/imap/smtp available with your own domain.

Otherwise you'd have to try and find a virtual host like solution for email. Perhaps a proxy inside your lan that the router sends to and it's looks at the domain and switches to the right server. 

I know Nginx (a great web server) has some email proxy features. I'd read up on that at [http://wiki.nginx.org/NginxMailCoreModule](http://wiki.nginx.org/NginxMailCoreModule). It has something about using an http server to determine which backend to route to.

Update: I found this little blurb of info using google. May help,

```
The nginx IMAP proxy can speak to a CGI to do IMAP authentication munging.

The CGI does whatever user lookups you need. The auth script then returns to
nginx the username, hostname, port, etc, to nginx which hands that off to the
IMAP server you specify for authentication.

At work we use a Catalyst server for this:

 * Client hits nginx
 * nginx hits auth_server.pl
 * auth_server.pl uses the passed-in username to look up the user's IMAP/POP
   server:port, and their internal account ID (which is what Cyrus uses for
   authentication)
 * auth_server.pl passes the above back to nginx
 * nginx proxies the connection to the user's IMAP/POP server:port, using the
   new acctid@domain credentials

The example on the nginx wiki seems to be pretty clear, using a simple PHP
script:

http://wiki.nginx.org/NginxImapAuthenticateWithApachePhpScript

We've been using this for a bit over two years, without issue. nginx is pretty
great, and the IMAP/POP proxying works very well. 
```

---

