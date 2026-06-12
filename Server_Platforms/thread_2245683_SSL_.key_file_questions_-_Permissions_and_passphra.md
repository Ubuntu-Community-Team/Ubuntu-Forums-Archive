---
title: "SSL .key file questions - Permissions and passphrase."
date: 2014-09-25
forum: Server Platforms
---

### Post by Coder68 on 2014-09-25
I have a new wildcard SSL cert with godaddy. I have imported it into a Windows server and exported the private key into a .pfx file. 

I need to get the .key file and this is what I found to do it:

**xport the private key** file from the pfx file 
openssl pkcs12 -in filename.pfx -nocerts -out key.pem 

**Export the certificate** file from the pfx file
 openssl pkcs12 -in filename.pfx -clcerts -nokeys -out cert.pem [B]

Remove the passphrase [/B]from the private key
 openssl rsa -in key.pem -out server.key


1. Why would I remove the passphrase from the private key? (I am guessing so it can be used).
2. What permissions should this .key file have? The about to expire key has 400 for permissions.

Thank you,

C68

---

### Post by Coder68 on 2014-09-25
After a lot more digging, I think I found the answers.

1. It is so we can reboot without entering the passphrase.  ([https://wiki.apache.org/httpd/RemoveSSLCertPassPhrase](https://wiki.apache.org/httpd/RemoveSSLCertPassPhrase))
2. 500 on the folder and 400 on the files is recommended. ([http://serverfault.com/questions/216477/what-should-be-the-persmissions-of-apache-ssl-folder](http://serverfault.com/questions/216477/what-should-be-the-persmissions-of-apache-ssl-folder)) I can't find the original doc he is talking about though.

---

### Post by Coder68 on 2014-09-25
I am getting an error when I try to remove the password from the certificate. Unable to load private key. How do I pass the password to this? I have tired several things I found on the net and they did not work.

openssl rsa -in cert.pem -passin pass:*passwordx *-out server.key <-- same error

Can someone point me in the right direction please?

p.s.
This is a sha2 key if that makes any difference.

---

### Post by Coder68 on 2014-09-26
It appears there is no private key. I exported the private key from Windows with a password, yet it is not in the privatekey.pem file!

Thoughts?

---

### Post by Coder68 on 2014-09-26
I found this command which DOES export the private key in the pem file.

> pkcs12 -in <cert.pfx> -out <cert.pem> -nodes 

Then I ran this, which made the key file.

> openssl rsa -in cert.pem -passin pass:*passwordx *-out server.key

Now to test and see if it works.

---

