---
title: "free mail server,"
date: 2007-01-25
forum: Server Platforms
---

### Post by feest on 2007-01-25
Hi i have a web server running lampp (linux apache mysql php perl) and i want to be able to mail with it, however i need a mail server for this, does anywone know a free mail server?

---

### Post by MrHorus on 2007-01-25
I use a combination of exim4, procmail and courier-imap-ssl and it works perfectly but if you want to run a mail server then you will want to ensure that your domain's MX record is set up properly or else you will have all sorts of problems with mails being rejected or never even reaching you to begin with.

---

### Post by jtc on 2007-01-25
If you by mailserver simply want to handle SMTP I'd say Postfix.

If you want to be able to access your mail through POP och IMAP you most likly want to use a separate server for that that purpose. Myself I've some good experience of using Courier.

---

### Post by DerHesse on 2007-01-25
[http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)

---

### Post by macubergeek on 2007-01-26
> **jtc said:**
> If you by mailserver simply want to handle SMTP I'd say Postfix.

If you want to be able to access your mail through POP och IMAP you most likly want to use a separate server for that that purpose. Myself I've some good experience of using Courier.

I'm running a Kubuntu box in a Windows environment running Exchange.

I want my Kubuntu box to be able to email me from a cron job via Postfix on localhost -->Exchange.

How do I config Postfix to do this?

---

### Post by chrisfay on 2007-01-27
> I want my Kubuntu box to be able to email me from a cron job via Postfix on localhost -->Exchange.

Not sure I totally understand, but if you want mail to relay from your postfix server through Exchange than you need to configure a relayhost on the Postfix side. 

If you want postfix to send it out then you shouldn't have to do anything special. 

Could you clarify?

---

### Post by feest on 2007-01-27
i want my php to be able to send mails

---

### Post by chrisfay on 2007-01-27
And what happens when you attempt to send mail via php? Or have you not even tried?

Create a new php file in your web root called mail.php and input:

```
<?php

$email = "user@domain.tld";
$body = "test message";
$subject = "test subject";

mail($email, $subject,$body);

echo "Test email has been sent.";

// end test mail script

?>
```

...replace "user@domain.tld" with your own email address, then navigate to the script in your browser. You should get the "test email has been sent" message. If you receive the email than your set.

If not, check your logs in /var/log/mail.log and mail.err

---

### Post by feest on 2007-01-29
tried this for so many times, there will never be a mail delivered.

---

### Post by chrisfay on 2007-01-29
My crystal ball is a bit cloudy....what do your logs say?

---

