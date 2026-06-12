---
title: "Advice for setting a Postfix server"
date: 2011-08-31
forum: Server Platforms
---

### Post by sergio-bobillier on 2011-08-31
Thanks to this entry in the Ubuntu documentation: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto) I have been able to set up a Postfix server with Virtual Domains working all right.

I have made some adjustments to the settings by reading through the Postfix documentation but I can't seem to get what I want.

The server should act as a mail server allowing users from various domains to receive email messages and also let them send messages to other domains (like google, etc), at the same time the server has to handle the email sent by web applications installed on the server.

Here is what I need:

1. If the client authenticates on the SMTP server it should:

[LIST]
[*]Allow any sender (including domains and users that are not in the virtual domains database) because some applications have send to a friend forms that send the email as if it was sent from the User's email.
[*]Allow any recipient (including the virtual domains on the server and other domain -relay-)
[/LIST]
2. If the client doesn't authenticate on the SMTP it should:

[LIST]
[*]Allow it to send messages only to the users registered on the server database. -deny relay access- So spammers cannot abuse of the server.
[/LIST]
I have been messing around with the **smtpd_client_restrictions, ****smtpd_sender_restrictions **and **smtpd_recipient_restrictions** directives but I haven't been able to get the configuration I want.

Any help from anyone with experience setting up Postfix MTA would be appreciated.

Thanks in advance

---

