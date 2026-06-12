---
title: "Apache2 &amp; mod_ssl Question: mod_ssl and Certificate-Based Authentication"
date: 2011-10-27
forum: Server Platforms
---

### Post by geudrik on 2011-10-27
Alright, I've been beating my head against a wall for a while now... 

I am trying to set up a certificate based access to a directory, /sekrit, on my webserver.
I am using a Class 1 CA-issued set of certificates for my server - SSL is forced, :80 connections are not allowed.  The set of CA files I'm using are listed as follows.
```

        SSLCertificateFile      /etc/apache2/ssl/ssl.crt
        SSLCertificateKeyFile   /etc/apache2/ssl/ssl.key
        SSLCertificateChainFile /etc/apache2/ssl/sub.class1.server.ca.pem
        SSLCACertificateFile    /etc/apache2/ssl/ca.pem

```

I have run the following commands to generate a user certificate (that they install in their browser) and every time I keep getting
```
(Error code: ssl_error_handshake_failure_alert)
```
```

$ openssl genrsa -out ~/client.key 2048
$ openssl req -new -key ~/client.key -out ~/client.csr
$ sudo openssl x509 -req -days 365 -CA /etc/apache2/ssl/ssl.crt -CAkey /etc/apache2/ssl/ssl.key -CAcreateserial -in ~/client.csr -out ~/client.crt
$ openssl pkcs12 -export -clcerts -in ~/client.crt -inkey ~/client.key -out ~/client.p12

```

I have also tried 1024 and 4096bit key lenghts, and the signing goes through all hunky dory, but I continually get the same error when trying to connect.

By the way, the code I have in my xxx.com:443 vhost is:
```

<Location /sekrit>
                SSLVerifyClient require
                SSLVerifyDepth  2
</Location>

```

---

### Post by geudrik on 2011-10-28
I seem to be making progress here...
```

        <Directory "/var/www/sekrit">
                # SSLCACertificateFile    /etc/apache2/ssl/ssl.crt
                SSLCACertificateFile    /etc/apache2/ssl/ca.pem
                SSLVerifyClient require
                SSLVerifyDepth  10
                SSLOptions      +StrictRequire
                SSLRequire      %{SSL_CIPHER_USEKEYSIZE} >= 128
                Options +Indexes
        </Directory>


```

I get prompted to identify my self, so I used one of the certs I've created, Then I get a blank page, so I refresh and I get this error...

```

An error occurred during a connection to somewherekewl.com.

Peer does not recognize and trust the CA that issued your certificate.

(Error code: ssl_error_unknown_ca_alert)


```
Can anyone shed any light on this?   :confused:

Edit: I understand what the error is saying / what it means, but it doesn't make any sense... I'm using the crt that startcom gave me (my class 1) to sign the users' keys when I convert them into k12's...  So what am I missing?

---

### Post by hawkmage on 2011-10-28
In general I prefer to use the SSLCACertificatePath directive instead of the SSLCACertificateFile.  

You should have a directory /etc/ssl/certs with a bunch of PEM encoded CA certs.  If the CA that signed your client certificate is not in /etc/ssl/certs put a copy in there and then you have to rehash the certificates by running the "c_rehash" command as root in the /etc/ssl/certs directory.

---

