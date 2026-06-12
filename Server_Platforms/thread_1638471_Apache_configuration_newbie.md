---
title: "Apache configuration newbie"
date: 2010-12-05
forum: Server Platforms
---

### Post by mpratt on 2010-12-05
Hello,
I am new to the server world, and I am trying to get an apache website up and running. I am running 10.04 lts and I need help to try to figure out how to set up a named virtual host, which files to modify and how to modify them.
thanks,
Mike

---

### Post by windependence on 2010-12-05
Mike,
 
Are you only running one website?
 
-Tim

---

### Post by mpratt on 2010-12-05
Yes, jst one site, I am just trying to learn the virtualhosts for own personal knowledge.

---

### Post by mpratt on 2010-12-05
Update, when I type in my domain name it now takes me to the correct website, but when I type in the ip address of the computer, it takes me to the apache default site, what could cause this?

---

### Post by SeijiSensei on 2010-12-05
> **mpratt said:**
> Update, when I type in my domain name it now takes me to the correct website, but when I type in the ip address of the computer, it takes me to the apache default site, what could cause this?

The default site traps all connections to the server that don't include a named virtual host in the URL.  This is the correct behavior.  If you want the computer to serve only one site regardless of the hostname given, place your website files under /var/www replacing the default "It Works!" index.html file.  I think you're much better off with the configuration you have now, though, with your site as a virtual host and the default site trapping any other requests.

---

### Post by mpratt on 2010-12-05
> **SeijiSensei said:**
> The default site traps all connections to the server that don't include a named virtual host in the URL. This is the correct behavior. If you want the computer to serve only one site regardless of the hostname given, place your website files under /var/www replacing the default "It Works!" index.html file. I think you're much better off with the configuration you have now, though, with your site as a virtual host and the default site trapping any other requests.
 
i appreciate the information, just one thing, when you say the default will trap everything but the domain name, the ip's are "blocked" from loading by apache? now if I create a new virtual host for a different domain, then both will be able to be reached by the respective domains, but blocked by ip?
 
thanks for the info

---

### Post by SeijiSensei on 2010-12-06
> **mpratt said:**
> i appreciate the information, just one thing, when you say the default will trap everything but the domain name, the ip's are "blocked" from loading by apache? now if I create a new virtual host for a different domain, then both will be able to be reached by the respective domains, but blocked by ip?
 
thanks for the info

I'm not sure what you mean by "blocked."  The server is correctly sending the page in /var/www/index.html when it encounters requests for which it has no virtual host defined.  That includes naked IP addresses.  The configuration for the default host is in /etc/apache2/sites-enabled/000-default.

You can set up countless virtual hosts with different ServerName directives.  A request for http://www.somedomain.com/ will get the pages in the DirectoryRoot associated with that ServerName.  A request for http://www.otherdomain.com/ will get the pages associated with that name.  I usually place each virtual host in a separate file under /sites-enabled/.

If you have another domain name tied to the server's IP address, but no virtual host defined for it, then requests for that domain will also get the default page.

---

### Post by mpratt on 2010-12-06
> **SeijiSensei said:**
> I'm not sure what you mean by "blocked." The server is correctly sending the page in /var/www/index.html when it encounters requests for which it has no virtual host defined. That includes naked IP addresses. The configuration for the default host is in /etc/apache2/sites-enabled/000-default.
 
You can set up countless virtual hosts with different ServerName directives. A request for [http://www.somedomain.com/](http://www.somedomain.com/) will get the pages in the DirectoryRoot associated with that ServerName. A request for [http://www.otherdomain.com/](http://www.otherdomain.com/) will get the pages associated with that name. I usually place each virtual host in a separate file under /sites-enabled/.
 
If you have another domain name tied to the server's IP address, but no virtual host defined for it, then requests for that domain will also get the default page.
 
Thank you, that answered the question I had. looks like I am fully up and running now.

---

