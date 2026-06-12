---
title: "Setting up a personal mail/calendar server"
date: 2011-01-05
forum: The Cafe
---

### Post by PurposeOfReason on 2011-01-05
With everything moving towards the cloud (and people loving this for some reason), as wells as google's growth in a direction I'm not particulary fond of I've been considering the idea of setting up a mail/calendar server for my own use, almost like a "personal cloud". All the searching I've been doing hasn't really brought anything that talked about anything I needed and was looking for either good links or experience doing this. I'd want to be using netBSD for this.

Another question would be, using android, is it possible to sync with non-google (see personal like I'd be setting up) calander/mail clients?

---

### Post by cariboo on 2011-01-05
You'd better check with your isp, most home internet access contracts don't allow servers.

What I did, because I just don't want to go to the hassle of setting up an mail server was to buy my own domain name, and use Google Apps for email, calendar and more. The service is free for up to 50 email addresses. It took less than an hour to set everything up.

---

### Post by PurposeOfReason on 2011-01-05
Would you happen to know if using the applications still call home to google or if they are able to stand apart?

---

### Post by HermanAB on 2011-01-05
[http://citadel.org](http://citadel.org)

It takes about 20 minutes to install and it does everything.  You can forward your outgoing mail to your ISP mail server and fetch mail from Google or wherever.  It is an all-in-one solution and Just Works (TM).

---

### Post by PurposeOfReason on 2011-01-06
> **HermanAB said:**
> [http://citadel.org](http://citadel.org)

It takes about 20 minutes to install and it does everything.  You can forward your outgoing mail to your ISP mail server and fetch mail from Google or wherever.  It is an all-in-one solution and Just Works (TM).
Hmm, I do like that, except that it seems to have too much overhead and also provides the client end to it all. My ideal situation is that I supply the frontends when I see fit (EX: using mutt/calcurse through ssh, loading the info into X client, etc.).


Been looking for a good hosting company for this and a seedbox if anyone knows of any.

---

### Post by HermanAB on 2011-01-06
As for Citadel having too much overhead...

Here is Citadel running on an Eee PC 701 netbook:
[http://www.aeronetworks.ca/howtos/eeepc-mdv-howto.html](http://www.aeronetworks.ca/howtos/eeepc-mdv-howto.html)
(scroll down to the bottom).
;)

---

### Post by ssam on 2011-01-06
this is something i am interested in doing, but have not got around to. i think you should look for a caldav server, egm DAViCal.

if your ISP limits you you could get a VPS (slicehost/linode/etc).

---

