---
title: "Apache + more domains"
date: 2008-11-15
forum: Server Platforms
---

### Post by virtualweb on 2008-11-15
Hi there,

I'm a newbie with UBUNTU. But I have a question before I wanted to use UBUNTU. 

Now, with normal apache on windows server, my problem is:
I can only make domains like:
[http://localhost/'sitename'/index.php](http://localhost/'sitename'/index.php)
or [http://localhost/'other'/index.php](http://localhost/'other'/index.php)
But when I use root in de index.php (so i use '/') i go to localhost and not to localhost/sitename.

Now i know with windows server you can do:
localhost:9493 and localhost:3002 and that's your root.

Is that also possible with UBUNTU server?

THanks for reading, hope i'll get an answer :-)!

---

### Post by Vegan on 2008-11-15
Apache usually listens on port 80 but it can be changed. Add 

Listen: port#

To the httpd.conf file in /etc/apache2

:guitar:

---

### Post by Marvindreyer on 2008-11-15
I completely agree with Vegan and advice you the same!

---

### Post by Philio on 2008-11-15
You should really use the file ports.conf in Ubuntu.

Also there is no semicolon after the word Listen it should just be:

Listen 80
Listen 9493
Listen 3002

If you want to setup multiple domains you need to setup virtual hosts. Or you could setup separate web roots for your different ports also using virtual hosts.

---

### Post by Philio on 2008-11-15
This thread might be useful:

[http://ubuntuforums.org/showthread.php?t=983243](http://ubuntuforums.org/showthread.php?t=983243)

---

