---
title: "Searching a daemon that is alternative to FTP / SSH not linked to /etc/passwd?"
date: 2010-06-19
forum: Server Platforms
---

### Post by frenchn00b on 2010-06-19
Hello

I would like to run a server or ssh or ftp on a specific port

Sort of jailed daemon that runs with a login / pwd  that is not /etc/passwd based to?

---

### Post by HermanAB on 2010-06-19
Sounds like your solution would be SSH with a public key.

---

### Post by sjinks on 2010-06-19
FTP: proftpd (see [http://www.proftpd.org/docs/directives/linked/config_ref_AuthUserFile.html](http://www.proftpd.org/docs/directives/linked/config_ref_AuthUserFile.html))

SSH: public key authentication or maybe PAM.

---

### Post by frenchn00b on 2010-06-19
:confused::confused:> **sjinks said:**
> FTP: proftpd (see [http://www.proftpd.org/docs/directives/linked/config_ref_AuthUserFile.html](http://www.proftpd.org/docs/directives/linked/config_ref_AuthUserFile.html))

SSH: public key authentication or maybe PAM.


I would like a jailed, somehtnig that is not usnig /etc/passwd for passwords and taht users do not see the whole /HOME

---

### Post by sjinks on 2010-06-19
proftpd can jail users in their home directory, see [http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html)

---

### Post by sjinks on 2010-06-19
Or you can

chmod 0711 /home
chmod 0700 /home/*

---

### Post by frenchn00b on 2010-06-19
> **sjinks said:**
> Or you can

chmod 0711 /home
chmod 0700 /home/*

but I have some folders /backup /data that I cannot put chmod og-rwx  :( 
that'as the problesm

i hope that proftpd can do some jailing and another port than 21

---

### Post by frenchn00b on 2010-06-19
> **sjinks said:**
> proftpd can jail users in their home directory, see [http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html)

Thanks, that's a great tool !! thanks so much

by teh way to increase the security do you use TLS ?

# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

---

### Post by frenchn00b on 2010-06-19
here is a cool howto !!
[http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10](http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10)

for TLS secured PROFTPD

I changed port + use passive too

---

### Post by mituw16 on 2010-06-19
have you thought of webdav as an alternative? 

I've found it more stable than FTP and not as much a hassle in setting up as SSH for users. 

I set up my webserver so that users can upload to their web folders only and they use webdav over SSL... aka https. very easy setup and secure. took about 30 min to get up and running, and by the nature of it, the users don't user /etc/passwd, they use what ever passwd file you create and then they are jailed into what ever folder you assign them, :D :D :D

---

### Post by frenchn00b on 2010-06-20
> **mituw16 said:**
> have you thought of webdav as an alternative? 

I've found it more stable than FTP and not as much a hassle in setting up as SSH for users. 

I set up my webserver so that users can upload to their web folders only and they use webdav over SSL... aka https. very easy setup and secure. took about 30 min to get up and running, and by the nature of it, the users don't user /etc/passwd, they use what ever passwd file you create and then they are jailed into what ever folder you assign them, :D :D :D

Thanks a lot !! I will try to find some configuratino files, as soon as I found some time a bit

I blocked the ssh using allowusers into sshd_config
and jailed the proftpd using defaults ~
nice

webdav looks nice
[http://ase.tufts.edu/its/images/winWebdav09.gif](http://ase.tufts.edu/its/images/winWebdav09.gif)

---

### Post by mituw16 on 2010-06-20
here is a great link that is really easy to follow. (even though it say for 9.10, it works perfectly on 10.04... :D )

[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10")

---

