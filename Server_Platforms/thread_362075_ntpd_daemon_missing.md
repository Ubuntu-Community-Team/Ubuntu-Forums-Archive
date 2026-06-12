---
title: "ntpd daemon missing"
date: 2007-02-15
forum: Server Platforms
---

### Post by mizar001 on 2007-02-15
Hi. I'm setting up a server (breezy) and i want an ntp synchronization with some time servers.

At first i looked in the already installed ntpdate client. But this process only starts at boot and can be started periodically with a cron job. This could be a solution but i prefer a some more tuned work.

So i looked for the ntp package, trying to configure an ntpd daemon to do all the synchronization job.
But, the ntpd is missing. All other utilities (ntpq,ntpdc,etc..) are present, but not ntpd. Why ?

---

### Post by MJN on 2007-02-15
**ntp-simple** is probably what you're after.

Mathew

---

