---
title: "ftp access"
date: 2008-10-19
forum: Security
---

### Post by Loukisgr on 2008-10-19
Hello everyone,

my question has to do with ftp service and access. I am running a small server as an experiment and i have apache installed. I want some users to access some of it's directories and upload file via ftp. THe problem is that the apache has root as an owner (and i don't want to change that) and i am afraid that if i give full access to the folders that users should access, i will have security vanurability to apache. What should i do? Is symbolic link the key to this problem? Or something else? It is the best if no files are seen from the ftp apart some of the apache folders.

Thanks in advance

---

### Post by Drezard on 2008-10-19
[A] create users using "useradd -d /var/www/public-ftp-apache-folder/ -s /bin/false username". This creates a username that can not login to ssh access but can login to FTP, but it also means they have a home directory of /var/www...

[B] set up chroot jail (I think its called, or else its root jail), that means they can only access their home (/var/www...) when they login to ftp, and thats all they can see aswell. I know vsftpd can do this not so sure about others. Give it a go though. 

[C] Backup data! If someone does actually mess up, then you want an easy way to be able to retrace their steps.

Give that a go. Any problems post results.

Daniel

---

### Post by cdenley on 2008-10-20
If you want FTP users to overwrite web accessible files, you are going to have to give them filesystem permissions to do so. This will compromise a layer of security, but that is the idea of what you're trying to accomplish. Ideally, you would leave everything owned by root, then only you can update files using sudo. If you want your user's to update files, then you just have to prevent their accounts from being compromised. Are you requiring SSL encryption over FTP? Plain, old FTP sends the user's password in plaintext.

---

### Post by Loukisgr on 2008-10-20
Thanks for your answers!!! You are very helpful. I will try all of these.

I know that ftp has no security but ssl needs to be funded right? I mean to create one and they are not cheap as far as i am concerned. Furhtermore i don't own a domain(i use no-ip) so this is a drowback

Thanks again.

p.s If you have found free ssl pls inform me.

---

### Post by cdenley on 2008-10-20
You can create your own self-signed certificate. The first time a user connects, they will not be able to verify your server isn't being spoofed, though.

[https://help.ubuntu.com/community/OpenSSL#SSL%20Certificates%20for%20Server%20Use](https://help.ubuntu.com/community/OpenSSL#SSL%20Certificates%20for%20Server%20Use)
[http://www.akadia.com/services/ssh_test_certificate.html](http://www.akadia.com/services/ssh_test_certificate.html)

---

### Post by Loukisgr on 2008-10-20
you mean the message theat says "this sertificate is invalid or expired" something like that right? The message that you get when a certificate expired but you still using it. I was about to use it as a buckup solution but thanks a lot for the links because it will be a great start. ty again.:)

---

