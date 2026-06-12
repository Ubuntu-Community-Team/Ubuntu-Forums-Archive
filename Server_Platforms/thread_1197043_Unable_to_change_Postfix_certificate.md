---
title: "Unable to change Postfix certificate"
date: 2009-06-25
forum: Server Platforms
---

### Post by Magic Monkey on 2009-06-25
I'm on 9.04 and installed postfix + dovecot + squirrelmail through apt. Then I did dpkg-reconfigure postfix and input the stuff.

It seems that when you first do dpkg-reconfigure postfix, a certificate is generated for you. At least thats what I think happened. I then decided to change my hostname and tried to create a new certificate, inputing my new hostname when asked to:

```
mkdir /etc/postfix/ssl
cd /etc/postfix/ssl/
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024
chmod 600 smtpd.key
openssl req -new -key smtpd.key -out smtpd.csr
openssl x509 -req -days 3650 -in smtpd.csr -signkey smtpd.key -out smtpd.crt
openssl rsa -in smtpd.key -out smtpd.key.unencrypted
mv -f smtpd.key.unencrypted smtpd.key
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650
```

I then went on and configured postfix to look for the certificates:
```
postconf -e 'smtpd_sasl_local_domain ='
postconf -e 'smtpd_sasl_auth_enable = yes'
postconf -e 'smtpd_sasl_security_options = noanonymous'
postconf -e 'broken_sasl_auth_clients = yes'
postconf -e 'smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination'
postconf -e 'inet_interfaces = all'
echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
echo 'mech_list: plain login' >> /etc/postfix/sasl/smtpd.conf
postconf -e 'smtpd_tls_auth_only = no'
postconf -e 'smtp_use_tls = yes'
postconf -e 'smtpd_use_tls = yes'
postconf -e 'smtp_tls_note_starttls_offer = yes'
postconf -e 'smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key'
postconf -e 'smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt'
postconf -e 'smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem'
postconf -e 'smtpd_tls_loglevel = 1'
postconf -e 'smtpd_tls_received_header = yes'
postconf -e 'smtpd_tls_session_cache_timeout = 3600s'
postconf -e 'tls_random_source = dev:/dev/urandom'
postconf -e 'myhostname = server1.example.com'
postconf -e 'home_mailbox = Maildir/'
postconf -e 'mailbox_command ='
```

Finally I restarted postfix with 	
/etc/init.d/postfix restart

Still, when I connect using Outlook 2007 it still displays the old hostname in the certificate.

I have checked main.cf and it points to /etc/postfix/ssl/
I even tried deleting all the files generated in the ssl directory and I still get the old certificate in Outlook.

Why?

---

### Post by ian.draco on 2011-01-11
You probably realized that you have configure dovecot to change imap and pop3 certificate ;)

---

