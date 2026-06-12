---
title: "Apache : selective authentication based on user-agent"
date: 2006-11-24
forum: Server Platforms
---

### Post by piers on 2006-11-24
Is it possible to only run certain parts of an apche configuration based on the user-agent?

For example, I want to run apache to host a website which has webdav enabled, this works ok but whenever I visit the page using a web browser I am prompted for a password. How can I get it to only authenticate when the user agent is a DAV client?

Does setenvif or browsermatch come into this? I'm quite stuck ](*,) 

Thanks in advance!

---

### Post by MJN on 2006-11-24
One solution, although there may exist something more specific/elegant one, would be the use the mod_rewrite module to rewrite the URL depending on the client user-agent. Specifically, whilst everyone comes in on the same page they can be redirected to different client-specific pages for different clients.
 
Check out [http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewritecond](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewritecond) where you will also find a specific example for matching certain client user-agents.
 
Can you see where I'm coming from?
 
Mathew

---

### Post by piers on 2006-11-27
Thanks for your help, i'll look into this.

Maybe the answer is to only allow DAV on a secure connection? So that any requests on port 443 will be handled by one config, i.e WebDAV - and everything else will just use the standard conf with n authentication?

Does this make sense? How could I go about doing this?

Piers

---

