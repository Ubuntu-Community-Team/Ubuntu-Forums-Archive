---
title: "citadel groupware server"
date: 2009-12-25
forum: Server Platforms
---

### Post by stlsaint on 2009-12-25
hello i have installed apache2 to use website and citadel for email server. My problem now is that at install i choose to run citadel 'alongside' apache webserver. Now i cant access citadel to configure it. Im running it on a vps using local ip on server...i can use 192,168.1.111 to see website but when i try port for citadel it just contiues to load and load. I was told about citadel here thus im posting here. im thinking i have to re-install citadel and choose to use internal http services but not sure and thats alot of work... :(

---

### Post by artcancro on 2009-12-25
There are a couple of different ways of getting WebCit (Citadel's web front end) to run alongside Apache.  The easiest way is to just allow it to run on a different port number (which is how it sets itself up by default anyway).  If that's not going to work for you for some reason, the virtualhost/proxy setup does work quite well.

There are some howto's here:
[http://www.citadel.org/doku.php/faq:installation:apacheproxy](http://www.citadel.org/doku.php/faq:installation:apacheproxy)

You can also ask about this topic on UNCENSORED! BBS in the Citadel Support room, where the developers and other users hang out.

Congratulations on getting started with Citadel; it's a wonderful package and does a lot of things.

---

