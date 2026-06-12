---
title: "Help with postfix and spamassassin please - dumping spam emails to only one mailbox"
date: 2017-02-23
forum: Server Platforms
---

### Post by wildcatleeds on 2017-02-23
Our organization is using postfix on Ubuntu as a mail relay server so  there's no official mailboxes on it other than root.  I've noticed some  spam in the log which spamassassin caught, but they're false positives  (pdf files that are gzipped by a printer / scanner / copier).  We have  no incoming emails from anything other than our organization (local  network only, outgoing to our organizational mail servers only, no incoming from the internet or from the mail servers).


  I'd like to set it up so these emails get dumped into either root's  mail or a user set up specifically for spam mail so I can teach  spamassassin using spam / ham.  And if it's ham, have it sent out  properly.


  Please let me know what information is further needed.

---

### Post by SeijiSensei on 2017-02-23
Why even use SpamAssassin at all if you trust your internal users and get no external mail on this box?

If you want to keep SA, you can write a few custom rules to exempt certain addresses from scanning:
```

header FROM_PRINTER     From =~ /printer\@example.com/i
score  FROM_PRINTER     -100
describe FROM_PRINTER   Exempt mail sent from printer

```
That will add -100 to the score for mail from [email]printer@example.com[/email] so it won't be tagged as spam. (You have to escape the "@" sign with a backslash because @ has a special meaning in Perl regular expressions.)

Put custom rules in a file with a .cf extension, like whitelist.cf, in /etc/mail/spamassassin. You can have as many such files as you want.  If you want those files to be applied in a specific order, use names like 00_whitelist.cf.

If you install [MailScanner](http://www.mailscanner.info) on the box, you'll have many more options.  You can route spam (and virus-infected) mail to a quarantine or a specific mailbox or both.  You can also construct separate "Spam Actions" and "Non Spam Actions" rulesets that will route spam and ham any way you want.  You could also send a copy of all mail from [email]printer@example.com[/email] to an archival mailbox as well as sending a copy to the original addressee.

I've used MailScanner successfully with SpamAssassin and ClamAV for years.  You can also maintain whitelists and blacklists of addresses, so you don't need to use kludgy solutions like the one I gave above.

---

