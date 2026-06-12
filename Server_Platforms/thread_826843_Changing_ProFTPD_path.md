---
title: "Changing ProFTPD path"
date: 2008-06-12
forum: Server Platforms
---

### Post by 330T on 2008-06-12
Hello, i've been running Ubuntu as a desktop for some time now and i'm switching over a web server to ubuntu server.

I have Apache2 up and running
Profptd up and running

I would like to change the default user long in directory to the www home directory but i've not been able to find how to do it.

I can edit my proftpd.conf but dont know what to edit to make the needed changes


Thanks
Brian

---

### Post by rogier.de.groot on 2008-06-12
Can't help you with proftpd, but may I suggest using SSH to transfer files instead?

---

### Post by 330T on 2008-06-12
> **rogier.de.groot said:**
> Can't help you with proftpd, but may I suggest using SSH to transfer files instead?

you may, could you link me to a great place to gain knolege on how to do so?  

still a newbie at command line stuff.

---

### Post by rogier.de.groot on 2008-06-12
Basically, just install the SSH server (sudo apt-get install openssh-server). I'll assume you're using a Windows client, in which case you'll want to Google for Putty & WinSCP. Putty is a telnet-like program, it basically gives you a remote commandline shell. WinSCP is a program for copying files over FTP, SFTP and SSH. If using an ubuntu client you should be able to enter a URL like "ssh://server" into the Gnome file manager.
You'll want to connect using the www-data user, if uploading files to /var/www anyway, so you'll need to give that user a password and a login shell. Do that with "sudo passwd www-data" and just editing /etc/passwd. I think by default www-data has /bin/false for it's shell, so find the line for the www-data user and change /bin/false to /bin/bash.
Good luck!

---

### Post by [vu] on 2008-06-12
Hello
Just Go to the Porject´s Site and read the documentation!

[http://www.proftpd.org](http://www.proftpd.org)

---

