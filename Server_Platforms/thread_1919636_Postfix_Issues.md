---
title: "Postfix Issues"
date: 2012-02-03
forum: Server Platforms
---

### Post by Speedy on 2012-02-03
Hello

I am new to postfix & I am having a few problems achieving what I want.
Postfix is being used for servers to relay mail to an external exchange server & to bounce messages sent to an old exchange domain.

**1.Sender Address Rewriting**
I want all outgoing email to be sent using a single address

Using ```
smtp_generic_maps = regexp:/etc/postfix/generic
``` I can map an incoming address to an outgoing address but, I want any incoming address to go out with a single email address. This is because when it hits the exchange server it needs to think it has come from the $myorigin account that is sending the mail to the exchange server 

If it doesn't the exchange server rejects the message with the following error.
```
Client does not have permissions to send as this sender (in reply to end of DATA command))
```

**2.Block incoming domains & send a NDR**
Any incoming mail to domain1.com will be bounced back to the sender with an NDR saying the email domain is no longer in use.

/etc/postfix/main.cf
```
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = myorigin.com
mydomain = mydomain.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no
append_at_myorigin = yes


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no
relayhost = somerelay:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_use_tls = yes

#sender_canonical_maps = pcre:/etc/postfix/sender_canonical
#sender_canonical_classes = envelope_sender

# Add sites to mynetworks to allow them to send mail
mynetworks = /etc/postfix/mynetworks

smtp_generic_maps = regexp:/etc/postfix/generic


```

Thanks in advance

---

### Post by Speedy on 2012-02-03
I have managed to resolve question 1. Sender address rewriting.
By using the below expression

/etc/postfix/generic
```
/@olddomain\.com$/ myorignemailaddress
```

---

