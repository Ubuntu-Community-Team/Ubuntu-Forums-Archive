---
title: "Save outgoing mail in imap sent folder automatically"
date: 2009-03-05
forum: Server Platforms
---

### Post by Phasmagon on 2009-03-05
I have searched alot these past few days but I can't say I found an answer that fulfills my needs.

So here the thing.

I need a mail server which will deliver mail for six people (at least for now), to around 12 accounts. These six people, as one can easily conclude, won't monitor only one account. Anyone of them will monitor at least two, while some will monitor more than that. And of course some of them will monitor same accounts.

So I set up the configuration for the mail server which consists of postfix and dovecot. Mail is delivered through IMAP, so that users can interact to the same mailbox (categorize mail on folders, delete mail, etc)

Testing the configuration works fine and mail gets delivered greatly whether local or external.

BUT THERE IS A VERY IMPORTANT ISSUE WITH THE OUTGOING MAIL.

Whenever a user sents mail, that mail is stored locally on the computer that actually sent the mail and not on the sent items on the server.
This means that:

1) If someone sent a mail from one computer he cannot review that mail from another computer.
2) There is no way to know if someone responded to a received mail and what he said in it.

I now that you can configure manually the email client, to store the outgoing mail to the sent items on the server, but this is hardly a solution, since:

1) I am not intimate with all the possible email client my users may use.
2) I don't have physical access to all the workstations (I now at least two of them will check mail from roaming locations using their personal computers and/or laptops).
3) The workstations I control are quite a few. Nine permanent desktops, and a few laptops that get replace quite often.
4) Anyone can turn off the feature for any reason of his own without notifying (at least) about it.

So is there any way to save outgoing mail on the server automatically, (without any mail client interaction) using postfix (or anything else)?

Thanks in advance,
Phasmagon.

---

### Post by u-foka on 2010-05-19
Hy!

Have you found a proper solution for your problem? I seems to found myself in the same situation...

---

### Post by HermanAB on 2010-05-19
Postfix has an 'alwaysbcc' parameter that can be used for this.

---

