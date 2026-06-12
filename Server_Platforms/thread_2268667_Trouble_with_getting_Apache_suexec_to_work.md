---
title: "Trouble with getting Apache suexec to work"
date: 2015-03-10
forum: Server Platforms
---

### Post by RavenLX on 2015-03-10
I'm having a hard time getting Apache and Suexec to work. I am trying to jail each domain into their own directory so scripts (perl, python, php, etc.) cannot read or write outside the domain's directory. Here's how I have it set up (following the tutorial here: [http://www.server-world.info/en/note?os=Ubuntu_14.04&p=httpd&f=8](http://www.server-world.info/en/note?os=Ubuntu_14.04&p=httpd&f=8) ) I'm working with an Ubuntu 14.04 server in VirtualBox as a test but hope to have it running on a server that holds actual domain names. Also note all times below are in UTC (I set the server for that rather than my local time zone - just matter of preference).

**The setup:**

Sites directory:
```

$ ls -l /var/www/sites
total 20
-rw-r--r--  1 root      root       11510 Mar  9 23:52 index.html
drwxr-xr-x  2 test1.com test1.com   4096 Mar 10 16:58 test1.com
drwxr-xr-x  2 test2.com test2.com   4096 Mar 10 23:54 test2.com

```

I created each site using this code at the command line (using test1.com as an example) :

```
$ sudo useradd  -d/var/www/sites/test1.com -s/bin/false -Um test1.com
```

For the sites in /etc/apache2/sites-available (using test1.com.conf as an example. test2.com.conf is set up the same but where test1.com is replaced with test2.com) :

```
<VirtualHost *>
ServerName test1.com
ServerAlias *.test1.com
DocumentRoot /var/www/sites/test1.com
SuexecUserGroup test1.com test1.com
</VirtualHost
```

Now for the suexec part I did this:

$ sudo apt-get install apache2-suexec-custom

Edited /etc/apache2/suexec/www-data :

The first few lines I have the following, and the rest of it I did not change (it's all commented info I won't include here) :
```
/var/www/sites
/var/www
public_html/cgi-bin
```

NOTE: There is no directory public_html/cgi-bin on my system, though. I don't know if that matters?

In the /etc/apache2/apache.conf I did not change anything.
In the /etc/apache2/sites-available/000-default-conf I changed the <directory> tag to reflect /var/www/sites but that is the only change I made. I made the same change to default-ssl.conf even though I don't think I use it (ie. I don't have ssl on this server).

Now, in test1.com I have:

```
-rwx------ 1 test1.com test1.com 241 Mar 10 16:58 suexec.cgi
-rw-r--r-- 1 test1.com test1.com 199 Mar 10 00:01 testwrite.php
```

The suexec.cgi file is the same as what is in the linked tutorial. Just basically prints an html page.
The testwrite.php is as follows:

[PHP]<?php
$test1 = "/var/www/sites/test1.com/";
$test2 = "/var/www/sites/test2.com/";
$file = "testwrite.txt";
$msg = "This is a test\n";
file_put_contents($test1 . $file, $msg);
print "Done.<br>\n";
?>[/PHP]

**What happens:**

Since I'm on a virtual machine, I go to the address: 192.168.1.12 (let's use that as an example of my test server's IP) in my host system's web browser. 

_Suexec test:_

So for this, I would go to: 192.168.1.12/test1.com/suexec.cgi and what I get is this:

```
Forbidden
You don't have permission to access /test1.com/suexec.cgi on this server.
```

_php test write:_

If I go to: 192.168.1.12/test1.com/testwrite.php I get this:

```
**Warning**:  file_put_contents(/var/www/sites/test1.com/testwrite.txt): failed to open stream: Permission denied in **/var/www/sites/test1.com/testwrite.php** on line **6**
Done.
```

Now these are supposed to work (the first example should have shown a page saying SuEXEC in big letters on it. The second page should have simply said "Done." and a file "testwrite.txt" should have been in the /var/www/sites/test1.com directory. 

None of this happened.

Can someone help me figure out what is wrong here and how to correct it?

---

### Post by RavenLX on 2015-03-11
Ok, I've looked into mpm-itk and even tried it. That did the same things as my OP. And it's I guess no longer supported(??) so that's not an option. I've heard of mod_privileges but that's for Solaris (I'm using Ubuntu 14.04) so that is not an option either. I'm thinking since suexec doesn't seem to work, there's no way to keep users in their own directories?

---

