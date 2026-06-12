---
title: "managing updates for 4 servers"
date: 2008-02-23
forum: Server Platforms
---

### Post by glok_twen on 2008-02-23
hi. i have 4 servers all running 7.10, server version. each has decent storage and cpu capacity. they are connected by gigabit.

however, my internet is low-end (slow) dsl.

what is the textbook answer to get upgrades done with both minimum effort, and minimum network use:
- netboot
- make some sort of partial local mirror just for the server packages i use
- something different

thanks.

gt

---

### Post by k_grdn on 2008-02-23
Hi,

I've used apt-cacher in the past on production servers, not a bad solution.

Regards,

k_grdn

---

### Post by glok_twen on 2008-02-23
cool thanks that looks perfect.

what do you usually do to make any given server regularly check for and then install upgrades? (i am used to just running a desktop and upgrading when the gui notification tells me to).

also, when upgrading to a new release, say after 8.04 comes out, will that need to be done manually?

thanks,
gt

---

### Post by k_grdn on 2008-02-23
Hi,

There's a package called unattended-upgrades which you can use to install security updates or you could use aptitude upgrade with the -security option from a cron job, it's best to log updates incase something goes wrong, you could also implement logrotate to compress the logged data.  Also I think there's a package called cron-apt.

Consider the security risks involved in running software upgrades without supervision!

Regarding 8.04 upgrade this would best be run supervised.

Regards,

k_grdn

---

