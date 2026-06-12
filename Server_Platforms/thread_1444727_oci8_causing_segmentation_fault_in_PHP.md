---
title: "oci8 causing segmentation fault in PHP"
date: 2010-04-01
forum: Server Platforms
---

### Post by jw29 on 2010-04-01
Hello,

I'm having a problem with the oci8 module in PHP.  I have been running this server for over a year with this configuration and never had an issue... I had been away since last Thursday, and suddenly this started happening this morning.  I'm the only one who has server access, which has me baffled.

I've narrowed it down to the oci8 module because:
* I created a PHP script that does nothing except call oci_login(), which seg faults.
* Any web page that uses the oci functions fails... it asks you to download the PHP file, which is empty (likely because the oci_login call done before anything in PHP is printed).  Any webpage that does not use oci works fine.

Just wondering if anybody has any ideas.

Thank you in advance for any ideas you can provide.

---

### Post by jw29 on 2010-04-02
Nevermind... I found that it was a bug in the oci8 module caused when the Oracle server you connect to throws back a message saying that your password is going to expire in X days, which was caused by a sudden, unannounced change in our IT service's policies.

---

