---
title: "gpg proxy"
date: 2011-01-31
forum: Security
---

### Post by mune on 2011-01-31
I got an idea, it is so simple that it would be amazing if someone have already found a solution.

My idea is this
A proxy P runs on port 8181 (or whatever) and it only forward the connections to the apache on port 80 only if the user connecting has signed a random script from the proxy. Did that, the proxy is transparent for that IP (for the next -say- 6 hours).

The Apache http server only accepts connection coming from localhost (the proxy P, so if the client tries to go directly to the server all it gets is an error).

It can work with a wiki, wordpress, ..., whatever would be running on the http server.

I googled a lot without finding anything, which is strange as it seems pretty easy. If it wasn't there either I'm a genius or I'm dumb and I'm missing something.

Anybody can give a hint?

Thanks

Fede

---

### Post by anomie on 2011-02-01
If your goal is to authenticate a user (or users) by way of cryptographic keys, try searching the 'net for "ssl client authentication".

---

### Post by mune on 2011-02-02
> **anomie said:**
> If your goal is to authenticate a user (or users) by way of cryptographic keys, try searching the 'net for "ssl client authentication".

Thank for the reply.

But, for what I understood SSL doesn't work with the OpenPGP (GnuPG) standard. Is it the same thing? Can the SSL framework handle a self-created key created with gpg exported in key-server (eventually signed by a well known third party)?

---

### Post by anomie on 2011-02-02
I'm not sure. But it may be that I am not understanding your idea: 

If your goal is client authentication (i.e. the client is going to sign a random string from the server), how will public key distribution help anyway? You need to have a secure way to distribute secret keys (i.e. private keys) to the clients, right?

---

### Post by mune on 2011-02-03
> **anomie said:**
> I'm not sure. But it may be that I am not understanding your idea: 

If your goal is client authentication (i.e. the client is going to sign a random string from the server), how will public key distribution help anyway? You need to have a secure way to distribute secret keys (i.e. private keys) to the clients, right?

OK, my idea is this

```
+-------+     +------+
|   P   |<--->|   U  |
+-------+     +------+
 ^
 |
\/
+-------+
|   WA  |
+-------+
```
P is the proxy (say on port 8383)
WA is a web application (say a wiki on port 80)
P and WA are on the same machine running apache and whose name is [www.example.com](www.example.com)

The user (U) points his browser to [www.example.org:8383](www.example.org:8383) and gets a mask asking for a e-mail address and a field where the user crypt a random text (supplied by P) with the secret key of that email address.

If the same text crypted by P using the public key is equal to the one given from the user, the user is authorized to access WA via port 8383.

(WA accepts only localhost request, so anybody has to go thought the proxy and not directly to WA.)

(Details: P looks for the public key on a certain key server and it has to generated from more than n days.)

---

