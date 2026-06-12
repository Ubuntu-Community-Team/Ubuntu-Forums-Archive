---
title: "Spamassassin quarantine - where?"
date: 2007-10-27
forum: Server Platforms
---

### Post by whit on 2007-10-27
I've got postfix running on 7.10 with the primary spam control being policyd-weight (excellent! - runs great on its default settings), and the backup being amavis-new with spamassassin. Stuff is pretty close to default for Ubuntu/Debian with all these tools. The mail.log is showing "quarantine" on some (obvious spam) messages that have made it by policyd-weight.

Here's my question. Where, by default, does the quarantined stuff go? I've run spamassassin previously (with sendmail on Gentoo) and when using a quarantine ended up with an mbox file of the stuff at /var/spool/mail, but that's evidently not the Ubuntu/Debian location - and I'm not finding it under the user's home directory either.

Now, it could be that the "quarantine" message is spurious - there are some spamassassin functions that amavis-new nullifies. But for the moment I'm a bit confused on this, and would welcome any clarification.

---

### Post by whit on 2007-10-27
Found 'em: /var/lib/amavis/virusmails. They're all gzipped. Is there some convenient utility for sorting through these? A quarantine where each just sits by itself compressed seems a bit inconvenient for actually ever finding anything in - somewhat defeating the point of saving it at all.

Hmm, "zless" can view them. Guess the only way to have an index of them though would be to grep the mail log for "quarantine" - or is there a better system out there?

---

