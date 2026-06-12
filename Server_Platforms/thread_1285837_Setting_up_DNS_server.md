---
title: "Setting up DNS server"
date: 2009-10-08
forum: Server Platforms
---

### Post by rabidityfactor on 2009-10-08
I have a server machine with a static IP starting with 117.240.xx.xx. Also I have obtained a domain name cea.ac.in. I'm able to access web pages on the server by typing in the static ip in the browser.

Now how do I map [www.cea.ac.in](www.cea.ac.in) to this static IP?

Should I setup a DNS thing? How do i do that?

---

### Post by Bachstelze on 2009-10-08
> **rabidityfactor said:**
> 
Should I setup a DNS thing? How do i do that?

Setting up a DNS server yourself is quite a cumbersome process when you're not used to it. If you don't have a good reason to host your own DNS server, your domain name provider should provide one for you.

---

### Post by rabidityfactor on 2009-10-08
Thanks for the very quick reply.

I've checkd out this thread.

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

and did not find it that difficult, but did not give it try though. Is it going to be hard?

---

### Post by i.r.id10t on 2009-10-08
You need 2 ips to do your own total DNS, as well as "glue records" from your registrar.  Godaddy makes this easy, but you'll need 2 IPs - ideally on 2 different boxes, but 2 on one box will work.

---

### Post by Oceanwatcher on 2009-10-08
> **rabidityfactor said:**
> I have a server machine with a static IP starting with 117.240.xx.xx. Also I have obtained a domain name cea.ac.in. I'm able to access web pages on the server by typing in the static ip in the browser.

Now how do I map [www.cea.ac.in](www.cea.ac.in) to this static IP?

So let me see if I understand you correct:

You have a server connected directly to the internet. This server has a static IP address and your friends can access the webpages on the server through this IP address?

The only thing you would need to do to get a domain to point to the server is to use a registrar service with a redirect. This does not cost a lot and some even give you this service for free as long as you pay the regular, yearly fee for the domain.

---

### Post by rabidityfactor on 2009-10-08
OK I understand.. Thanks for the quick replies everyone.

---

### Post by caue.rego on 2009-10-29
Ok, I have the exact same issue, but I got a question that was not asked...

So 2 different static IPs would be needed, ok. I assume this is a safety measure convention that ends up being a requirement by the registrar (in my case, [http://registro.br](http://registro.br) ). They do ask at least 2 DNS servers.

Then, when specifying the IP address to the DNS host on the registrar, it also asks for a domain name (like let's say ns.domain.com.br ) I have no idea why that's a requirement, but how could I setup my own "ns." thing if that's exactly what I needed to do at first!?

Is there another yet bigger nameserver other than the [13 root servers]("http://en.wikipedia.org/wiki/Root_nameserver")? Would I need to register this IP there somehow??

Plus another thing: isn't there any way to **do this with just 1 IP?**

And one last thing: [http://www.everydns.com/](http://www.everydns.com/) this seems like a great free DNS service. I'm already trying it out.

---

