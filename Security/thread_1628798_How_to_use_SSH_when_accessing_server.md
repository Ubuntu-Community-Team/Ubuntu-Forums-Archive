---
title: "How to use SSH when accessing server?"
date: 2010-11-23
forum: Security
---

### Post by listerdl on 2010-11-23
Hi I dont seem to find what I am looking for on the forum - perhaps someone can kindly point me in the direction for a SSH tutorial?

Bascially I am trying to connect to a godaddy server hosting account using SSH - should be a snap right?

Sorry if this is a real basic question, just interested. Thanks!!

* On filezilla which I use there is an option to use SFTP - SSH File Transfer instead of FTP - is it as simple as using that choice? I.e. no need to install OpenSSH or putty for windows?

Thanks!

---

### Post by mikewhatever on 2010-11-23
The general syntax look something like this: ssh user@ip, where user is your username on the server and ip is the ip address or domain name of the server. (example: ssh [email]listerdl@godaddy.com[/email])
SSH client is installed by default in Ubuntu, but if you try connecting from Windows, do install Putty.

---

### Post by listerdl on 2010-11-23
great thanks for that...is the client called openSSH right?

I should have a play with it first and then post questions i guess - thanks!

---

### Post by mikewhatever on 2010-11-23
The exact package name it openssh-client, in other words, were you to install it, that would have been the package to install.
Take a look at some community docs for more info.
[https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo)

---

### Post by magnatron on 2010-11-23
Dont forget to edit /etc/ssh/sshd_config and scroll down to the part that says permit root login and change the yes to no. If you need root access you can use sudo as a regular user.

---

### Post by listerdl on 2010-11-23
> **mikewhatever said:**
> 
SSH client is installed by default in Ubuntu

Is that via Places > Connect to Server ?

Thanks!

---

### Post by mikewhatever on 2010-11-23
> **listerdl said:**
> Is that via Places > Connect to Server ?

Thanks!

That would give you a file browser window over sftp, but not the shell. Handy when you want to copy files.

---

### Post by magnatron on 2010-11-23
If your using the default desktop Gnome gSTM makes a nice addition to Putty & sftp ;)

---

