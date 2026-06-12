---
title: "FTP Server and Windows"
date: 2009-01-27
forum: Server Platforms
---

### Post by nightmare0 on 2009-01-27
Ok hello everyone. Im trying to get a FTP server setup, thats going just fine :) Here's the problem.... the files that the FTP server is meant to access is on a windows share! I'm having the hardest time trying to get an FTP Server to be able to get to these files! Any ideas?

---

### Post by starling on 2009-01-28
More info?
how is the FTP server meant to access the samba share? do you want to make the samba folder the FTP folder, or sync the two? What is your FTP software?

---

### Post by nightmare0 on 2009-01-28
The samba share is on a windows Domain with an Active Directory Domain and I want the FTP to be going directly to that folder so that my users are directly editing their files (that and I dont have that kind of hard drive space on my FTP server), so I will have to have a user that the server can connect with that does have full access to everything, and as far as my FTP server goes... it was ProFTP but i started having issues with MySQL authentication so I'm going to try PureFTP, maybe. Which one would work better for this situation or does it not really matter?

---

### Post by tomwerner470 on 2009-01-28
The main issue here is do you have one share that multiple users need to access or are you trying to expose user home directories via ftp? Both are doable, but without some trickery the second one will be a pain to maintain.

We have a simliar setup at my place of work where want to share a single samba share to mulitple users over the web using ftp, to do this, we created a new ftp user and mounted the share in the root of that new user's home directory.

I have used vsftpd for this as there seems to be quite a bit of documentation about and it supports SSL Ftp - which is important if your ftp traffic is going outside your lan.

If you have some details about the number of shares, I may be able to help you with the finer details.

Regards,

Tom

---

### Post by nightmare0 on 2009-01-28
> **tomwerner470 said:**
> The main issue here is do you have one share that multiple users need to access or are you trying to expose user home directories via ftp? Both are doable, but without some trickery the second one will be a pain to maintain.

We have a simliar setup at my place of work where want to share a single samba share to mulitple users over the web using ftp, to do this, we created a new ftp user and mounted the share in the root of that new user's home directory.

I have used vsftpd for this as there seems to be quite a bit of documentation about and it supports SSL Ftp - which is important if your ftp traffic is going outside your lan.

If you have some details about the number of shares, I may be able to help you with the finer details.

Regards,

Tom
Hi Tom, I'm not sure I completely understand what you mean about 'exposing home directories' but I'm assuming that you are talking about each user having separate folders for storage. If so , the answer is that I need to be able to expose their 'home' directory which is a file share on a Windows File Server. And to answer your question about how many people/users... about 400+ :)

---

### Post by nightmare0 on 2009-01-31
Anybody have a solution? :(

---

### Post by HermanAB on 2009-01-31
Hmm, note that FTP is designed to use very little server resources.  It reverses the load onto the client.  So in this case, the best solution is to run the FTP server on the Windows machine.  All you need to do is install Filezilla Server on Windows.

Cheers,

Herman

---

### Post by nightmare0 on 2009-01-31
> **HermanAB said:**
> Hmm, note that FTP is designed to use very little server resources.  It reverses the load onto the client.  So in this case, the best solution is to run the FTP server on the Windows machine.  All you need to do is install Filezilla Server on Windows.

Cheers,

Herman

Unfortunately there's an exchange server setup for web access and we were going to host the FTP server on a separate server to reduce load (as we have multiple Virtual Servers hosted there also) and because we were planning on using MySQL for Authentication, unless with a windows FTP the User Authentication can come from the Active Directory! (can it? I've never used Windows for anything web/ftp related.. I don't like IIS)

---

### Post by nightmare0 on 2009-02-01
Please anybody this is due to be in production very soon.

---

### Post by tomwerner470 on 2009-02-03
Unfortunately, this out of my depth on ftp setups, however, when I had a look around proftpd should be able to do virtual users from ldap (active directory).

One question here though is why do you need the ftp access? If it is for users to access files remotely, have you considered VPN?

---

### Post by nightmare0 on 2009-02-13
I have just that I have no experience there... can you redirect me to the correct forums for that... I'm pretty sure that this is a ubuntu forum ;) probably won't find too much help here! (with windows vpn I mean)

---

### Post by HermanAB on 2009-02-14
Setting up a VPN is difficult, especially when compared to FTP.  I won't recommend that right now.

FTP can be secure if you separate the upload and download directories.  That is how all public anonymous servers work.  The other way to secure things, is to use ssh-server which provides SFTP over port 22.  The Windows FileZilla client can do SFTP.

Cheers,

Herman

---

### Post by nightmare0 on 2009-02-14
I'm not so concerned about secure uploading and downloading more than I am of being able to use my Windows DC to authenticate  the FTP Users and get their 'root' to be their folder on yet another server on the network, which the FTP server needs to have a password to connect to...

---

### Post by linux_tech on 2009-02-14
You should be able to configure PAM to use kerberos for authentication

---

### Post by nightmare0 on 2009-02-14
how would I go about configuring that? PAM and ProFTP/PureFTP either way...

---

### Post by nightmare0 on 2009-02-17
PAM? anyone? :(

---

### Post by HermanAB on 2009-02-17
See this for some ideas:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by nightmare0 on 2009-02-17
> **HermanAB said:**
> See this for some ideas:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman
 
Thanks so much! This may solve a HUGE part of my problem! 
Thanks again Herman!

---

