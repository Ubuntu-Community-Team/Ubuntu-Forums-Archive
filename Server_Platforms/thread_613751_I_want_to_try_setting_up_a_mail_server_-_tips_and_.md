---
title: "I want to try setting up a mail server - tips and suggestions?"
date: 2007-11-15
forum: Server Platforms
---

### Post by edmicman on 2007-11-15
My work hosts our email server inhouse, on a debian server that an outside consultant set up a looooong time ago.  I think he occasionally logs in to do maintenance, though no one really knows.  We administer and set up new email accounts via Webmin, and I think it uses sendmail as it's mail server.  Our webclient access is via squirrelmail, though we primarily use IMAP or POP clients like Thunderbird or Outlook.

A coworker and I have talked about how really, if something were to happen to this mail server, none of us really have any idea how it was set up, and the guy who originally set it up may be available less and less.  We were thinking it'd be a good exercise to build a new one from scratch, both as a learning exercise and if it went well, possibly even eventually migrating to the new setup that we fully know how to maintain.

Sooooo, I'm looking for any tips or suggestions, both in general, and things like what mail software and webclient software to use.  I've got some experience setting up Ubuntu servers, mostly just as internal development setups, but I like how it works and things are usually well documented.  I could set things up like how we already have them....I hate Squirrelmail, though, but it works.  But I was also looking at some of the "commercial" open source offerings, too, like Scalix and Zimbra.

I think I like the looks of Scalix better, but I'm turned off by the 25 "Premium" user limit, and would be hard pressed to convince the powers that be for a pay solution to something that was free before for unlimited users.  Zimbra looks like it offers quite a lot of features, though, too.  What else is out there?  Is Sendmail the old standby?  Is there a better mail server software?  

Thanks for any tips!

---

### Post by Fire_Chief on 2007-11-15
How many users are in your organization? I'm guessing everyone would be using the mail system? Since you are currently using POP/SMTP/IMAP type connectivity with squirrelmail, isn't that the same as the standard user options on Scalix? You can use the Community Edition with unlimited standard users. The 25-premium users just get some additional features, which up to now you have not had or used anyway.

---

### Post by edmicman on 2007-11-15
> **Fire_Chief said:**
> How many users are in your organization? I'm guessing everyone would be using the mail system? Since you are currently using POP/SMTP/IMAP type connectivity with squirrelmail, isn't that the same as the standard user options on Scalix? You can use the Community Edition with unlimited standard users. The 25-premium users just get some additional features, which up to now you have not had or used anyway.

Thanks for the reply!  It looks like have ~60 email addresses currently, for a main domain, and a couple smaller ones that are basically just aliases.  

One of the things that caught my eye about Scalix was that it offered some Outlook integration and groupware things like calendaring.  But I think that was just offered on the Premium users?  Most of our staff uses Outlook, but connected via POP3 or IMAP; most of our tech staff just uses Thunderbird via IMAP.  But I know a number of users have wanted the ability to have shared calendars and meeting requests and such....I was thinking that if I was going to try something new, I might look at something towards that end.  

But yes, for basic stuff, and essentially what we already have now, Scalix or probably pretty much anything else would be enough.  What's out there in the OSS world that offers actual groupware type email and applications, or is it all for-pay enterprise level stuff?

Thanks again for your help!

---

### Post by HermanAB on 2007-11-15
Use this: [http://www.citadel.org](http://www.citadel.org)

There is nothing easier than Citadel and since it uses a BerkeleyDB backend, it is very efficient and fast.  It tops out at 256 terabytes of mail, which is about 2560 times better than MS Exchange... ;)

Cheers,

H.

---

### Post by garba on 2007-11-15
> **edmicman said:**
> 

But yes, for basic stuff, and essentially what we already have now, Scalix or probably pretty much anything else would be enough.  What's out there in the OSS world that offers actual groupware type email and applications, or is it all for-pay enterprise level stuff?

Thanks again for your help!

I must have spent something like one zillion hours looking for a solid groupware solutions on linux and the answer is:

there's none that comes even close to exchange-outlook

let me get this straight, i couldn't care less about the groupware stuff. If you are looking for a solid, serious email solution I would go the postfix/courier route, though cyrus might serve you better on the imap side. But if you are looking for an all-in-one exchange/outlook replacement, simply forget about it. Here's a mini review of all the groupware solutions I've come across so far:

- zimbra: fake open source, very hard to integrate with your current smtp/imap setup (if any), takes up a lot of resources, a wondrous ajax-based web app on the frontend though 
- scalix: nearly an outlook clone, it comes with an evolution connector that sucks to no end, nice web frontend though
- kolab: this is one interesting project: it relies on imap shared folder to serve shared calendars contacts etc, works with kde kontact
- openexchange/opengroupware: given the livecd a try, no luck

I've found all the programs mentioned above bloated and plagued by sub-par (nonweb) client side functionalities

- horde: php-mysql based, i love this one but it still needs some time to mature, slightly hard to setup but I find it a very professional looking app
- egroupware: this is what we currently have up and running, it's a web-app and it comes with some kontact support (but it doesn't support disconnected operations), it comes with syncml support and eventually got our palms to work with it

hope this helps

---

### Post by HermanAB on 2007-11-15
Well, yeah, Citadel doesn't come close to Exchange, because Citadel is simply miles ahead.

---

### Post by edmicman on 2007-11-15
Thanks everyone!  I'll definitely check out Citadel, it looks like it might be sharp.  Heck, I still might try some of the others, too!

---

