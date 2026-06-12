---
title: "Unexpected reboot"
date: 2009-07-09
forum: Server Platforms
---

### Post by andremta on 2009-07-09
My Server had an expected reboot 2 times in a week.

Which logs contains the information I need to know what happened minutes before the reboot? /var/log/messages ?

---

### Post by dragos2 on 2009-07-09
$ last

---

### Post by andremta on 2009-07-17
This is happening 2/3 times a week.

And It happens almost at the same time. I don't have any crontab running near that time.

What could be happening? /var/log/messages seems to be cleaned after reboot. How can I find out what happened? No intended reboot was made, I check the $last

It seems like a power outage, but I do have an UPS connected as well with other servers and they didn't restart at all.


I have a DELL PowerEdge 2950 server with IMPI, if this will help.

---

### Post by smeerbartje on 2009-07-17
> **andremta said:**
> This is happening 2/3 times a week.

And It happens almost at the same time. I don't have any crontab running near that time.

What could be happening? /var/log/messages seems to be cleaned after reboot. How can I find out what happened? No intended reboot was made, I check the $last

It seems like a power outage, but I do have an UPS connected as well with other servers and they didn't restart at all.

What do you mean by checking '$last'? Is this a command or something?

---

### Post by andremta on 2009-07-17
> **smeerbartje said:**
> What do you mean by checking '$last'? Is this a command or something?

Yes, $man last
to check last logins and reboots by users.

---

### Post by dragos2 on 2009-07-17
> **andremta said:**
> Yes, $man last
to check last logins and reboots by users.

// from Vivek Gite
/etc/sysctl.conf
kernel.panic = 10 # to reboot after 10 seconds of a kernel panic

Also there was a kernel module that can provide useful information in case
of crashes but don't remember its name.

It was on the blog of Vivek Gite.

---

### Post by andremta on 2009-07-17
> **dragos2 said:**
> // from Vivek Gite
/etc/sysctl.conf
kernel.panic = 10 # to reboot after 10 seconds of a kernel panic

Also there was a kernel module that can provide useful information in case
of crashes but don't remember its name.

It was on the blog of Vivek Gite.

And how can I find out the machine was rebooted due a Kernel Panic?

---

