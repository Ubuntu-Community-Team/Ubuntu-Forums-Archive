---
title: "Friendly SMTP"
date: 2006-05-03
forum: Server Platforms
---

### Post by Stryker777 on 2006-05-03
I am using postfix as my smtp server.  Since I have my servers co-located I figured no one would complain about my once a week 200 email mailing list.  Some isps got angry though because I was sending too fast.

I DO NOT want to use my isp's smart host because of they have a habit of monitoring (looking at) emails.  I think that is a violation of everyones privacy and will not support it.

I havent found a way to delay sending so I only send 1 every so many seconds.  

Anyone have any advice on that?  A good smarthost package I can forward postfix to?  Maybe a postfix setting that will delay between sends?  

Thanks

---

### Post by souki on 2006-05-03
you can lower the number of maxproc for the smtp transport in master.cf
default is 100

[http://www.postfix.org/rate.html]("http://www.postfix.org/rate.html")

---

### Post by Stryker777 on 2006-05-03
Thank  you,
Good link there.  I dont know how I ever missed it.  I have been searching around for days lol.  I didnt do maxproc yet because that link had recipient limits listed.  Here is what i added to my config.  What do you think?
```

#how many concurrent connections to one host raises if available
initial_destination_concurrency = 2
#cap on how many concurrent connections to one host
default_destination_concurrency_limit = 5
#limit how many messages to one local recipient at a time
local_destination_concurrency_limit = 2
#Limit to how many recipients one email can have to one host.  Breaks into smaller lists if above.
default_destination_recipient_limit = 5

```

Thanks again!

---

### Post by MJN on 2006-05-03
[quote=Stryker777]I DO NOT want to use my isp's smart host because of they have a habit of monitoring (looking at) emails. I think that is a violation of everyones privacy and will not support it.[/quote] 
If they're inclined to do that what makes you think they aren't monitoring all outgoing traffic on port 25?

Mathew

---

### Post by MJN on 2006-05-03
[Duplicate post snipped]

---

### Post by Stryker777 on 2006-05-03
Because I work for them.  I know what does happen and often protest it.  Im only contract though so i dont have any pull.

---

### Post by MJN on 2006-05-03
Fair enough!

---

