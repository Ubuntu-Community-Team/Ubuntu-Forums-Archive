---
title: "Sending email with postfix ..."
date: 2009-04-02
forum: Server Platforms
---

### Post by Snoopx on 2009-04-02
Hello to everybody. I'm a "little" web designer and recently i have installed ubuntu 8.10 on my laptop at home. I'm making a php web site and i have a contact form where people can send they're messages. What is my problem and my question: i have a laptop at home, adsl internet, dynamic ip, no domain registered (just a normal connection with a normal laptop :d) i have installed ubuntu cause i was going crazy with vista and i want to configure it to send email to an external address (contactus@hotmail.com for example). I have read a lot of artciles and i have try to install and configure postfix in many way but nothing i can't make my ubuntu-laptop to send email. What i must to do ? Thanks!

---

### Post by hyper_ch on 2009-04-02
you need to relay email through your ISP. I assume you have a real email account at your ISP?

(1) Edit main.cf
```

sudo nano /etc/postfix/main.cf

```

and add the following:
```

smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
smtp_always_send_ehlo = yes
relayhost = smtp.yourisp.com

```
Replace there the "smtp.yourisp.com" with your ISPs real smtp server. In case your ISP does not use a standard port but a different one (mine uses 587) then add it like this:
```

relayhost = [smtp.yourisp.com]:587

```
Exit and save the file

(2) create the /etc/postfix/saslpasswd file
```

sudo nano /etc/postfix/saslpasswd

```
and add
```

smtp.yourisp.com     yourlogin:yourpassword

```
Replace the info accordingly. Again you use the smtp server of your ISP and replace "yourlogin" with the username you need to enter to login and the password also. The username is in some cases the whole email address. Once done, save and exit the file.

(3) Postmap the /etc/postfix/saslpasswd file
As postfix uses hashes you'll need to postmap the file
```

cd /etc/postfix
postmap saslpasswd

```

(4) Restart postfix
```

sudo /etc/init.d/postfix restart

```

Now you can send email from your server that gets relayed through your ISP.

---

### Post by Snoopx on 2009-04-02
done...not working !:confused::confused:

---

### Post by hyper_ch on 2009-04-02
how about having a look at the logs?

---

### Post by HermanAB on 2009-04-02
If you just want to forward mail, then postfix with its hundreds of configuration items is total overkill.  You should try nullmailer (and remove postfix).
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

So only need to set about 2 things to make nullmailer work.

---

