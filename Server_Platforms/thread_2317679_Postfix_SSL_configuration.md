---
title: "Postfix SSL configuration"
date: 2016-03-18
forum: Server Platforms
---

### Post by Pascal_Pharand on 2016-03-18
Hi everyone,

I just finished configuring my postfix/dovecot mail server on my ubuntu 14.04 LTS server everything seems to be working well. I can send and receive message but I cannot seem to get the SSL working properly with the messaging applications like thunderbird or outlook.
I have bough SSL certificates from Rapidssl for my website domain but when I try to connect in thunderbird I get the warning that I have to add a security exception. I have tried many tutorial and my setup is based on this one : [http://www.binarytides.com/install-postfix-dovecot-debian/](http://www.binarytides.com/install-postfix-dovecot-debian/)

any help would be appreciated.

Here is my postfix (main.cf)

```

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = hiresweather.com


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


smtpd_tls_cert_file=/etc/apache2/ssl-certs/hiresweather.crt
smtpd_tls_key_file=/etc/apache2/ssl-certs/private2.key
smtpd_tls_CAfile=/etc/apache2/ssl-certs/rapidSSL_Root_CA.pem
#smtp_tls_CAfile=/etc/apache2/ssl-certs/rapidssl_cabundle.crt


smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.hiresweather.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#mydestination = hiresweather.com, localhost, localhost.localdomain, localhost
mydestination = localhost, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all


# LMTP SOCKET
virtual_transport = lmtp:unix:private/dovecot-lmtp


# SASL


smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_tls_auth_only = yes


# MALIBOX DOMAIN


virtual_mailbox_domains = /etc/postfix/virtual_mailbox_domains

```

This is my dovecot (10-ssl) : 

```

##
## SSL settings
##


# SSL/TLS support: yes, no, required. <doc/wiki/SSL.txt>
ssl = required


# PEM encoded X.509 SSL/TLS certificate and private key. They're opened before
# dropping root privileges, so keep the key file unreadable by anyone but
# root. Included doc/mkcert.sh can be used to easily generate self-signed
# certificate, just make sure to update the domains in dovecot-openssl.cnf
ssl_cert = </etc/apache2/ssl-certs/hiresweather.crt
ssl_key = </etc/apache2/ssl-certs/private2.key
ssl_ca = </etc/apache2/ssl-certs/intermediate.crt


# If key file is password protected, give the password here. Alternatively
# give it when starting dovecot with -p parameter. Since this file is often
# world-readable, you may want to place this setting instead to a different
# root owned 0600 file by using ssl_key_password = <path.
#ssl_key_password =


# PEM encoded trusted certificate authority. Set this only if you intend to use
# ssl_verify_client_cert=yes. The file should contain the CA certificate(s)
# followed by the matching CRL(s). (e.g. ssl_ca = </etc/ssl/certs/ca.pem)
#ssl_ca =


# Require that CRL check succeeds for client certificates.
#ssl_require_crl = yes


# Directory and/or file for trusted SSL CA certificates. These are used only
# when Dovecot needs to act as an SSL client (e.g. imapc backend). The
# directory is usually /etc/ssl/certs in Debian-based systems and the file is
# /etc/pki/tls/cert.pem in RedHat-based systems.
#ssl_client_ca_dir =
#ssl_client_ca_file =


# Request client to send a certificate. If you also want to require it, set
# auth_ssl_require_client_cert=yes in auth section.
#ssl_verify_client_cert = no


# Which field from certificate to use for username. commonName and
# x500UniqueIdentifier are the usual choices. You'll also need to set
# auth_ssl_username_from_cert=yes.
#ssl_cert_username_field = commonName


# DH parameters length to use.
#ssl_dh_parameters_length = 1024


# SSL protocols to use
#ssl_protocols = !SSLv2


# SSL ciphers to use
#ssl_cipher_list = ALL:!LOW:!SSLv2:!EXP:!aNULL


# Prefer the server's order of ciphers over client's.
#ssl_prefer_server_ciphers = no


# SSL crypto device to use, for valid values run "openssl engine"
#ssl_crypto_device =



```

---

