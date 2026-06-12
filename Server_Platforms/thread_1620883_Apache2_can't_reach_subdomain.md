---
title: "Apache2 can't reach subdomain"
date: 2010-11-13
forum: Server Platforms
---

### Post by alexlaban on 2010-11-13
Okay so I'm running apache2 with a couple of virtual hosts and 2 of those are running on the same domain. Now my problem is that one of those is suppose to run on a sub domain autv.example.com and the other on everything else but I can't get that to work.

I've got 2 files in sites-available autv.example.com and example.com  and both are enabled with symbolic links in sites-enabled.


So does anyone know what's wrong with my configuration?

---

### Post by James78 on 2010-11-14
Did you setup the subdomain in your DNS server? You Virtualhost configuration can be perfect, but it can't ever work without the correct DNS setup.

Also, please post your configuration. It's hard/impossible to tell you what's wrong without being able to read it for myself.

---

### Post by alexlaban on 2010-11-16
Never mind I fixed it, I had a default host for all invalid subdomains but seems like it got in conflict with the dev subdomain so I removed the default host and added so that [www.example.com](www.example.com) and *.example.me redirected to example.com

---

### Post by James78 on 2010-11-17
If you can in anyway, you should leave the default virtualhost, as it's there for a reason. It catches all traffic not designated anywhere else. The very first virtualhost encountered is the default one. So say, if I have a svn.domain.com virtualhost that apache encounters first (which makes it the default one; the vhost has svn logins and everything), with SSL and regular http, and I use SSL somewhere else on my site, I actually got prompts to login, even though I was using a completely different vhost. Took forever to track down, so the default vhost should always be left there.

Other areas:
- Accessing the server via IP will result in the first vhost encountered, wouldn't you rather make a default vhost that shows a page saying "use the full url"?
- And it will also catch any other unserved vhosts. For example, if I have specified in dns ftp.domain.com, it'll go to my home page if that's the first vhost, but as said right before here, if I use the default vhost with the nice "use the full url" page, it'll show that one instead, which is completely perfect, because I want that page to be shown for everything that a vhost is not configured for.

---

