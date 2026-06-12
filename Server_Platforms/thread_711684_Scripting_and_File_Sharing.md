---
title: "Scripting and File Sharing"
date: 2008-02-29
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-29
Firstly my question deals with file permissions in FTP servers. I am using vsftpd on my server and am testing different accounts. I have them all point to the same directory but they all none of the other accounts can access to download the file. How do I change file permissions so it can be shared, also is there a way to automatically do this?

My second question goes with making accounts, it seems very tedious to have to go in and change the allowed users file and set the directory to all of the same location, is there a way to make a script so when I create a new user it automatically does that as well?

---

### Post by Mr. C. on 2008-02-29
The vsftpd server can be configured in a variety of ways.  You'll have to explain how you have it configured (real users, anonymous users, virtual users), and then we'll need to see the vsftpd.conf file (without the comments please).

Sure, you can script just about anything.  First start by describing the steps you manually undertake now.  Show the command lines.  Then they just get packaged into a parameterized script.

---

### Post by Holmes89 on 2008-03-01
Okay from what I can gather I need to make a common directory for every user. I make new users by the *adduser* command, I then go to my /etc/vsftpd.allowed_users file where I list the users. I then have a directory that is called FTPShare and I try to link them to the directory by using:
[]sudo ln-s /home/FTPShare /home/username/ [/]

This however puts a link in their folder but they are unable to change directory. I do not want to give them chroot privileges because I don't want them accessing all of my files. How do I allow them to all access the same directories and directory files?

You asked for my conf file so here is a copy of it:
> listen=YES
anonymous_enable=NO
local_enable=YES
userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd.allowed_users
write_enable=YES
local_umask=21
anon_mkdir_write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Welcome to the jHolmesNet FTP server.
chroot_local_user=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


---

### Post by Mr. C. on 2008-03-01
Let's take things one at a time.

First, don't try to use symlinks - this is the wrong approach.

I'd recommend you use vsftpd's virtual users.  This allows you to create new users, that don't require accounts in /etc/passwd, and you can control those users more tightly.  Can you get virtual user's setup ok ?

With virtual users, you can do some interesting things, on a per-IP or username basis, such as giving some  users read/write, some read-only, etc.

---

### Post by Holmes89 on 2008-03-01
okay that sounds great, how do i do it? I'm new at this stuff, and this is just things I found from other places.

---

### Post by Mr. C. on 2008-03-08
Sorry for the delay - do you still need help with this ?  If so, have you read the various HowTo's in creating virtual users with vsftpd ?

---

### Post by Holmes89 on 2008-03-29
Yes I've been looking but I don't know what to do. I want to make virtual users that all link to the same directory so that I can download a file that someone else uploads and vice-versa. Does anyone know of a good guide?

---

### Post by Mr. C. on 2008-03-30
Sorry, I don't track various guides, how-to's, etc.  You'll have to search for those or hope someone gives you a good one.

I can only help you learn how the facilities work, and guide you along.

---

### Post by netlogic on 2008-03-30
> **Holmes89 said:**
> . How do I allow them to all access the same directories and directory files?


it is very simple.
just edit the their default home dir location.

1. vi /etc/passwd
2. find bob
3. bob might look like ```
**bob:x:1011:1011:,,,:/home/bob:/bin/bash**
```
4. change bob settings to ```
**bob:x:1011:1011:,,,:/home/piracy-is-bad:/bin/bash**
```
5. do same thing for john and other pirates.

---

### Post by netlogic on 2008-03-31
Oh! I forgot. After the change, just chroot to the same directories. Just create two different accounts for each users. One for ftp. Another one for ssh. I am assuming they don't have a ssh account. Make sure configure your /etc/pam.d/vsftpd for your needs. If they don't need the interactive shell usage, don't offer it. Usually, only programmers will need it.  You can always setup a simple https page, so users can change their passwords. Always try best to keep things simple. I usually change to "allow" and add users who need ftp in /etc/ftpusers.  All ssh users should use keys.

---

