---
title: "All subdomains redirecting to default page... how do I stop this?"
date: 2011-10-12
forum: Server Platforms
---

### Post by CaffeineFreeless on 2011-10-12
All subdomains that I type in for my domain (made up, anything I don't specify in a VirtualHost or something) end up redirecting to the main page of the domain (ie [www.something.com](www.something.com)).

I don't like this behavior. I'd rather non-existent subdomains 404 instead.

Any ideas what might be causing this behavior?

---

### Post by volkswagner on 2011-10-13
Do you have a wildcard setup on your DNS server?

Is your server on your local LAN?  If so does this happen to clients outside your LAN?

---

### Post by Jonathan L on 2011-10-13
> **CaffeineFreeless said:**
> All subdomains that I type in for my domain (made up, anything I don't specify in a VirtualHost or something) end up redirecting to the main page of the domain (ie [www.something.com]("http://www.something.com")).

I don't like this behavior. I'd rather non-existent subdomains 404 instead.

Any ideas what might be causing this behavior?

Hi Caffeine

If you are getting to the correct server, then your DNS is okay.  (Otherwise your browser would give you no such server.)

I take it you're using Apache as your web server, with virtual hosts for a number of things.  The first virtual host is the default one.  [http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

So put your real hosts in virtuals, and have the "oops 404 no such domain" host as the first virtual.

Hope that helps.

Kind regards,
Jonathan.

---

