---
title: "My FTP Requirements"
date: 2007-05-18
forum: Server Platforms
---

### Post by Arinux on 2007-05-18
Hello everyone,

I am planning to build a small enterprise ftp server on ubuntu

I am a complete ubuntu noobie and would like some guidance from the experts :KS

Okay this is what i have in mind

Which ftp server to use is my first query? While going through some discussions I found out that vsftpd is a  good choice. So need advice on this

Second thing i want a folder where i will host files which user's will access

I don't want annoymous login

I want one local user to be created who can access only that folder that too on read only mode

Now the clients will work on mac , windows etc and should be able to access those files and download them using that local user name and password

User's should be able to download file and not upload.

I tried to view some topics but could not get the entire setup of what I want.

What are the possible ways of making this more secure?

Regards

---

### Post by bukwirm on 2007-05-18
Reading the server's configurations files and the documentation should get you off to a pretty good start.

---

### Post by fyl2u on 2007-05-18
All of the things you've mentioned are in the config file for vsftpd, so it should suit your needs.

I'm an Ubuntu noob too, less than a week's experience, but I've set up a 10-user FTP server using vsftpd this week and its working a treat.

Have you installed vsftpd yet?

If not, install by typing this in the terminal:  "sudo aptitude install vsftpd" (without the quotes)

You can then read the manuals by typing: "man vsftpd" for the info on the actual daemon and "man vsftpd.conf" for the info about using the config file.

When you're ready to edit the config file to your needs, bring up another terminal window (by using 2 terminal windows you can edit the config file while still reading the manual file in the first terminal).

You'll need to navigate to the config file first.  Do this by typing: "cd /etc".  /etc is the directory that the config file is kept in.

Once there, type "sudo pico vsftpd.conf" to edit the config file.  Save the file by pressing CTRL-O.

Then you're ready to start the daemon: "sudo /etc/init.d/vsftpd start "

---

### Post by fyl2u on 2007-05-18
P.S. [https://help.ubuntu.com/7.04/server/C/ftp-server.html](https://help.ubuntu.com/7.04/server/C/ftp-server.html)

---

### Post by fyl2u on 2007-05-18
In the config file, check out the "chroot" lines - this will allow you to restrict the user's access to ONLY the ftp folder.

This gets around the Internet Explorer 7 "bug" that shows the user a directory listing of your root directory instead of showing the proper FTP folder.

---

### Post by Arinux on 2007-05-18
Thanks a lot guys

I will try this and let you all know if i face any problems

:popcorn:

Regards

---

### Post by Arinux on 2007-05-18
Hello all , can some one give me more details on local_umask , what does it do? Is it required for the type of setup I am looking for? Thanks in advance

:confused:

---

### Post by fyl2u on 2007-05-18
> **Arinux said:**
> Hello all , can some one give me more details on local_umask , what does it do? Is it required for the type of setup I am looking for? Thanks in advance

:confused:

Mine's just set to the default 077.

Try it at that, and if you have problems, try it at 022 instead :-)

---

### Post by Arinux on 2007-05-21
Hey everyone , the basic ftp server works fine ! Now one issue with ie7 , when i open it it shows the entire filesystem , as mentioned i have to modify the chroot option, but i am not sure how to do it ! Can any one guide me through this ? I read the documentation but could not understand the concept of chroot jail and even it was mentioned that it has security risks 

And in normal browsers when i click up to higher level directory it browses up which I don't want. I think again this has to do something with chroot !

Looking forward for solution :p

---

### Post by fyl2u on 2007-05-21
> **Arinux said:**
> Hey everyone , the basic ftp server works fine ! Now one issue with ie7 , when i open it it shows the entire filesystem , as mentioned i have to modify the chroot option, but i am not sure how to do it ! Can any one guide me through this ? I read the documentation but could not understand the concept of chroot jail and even it was mentioned that it has security risks 

And in normal browsers when i click up to higher level directory it browses up which I don't want. I think again this has to do something with chroot !

Looking forward for solution :p

# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
# chroot_list_file=/etc/vsftpd.chroot_list

This is how I got around the problem.

---

### Post by frodon on 2007-05-21
If it's for professional use i strongly recommend you the use of encryption because the standard FTP protocol send username and password in plain text so it's not really hard to get the username and password for someone who really want to know them.

As for the FTP server choice i don't know vsftpd so i can't tell you anything about it, i'm used to proftpd which is also a well known and often used FTP server, it's the server used by sourceforge for example.
If you have time to read i wrote a small guide to start with proftpd :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by Arinux on 2007-05-22
Thanks for the update Frodon, I was about the ask the same thing. So the server is up and running and trying out some load testing ;)

How can we secure a ftp server , like in vsftpd.conf we have the option of ssl , does that help? 

Doesn't know much of security, so would like some guidance in this area

Regards

---

### Post by Arinux on 2007-05-23
Humm , I tried enabling ssl , but now on client side , ftp is not accessible ! What could be the reason for this? Any way to fix it , can someone help me to encrypt the authentication process.Looking forward for replies.....

Regards
:D

---

### Post by frodon on 2007-05-23
I detailed how to enable TLS encryption in my guide for proftpd but i don't know for vsftpd, i'm sure that you can find some good documentation/tutorial for vsftpd googling a little bit.

---

### Post by Arinux on 2007-05-25
Hey all,

I found a good link to configure vsftpd with tsl and ssl suppot

[http://wiki.vpslink.com/index.php?title=Configuring_vsftpd_for_secure_connections_(TLS/SSL/SFTP](http://wiki.vpslink.com/index.php?title=Configuring_vsftpd_for_secure_connections_(TLS/SSL/SFTP))

hope this helps others too

Now i got one more query, I want to monitor /var/log/vsftpd.log realtime on a shell 

How can I do that?

Regards

:o

---

### Post by Arinux on 2007-05-31
Hi Frodon,

I followed your FTP guide and encountered the following error

ari@Crysis:/etc/ftpcert$ sudo chmod +x sign.sh
ari@Crysis:/etc/ftpcert$ sudo ./sign.sh server.csr
CA signing: server.csr -> server.crt:
Using configuration from ca.config
Enter pass phrase for ./ca.key:
Error opening CA certificate ./ca.crt
11388:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('./ca.crt','r')
11388:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load certificate
CA verifying: server.crt <-> CA cert
Error loading file ca.crt
11393:error:02001002:system library:fopen:No such file or directory:bss_file.c:122:fopen('ca.crt','r')
11393:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:125:
11393:error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
usage: verify [-verbose] [-CApath path] [-CAfile file] [-purpose purpose] [-crl_check] [-engine e] cert1 cert2 ...
recognized usages:
        sslclient       SSL client
        sslserver       SSL server
        nssslserver     Netscape SSL server
        smimesign       S/MIME signing
        smimeencrypt    S/MIME encryption
        crlsign         CRL signing
        any             Any Purpose
        ocsphelper      OCSP helper

Can you help with this?

Regards

:(

---

### Post by frodon on 2007-05-31
There's sometimes some problems creating the certificate, i would advice you to follow the whole certificate creation process several times and see if you have still the same problem each time.

---

### Post by Arinux on 2007-05-31
Hi Frodon,

Now i got a new error message


1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
CA verifying: server.crt <-> CA cert
server.crt: /C=IN/ST=MAH/L=Pune/O=Symantec/OU=Global IT/CN=Arindam Ghosh/emailAddress=arindam_ghosh@symantec.com
error 18 at 0 depth lookup:self signed certificate
/C=IN/ST=MAH/L=Pune/O=Symantec/OU=Global IT/CN=Arindam Ghosh/emailAddress=arindam_ghosh@symantec.com
error 7 at 0 depth lookup:certificate signature failure
13758:error:04067084:rsa routines:RSA_EAY_PUBLIC_DECRYPT:data too large for modulus:rsa_eay.c:668:
13758:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:

I tried this for like ten times but still get the same error message !

:confused:

---

### Post by frodon on 2007-05-31
Hum, it's out of my knowledge, i remember having this kind of problem once in the past and i think i solved it choosing short password and informations for the certificate.
Anyway if you have too much problems to create the certificate by hand you can install gproftpd which i beleive can generate a certificate for you.

---

### Post by Arinux on 2007-05-31
Hi Frodon ,

Now the error has changed

1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
CA verifying: server.crt <-> CA cert
server.crt: /C=IN/ST=MH/L=PUN/O=Symantec/OU=IT/CN=IT
error 18 at 0 depth lookup:self signed certificate
/C=IN/ST=MH/L=PUN/O=Symantec/OU=IT/CN=IT
error 7 at 0 depth lookup:certificate signature failure
17444:error:0407006A:rsa routines:RSA_padding_check_PKCS1_type_1:block type is not 01:rsa_pk1.c:100:
17444:error:04067072:rsa routines:RSA_EAY_PUBLIC_DECRYPT:padding check failed:rsa_eay.c:708:
17444:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:

Any suggestions ?

:guitar:

---

