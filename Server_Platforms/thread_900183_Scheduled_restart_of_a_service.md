---
title: "Scheduled restart of a service?"
date: 2008-08-25
forum: Server Platforms
---

### Post by lainen on 2008-08-25
Hi there, what ways are there to schedule a restart of a service in Ubuntu 7.04/8.04? What i would like to do is the schedule a restart of service X every sunday night.

PS. I'm very new to the linux world and learning every day, so please be kind with me if this is a "must know" kind of thing (i did search through google.com/linux but found nothing) :)

---

### Post by synergy_ek on 2008-08-25
search for a cron documentation or just run crontab -e

---

### Post by sameerds on 2008-08-25
> **lainen said:**
> Hi there, what ways are there to schedule a restart of a service in Ubuntu 7.04/8.04? What i would like to do is the schedule a restart of service X every sunday night.

PS. I'm very new to the linux world and learning every day, so please be kind with me if this is a "must know" kind of thing (i did search through google.com/linux but found nothing) :)

The best way to schedule background jobs is to use cron. But I am more curious about this service that needs a scheduled restart. If restarting is so important, maybe that service itself comes with scripts to do that?

---

### Post by lainen on 2008-08-25
Thank you, cron seems to fill my needs perfectly.

Why we need to restart the service is because we have a memoryproblem with an application and until we have a "real" fix for it we need to restart the service. So it's a temporary workaround.

---

