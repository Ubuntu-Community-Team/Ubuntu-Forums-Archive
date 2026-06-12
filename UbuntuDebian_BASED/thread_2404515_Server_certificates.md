---
title: "Server certificates"
date: 2018-10-24
forum: Ubuntu/Debian BASED
---

### Post by kyomai3006 on 2018-10-24
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I successfully configured an OwnCloud server at home based on a Ubuntu OS. I configured it so that one needs to use https to access the server. It works as described in numerous forum posts using a self-assigned server certificate. Anyway, I would like to redirect a sub-domain of my web provider to that OwnCloud server and I ran into the server certificate problem. What certificate shall I use? A certificate of my web provider or the self-assigned certificate of my Ubuntu server at home?[/COLOR]

[COLOR=#000000]To be honest I don't quite understand the concept of those certificates [/COLOR]:confused:[COLOR=#000000] I read something here and there on the web but I still don't understand how to make a browser accept a certificate of a server that I set up?[/COLOR]

[COLOR=#000000]Ubudubu[/COLOR]

---

### Post by SeijiSensei on 2018-10-25
Certificates are assigned to hostnames and domain names.  If you access [www.example.com](www.example.com) as web.example.com, and the cert is for the first of these names, the browser will throw an error.

I don't know if you can create a "wildcard" self-signed certificate, one that matches *.example.com.  That might help but only if the hosted domain matches the server's domain. 

You'd need to give us more information about "redirecting a sub-domain of my web provider."  Is the remote site called something like mysite.providersdomain.com?  If so, I don't think there's much you can do to fix that unless you can obtain a copy of the provider's certificate.  And even then, it would need to be a wildcard cert.  And you'd need the private key for the cert as well.

---

