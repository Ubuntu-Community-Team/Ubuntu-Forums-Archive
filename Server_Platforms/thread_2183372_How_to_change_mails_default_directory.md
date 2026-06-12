---
title: "How to change mails default directory"
date: 2013-10-24
forum: Server Platforms
---

### Post by mroussin51 on 2013-10-24
Hi all,

I am running **Ubuntu 12.04.3-Server AMD 64**. On which I have installed **Postfix** and set the mail directory as follows: [B]sudo postconf -e 'home_mailbox = Maildir/'

[/B]I would like to know how to tell the mail **MDA** where the new **Maildir/** is located so that I see my mail when I type **mail **on the command line once again.

I am unsure if I should abandon **mail** in favor of **procmail** as I an a layperson with regards to mail servers.

I have searched google thoroughly for this but have come up short. If someone can point me at a good tutorial or recommend reading it is appreciated.

best regards

The Rooster

---

### Post by SeijiSensei on 2013-10-24
I  suspect the **mail** program doesn't know how to work with Maildir systems very well.  It's a very primitive program that basically looks to the local file system for traditional mbox mailboxes.  Procmail isn't a solution either.  It is a "delivery agent" which can be programmed to massage and reroute messages on the way to your mailbox.

If you are looking for a decent text-based mail reader, I recommend **alpine** which is in the Ubuntu repositories ("sudo apt-get install alpine").  It was first developed as "Pine" at the University of Washington when UWash was also developing the IMAP mailbox protocol.  It knows how to handle all sorts of mail sources and has a nice full-screen text interface with helpful commands at the bottom of the screen.  The default text editor "nano" that ships with Ubuntu was originally created as the composition editor for pine.

---

### Post by mroussin51 on 2013-10-24
Dear [COLOR=#000000]SeijiSensei,

Thanks so much for explaining that to me. I think the reason I was not finding the answer on google due to the fact that I was searching for something that does not exist. I am certainly going to give alpine a try.

Very best regards,

mroussin51[/COLOR]

---

