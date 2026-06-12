---
title: "Apache configuring Ubuntu 8.04 Server"
date: 2008-08-02
forum: Server Platforms
---

### Post by maxidrom11 on 2008-08-02
I am new to this
First I tell what I need
I have dedicated server
--------------------------------
I need hosting for **multiple websites**
I need documentroot in **/srv/www/** directory 

What to I have to do to configure my Apache2 to get **multiple websites** working in **/srv/www/** directory ???

---

### Post by arkopII on 2008-08-02
You need to configure one virtual host for each site that you want to publish. For that, you should take a look at the default file in /etc/apache2/sites-available. In your case, basically, each virtual hosts file should change the DocumentRoot directive to be the path /var/www/yoursitefiles.

I hope that helps.

---

### Post by Dedoimedo on 2008-08-02
Hello,

I have written a long guide, using the CentOS 5 as the platform, but the principle remains pretty much the same, excluding the location of some of the files and directories, which I hope you can figure on your own.

If you're interested, see the link in my siggie - please note it's 150 pages :)

Cheers,
Dedoimedo

---

### Post by maxidrom11 on 2008-08-03
thanks for your wise answers - 

I will go on with posting here here as I proceed ...

---

