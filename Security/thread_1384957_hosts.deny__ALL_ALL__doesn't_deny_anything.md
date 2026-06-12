---
title: "hosts.deny:  ALL: ALL  doesn't deny anything"
date: 2010-01-19
forum: Security
---

### Post by loldrup on 2010-01-19
I was under the impression that writing:

ALL: ALL

as the only line in your /etc/hosts.deny file would render the computer inaccessible to/from any other computer in the world.
Yet I can still access any server (like eg. this forum). How come?
I have even rebooted (ya, I'm an old Windows user)

Ubuntu 9.10

---

### Post by lafayette on 2010-01-19
hosts.deny only rules the services that support tcp_wrappers. Apache, for example, is not in this category.

---

### Post by loldrup on 2010-01-19
Ok.
I want to block the browser from visiting all but a few websites - do you have an idea about how I could do that?

---

### Post by lafayette on 2010-01-19
read apache documentation regarding the directives

Deny
Allow
Order deny,allow


it's pretty simple to do it (if you're using apache, obviously). there are lot of examples, just google

---

### Post by lisati on 2010-01-19
I think we're at crossed purposes here....

Are we talking BROWSING (like reading the forums) or running a server (like you might use Apache for)???????

---

### Post by loldrup on 2010-01-19
> **lisati said:**
> I think we're at crossed purposes here....

Are we talking BROWSING (like reading the forums) or running a server (like you might use Apache for)???????

I want to block the browser. The computer is to be used to visit a select few sites only. It doesn't run a webserver.

---

### Post by HermanAB on 2010-01-19
Howdy,

Read up on squid-cache, squidguard and dansguardian.  You can also block specific sites using a short circuit to 127.0.0.1 in the /etc/hosts file.

---

### Post by Lars Noodén on 2010-01-19
> **loldrup said:**
> I want to block the browser. The computer is to be used to visit a select few sites only. It doesn't run a webserver.

Then HermanAB' suggestions of squid-cache, squidguard and dansguardian would help.  You can run them on another computer or on the same computer.  

For full effect you will have to combine them with packet filtering, often marketed as 'firewall'.   The filter then blocks any packets the restricted groups might try to send or receive externally, but allow contact on the same machine with the proxy.  The proxy, since it is running as a different account and thus not a member of the restricted group, then has full access out.  

You can make any of the restricted accounts on that computer as members of a group.  Then IPTables, linux's packet filter, can block any contact to or from external addresses.  If you use an external proxy, then obviously there would be one exception in the packet filter's rule list for the proxy, otherwise not.

---

### Post by loldrup on 2010-01-19
> **Lars Noodén said:**
> Then HermanAB' suggestions of squid-cache, squidguard and dansguardian would help.  You can run them on another computer or on the same computer.

Thank you - I will look into that.

---

### Post by bodhi.zazen on 2010-01-19
Apache does not use tcpwrappers (unless it is compiled server side to do so), so hosts.deny will not help.

In additions, tcpwrappers are a server side tool, not client side.

If you have a short list of sites , on a single computer, use /etc/hosts

127.0.0.1 site.com

If you have a large list of sites or multiple users, use a proxy, such as squid or privoxy.

---

### Post by sad1sm0 on 2011-07-31
I know this is an old thread, but I wanted to post for anyone who might stumble across this in a search. Another method that would be quite efficient is to use a service like OpenDNS to filter the web availability to your users. It's simple to configure, and has an easy web based interface. This coupled with the fact that the users have no access to this as long as you set the DNS servers on the router/gateway and not on the physical machine that you are using. In addition, OpenDNS give you a way to monitor traffic and ensure that no one is finding ways around the system.

---

