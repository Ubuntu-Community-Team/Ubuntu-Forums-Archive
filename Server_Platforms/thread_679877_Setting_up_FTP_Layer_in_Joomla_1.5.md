---
title: "Setting up FTP Layer in Joomla 1.5?"
date: 2008-01-27
forum: Server Platforms
---

### Post by dada1958 on 2008-01-27
I installed Joomla 1.5 on my web server, running Ubuntu-server 6.06, this afternoon; installation went fine but I also want to set up the ftp layer to install components like the fireboard forum.
I already have access to my web server with ssh.
So I guess I'll have to enable ftp on my server, what's the best way to do that and how do I set that up with user name and password?
And what's going to be my FTP Root Path? See attachment.
TIA

---

### Post by joesapo on 2008-01-29
Interested in this as well.  Will post back if I make progress, but any help is welcome.

:)

---

### Post by dada1958 on 2008-01-29
The FTP-layer is part of Joomla, so you don't have to fiddle with FTP on your server. You can assign any user name and password when you're doing the FTP-layer thing during the installation. The FTP Root Path should be /var/www/yourjoomlasite.
That's the good part until now. When I try to install the FireBoard zip file, I'm getting these errors, see attachment. The zip file has been transferred to my server though, see other attachment.

---

### Post by adamos on 2008-04-14
I am struggling with 1.5.2 too. I never had any problems with joomla 1.0.x.

I tried every single method mentioned but no result. I did the phpsuexec method but it didnt work. You MUST create an ftp account in your server. you cant assign a random name to it.. try intalling vsftpd and create an account

---

### Post by furv on 2008-04-22
Not sure if this will help...
On an Ubuntu linux box I set access to only a single directory for the FTP user I created (/var/www/joomla) which was the Joomla installation directory. Then on the Joomla Installation screen I set the FTP Root Path to "./" (period, but no quotes), and finally the verify ftp settings was happy. Note that "/" was what the "autofind ftp path" gave me, but that was not accepted by the verification.

---

### Post by adamos on 2008-04-24
I started my server from scratch and I managed to get joomla 1.5.3 working with the ftp layer.

install proftpd or vsftpd and create a username and password and assign the working directory to be the one that you will have joomla installed.

in the username field put [email]username@yourserver.com[/email]
passwd : your password, working directory you can put slash (/) since its on joomla directory already and the host would be ftp.yourserver.com , port 21 and you will be good to go. no more permission issues.. dirs are 755 and files 644. 
if you are concerned about security, disable bash login for the ftp and move files such as configuration.php one directory up. there are more tricks in joomla forums.

Adam

---

