---
title: "Certificate error while using sudo apt-get update"
date: 2015-08-22
forum: Server Platforms
---

### Post by darkjfman on 2015-08-22
I installed Ubuntu Server 14.04 on an old machine, and I tried to run sudo apt-get update but it's followed by this error message:


    Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease 
    Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg 
    Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release 
    Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources    
    Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources    
    Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources    
    Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources    
    Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources 
        server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none 
    W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources) server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
            
    E: Some index files failed to download. They have been ignored, or old ones used instead.


I attempted the following solutions:


 1. Update dns server to 8.8.8.8 and 8.8.4.4
 2. sudo update-ca-certificates


         Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
         Running hooks in /etc/ca-certificates/update.d....
         done.
         done.


 3. I made sure it's not being done under proxy connection.

---

### Post by howefield on 2015-08-23
Thread moved to the "*Server Platforms*" forum.

---

