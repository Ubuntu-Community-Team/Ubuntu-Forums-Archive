---
title: "CUPS Queue Managment Question"
date: 2013-08-07
forum: Server Platforms
---

### Post by Vartan An on 2013-08-07
Hello every one, i got a small question,
In the CUPS web interface i can see the queue but because i am using a windows environment the printing is done as "guest user" and on the interface under user i see "Withheld", my question is there any way to have the interface display the IP or even the hostname of the computer that sent the print job?


thank you in advance.
Vartan

---

### Post by JnPson on 2013-08-21
BUMP
I wonder if there is a way to see who or what computer is printing.

---

### Post by cartaysm on 2013-08-21
Change config to;

JobPrivateAccess all
JobPrivateValues none

---

### Post by JnPson on 2013-08-21
Thank you for answering, but the proposed solution didn't help. I still see ```
Name: Unknown, User: Withheld.
```

I don't wish to steel this tread from Vartan An, but I'm having a similar problem at work. I can't see which computer is stopping the printing queue and I would like to identify it to solve the problem.

---

### Post by SeijiSensei on 2013-08-21
Take a look at the logs in /var/log/cups and see if you get any clues.

---

### Post by JnPson on 2013-08-21
I missed the second part in cupsd.conf. 
```
# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess all
  JobPrivateValues none
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
```
 
and
```
# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess all
  JobPrivateValues none
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

```

I don't know if it is nessesary but, I set both to *all* and *none*, Now it works. Thank you guys for the help.

---

