---
title: "Help with PostFix SMTP Server"
date: 2016-02-28
forum: Server Platforms
---

### Post by Alec_Sadler on 2016-02-28
when I try to send a mail to gmail I get the following error(using postfix on linux 14.03)

host gmail-smtp-in.l.google.com[173.194.193.27] said:
    550-5.7.1 [65.185.47.86] The IP you're using to send mail is not authorized
    to 550-5.7.1 send email directly to our servers. Please use the SMTP relay
    at your 550-5.7.1 service provider instead.

Does anyone know a simple solution to this problem?

Also I have seen some examples of postfix directly relaying mail through gmail's smtp server, this option seems optimal to me, however I cannot figure out how to instruct postfix to relay its mail to gmail's smtp server.

Sorry if these are dumb questions or confusing. I'm just looking for a way to send emails from my domain without then being rejected(with postfix)

Thanks much in advance!

---

### Post by SeijiSensei on 2016-02-28
Only your ISP can help with this.  If you're using a residential connection, they may tell you that you are violating the Terms of Service which often include a "no-servers" clause.

---

### Post by houstonbofh on 2016-03-02
Gmail does not accept e-mail from consumer IP ranges.  (Spam fighting) You will need a static IP address not on any black lists, or a smart host. (smtp relay with login)

---

