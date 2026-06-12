---
title: "Ubuntu File Upload Command"
date: 2010-04-16
forum: Ubuntu One (CLOSED)
---

### Post by false_chicken on 2010-04-16
Is there a way to upload a file to my ubuntu one account from the CLI? I would like to schedule a file to be uploaded from my computer every day.

---

### Post by rudihawk on 2010-04-16
You could just setup a cron job to copy the file into your Ubuntu-One directory in your Home folder which will then be sync'ed with the cloud.

---

### Post by joshuahoover on 2010-04-16
> **false_chicken said:**
> Is there a way to upload a file to my ubuntu one account from the CLI? I would like to schedule a file to be uploaded from my computer every day.

There isn't a way to run Ubuntu One from the command line. As was suggested previously, you could schedule to have files transferred to the ~/Ubuntu One folder. But if you are trying to do this on a headless machine (like a server) then this won't work as we require GNOME. We are looking at changing this requirement in the future so users can run Ubuntu One from a terminal session.

Thank you,

Joshua

---

### Post by rudihawk on 2010-04-19
> **aion4217 said:**
> I would like to schedule a file to be uploaded from my computer every  day.

Just setup a cron job(which will run at a specified time/interval) and will copy the file/folder you want to sync into your ~/Ubuntu-One folder. Ubuntu-One should then automatically upload the file.

---

### Post by JedMeister on 2010-04-20
> **joshuahoover said:**
> There isn't a way to run Ubuntu One from the command line. As was suggested previously, you could schedule to have files transferred to the ~/Ubuntu One folder. But if you are trying to do this on a headless machine (like a server) then this won't work as we require GNOME. We are looking at changing this requirement in the future so users can run Ubuntu One from a terminal session.

Thank you,

Joshua
:( that it's not available from CLI yet.
:) that it's something you're looking into!

Hopefully this will happen soon. Then I'll use it lots! 

Thanks for the info Joshua.

---

### Post by false_chicken on 2010-04-22
Thanks for the responses I went with the cron suggestion lol

---

### Post by rudihawk on 2010-04-24
> **false_chicken said:**
> Thanks for the responses I went with the cron suggestion lol

Does it work as you expected?

---

### Post by snowmann on 2010-10-11
are there any new informations about a cli tool?

thanks.

---

