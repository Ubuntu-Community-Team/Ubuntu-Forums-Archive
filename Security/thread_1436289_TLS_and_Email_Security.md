---
title: "TLS and Email Security"
date: 2010-03-22
forum: Security
---

### Post by Chrisso101 on 2010-03-22
More a general question than specifically ubuntu but can anyone say if an email is sent using TLS it will definitely be received by the intended recipient unread and unchanged?

The reason I ask is that I've just set up Postfix to submit messages through my Gmail account on the Gmail server smtp.gmail.com:587 using TLS and CA certificates, since my ISP doesn't do TLS/SSL for sending or receiving mail (according to ehlo). Just for a bit of fun really because I don't send any confidential emails.

It's just that, as I said, my ISP's mail submission and delivery is not secure yet I can submit "secure" messages through the gmail smtp server that are addressed to myself at [EMAIL="chris@myinsecureisp.com"]chris@myinsecureisp.com[/EMAIL] and receive said messages. So somewhere along the line the encryption is getting dropped and the message is being forwarded onwards and delivered in the clear.

Does this mean that my ISP, and possibly others, could read my messages that had started their journey via a secure connection?

---

### Post by cdenley on 2010-03-22
I don't think messages ever get encrypted between servers. I think e-mail will always be sent plaintext, unless the sender and recipient use the same e-mail service.

---

### Post by OpSecShellshock on 2010-03-22
If copies of messages that you send are kept on servers that are outside of your control, they can be read by whoever owns the servers. That's not to say they will, but they can.

---

### Post by slowth5 on 2010-03-22
> **Chrisso101 said:**
> Does this mean that my ISP, and possibly others, could read my messages that had started their journey via a secure connection?

Yes. You are correct in assuming email is plain text sent in the clear. Your connection with the gmail server might be encrypted, but once it leaves the gmail server, it will most likely be in the clear. 

Public key encryption is one way to secure email.

---

### Post by Chrisso101 on 2010-03-23
Thank you all for that. It's good to keep these things in mind.

---

### Post by rookcifer on 2010-03-23
TLS is just for secure *authentication*.  It will not encrypt the e-mail end-to-end.  For that you and your contact will need to either pre-negotiate keys (symmetric cryptography) or use public keys (asymmetric cryptography).  Gnupg is in the repos and will accomplish either.

---

### Post by augustsalbert on 2010-03-24
[COLOR=Black]I think most Internet-based e-mail systems use a combination of three main protocols: SMTP (for message delivery) and POP and IMAP (for message retrieval). TLS is application protocol-independent. TLS security is to be considered casual encryption  of from an  Msen mail server to your PC.  It did/can not cover the entire conversation from sender  to recipient.  The only protection it provides is from sniffers on the ethernet/phone line. To get complete protection, it needs to be used in conjunction with PGP, which encrypts the contents of the message. [/COLOR]

---

### Post by yeleek on 2010-03-26
PKI is your friend.

Get yourself a free certificate from somewhere like here:

[http://www.instantssl.com/ssl-certificate-products/free-email-certificate.html](http://www.instantssl.com/ssl-certificate-products/free-email-certificate.html)

then presuming you are sending to someone who also has a certificate you can encrypt the email with their public certificate, only their private certificate will be able to decrypt it i.e. confidentiality.

Alternatively - 'sign' (encrypt a hash) of an email you send with your private key, anyone you send it to can use your public key to confirm that it was you that encrypted it.

Idea being - private key is known only to you, public key is known to everyone.

---

