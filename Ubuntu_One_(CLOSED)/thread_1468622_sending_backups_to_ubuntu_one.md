---
title: "sending backups to ubuntu one"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by nbv4 on 2010-05-01
I have a website I run thats deployed on a server running ubuntu server (karmic, but will be upgrading to lucid in a few days). Currently I have a bash script that runs every 6 hours from my home machine that does the following:

1. signs into my server via ssh
2. runs a script that takes a snapshot of the postgres database
3. scp's that dump back to my home machine

I want to modify this slightly so the cron job is ran from my server, and instead of sending the dump file to my home computer, I want to send it to my Ubuntu One account. Is this possible/easy?

I found this: [http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars](http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars) but that seems really messy. I don't think it's worth the hassle to have to mess around with CouchDB. Is there an easier, more straight forward way?

---

### Post by joshuahoover on 2010-05-03
> **nbv4 said:**
> I have a website I run thats deployed on a server running ubuntu server (karmic, but will be upgrading to lucid in a few days). Currently I have a bash script that runs every 6 hours from my home machine that does the following:

1. signs into my server via ssh
2. runs a script that takes a snapshot of the postgres database
3. scp's that dump back to my home machine

I want to modify this slightly so the cron job is ran from my server, and instead of sending the dump file to my home computer, I want to send it to my Ubuntu One account. Is this possible/easy?

I found this: [http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars](http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars) but that seems really messy. I don't think it's worth the hassle to have to mess around with CouchDB. Is there an easier, more straight forward way?

There isn't a way to do this with Ubuntu One right now. The reason is mainly because Ubuntu One won't run on a headless box like a server. If it did, you could send the Postgres dump to a folder synchronized by Ubuntu One.

Thank you,

Joshua

---

