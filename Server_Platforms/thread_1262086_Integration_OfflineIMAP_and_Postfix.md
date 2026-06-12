---
title: "Integration OfflineIMAP and Postfix"
date: 2009-09-09
forum: Server Platforms
---

### Post by cirobr on 2009-09-09
Hello,

I have successfully set up long ago an email server that reads mail from my POP ISP. It uses fetchmail/postfix/dovecot as on the below link:

[http://ubuntuforums.org/showthread.php?p=6394672#post6394672]("http://ubuntuforums.org/showthread.php?p=6394672#post6394672")

More recently, my ISP has adopted IMAP. Fetchmail was a complete failure for email capture, as all mails were flushed from the ISP once read by the server. As of today, the thread for this problem is open:

[http://ubuntuforums.org/showthread.php?t=1224716]("http://ubuntuforums.org/showthread.php?t=1224716")

As an attempt to solve it, I'm wondering to replace Fetchmail by OfflineIMAP. Would appreciate any help on how to integrate it with Postfix, therefore with minimum impact to the server and users.

Although OfflineIMAP shows simplicity, some basics are missing on the below reference page, such as how to configure the IMAP server password.

[http://software.complete.org/software/wiki/offlineimap/]("http://software.complete.org/software/wiki/offlineimap/")

Thanks.

---

