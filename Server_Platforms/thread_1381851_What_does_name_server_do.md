---
title: "What does name server do?"
date: 2010-01-15
forum: Server Platforms
---

### Post by programming.name on 2010-01-15
Hi.
I'm thinking of building a web server on ubuntu 9.10 server edtion for a learning purpose. 
I recently purchased a domain from a web company and the company's website has a page where I can change Name Servers(Master and Secondary Name Serevers with the following syntax: ns.aaaaa.com, ns1.aaaaa.com). What can I do with that? Could you please explain why the company provides the name server? Becuase As I checked with my router setting, it already has a DNS address set from my ISP. How is the actual difference between them?

---

### Post by volkswagner on 2010-01-15
Your web company provides DNS servers where you can enter your ip address.  This allows the world to enter your domain name and the DNS converts it to your ip, there for directing the request to your server.

I started a [thread]("http://ubuntuforums.org/showthread.php?t=1369962") that may have some helpful info.

Your router has dns so your internal lan requests can have the requested domain name converted to an ip which will direct the browser to the correct location.

Hope this helps

---

