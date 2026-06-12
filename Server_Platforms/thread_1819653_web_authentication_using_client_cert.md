---
title: "web authentication using client cert"
date: 2011-08-06
forum: Server Platforms
---

### Post by rwslippey on 2011-08-06
Hello again,

Got an idea here and I'm not sure how to implament it, hoping someone has an idea.  This may not be the greatest place for this question so if I'm in the wrong place please let me know.

I am running a ubuntu server and want to host a web application (php/mysql based) however I dont want to use usernames and passwords for authentication. I'd like to use a client certificate. The military uses similar technology using the CAC card to provide the certificate for authentication.


not sure if this would be done using the apache modules or if php would be a better place to play with this


Thanks

Rob

---

### Post by SeijiSensei on 2011-08-06
You'd need to do some serious study of how [public-key systems]("http://en.wikipedia.org/wiki/Public-key_cryptography") work before you could begin to do this.  PHP alone isn't able to handle this.  You'd need to create a Certificate Authority, sign the certs, distribute them to authorized users, help them install them into their browsers, etc., etc.

As an alternative, might I suggest using cookies with long lifetimes?  You'd still need to let authorized users connect once in order to get the cookie initially, but once they have it, it's easy to check in [PHP]("http://php.net/manual/en/features.cookies.php") to see if it exists on their computer when they connect to the page.  You just want to make sure that the item in the cookie that authorizes a connection is hard to guess.  Something like an SHA1 hash is a good option.

You could set up something where you invite authorized users to visit a particular URL which installs the cookie into their browser, then takes them to the actual website.

---

### Post by rwslippey on 2011-08-06
Thanks for the reply, I hadn't thought of that angle. I'm also implamenting other security options into this. Its not really to make it easy for users to log in, just to add a layer of security to the site. Their are only about 3 or 4 systems that will ever connect so distributing certificates, or setting up cookies would be easy. 

I'm curious what you think of the this. 

[http://www.impetus.us/~rjmooney/projects/misc/clientcertauth.html](http://www.impetus.us/~rjmooney/projects/misc/clientcertauth.html)

---

### Post by SeijiSensei on 2011-08-07
> **rwslippey said:**
> Thanks for the reply, I hadn't thought of that angle. I'm also implamenting other security options into this. Its not really to make it easy for users to log in, just to add a layer of security to the site. Their are only about 3 or 4 systems that will ever connect so distributing certificates, or setting up cookies would be easy. 

I'm curious what you think of the this. 

[http://www.impetus.us/~rjmooney/projects/misc/clientcertauth.html](http://www.impetus.us/~rjmooney/projects/misc/clientcertauth.html)

Yes, that approach works if you make sure the protected pages are only available with SSL.  Notice this block of code:

```

<VirtualHost _default_:443>
...
<Location /cert>
   SSLRequireSSL
   SSLVerifyClient require
   SSLVerifyDepth 10
</Location>
...
</VirtualHost>

```

That requires the client to negotiate an SSL connection using the certificate you have created in order to access files in the /cert location.  You need to ensure that that location is not also visible via ordinary HTTP to enforce this policy.

---

