---
title: "[SOLVED] Advice on name based virtual host one FQDN"
date: 2008-09-05
forum: Server Platforms
---

### Post by volkswagner on 2008-09-05
I am using an LAMP Ubuntu 6.06.

I have webmin installed.  I have in the past created a name based virtual host.  Well, at least I thought I did.  I can't seem to reproduce the same outcome.

I have one FQDN = [www.volkswagner.com](www.volkswagner.com), genius I know.  I have DynDns running to resolve my dynamic ip.

Past setup I had site one come up with volkswagner.com. I would get site two up with volkswagner.com/site2.

I wanted to add TWiki to the server.  I am not sure how I should clean this up.  While trying to add a second virtual host, I botched my previous setup.  

My first question, can I cleanly run multiple hosts, with one FQDN?  Should I change the format to:

site1= volkswagner.com
site2= site2.volkswagner.com
wiki= wiki.volkswager.com

Can I do the above without paying for additional domain fees?  
I think these would be considered subdomains?
If I create these as subdomains at godaddy, do I forward them to the same name, ie: the actual subdomain?  When I clik add subdomain this is what I am greeted with (screen shot attached).

---

### Post by windependence on 2008-09-05
OK, well you do not need another domain name to do what you want.

I would approach this with subdomains just like you posted. Looks good to me. Each subdomain will be a different virtual host.

Yes, each subdomain will still point to the same IP address or FQDN from your GoDaddy domain control panel. Apache will sort out where they go on your server.

You really should explore learning more CLI and try to rely less on WebMin, because sometimes WebMin doesn't always do things the way you expect. If you need help we are here to help you. :)

-Tim

---

### Post by volkswagner on 2008-09-05
Thanks for the fast reply.  Can you point me to a how-to on adding name based virtual host.  I don't mind CLI.

I know this has been asked many times.  I can't seem to locate how I set up previously.  When I tried the following, it gave errors when I previously had none.  Maybe because I had previous set up, or because I am running 6.06 not hardy.

[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1]("http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1")

---

### Post by windependence on 2008-09-05
Here's some for Dapper:

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

[http://www.cahilig.org/apache2-name-based-virtual-hosting-debianubuntu](http://www.cahilig.org/apache2-name-based-virtual-hosting-debianubuntu)

This may also help:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

[http://www.daryl.mu/2008/01/20/howto-set-up-apache-virtual-hosts-on-ubuntu-gutsy-gibbon/](http://www.daryl.mu/2008/01/20/howto-set-up-apache-virtual-hosts-on-ubuntu-gutsy-gibbon/)

-Tim

---

### Post by volkswagner on 2008-09-05
Thanks again.  

I just discovered the subdomain will need to be set up at dyndns not godaddy. When I add a host a dyndns I prompted to choose one of three....

.```
 Service Type

    *
      Sets host to one of three possible states.
      &#8211; Host With IP address would allow visitors to access services at your network by IP address;
      &#8211; WebHop Redirect would redirect web-requests from address http://www.yourname.example.org to URL that you would provide below;
      &#8211; Offline Hostname will hide your host IP or URL redirection settings (useful for temporary maintenance).

```

I am not sure what to choose here.  My first instinct was ip address, than the next choice was auto detected ip.  I don't think this is correct.  It seems I may need to choose my top level domain, to keep the dynamic redirects.  Will apache be able to handle this.  It seems as per your earlier post, answer would be yes.

Edit:  Now I am getting more confused.  Do I need to make an alias rather than additional host.  I see add alies (CNAME), this is how the "www" was added to the top level domain.

---

### Post by volkswagner on 2008-09-07
Well I got it all sorted.  I learned a lot, still too much more to learn.

I added the subdomains at dyndns, since they are handling my DNS.  I used the subdomain names to create the name of the virtual host in apache.  I did end up having better luck through webmin.  With all the vast information on the net about virtual hosts, it was difficult to weed through my particular situation.  

It seemed the choices for what address to use, for the VH was where I had the most trouble.  What seemed best for me was to choose "on all addresses".  When I tried to use anything else, apache would complain of overlap.

Thanks again for the help.

---

