---
title: "Clarification on DNS"
date: 2007-06-04
forum: Server Platforms
---

### Post by pkarjala on 2007-06-04
In the continuing saga of setting up our own LAMP server, my boss recently asked whether we had a DNS  installed on it.  I notified him that we do, but it's not currently configured or actively running.

He seems to be of the mindset that we HAVE to have a DNS running on the LAMP install in order for web pages to serve.  I'm pretty sure this isn't the case, but wanted to ask a few questions just to make sure.

- If we have our LAMP server running on a public static IP address serving up our webpage, and have our domain registrar point a domain name at it, is any further action required on our part?
- What use would a DNS be required for?  An example I can think of is if we had a large network locally hosted and wanted to have a local DNS to speed up URL resolution.  Are there other good examples I can use?
- Is there ever a case that you would need to have a DNS running on a computer that is also serving up web pages?

Thanks again, Ubuntu forum folken!

---

### Post by turinglabs on 2007-06-05
You don't need a DNS server if all you want to do is serve public web pages, and already have your server's hostname registered with your registrar's DNS servers. You are right in that you could run what is called a caching-only nameserver on this box, and point your internal clients at it to speed up name resolution (think of it as a DNS proxy). This is opposed to an authoritative name server, which is the final authority for name/address mappings in a particular domain. This authoritative one is what your registrar has, and what you don't need.

You could also have a DNS server running on that box that has a 'split' configuration, so that it forwards requests for internet hostnames to outside servers, but handles any internal domains as authoritative. One of the best reference books for DNS if you are interested is O'reilly's 'DNS and Bind'.

---

### Post by pkarjala on 2007-06-05
Thank you very much for the clarifications, Doug.  :)

---

