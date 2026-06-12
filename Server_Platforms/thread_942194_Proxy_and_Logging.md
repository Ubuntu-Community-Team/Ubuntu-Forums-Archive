---
title: "Proxy and Logging"
date: 2008-10-08
forum: Server Platforms
---

### Post by freelinuxhelp on 2008-10-08
Hi Everyone,
I'm forwarding DNS queries to OpenDNS as a form of content filtering. After running for a few months, I checked the log at OpenDNS.com to find that some of our users are visiting sites that are NOT appropriate for work. I showed the logs to upper management (my company is a firm believer in micro-managing its employees) and explained our options to them.
They are most interested in setting up a proxy server that provides content filtering, but also want to know who is attempting to access these sites. Do any of you have experience with this on Ubuntu?
I know about projects like Untangle and Monowall, but I already have a machine running Ubuntu Server 8.04.1, and I'd like to just run it there. If it matters, this is a network of about 250 machines with Windows 2003 servers and XP clients.
I've seen things like DansGuardian and Squid, but I'm not sure if they offer the reporting solutions that my managers are going to want.

---

### Post by lykwydchykyn on 2008-10-08
I only have a modest Dansguardian setup here at the house to keep the kids safe, but it does logging if you enable it (it may be default).  The logs record date and time, ip of the client, what was accessed, whether it was blocked or allowed, and why.

I don't know of a reporting tool of any sort for summarizing the logs, though if you're clever with python or ruby you might be able to make something of your own given the simplicity of the files.

Even with two computers hitting it, the logs fill up fast, just FYI.  Even a single web page can leave a couple dozen entries (every jpg, stylesheet, javascript, etc is a download).

---

### Post by elias@cpaefs.com on 2008-10-09
For dansguardiang or squid logging and reports I would recomend SARG

[http://sarg.sourceforge.net/](http://sarg.sourceforge.net/)

---

### Post by freelinuxhelp on 2008-10-09
SARG looks like it will do nicely. Thanks! :-)

---

