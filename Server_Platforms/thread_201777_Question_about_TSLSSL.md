---
title: "Question about TSL/SSL"
date: 2006-06-22
forum: Server Platforms
---

### Post by Winblowz on 2006-06-22
I'm currently setting up a mail/http server with Ubuntu. If it is only a home server, to run my website and for my email only, do I need to use encryption (TSL/SSL)?

---

### Post by jvl on 2006-06-22
Depends how sensitive data you have and/or how paranoid you are :)

HTTP passwords without SSL are in cleartext, i.e. easily sniffable.

---

### Post by Winblowz on 2006-06-22
I won't be emailing any really private things, like a credit card number. There isn't really anything that will be too private.

---

### Post by jvl on 2006-06-22
what exactly do you plan to set up? 

webserver: 
what kind of pages will you be serving?
mail server:
sending out only, pop3 or imap server?

---

### Post by Winblowz on 2006-06-22
.html pages for my webserver (if that is what you mean). I'll be setting up an imap mail server with dovecot and postfix/exim.

---

### Post by jvl on 2006-06-22
If you'd be serving static web pages and you won't have any password protected areas of the website, then you probably don't need HTTPS (HTTP over SSL)

When it comes to passwords for imap, there are schemes that encrypt just the password and the rest of the communication is cleartext (CRAM-MD5, APOP etc.). That could be enough. 

If you need privacy, consider using encryption everywhere. I use encryption everytime I could, because I value privacy, but it's everyone's decision. (I.E. SSL VPN when I'm on wifi, SSH logins instead of telnet, pop3s, imaps instead of pop3 and imap ... you get the idea. The performance of today's computers is strong enough, so all traffic could be encrypted. :-)

---

### Post by Winblowz on 2006-06-22
I am still very new to setting up my own mail and web server. The thing that made me not want to use SSL was that it cost money for the SSL certificates. It also seemed very hard to get working. Do you know of anywhere I could get them completely free? I actually wouldn't mind using encryption, but I really don't know if forking out money for this is worth it. Is it hard to make your own certificate?

---

### Post by lamego on 2006-06-22
You can use TSL/SSL without buying a certificate, you can use a self-signed certificate.

---

### Post by herald on 2006-06-23
From what it sounds like, Skip the SSL for the web server.  If it's a public server, people will wonder about the self-signing thing.  Additionally, as was mentioned earlier, if you're not going to host any password protected areas, the task of having to accept the certificate for everyday web content is annoying and excessive.  TSL for the mail is a toss up.  If it's a publicly connected box, without any firewalling infront of it, I'd tend to use the TSL.  Unprotected cleartext passwords on the internet are a scary thought, but if it's not going to contain anything sensitive, I suppose it isn't a big deal.

---

### Post by Winblowz on 2006-06-23
If I did decide to use TSL/SSL for email, where could I get the certificate for free? I would also be very willing to make my own, but I don't know what to do. Could someone please tell me how to make my own?

---

### Post by jvl on 2006-06-23
Check out apache Compile howto at [http://www.tldp.org/HOWTO/Apache-Compile-HOWTO/]("http://www.tldp.org/HOWTO/Apache-Compile-HOWTO/") in section 2.4.2 there is way to create self signed cert.

```

cd /usr/local/ssl/bin

./openssl req -new > new.cert.csr
./openssl rsa -in privkey.pem -out new.cert.key
./openssl x509 -in new.cert.csr -out new.cert.cert \
-req -signkey new.cert.key -days 999

cp new.cert.key /usr/local/apache/conf/ssl.key/server.key
cp new.cert.cert /usr/local/apache/conf/ssl.crt/server.crt

```

Don't forget that the Common name must be FQDN (i.e. [www.ubuntu.com](www.ubuntu.com) if you're hosting [www.ubuntu.com](www.ubuntu.com) :-) )

---

### Post by herald on 2006-06-26
[QUOTE=Winblowz]If I did decide to use TSL/SSL for email, where could I get the certificate for free? I would also be very willing to make my own, but I don't know what to do. Could someone please tell me how to make my own?[/QUOTE]
This example uses Sendmail and Dovecot, but should give you a decent starting place.  You can google what you need to from there:
[http://www.brennan.id.au/12-Sendmail_Server.html#encryption]("http://www.brennan.id.au/12-Sendmail_Server.html#encryption")

---

