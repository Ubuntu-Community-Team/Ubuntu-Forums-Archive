---
title: "LTSP and thin client setup"
date: 2010-01-31
forum: Server Platforms
---

### Post by Centurion030 on 2010-01-31
Hello,

New to ubuntu but not to Linux, Debian Lenny & Etch and esx. 

We are going to be setting up a thin client install for a distance learning center. While the Major has done this, I have a few questions.

First, our server is going to be a dual-Xeon Dell Precision 670 with 6 gigs of memory and ~640GBs of hard drive storage. I believe, will have to look at them again, the thin clients are Dell GX 270s.

My main question is that even if this is going to be a 64-bit server, I need not worry about the clients being 32-bit? 

That's it for now. We are looking at 20 thin clients being tied to the server.

James

---

### Post by namdung on 2010-02-03
Yes you should be able to create 32 bit clients.

The server should be good enough for 20 clients. Tell us how it goes.

---

### Post by Centurion030 on 2010-02-14
Will keep everyone informed. 

We'll only have 12 clients-that is the amount of desks we have. The HD's will be 1TB's on the server. Switch will be 10/100/1000 Dell PowerConnect.

James

---

### Post by _UsUrPeR_ on 2010-02-17
Bear in mind that with an ltsap-localapps installation, you can cut a lot of network and server overhead from the equation. Ltsp-localapps allows you to run programs installed on the ltsp image instead of using the server's resources. It is recommended to have a gig of RAM per client when running localapps.

For more information about localapps, you can check here: [https://wiki.ubuntu.com/LTSPLocalAppSetup](https://wiki.ubuntu.com/LTSPLocalAppSetup)

For even more information, check out the ltsp irc channel:
/server irc.freenode.com
/join #ltsp

In order to create a 32-bit client image, make sure that you are running "ltsp-build-client --arch i386". If you have installed the LTSP environment from the Ubuntu Alternate Installation CD, you will need to re-build the miage after installation, because the client LTSP image architecture defaults to whatever the server architecture is. I.E. if installing 9.10 i386 Alternative with LTSP support, it will automatically build an i386 ltsp image.

---

