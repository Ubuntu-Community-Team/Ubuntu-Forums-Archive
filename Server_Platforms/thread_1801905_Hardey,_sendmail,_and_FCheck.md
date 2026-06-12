---
title: "Hardey, sendmail, and FCheck"
date: 2011-07-11
forum: Server Platforms
---

### Post by nweyer on 2011-07-11
Hello all,

I am hoping someone can point me in the right direction here.  I recently inherited an Ubuntu server where the previous admin had installed sendmail and FCheck IDS.

The issue I am encountering is that sendmail appears to be rewriting both /etc/mail/m4/dialup.m4
 and /etc/mail/sendmail.cf constantly (at least once per hour).   dailup.m4 never seems to change (other then the creation date), while sendmail.cf has the line describing who and when it was built changed.

So far I have had no luck tracking down why sendmail would be rewriting these files.

Any help would be appreciated.

---

### Post by SeijiSensei on 2011-07-11
> **nweyer said:**
> So far I have had no luck tracking down why sendmail would be rewriting these files.

sendmail would never rewrite these files.  I'm guessing there's a cron job running that does so.  There are a number of places that job could be created:

/etc/crontab
/etc/cron.hourly - since it appears the changes occur at that frequency
/etc/cron.d
/var/spool/cron/root

Happy hunting!

---

### Post by nweyer on 2011-07-11
> **SeijiSensei said:**
> sendmail would never rewrite these files.  I'm guessing there's a cron job running that does so.  There are a number of places that job could be created:

/etc/crontab
/etc/cron.hourly - since it appears the changes occur at that frequency
/etc/cron.d
/var/spool/cron/root

Happy hunting!

Hrm.  Well, there is a 'sendmail' in cron.d, but I ran the commands it contained manually and got no changes.  However that calls /etc/init.d/sendmail which has the ability to rebuild. So that gives me a potential place to look.

The only entry in cron.hourly is the FCheck one.

---

