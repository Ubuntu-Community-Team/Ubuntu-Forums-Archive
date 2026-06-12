---
title: "Inserting fake mail via disconnect IMAP"
date: 2011-04-01
forum: Security
---

### Post by Blutkoete on 2011-04-01
Hello!

After a April Fools' Day joke with fake mails (simply faked by forwarding & changing the text body) I tried to insert "real" fake mail into my online GoogleMail account. It was incredibly simple and that freaks me out a little.

I simply created the mail in Kontact, moved it to the folder I wanted it to appear in and synced - done. Someone with better knowledge might probably even manipulate the Kontact database on my computer and then sync, even changing old mails from years ago.

Is there a way to prevent this or find out that the mail wasn't really e.g. sent but just faked? I'm working at the university as a teaching assistant at the moment and from time to time you have those "No, I didn't miss the deadline, I send the mail with the paper to you" students. It was never necessary until now, but I always thought that I might check that by simply asking the student to show me his or her "Sent" folder in their online mail account. But that won't work if you can insert mails into your "Sent" folder via disconnected IMAP.

Thank you very much,

Blutkoete

---

### Post by Seq on 2011-04-01
Email is just a bunch of text files that meet a certain number of requirements (a few required headers, a few formatting restrictions). It is not hard to forge, as you have seen.

If you're trying to find a way to prevent your students from forging a message and putting it in their own sent folders? No, there is nothing you can do to prevent them from doing that on their own computers.

Regarding if a message is "really" sent, or "fake" sent, you could check the timestamp (though they probably put a fake one in the headers). If they are accessing this via IMAP in a program that uses maildir, you could check the timestamp of the message file itself (though they could have changed it after writing the file. Also this wouldn't work for programs that use spool files).

All the fancy routing information indicating the message was received, what servers it touched, any auth checks performed, spam testing results, etc. all happen *after* the message was sent, and their copy would not contain any of that information regardless.

---

### Post by Seq on 2011-04-01
Specifically regarding gmail, I believe their web interface lists the date as when *they* saved the message, not when the message headers indicated it was sent.

When I migrated to gmail a few years ago, I copied over all my old email. Gmail's web interface shows that I sent hundreds of messages on the day I migrated, preventing a forged date (but also preventing preserving actual dates as far as gmail is concerned).

You might be able to use that, but that is a gmail-only quirk and not something reliable for all email providers.

---

### Post by Blutkoete on 2011-04-01
Thank you!

With "preventing" I meant more like preventing someone from messing with my GoogleMail folder if he has physical access to my computer. But that's probably more about encrypting & securing my own system or simply disabling IMAP in GoogleMail. But one more question: Is all the routing information really stored in the student's sent folder as well or only in my received folder?

I'll have a look into the time stamp with that saving vs. sent time. 

I'm even not sure whether asking someone to show me detailed info in their online mail account is very moral. The old Do-you-want-to-get-all-the-bad-ones-and-also-kill-some-good-ones-or-don't-convict-a-good-one-but-also-allow-some-bad-ones-to-get-away problem.

Let's just hope nobody ever tries to cheat a deadline this way - the assignments I get sent are (I hope) not important enough for that.

---

### Post by Seq on 2011-04-01
> **Blutkoete said:**
> With "preventing" I meant more like preventing someone from messing with my GoogleMail folder if he has physical access to my computer. But that's probably more about encrypting & securing my own system or simply disabling IMAP in GoogleMail.

Yes, it is a matter of securing your computer. If somebody has physical access they can do anything you can.

> **Blutkoete said:**
> But one more question: Is all the routing information really stored in the student's sent folder as well or only in my received folder?

No. Absolutely no routing information is stored for sent mail. They sent the message and are done with it. Routing is a delivery thing.

---

### Post by Blutkoete on 2011-04-01
Thank you two!

The time stamp would work. I changed my system time, created a mail to a friend of mine for yesterday, moved it to the GMail Sent folder and synced. It shows up in the online account as if written this very moment.

I hope that's true for all mail accounts.

Marked as solved.

---

### Post by Seq on 2011-04-01
> **Blutkoete said:**
> Thank you two!

The time stamp would work. I changed my system time, created a mail to a friend of mine for yesterday, moved it to the GMail Sent folder and synced. It shows up in the online account as if written this very moment.

I hope that's true for all mail accounts.

It very probably is not. There is no requirement one way or the other for which date email programs display (when they first received the message, or when the message indicates it was sent, etc). As there is no requirement, everybody will be different.

---

### Post by Blutkoete on 2011-04-01
Hmm.

So it's like this: While it would be easy to detect the cheating if the finding-out involves experts, lawyers and judges, in my situation ("Please send me the Simulink model until Friday, 20 pm", only an optional course at university) I won't be able to determine whether the student in front of me telling me that he or she sent the mail but somehow it didn't arrive in my mail account is telling the truth or not (if he or she is not using GMail).

But as nobody tried that excuse until now, I'll just hope it won't happen in the future.

EDIT: I'll just ask the university's mail administrators about this and then tell the students that I'll only accept assignments sent via their university mail account. Quick & dirty.

---

### Post by SeijiSensei on 2011-04-03
I'll add that the Date: field in an email is determined entirely by the sender's computer.  That doesn't hold true for the times reported in the Received headers, of course; they report the timestamps on the various servers that are transporting the message.  The date that shows up in your mail client can be easily forged just by resetting the system clock of the sending computer.

---

