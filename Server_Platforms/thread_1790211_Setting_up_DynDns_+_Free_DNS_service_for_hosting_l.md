---
title: "Setting up DynDns + Free DNS service for hosting locally"
date: 2011-06-24
forum: Server Platforms
---

### Post by renegadeandy on 2011-06-24
Hey guys!

This is the deal. I have an Ubuntu Server, a dyndns account and an account with [http://freedns.afraid.org/](http://freedns.afraid.org/).

My DynDns stuff is all working just great - novo.dyndns.tv is the address.

Now I need a domain which I have already bought, to be linked to that machine at novo.dyndns.tv

I signed up with freedns.afraid.org and now I am a bit confused at what records to add where.

I added a domain - jenniarmstrong.com then setup a webforward as follows:

redirect from [http://jenniarmstrong.com](http://jenniarmstrong.com) to [http://novo.dyndns.tv](http://novo.dyndns.tv) 
and redirect from [http://www.jenniarmstrong.com](http://www.jenniarmstrong.com) to [http://novo.dyndns.tv](http://novo.dyndns.tv) , however if you go and visit:

[http://www.jenniarmstrong.com](http://www.jenniarmstrong.com) - you will see my problem! It takes you back to freedns.afraid.orgs server and says there is not a webforward setup for [www.jenniarmstrong.com](www.jenniarmstrong.com) 

This tells us that the nameservers are all setup fine - and its something in my freedns config which is failing. Please help!

---

### Post by Bachstelze on 2011-06-24
What you need in FreeDNS is not a Web redirection but a CNAME record pointing to novo.dyndns.tv. I can't tell you exactly how to do that, though, since I don't use it.

---

### Post by renegadeandy on 2011-06-24
Hmm ok , I tried adding a cname from:

subdomain www
domain jenniarmstrong.com
destination novo.dyndns.tv

However it still isnt working - notice when you go to [www.jenniarmstrong.com](www.jenniarmstrong.com) the url on your browser in afraid.org says no web forward found?

---

### Post by Bachstelze on 2011-06-24
Hmm, I guess you need to wait for someone more familiar with how FreeDNS works (or ask FreeDNS directly) becausehttp://jenniarmstrong.com works fine, so if you have the same Web redirect on both, www. should work too...

---

### Post by renegadeandy on 2011-06-24
Weird, in the end i needed 2 web forwarding entries. Despite CName being able to do the same job. I think the afraid.org gui and design really does leave something to be desired, its not clear why this now works!

---

