---
title: "Sign a file with SSL server certificate"
date: 2011-03-12
forum: Security
---

### Post by shoot2kill on 2011-03-12
Hi, I have got a file (plaintext.txt) which I need to sign with a SSL certificate. I have been given a private key (private.pem) to use in the certificate, but don't know how I'd go about signing the file.

---

### Post by shoot2kill on 2011-03-14
Bump!

---

### Post by akakingess on 2011-03-14
I would be interested to see if you can 'sign' a file with an SSL certificate, so I will stay posted to see the outcome, sorry I can't be of any assistance as this has peeked my interest as well..

---

### Post by BkkBonanza on 2011-03-14
You can use openssl to do this to generate a signed text in S/MIME format.

eg.
openssl smime -sign -signer mycertkey.pem -in text.txt -out signtext.txt

This assumes a cert file with key embedded but if the key file is seperate from the cert then you would use -inkey and -certfile. It will prompt for a passphrase for the key file unless it was generated without one.

---

### Post by shoot2kill on 2011-03-14
So, if all i have is a private key, do i have to create a certificate in order to sign the file? or can i just do it with the private key?

---

### Post by BkkBonanza on 2011-03-14
I haven't tried that but you could see if the pem file will work for the -signer option. If not then I guess you need to have both or a combined one.

I use TinyCA to manage my own CA for some stuff I do and it has the option of exporting either type of pem file. It could be that the private key you have is actually both in one. (You can view it in a text editor to see if there is both sections - the section headers are human readable).

I may be getting mixed up or not sure what you want but I think the general usage is to sign with your OWN key and the recipient's CERT. This confirms to them that you signed it and it's only meant for them. They can verify you signed it by checking against your CERT (which they should have). However, that's all to do with email certs and I suppose server certs may be used differently. 

Anyway, I did test that command above before posting it and with my combined cert (size about 3.1k and has two sections inside, one called certificate and one called private key) it did successfully sign the text and output it with a mime header and an encoded block appended. 

I typically use Enigmail in Thunderbird for doing this so it's a bit off my usual path. I was happy to see that it does work.

(You should be able to generate a cert with openssl as well which could be used for the signing)

---

### Post by BkkBonanza on 2011-03-14
I was just looking into signing a bit more with openssl. If you want a more generic non S/MIME approach then it appears you can do it by creating a digest and signign that. Then you pass that along with the data to a user who can verify it.

See this article here for details. This isn't a usage that I've done.
[http://www.codealias.info/technotes/openssl_rsa_sign_and_verify_howto](http://www.codealias.info/technotes/openssl_rsa_sign_and_verify_howto)

---

