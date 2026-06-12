---
title: "OpenSSL working for Firefox and Chrome, page errors with IE"
date: 2010-11-23
forum: Server Platforms
---

### Post by byb3 on 2010-11-23
Hi,

Basically I've got a web server running, I've become my own Certificate Authority, signed my server certificate and created a client certificate.

I've set up Apache to Require an SSL Certificate.

On the clients, I've added my own root CA to Trusted Root and the client certificate to Personal Certificates.

However, whenever I browse with IE6 or IE8 (I don't have IE7 to hand) the browser prompts for the certificate and I can choose it, but as soon as I choose it, it falls back to the terribly unhelpful 'Internet Explorer cannot display the webpage'.  

This works absolutely fine in Firefox and Chrome.  And from what I can tell, Chrome appears to use the same Certificate base as IE (where as Firefox looks to have its own independent one).  So if that is the case then my Certificates would appear to be set up fine, but IE will not load the page.

I honestly have no idea why.  On the apache error.log I get:
[Tue Nov 23 23:22:21 2010] [error] [client 172.21.25.51] Re-negotiation handshake failed: Not accepted by client!?

I would be happy as anyone to be able to dump IE, but I can't.

I realise this is an Ubuntu Forum, but the expertise on these sort of matters is much better on a forum like this and we're more likely to have faced them before.  I've been on the Microsoft forums and all I get is the usual advice to clear temporary settings and some other rubbish that doesn't work.  

Please can anyone offer some friendly advice.

Cheers,

---

### Post by byb3 on 2010-11-23
Something I have done has fixed it, but I am unsure of the combination.

I promise to re-visit this thread in the hope that someone else will be helped by this.

Cheers!

---

### Post by numeric_way on 2010-11-24
Hi,
Can you show us your apache configuration for this vhost using ssl?

---

