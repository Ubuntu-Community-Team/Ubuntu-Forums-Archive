---
title: "ubuntu mail server"
date: 2013-03-27
forum: Server Platforms
---

### Post by sipetron on 2013-03-27
i have problem with mail server , i tryed many application like postfix and sendmail , until now i cant connect to pop3 or smtp from other mechin .
please help me because exchange server make me losse my mind :(:(

---

### Post by darkod on 2013-03-27
You need to provide more details about the error messages you get, or similar. Installing a basic mail server is not that difficult. You need postfix for example, and you also need something like dovecot that actually helps with pop3, imap, etc. Maybe that's why it didn't work.

You have all the basic info you need in the official documentation:
[https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html)

---

### Post by sipetron on 2013-03-28
i done all of that before 
the problem is when i tray connect to mail server using outlook , its keep telling me that the pop3 password error . 
what i must do in that case ?

---

### Post by darkod on 2013-03-28
You might be entering a wrong username or password. Have you double checked that the username and password are correct?

I assume you created the user in ubuntu. Have you tried to log into the server with the username to see if it works?

---

### Post by sipetron on 2013-03-28
ofcourse i use the right username and password , its the same for every thing ssh , mysql, login .
i tray to make new user and the same result .

---

### Post by darkod on 2013-03-28
Also double check if the outlook settings are correct. I'm not sure but I think dovecot installs with secure connection by default (SSL), so an email client will be able to connect only if it's configured for the correct type of connection. Sometimes the client can autodetect the connection type, sometimes it has to be set manually.

Apart from that I don't have any other ideas. Few weeks ago I did a simple test with postfix and dovecot, leaving everything by default and using only a local domain, and Thunderbird connected to it right away.

---

### Post by SeijiSensei on 2013-03-28
Logs are your friend.  What do you see in /var/log/mail.log?

---

### Post by sipetron on 2013-03-28
Mar 28 20:40:06 server dovecot: pop3-login: Aborted login (auth failed, 1 attempts): user=<hassan@server.net>, method=PLAIN, rip=192.168.1.8, lip=192.168.1.3

Mar 28 20:44:42 server dovecot: pop3-login: Aborted login (auth failed, 2 attempts): user=<hassan>, method=PLAIN, rip=192.168.1.8, lip=192.168.1.3, TLS

---

### Post by SeijiSensei on 2013-03-28
As darkod said, dovecot is forbidding the use of plain-text logins.  Take a look in dovecot.conf for things like "disable_plaintext_auth"  and the list of "mechanisms" in the auth {} section of the file.  On my local server which accepts plaintext logins I have the first entry set to "no" and "plain" as the only mechanism in auth{}.

---

### Post by sipetron on 2013-03-30
nothing work

---

### Post by darkod on 2013-03-30
Did you changed the options in the configuration as Sensei said, and restarted the server after that?

Another option is to simply install Citadel which is a mail server: [www.citadel.org](www.citadel.org)

The Easy Install script does all the work, you can install it easily on ubuntu: [http://www.citadel.org/doku.php/installation:easyinstall:prereq-debian.html](http://www.citadel.org/doku.php/installation:easyinstall:prereq-debian.html)

Depending whether you are running Apache on the server that you wish to use, and how do you want to do the authentication: Internal, Linux users on the machine, LDAP or AD.

---

### Post by sipetron on 2013-03-31
This program was unable to connect or stay connected to the Citadel  server.  Please report this problem to your system administrator

---

### Post by darkod on 2013-03-31
Give us more details, that is not enough.

1. How did you install, did you use the Easy Install script with the command provided in my link?

2. Are you trying this on "brand new" ubuntu server or you already have services like Apache and postfix running?

3. What port did you select for the Citadel webserver, port 80 or you left it on another value?

If you want this machine to be only a mailserver, I suggest you reinstall clean ubuntu server again, in the task selection select only OpenSSH and nothing else. If you have Apache and other mail services already running, regardless whether they work or not, it might clash with Citadel so you have to be careful about ports and where are services running.

Also, you have to decide if you want Citadel to use internal authentication, or another type.

---

### Post by sipetron on 2013-03-31
i installed it on clean new ubunut 12.04. server , no extart service i gust install lamp server & mysql & ssh & bind nothing else .

---

### Post by darkod on 2013-03-31
LAMP and mysql is extra on the basic ubuntu server. Do you need these services? Because you don't need them for the Citadel mailserver. If you need them for something else, that's another thing.

Just yesterday I installed Citadel with the Easy Install script, and it worked right away. But I instaled on ubuntu server that had only ssh installed, nothing else. Also, it depends on the options you selected during the Citadel installation. If you changed some of the options, it might not work as intended.

---

### Post by sipetron on 2013-03-31
same result

---

### Post by darkod on 2013-03-31
Sorry, I have no idea what is wrong. Are you running the script with the curl command as root? You need to run it as root so that it installs correctly. And you did install the ubuntu/debian prerequisits, right?

Or you might be making a wrong choice in one of the questions during Citadel installation.

In any case, I have no idea what moght be going wrong, I don't know much about Citadel myself.

---

