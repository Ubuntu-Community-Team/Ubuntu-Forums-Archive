---
title: "Apache Basic Auth + ssl not encrypting"
date: 2008-07-21
forum: Security
---

### Post by [pl]ice on 2008-07-21
Hi,
  I'm about to setup basic auth for apache,to see folders etc.
 What i read on the forums, is that apache + ssl + basic auth does not encrypt the user/passwd , the encryption only takes place AFTER the user have logged in. I've looked through apache help etc, and they state that its not the case.
  Yet, ppl sucesfully sniffed the user/pass on such a config. Did anyone came across this one? Or can pls someone can test this out (i can't atm, no PC...)
  What are other ways to instead of using basic auth? I'm not familiar with PHP, but then i guess PHP will be over ssl. I'd prefer standard apache access settings.
 Thank You

 Polish

---

### Post by cdenley on 2008-07-21
I just captured my traffic while authenticating, and it looks fine to me. Maybe what you are referring to is that when you redirect the users if they're not using SSL, they will be authenticated before being redirected.

In other words, if they go to [http://mydomain.com](http://mydomain.com), it will authenticate without SSL, even if you configured mod_rewrite to redirect them. As long as they go to [https://mydomain.com](https://mydomain.com), it should be encrypted.

---

### Post by Titan8990 on 2008-07-21
I believe your best bet would be to set up a packet sniffer and check it out for yourself. You can put the packet sniffer on your local machine or somewhere on the network with ARP poisoning.

---

### Post by [pl]ice on 2008-07-21
> **cdenley said:**
> I just captured my traffic while authenticating, and it looks fine to me. Maybe what you are referring to is that when you redirect the users if they're not using SSL, they will be authenticated before being redirected.

In other words, if they go to [http://mydomain.com](http://mydomain.com), it will authenticate without SSL, even if you configured mod_rewrite to redirect them. As long as they go to [https://mydomain.com](https://mydomain.com), it should be encrypted.

Yeh, that what i was suspecting,with the redirection. In that case, how do i point continously to https in the first place? Should it look like that:
   visit http redirect to https, then login. How this can be achieved? through mod_redirect?

thanks guys

---

### Post by cdenley on 2008-07-22
> **'[pl]ice said:**
> Yeh, that what i was suspecting,with the redirection. In that case, how do i point continously to https in the first place? Should it look like that:
   visit http redirect to https, then login. How this can be achieved? through mod_redirect?

thanks guys

I suppose you can configure your default vhost to use an empty directory as root, then have it redirect without requiring authentication. Only configure your SSL vhost to require authentication.

---

