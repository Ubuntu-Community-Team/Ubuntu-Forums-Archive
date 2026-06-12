---
title: "Dovecot Thunderbird missing attachements"
date: 2012-01-10
forum: Server Platforms
---

### Post by kamaji792 on 2012-01-10
I am running a Dovecot e-mail server to collect e-mails.  Installed with the Ubuntu Howto.  We are using Thunderbird as the client (on Windows).

All is working fine and dandy but just a few people who e-mail us can't send attachments.  Well they can but we can't see them.

Any idea how I may track down this problem?

Thanks in advance k

---

### Post by SeijiSensei on 2012-01-10
Neither dovecot nor Thunderbird remove attachments. 

In Thunderbird, use the command View > Message Source to see the entire plain-text message you received.  See any attachments?  If not, they were stripped by something else along the way.

If all the senders with this problem come from the same organization, I'd hazard a guess that their mail system is somehow mis-configured.

---

### Post by kamaji792 on 2012-01-11
Thanks for the reply SeijiSensei.

I looked at the source for the e-mails and, you were absolutely right, the attachment is there.

We are essentialy in the realm of solved.  I have been able to refine the conditions under which the problem occurs.
[LIST]
[*]They only occur with attachments from **Hotmail** accounts.
[*]It only occurs when replying to an e-mail we sent.
[/LIST]

I think the main issue is something to do with our e-mail signature confusing Tunderbird so it can't see the attachment, linked in with the e-mail being from a Hotmail account.

Thanks again k

[edit] The workkaround is to get Hotmail users to send us an e-mail with an attachment as a new e-mail rather than replying to it.  Obviously I'll have a look at our e-mail signature to see if anything is wrong.

---

