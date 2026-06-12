---
title: "[SOLVED] Setup Jabber Server"
date: 2008-07-13
forum: Server Platforms
---

### Post by Dr Small on 2008-07-13
I am looking around for a good guide on how to setup a Jabber Server, something that I can use to connect to in Pidgin, for example. No Java stuff.

The guide at the Ubuntu Wiki did not work for 'jabber', so I was wondering if there was any other guides for setting up different jabber servers.

Dr Small

---

### Post by Kango_V on 2008-07-13
It's a shame you say no Java, as that counts out OpenFire.  This is awesome.  We got ours up and running in a few minutes!

Works with every client that we tried.  Completely open source too!

---

### Post by Dr Small on 2008-07-13
> **Kango_V said:**
> It's a shame you say no Java, as that counts out OpenFire.  This is awesome.  We got ours up and running in a few minutes!

Works with every client that we tried.  Completely open source too!
Well, I figured the java was for web-based usage. Maybe I am incorrect? Does the java version work with Pidgin and such?

Dr Small

---

### Post by Dr Small on 2008-07-13
Ok. So I got Openfire setup, and can connect in Pidgin, but it will not accept the self-signed certificate. Any way I can fix this? I am not getting my certs signed.

Dr Small

---

### Post by Dr Small on 2008-07-13
I apologize for the triple post, but I wanted to say that everything is working now and openfire seems to be working the way it should. Thanks for your suggestion, Kango_V.

**[SOLVED]**

---

### Post by gfca on 2008-07-15
> **Dr Small said:**
> I apologize for the triple post, but I wanted to say that everything is working now and openfire seems to be working the way it should. Thanks for your suggestion, Kango_V.

**[SOLVED]**

Hi,
can u please tell how did you solve the "self-signed certificate" problem?

Thanks

---

### Post by Dr Small on 2008-07-15
I just kept removing the certificates from Pidgin, and then I modified the account and ticked the little checkbox to have it create the account. I didn't have any more problems after that.

Dr Small

---

