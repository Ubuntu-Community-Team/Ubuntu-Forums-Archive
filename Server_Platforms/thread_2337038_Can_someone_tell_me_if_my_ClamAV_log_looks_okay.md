---
title: "Can someone tell me if my ClamAV log looks okay?"
date: 2016-09-13
forum: Server Platforms
---

### Post by Heeter on 2016-09-13
Hi all

Wondering if someone can tell me if clamav is updating correctly, if this looks okay, I constantly see this in the logs

```

Number of files: 46 (reg: 46)
Number of created files: 0
Number of regular files transferred: 0
Total file size: 20,639,374 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 1,541
File list generation time: 0.244 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 34
Total bytes received: 1,571

sent 34 bytes  received 1,571 bytes  642.00 bytes/sec
total size is 20,639,374  speedup is 12,859.42
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/spamattach.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/phishtank.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_phishing_URL.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/junk.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/porcupine.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/sanesecurity.ftmâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/.phishtank.ndb.eOMPDkâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/blurl.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_malware_attach.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/spamattach.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_extended_malware.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_malware_URL.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/jurlbl.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow.attachments.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/porcupine.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_cracked_URL.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_extended_malware.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/sanesecurity.ftm.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_bad_cw.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/phishtank.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/scam.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_bad_cw.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_malware.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/junk.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/jurlbl.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_malware_attach.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/sigwhitelist.ign2.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_malware.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/sigwhitelist.ign2â&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/crdfam.clamav.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/rogue.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_phishing_URL.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_cracked_URL.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/crdfam.clamav.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow.attachments.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/bofhland_malware_URL.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_malware_links.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/blurl.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/spamimg.hdb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/scam.ndb.sigâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/winnow_malware_links.ndbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/spamimg.hdbâ&#8364;&#8482;: Operation not permitted
chmod: changing permissions of â&#8364;&#732;/usr/unofficial-dbs/ss-dbs/rogue.hdb.sigâ&#8364;&#8482;: Operation not permitted

```

```

Tue Sep 13 18:59:01 MDT 2016 - Pausing database file updates for 156 seconds...

Tue Sep 13 19:01:37 MDT 2016 - Pause complete, checking for new database files...
====================
= ClamD is running =
====================

======================================================================
Sanesecurity Database & GPG Signature File Updates
======================================================================

Sanesecurity mirror site used: jfka.mirror.jhcloos.com 45.55.230.41

Number of files: 46 (reg: 46)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 5
Total file size: 20,637,971 bytes
Total transferred file size: 5,059,718 bytes
Literal data: 44,038 bytes
Matched data: 5,015,680 bytes
File list size: 1,549
File list generation time: 0.217 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 18,326
Total bytes received: 12,292

sent 18,326 bytes  received 12,292 bytes  12,247.20 bytes/sec
total size is 20,637,971  speedup is 674.05

Testing updated Sanesecurity database file: jurlbl.ndb
Sanesecurity GPG Signature tested good on jurlbl.ndb database
Clamscan reports Sanesecurity jurlbl.ndb database integrity tested good
Successfully updated Sanesecurity production database file: jurlbl.ndb

Testing updated Sanesecurity database file: phishtank.ndb
Sanesecurity GPG Signature tested good on phishtank.ndb database
Clamscan reports Sanesecurity phishtank.ndb database integrity tested good
Successfully updated Sanesecurity production database file: phishtank.ndb

======================================================================
SecuriteInfo Database File Updates
======================================================================

4 hours have not yet elapsed since the last SecuriteInfo update check

     --- No update check was performed at this time ---

Next check will be performed in approximately 3 hour(s), 26 minute(s)

======================================================================
MalwarePatrol Database File Update
======================================================================

6 hours have not yet elapsed since the last MalwarePatrol download

     --- No database download was performed at this time ---

Next download will be performed in approximately 5 hour(s), 26 minute(s)

===============================================================
= Database reload has been disabled in the configuration file =
===============================================================

```

Just wondering about the "Operation not permitted" at the end

This is for a Ubuntu 14.04 Email Server running Dovecot/postfix/mailman

Regards

---

### Post by howefield on 2016-10-03
In the absence of any other reply, I'd suggest checking the log versus the latest db release to check that clamav is being updated.

```
Mon Oct  3 13:01:58 2016 -> freshclam daemon 0.99 (OS: linux-gnu, ARCH: x86_64, CPU: x86_64)
Mon Oct  3 13:01:58 2016 -> ClamAV update process started at Mon Oct  3 13:01:58 2016
Mon Oct  3 13:01:58 2016 -> WARNING: Your ClamAV installation is OUTDATED!
Mon Oct  3 13:01:58 2016 -> WARNING: Local version: 0.99 Recommended version: 0.99.2
Mon Oct  3 13:01:58 2016 -> DON'T PANIC! Read http://www.clamav.net/support/faq
Mon Oct  3 13:01:58 2016 -> main.cvd is up to date (version: 57, sigs: 4218790, f-level: 60, builder: amishhammer)
Mon Oct  3 13:01:58 2016 -> daily.cvd is up to date (version: 22296, sigs: 650100, f-level: 63, builder: neo)
Mon Oct  3 13:01:58 2016 -> bytecode.cvd is up to date (version: 283, sigs: 53, f-level: 63, builder: neo)
Mon Oct  3 13:01:58 2016 -> --------------------------------------
```

The "*Operation not permitted*" would appear to be a separate issue.

---

### Post by SeijiSensei on 2016-10-03
> â€˜/usr/unofficial-dbs/ss-dbs/bofhland_phishing_URL.ndbâ€™

Are those special characters just a problem of translation to or from UTF-8?  Or do they exist in the filenames themselves?  That could be the problem right there. 

The "operation not permitted" error means that the script doesn't have the required permissions to make changes to those files.  Have you looked at those files in "/usr/unofficial-dbs?  What's their ownership and permissions? 

I'd try deleting the entire /usr/unofficial-dbs tree and letting the application rebuild it.

(By the way, I don't know what created that directory, but it doesn't conform to the Linux [filesystem standard]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").  It should be someplace like /usr/share.  Nothing should be creating directories directly below /usr.)

---

