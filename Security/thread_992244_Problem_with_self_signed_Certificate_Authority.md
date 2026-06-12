---
title: "Problem with self signed Certificate Authority"
date: 2008-11-24
forum: Security
---

### Post by mozkill on 2008-11-24
I tried creating a self signed CA  and then creating a server certificate (in this case a cert for tomcat SSL with JBoss)  and when the web browser views the certificate it says "The certificate cannot be verified up to a trusted certificate authority."

I don't understand what I did wrong because I did the following:

1. Created a private key and a public CA.crt using openssl.
2. Created a tomcat keystore with a site certificate request.
3. signed the cert request with my CA (domain.test)
4. imported the cert response into my tomcat alias in my keystore
5.  imported the public CA cert into my jssecacerts file in my JVM

---

### Post by Titan8990 on 2008-11-24
You will ALWAYS have that issue with self-signed certificates. Only way around is to have your certificate signed by an authority such as godaddy.com or verisign (very expensive).

---

### Post by mozkill on 2008-11-24
I was missing the step where i needed to also import the public CA root cert into my web browsers root-cert store.

Thanks for the answer.  I guess the site cert was trying to validate against the browsers root cert store.

---

### Post by mozkill on 2008-11-24
> **Titan8990 said:**
> You will ALWAYS have that issue with self-signed certificates. Only way around is to have your certificate signed by an authority such as godaddy.com or verisign (very expensive).


It turns out there wasn't a problem with me creating my own CA authority and my own self signed certs.  It worked great.

I just had to use openSSL to create the CA authority but the rest of it I could do with Java "keytool".

Best of ALL.  Its FREE!

---

### Post by mozkill on 2008-11-24
It turns out that I still have a problem when I try to create a so-called "wildcard certificate".  In that case the browser says the cert is ok except for one small thing:

IE7 reports:
For cert: *.domain.test
"The certificate is intended for the following purpose(s): Ensures the identity of a remote computer"

Firefox reports:
For cert:  *.domain.test
"Certificate belongs to a different site, which could indicate an identity theft." and "*.domain.test:443 uses an invalid security certificate.  The certificate is only valid for *.domain.test (Error code: ssl_error_bad_cert_domain)"

NOTE: I guess I am assuming here that if I have a wildcard cert *.domain.test  that if I access it via the URL "domain.test" that it will validate.

---

### Post by mozkill on 2008-11-24
It turns out my wildcard cert works as long as I dont assume that it will work with the base domain name itself.

I do have one question though:

DigiCert website says:

"A wildcard certificate for *.example.com will secure [www.example.com](www.example.com), mail.example.com, and any other first-level subdomain of example.com. DigiCert's wildcard even secures the base domain itself&#8212;example.com&#8212;something no other wildcard currently offers."


And so, if this is possible for DigiCert, then does anyone know how I can provide this functionality via the typical method of generating your own CA as I explained above?

Question put another way: [COLOR="Red"]Is it possible for me to create my own self signed cert, signed by my own CA, that is a wildcard cert that will also support validation against the base domain name by itself???[/COLOR]

---

### Post by mozkill on 2008-11-24
I still don't know how to make a "base domain wildcard cert" but here is the HOWTO that I posted.  It is the first post in my blog:

[http://codingathome.blogspot.com](http://codingathome.blogspot.com)

---

### Post by stmurray on 2008-11-25
My knowledge of certs is fairly limited but, I believe one of the "gottcha"s with a wildcard cert is that they only match one level-- that is if your wildcard is *.domain.test, then server1.domain.test will work, but server1.subdomain.domain.text will not.  (Not sure if that is your issue or not)

Since you are creating your own CA anyway, I would create each cert as I need them, rather than do wildcards.  They always seem quirky with working with all browsers all the time.  (They also pose a slightly higher security risk in that if the wilcard cert gets compromised, then all your https servers can be spoofed, as well as any new server the attacker wants to put up with.  In organizations that use them, the cert always seems to get copied all over the place....)

---

### Post by mozkill on 2008-11-25
Thanks very much for your kind answer.

I want to use wildcard cert because I am creating a Jboss app with an iFrame that points to another server on my network, and since that involves "cross-site scripting", having the wildcard cert allows the browser to believe both servers are really the SAME site.

I know that I cannot get the wildcard to match sub-domains.  What i am asking is different.   I want "*.domain.name"  to also match  "domain.name" , without needing the "www" prefix.

I know it is possible since DigiCert SSL provider sells wildcard certs that are able to do this.  I am hoping some super smart person on this linux site might know how to do it.

---

### Post by stmurray on 2008-11-26
I believe you are right-- it should work. My guess would be that there is  an issue either with the CA Cert or the wildcard cert (like you have to add some special "extensions" to the CA x509 certificate to allow it to sign wildcard ssl certs or the wildcard cert must have an alternate name, etc).

By the way, I also thought the "same origin policy" that restricts what data from one domain can use for a different domain, (and newer browsers now extend to prohibit named frames from different domains from writing to one another, as  you say) works at the domain level.  This means that [www.target.com](www.target.com) can write to a frame within the same page from server1.target.com.  Am I wrong about that?

---

### Post by tatojo on 2008-11-28
Want to build a pair certificate.cer and privatekey.key with openssl, so that could sign a file using privatekey.key.pem and verify the signature with certificate.cer.pem, but can't achieve the task in ubuntu. Have any suggestion? (BTW, just RTFM).

---

### Post by mozkill on 2009-01-05
> **stmurray said:**
> By the way, I also thought the "same origin policy" that restricts what data from one domain can use for a different domain, (and newer browsers now extend to prohibit named frames from different domains from writing to one another, as  you say) works at the domain level.  This means that [www.target.com](www.target.com) can write to a frame within the same page from server1.target.com.  Am I wrong about that?

Im not exactly sure what you ask but after the browser imports the wildcard cert I am able to do cross site scripting with an iFrame without getting a prompt...

---

