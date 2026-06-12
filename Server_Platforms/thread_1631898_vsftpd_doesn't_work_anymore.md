---
title: "vsftpd doesn't work anymore"
date: 2010-11-27
forum: Server Platforms
---

### Post by Strega on 2010-11-27
Hello,

I recently installed vsftpd on my system and it was running fine for my system users. Now I wanted to add virtual users so I googled it, I found this tutorial: [http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)
I did what they've been saying over there but when I restarted the vsftpd I couldn't login with the virtual user and also not with the system user anymore. This is the error ( with the system user who could login before ): ```
Status:	Verbinden met 109.230.234.21:21...
Status:	Verbinding aangemaakt, welkomstbericht afwachten...
Antwoord:	220 (vsFTPd 2.2.2)
Commando:	USER strega
Antwoord:	331 Please specify the password.
Commando:	PASS ************
Antwoord:	530 Login incorrect.
Fout:	Fatale fout
Fout:	Kan niet verbinden met server
``` At the end it says ( translated )```
Error:	Fatal error
Error:	Can not connect to the server
```

Does anybody know how to fix this?

Regards,
Strega

---

### Post by windependence on 2010-11-27
My guess is you blew out the password information when you did the tutorial. Just skimming over the article it looks like you would be messing with the password file and some other things that would blow out your password information. Not sure how to reset it, but there must be some admin mode where you can reset the password.
 
-Tim

---

### Post by windependence on 2010-11-27
Did you do this step?:
 

>  
Finally we need to configure PAM to use the password file, so edit /etc/pam.d/vsftpd # Customized login using htpasswd fileauth    required pam_pwdfile.so pwdfile /etc/vsftpd/passwdaccount required pam_permit.so

 If you did, look into the Vsftp tarball/docs for the PAM sample (/etc/pam.d/vsftp), it uses the PAM module pam_userdb.so which allows you to maintain a separate passwd list. When you did this step you told it to use a password file and it probably is either blank or doesn't exist until you create it
 
 
-Tim

---

### Post by Strega on 2010-11-27
You mean the password of my system user? But I can still login in ssh, so I think it's not the password. Can I check somewhere if the vsftpd deamon is even running? It normally should, because I did ```
/etc/init.d/vsftpd stop
/etc/init.d/vsftpd start
```
But you never know...
The output of stopping and starting the vsftpd deamon is```
...:~# /etc/init.d/vsftpd stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop vsftpd
vsftpd stop/waiting
...:~# /etc/init.d/vsftpd start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd
vsftpd start/running, process 40298

```
Regards,
Strega

---

### Post by windependence on 2010-11-27
Loggin into the server via ssh has nothing to do with vsftp. Try loggin in using ssh -vv *yourserver* and post the out put here.
 
-Tim

---

### Post by Strega on 2010-11-27
This is the "/etc/pam.d/vsftpd" file```
# Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required        pam_shells.so

# Virtuele gebruikers
auth    required        pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required        pam_permit.so

```

Anything wrong with it :) ?

Regards,
Strega

---

### Post by windependence on 2010-11-27
No, nothing wrong with this file but this is not where the passwords are stored.
 
Did you create your user ID in the password file like this:
 
```
 
htpasswd -c /etc/vsftpd/passwd username

```
 
If not, you need to create the users in the password file. The file is /etc/vsftpd/passwd but you cannot edit it directly as the file is encrypted.
 
Were you having trouble logging in via ssh to the server as well?
 
-Tim

---

### Post by Strega on 2010-11-27
I've created the user that way yes, just like the tutorial said. I use Putty to send the commands, do you mean the output I get there if I log in?

---

### Post by windependence on 2010-11-27
OK it seems the /etc/vsftpd/passwd file is not encrypted unless you specifically make it that way so take a look at the passwd file and see what the password is set to for the users. I am going to bet it's blank. That means the users have blank passwords. You can try logging in with blank passwords and see if that works. 
 
The password file should have this format:
 
```
 
USER
PASSWORD
USER2
PASSWORD2
[..etc..]

```
 
Let me know what you find in the passwd file.
 
-Tim

---

### Post by Strega on 2010-11-27
I didn't create a virtual user account for my system user because normally he would be able to login without right? I did try to make one for "bart_v", who isn't a system user. But also for him it fails to connect to the server.
This is what the passwd file looks like```
bart_v:5mhO.XVaVgVY2

```But also the final error I get when I login to ftp with any user is```
Fout:	Fatale fout
Fout:	Kan niet verbinden met server

Error:	Fatal error
Error:	Can not connect to server
```Which means, when I try to login, I can't connect to the server, is it possible that vsftpd isn't working and where can I check this?

---

### Post by windependence on 2010-11-27
However, you are also getting authentication messages. You can grep the process to find oout if it's running:
 
```
 
ps aux | grep vsftp

```
 
-Tim

---

### Post by eeffoc on 2010-11-27
According to Tim:

The password file should have this format:

Code:
 
USER
PASSWORD
USER2
PASSWORD2
[..etc..]

BUT...the password file you posted is as such:

bart_v:5mhO.XVaVgVY2

Not sure if it matters or not, as I'm not extremely experienced with setting up password protected users in vsftpd, but maybe it should be setup as such:

bart_v
5mhO.XVaVgVY2

Just a suggestion...I'll dig around and see what I can find out though. :)

---

### Post by eeffoc on 2010-11-27
I did find this in the forums: 

[vsftpd installation and configuration]("http://ubuntuforums.org/showthread.php?t=518293")

I hope it helps!

---

