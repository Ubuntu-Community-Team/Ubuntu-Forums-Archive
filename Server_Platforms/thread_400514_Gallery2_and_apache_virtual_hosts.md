---
title: "Gallery2 and apache virtual hosts"
date: 2007-04-03
forum: Server Platforms
---

### Post by -hecate- on 2007-04-03
When gallery2 is setup to use an apache virtual host, such as gallery2.blah.com - in the default config it appears to hijack all requests for hosts that aren't defined as a virtual host. Eg: Browsing to the IP address of the server takes you to gallery2. It effectively makes the gallery2 install the default virtual host.

Looking at /etc/apache2/apache2.conf, it appears this is happening because /etc/gallery2/apache.conf is being loaded *before* the virtual host configurations - /etc/apache2/sites-enabled/000-default does not get loaded first.

Is this a known issue? a quick scan of the forums doesn't show up any similar posts...

---

### Post by pppetter on 2007-04-03
I for one can't figure out how that could happen, mainly since _I assume_ it's described in your gallery2 virtualhost file where it's document root is, and what domainname it's suppose to answer to.

I have no idea what could actually cause your problem. And I don't know why you are talking about apache2.conf. I use gallery one and set it up with an enabled virtualhost file in /etc/apache2/sites-available/ like this:
> NameVirtualHost *
<Virtualhost *>
ServerName galleri.bounceme.net
DocumentRoot /var/www/galleri
</Virtualhost>

I have another one pointing to /var/www, but that has nothing to do with it. If what you are writing here is true, then this is flaw in apache itself.

But chances are you just missed something. For example, setting the document root in the gallery software itself (with the configuration wizard)...

I'm not the best person at giving pointers on what to check, but I hope this might help you somehow :)

---

