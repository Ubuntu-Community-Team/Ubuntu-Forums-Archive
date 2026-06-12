---
title: "SMTP Authentication with Active Directory"
date: 2008-08-26
forum: Server Platforms
---

### Post by blakegrover on 2008-08-26
Hi,

I am a big ubuntu fan, but at my job they are 99% microsoft servers and 1% linux.  We would like to be able to put a linux server outside our internal network.  We would like to put sendmail/postfix and configure it so employees can use this linux server as a smtp mail server.  We would like to make them authenticate with our active directory so not everyone would be able to use our smtp server to send out email.

I have noticed some say to use sendmail, sasl, pam, and winbind.  But I do not have a lot of experience in senmail to get things going.  Any help would be appreciated.

Thanks
Blake

---

### Post by HermanAB on 2008-08-26
If you have less than 10,000 users, then it would be much less hassle to install Citadel as the mail server and edit /etc/pam.d/citadel to tell it to make use of winbind and krb5 to connect to ADS.

See [http://www.citadel.org](http://www.citadel.org)

Cheers,

Herman

---

### Post by blakegrover on 2008-08-26
Well we have around 4,000 employees and 30,000 students.  So I think we are over the 10,000 limit.  We use Proofpoint (spam/virus filtering) before it gets to our exchange servers and it looks like they will be able to turn on smtp authentication on those servers. Thanks for your help though

---

### Post by blakegrover on 2008-08-26
We actually are interested in getting an opensource solution setup and try before we use proofpoint as the smtp authentication.  Does anyone know how to get sendmail to have the smtp authentication to lookup in active directory?

---

### Post by blakegrover on 2008-09-08
Does anyone else have a tutorial or howto to get sendmail setup so you can authenticate smtp requests with active directory and then forward the email to the appropriate location?

Blake

---

### Post by HermanAB on 2008-09-08
BTW, Citadel doesn't have a 10,000 limit.  It is just that nobody has used it in very large installations.  It will probably work fine for you, since it certainly scales better than Exchange and you clearly know how to build beefy servers.  

I'd recommend that if you use Citadel, you put the Oracle BerkeleyDB database on a separate machine and calculate carefully how much storage space you would need.  BerkeleyDB can handle up to 256 TB of data, which should be enough for what you want to do.

This will certainly be easier than building a mail server out of the usual Lego kit (Postfix, Apache, Dovecot, Roundcube).

Cheers,

Herman

---

