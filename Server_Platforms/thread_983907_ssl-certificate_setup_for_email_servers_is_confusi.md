---
title: "ssl-certificate setup for email servers is confusing me"
date: 2008-11-16
forum: Server Platforms
---

### Post by randomstuff on 2008-11-16
As stated in my other thread, I am trying to set up Postfix + Dovecot on my server. I have finally gotten Postfix to work, but Dovecot still doesn't work correctly. 

trying to connect remotely results in this:

```

openssl s_client -connect 88.189.182.88:993
CONNECTED(00000003)

```

But nothing further happens.

I believe that this is because my ssl certifcate setup is not correct, but the [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is very unclear about how to set it up correctly. I would appreciate if it if someone could answer the following questions:

[LIST=1]
[*]When setting up postfix I created a lot of certificates and keys, should/can I reuse any of these for dovecot? E.g. the postfix guide specifies the following steps:
```

      Configure Postfix for SMTP-AUTH using SASL (Dovecot SASL):

      sudo postconf -e 'smtpd_sasl_type = dovecot'
      sudo postconf -e 'smtpd_sasl_path = private/auth-client'
      sudo postconf -e 'smtpd_sasl_local_domain ='
      sudo postconf -e 'smtpd_sasl_security_options = noanonymous'
      sudo postconf -e 'broken_sasl_auth_clients = yes'
      sudo postconf -e 'smtpd_sasl_auth_enable = yes'
      sudo postconf -e 'smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination'
      sudo postconf -e 'inet_interfaces = all'


      [Note] 	

      The smtpd_sasl_path configuration is a path relative to the Postfix queue directory.
   2.

      Next, configure the digital certificate for TLS. When asked questions, follow the instructions and answer appropriately:

      openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024
      chmod 600 smtpd.key
      openssl req -new -key smtpd.key -out smtpd.csr
      sudo openssl x509 -req -days 365 -in smtpd.csr -signkey smtpd.key -out smtpd.crt
      openssl rsa -in smtpd.key -out smtpd.key.unencrypted
      mv -f smtpd.key.unencrypted smtpd.key
      openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650
      sudo mv smtpd.key /etc/ssl/private/
      sudo mv smtpd.crt /etc/ssl/certs/
      sudo mv cakey.pem /etc/ssl/private/
      sudo mv cacert.pem /etc/ssl/certs/

      [Note] 	

      You can get the digital certificate from a certificate authority. But unlike web clients, SMTP clients rarely complain about "self-signed certificates", so alternatively, you can create the certificate yourself. Refer to the section called “Creating a Self-Signed Certificate” for more details.
   3.

      Configure Postfix to provide TLS encryption for both incoming and outgoing mail:

      sudo postconf -e 'smtpd_tls_auth_only = no'
      sudo postconf -e 'smtp_use_tls = yes'
      sudo postconf -e 'smtpd_use_tls = yes'
      sudo postconf -e 'smtp_tls_note_starttls_offer = yes'
      sudo postconf -e 'smtpd_tls_key_file = /etc/ssl/private/smtpd.key'
      sudo postconf -e 'smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt'
      sudo postconf -e 'smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem'
      sudo postconf -e 'smtpd_tls_loglevel = 1'
      sudo postconf -e 'smtpd_tls_received_header = yes'
      sudo postconf -e 'smtpd_tls_session_cache_timeout = 3600s'
      sudo postconf -e 'tls_random_source = dev:/dev/urandom'
      sudo postconf -e 'myhostname = mail.example.com'



```
[*] What should I put into the dovecot config file, eg
```

ssl_cert_file = /etc/ssl/certs/snakeoil.pem
ssl_key_file = /etc/ssl/private/snakeoil.key

```

Should these refer to the postfix keys/certificates or do I need to crate new ones? The .pem file, is that the certificate used to sign the key, and is they key file the key that is signed with the server certificate?
[*] Can anybody provide me with a comprehensive list of keys/certificates that I need in a postfix/dovecot setup, and which keys should be specified where in the various config file?
[/LIST]

I would appreciate any help, I am growing tired of fighting with dovecot all day long :/

---

### Post by MJN on 2008-11-16
For both Postfix and Dovecot you need two (sometimes three) things:
 
1. The server's private key (/etc/ssl/private/smtpd.key in your case). This is known only to the server and is used to decrypt data that has been encrypted by the public key.
 
2. The server's certificate (/etc/ssl/certs/smtpd.crt in your case). This contains the server's public key and is optionally signed by a mutually trusted 3rd party (or self-signed in your case). Given the intrinsic connection between the public/private key pair this certificate can be freely distributed and used by connecting clients as a mechanism to trust (and exchange encrypted data with) only the holder of the private key.
 
3. Supporting CA file (/etc/ssl/certs/cacert.pem). This is only required if your certificate sits at the bottom of a long chain of certificates whose authenticity cannot be verified by other means. For example, you might have a long chain of 'private' CAs doing your signing and so the certificates for each would need to be sent to the client (if the final certificate doesn't already contain them) so they could traverse the chain verifying each step (e.g. I can trust D because it is signed by C who is signed by B who is signed by A, who I trust). It is also sometimes used to help authenticate clients in a similar fashion.
 
So, for Postfix your current configuration is fine - the private key, public certificate/key and CA chain file are all specified.
 
For Dovecot you only really need two parameters setting, the private key and public cert/key:
 
```
ssl_key_file = /etc/ssl/private/smtpd.key
ssl_cert_file = /etc/ssl/certs/smtpd.crt
```Yes, they can use the same keys/certificates because these are identifiers for the server, not the processes, hence are equally applicable to Postfix and Dovecot (this is assuming you connect to each service using the same name (and different port number)).
 
Any help?
 
Mathew

---

### Post by randomstuff on 2008-11-16
Thank you so much, you are my hero!

Your explanation was very nice and completely clear. My email server is now working both ways (sending and receiving). Thank you for taking your time to help me, this is very much appreciated!

---

### Post by MJN on 2008-11-16
You're welcome!

Mathew

---

### Post by randomstuff on 2008-11-16
I have another question actually, what are they key passphrase and challenge passwords for? I don't need to enter them when connecting, nor when restarting or configuring the services, so when do I need them? Or can I just forget about them?

---

### Post by MJN on 2008-11-16
When you created your private key it was encrypted with triple-DES hence it would have been no use to anyone unless they knew the passphrase to decrypt it. However, this also makes it no use to any application unless you are there to feed it the passphrase when you first start the process.

Hence, for convenience, you then permanently removed the encryption from the key to allow applications to access it without user intervention.

Of course, this presents a potential security vulnerability which is why the key is kept root-owned with 600 (owner read/write only) permissions.

Mathew

---

### Post by randomstuff on 2008-11-16
Ah, that makes sense indeed. Thank you!

---

### Post by Tichondrius on 2008-11-20
Hhahaha, sorry to crash the party but MSN said:

"1. The server's private key (/etc/ssl/private/smtpd.key in your case). This is known only to the server and used to encrypt data that can only be decrypted by the public key..."

What ????  Listen to your own words - "...that can only be decrypted by the public key...".   But the public key is PUBLIC (hello?) so that means
ANYONE can use your public key decrypt anything that you encrypt with your private key.  So there is no point in encrypting anything with your private key, is there ?

The private key is ACTUALLY USED TO DECRYPT (not encrypt) data that people encrypted with your PUBLIC key and sent to you. This way they know ONLY YOU can read what they sent. You use their public key to encrypt what you want to send to them, and the in turn use their PRIVATE KEY TO DECRYPT it, and so on.

Hope you understand now...

---

### Post by MJN on 2008-11-20
Thank you for pointing out my error - corrected now.
 
> You use their public key to encrypt what you want to send to them, and the in turn use their PRIVATE KEY TO DECRYPT it, and so on.No, not for TLS/SSL.
 
The public/private key pairs are used only to authenticate and securely exchange a random number. This common secret is then used as the key for a symmetrical cipher encryption/decryption.
 
The use of an asymmetric algorithm (public/private key pairs) would be too slow (in the order of hundreds of times slower) for the data stream and is hence only used for non-realtime applications such as encrypted e-mail, which is probably what you were thinking of.
 
> Hope you understand now...Yes, I always did. It was merely an error on my part swapping the encryption/decryption function round - it was a fairly lengthy post and whilst I proof read for spelling mistakes I admit to missing this error.
 
Sorry if this caused any confusion, and I hope now *you* understand.
 
Mathew

---

### Post by Tichondrius on 2008-11-20
I also understand and already know this, and from your other comments I figured that you also understood how encryption process works, so that **your original mention of using a private key to encrypt data ** was only a mis-statement and not really what you believe.

But still a  mistake is a mistake, at least that's what my math prof said when I forgot a square root could be negative as well as positive.

btw, private keys are used to encrypt raw data in at least one situation - when signing a document. When you do that, anyone can use your public key to decrypt the message, thus proving that the message was written by you (because only you have your private key). This application of public/private keys provides identity authentication, not encryption.

---

