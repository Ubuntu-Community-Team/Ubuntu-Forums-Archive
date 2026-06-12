---
title: "Assignig a domain name to my server"
date: 2012-10-23
forum: Server Platforms
---

### Post by prostudent on 2012-10-23
This may sound stupid.

I've got a server with a static IP address. Is there any way I can assign a domain name to it, like [www.domain.com?]("http://www.domain.com?")

---

### Post by CharlesA on 2012-10-23
You'd have to buy a domain and then create an A record for that domain, pointing to the IP address of the server.

Of course, that only applies if you want the box accessible from the Internet. If it is local only, you can assign whatever domain you want - example.com, blahblah.org, etc.

---

### Post by prostudent on 2012-10-23
And how do I make that locally?

---

### Post by CharlesA on 2012-10-23
Add an entry to DNS or your hosts file.

Doing it in DNS makes it easier to manage.

---

### Post by Lars Noodén on 2012-10-23
If it's local to just that machine and no others will use the domain, you can make an entry in [/etc/hosts](http://manpages.ubuntu.com/manpages/precise/en/man5/hosts.5.html)  However, not all services acknowledge /etc/hosts, so you might have to try a second option like dnsmasq if that does not work.  

If you want others on the LAN to access it, one way would be to install dnsmasq and add that to your list of DNS resolvers.  You can then set dnsmasq to return the server's ip address.

However, if you want to use an external address and have it available to the world, you'll have to pay for a registrar.  Just make sure that the one you choose really allows you to keep the domain yourself and that you can transfer any time.  There are a lot of shysters.

---

### Post by CharlesA on 2012-10-23
> **Lars Noodén said:**
> 
However, if you want to use an external address and have it available to the world, you'll have to pay for a registrar.  Just make sure that the one you choose really allows you to keep the domain yourself and that you can transfer any time.  There are a lot of shysters.

+1. I used domain.com for my domains, but I know there are a bunch of good ones out there (and probably an equal number of bad ones too).

---

### Post by anonymouschief on 2012-10-23
Install and run Bind DNS. That will allow you to set that domain as a local domain. You could then configure name servers for your domain.

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[https://help.ubuntu.com/12.04/serverguide/dns-installation.html](https://help.ubuntu.com/12.04/serverguide/dns-installation.html)
[https://help.ubuntu.com/12.04/serverguide/dns-configuration.html](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html)

---

### Post by CharlesA on 2012-10-23
You don't need BIND to run a "domain" on a local LAN. dnsmasq or editing your hosts file is plenty.

---

### Post by anonymouschief on 2012-10-23
> **CharlesA said:**
> You don't need BIND to run a "domain" on a local LAN. dnsmasq or editing your hosts file is plenty.

Good to know. I will check out DNSMasq.

---

### Post by CharlesA on 2012-10-23
I've got a test machine set up to resolve charlesa.net to 127.0.0.1, so I can test changes to my website on that box before uploading them to the production site.

Hopefully that answers your question. ;)

---

### Post by donniezazen on 2012-10-23
I registered a mydomain.dyndns.org for free on dyn.com and am using ddclient for locating my server.

---

