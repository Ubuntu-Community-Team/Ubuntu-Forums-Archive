---
title: "Open source email encryption gateway"
date: 2009-02-10
forum: Server Platforms
---

### Post by m.brinkers on 2009-02-10
This might be interesting for Ubuntu users. It has been thoroughly tested on 8.04 and .deb files are available.

I would like to announce the release of my open source email 
encryption gateway.

Djigzo email encryption gateway is an email server (MTA) that encrypts
and decrypts your incoming and outgoing email. Because Djigzo serves as
a general SMTP email server, it is compatible with any existing email
infrastructure and can easily be placed before or after existing email
servers. Djigzo is typically installed as a "store and forward" server.
Email is therefore only temporarily stored until it is forwarded to it's
final destination. 

Djigzo currently supports two encryption standards; S/MIME and PDF
encryption. S/MIME provides authentication, message integrity and
non-repudiation (using X.509 certificates) and protection against
message interception. S/MIME uses public key encryption (PKI) for
encryption and signing. PDF encryption can be used as a lightweight
alternative to S/MIME encryption. PDF allows you to decrypt and read
encrypted PDF documents. PDF documents can even contain attachments
embedded within the encrypted PDF. The password for the PDF can be
manually set per recipient or a password can be randomly generated and
sent to the recipient via SMS. 

General features

  * Virtually unlimited number of users and certificates. 
  * Sender notification after email encryption. 
  * Settings can set at global, domain or user level. 
  * Web based interface. 
  * Separate back-(encryption engine) and front-end (SOAP API). 
  * Tightly integrates with Postfix (MTA). 
  * Java, Spring based. Services can be easily replaced 
    and/or extended. 
  * Can be installed stand-alone or as a "Virtual appliance". 
  * AGPLv3 licensed (commercial license available). 

S/MIME features

  * S/MIME 3.1 (X.509, RFC 3280). 
  * Automatic and manual certificate selection. 
  * Domain certificates (encryption to certain domains with 
    just one certificate). 
  * Certificates are automatically extracted from incoming email. 
  * Support for multiple certificates per sender/recipient. 
  * Incoming email is automatically decrypted. 
  * Immune against 'corruption' by non S/MIME aware disclaimer 
    services. 
  * Certificate revocation lists (CRLs) are automatically 
    downloaded (LDAP and HTTP). 
  * Support for Hardware Security Modules (HSM). 
  * Compatible with existing S/MIME implementations 
    (Outlook, Outlook express, Lotus Notes, Blackberry etc.). 

PDF email encryption features

  * Email is automatically converted to an encrypted PDF 
    (including all attachments). 
  * PDF is encrypted with AES-128. 
  * PDF passwords can be automatically generated per user and 
    sent by SMS. 
  * The recipient can reply with the built-in secure portal. 

Djigzo is open source. There is a "virtual appliance" available with a
full installation that allows you to experiment with or run it.

For more information see [www.djigzo.com](www.djigzo.com)

Best regards,

Martijn Brinkers

---

### Post by wayneandleanne on 2009-02-10
cool

---

### Post by neha srinivas on 2010-02-20
can i include my own encryption method into this gateway???

---

