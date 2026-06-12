---
title: "How to reboot headless server with pass phrase"
date: 2008-06-27
forum: Server Platforms
---

### Post by satimis on 2008-06-27
Hi folks,


I have a headless server which requires "pass phrase" to start Apache at boot.  After remote rebooting I can ssh connect the server.  But I can't start Apache because I have no way to keyin the password remotely.


After connection, running;

$ sudo /etc/init.d/apache2 restart```

 * Forcing reload of apache 2.0 web server...                                   [Sat Jun 28 10:33:50 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address [::]:443
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```
Is there any glue.  TIA


B.R.
satimis

---

### Post by RealPSL on 2008-06-27
Your best bet here is to use the SSLPassPhraseDialog directive

[URL="http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#sslpassphrasedialog"]
[/URL]

If you use the exec method to run a script that only root has access that simply does a echo of the password required.

---

### Post by satimis on 2008-06-28
> **RealPSL said:**
> Your best bet here is to use the SSLPassPhraseDialog directive

[URL="http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#sslpassphrasedialog"]
[/URL]

Hi RealPSL,


Thansk for your advice.  I haven't got experience on running SSLPassPhraseDialog directive before.


Googling brought me following info;


on /etc/apache2/httpd.conf

adding follows;```


<IfModule mod_ssl.c>
#   Pass Phrase Dialog:
#  #SSLPassPhraseDialog  builtin
SSLPassPhraseDialog exec:/content/ssl/pp/pp.out
</..>

```


File pp.out```

#!/bin/sh

PASS1=somepass1
PASS2=somepass2

case $1 in
    www.pass1.com:443) echo $PASS1;;
    www.pass2.com:443) echo $PASS2;;
esac

exit 0

```


What shall I replace "somepass1" and "somepass2"?  Whether the request for "Pass Phrase" will popup on ssh-connecting the remote server?  


Where shall I create the path "/content/ssl/pp/pp.out" ?

Any additional Apache package needed to install?


Please shed me some light. TIA


> 
If you use the exec method to run a script that only root has access that simply does a echo of the password required.
Sorry I don't catch please explain in more detail.  Thanks


B.R.
satimis

---

### Post by mrpeenut24 on 2008-06-28
Did you set up the ssl certificates yourself?  If so, you can make a different ssl cert that doesn't require a password at startup.  This is somewhat insecure, but it's not hard to safeguard it with permissions.

See [here]("http://www.tc.umn.edu/%7Ebrams006/selfsign.html").

---

### Post by satimis on 2008-06-28
> **mrpeenut24 said:**
> Did you set up the ssl certificates yourself?  If so, you can make a different ssl cert that doesn't require a password at startup.  This is somewhat insecure, but it's not hard to safeguard it with permissions.

See [here]("http://www.tc.umn.edu/%7Ebrams006/selfsign.html").
Hi mrpeenut24,


Thanks for your advice and URL.


I haven't setup the certificate yet.  Each time starting Apache I accept the popup certificate temporarily.


satimis

---

### Post by mrpeenut24 on 2008-06-28
You are using ssl right?  That's the only reason I can think of Apache asking for a password.  How did you set it up?  What does it popup each time?

---

### Post by satimis on 2008-06-28
> **mrpeenut24 said:**
> You are using ssl right?  That's the only reason I can think of Apache asking for a password.  How did you set it up?  What does it popup each time?
Hi mrpeenut24,


I'm running ssl/openssl.  I followed following guide to setup Apaches2;

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)


According to the notes taken down during installation I ran;

$ sudo openssl genrsa -des3 -out server.key 1024

to generate the key and keyin the pass phrase.  Therefore each time booting the server I have to enter pass phrase to start Apache.


satimis

---

### Post by p_quarles on 2008-06-28
Would taking Apache out of the boot up procedure and then starting it manually work? It sounds like the problem has to do with a pre-login pass phrase dialogue, and this would avoid that.

---

### Post by mrpeenut24 on 2008-06-28
satimis: Excellent.  So you do have SSL installed, and you set it up yourself.  The page you followed had directions for disabling the password.  Did you follow it?

> 
         In any case, you can choose to run your secure web server without         a passphrase by leaving out the -des3 switch in the generation         phase or by issuing the following command at a terminal prompt: 




The howto leaves out how to actually do this.  From this point down, it continues to use server.key, without ever renaming server.key.insecure to server.key.


Run this:
```


  sudo openssl rsa -in server.key -out server.key.insecure
sudo mv server.key server.key.secure
sudo mv server.key.insecure server.key

```

 then move the server.key to wherever you were storing your keys.  This should do it without having to redo the certificate as well.

---

### Post by satimis on 2008-06-28
Hi mrpeenut24,


Thanks for your advice.


> 
The page you followed had directions for disabling the password.  Did you follow it?

Sorry, no.  I keep the "pass phrase".  I want to learn.


I build this server for testing, specifically for testing SugarCRM.  However I encountered lot of problem first Cyrus then MySQL.  Now SugarCRM is running but I can't login.  


I use the same MySQL root user password on SugarCRM.  The later use MySQL database.  I wonder whether the problem comes from MySQL.  I'm still struggling.  It looks quite funny to me.


B.R.
satimis

---

### Post by satimis on 2008-06-28
> **p_quarles said:**
> Would taking Apache out of the boot up procedure and then starting it manually work? It sounds like the problem has to do with a pre-login pass phrase dialogue, and this would avoid that.
Hi p_quarles,


If booting on the server and keyin "pass phrase".  Apache starts without problem.  I'm interested to learn how to it remotely.


B.R.
satimis

---

