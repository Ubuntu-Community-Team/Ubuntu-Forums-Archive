---
title: "OpenVPN create and sign certificate question"
date: 2015-10-05
forum: Security
---

### Post by Drenriza on 2015-10-05
Hi all

I am _**not**_ a OpenVPN master, so i am hoping for some feedback / guidance on my question.
Where the below is my current understanding from reading different tutorials / threads on the web.

When creating a new certificate / key for a new OpenVPN user with easy-rsa, you first create the server side
[LIST]
[*]certificate 
[*]key file 
[*]csr file 
[/LIST]
The certificate and key file is than copied to the client over a secure (ssh) connection, where the client than create his / her private
[LIST]
[*]csr file 
[*]key file 
[/LIST]
The csr and key file are than securely copied back to the server, where the server sign the csr file to create a crt file that is
than copied yet again back to the client?

If the above is correct, than how does the VPN authenticate the client?? (totally guessing here)
You tell the VPN server, "Hey, i would like to connect to you and my certificate is xxxxx".
Than if the user exist, you're asked to enter your password. Which i presume is the password for the key file created by the server.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

For older keys information such as the encryption type used for the connection is from my understanding written in the key file?
Proc-Type:
DEK-Info:

But where is it written what newer keys use when this is not written in the key file?

**Grey areas**
[LIST]
[*]What is the purpose of the server side csr file?
[LIST]
[*]If a client side csr file is created and copied to the server, to sign it and create the crt file. 
[/LIST]
  
[*]What is the purpose of the client private key file? 
[*]Can you create all the files needed for a new VPN user locally on the server, and copy the files over directly without having to create client side files?
[LIST]
[*] .crt file 
[*].key file 
[*].certificate file
[LIST]
[*]What is the dis-advantage to this approach? 
[/LIST]
   
[/LIST]
  
[*]What is the difference between easy-rsa/build-key and build-key-pass?
[LIST]
[*][B]Similar to build-key, but protect the private key with a password
????
[/B]
[/LIST]
  
[*]A ; in the OpenVPN server configuration file, is that the same as a # (comment)? 
[/LIST]

Hoping someone can cast some light on the subject for my understanding.

Thanks in advance
Kidn regards

---

### Post by Skaperen on 2015-10-05
a CSR file is a Certificate Signing Request.  you can self-sign it (making a "self signed certificate" sometimes called a "selfie") or have a CA (Certificate Authority) sign it.

---

### Post by Drenriza on 2015-10-05
> **Skaperen said:**
> a CSR file is a Certificate Signing Request.  you can self-sign it (making a "self signed certificate" sometimes called a "selfie") or have a CA (Certificate Authority) sign it.

So on the server that created the certificate / key you can say through easy-rsa that the server shall self-sign the created csr file, that in turn creates a crt file?
How does one do that?

---

