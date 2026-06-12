---
title: "Hosting one website on Ubuntu server and an IIS server?"
date: 2013-10-04
forum: Server Platforms
---

### Post by Joey_Racca on 2013-10-04
Greetings my leet tech friends,

I am not sure if i am posting this in the correct forums, but i am desperate for help. I have searched all over the net, and cant seem to find the answer.

I have a Ubuntu 12 running an apache web server with a domain example [www.site2.com]("http://www.site2.com")

I also have an Windows 2012 server running IIS with a domain example [www.site1.com]("http://www.site1.com")

I would like to have website [www.site1.com]("http://www.site1.com") point to my ubuntu server, and links from the website on ubuntu point to asp.net web apps hosted on my IIS7 server, and not use the domain [www.site2.com]("http://www.site2.com")

There both seperate machines with separate IP address.. (edit) both are on the same network. both have external ip's and private ip's

Not sure if i explained this well enough, but any help would be greatly appriciated.

---

### Post by whitesmith on 2013-10-04
Hi and welcome! You would have much better luck if this were in Networking & Wireless. A moderator can move it for you.

---

### Post by btindie on 2013-10-04
You can configure Apache/nginx to act as a reverse proxy for the requests you want served by IIS7.

So a request would look like the following

client -> Ubuntu -> IIS7 -> Ubuntu -> client

either that or you can do it as a sub-domain - www2.site1.com

---

### Post by SeijiSensei on 2013-10-04
Because you can associate [Proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") directives with specific virtual hosts, you can set up the box to distribute files for [www.site1.com](www.site1.com) from its local DocumentRoot, while sending requests for [www.site2.com](www.site2.com) back to the IIS box using the proxy features.  The Linux box would require two network interfaces, with one pointing to the Internet, and the other pointing to a local network on which the IIS server resides.

---

### Post by btindie on 2013-10-05
> **SeijiSensei said:**
> The Linux box would require two network interfaces, with one pointing to the Internet, and the other pointing to a local network on which the IIS server resides.
No it wouldn't. If they're both behind the same NAT device it would just use the local private IP to connect to the IIS server.

---

### Post by mörgæs on 2013-10-05
> **whitesmith said:**
> Hi and welcome! You would have much better luck if this were in Networking & Wireless. A moderator can move it for you.

Either that or Server Platforms. Trying the latter for now.

---

### Post by SeijiSensei on 2013-10-05
I was assuming the Ubuntu server had an Internet-facing interface.

---

