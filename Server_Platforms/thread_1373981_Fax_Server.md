---
title: "Fax Server"
date: 2010-01-06
forum: Server Platforms
---

### Post by Vegan on 2010-01-06
I have accumulated a bunch of fax modems and noticed some were garbage so they have been shredded. Anyway some work and I was inquiring about adding yet another service to my server.

Why not a fax daemon. Then share it via SAMBA or other package so that everyone can send/read faxes. Feasible?

---

### Post by BkkBonanza on 2010-01-06
Check this out,

[http://vigna.dsi.unimi.it/fax4CUPS/](http://vigna.dsi.unimi.it/fax4CUPS/)

I haven't used it.

---

### Post by Vegan on 2010-01-10
I am using SAMBA at present so I was speculating if anyone had gone that route yet?

---

### Post by BkkBonanza on 2010-01-10
Don't see why it wouldn't work with Samba. Samba runs on top of CUPS. So if you have a CUPS printer then Samba can share it to your network and anyone can use.

---

### Post by HermanAB on 2010-01-10
Howdy,

Start by installing efax and get it to work on its own, before trying to integrate it with CUPS.

---

### Post by Vegan on 2010-01-10
I noticed something in a Debian package, been unwell but I am slowly getting back to it.

Found it with Google a few days ago but forgot to bookmark it.

---

### Post by i.r.id10t on 2010-01-11
Did one with samba... created a fake printer (see the fake pdf printer instructions), print to it, get an email with a link to a form that would get cover sheet info and where to send it.. submit form, outgoing fax put in que and sent once line was available.  Incoming faxes were sent to a single folder and that was shared via samba.

Ran it on a P-200 w/ 64mb ram, serviced 25 users for 4 years, 50k faxes per year in and out.  Issues were with phone lines being busy (they only had 3 lines), and they kept forgetting to turn the server back on after extended power outages.

---

### Post by Vegan on 2010-01-11
Anyone try HylaFAx as that is another open source one I noticed.

---

### Post by koenn on 2010-01-11
hylafax is somewhat the reference in open source fax servers, it's been around forever. 

It'll accept faxes (to send) in a number of ways (from a mail client, from a "printer" driver, ...) and IIRC it can be combined with Samba, but you'll have to look that up (or wait for someone here to confirm). 

[http://www.hylafax.org/content/Documentation](http://www.hylafax.org/content/Documentation)

---

### Post by Maheriano on 2010-01-11
So this will allow you to fax someone a document that's on your computer? And receive one to your printer? Which number do they fax to?

---

### Post by koenn on 2010-01-11
yes, you can fax documents straight from your computer. 
You can receive faxes on a printer, but also  in a shared folder on your network (or on your computer if you run the fax server there); most fax servers can also convert the received fax to a mail attachment and mail it to a given address. Advanced configuration will also allow you to have the fax server select a delivery method / destination based on characteristics of the received fax or of the fax session itself (eg the sender's caller ID)

You need a modem (or a "fax board") connected to a phone line - that's the number they'll fax to/from.

wikipedia will tell you all about it.

---

