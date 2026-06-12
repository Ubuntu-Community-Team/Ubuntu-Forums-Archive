---
title: "[SOLVED] tired of trying to configure vsftpd with no success"
date: 2008-03-06
forum: Server Platforms
---

### Post by Mike V on 2008-03-06
Hi, all, I've trying to set up a ftp server, I download and install vsftpd because I have only read good things about it, I have three weeks (not daily of course) trying to make it work, but so far I can only see the service, I read a lot about it but I just can't get it working, what I want to do is the following:

* Local user, must be able to log in and do whatever he wants (using ssl is prefered)
* anonymous user must be able to log and can only access a simple folder with a lot of softlinks (music, documents, archives, etc) he can download whatever he wants but he could not write anything.

this is one of my config files, but as I already mentioned it doesnt work :(

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=mike
idle_session_timeout=300
data_connection_timeout=120
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/home/mike
force_dot_files=YES
hide_ids=YES
max_per_ip=1
max_clients=6


If any of you can point me in the right direction or have a proper configuration file that does what I want I would appreciate it.

Thnx in advance.

---

### Post by Cypher on 2008-03-07
Try this instead..
```

sudo apt-get install proftpd

```
Once the package is downloaded and installed, you will get a menu asking if you want the INET or STANDALONE version, just choose STANDALONE and let the configuration complete.

Now FTP to your machine from anywhere else and you should be all set..

---

### Post by hyper_ch on 2008-03-07
are you sure you need a ftp server?

Wouldn't sftp/scp also work?

---

### Post by Mike V on 2008-03-08
well I don't think so, because the anonymous user can be any friend who doesn't know about  the exact location or name of the files to be downloaded, and about the other ftp server its stable like vsftpd, I like vsftpd, the only thing that I don't like its that I cant configure it right :(

---

### Post by HermanAB on 2008-03-08
Hmm, vsftpd should work right out of the box.  You should not need to configure anything, same with proftpd.  

So, uninstall vsftpd, make sure ALL the configuration files are deleted, then install it again and this time, try it out before changing anything in the configuration.

Cheers,

Herman

---

### Post by Jimmyfj on 2008-03-08
I use the vsftpd FTP server on my system, and has done so for a long time now. It works just fine for me.

What I've done is that I've disabled anonymous login completely. Created an account which I named "dudes" and use that for all my friends so that they can login via a secure connection. No troubles with the server at all that way, and my friends are happy. They can do what ever they want on the ftp, but they have no clue to where the stuff they upload is stored, they needn't know that either. 

So disable the anonymous login and create an account with an easy password and start trusting both your system and your friends.

---

### Post by Mike V on 2008-03-08
Thanks HermanAB and Jimmyfj, I remove vsftpd and then did what Jimmyfj suggested, but now I have another little problem, when I log in in with my account I can do anything (obviously), but I create some links (ln -s TARGET LINKNAME) in his (generic account) home directory, but when I log I cannot do a "cd LINKNAME" and the rights are "drwxr--r-- mike mike Music_00", so they must be able to cd there, am I right?, What could it be?

Thanks in advanced

---

### Post by hyper_ch on 2008-03-09
> **Mike V said:**
> well I don't think so, because the anonymous user can be any friend who doesn't know about  the exact location or name of the files to be downloaded,

well, on any ftp server one has to know the path to the files he wants to download... same goes for scp/sftp....

installing mysecureshell and creating a new user with that as default shell and he can't move out of his homedire and you put the things in there that you want to make available.

---

### Post by Mike V on 2008-03-09
> **hyper_ch said:**
> well, on any ftp server one has to know the path to the files he wants to download... same goes for scp/sftp....

installing mysecureshell and creating a new user with that as default shell and he can't move out of his homedire and you put the things in there that you want to make available.

yeah I know, what I was trying to say is that I want to have something like this:

/ (his home folder)
/Music0
/Music1
/Music1/GH
/Videos
/Flashes
/Misc

but in reality those folders are like this:

/home/dudes (home folder)
/media/DATA00/Music00
/media/DATA00/Music01
/media/DATA00/Music01/GH
/media/DATA00/Vidz
/media/DATA00/FlashFiles
/media/DATA00/Documents

all of this with only read access for the dudes account, sorry for the misunderstanding, also they will be using a graphical ftp client like fireftp, so they can look directly into the folders available with little or no previous  knowledge of what they are looking for.

---

### Post by hyper_ch on 2008-03-10
that should be easily doable with hardlinks...

---

### Post by Mike V on 2008-03-11
yeah, but hard links doesn't work with directories, not even root can do that.

---

### Post by hyper_ch on 2008-03-11
are you sure? A directory is nothing but a file either... hardlinking directories should be possible... well, I'm not on my machine right now, so I can't test...

---

### Post by Mike V on 2008-03-11
yeah I cant :( the docs says its to prevent recursive listing :S

---

### Post by hyper_ch on 2008-03-11
interesting...

---

### Post by Mr. C. on 2008-03-11
> **hyper_ch said:**
> are you sure? A directory is nothing but a file either... hardlinking directories should be possible... well, I'm not on my machine right now, so I can't test...

Its a bit more complicated than that.  Directory hard linking is a no-no.

---

### Post by Mike V on 2008-03-11
well I think I will need to find another approach, thnx anyway all of you

---

