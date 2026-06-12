---
title: "Build my own Ubuntu Server"
date: 2009-08-11
forum: Server Platforms
---

### Post by Assim on 2009-08-11
I've had a few websites with PHP, MySQL and others. I know how to upload using FTP, and all those things that need to be known when buying a website from a web host.

Now what I don't know is how they do it in the technical side. I tried to install Ubuntu Server Edition on but all what I see is those terminal thingy which I don't know but I can learn of course. What I don't know is:

Q1: How to put files there, any of those for the website such as those .php and .html files?
Q2: How can I let anyone who connects to my domain name to go to my server?
Q3: What is OpenSSH, explain more please. Also tell me what it does.
Q4: Tell me more and more about the server edition.

Please, if you could answer at least one question, then please do, it will make a big difference until someone else answers the other questions.

---

### Post by Assim on 2009-08-11
Another question: What if I have a dynamic IP and not a static IP address? What should I do?

---

### Post by grantemsley on 2009-08-11
Q1: Your website's files typically go in /var/www
Q2: Make sure apache2 is installed, and if you have a router, you'll need to forward port 80 to the ubuntu server
Q3: OpenSSH is an SSH (Secure SHell) daemon.  It lets you get to the command line from another machine.  If you are using windows on your desktop, download Putty (google it) which is an excellent SSH client for windows.
Q4: The server edition does not have a GUI.  There is no mouse, no graphics. If this is your first time playing around with linux, I'd recommend installing the desktop version.  You can then add the server software (like the webserver) afterwards.

Also, if you have a dynamic IP address, you'll have to use something like dyndns.org and a program to update it with your new IP every time it changes.

---

### Post by Assim on 2009-08-11
> **grantemsley said:**
> Q1: Your website's files typically go in /var/www
Q2: Make sure apache2 is installed, and if you have a router, you'll need to forward port 80 to the ubuntu server
Q3: OpenSSH is an SSH (Secure SHell) daemon.  It lets you get to the command line from another machine.  If you are using windows on your desktop, download Putty (google it) which is an excellent SSH client for windows.
Q4: The server edition does not have a GUI.  There is no mouse, no graphics. If this is your first time playing around with linux, I'd recommend installing the desktop version.  You can then add the server software (like the webserver) afterwards.

Also, if you have a dynamic IP address, you'll have to use something like dyndns.org and a program to update it with your new IP every time it changes.
Thanks, now let's say I have the desktop version, what should I do to add the server software.

Thanks. :)

---

### Post by hessiess on 2009-08-11
> **Assim said:**
> Thanks, now let's say I have the desktop version, what should I do to add the server software.

Thanks. :)

```

sudo apt-get install apache2 php5 libapache2-mod-php5

```

Use SFTP instead of the highly insecure outdated FTP protocol.

---

### Post by bear24rw on 2009-08-11
> **hessiess said:**
> ```

sudo apt-get install apache2 php5 libapache2-mod-php5

```

Use SFTP instead of the highly insecure outdated FTP protocol.

forgot ssh ;)

```
sudo aptitude install openssh-server apache2 php5 libapache2-mod-php5
```

---

### Post by Kolipoki on 2009-08-11
> **grantemsley said:**
> Q1: Your website's files typically go in /var/www
Q2: Make sure apache2 is installed, and if you have a router, you'll need to forward port 80 to the ubuntu server
Q3: OpenSSH is an SSH (Secure SHell) daemon.  It lets you get to the command line from another machine.  If you are using windows on your desktop, download Putty (google it) which is an excellent SSH client for windows.
Q4: The server edition does not have a GUI.  There is no mouse, no graphics. If this is your first time playing around with linux, I'd recommend installing the desktop version.  You can then add the server software (like the webserver) afterwards.

Also, if you have a dynamic IP address, you'll have to use something like dyndns.org and a program to update it with your new IP every time it changes.

Just to add a bit on those:
Q1. Some people have recomended to make you web site inside another folder in the /var/www directory, as www is owned by the root user.
Q2. Nailed.
Q3. Putty would be the perfect tool for CLI. Nonetheless, if your end is a Win machine, you might want to try WinSCP, which will connect more securely through the SSH server and act just like an FTP client. You will see the explorer-like view, with both local and remote windows. 
Q4. Don't give up on non-gui option. You might be able to enjoy it later on and the only things you will really need to manage the server are the options in the Q3 answer. Cheers...

---

### Post by bear24rw on 2009-08-11
also check out FileZilla for ftp/sftp/other? transfers its completely cross platform and super easy to transfer files across ssh

---

### Post by oj0kksn5 on 2009-08-11
winscp is easy to transfer files to and from server and uses ssh

---

### Post by Assim on 2009-08-11
> **bear24rw said:**
> forgot ssh ;)

```
sudo aptitude install openssh-server apache2 php5 libapache2-mod-php5
```
Great, it works. :)

So now this would work nicely as a server? I mean even though that I'm running the desktop edition, but if I do this on my server, would it work nicely or...?


> **Kolipoki said:**
> Just to add a bit on those:
Q1. Some people have recomended to make you web site inside another folder in the /var/www directory, as www is owned by the root user.
Q2. Nailed.
Q3. Putty would be the perfect tool for CLI. Nonetheless, if your end is a Win machine, you might want to try WinSCP, which will connect more securely through the SSH server and act just like an FTP client. You will see the explorer-like view, with both local and remote windows. 
Q4. Don't give up on non-gui option. You might be able to enjoy it later on and the only things you will really need to manage the server are the options in the Q3 answer. Cheers...
Thanks for the extra information, I really appreciate that. ;)

---

### Post by Assim on 2009-08-11
One more thing, where can I manage the MySQL database.

I also couldn't add more files, or is it because I should be the "root" user in this case?

---

### Post by bartos on 2009-08-11
> One more thing, where can I manage the MySQL database 

phpMyAdmin is used to manage MySQL databases. Very good web interface. You will also want Webmin installed to make changes easier to services or users and many other things.

Q1 Changing httpd.conf in /etc/apache2/. You can set your webpages in any directory even /home/you/.look for <Directory "/home/<your user name here>/public_html/"> 

Q2 My router lets me bind Mac address to an ip address so my server is always .120 as long as I don't change nic.then set port forwarding to that IP

Q3 SSH is your main communication with your server. Either typing in commands or transferring files. Midnight Commander is an awesome terminal file explorer (sudo apt-get install mc)

Q4 With Webmin, mc and phpMyAdmin, you don't need a GUI.

Good Luck

---

### Post by Assim on 2009-08-12
Great. But before trying to install PhpMyAdmin, it would ask me for the host which I presume localhost is fine, as for the username and password? Is it root for the username, but how do I set the password?

Thanks. :)

---

### Post by bartos on 2009-08-12
Mysql should have asked you to enter a password on install. Which is the password you use for phpMyAdmin.

---

### Post by Assim on 2009-08-12
It didn't ask for any password when I installed it through the terminal in my desktop edition of Ubuntu.

---

