---
title: "mail function problem"
date: 2009-02-19
forum: Server Platforms
---

### Post by attyla on 2009-02-19
First excuse me for bad english. I want to use the function mail() in order to send the e-mail. I know that at first it is necessary appropriately to configure the php.ini file. I also know that I can use the SMTP option in Linux, if I don't have Sendmail set up. How the section [mail function] might look on a Linux without Sendmail? What is it necessary to change, when instead of Sendmail it installed itself and it configured Postfix correctly?

Thank you very much for the reply.

---

### Post by HermanAB on 2009-02-19
Most mail programs (Postfix, Qmail, Citadel) will install a dummy program called sendmail that will forward mail correctly in order to make these type of common scripts that expect sendmail to be there work.

Cheers,

Herman

---

### Post by ingeva on 2009-02-19
> **attyla said:**
> First excuse me for bad english. I want to use the function mail() in order to send the e-mail. I know that at first it is necessary appropriately to configure the php.ini file. I also know that I can use the SMTP option in Linux, if I don't have Sendmail set up. How the section [mail function] might look on a Linux without Sendmail? What is it necessary to change, when instead of Sendmail it installed itself and it configured Postfix correctly?

Thank you very much for the reply.

I've just been trying to set up postfix, but it won't send.
I think I know why: The server it tries to send to requires authentication, but I haven't found how to set it up.

I installed the following tiny smtp server:

```
sudo apt-get install ssmtp
```and then I edited the following file (need to be root to do that):

/etc/ssmtp.conf

The result in my case (Should be self-explanatory; I have changed the domain of my mailserver and the password:

```
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=inge@xyxyxyxyxy.com
AuthUser=inge@xyxyxyxyxy.com
AuthPass=zxzxzxzx
UseSTARTTLS=NO

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail.xyxyxyxyxy.com:587

# Where will the mail seem to come from?
rewriteDomain=xyxyxyxyxy.com

# The full hostname
hostname=Pantera

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES
```Works like a charm. Posfix made mail(...) return with a positive code, making it look like the mail was sent. It also returned "immediately".
With ssmtp there is a delay, corresponding to the time it takes to
communicate with your external smtp server.

---

### Post by attyla on 2009-02-20
Function mail() works :D Thanks Ingeva

---

