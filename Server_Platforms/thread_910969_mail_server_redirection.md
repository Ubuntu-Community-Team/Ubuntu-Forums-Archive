---
title: "mail server redirection"
date: 2008-09-05
forum: Server Platforms
---

### Post by devonps on 2008-09-05
Hi,

I've setup a sub-domain which is [mail.thedcl.co.uk](mail.thedcl.co.uk), which I want my users to point to for their webmail access.

Currently this domain takes me to my default domain page [www.thedcl.co.uk](www.thedcl.co.uk). My question is Where do I make the redirection changes so that the users can collect their mail?

BTW: If it makes any difference I'm using Citadel for my mail solution.

Any help is appreciated,

Steve.

---

### Post by windependence on 2008-09-05
You're gonna have to point your MX records at the mail server from your domain control panel with your registrar.

HermannAB is the man to ask about the citadel configuration.

-Tim

---

### Post by devonps on 2008-09-05
> **windependence said:**
> 
HermannAB is the man to ask about the citadel configuration.

-Tim

I'm fine with the Citdel config - it's already running from the internal LAN side of things.

Thanks anyway,

Steve.

---

### Post by windependence on 2008-09-05
Well, to make your subdomain go right to your webmail page, you could just set up a vitual name based host and point it at your mail page for the doc root. No changes would be necessary for the domain DNS that way, but if users type mail.thedcl.co.uk, they will go right to the webmail page. Is that what you wanted to do?

-Tim

---

### Post by devonps on 2008-09-05
Yes that's exactly what I want to happen. :)

---

### Post by devonps on 2008-09-06
> **windependence said:**
> Well, to make your subdomain go right to your webmail page, you could just set up a vitual name based host and point it at your mail page for the doc root.
-Tim

Am I correct in assuming that this would be done from within the Apache config file?

---

### Post by windependence on 2008-09-06
You would define these in /etc/apache2/sites-enabled. After they are defined, you would need to enable them with a2ensite example.com.

More info here:

[http://www.cahilig.org/apache2-name-based-virtual-hosting-debianubuntu](http://www.cahilig.org/apache2-name-based-virtual-hosting-debianubuntu)

-Tim

---

### Post by devonps on 2008-09-08
Hi,

I've configured the Apache web server to present 2 different pages when using either [http://thedcl.co.uk](http://thedcl.co.uk) and [http://mail.thedcl.co.uk](http://mail.thedcl.co.uk), using virtualhosts.

This is not quite what I want. What I want to happen for the 2nd URL is that the user is displayed a login page automatically rather than a static html page.

I can access the email login page via the internal LAN - using the server's name and/or IP address.

How can I "redirect" the user automatically to their email login page?

I can access the email login page by appending the port number to the URL - but I'd prefer not to use this method.

---

