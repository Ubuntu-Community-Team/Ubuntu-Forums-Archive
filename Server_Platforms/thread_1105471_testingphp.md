---
title: "testing/php"
date: 2009-03-24
forum: Server Platforms
---

### Post by macjak on 2009-03-24
I've checked that libapache2-mod-php5 is enabled yet I can't get test.php to run. When I entered sudo /etc/init.d/apache2 restart I got the follwing output:  * Restarting web server apache2                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                      [ OK ]
Entering [http://localhost](http://localhost) works: I get: IT WORKS
Could someone help beginner get his lamp stack working? Just want to learn to write php scrips so offline is fine.   Thanks

---

### Post by Iowan on 2009-03-24
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205") help page covers that error.

---

### Post by pparks1 on 2009-03-24
The error about Apache is more informational than anything else,it doesn't prevent Apache from starting up.

When you attempt to hit [http://localhost/file.php](http://localhost/file.php) what happens?

---

### Post by macjak on 2009-03-25
It's working now! Perhaps I just needed to restart apache so since I shut down last night..... The only mystery is why after typing 'sudo /etc/init.d/apache2 restart' I got: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName. I quess the next step is to find the apachect1 script so as to control stopping and starting of apache2. Do you know where this is in ubuntu?    Thanks for your help!

---

### Post by MystaMax on 2009-03-26
You can fix the error that you receive when restarting Apache by adding/updating the [ServerName directive]("http://httpd.apache.org/docs/2.0/mod/core.html#servername") to your /etc/apache2/apache2.conf file.

```
 ServerName YOURDOMAINNAME.COM 
```The apache2ctl script is in the /usr/sbin/ directory, but I should ask why you're looking for it? You should just type:

```
 sudo apache2ctl graceful 
```The above code will wait for all open connections to close to apache2, and then restart the daemon.

Other commands are:

apache2ctl start, stop, restart, graceful, configtest

Those are the ones I use on a regular basis.

If you were thinking of editing those apache2 scripts, I'd highly advise you didn't.

P.S. I used the man pages and whereis from the command line to find most of this information

```


whereis apache2ctl
man apache2ctl

 
```Hope this helps, good luck.

---

### Post by hyper_ch on 2009-03-27
and if you want to run php scripts fromt he terminal install php5-cli.

---

