---
title: "Certificate on server"
date: 2018-04-05
forum: Security
---

### Post by derrickward on 2018-04-05
[COLOR=#333333][FONT=&quot]Hello
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have installed Mahara (Eportfolio system) on ubuntu 16.04[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I need to install a ssl certificate to allow outside access to mahara.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Can anyone advise on the best way to manage the certificate.  Is there an application that I can use to manage the installation of the certificate OR do I just install it on ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]What is the best way to get the certificate on the server.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]The DNS entry will be created and a public IP will be used so we have that covered.  Just need to work out how to install the certificate.
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have a certificate that we have purchased from a 3rd party.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I am trying to work out how to upload the certificate to the server and determine the process for obtaining the key.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I assume I have to re-key the certificate with my 3rd party provider.  If so, how do I get the Certificate Signing Request (CSR) to allow me to re-key the certificate.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Once I have re-keyed the certificate how would I go about uploading the certificate to the server.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]thanks [/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Derrick[/FONT][/COLOR]

---

### Post by tamlee on 2018-04-19
you can more description ?

---

### Post by sevendogsbsd on 2018-04-24
What do you mean "re-key" the certificate? When a CSR is created, the private key is created and you must protect that on the server with file permissions (NEVER SHARE IT WITH ANYONE). The CSR gets sent to the 3rd party certificate authority who then issues your certificate public key. You install the certificate public key, and any necessary root and CA certs in the chain into whatever software you are using (Apache, Tomcat, etc) and configure the software to use the certificate.

---

