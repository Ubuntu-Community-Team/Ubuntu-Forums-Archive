---
title: "Ubuntu 7.10 server - Qpopper - Problem with self signed certificates"
date: 2007-11-14
forum: Server Platforms
---

### Post by ToniVC1963 on 2007-11-14
Hi,

I recently moved from a Solaris server to an Ubuntu 7.10 one. Most of the migration was easy, but I'm facing a weird problem and I'm clueless...

On the Solaris server I was using Qpopper as a POP3s server, so I decided to use the same software on my new Ubuntu server. But I have a weird problem with certificates. To generate the Solaris server certificate I used the instructions found on the Qpopper web site:

[http://www.eudora.com/products/unsupported/qpopper/faq.html#certs](http://www.eudora.com/products/unsupported/qpopper/faq.html#certs)

so:

/usr/local/ssl/bin/openssl req -new -nodes -out req.pem -keyout /etc/mail/certs/cert.pem

/usr/local/ssl/bin/openssl genrsa -des3 -out ca.key 1024 

/usr/local/ssl/bin/openssl req -new -x509 -days 365 -key ca.key -out ca.crt 

/usr/local/ssl/bin/openssl x509 -req -CA ca.crt -CAkey ca.key -days 365 -in req.pem -out signed-req.pem -CAcreateserial 

cat signed_req.pem >> /etc/mail/certs/cert.pem 


The generated self signed certificate worked fine on the Solaris computer, and POP3s service could be used by any mail client we tried. 

But now I use exactly the same procedure to generate the self signed certificate on my new Ubuntu server and the newly generated certificate is only accepted by Outlook Express, but not by Thunderbird or Mozilla... Outlook Express complains about the certificate not being verified (that's normal), but you can accept it and open the POP3s session normally. But the other mail clients simply state that the certificate is invalid or corrupt and refuse to continue...

The funny thing is that if I use the old self signed certificate from the old Solaris server on my new Ubuntu server... it works with any mail client! (the new server has the same name than the old one). The problem is that the old certificate will expire soon, and the old server will also be shut down forever soon... I'm afraid that when the old certificate expires I won't be able to generate a new valid one on the Ubuntu server that may be accepted by all mail clients...

Any idea?? Am I missing something? Of course I can give you more information if you need it.

Thanks!

Toni

---

### Post by ToniVC1963 on 2007-11-15
Nobody has installed Qpopper on a 7.10 server with SSL??

---

### Post by MJN on 2007-11-15
I could be way off the mark, but I'm sure you're willing to try anything given the impending certificate expiration!

I'm wondering if it might be something to do with the fact that you've changed certificates on what your clients thinks is the same machine. Perhaps the clients are not accepting this (particularly given the lack of a trust path) and are not being particularly helpful with the error. Perhaps they are comparing the new cert with the old one...?

Can you try connecting with a Thunderbird/Mozilla client **that hasn't connected previously to the old server**?

I could well be a million miles away from the truth here, particularly as this would happen every time a new certificate was created. Try it anyway if only to make me look stupid. ;)

Mathew

---

### Post by ToniVC1963 on 2007-11-15
> **MJN said:**
> Try it anyway if only to make me look stupid. ;)


Thanks for you answer, Mathew. No, you definitely will not look stupid, or at least not more stupid than myself!, because I already thought about that possibility and tried with a client computer that never had connected to the server before (in fact, a newly installed one!)... and it showed exactly the same behaviour: Outlook Express accepted the certificate after warning about it's unreliability, but Thunderbird simply refused it saying it was invalid or corrupt...

Since I still have my old Solaris server on, I've created a new certificate with a much larger validity time, just in case. But, still, I would be happier if I could create new certificates on the new Ubuntu server that could be accepted by any e-mail client.

Thanks!

---

### Post by MJN on 2007-11-15
Oh well, it was worth a punt!

I'm at a loss as to what to suggest. Just to clarify, you say you've now created a new longer-life certificate on the Solaris box...? Does the Ubuntu box work using this certificate? If not then surely that points to it not being the certificate at fault but rather the Qpopper config (or version etc) on Ubuntu?

Mathew

---

### Post by ToniVC1963 on 2007-11-16
> **MJN said:**
> Does the Ubuntu box work using this certificate?

I haven't tried it yet, but I think I've found where's the problem:

I did an "openssl verify cert.pem" with both certificates, and while the old one (the one from the Solaris server) gave only the "error 20 at 0 depth lookup:unable to get local issuer certificate" error, the new one gave a couple of different (and weird) ones.

So, I did an "openssl x509 -text -in cert.pem" and saw two relevant differences:

1) Old certificate showed an "Signature Algorithm: md5WithRSAEncryption" while new one showed "Signature Algorithm: sha1WithRSAEncryption". (I don't think it's relevant...)

2) I observed that on the old certificate I used different Common name (CN) information when creating the certificate and the CA certificate, while on the new one I used the same info!

So I tried: I created a new certificate on the new Ubuntu server giving different Common names when creating both cert.pem and ca.crt, and the resulting cert.pem verification gives now the same result as the old one! So, I think now it will work. When I can test it I'll make you know ;)

Qpopper FAQ says that the info you enter when you create the CA certificate is not relevant, but I think they should add: "... providing you use different Common names!".

As I said, I haven't tried it yet, but I think that was the problem. It makes sense, or at least I hope so! I will test it next week.

Toni

PD: I hope you can understand my explanation... English is not my native language...

---

### Post by MJN on 2007-11-16
I wish I could share your confidence...! (I'm not so sure it'll work but reserve the right to come back and edit this post to say 'yeah that'll be it'!!)
 
By the way, it had never occured to me that English wasn't your native language so no need for the apologies!
 
Mathew

---

### Post by ToniVC1963 on 2007-11-16
Well, finally I couldn't resist, I've tested it right now, and... IT WORKS!!! :) The new certificate created on the new Ubuntu server works with all clients! EUREKA! ;)

So, to resume, the only change I've made is entering different Common name information when creating both the main certificate and the CA's one. If you enter the same Common name in both cases, the resulting "wrong" certificate will be accepted by Outlook Express, but not by Thunderbird (to name some). Weird...

Maybe I should contact Qpopper developpers and ask them to add this warning to their FAQ?

> **MJN said:**
> By the way, it had never occured to me that English wasn't your native language so no need for the apologies!

Oh, thanks! O:)

Toni

---

### Post by MJN on 2007-11-16
Yeah I knew it would work...
 
(Where's that edit button? ;))
 
Mathew

---

### Post by ToniVC1963 on 2007-11-16
> **MJN said:**
> Yeah I knew it would work...
 
(Where's that edit button? ;))


Hahaha! That's fun! :D

Just to close this thread, I'll add two examples of what I did:

**** FIRST EXAMPLE: "wrong" certificate:

I used the following procedure to creat the certificate:

> 
[COLOR="Blue"]
openssl req -new -nodes -subj '/C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/**CN=EEEE**/emailAddress=FFFF' -out req.pem -keyout cert.pem

openssl genrsa -des3 -out ca.key 1024

openssl req -new -x509 -days 365 -subj '/C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/**CN=EEEE**/emailAddress=FFFF' -key ca.key -out ca.crt

openssl x509 -req -CA ca.crt -CAkey ca.key -days 365 -in req.pem -out signed-req.pem -CAcreateserial

cat signed-req.pem >> cert.pem
[/COLOR]


Please note that in both cases I use CN=EEEE. The output of the "openssl verify cert.pem" is:

> 
[COLOR="Blue"]
cert.pem: /C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/CN=EEEE/emailAddress=FFFF
error 18 at 0 depth lookup:**self signed certificate**
/C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/CN=EEEE/emailAddress=FFFF
error 7 at 0 depth lookup:**certificate signature failure**
8705:error:0407006A:rsa routines:RSA_padding_check_PKCS1_type_1:block type is not 01:rsa_pk1.c:100:
8705:error:04067072:rsa routines:RSA_EAY_PUBLIC_DECRYPT: padding check failed:rsa_eay.c:699:
8705:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:
[/COLOR]


Note the two error messages. Even with these errors, this certificate is accepted by Outlook Express, but not by Thunderbird.

**** SECOND EXAMPLE: "good" certificate:

I use almost exactly the same procedure, but check the bold items!:

> 
[COLOR="Blue"]
openssl req -new -nodes -subj '/C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/**CN=EEEE**/emailAddress=FFFF' -out req.pem -keyout cert.pem

openssl genrsa -des3 -out ca.key 1024

openssl req -new -x509 -days 365 -subj '/C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/**CN=ZZZZ**/emailAddress=FFFF' -key ca.key -out ca.crt

openssl x509 -req -CA ca.crt -CAkey ca.key -days 365 -in req.pem -out signed-req.pem -CAcreateserial

cat signed-req.pem >> cert.pem
[/COLOR]


Nothe the use of two different Common names (CN=), one for the server certificate itself (EEEE) and a diferent one for the CA certificate (ZZZZ). With this simple change, the output of the "openssl verify cert.pem" is now:

> 
[COLOR="Blue"]cert.pem: /C=ES/ST=AAAA/L=BBBB/O=CCCC/OU=DDDD/CN=EEEE/emailAddress=FFFF
error 20 at 0 depth lookup:unable to get local issuer certificate
[/COLOR]


That is, only the expectable "unable to get local issuer certificate" error. This certificate is accepted by ALL mail clients.

Of course, instead of AAAA, BBBB, etc. I used real information. For the "good" certificate I made EEEE to be the real name of the Ubuntu server, and ZZZZ anything different from it.

---

