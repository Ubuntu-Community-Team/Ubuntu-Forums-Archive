---
title: "Gmail &amp; Thunderbird"
date: 2012-02-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by FraggedLocust on 2012-02-27
I'm trying to migrate my Gmail into Thunderbird 11 (on Ubuntu 12.04). I have an error where copying the mail to the sent folder fails. Using the Account Settings for Copies & Folders, I checked to make sure the sent items do go to [gmail]/Sent Items. I've been doing some research, but all the information for this problem seems to be very dated (Thunderbird 3). Does anyone have any advice on how to get this sorted out?

EDIT: Also, I'm noticing that while the Gmail account is the active account (i.e. inbox/reading pane) the cursor has a spinner that doesn't go away, which makes me believe it is constantly polling my inbox. How do I fix this?

---

### Post by cortman on 2012-02-27
Are you using POP or IMAP?

---

### Post by FraggedLocust on 2012-02-27
> **cortman said:**
> Are you using POP or IMAP?

I'm using IMAP (forwarded from Hotmail via POP), because I eventually want to be able to use Gmail on multiple devices.

---

### Post by cortman on 2012-02-27
With IMAP doesn't it save messages in [IMAP] Sent? I also thought Imap saved an offline copy and updated with your account whenever you logged in. I don't think you should need to edit anything with copies and folders, that's more for POP3.
I could be wrong on this, but that's my impression.

---

### Post by FraggedLocust on 2012-02-27
It tries to save mails to my Sent folder, which is set up as an IMAP link to Gmail, but it fails. I don't have any local folders set up yet, except the default Trash/Outbox folder.

---

### Post by philinux on 2012-02-27
Moved to Precise forum.

---

### Post by checoimg on 2012-02-27
Imap as far as I know doesn't save e-mails. POP was made for I believe.

---

### Post by xajeiw9I on 2012-02-27
IMAP saves everything in the server, so you can access it using multiple clients. POP just downloads e-mail and delete them, so you have to keep them in a single device (and keep a backup).

Try configuring Thunderbird with the settings recommended by Google:

[http://support.google.com/mail/bin/answer.py?hl=en&answer=78892](http://support.google.com/mail/bin/answer.py?hl=en&answer=78892)

---

### Post by Gregory Lee on 2012-02-27
For Thunderbird using an IMAP mail server, whether it saves mail you send in the Sent folder, whether the Sent folder is local or an IMAP folder (on the server), and whether you're "subscribed" to the Sent folder, are all selectable options for Thunderbird.  I don't know what's going on, but it might help to give your Thunderbird account settings a careful look, to check all this out.  I don't understand what you're saying about your Sent folder being an IMAP link to your Gmail account -- you're talking about the file structure on the mail server?

---

### Post by FraggedLocust on 2012-02-27
> **Gregory Lee said:**
> I don't understand what you're saying about your Sent folder being an IMAP link to your Gmail account -- you're talking about the file structure on the mail server?
Yes. I can send email to other accounts from Thunderbird/Gmail, but cannot save a copy to the server, or receive any new mails from after the time it was initially set up.

---

### Post by VinDSL on 2012-02-27
A couple of things...

You can save a "local copy" of emails, using IMAP, if you wish (depending on the mail client).  You can even save "local copies" to multiple machines.

Secondly, Google uses their own implementation of IMAP, e.g it's not standard IMAP.

In Thunderbird, you can manipulate the Gmail IMAP folders directly below your name, but folders inside *[COLOR="DimGray"][Gmail][/COLOR]* can't be fooled with, even though you can see them. Folders that you have created are an exception to the rule.

There are 2 Sent folders, yours' and Google's (Google saves everything you send/receive, regardless of what you do).

You *might* be able to save mails to your Sent folder, but I can guarantee you that you cannot save/delete anything to/from *[COLOR="DimGray"][Gmail][/COLOR]* folders.

Matter of fact, your Sent folder, and Google's Sent folder, may be one and the same, even though it *looks* like they are two different folders.  In that case, you won't be able to do anything to it.  LoL!

---

