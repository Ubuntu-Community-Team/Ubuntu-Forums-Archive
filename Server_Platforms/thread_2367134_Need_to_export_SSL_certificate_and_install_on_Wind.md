---
title: "Need to export SSL certificate and install on Windows"
date: 2017-07-26
forum: Server Platforms
---

### Post by callyozzie on 2017-07-26
[B][SIZE=3]To give you some background on what I was doing...[/SIZE]
[/B]
I have installed OwnCloud on my Ubuntu Server using this guide: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-owncloud-on-ubuntu-16-04Lets](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-owncloud-on-ubuntu-16-04Lets) 

While doing that I also used this guide to help me encrypt Apache2 using 'Lets Encrypt': [https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-16-04)

These all worked fine.
[SIZE=3]

**My Issue...**[/SIZE]

I now what to use the OwnCloud file server to store my 'SafeInCloud' password manager file. SafeInCloud shows this message when entering the details of the server, and doesn't let me add it.

[IMG]http://i.imgur.com/Ft3te1a.png?2[/IMG]

I have looked online to solutions but can't seem to find one that lets me export the right files.

In the diectory /etc/letsencrypt/live/mydomain.com i have these files:
[LIST]
[*]cert.pem
[*]chain.pem
[*]fullchain.pem
[*]privkey.pem
[*]README
[/LIST]

I don't have the best idea of this kind of stuff so I might not be searching the right thing to solve this.

Thanks in advance.

---

### Post by darkod on 2017-07-26
You need to research how to convert it to .pfx file. Usually that file is protected by password (that you choose during the conversion/export) and can be imported on windows. I think you would use openssl command for that. Try google, there should be plenty of tutorials and advice.

PS. This looks to be one example:
[https://stackoverflow.com/questions/808669/convert-a-cert-pem-certificate-to-a-pfx-certificate](https://stackoverflow.com/questions/808669/convert-a-cert-pem-certificate-to-a-pfx-certificate)

---

### Post by Habitual on 2017-07-26
[https://www.sslshopper.com/how-to-move-or-copy-an-ssl-certificate-from-one-server-to-another.html](https://www.sslshopper.com/how-to-move-or-copy-an-ssl-certificate-from-one-server-to-another.html) may help.

---

### Post by callyozzie on 2017-07-26
Thank you for the responses, 

By using this command: openssl pkcs12 -inkey privkey.pem -in fullchain.pem -export -out Output.pfx
I was able to export it to a pfx file.


Using this link: [https://www.sslshopper.com/move-or-copy-an-ssl-certificate-from-an-apache-server-to-a-windows-server.html](https://www.sslshopper.com/move-or-copy-an-ssl-certificate-from-an-apache-server-to-a-windows-server.html)

I installed the certificate onto my windows machine, but when I go to add the server in SafeInCloud it still comes up with this error message as before:

[IMG]http://i.imgur.com/75B1Z0K.png[/IMG]

---

