---
title: "Ubuntu postfix and external exchange server"
date: 2010-10-14
forum: Server Platforms
---

### Post by frankos44 on 2010-10-14
I have an issue with mail.

[www.mydomain.com](www.mydomain.com) is a website that sends mail directly using postfix on a ubuntu server.

I am trying to send an email to [email]joebloggs@mydomain.com[/email] which is hosted elsewhere on a microsoft exchange server. (yes i know but thats another subject)

The website is able send mail to anyone accept [email]anybody@mydomain.com[/email]. It seems to me that the email is being resolved locally and never gets sent as the domain name is same for both the website and email address.

Does anybody know how to fix this?

---

### Post by SeijiSensei on 2010-10-15
The simples solution is to make the Exchange server the "smart host" in Postfix.  See [http://embraceubuntu.com/2005/09/07/setting-a-smarthost-in-postfix/](http://embraceubuntu.com/2005/09/07/setting-a-smarthost-in-postfix/).  This tells Postfix to forward all mail to the Exchange server and let it handle subsequent delivery.

Of course the Exchange server will need to allow inbound SMTP mail from the web server.  This might entail firewalling or other issues you'll need to resolve with the admin of the Exchange server.

---

### Post by frankos44 on 2010-10-15
Thank for your quick response. I shall investigate.

---

