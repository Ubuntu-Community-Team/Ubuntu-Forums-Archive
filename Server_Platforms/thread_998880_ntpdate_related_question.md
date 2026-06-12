---
title: "ntpdate related question"
date: 2008-12-01
forum: Server Platforms
---

### Post by fouadk on 2008-12-01
hi everyone...

i need to synchronize my server clock with another server running active directory....

the way i do it manually is like the following:

```

sudo /etc/init.d/ntp stop
i write the password

sudo ntpdate 192.168.100.100

sudo /etc/init.d/ntp start

```

i want this to be automated on an hourly or daily basis.

how to do it ?

please help

thanks in advance

---

### Post by obg123 on 2008-12-01
cut away the sudos and put the rest in a script file. Then put the script file in /etc/cron.hourly/. Done.

Edit: Yes, you might have to sudo mv script /etc/cron.hourly/

---

### Post by fouadk on 2008-12-01
so if i create a file called for example ntp_upgrade.sh and give it root:root ownership with 775 as mode and put in it:

sudo /etc/init.d/ntp stop
ntpdate 192.168.100.100
/etc/init.d/ntp start

snd place this file in /etc/cron.hourly/
it should work???

---

### Post by MJN on 2008-12-01
You are going around this the wrong way. Ntpdate is not intended to be run on a regular/sceduled basis due to the risk of step changes.
 
You have ntpd installed (that's what provides your ntp service) and so use it as this is what it's for. List the AD server in /etc/ntp.conf and you're done.
 
If your machine is not always on, say perhaps a client workstation then you can use ntpdate but should not be trying to ntp(d) and ntpdate at the same time.
 
Mathew

---

### Post by fouadk on 2008-12-01
my linux server and AD server are always on....

the problem that i am facing is that every 15 days the time difference between the two servers becomes greater than 5 minutes so they loose connection so in order to avoid that every day i synchronize manually using ntpdate even though the IP of my AD server is listed in /etc/ntp.conf

---

### Post by obg123 on 2008-12-01
> **fouadk said:**
> so if i create a file called for example ntp_upgrade.sh and give it root:root ownership with 775 as mode and put in it:

sudo /etc/init.d/ntp stop
ntpdate 192.168.100.100
/etc/init.d/ntp start

snd place this file in /etc/cron.hourly/
it should work???

Yes it should. I don't have that much experience with ntpd though, so I can't comment on MJN's statement.

---

### Post by MJN on 2008-12-01
> **fouadk said:**
> my linux server and AD server are always on....
 
the problem that i am facing is that every 15 days the time difference between the two servers becomes greater than 5 minutes so they loose connection so in order to avoid that every day i synchronize manually using ntpdate even though the IP of my AD server is listed in /etc/ntp.conf
 
Then you've got a problem and your proposed workaround is at best a sticking plaster. Fix the the cause, not the symptom.
 
Do you know which server is drifting? (a 3rd machine can be used to determine this)
 
Mathew

---

