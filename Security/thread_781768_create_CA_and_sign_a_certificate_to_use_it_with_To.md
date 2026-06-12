---
title: "create CA and sign a certificate to use it with Tomcat"
date: 2008-05-04
forum: Security
---

### Post by lulon on 2008-05-04
Hi, I need help with this, please, I'm doing my final project degree.

I want to create a CA to sign my certificate. This is what I do:

1. I've created my certificate with keytool. 

2. With this certificate I've created my CSR

3. I've created a new CA with Openssl:

[INDENT]./CA.pl -newca

[LIST]
[*]a name
[*]secret passphrase for the private key
[*]more information
[/LIST][/INDENT]

4. I've rename the CSR with the name "newreq.pem" and then I've signed it.

[INDENT]./CA.pl -sign[/INDENT]

5. Now, I have the new certificate signed, "newcert.pem"

6. What do I have to do for use them with Tomcat??
I think I have to install the CA certificate and the signed certificate, but how??

Thanks.

---

### Post by cbobb@alinean.com on 2008-05-08
If you are using tomcat 6.x

Generate the cert / csr creation:

[http://www.digicert.com/csr-creation-tomcat.htm](http://www.digicert.com/csr-creation-tomcat.htm)

Install the generated cert into the Tomcat Keystore:

[http://www.digicert.com/ssl-certificate-installation-tomcat.htm](http://www.digicert.com/ssl-certificate-installation-tomcat.htm)

Hope that helps.

---

### Post by datajelly on 2008-08-15
I had originally bumped into some problems getting SSL installed in Tomcat. I think basically what you'll need to do is convert the .pem file into a .p12 file. I've written up the steps I took to get it running. It was originally done for Windows (ugh), but we've since moved it over to Ubuntu with no problems, I hope you might find it helpful:

[http://blog.datajelly.com/2007/06/adding-ssl-to-tomcat.html]("http://blog.datajelly.com/2007/06/adding-ssl-to-tomcat.html")

---

