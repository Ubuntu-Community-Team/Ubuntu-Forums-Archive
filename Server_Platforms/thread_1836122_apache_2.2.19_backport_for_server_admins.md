---
title: "apache 2.2.19 backport for server admins"
date: 2011-08-30
forum: Server Platforms
---

### Post by ptn107 on 2011-08-30
Users running Ubuntu 10.04 LTS, 10.10, or 11.04 who would like to help test the backport of the latest stable apache2 can download it by adding this ppa.  Beats waiting for Oneiric or mixing repositories.

ppa:ptn107/ppa

---

### Post by jqp on 2011-09-01
I've got about 7 servers on LTS versions that need apache upgraded to score points on PCI scans. I'll report back what I find if I get a chance (and permission) to test this..

Makes me wonder what the hell the point of LTS is when there's security updates that I can't get through the proper channels... but yeah, thanks for the hard work if I get it working.

---

### Post by snek on 2011-09-02
Thank you my dear sir!
Just installed it on my VPS and everything worked without a hitch.
Was paranoid about the recent security hole so I am glad to find an updated version of apache.
Just saw that 2.2.20 is also out now, any chance you will release an update for that soon? :)

Ignore me, I just saw you did release 2.2.20 and not 2.2.19 like previously mentioned.. My bad!

---

### Post by snek on 2011-09-02
Hmm I just noticed that on launchpad Lucid has apach2 2.2.20 listed, but after adding the PPA it only seems to update to 2.2.19...
Any clues as to why this could happen? Also apache2-mpm-prefork is still at 2.2.19

---

### Post by SeijiSensei on 2011-09-02
I posted a question about when 2.2.20 might be released for Lucid on the Ubuntu Apache2 package page at [launchpad](https://answers.launchpad.net/ubuntu/+source/apache2/+question/169912).

---

### Post by ptn107 on 2011-09-02
I uploaded apache 2.2.20 to the ppa.  It should build soon if there are no errors.

---

