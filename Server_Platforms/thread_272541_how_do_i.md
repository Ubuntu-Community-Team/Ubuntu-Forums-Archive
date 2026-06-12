---
title: "how do i?"
date: 2006-10-06
forum: Server Platforms
---

### Post by tmez on 2006-10-06
how do i add my domain to my webserver?

---

### Post by Macchi on 2006-10-06
Disclaimer: I am not an Apache guru but I have used it with moderately complex configurations. 

Let me first try to understand your problem:

For a public internet domain:
Do you have a DNS provider? Did you point your domain towards the IP address for your server on the internet? Is it a fixed or dynamic address? How is your server connected to the internet?
What do you mean by adding your domain to your webserver?

For your internal network:
Are you aware of how DNS and /etc/hosts work on your local network?
To be able to access your website from your local network (by its domain name) with the same url as from the internet you will need a local DNS server with caching and a mapping for your external domain towards the local server. Alternatively you may adjust the /etc/hosts file so that you (and Apache) can use the same url as from outside.

Regarding Apache:
Are you going to host different domains in the same server?
Then you will have to set up Virtual Hosts. Search for instructions on the forum. Add a new file to /etc/Apache2/sites-available and then use a2ensite to add the sites to the /etc/Apache2/sites-enabled. Remove them with a2dissite. Remember to restart/reload apache after changes.

---

### Post by tmez on 2006-10-06
i want to set my web server domain up on my web server

---

