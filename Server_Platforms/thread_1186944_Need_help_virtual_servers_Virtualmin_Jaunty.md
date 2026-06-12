---
title: "Need help virtual servers Virtualmin Jaunty"
date: 2009-06-14
forum: Server Platforms
---

### Post by ingenuitylabs on 2009-06-14
I'm still new to Linux.
I have installed Jaunty with Virtualmin, and have a virtual server working and everything setup.  I am using dynamic IP with dyndns.com forwarding.

My problem is this:

My server is on ip 192.168.1.45
virtual server is 192.168.1.55

I cannot for the life of me (and I've searched for 2 days) figure out how to direct the user to the proper folder on the server.  I know there is a simple solution but I cannot figure it out.  My default folder for the (main admin?) server is /var/www   the folder for the virtual server is /home/public_html.  I have a domain that is forwarded to dyndns.com which then forwards to my server ip 192.168.1.45.  How do I tell the server to accept this particular domain and show the virtual server folders instead of the root default?  When I enter the domain it goes to my server just fine, but it displays the root folder instead of the virtual one.  Hope I'm explaining it right.  

Also, I setup ftp access through the virtual server username etc., and went just fine to the /home/public_html folder...so why does the domain not point there?

Please help! lol :)

Sorry if I haven't explained everything correctly, but any help would be more than appreciated.  thanks!

---

### Post by ingenuitylabs on 2009-06-14
Anyone?

I have checked the VirtualNameHost files etc. and everything looks correct to me.

If i type in 192.168.1.55 it takes me right there...just don't know how to tell it to go there when the server accepts connections on 192.168.1.45.

:(

---

### Post by SwellJoe on 2009-06-14
Start here:

[https://www.virtualmin.com/documentation/web/troubleshooting#the_wrong_site_shows_up](https://www.virtualmin.com/documentation/web/troubleshooting#the_wrong_site_shows_up)

It's usually that you have mismatches in your NameVirtualHost and VirtualHost sections.  Most folks get really confused by how *:80 and 192.168.1.1:80 style host selectors work, and so we recommend you stick with always using a specific IP and removing all references to * in the Apache configuration.  (It's possible to get it all working correctly inter-mixing them, but even I have problems doing so, and I've been configuring Apache for a dozen years or more.)

Feel free to hit us up for advice in the Virtualmin forums.  I'll try to remember to keep an eye on this thread, but I'm not a regular here.

---

### Post by ingenuitylabs on 2009-06-15
Thanks for the info.  I will check out the virtualmin forum.  I think last time I tried the server were down or something, but I'm eager to get this figured out :)

---

