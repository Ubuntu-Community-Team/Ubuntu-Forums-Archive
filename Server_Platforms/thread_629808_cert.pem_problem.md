---
title: "cert.pem problem"
date: 2007-12-02
forum: Server Platforms
---

### Post by mitjab on 2007-12-02
Syntax error on line 1 of /etc/apache2/sites-enabled/cert.pem:
Invalid command '-----BEGIN', perhaps misspelled or defined by a module not included in the server configuration


file started with -----BEGIN CERTIFICATE-----
and end with -----END CERTIFICATE-----


what is wrong here?

---

### Post by Maxtorm on 2007-12-02
Shouldn't the cert file be elsewhere? I believe all files in the sites-enabled directory have to be in standard Apache config format. For instance: [http://www.focus-sis.org/docs/index.php/Linux_Apache2_SSL_Config](http://www.focus-sis.org/docs/index.php/Linux_Apache2_SSL_Config)

---

### Post by MJN on 2007-12-03
That's correct - the **Include** **/etc/apache2/sites-enabled/[^.#]* **directive in apache2.conf parses everything in sites-enabled/ as configuration. Move the certificate up a level (and change where it's referenced).

Mathew

---

