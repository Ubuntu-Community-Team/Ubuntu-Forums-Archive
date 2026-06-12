---
title: "snort-2.8.3.1 + BASE Installation Problem"
date: 2008-12-30
forum: Security
---

### Post by fast-Eddie on 2008-12-30
Hi,

I'm trying to install snort & BASE and have run into an issue. I've followed Bodhi Zazen's post on how to set it up but when I get to the "Install BASE" section, I have problems. I open Firefox to the BASE page and go through the steps and when I get to step 4, I click the "Create BASE AG" button and I get the following message on the next window:

" The underlying Alert DB is configured for usage with BASE.

Additional DB permissions
In order to support Alert purging (the selective ability to permanently delete alerts from the database) and DNS/whois lookup caching, the DB user "snort" must have the DELETE and UPDATE privilege on the database "snort@localhost" 

I don't think this is right. Is anyone able to help??

I'm a linux novice and have been trying to setup snort for days now. I must have tried & re-tried over 20 times now without luck. I'm using Ubuntu 8.10.

Any ideas anyone?? :(

---

### Post by Sarmacid on 2008-12-30
Seems like the user snort needs some privileges in mysql, try this```
mysql -u root -p
grant create,delete,insert,select,update on snort.* to snort@localhost;
grant create,delete,insert,select,update on snort.* to snort;
exit

```

---

### Post by fast-Eddie on 2008-12-30
Thanks Sarmacid. 

Tried the commands you provided and rebooted however when I go through the BASE setup, I still get the same error on step 4. 

Any other suggestions??

---

