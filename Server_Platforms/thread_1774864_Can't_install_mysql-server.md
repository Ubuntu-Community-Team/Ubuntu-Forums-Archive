---
title: "Can't install mysql-server"
date: 2011-06-03
forum: Server Platforms
---

### Post by tampe125 on 2011-06-03
hi, i have a problem that's driving me crazy:

i'm trying to install mysql-server on my pc. so i type this on my terminal:

```

sudo apt-get install mysql-server

```it starts to download & install everything, but when it has to configure the server, it simply "freeze" and does nothing!

how can i solve that?
i've tried to purge and reinstall, but it was no use!

any advice?
thanks in advance!

---

### Post by tampe125 on 2011-06-04
i re-installed Ubuntu 11.04.
from a fresh install, i have the same problem.

when Ubuntu tries to configure mysql, it simply freeze and does nothing!

please, can you help me?
i really need mysql ](*,)

---

### Post by joppuh123 on 2011-06-04
Do you run ubuntu desktop or server.

If you run server you could try to install mysql while installing the whole system from CD or USB

You could also try to install LAMP its apache mysql and PHP

---

### Post by tampe125 on 2011-06-04
i use ubuntu desktop.
now i just tried and...

it worked O_O

i really don't know why, nothing has changed...

---

### Post by sandpaperback on 2011-06-26
I'm currently having the same issue. I just got a VPS and I'm trying to set everything up. Once I apt-get install mysql-server, it goes along for a bit then hangs. Upon reboot, the mysql process is running and maxing out my allotted RAM, can't be killed and can't be uninstalled.

:-( Just did a reinstall of the OS (11.04) and will try a third time.

---

### Post by Roth NRK on 2011-06-27
I've been trying to install mysql-server on 10.04 LTS and have the same problem with the install freezing towards the end. 

I don't want to reinstall the OS

Does anyone have a solution to this problem? 

Thank you in advance.
Roth

---

### Post by sandpaperback on 2011-06-27
I opened a ticket with my VPS provider. They said my issue is just that the installation needs more memory available to continue, so they've raised my cap temporarily. Going to give it a shot now.

---

