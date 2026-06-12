---
title: "Webmin"
date: 2005-09-17
forum: Server Platforms
---

### Post by dcostelloe on 2005-09-17
Anyone used webmin?

Is it safe for configuring all in one?

Are there any issues with webmin and postfix?

Lot of questions trying to setup a server the easy way.  :razz:

---

### Post by Wide on 2005-09-17
Sure go ahead & use Webmin, I been using it for years, never a problem.

---

### Post by Rollo Tamasi on 2005-09-17
[QUOTE=Wide]Sure go ahead & use Webmin, I been using it for years, never a problem.[/QUOTE]

i had a go at installing webmin last night but it didn't go as planned. When i hit in my.ip.address:10000 is came back when an error saying to try and use a secure connection, so then i used [https://my.ip.address:10000](https://my.ip.address:10000) but i just got the same, error ! file not recoginised.

Is there some procedure that i need to do before installing webmin? I have fully access to the directory that webmin is installed into and have chmod777 permissions on the entire /var/www/ dir.

I have a thread in this forum regarding a phpmyadmin installation aslo, i'd imagine the problem i'm having with the installation of phpmyadmin is steming from the same issues that i'm having regarding webmin.

---

### Post by Phreekystylze on 2005-09-18
are you trying to connect on the local machine or are you connecting from a remote location?

from same machine try [https://localhost:10000](https://localhost:10000) and if you're not on the local machine then use the [https://ip.address:10000](https://ip.address:10000) and make sure you are using SSL in webmin or else you will need to use http instead of https

-Phreek

---

### Post by Rollo Tamasi on 2005-09-18
[QUOTE=Phreekystylze]are you trying to connect on the local machine or are you connecting from a remote location?

from same machine try [https://localhost:10000](https://localhost:10000) and if you're not on the local machine then use the [https://ip.address:10000](https://ip.address:10000) and make sure you are using SSL in webmin or else you will need to use http instead of https

-Phreek[/QUOTE]

yeah i have tried both locallly and remotely, i get the same error

---

### Post by dcostelloe on 2005-09-19
Have you tried machinename.localhost:10000

---

### Post by geek404 on 2005-09-21
[QUOTE=Rollo Tamasi]yeah i have tried both locallly and remotely, i get the same error[/QUOTE]

I would check you /etc/webmin/miniserv.conf file for the following line.  ```
allow=127.0.0.1
``` 
If you want to connect from a remote machine put that machines ip address there.  

Another thing I have seen that is specific to ubuntu is that when installing webmin it by default copies the root account and password for login to webmin.  Well by default in ubuntu root is not enabled and you don't know the password.  So prior to installing webmin you need to set a password for root.  ```
sudo passwd root
```   This make Ubuntu less secure than default install but I have not gone back to research the issue.  I am sure there is a way to perform the user sync post install.  

Hope this helps.

Brian

---

### Post by kivu on 2005-09-21
[QUOTE=geek404]I would check you /etc/webmin/miniserv.conf file for the following line.  ```
allow=127.0.0.1
``` 
If you want to connect from a remote machine put that machines ip address there.  

Another thing I have seen that is specific to ubuntu is that when installing webmin it by default copies the root account and password for login to webmin.  Well by default in ubuntu root is not enabled and you don't know the password.  So prior to installing webmin you need to set a password for root.  ```
sudo passwd root
```   This make Ubuntu less secure than default install but I have not gone back to research the issue.  I am sure there is a way to perform the user sync post install.  

Hope this helps.

Brian[/QUOTE]
 No need to set a password on the ubuntu root account. See this thread: 
[http://ubuntuforums.org/showthread.php?t=938](http://ubuntuforums.org/showthread.php?t=938)

This is a copy:
In /usr/share/webmin/ there is a Perl script called changepass.pl to change root password in webmin use this:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

And that will fix it! No install/removal necessary.

---

