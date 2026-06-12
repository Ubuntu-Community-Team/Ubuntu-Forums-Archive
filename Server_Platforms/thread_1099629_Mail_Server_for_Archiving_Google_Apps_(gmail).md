---
title: "Mail Server for Archiving Google Apps (gmail)"
date: 2009-03-18
forum: Server Platforms
---

### Post by OoteR on 2009-03-18
Hello all,

I've done some searching around not quite found what I'm looking for. 

I have google apps (premier) and am looking for an easy way to archive all messages sent to my domain. 

Google seems to have 2 ways of allowing this. 

1) Setup my own MTA and point my MX records to it. Do a store-forward to google's servers.

2) Give gmail a server address to relay mail to. 

Has anyone on here implemented a solution for this problem?

I need to archive mail for all my users in the easiest way possible, and haven't found an 'easy' solution yet. I'd hate to have to setup up a full MTA with all users etc to mimick the accounts that are on google's servers. I'd rather setup a 'set it and forget it' scenario. 

I think #2 could work if I accept all mail for the domain from gmail's servers, but I am not sure about how to create a catch-all address to save the mail to. 

Thanks for any help!

---

### Post by HermanAB on 2009-03-18
I would use Citadel.  It is easy to install, very configurable and rock solid stable with an Oracle BerkelyDB back-end.  It can store Terabytes of data.  You should be able to configure it with its Fetchmail-like feature to automatically download your schtuff:
[http://www.citadel.org](http://www.citadel.org)

You could have it up and saving your schtuff within an hour.

Cheers,

Herman

---

### Post by OoteR on 2009-03-18
Now why in the world would you throw that out in front of me? 

I had my administrators ready to go on google! Now I look at Citadel as a possible alternative to google completely. 

Thanks for nothing. 

:) No really, I appreciate the help.

Thanks!

Does the fetchmail stuff change any of the headers in the messages? After reading some more it seems i'd be better off to host the MTA myself and forward to google. I'm having a hard time making up my mind here.

---

