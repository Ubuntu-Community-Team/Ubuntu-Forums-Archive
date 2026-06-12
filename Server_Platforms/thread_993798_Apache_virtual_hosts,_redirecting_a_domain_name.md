---
title: "Apache virtual hosts, redirecting a domain name"
date: 2008-11-26
forum: Server Platforms
---

### Post by pslStu on 2008-11-26
Greetings

Apologies if this is repeated elsewhere, I couldn't seem to find exactly what I was after. (and moved the thread here by a suggestion in the Beginners forum).

What I would like to do is redirect a specific incoming domain name on to another domain name, while keeping the original in the address bar.
So, a user types in [www.domain1.com](www.domain1.com), which points to my server, and I want it to automatically redirect to [www.domain2.com](www.domain2.com), but still show [www.domain1.com](www.domain1.com) in the address bar.
(it seems most domain name providers have this feature in a nice little package waiting to be used, but not the one I'm with, and changing it isn't an option)

I'm using individual Virtual Host files in /etc/apache2/sites-available as it's a multi-domain server, indentifying by name.

I found ```
Redirect / http://www.domaintobeforwardedto.com/
``` on a website, which does redirect if I place it within the <VirtualHost> tag of the virtual host file, but it changes the URL in the address bar.

I should also add that this is a temporary measure, as it doesn't seem best practice, but unfortunately it's required.

It was suggested that I change the CNAME of domain1.com to the A of domain2.com, but I don't think that's going to be possible as the domain2.com is a WordPress.com hosted blog. (or is it possible? I'm not sure)

Can anyone help me out?

---

### Post by Philio on 2008-11-26
You can just point both domains at the same IP address (an A record or CNAME record will work), and then add a ServerAlias into your Apache config like:

<VirtualHost 1.2.3.4:80>
  ServerName domain1.com
  ServerAlias domain2.com
  etc
</VirtualHost>

---

