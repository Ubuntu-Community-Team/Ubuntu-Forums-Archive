---
title: "security certificate from 'localhost' instead of domain"
date: 2007-04-11
forum: Server Platforms
---

### Post by nucklebone on 2007-04-11
I've set up a nice little mail server (secure), but I keep getting this message every time I check my mail:

[COLOR="DarkRed"]You have attempted to establish a connection with
"host.yourdomain.com". However, the security certificate
presented belongs to "localhost"...[/COLOR]

Not a deal breaker, but rather annoying to come back to my computer and find that it was waiting for a response, instead of fetching my mail as I 'multi-task'.

When I created the certificates on my mail server, I used my domain name.

I am by no means a SASL/TSL genius, so I'm probably missing something simple. Maybe the problem is on the client end?

---

### Post by MJN on 2007-04-11
Your client is fine and doing what it's supposed to be doing i.e. pointing out the mismatch of server and certificate.

What mail server are you using? Given you're talking about 'checking your mail' presumably you are actually connecting to a POP/IMAP server (I would call an MTA like Postfix a mail server but as long as we're talking the same thing it doesn't really matter).

Are you sure the certificate it's presenting is the certificate *you* created for it (i.e. not some default, if such a cert exists). Does your client actually let you view the supplied certificate? It might give you a clue as to what certificate is being sent, and whether it's the one you thought....



Mathew

---

### Post by nucklebone on 2007-04-13
It is Postfix on an Ubuntu Edgy 6.1 usung IMAP with tsl and sasl enabled.

When I was setting up the certificates, I gave real answers to the questions that were asked on-screen ie. name, department, emails, etc... and used my real domain name.

I'm not sure how to tell if a default cert is being read, or how to change defaults if it is. I'm a little new to this "roll your own server" business.

Oh, I notice too, that when I restart Apache, Apache spits up a comment about not being able to determine the fully qualified domain name, so it uses 127.0.0.1. Sound related?


Thanks,
n

---

### Post by MJN on 2007-04-13
Given you said the certificate error occurs when you *check* your mail this points to the issue being with your IMAP server - which are you using? Dovecot? Courier? Some other...?

It could well be using its own certificates by default i.e. not using your 'custom' ones.

If you let us know which IMAP server you're using, your config file, and perhaps also where you've got your certs stored currently I'm sure we'll have you up-and-running in no time.

The Apache error is unrelated - that's probably occurring because you don't have a ServerName directive listed in your config. In particular, Apache needs to know what *it's* called and in the absence of you telling it it's taken on the name (IP address) of 127.0.0.1. Search the archives as this is quite a common one...

Mathew

---

### Post by nucklebone on 2007-04-14
I'm using Curier.

After reading your post, I looked in /etc/courier/imapd.cnf and found this line:
```
CN=localhost
```

Is that my problem?

My 'custom' certs are located in /etc/postfix/ssl/

To clarify, I used the tutorial located here: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5) to set up postfix. Specifically these instructions, verbatim:
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

---

### Post by MJN on 2007-04-14
But those are for your Postfix certificates. Sure, you can use the same certs for Courier too but you need to tell Courier where they are.

I've only ever used Dovecot but I'm sure someone familiar with Courier can tell you how to configure it (or check the manual/config etc).

Mathew

---

### Post by nucklebone on 2007-04-14
Hrrmmmm... starting to see the error of my ways. Thanks for pointing me in the right direction.

---

### Post by nucklebone on 2007-04-14
Got it!

I didn't realize it was Courier that supplied the cert in question. I had thought it was a matter of connection with Postfix. But after seeing your line of logic I figured it out. Created the correct certs and Mail is working like I wanted it to.

Thanks!

---

### Post by MJN on 2007-04-14
Well done!

 :guitar:

---

### Post by kmoffat on 2007-05-01
> **nucklebone said:**
> Got it!

I didn't realize it was Courier....Created the correct certs and Mail is working like I wanted it to.

Thanks!

What was the method you used to create courier certs?

(I have the same error.)

---

### Post by cjsimmons on 2007-09-09
> **nucklebone said:**
> 
[COLOR="DarkRed"]You have attempted to establish a connection with
"host.yourdomain.com". However, the security certificate
presented belongs to "localhost"...[/COLOR]


I'm getting this error and was wondering if it's possible to edit/replace the certificate with the correct details.

---

