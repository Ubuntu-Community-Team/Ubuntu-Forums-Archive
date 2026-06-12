---
title: "Ubuntu 6.10, Postfix, Courier &amp; Amavisd-new: problems with UTF-8"
date: 2007-02-20
forum: Server Platforms
---

### Post by felobros on 2007-02-20
Hi,
I'm working on Ubuntu 6.10 mail server configuration. The packages installed are: Postfix, with virtual maildirs, postfixadmin (to admin postfix by web), Courier, Cyrus SASL,
Amavisd-new, ClamAV, Spamassassin and SquirrelMail.
After a long time passed reading many how-to, not exhaustives (wroten for older version of the software), and also many manuals of the packages, I obtained a running mail server, but still a big problem about the UTF-8 encoding of Unicode-aware 6.10.
In fact, after many tests I discovered that Amavisd-new, running under perl 5.8.8 (also Unicode-aware), gets and parse the input message saving it in the correct maildir, but the message is encoded in UTF-8. Amavisd-new process change characters to UTF-8 but the MIME ContentType still with the original charset... So I have an internal encoded UTF-8 message file but the MIME is set with another charset (i.e. ISO-8859-15 euro). So, when I download a message with my client I have problems with extra chars, because the charset in the MIME still the original!
I don't want to change locales because Unicode-aware may be the future, and also I will put on my server sites in different languages, and charsets.
I think that Amavisd-new/Perl should change MIME Content-Type after encoding a message in UTF-8, so the mail client can show characters in the correct aspect.
Until now, I haven't found a solution or an "escamotage" to avoid this problem. :( 
Is there someone that can help me?
Thanks!

---

### Post by Mr. C. on 2007-02-22
This is your problem:

[http://groups.google.com/group/mailing.unix.amavis-user/browse_frm/thread/d99626ec50b8804f/918ca30fe51edc63#918ca30fe51edc63](http://groups.google.com/group/mailing.unix.amavis-user/browse_frm/thread/d99626ec50b8804f/918ca30fe51edc63#918ca30fe51edc63)

---

