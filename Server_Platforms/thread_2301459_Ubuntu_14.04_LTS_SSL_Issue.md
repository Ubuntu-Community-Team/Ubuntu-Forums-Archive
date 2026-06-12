---
title: "Ubuntu 14.04 LTS SSL Issue"
date: 2015-11-02
forum: Server Platforms
---

### Post by Mike_Ramsey on 2015-11-02
Greetings I have been using Ubuntu server for quite a few years now but I have a small problem that I hope someone can shed some light on. I use my server as a home server mainly for document storage etc. I also use it as a web server for experimenting and learning. I have recently been playing with owncloud, which works great by the way, however the recommended setup is to utilize https. My problem is that I am not using a FQDN since I am just hosting from my home internet connection using DynDNS to keep my public ip updated. Has anyone set up an SSL with a similar setup? Then I go to https:// the pages do not load. I use https when connecting to webmin and just get the warning but I can proceed anyway so I am assuming I am just overlooking something somewhere. Any suggestions are greatly appreciated.

---

### Post by sandyd on 2015-11-03
Can you post the configuration you are using for owncloud?

What you can do is generate a self-signed SSL certificate for use with owncloud with the common name set to the dyndns address.

---

### Post by Mike_Ramsey on 2015-11-09
Ok I solved the SSL issue by creating a self signed cert and I also solved the DynDns issue by moving my name servers to namecheap and utilizing their DNS tools. I how ever am still having an issue getting my sub.domains to properly resolve using https. One resolves but the css is all screwed up and the other which is owncloud, I just get a forbidden message that indicates not having permission to access the page.

---

### Post by sandyd on 2015-11-09
If you are getting an error about the Common Name not matching, and you set your own certificates to trusted, you will have to do one of the following.

a) Generate a wild card self-signed certificate (Set the CN to *.mydomain.com)
b) Generate a self signed certificate for each subdomain.

Also....
Browsers have been tightening the security belts for a while now, chrome will complain about loading non-https content on https/etc depending on server settings.

If you have oddities on the page, or some content is not loading, right click on the page, choose inspect element, and go to the console. Reload the page, and check if you have any errors.

For the subdomain that you are getting a forbidden message, check the apache2 logs for errors.

---

