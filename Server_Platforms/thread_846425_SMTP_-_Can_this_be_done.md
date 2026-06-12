---
title: "SMTP - Can this be done?"
date: 2008-07-01
forum: Server Platforms
---

### Post by shendrickson10 on 2008-07-01
First let me state that this is my first linux installation.  I've only dabbled in your world.  I would like to learn more.  Please be kind and thank you in advance for any assistance.
I would like to be able to use this server as a SMTP relay/smarthost.  I'm a small company that has three divisions.  We have the dreaded exchange as an email platform.  The problem with exchange/outlook is that I can only send/reply from one address.  Even with add-on's I'm having issues with our configuration.  I'm able to receive emails from different domains just fine.  I would like to setup a front-end SMTP engine that would accept email from multiple domains and forward them into the exchange server for delivery.  Then on the outbound side, have SMTP acounts configured on the outlook clients that send mail from the various domains through this new Ubuntu server running Postfix.  Can that be done?

---

### Post by 505 on 2008-07-01
I'n not completely sure, but I don't think it can be done. The problem is in Outlook. If you configure Outlook to operate against an Exhange server it will use that Exchange server to send mail. I don't think there is a way to select a different SMTP server. However, I you would use IMAP in Outlook it is no problem. Then you can configure your own SMTP server to handle the outgoing mail.

---

### Post by shendrickson10 on 2008-07-01
Thank you for the reply.  So are you saying that if I configure Outlook to use IMAP, I can then point it to different SMTP engines?  Would I be able to install one ubuntu server that would host multiple domains and forward that email in?  Sorry, like I said, I'm new to this.

Steve.

---

