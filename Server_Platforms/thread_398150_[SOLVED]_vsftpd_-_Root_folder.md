---
title: "[SOLVED] vsftpd - Root folder"
date: 2007-03-31
forum: Server Platforms
---

### Post by victorbrca on 2007-03-31
Hi all,

  I've set up a root folder to be used by my two ftp users with different privileges. It works ok when I access it from Windows, but not the same when I access from Linux.

  User's are suposed to be "chrooted" to that folder only, but in Unix when I access with the privileged account I can see an modify "/" completelly. The annymous works ok when accessed from Windows and/or Linux

  I'm not using chroot per say, instead I used the following string on "vsftpd.conf":

> # Sets root directory for non-anonymous users
local_root=/media/sdb1/ftp/wazem

# Sets root directory for anonymous
anon_root=/media/sdb1/ftp/wazem


  Any idea??


Thanks!!!


Vic.

---

### Post by Mr. C. on 2007-03-31
From man vsftpd.conf :
> local_root
     This  option  represents  a  directory  which vsftpd will try to
     change into after a local (i.e. non-anonymous) login. Failure is
      silently ignored.

This does not chroot, it changes directory (eg. it is only a cd command).

MrC

---

### Post by victorbrca on 2007-03-31
Ok, it makes sense. But why is anonymous getting chrooted on the folder I specified which is not the default ftp root and a local user is not? It would make sense if I was using the default ftp root folder, as I'd guess vsftpd would not allow an anonymous login go anywhere else, but this is not the case. Is vsftp smart enough to adapt the rules to the changed ftp root folder?

Or, why when I access it from Windows with the local user it does not let me browse anything other specified ftp root folder, but when I access from Linux it does?

Just trying to understand it.... 


Thanks, :)


Vic.

---

### Post by Mr. C. on 2007-03-31
You have to specifically set chroot_local_user to enable chroot for local users.  There are security issues with this, so you have to understand what the risks are.

Anonymous users are chrooted.  Since they do not have write permission in the chroot directory, it is secure.

vsftpd does what its configuration tells it to do, but you have to read the defaults in man vsftpd.conf to understand this.

It does not behave differently when you log in via Windows vs. when you log in via some *nix system.  It is not fickle.  If you believe otherwise, show evidence.

MrC

---

### Post by victorbrca on 2007-03-31
Hi Mr C.


  Thanks for the reply and the time for the teachings.. :)

  I will go through all the docs again and try to configure the chroot for he local user so I have the proper security.

  I am however experiencing the related issue, as when I log from my Linux laptop with the local user account I am presented with "/", and when I log from my Windows desktop using the same local user account I'm presented with the ftp root folder that I set with the command on my 1st post. If I try to go up it opens a browser with my default home page.

  It may be due to my lack of knowledge (which I'm working on)... But I'd be glad to help the vsftpd project in case this is really a bug. Not sure how thou...

Once again thanks for all the clarifying...


Vic.

---

### Post by Mr. C. on 2007-04-01
I'm sure there is no bug.

If you post your vsftpd.conf file, without the comments, I'll take a look.  The following command will provide the relevant output:

```
$ grep -v '^#' /etc/vsftpd.conf
```

MrC

---

### Post by victorbrca on 2007-04-01
Thanks a lot.... 

Here it is..

> listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome Wazem FTP
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

local_root=/media/sdb1/ftp/wazem
anon_root=/media/sdb1/ftp/wazem
no_anon_password=YES



Vic.

---

### Post by Mr. C. on 2007-04-01
Nothing out of the ordinary in your vsftpd.conf file.    I tested it, and here is my output via Linux and Windows, using your setup:

```
$ ftp localhost
Connected to localhost.
220 Welcome Wazem FTP
Name (localhost:mrc): 
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0               0 Apr 01 04:52 afile
226 Directory send OK.
ftp> pwd
257 "/tmp/sdb1/ftp/wazem"
ftp> quit
221 Goodbye.
```

Trial 1: Everything as expected.  Local user login changed directory to local_root dir.
```
$ ftp localhost
Connected to localhost.
220 Welcome Wazem FTP
Name (localhost:cappella): ftp
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0               0 Apr 01 04:52 afile
226 Directory send OK.
ftp> pwd
257 "/"
ftp> quit
221 Goodbye.
```
Trial 2: Everything as expected.  Anonymous login changed directory to anon_root dir.

```
C:\Documents and Settings\MrC>ftp 192.168.0.2
Connected to 192.168.0.2.
220 Welcome Wazem FTP
User (192.168.0.2:(none)): mrc
331 Please specify the password.
Password:
230 Login successful.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
afile
226 Directory send OK.
ftp: 7 bytes received in 0.00Seconds 7000.00Kbytes/sec.
ftp> pwd
257 "/tmp/sdb1/ftp/wazem"
ftp> quit
221 Goodbye.
```
Trial 3: Everything as expected.  Local user login via Windows changed directory to local_root dir.

C```
:\Documents and Settings\MrC>ftp 192.168.2.12
Connected to 192.168.0.2.
220 Welcome Wazem FTP
User (192.168.0.2:(none)): ftp
230 Login successful.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
afile
226 Directory send OK.
ftp: 7 bytes received in 0.00Seconds 7000.00Kbytes/sec.
ftp> pwd
257 "/"
ftp> quit
221 Goodbye.
```
Trial 4: Everything as expected.  Anonymous login via Windows changed directory to anon_root dir.

If you are connecting to FTP via a browser, the default will be anonymous login.

You have *both* anonymous and local users attempting to CD into the same directory:

```
local_root=/media/sdb1/ftp/wazem
anon_root=/media/sdb1/ftp/wazem

```

vsftpd will silently fail if the logged in user (real or anonymous) does not have permission to cd into that directory.  Check your permissions on all directories down to wazem.

If you perceive you are getting different results, show your output as I have.  Actual data is more reliable than your interpretation.

MrC

---

### Post by victorbrca on 2007-04-01
Hi Mr C.


  I got the exact same results as you on *nix and Windows. Anonymous is stuck to ftp root while local user can change to real /. 

  However, if on windows I open my documents folder, type my ftp address on the address bar and logon with the local user account, I am them not able to change to anything bellow my ftp root. I am able to do that with the same user account on command prompt, but not using the folder. I tried typing in the password 4 different times just to be sure, and I still got the same result.

  You could guess that I'm not getting authenticated and not getting any error msg, but I'm able to create a folder, which I've disabled my anonymous account of doing.


Vic.

---

### Post by Mr. C. on 2007-04-01
> **victorbrca said:**
> However, if on windows I open my documents folder, type my ftp address on the address bar and logon with the local user account
This is using IE's built-in FTP.  How are you performing the "logon" ?
> **victorbrca said:**
> 
 I am them not able to change to anything bellow my ftp root. 
This is because you are still logged in anonymously.
> **victorbrca said:**
> 
I am able to do that with the same user account on command prompt, but not using the folder. I tried typing in the password 4 different times just to be sure, and I still got the same result.
Where are you typing a password ? You are connected anonymously.  You must review your  vsftpd logs in /var/log to convince yourself that vsftpd is behaving as you configured.

> **victorbrca said:**
> You could guess that I'm not getting authenticated and not getting any error msg, but I'm able to create a folder, which I've disabled my anonymous account of doing.
You have write_enable=YES, which *allows* even anonymous users to create directories.  Review the man page.

I'd like to try to convince you to stop believing the system or some server like vsftpd is broken, and when things are working like you expect, accept that you don't understand how the system is working, or that the mistake or misconfiguration is yours.

MrC

---

### Post by victorbrca on 2007-04-01
Hi Mr C.,


  IMHO, I'll believe in whatever you tell me to. I'm just a noob in Linux and have a deep respect to all experienced people, like you, who try to help me.

  I do believe that it's most likelly a configuration error due to my lack of knowledge. I just would like to understand where I'm making those mistakes...

  Anonymous can not create a folder as I changed the ownership of all folders to the local user.

> Where are you typing a password ? You are connected anonymously. You must review your vsftpd logs in /var/log to convince yourself that vsftpd is behaving as you configured.

  If you right click on the Widowns built-in ftp it shows a menu with an option "Login as". From there you can type in a user-name and password.


```
webm@pluto:/var/log$ sudo cat vsftpd.log
Sun Apr  1 08:10:34 2007 [pid 4109] CONNECT: Client "192.168.1.10"
Sun Apr  1 08:10:34 2007 [pid 4108] [ftp] OK LOGIN: Client "192.168.1.10", anon password "<no_password>"
Sun Apr  1 08:12:35 2007 [pid 4150] CONNECT: Client "192.168.1.10"
Sun Apr  1 08:12:35 2007 [pid 4149] [webm] OK LOGIN: Client "192.168.1.10"

```

  Please understand that I'm no trying to prove a point. Just trying to understand... Feel free to give up on me anytime!!!  :)

Thanks again,


Vic.

---

### Post by Mr. C. on 2007-04-01
> **victorbrca said:**
> 
  Anonymous can not create a folder as I changed the ownership of all folders to the local user.

There are two items to consider: 1) what vsftpd is configured to allow (write_enable), and what your Linux privileges allow.  vsftp tries to let an anonymous user create a folder, but linux permissions will deny the creation.  The two are distinct, and separate.

  If you right click on the Widowns built-in ftp it shows a menu with an option "Login as". From there you can type in a user-name and password.
> **victorbrca said:**
> 
  Please understand that I'm no trying to prove a point. Just trying to understand... Feel free to give up on me anytime!!!  :)
No problem.  It sounds like you're becoming very familiar with how vsftpd works. You'll get the hang of it.

MrC

---

