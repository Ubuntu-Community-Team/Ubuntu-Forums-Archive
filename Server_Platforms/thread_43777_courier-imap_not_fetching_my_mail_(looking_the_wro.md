---
title: "courier-imap not fetching my mail (looking the wrong place?)"
date: 2005-06-23
forum: Server Platforms
---

### Post by Ribs on 2005-06-23
Hi,

Before I begin, I'm going to make one thing painfully clear. I'm a complete novice at mail servers, I have no idea what I'm doing most of the time. I followed this guide to set up a postfix + courier mail server; [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

After much tweaking, I was able to get stuff working... almost. It seems that when I try to fetch mail with evolution, nothing is retrieved at all. however, postfix does appear to store the e-mail in /var/spool/mail/virtual/ribs.

However I don't think courier is looking there. I have a feeling it's looking elsewhere, and therefore telling evolution that there is no e-mail present. How can I fix this? I have looked around the config files, to no avail.

Thanks in advance for your help.

Regards,
-Ribs.

---

### Post by Ribs on 2005-06-23
Time to feel really stupid  :roll: 

Seems it was looking in the right place after all, evolution just decided to show it in a silly little vfolder at the bottom, which I wasn't expecting... oh well...

Regards,
-Ribs.

---

