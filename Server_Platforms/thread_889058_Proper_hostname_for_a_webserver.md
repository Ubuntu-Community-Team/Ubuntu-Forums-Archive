---
title: "Proper hostname for a webserver"
date: 2008-08-13
forum: Server Platforms
---

### Post by 2smooth on 2008-08-13
What's the proper hostname for a _single _webserver connected to the outside world?

example.com
name.example.com

And does your choice matter if you use the dns of your're domain name provider?

And does your choice matter for internal services?

---

### Post by kustomjs on 2008-08-13
I put mine as server1 but I am thinking about switching the hostname also so I need to figure that one out 2.

---

### Post by MJN on 2008-08-13
You may need to rephrase your question as it's not all that clear.

name.example.com is what's known as a *fully qualified* domain name i.e. it contains a hostname portion (name) and domain portion (example.com) - together they uniquely identify a particular host within a particular domain.

Can you elaborate on the context of your question? For example, is it in relation to a particular Apache configuration setting?

Mathew

---

### Post by jesusdemontreal on 2008-08-13
In my case, I use Dynamic DNS through a router, so the hostname of my server is totally irrelevant. Dynamic DNS has the IP of my ISP's connection and my router passes request to the internal IP of my server. The domain name seen on the internet (i.e. when browsing to my website) is assigned by DDNS. If you own your own domain name but you own only one IP you have i would consider assigning www as it's DNS name. But the hostname inside the server itself wont interfer with the outside world for the queries for your hostname are treated by the DNS server, which in turn points to your ISP's IP and not to the server's internal hostname.

---

### Post by MJN on 2008-08-14
> **jesusdemontreal said:**
> But the hostname inside the server itself wont interfer with the outside world for the queries for your hostname are treated by the DNS server, which in turn points to your ISP's IP and not to the server's internal hostname.

If you host more than one site at the same IP (name-based virtual hosting) then it does then become relevent as the web server needs to match each site to the name requested by the client (in HOST header).

Mathew

---

### Post by 2smooth on 2008-08-14
My question has three parts

-Does it matter whether you call you're machine, a LAMP server,

name.example.com or example.com?

-Is you're hostname in general really irrelevant if you're using the dns of you're domainname provider? 

-Is you're hostname really irrelevant if you're using your machine for virtual hosting on the same ip and are using the dns of you're domainname provider ? 



> **MJN said:**
> You may need to rephrase your question as it's not all that clear.

Mathew

---

### Post by MJN on 2008-08-14
I hope these responses don't sound too awkward - I am genuinely keen to help it's just that there are still some ambiguities to what you're asking. I'm sure it's clear in your head, it's just we need to be all understanding it the same if we are to provide a meaningful answer! I'll give it a shot anyway...
 
> **2smooth said:**
> Does it matter whether you call you're machine, a LAMP server,
 
name.example.com or example.com?
 
If when you say 'call your machine' you mean the name you assign it in /etc/hostname then no, it doesn't matter what you've called it _as long as any applications that rely on it behave as you wish them to_. If, however, you are talking about telling Apache its 'name' using the the Servername then yes, it could be significant because it uses this identity when serving up the correct virtual host to a connecting client.
 
> -Is you're hostname in general really irrelevant if you're using the dns of you're domainname provider?
 
Irrelevant insofar that their DNS will at least convert the name that the outside world uses into your unique IP address. However internally the hostname can often become significant e.g. in Apache as already discussed, in Postfix as a means of knowing what is local and not (these can be overridden by more specific directives if required), and no doubt by other applications in different ways.
 
> -Is you're hostname really irrelevant if you're using your machine for virtual hosting on the same ip and are using the dns of you're domainname provider ?
 
It depends again on what you mean by hostname - if it is the one in /etc/hostname then it is irrelevent as long as you have advised Apache what its sites are called using the Servername directive.
 
If it helps, my server name is 'rugrat' with a domain of 'newtonnet.co.uk' however these names play no role in Apache it is called 'www.newtonnet.co.uk', 'secure.newtonnet.co.uk', 'mail.newtonnet.co.uk', 'zm.newtonnet.co.uk' etc for its virtual host names and for Postfix it considers itself to be called 'secure.newtonnet.co.uk'.
 
Does that help? Or have I just confused the issue further?
 
Mathew
 
P.S. Just picking up on your example, as perhaps that's where the significance lies. 'example.com' is not technically a hostname as their is no real domain portion - unless you happened to be the owner of the .com domain. A hostname should either be a single component/name or, if combined with a domain, be fully qualified and contain both the name of the host and its domain. It all depends on the context of where you're using the term - 'hostname' is one of those terms that means different things in different contexts to different people.

---

### Post by 2smooth on 2008-08-14
> **MJN said:**
> I hope these responses don't sound too awkward 
If when you say 'call your machine' you mean the name you assign it in /etc/hostname then no, it doesn't matter what you've 

Yes with hostname i mean /etc/hostname

> If, however, you are talking about telling Apache its 'name' using the the Servername then yes, it could be significant because it uses this identity when serving up the correct virtual host to a connecting client.

Can you please give an example of this

Btw thanks for your lengthy answers.

---

### Post by MJN on 2008-08-14
I'm not sure if we're heading towards finding you an answer as I'm still not entirely sure exactly what the question really is!

> Can you please give an example of thisSure...

In the code below we have the code which enables Apache to host multiple sites on the same machine (and IP address). Each site needs uniquely identifying otherwise when a client connects Apache wouldn't know which site to serve - this is done through the Servername directive on the server and client sending the name as a HOST header when it connects.

```
<virtualhost *:80>
Servername www.example.com
Serveralias  example.com
Documentroot /var/www/default/
.
.
</virtualhost>

<virtualhost *:80>
Servername www.widgets.com
Documentroot /var/www/widgetsite/
.
.
</virtualhost>

<virtualhost *:80>
Servername www.gizmos.com
Documentroot /var/www/gizmosite/
.
.
</virtualhost>
```If you hadn't specified the Servername's then Apache would only be able to identify itself by its own hostname (or, more specifically, by the IP address that that hostname translates to).

Does that help? I can't help but feel we've (I've?) gone off at a right tangent here... but there's too much ambiguity to be any more specific.

If anyone else wants to chip in if they have a better understanding of what the question really is then please do as I feel I'm not really providing that much help here!

Mathew

---

### Post by 2smooth on 2008-08-14
> **MJN said:**
> 
If anyone else wants to chip in if they have a better understanding of what the question really is then please do as I feel I'm not really providing that much help here!

Mathew

You make me laugh. 
Ok.

On one side i have three registerd domain name's let's say banana.com, cherry.com and kiwi.com

I want banana.com to be the main name of the webserver.
And cherry.com and kiwi.com to be virtual hosts.

On the other side i have a machine with lets say ip 64.202.179.170

Thinking about how to set this all up, i start to wonder how relevant the /etc/hostname is in this whole setup?

For example should the domain name as configured on the server be the same as banana.com?

Should the FQDN as configured on the server be the same as somename.banana.com?

Are these names tight or loosely related?

If in the control panel of my domain name provider, i configure
kiwi.com and alias [www.kiwi.com](www.kiwi.com) to point to the same machine, is it still necessary to create a [www.kiwi.com](www.kiwi.com) server alias for kiwi.ocm in apache conf?

This sort of questions are coming on my mind.

---

### Post by MJN on 2008-08-14
Thanks for that 2smooth!

> **2smooth said:**
> Thinking about how to set this all up, i start to wonder how relevant the /etc/hostname is in this whole setup?

It's not relevent in the scenario you describe as you have told Apache what it is called through the Servername directives hence you can call your 'real' hostname (/etc/hostname) whatever you like.

> If in the control panel of my domain name provider, i configure
kiwi.com and alias [www.kiwi.com]("http://www.kiwi.com") to point to the same machine, is it still necessary to create a [www.kiwi.com]("http://www.kiwi.com") server alias for kiwi.ocm in apache conf?Yes, absolutely. Clients that use the URL [www.kiwi.com]("http://www.kiwi.com") will be passing that name to Apache and so it has to know that [www.kiwi.com]("http://www.kiwi.com") is actually an alias for kiwi.com and hence should be served with the same content. If you didn't tell Apache then it would just serve up the content from the default server, that being the first one in its list - of course if you've only got the one site running then this is not a problem.

Mathew

---

