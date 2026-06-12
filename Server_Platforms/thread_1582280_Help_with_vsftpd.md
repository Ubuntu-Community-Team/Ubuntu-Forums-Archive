---
title: "Help with vsftpd"
date: 2010-09-26
forum: Server Platforms
---

### Post by dragao-azul on 2010-09-26
Hey,

I've been following [this]("http://ubuntuforums.org/showthread.php?t=518293") tutorial to configure a ftp server but I'm having some problems that I hope you can help me with:

1- I've set up 3 virtual users, one of them is a system one (with a different password) and writes on his own home folder.

With this one I haven't found any problems yet, but with the other 2 users I can't access files/folders created by them. It's a permissions problem for sure, but I'm not sure how to correct it.

With these users I can upload files, create files and create folders. The problem is I can't access what I create (I can't enter a folder I created but it is there and I can upload files into it).


2- Whenever I turn on ssl_enable=YES I can't access the server (even from the server itself when I connect to localhost, It's a regular Ubuntu installation). Any Ideas on this?


Here's the config file for the users:
```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/(folder)
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=(the user i created for this, owns the root folder)
```

And here's part of the vsftpd.conf file:
```
...
#ssl_enable=YES (if I turn this on I can't login)
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990
```

Thz in advance.

;)

---

### Post by dragao-azul on 2010-10-01
Any idea? :(

Thz

;)

---

### Post by SlugSlug on 2010-10-01
check out /var/log/

chances are you've not done a ssl certificate properly or somit..

---

### Post by dragao-azul on 2010-10-01
I haven't created any certificate... :S

On the tutorial it said:
> No need to create a certificate. vstfpd uses the certificate Ubuntu creates upon it's installation, the "snake-oil" certificate (openssl package, installed by default). Please don't be afraid of it's name! 

So I guess I do need one after all :P

Can you explain how do I create one? Or where can I find that information?

---

### Post by SlugSlug on 2010-10-01
do you have openssl installed?

---

### Post by dragao-azul on 2010-10-01
Yes

---

### Post by dragao-azul on 2010-10-02
I just found out that the permissions problem happens with every user connect through ftp.

How can I make it so that the permissions of the uploaded AND created files/folders are the same as if the user was creating the folders/files directly in the system?

And can you explain what do I do with openssl to get the certificate? (and how do I "give it" to the ftp server?)

Thz

;)

---

### Post by dragao-azul on 2010-10-04
Ok,

I solved the permissions problem and I can kinda connect with ssl (but there's still some sort of problem).

First I had this:
```
rsa_cert_file=/etc/vsftpd/vsftpd.pem

ssl_enable=YES
allow_anon_ssl=YES
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

```

And i got this error in fireftp:
522 SSL connection failed; session reuse required: see require_ssl_reuse option in vsftpd.conf man page
: //

I couldn't get the list of files.

Then I added:
```
require_ssl_reuse=NO

```

Now I don't get any error but I never get a directory listing as well.

Any ideas?

Thz

;)

---

