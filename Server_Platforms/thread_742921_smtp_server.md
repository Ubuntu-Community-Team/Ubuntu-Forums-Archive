---
title: "smtp server"
date: 2008-04-02
forum: Server Platforms
---

### Post by kaiiserni on 2008-04-02
Hi,

Since 3 weeks I work in the IT-department of a Belgian company.
We have a problem with our bulk mailing. We send over hunderds mails in an hour.
We do that by using the smtp server of our ISP. 
We are not allowed to have an mailserver running, our ISP blocks these ports.
Our ISP sets limits: maximum 200 mails in 5 minutes. So when we are over this 200 mails we get locked out for 30 minutes.

I already have an ubuntu server running as a fileserver.
I was thinking of installing a sort of smtp server which splits our mailmerges in blocks of 150 (just to be sure) and only sends these blocks every 10 minutes. And eventually forwards these mails to the smtp of our ISP.

Is this possible? and how? Can somebody point me in the right direction?

thanks in advance

---

### Post by HermanAB on 2008-04-02
Upgrade your account so that you are allowed to run your own mail server, then install Postfix, Qmail or Citadel.

Cheers,

Herman

---

### Post by kaiiserni on 2008-04-02
We already have an professional account.
In Belgium we don't have much choice in internetproviders.

Isn't there a way to make an internal smtp server use the smtpserver from the ISP in ubuntu?
I know there is such an option in SMEserver.
The only thing I am really looking for is a method to spread the mails to have a maximum of 200 mails per 5 minutes.

I don't know where to look. On google I only find smtp solutions for windows. Or they are too expensive, or they are to crappy / unprofessional.

Any ideas?

thanks

---

### Post by HermanAB on 2008-04-02
Postfix:
relayhost = mail.example.com

in Citadel, you set it in the internet configuration screen.

[http://www.postfix.org/](http://www.postfix.org/)
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

---

### Post by uncannybuzzard on 2008-04-03
does your isp block port 587? this is typically used as an alternate for port 25. trying configuring a mailserver to use this port instead.

---

### Post by kaiiserni on 2008-04-03
all ports from 0 to 1000

---

### Post by hyper_ch on 2008-04-03
why not renting your own server at some ISP? for &#8364; 50.-/M you get a good, dedicated box. On there you have your static IP and you can mail as much as yuo want.

---

