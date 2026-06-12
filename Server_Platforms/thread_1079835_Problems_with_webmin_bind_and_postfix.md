---
title: "Problems with webmin bind and postfix"
date: 2009-02-24
forum: Server Platforms
---

### Post by vaudevillian on 2009-02-24
Let me say hello and thank you for reading my post.

I am very new to linux, This is my first install. Spacificly ubuntu server 8.10 amd64 bit version. I have installed Lampp and mail server in the inicial setup and gnome desktop up and running without any problems.

I am setting up a webserver/mail server.

I got xampp installed succesfuly and running. I also installed webmin and usermin also installed virtualmin.

I have followed all the help files so far. I ran into a problem when trying to bind dns server in virtualmin.

Bind inside Webmin says there is no problems found.

So I tried to continue setup of virtualmin and it gave me an error:

"The status of your system is being checked to ensure that all enabled features are available, that the mail server is properly configured, and that quotas are active ..

      Virtualmin is configured to setup DNS zones, but this system is not setup to use itself as a DNS server. Either add 127.0.0.1 to the list of DNS servers, or turn off the BIND feature on the module config page.

.. your system is not ready for use by Virtualmin."

I added 127.0.0.1 to the top of the DNS server list but when I saved it and  applied configuration re-checked hostname and dns client it is not saved.

Also when I try and goto Posttfix I am getting this error:

"Error while checking current Postfix configuration. Please manually fix Postfix configuration.

postfix: fatal: open /etc/postfix/main.cf: No such file or directory"

I went to that directory and yes the file is missing.... I cant seem to find any info regarding this missing file. I dont know if I missed something somewhere or what.

Thanks in advanced. :)

---

### Post by darek_dade on 2009-02-24
Try 
```
find . -name main.cf
```
to find this file.

---

### Post by vaudevillian on 2009-02-24
The file does not exist.

Could I possibly create this file? What do I need to put in it?

---

### Post by darek_dade on 2009-02-24
I am sorry, it should be
```
find / -name main.cf
```

You might want to look for this file: /usr/share/postfix/main.cf.dist It should contain commented and complete version of main.cf

---

### Post by vaudevillian on 2009-02-25
So, if I copy the main.cf.dist from the /usr/share/postfix/ folder to the /etc/postfix/ folder and rename it to main.cf it should be fine?

---

### Post by darek_dade on 2009-02-25
Yup, it should be fine. It will probably need some configuration, for more info go here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by vaudevillian on 2009-02-25
could all these issues possibly be resolved by adding a dns server? When I first installed ubuntu server I only installed mail and lamp.

---

### Post by Francewhoa on 2009-06-29
I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing Virtualmin, Webmin & Usermin.

---

