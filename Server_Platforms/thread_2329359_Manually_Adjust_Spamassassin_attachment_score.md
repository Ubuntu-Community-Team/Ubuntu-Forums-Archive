---
title: "Manually Adjust Spamassassin attachment score"
date: 2016-06-30
forum: Server Platforms
---

### Post by nbrooks1 on 2016-06-30
I am looking to manually adjust spamassassin attachment scores. I cant seem to find any info regarding my search. Are there any recommendations? Is this possible?

Also is there a way to detect what type of attachment it is? For example I would like to raise attachments with .exe to automatically be marked as 6.0, a .zip to 2.0 etc 
Thank you in advance

---

### Post by nbrooks1 on 2016-07-15
bump

---

### Post by SeijiSensei on 2016-07-17
I don't use SA on Ubuntu, but most installations use /etc/mail/spamassassin as the location for user-defined rules.  You can include a "scores.cf" file there to change the scores assigned to various triggers by default.

That said, SA probably isn't really your best choice.  I suggest taking a look at [MailScanner]("http://www.mailscanner.info/") which is a powerful email filtering program that uses SA for spam scanning and supports a wide variety of anti-virus scanners as well.  It also has a system of rules that apply to specific file types like .exe's.

To do what you want, you'd need an SA rule that looks at the various Content-Type, Content-Description, or Content-Disposition headers for strings like \.zip$.  Something like this:
```

header MSG_HAS_ZIP          Content-Type =~ /\.zip$/i
score MSG_HAS_ZIP           2
describe MSG_HAS_ZIP        Message contains a ZIP attachment

```
Put rules like these in /etc/mail/spamassassin/attachment_rules.cf and restart your mail server software.

---

