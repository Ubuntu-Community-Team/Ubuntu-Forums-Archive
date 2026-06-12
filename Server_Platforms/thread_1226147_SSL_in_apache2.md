---
title: "SSL in apache2"
date: 2009-07-29
forum: Server Platforms
---

### Post by bluethundr on 2009-07-29
I am attempting to configure SSL in apache2.


in /etc/apache2/sites-available I have edited default-ssl

and added these lines:

```

  SSLCertificateFile    /etc/apache2/ssl/reports.pem
  SSLCertificateKeyFile /etc/apache2/ssl/reports.beezag.com.key

```

Then I restart apache and get this message prompting me to enter my RSA key passphrase which I do:

```

Starting web server: apache2Apache/2.2.9 mod_ssl/2.2.9 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Server nagios.beta.beezag.com:443 (RSA)
Enter pass phrase:

OK: Pass Phrase Dialog successful.
 failed!

```

As you can see the pass phrase seem to be ok, but apache fails to start. any tips?

---

### Post by weather15 on 2009-07-29
Is mod SSL enabled also I see that you edited /etc/apache2/sites-available/default-ssl did you move that file to sites-enabled?

---

### Post by bluethundr on 2009-07-29
before I attempted to restart Apache I issued a2enmod ssl and a2ensite default-ssl.

---

