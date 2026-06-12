---
title: "FQDN? Attempting to set up server for first time..."
date: 2009-02-13
forum: Server Platforms
---

### Post by infallible on 2009-02-13
After using ubuntu 8.04 amd64 for a while, I've decided to incorporate some server functionality into my system, mostly following guides and howto's because of my ignorance. I'm starting out with a postfix mail server based on this [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/") guide, and I keep encountering notifications about the "fully qualified domain name" and "ServerName". How do I set this up? It seems like I should do so before I continue too far. I'm also not sure when (or how, but I'll get to it when the time comes, i suppose) I should point my domain name towards my server via GoDaddy's stuff. Can anyone help out a guy who is so new to the server game?

---

### Post by LarsW_Tierp on 2009-02-13
Hi
I think that you might get your hostname by running "hostname" in terminal.
The FQDN is the URL that u use when connecting to your server from Internet. eg. mail.yourdomain.com

BR
Lasse

---

### Post by infallible on 2009-02-14
Thanks, lars, but I'm not sure how to apply that information. In fact, now that I've progressed halfway into the setup of flurdy's guide, I'm not even sure what functionality I will have gained, or if I can even use it. I'm going to bail on postfix and play with apache for a while, I think.

---

### Post by HermanAB on 2009-02-14
In file /etc/sysconfig/network:
HOSTNAME=mail.example.com

Then restart networking.

In Godaddy, define the domain name mail.example.com, A, MX and PTR records.  With your ISP, ensure that you have a small business server account, else port 25 will be blocked and your server won't work.

Hope that helps!

Herman

---

### Post by infallible on 2009-02-15
hmm...

apache is still giving me the ServerName diatribe. 
there is no /etc/sysconfig/ folder.
I'm using 8.04amd64, if that makes a difference.
qwest assures me that my residential account with static IP will suffice for what little traffic I expect, but I'm not there yet...

---

